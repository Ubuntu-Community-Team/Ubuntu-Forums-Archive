---
title: "Install CD leaves me with no display"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by greenmaze on 2006-11-04
I'm trying to install edgy from the CD, but no matter what boot options I use(safe graphics, vga=771, noapci, nolapci), I'm left with no display. I can tell the computer boots into the live system because I can hear the melody that's played when the desktop normally appears. This leads me to believe there's just something wrong with the screen size or refresh rate.

After hearing the boot up melody, I press ctrl-alt-F1 and I then run the command "sudo dpkg-reconfigure xserver-xorg". Everything seems to detect ok so I run the command "startx". I receive an error stating that the server is already running. Is there a way to stop the server (I tried ctrl-alt-backspace) so I can restart X with the new configuration?

Thanks

---

### Post by senior on 2006-11-04
Hi Greenmaze,

Use after start-up 

Alt +Ctrl   and -

to alter screensize 
Success,
Senior

---

### Post by greenmaze on 2006-11-05
Thanks, but that didn't work.

I ended up installing from the alternate CD in text mode, but I've run into the same problem. I get a blank screen upon boot. I can hear the melody that's played at the logon screen so I know it's not locked up.

I've searched the forms for similar issues, but I've not been able to find anything that helps me.

Being that I have a Nvidia graphics card, I figured I try to install the drivers via the command line. The problem I run into when trying to install the drivers is that "apt-get install ..." wants to use the CD instead of downloading from the internet. It asks to have the CD inserted into the CDROM and press enter, but when I do, it just keeps asking for the CD to be inserted into the CDROM. My internet connection is working because I can do "apt-get update". Is there a way to have "apt-get install" use the internet repositories insead of using the CDROM?

---

### Post by taurus on 2006-11-05
1.  Boot your machine into recover mode from GRUB and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Reboot and see what happens.

2.  If you don't want to use your CD-ROM, then you need to edit your /etc/apt/sources.list and comment out the first line in it by placing a # in front of it.  May as well do it from the recover mode too...

```
nano -Bw /etc/apt/sources.list
```

---

### Post by greenmaze on 2006-11-05
Thanks for the info.

I was finally able to get my video working correctly following the instructions on the following link.

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

For people who run into the same problem and find this posting, the instructions on [http://ubuntuguide.org](http://ubuntuguide.org) didn't work for me.

---

