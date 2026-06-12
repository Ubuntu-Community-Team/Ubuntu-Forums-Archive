---
title: "dapper upgrade- problem with x server"
date: 2006-04-09
forum: Installation &amp; Upgrades
---

### Post by lemmy999 on 2006-04-09
After upgrading from Breezy to dapper flight 5 i am getting xserver error messages. 
the error message says that the xserver didnt start. the xserver log output is not very clear. i'm not sure what is relevant



As a newb is this easy to fix? My options appear to be

1. Re-install and lose anything on Home
2.try and retrieve what i need from home using a live CD, then burn to disk
3. try and resolve the xserver problem
4. install the OS on another partition and then attempt to retrieve data from Home

Any thoughts as to the best way to proceed?

---

### Post by ubernoob on 2006-04-09
since you don't write your output here i can just take a wild guess, and that is that you need to install drivers for your graphic card.  Are you using ati or nvidia? And how does your xorg.conf look like? /etc/X11/xorg.conf

---

### Post by aysiu on 2006-04-09
> Any thoughts as to the best way to proceed? I would go with these two, in this order: [QUOTE=lemmy999]
3. try and resolve the xserver problem
2.try and retrieve what i need from home using a live CD, then burn to disk[/quote]

---

### Post by lemmy999 on 2006-04-09
i'm using an ATI radeon 7000 card.

i've tried the etc conf but am getting the following message

gedit: error while loading shared libraries: libavahi-client.so.3: cannot open shared object file. no such file or directory

i assume that the command gedit /etc/x11/xorg.conf is correct?

---

### Post by ubernoob on 2006-04-09
if you don't have x-server running, gedit won't do you any good. You need shell commands. Try 
sudo nano /etx/X11/xorg.conf to change your file or
cat /etx/X11/xorg.conf to print the file to screen.

---

### Post by lemmy999 on 2006-04-09
tried sudo dpkg-reconfigure xserver-xorg

output says that xserver.xorg is not installed.

---

### Post by ubernoob on 2006-04-09
sudo apt-get install xserver-xorg

or you can do 
sudo apt-get install ubuntu-desktop

i think the last one is better since that will probably install xserver-xorg and other packages you might be missing

---

### Post by lemmy999 on 2006-04-09
ok

tried the ubuntu desktop solution. 

output says that there are unmet dependencies

---

### Post by lemmy999 on 2006-04-09
i have also tried installing xserver but keep getting output

could not open lock file /var/lib/dpkg/lock- open (13 permission denied)

keep being asked if i am root??

---

### Post by ubernoob on 2006-04-09
do you use "sudo" before the command?

And how did you upgrade to dapper? I think you should go trough it all over again... search the forum for a howto for upgrading (or downgrading)

---

