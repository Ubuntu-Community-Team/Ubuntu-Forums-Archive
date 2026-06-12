---
title: "Problem - With Resolution After Nvidia Driver Installed !!"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by AbItOuS on 2006-03-09
Hello All,

i downloaded latest nvidia driver for my suse10 

and i entered Suse 10 ( FailSafe ) and installed it

the problem is my resoultion automated to 1200*an other big number :( 

and i wanna change it to 1024*768 cuz my monitor can't hold a bigger than

that resolution !! can any one help me to do it in terminal by commands

cuz i can't see any thing in kde or gnome or any graphical screen cuz of sync out of range  !! :(

thanks to all

---

### Post by kaamos on 2006-03-09
Hello!

I haven't used Suse in some time, but I guess this should work there as well. Pressing ctrl+alt+F1 should get you a console login. Then use the command
```
sudo nano /etc/X11/xorg.conf
```
to get to your graphical settings. The file has sections like this:
>      Depth 24
     Modes "1400x1050" "1280x768" "1024x768" "800x600" "640x480"
Just remove the resolutions your monitor is not capable of. Save the file and then 
```
sudo /etc/init.d/gdm stop
```
(if you have the kde login manager, just replace gdm with kdm) and
```
sudo /etc/init.d/gdm start
```

---

### Post by AbItOuS on 2006-03-09
thanks sir :) for ur fast reply and quality support ;)

i'll try right now..

i hope it work....

best greets for u

---

### Post by AbItOuS on 2006-03-09
it does n't work sir

cuz i can't find X11 !!

and the order nano !! can't procced....

more help for SUSE 10 Here plz :)

thanks for ur helping ;)

---

