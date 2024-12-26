# NOTAM-to-Boundaries
Convert a NOTAM airspace block defining a Fly-zone into corresponding no-fly boundaries as expected by the majority of free flight computers.

This code is javascript wrapped in HTML written with assistance from ChatGPT.  It contains lots of inefficiencies and is not under active development.

Usage: download to your device and execute the code in a browser.  

Background.  Free flight (e.g. paragliding, hang gliding) is typically conducted outside of controlled airspace.  In Europe and North America by default all airspace is un-controlled.  The relevant airspace authority define blocks of controlled airspace.  In essence the skies are open-unless-excluded.  
The popular free-flight computers (e.g. XCtrack, XCSoar, LK8000, FlySkyhy, Oudie, Naviter) are built on the  open-unless-excluded principle.  They accept, from various sources, airspace defintions displaying the airspace blocks and, in some cases, generating advance warning alarms when approaching boundaries.  

Other parts of the world operate a controlled-by-default approach to airspace with areas designated for free flight defined by specific airspace blocks (ypically class G).  This reverse default presents an issue for the flight computer software; they are not expecting to be told un-controlled areas.

This uility partially automates the creation no-fly airspace blocks surrounding a defined un-controlled zone.

It expects as input a file containing one or more contiguous airspace blocks.  If the airspace is non-contiguous then it could be edited into multiple contiguous areas and processed separately.

IMPORTANT. it can only handle polygon area definitions.  (Airspaces are frequently defined with arcs and circles - this code cannot handle those shapes.  If anyone knows how to handle such shapes I'd be very interested to hear for another project I'm working on.)

Upon opening the input file the airspace blocks are displayed on a map and a first estimate of the outer boundary is drawn as a green polgon.  For simple/ small number of airspace blocks the outer boundary may be accurate but for 3+ blocks it is likely to require some manual intervention.  Each input block is drawn as a blue polygon with numbered markers at the points. A green line is drawn reflecting the current outer boundary.  To the right side of the map is a table of all the points of the input airspace blocks indicating their inclusion/ exclusion and sequence in the outer boundary. Each point can be dragged and dropped in the table to change it's sequence. If a marker point is clisked on the map it's inclusion/ exclusion status is toggled.

When the user is satisfied with the shape fo the outer boundary clicking the 'Generate Airspace' button (1) draws a red coloured polygon denoting the western boundary and a green polygon for the east boundary (2) creates a 'restricted airspace.txt' file in the devices downloads folder containing.  The restricted airspace file contains the west and east boundaries plus a "ceiling" corresponding to each of the input blocks.

The generated airspace file should be validated before use.

No warranty, implied or otherwise, is made as to the accuracy of data created by this utility.  As always, the responsibility for flight is entirely with the individual.
