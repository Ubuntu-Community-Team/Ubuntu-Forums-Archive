---
title: "Installing Ubuntu 7.10 with 8800GT"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by vonfeldt7 on 2007-12-15
I have looked into several threads on this very topic, but not found an answer to my problem. I want to install Ubuntu 7.10 with my 8800GT, but the drivers on the live cd are too old (I'm told I need [these drivers]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html")) and to install them once I get Ubuntu 7.10 installed...the problem however, is that I can't even get Ubuntu installed. Is there anyway that I can update the drivers on the live cd or something like that? 

What exactly needs to be done here? Thanks.

*EDIT* Nevermind, I got it to work.

---

### Post by src2206 on 2007-12-16
Could you please share how did you solve your problem? As that will help other with similar problem as yours.

---

### Post by notaphish on 2008-01-09
Changed to low-video mode and 800x600 resolution and it allowed me to get into the live cd.

Now the only problem is that the card is not yet supported by a restricted driver or by Envy.

---

### Post by or1on on 2008-01-09
just download the driver from nvidia and make sure u have your kernal sources gcc and build-essential files installed, then ctrl+alt+f1 login in to cmd line and kill the gui sudo /etc/init.d/gdm stop verify its down ctrl+alt+f7 if blank screen then go back to f1 screen and cd to where u downloaded the nvidia driver and sudo sh nvidiadriver name and follow the onscreen directions once done do a sudo modprobe nvidia and then type startx if u see an nvidia logo b4 your login screen then ur set

---

### Post by papatrpt89 on 2008-01-11
> **or1on said:**
> just download the driver from nvidia and make sure u have your kernal sources gcc and build-essential files installed, then ctrl+alt+f1 login in to cmd line and kill the gui sudo /etc/init.d/gdm stop verify its down ctrl+alt+f7 if blank screen then go back to f1 screen and cd to where u downloaded the nvidia driver and sudo sh nvidiadriver name and follow the onscreen directions once done do a sudo modprobe nvidia and then type startx if u see an nvidia logo b4 your login screen then ur set


Or1ion, I based the start of a howto on your guide here.  It is located at [http://ubuntuforums.org/showthread.php?p=4119312](http://ubuntuforums.org/showthread.php?p=4119312)

Thanks for this!  I will be updating my guide as I get experience with installing it (I just helped a friend build a PC with dual 8800GT cards).  If anyone has any experience, please post!

I am especially curious as to how the SLI part of things will work.

---

### Post by zurn on 2008-01-11
I was able to install it using the Ubuntu alternate cd.

Go here
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and check the box "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer"

---

### Post by Boichot1956 on 2008-01-16
I had trouble with the Live CD of Ubuntu and I couldn't get it to run from my laptop.  I tried using keys F2, F9, F10, F11, F12, Del key and Alt +F10.  I couldn't get the Bios up or boot the Live CD.  I finally had to download Ubuntu 7.10 Alternate Desktop CD.  I wanted to keep Windows 2000 on the laptop and put Ubuntu on my USB Flash Drive Memory stick.  I was going to do this with the live cd.  Can I still do this with the alternate desktop cd?  I need to know how to do this if I can.  Please contact me as soon as possible.  I really do not want to delete windows2000.  I want to be able to use both programs.  I also was thinking about duel booting or booting from USB Flash Drive.  But because I can't get into my Bios I have to do a duel boot and pick the program that I want to run at that time.  Please help me.  I know how to do this on a Desktop computer but not on a laptop.  Please help me.  I decided to come to you for help.  I love Linux programs and that got me very interested in Unbuntu Linux.  I think I can do this and I really think I will love this program once I get.  Can you also help me if I need help when I go to play my favorite radio station online at [www.wvmv.com](www.wvmv.com) and I can't hear it?  It runs on windows media.  I know that there is a way to do it on Fire Fox but there is something I have to do.  Please help me get Ubuntu Linux on my laptop.  Do you also have classes or lessons on using Ubuntu 7.10 Gutsy Gibbon.  I am very gutsy but I don't want to accidentally arase Windows 2000 when I am not ready to yet.  If I have to just let me know what files I should back up just in case I accidentally arase what I need.

Thank you,

Vickie

---

### Post by bobetko on 2008-01-17
I did everything that needed to be done... and it doesn't work.

I  installed NVIDIA drivers (10.14.19)... everything seems OK, but when I so startx I get Fatal Server Error: no screens found. If I do sudo /etc/init.d/gdm start, I get message that ubuntu will start in low-graphic mode?
So, what I am doing wrong?

Thanks

---

### Post by owlgorithm on 2008-01-21
I just clean-installed Ubuntu 7.10 using the Alternate Desktop CD. I followed the directions given above, but I did have to install libc6-dev using Synaptic because the nVidia installer said it couldn't find my libc libraries -- I had libc6 installed by default but this apparently upgraded some of the components in a way that nVidia's installer liked. Everything appears to be working normally.

---

### Post by uterrorista on 2008-02-16
Is anyway to install Ubuntu 7.10 (with 8800GT) without using the Alternate CD ?

---

### Post by benste on 2008-02-16
You should run the live CD in low graphics mode-
[than use envy (http://albertomilone.com/nvidia_scripts1.html)]("http://albertomilone.com/nvidia_scripts1.html")
to install the Nvidia driver - works fine on the PC of my brother

---

