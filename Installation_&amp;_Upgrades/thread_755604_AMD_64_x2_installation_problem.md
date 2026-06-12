---
title: "AMD 64 x2 installation problem"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by Rebooth on 2008-04-15
please help i'm tryin to install ubuntu 7.10 64bit amd? 
i have both amd64 intel64 cds that i tried

amd 64 x2 4400+
asrock aliven nf7 fullhd
1 gb /256 shared
samsung monitor 591s
40gb hdd

it stops at 
check battery state..
running boot ... etc/rc.local


is it normal? what will i do?
any bios setup tips?drivers 

i'm a newbie in linux please help

---

### Post by Partyboi2 on 2008-04-15
what graphic card are you using?

---

### Post by Sef on 2008-04-15
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Did you check the disk for defects?

---

### Post by Rebooth on 2008-04-15
i use the built-in graphics on motherboard- nvidia geforce 7 series (nv44)
my cds are from ubuntu -
2-- 7.10 for PC
2--7.10 for 64bit PC


1--7.10 for AMD64 ----downloaded and burned using nero

i tried  all of does cds.

my 7.10 [for PC] and [64bit for PC] where guaranteed working from other computers  except amd64 cd. 

first it reads the all cds then i choose start/install unbuntu. and it goes up until here....


-----------------------
*Starting deferred execution scheduler atd 	[ok]
*Starting Periodic command scheduler crond 	[ok]
*Checking battery state ... 			[ok]
*Running local boot scripts (/etc/rc.local)	[ok]

----------
it flashed i think 2-3 times then this one appeared
-----


**Ubuntu is running in low-graphics mode**

Your screen and graphics card could not be detected correctly. To 

use higher resolutions, visual effectes or multiple screens, you 

have to configure the display yourself.


[ ] Always run in low-graphics mode

                           
                    Configure...   Shutdown     Continue
-----------------
when i finnish configure .. it returns back 


-----------------------
*Starting deferred execution scheduler atd 	[ok]
*Starting Periodic command scheduler crond 	[ok]
*Checking battery state ... 			[ok]
*Running local boot scripts (/etc/rc.local)	[ok]

----------

same with choosing Continue; and [ ] Always run in low-graphics mode

please help me sir.. :(
i'm currently using mandriva 2008 and xp as dual boot

---

### Post by Partyboi2 on 2008-04-15
When you get to> *Running local boot scripts (/etc/rc.local)	[ok] press Ctrl+Alt+F2 to get to a terminal then 
```
sudo dpkg-reconfigure xserver-xorg
``` choosing nv for the video driver. Finish answering all the questions then back in the terminal type
```
startx
``` If choosing nv does not work then try with vesa. If none of these work then I suggest downloading the [alternate cd]("http://releases.ubuntu.com/7.10/") which is a text base installer.

---

