---
title: "WiFi Driver issue"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by nurchi on 2011-06-09
Hello all

I installed Ubuntu 11.04 this morning for a computer that would be controlling a CNC.
Then I tried to install EMC2. Unsuccessful, after a couple hours I decided to just download their preinstalled CD image ([www.linuxcnc.org](www.linuxcnc.org))
They only provide LTS versions, so the latest one they have is 10.04

This is all fine except after installing 10.04, my WiFi stopped working.
It is a PCBOWAU2-N from "Patriot Memory" and it uses Realtek RTL8191SU chip.

I tried building the driver from sources, but not even sure where to start. Make {something} was my guess, but there doesn't seem to be anything reasonable for "make"

I was wondering if it is possible (and I am sure it is, just a matter of how) to insert a 11.04 CD, while 10.04 is installed and somehow grab the drivers from the CD.

Thanks.

---

### Post by walt.smith1960 on 2011-06-09
Hi

Does your dmesg output look similar to this? The bug mentions Ubuntu 10.10 but I'm quite sure it applies to 10.04 as well.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

The fix here is to simply create a folder 
/lib/firmware/RTL8192SU  then copy the downloaded firmware file into the newly 
created folder and restart.

---

### Post by Bucky Ball on 2011-06-09
Welcome to the forums and Ubuntu. Is this the page you have been looking at?

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

All you should need to do is open a terminal, get into the directory the drivers are in then:

```
sudo su
make
make install
```and you're done. The instructions are in a 'read me' file in the driver directory.

I am running 10.10 and everytime there's a kernel update I need to reinstall (Realtek but not same as your card). 10.04 LTS is the go (LTS recommended for production machines and long-term support until 2013) and you shouldn't have too many probs getting the drivers in.

BTW, have you connected with a cable and gotten your updates? That may provide you with something. System>Administration>Additional Drivers after the update?

---

### Post by walt.smith1960 on 2011-06-09
> **Bucky Ball said:**
> Welcome to the forums and Ubuntu. Is this the page you have been looking at?

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

All you should need to do is open a terminal, get into the directory the drivers are in then:

```
sudo su
make
make install
```and you're done. The instructions are in a 'read me' file in the driver directory.

I am running 10.10 and **everytime there's a kernel update I need to reinstall **(Realtek but not same as your card). 10.04 LTS is the go (LTS recommended for production machines and long-term support until 2013) and you shouldn't have too many probs getting the drivers in.

BTW, have you connected with a cable and gotten your updates? That may provide you with something. System>Administration>Additional Drivers after the update?

That's the advantage of inserting the firmware file vs. building and installing the driver.  Inserting the firmware is a one-shot deal, the fix is good regardless of kernel updates.  Of course the firmware fix will likely work only if error messages shown in dmesg are like those shown in the bug report.

---

### Post by Bucky Ball on 2011-06-09
How is this achieved, Walt?

---

### Post by walt.smith1960 on 2011-06-10
I don't have 10.04 running but I do have 10.10 and the steps are the same. Note that the rtl8192SU is supported "out of the box" by 11.04 and 11.10.

The first step is to create a new folder.  Using the GUI route,  from an administrative account terminal I do

[LIST=1]
[*]sudo gksu nautilus.  Use caution here because if you delete, rename or move the wrong thing you could break your installation. Places -> Computer -> File system -> lib -> firmware.  Create a new folder and label it "RTL8192SU".  There's already a folder labeled RTL8192SE present.
[*]I downloaded and extracted the required binary file "rtl8192sfw.bin" from launchpad librarian as recommended in the bug report.  If that file doesn't work for some reason, you can find what I believe is an updated version in the driver software from realtek.  Download and extract the files from the current RealTek software.  It's in a folder whose label I don't recall.  Look in the different folders and you'll find it.  I'll attach the .bin file I'm using here as well.
[*]Move or copy the binary file into the newly created RTL8192SU folder.
[/LIST]
Restart and you're done.  This can be accomplished more quickly via the command line. The steps are in the bug report referenced earlier.  This has worked for me on 3 different machines using TrendNet TEW-649UB adapters.  I hope this is of some help to you and others.

[ATTACH]194782[/ATTACH]

---

### Post by nurchi on 2011-06-10
I got it working.

I guess, connecting a cable and running all the updates made some difference.

After installing about ~300MB of updates (spanned as 2 separate update sessions each followed by a system restart), I got the drivers built.

I guess I knew nothing about how "make" worked. I had been trying to launch "Makefile" directly, getting all kinds of weird errors.
I even edited it and added #!/bin/bash/ as the first line, nothing worked until I read Bucky Ball's post.

I guess, this is what happens when you do all the development under windoze using a GUI... (I use an opensource one though)

Finally, after doing all that it still didn't work, but I tried ndis wrapper and the Windows driver and it just worked (did not work before the updates were applied).

I just wanted to thank everyone for your help and support.
Have the software running now, controlling a CNC machine.

P.S.
Bucky Ball, my Linux driver package from RealTek website did not have the instructions that you posted (from read me file); however another one did, can't remember which one though.

---

