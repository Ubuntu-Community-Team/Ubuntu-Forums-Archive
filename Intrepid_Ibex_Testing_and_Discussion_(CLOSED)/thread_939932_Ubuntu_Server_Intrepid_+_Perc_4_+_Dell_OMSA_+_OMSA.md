---
title: "Ubuntu Server Intrepid + Perc 4 + Dell OMSA + OMSA web page ??"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by oneloveamaru on 2008-10-06
I had to add a couple hard drives to a server, so I took the long road and also did a fresh install of Ubuntu Server "Intrepid" on a Dell 2850 with a Perc 4 card. I got Dell OMSA up and running as normal but now it can no longer see my Perc 4 card when I run "omreport storage controller"   Something changed... any ideas?

Also, the OMSA web page fails to load as well. Any help there would be appreciated too, thanks!

:~# omreport storage controller
No controllers found

 With Hardy on the same EXACT server set up, i can run "omreport storage controller" without any problems.

:~# omreport storage controller
 Controller  PERC 4e/Di (Embedded)

Controllers
ID                                : 0
Status                            : Ok
Name                              : PERC 4e/Di
Slot ID                           : Embedded
State                             : Ready
Firmware Version                  : 5A2D
Minimum Required Firmware Version : Not Applicable
Driver Version                    : Not Applicable
Minimum Required Driver Version   : Not Applicable
Number of Connectors              : 2
Rebuild Rate                      : 30%
BGI Rate                          : Not Applicable
Check Consistency Rate            : Not Applicable
Reconstruct Rate                  : Not Applicable
Alarm State                       : Not Applicable
Cluster Mode                      : Not Applicable
SCSI Initiator ID                 : 7
Cache Memory Size                 : 256 MB
Patrol Read Mode                  : Auto
Patrol Read State                 : Stopped
Patrol Read Rate                  : Not Applicable
Patrol Read Iterations            : 529

---

### Post by cariboo on 2008-10-06
You do realize that Intrepid hasn't been released yet and is really buggy. I would suggest to downgrade back to hardy for at least another 6 months. Servers are supposed to be reliable, go with what works, not the bleeding edge.

Jim

---

### Post by oneloveamaru on 2008-10-23
I figured out that it's not Ubuntu specific. Debian Lenny has the SAME problem. I think it has something to do with the new Kernel. I have a Debian Lenny box running with a Perc 3 controller and omreport storage controller spits out the info about the Perc 3 with no problems. It just doesn't work with the perc 4 controller.

Anyone have any suggestions??

---

