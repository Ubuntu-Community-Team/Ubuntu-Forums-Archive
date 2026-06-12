---
title: "just updated to 7.10, missing mime octet streams etc?"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by daceo on 2007-11-26
Hi,
just updated from kubuntu 7.4 to 7.10. 3d graphics seem more stable, but all is not well somewhere inside, have tried the following any ideas

on opening open office:
Malformed URL
file:///home/frank
then:
Could not find mime type
application/octet-stream
then:
No mime types installed.

and can't open any documents...

tried 
 rm ~/.kde/share/mimelnk/application/octet-stream.desktop
 says 

No such file or directory

kcontrol in a console gives

frank@frank-desktop:~$ sudo kcontrol
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: "/var/tmp/kdecache-frank" is owned by uid 1000 instead of uid 0.
kio (KSycoca): WARNING: Found version 93, expecting version 94 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): ERROR: No database available!
kcontrol: WARNING: No K menu group with X-KDE-BaseGroup=settings found ! Defaulting to Settings/
kio (KSycoca): WARNING: Found version 93, expecting version 94 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): WARNING: Found version 93, expecting version 94 or higher.
kio (KSycoca): WARNING: Outdated database found
ERROR: Communication problem with kcontrol, it probably crashed.
frank@frank-desktop:~$ kio (KSycoca): WARNING: Found version 93, expecting version 94 or higher.
kio (KSycoca): WARNING: Outdated database found
Error: "/tmp/ksocket-frank" is owned by uid 1000 instead of uid 0.
kcontrol: ERROR: : couldn't create slave : Unknown protocol 'file'.
kcontrol: ERROR: : couldn't create slave : Unknown protocol 'file'.
                                                                       
and does not come up with any buttons or anything, 
system settings just crashes, 

any ideas

cheers

daceo

athalon xp+2200 
ati 9250

---

