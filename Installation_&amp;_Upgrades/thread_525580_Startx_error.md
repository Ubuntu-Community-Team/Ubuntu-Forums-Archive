---
title: "Startx error"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by mike6426 on 2007-08-14
I am trying to install ubuntu 7.04 on my laptop, a dell inspiron 1420.  My computer has an Intel x3000 and the driver I am trying to use is vesa.  I have had multiple problems, most of which I have solved, all dealing with the xserver.  I have done a dpkg-reconfigure xserver-xorg and a dpkg-reconfigure -phigh xserver-xorg.  After doing both of these, I have tried to startx, but it comes up with this error.

(==) Log file: "/var/log/Xorg.0.log", Time: Tues Aug 14 09:49:01 2007
(==) Using config file: "/ect/X11/xorg.conf"
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

I have also tried to remove /tmp/.X0-lock, but there is no file with that name.  Also, I cannot access the log file because I do not have permission to access it.

---

### Post by dannyboy79 on 2007-08-14
first, you can always cat a log file as yourself, if it scrolls to fast than just use the pipe and less. so it would be like this
cat /var/log/Xorg.0.log | less
then you just hit enter to look at line by line, when you want to exit out of that, just hit "q"
or you could just use gksudo with gedit. gksudo, sudo, and gksu require YOUR password and it'll give you temporary root priveleges. So it would be
gksudo gedit /var/log/Xorg.0.log
NOTE: you always to use gksudo when opening any GUI type app, like nautilus, gedit etc etc. Any terminal based command or even to run vi or nano, you can still use just sudo.

As far as the error about not finding any screens, make sure you xorg.conf has all the neccessary sections within it. It should be recreated when you do the sudo dpkg-reconfigure xserver-xorg so I am not sure why your getting these errors. also, you don't have VESA in your xorg.conf I hope, meaning it should be capitalized. Linux is case sensitive.

Also, what happens if you do this after editing your xorg.conf file

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
(NOTE: this is assuming you're using Gnome)

are you presented with a login now? if not, what is the error this time?

---

### Post by mike6426 on 2007-08-14
Nvm about that.  It seems that the error is caused by the screen mode, there is no "1024x768", "800x600", "640x480".  The modes have names like 112 and 13b, should that be correct?

---

### Post by dannyboy79 on 2007-08-14
112 and 13b are certainly not vaild scrren modes. here's a clip from my xorg.conf

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
  [B]  SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection[/B]
EndSection

Nevermind all the unusual stuff, I run 2 seperate screens. the stuff that is bolded must be in their for it to work I imagine.

---

### Post by mike6426 on 2007-08-14
I have that in the .conf, but looking in the log file it says things such as "Mode: 117: (1024x768)".  Under that there is a lot of technical jargon, the inputs being numbers.
There are also ones similar to that with the various resolutions, but there are also ones with (0x0).

---

### Post by dannyboy79 on 2007-08-14
you don't be chance have this in your xorg.conf do you? 

Load "glx"

I don;t think that module will work with vesa.

---

### Post by mike6426 on 2007-08-14
yes it did have that, I took it out.  But I still get a failed to start the x server.

---

### Post by mike6426 on 2007-08-15
bump

---

### Post by dannyboy79 on 2007-08-15
and what's the new error if any? have you gogled this? have you tried to install the i810 driver, is that one compatible with your gfx card?

---

### Post by mike6426 on 2007-08-15
I have looked that one up, it was the first one that came up.  This is the problem that comes up [http://ubuntuforums.org/showthread.php?t=515473&highlight=startx+error](http://ubuntuforums.org/showthread.php?t=515473&highlight=startx+error).  After I fix that one, the problem from the beginning happens.

I have tried that driver, it did not help.  I looked up the driver on the xserver site and the one that seems to work with it (i965) is not on the list.

---

### Post by dannyboy79 on 2007-08-15
you definetly don't want to be starting the xserver as root. just enter 
startx.
please post your entire xorg.conf so I can see it. if you're not sure how to get it so you can copy it and paste it here, then just work from a livecd, then mount your ubuntu partition to a folder like /mnt  and show it using gedit, then copy and paste it here.

---

### Post by dannyboy79 on 2007-08-15
according to this bug report, back in March, the X3000 GFX chip is working with i810. There's an xorg.conf toward the bottom that the person even states that compiz-fusion is working.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62135](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62135)

---

### Post by mike6426 on 2007-08-15
ya, live cd runs into the same problems unfortunatly.  I am going to try to get it using a flash drive.  Can't mount flash drive...don't know what file system it uses.

---

### Post by dannyboy79 on 2007-08-15
you're saying that a normal live cd, even run in safe mode doesn't work? MOst usb sticks are fat32, you can try to specify the filesystem as vfat. I am sure there are solutions for this, have you tried the boot options like irqpoll yet?

---

### Post by mike6426 on 2007-08-15
ya, no live cd works.  I have also tried that filesystem.  I have not tried that boot option yet, but I am going to try [http://ubuntuforums.org/showthread.php?t=509408&highlight=Inspiron+1420](http://ubuntuforums.org/showthread.php?t=509408&highlight=Inspiron+1420) first.

---

### Post by dannyboy79 on 2007-08-15
yeah, that'd be the thread. I can't believe Feisty is that incompatible with your hardware! Heck, why wouldn't you just give Gutsy a try?

---

### Post by mike6426 on 2007-08-16
I can't install Gutsy as the CD does not have a kernel.  I could not do the fix here [http://ubuntuforums.org/showthread.php?t=509408&highlight=Inspiron+1420](http://ubuntuforums.org/showthread.php?t=509408&highlight=Inspiron+1420) because it does not like my internets.  Any help please, I really want ubuntu on my laptop, not vista.

---

### Post by dannyboy79 on 2007-08-16
i don't know what you mean it doesn't like your internets. if you're saying that you're not connected to the net then download all the deb's from another machine, put them on a usb stick and copy them from the usb stick to your machine then run the commands from the command line.

I don't know what you mean by gutsy doesn't have a kernel, I just installed gutsy tribe 4 the other night.

I am running out of ideas to tell you sorry. the vesa gfx module is suppose to be compatible  with pretty much all hardware. I would just keep gogling around and you'll find an answer sooner or later.

---

### Post by mike6426 on 2007-08-16
Ya, I can't connect to the internet.
Also, it seemed that i installed a bad .iso, but i redownloaded.  now it says can't access tty; job control turned off.  I have tried to do [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588), but the module piix is not found.  My laptop does not like linux :sad:.

---

### Post by dannyboy79 on 2007-08-16
WOW, you definitely have it bad. Why don't you try out Linux Mint or other distro's. I mean if you want to keep trying that's fine, there are TONS of soltutions for the tty error. I can only tell you to read the many pages on it either at the link you already posted or this link: [http://ubuntuforums.org/showthread.php?t=415009&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off](http://ubuntuforums.org/showthread.php?t=415009&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off)

---

### Post by mike6426 on 2007-08-16
I got it to work using [QUOTE=strikeback03]So I finally had some time to try a few of the suggestions. For me adding "all_generic_ide" to the line before booting from the LiveCD allowed me to boot. Don't remember if that tip was in this thread or not. Guessing from what scrolled by with quiet and splash turned off, the system was complaining about my built in card reader.[/QUOTE] from the thread that you pointed me to.  Thank you for the reference.  I'm installing Gutsy right now.

---

### Post by dannyboy79 on 2007-08-16
i am glad you got it working.

---

