---
title: "Need Help Configuration problem after xserver failure on install"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2005-04-10
Ive been trying to get Ubuntu going since the 8th and tryed reinstalling a few times. I have nv which seems to be set up ok but have a trouble maker monitor "Bridge BM17C" 17 inch monitor. Autodetect refresh was way off so I tryed moding it in dpkg-reconfigure xserver-xorg but that did not seem to work. I went into xorg.config and the sinc and refresh looked  ok
 section "monitor"
 Identifier "Bridge BM17C"
OPTION "DPMS"
HorixSync 30-70
VertRefresh 50-160

 The reses look comparable to my xp set up.
 The error I got was some no sybols found 
and nv(0):no valid modes found
screen found but no usable configuration.

 Im trying to mod it in debug mode as I have to reinstall to get the regular prompt as its has some text output then a black screen. Im a total linux newb and would apreciate any help  :shock:

---

### Post by nad on 2005-04-10
Please reply with your xorg.conf file and /var/log/Xorg.0.log files in an attachment.

Dan M

---

### Post by Omnios on 2005-04-10
[QUOTE=nad]Please reply with your xorg.conf file and /var/log/Xorg.0.log files in an attachment.

Dan M[/QUOTE]

 I would but im in xp and cant do much with Linux other than read the logs and config.
 In my winXP set up it listed my monitor as a Bridge BM17C but after checking the back of the monitor it seems to be a KTK BM17E , 17" monitor. Im going to try to reinstall and use a lower depth setting off the defaults. My vid is a Nvidia GeForce2 MX 100/200. Im going to try to get into the log file as it is a screens found but but none have a usable configuration error which is probably a sync refresh error to see what the errors are for the the reses. Im a total newb as in I dont even know a lot of the commands yet but I will learn. Thanks for the post by the way I was getting scared lol.

---

### Post by Omnios on 2005-04-10
Im getting two main erros for res checks 
Bad mode clock/ Interlace/doubleese$
and is larger than boisy programmed panel size.
Getting both errors on practicly everything.
I think it cant detect hscync and crefresh rang and havent found any specs on the net yet.

---

### Post by Omnios on 2005-04-11
I know its definatly the monitor from what I read on the web and also there is vert detect problems with one of them. My Winxp/NVididia Gforece2 runs it as a Bridge BM17C under windows"windows autodetect lol. WHen I finaly peeled the monitor off the back of the wall and read read the back of the monitore I found out it is actualy a KTX model number BM17E which is a defunct high problem monitor but once you get them working they perform very well. One problem I read so far is with vert Refresh. Right now Its set a 80hz and looks sweet. 

 Another problem I have is I can mod dpkg-reconfig xserver-xorg in recovery mode but I can't run x-server from the main command prompt. Another not when xserver errored on install it told me to run DMG? what aould that be remember im a first time linux newb. The error messages I am getting is screens found but none have have a usable configuration. In the log I got res errors on just about every res.

(ww) nv(0) config file hsync range 30-65 khz not within DDC hsync ranges
(ww) nv(0) config file config file vrefresh range 50-75hz not within DDC vreshresh ranges.
(ll) nv(0) Generic Monitor: using hyyne of 30.00-65.00 Khz
(ll) nv(0) Generic Monitor: using vrefresh range of 50.00-75.00 hz
clcok range: 12.00 to 350.00 hz

The main errors im getting is 
 Bad mode clock/Interlace/doublese$
and 
 is larger than the boissy programmed panel side of 1x1$

 My win xp hz is 60,,,,-85 but no luck finding  the horizontal.

 Sorry cant post the full files Im running XP right now

---

### Post by nad on 2005-04-11
If this is a SUN-BM17E, I have found the following specs:

Horizontal: 30-74KHz
Vertical: 50-120Hz

It also supports DDC info scanning.

I would suggest trying these values before you fry your monitor.

I can not help you further without reviewing your unattached files.

Dan M

---

### Post by Omnios on 2005-04-11
Its A KTX (now defunct) BM17E I found a windows ini driver and found the following info in it. I nkow its a Ktx because I got the info off the tag on the back of the monitor.

 KTX BM17E
Modes. \1280.1024 "Model,, "#).0-70.0, 50.0-160, +,+
Max Res 1280.1024
DPMS,, 1
ICM Profile,1,7
 
 My Xp has unsuppoorted hz off and has 60,70,72,75,80 hz
This might also be a problem with the monitor interacting with the video card but not shure.

 Is there a way of saving the logs to floppy in Linux Recover Mode?

 Trying to get the files on a floppy so I can send post them in XP, checked a few web sites on linux commands and cant seem to find my floppy, I think its broken, anyways im still going to plug away at it even if it takes me till the next release, I just like Ubuntu and dont feel like trying another distro. The install may be easier but dont need the other headacks. =;

---

### Post by Omnios on 2005-04-12
K want to try something I have network in recovery mode so I downloaded the nvidia driver. sudo apt-get install nvidia-settings. However I could not use sudo nvidi-glx-config enable Im assuming that what is done to enable it in console but im in recover dos. Also is there a way to get into dos (short cut)  from the main boot it seems to be runnign in black screen.

---

### Post by nad on 2005-04-12
From the boot menu choose Recovery Mode. This will give you a single user terminal session in ubuntu.

I have found ubuntus' handling of the floppy drive, /dev/fd0 and mount point /media/floppy0, to be inconsistent and broken. Apt-get install mtools. This will give you a dos like interface to your floppy and is certainly easier from the command line. mdir will do a directory listing on /dev/fd0. 'mcopy somefile a: ' will copy to a: . You can even mix dos and unix naming conventions and it will usually work.

Dan M

---

### Post by Omnios on 2005-04-12
Finaly managed to get the files mtools worked well thanks for the tip. I had to zip them to upload them could have added .txt to them but they might have currupted. Thanks for all the help it kept me going hopefully we will have this solved soon.

---

### Post by nad on 2005-04-12
I would set the HSync and VRefresh to more reasonable values, comment out the VideoRam line and maybe comment out the Load "ddc" line.

Do not try to use the nVidia driver until your monitor is working.

Dan M

---

### Post by Omnios on 2005-04-12
K tryed that and even tryed using the autodetect the vsyn and refresh rates on reconfig. When I try to boot normaly it lookes like gnome is running but I just cant see it so im assuming it thinks everything is ok when it is  not. By pressing return etc I can get some text visable and it seems the computer settles down and just gives me a black sceen. I tryed the KTX bm18E specs (they are huge by the way) and that didnt seem to work. I am not getting the xserver error when I boot Ubuntu normaly which is strange.

---

### Post by nad on 2005-04-12
Can you switch to a terminal screen, CTRL + ALT + F1, after it boots normally to a blank x screen?

Dan M

---

### Post by Omnios on 2005-04-12
[QUOTE=nad]Can you switch to a terminal screen, CTRL + ALT + F1, after it boots normally to a blank x screen?

Dan M[/QUOTE]

 No and I also tryed ctrl alt backspace to try to change the res. SOmetimes theres a flashing prompt on the bttom of the dcreen that moves around and stuff and it lookes as if its switching as the cursor sometimes sissapears but I still can't see anything but the flashing cursor or a black screen.

---

### Post by nad on 2005-04-12
I've seen this problem. It seems to be a driver conflict. I can usually recover by CTRL + ALT +DELETE (the three fingered M$ salute). Ubuntu scans this as a shutdown command and the computer reboots. I repair my xorg.conf (I do a fair amount of config testing) at a terminal screen and init 2 to my normal boot sequence.

From the number of posts here, Xorg seems to be completely borked in some configurations.

Dan M

---

### Post by Omnios on 2005-04-12
does anyone know anything about the xorg no DCC option I read something about it but it didnt say how to writ it in the config?

---

### Post by Omnios on 2005-04-12
K I posted a bug on Bugzilla the other day and found out today that the it seems that the nvidia driver thinks my monitor is a flat panel and doing all kinds of wierd stuff to it. Hopefully it will be fixed by nvidia  [-o<

---

### Post by Omnios on 2005-04-14
Got it sorted out.there is a nv driver bug took me days but I got the nividia driver installed, the glx package installed and moded the xorg config to show the nvidia driver in reconfig. Its running real good. Thanks to everyone for the support. This comminity and forum ahs ms windows borked :)

---

