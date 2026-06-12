---
title: "error booting"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by c30tehran on 2008-09-20
i ran into a problem when booting the ubuntu  8 .there was not any 
problem when intalling the software. but after reseting for twor or three time,
i couldn't run the program .i have already tried scandisk and safemode as well.but the problem does exist.
anyway ,i installed the software again on a differnet drive and still got the same problem. but i could solve the problem in a way . i still have the first installation and waiting paiting from you help so that i can solve it
--------------------------------
etc/init.d/rc : 317 : sed : permission denied 

.... 
init : unable to execute : " /bin/sh" for rc-default: permisstion denied 
init : rc-default main process (4420) termited with status 255 
udevd-event [4422] : run - program:exec of program ' /lib/udev/usb-id failed' 
udevd-event [4423] : run - program:exec of program ' /lib/udev/scsi-id failed' 
udevd-event [4426] : run - program:exec of program ' /lib/udev/path-id failed' 
....... 
------------------------------------ 
ctrl+alt+f1 

starting up 
loadin , please wait ... 
kinit : name -to -dev-t (/dev/disk/by-uuid/...) = sda13 (8 , 13) 
kinit : trying to resume from /dev/disk/by-uuid/.... 
kinit: no resume image , doing normal boot ... 
-------ctrl-alt-del------------------------ 
init : unable to "/bin/sh" for ctrl-alt-del ; permission denied 
init : ctrl-alt-del main process (4474) 
terminated with status 255

---

### Post by wpshooter on 2008-09-20
Before installing, did you check the integrity of your Ubuntu install CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by Pumalite on 2008-09-20
What about md5sum on the iso, burnning at 4x, not using CD-RW? Clean the lens in your burner just in case.

---

### Post by amitkr on 2009-06-27
**/etc/init.d/rc: 2: sed: Permission denied** 			
 			 			 		   		 		 		I am not able to login to ubuntu 7.04. As the bootin starts and the bar starts filling, a black screen appears and it says - /etc/init.d/rc: 2: sed: Permission denied, almost 20 times. I tried to login from recovery mode, but failed. I don't have any clue now, how to recover my data. I got the ubuntu 7.04 live cd, somebody said run it, but it doesn't shows my data, so I am not installing it. Please, help me out.........plzzzzzzzzzzzz. My position is very bad and I despeately need my data. I don't have any backup of those. plzzzzzzzzzzzzzzzzz:sad:

---

### Post by presence1960 on 2009-06-27
> **amitkr said:**
> **/etc/init.d/rc: 2: sed: Permission denied** 			
 			 			 		   		 		 		I am not able to login to ubuntu 7.04. As the bootin starts and the bar starts filling, a black screen appears and it says - /etc/init.d/rc: 2: sed: Permission denied, almost 20 times. I tried to login from recovery mode, but failed. I don't have any clue now, how to recover my data. I got the ubuntu 7.04 live cd, somebody said run it, but it doesn't shows my data, so I am not installing it. Please, help me out.........plzzzzzzzzzzzz. My position is very bad and I despeately need my data. I don't have any backup of those. plzzzzzzzzzzzzzzzzz:sad:

7.04 is no longer supported. you should either use 9.04 or 8.04-they are the best bet. You can boot off the Ubuntu Live CD and access your data to back up.

---

