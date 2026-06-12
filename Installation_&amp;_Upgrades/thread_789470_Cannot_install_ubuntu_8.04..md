---
title: "Cannot install ubuntu 8.04."
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Surma on 2008-05-10
I'm trying to install Ubuntu 8.04. After I hit install Ubuntu on the live CD it says loading kernel and then it takes me to a black screen with a cursor in the upper left. But now I tried to start up windows and I get an OS option screen, I tried Ubuntu but the same thing happened without the loading kernel box. So then I tried to start windows and I couldn't get past the login screen. I think the problem may be that I'm using up too much hard-disk space having windows and Ubuntu on it. My computer has about 390 megabytes of RAM and 7 gigs of hard drive space. If windows is taking up all that space and preventing Ubuntu from running do you know how to uninstall windows without being in an OS?

---

### Post by Pumalite on 2008-05-10
What kind of Windows are you running?
Post:
sudo fdisk -l

---

### Post by Surma on 2008-05-10
Windows 2000.

---

### Post by Pumalite on 2008-05-10
Get Gparted Live CD and shrink Windows, then install Ubuntu.

---

### Post by Surma on 2008-05-10
I don't want windows at all because it doesn't work with my graphics tablet.  And even if I wanted it I would want to get a different windows like XP if I get a better computer and wanted to play games.

---

### Post by Pumalite on 2008-05-10
Then use Gparted Live CD to make a large partition of your whole drive, formatted ext3 and install Ubuntu; Guided>Use Entire Disk.

---

### Post by Surma on 2008-05-10
Is there any other way? because 2 diffferent cd burners can't recognize my cd's.  Yes my CD drive is writable

---

### Post by Pumalite on 2008-05-10
Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on good quality CD-R, check CD integrity before install. Clean the lens in your burner, just in case. Other possibilities:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by Surma on 2008-05-10
I meant on gparted.  I bought my CD from a recommended site.

---

### Post by kevinl on 2008-05-10
I have placed a post around 7 hours ago about the same problem with Ubuntu on a VIA EPIA-EX attempting to load both 7.x and 8.x Ubuntu.  It is likely the problem is an incompatibility with the video display you are using.

There are many things that will cause a "black-out" and once it happens, the installation cannot proceed (obviously!).  My suggestion to the Ubuntu folk is that they delay to the last moment the loading of the video drivers and, when they are being installed, ask the user to confirm they work.  Where they don't work, the installation should try to determine the video adaptor and then refer to the latest list of websites supporting a Linux driver for that piece of hardware.  Once again, there is the need for the user to be able to intervene and say the mod-probe had got it wrong when detecting the hardware and this notification should be sent automatically by email if the person has the computer connected to the Internet to the area within Ubuntu that handles these types of matters.  In that way the architects of Ubuntu get good feedback as to whether there are problems with the mod-probe; an essential bit of software for detecting the hardware makeup within the PC.  If it doesn't work well then people will soon become disappointed when trying to install Ubuntu.

---

### Post by Pumalite on 2008-05-10
My impression is that he is saying that his burner doesn't read the CD. Different from booting and ending up with a blank screen.

---

### Post by Surma on 2008-05-10
I can barely even get past the install screen.  Plus it doesn't black out it has a cursor blinking in the upper left.

---

### Post by Pumalite on 2008-05-10
Try your luck with the gparted in the Live CD if you can boot it. I'd check the burner.

---

### Post by Surma on 2008-05-10
My writable CD-ROM drive (which is on the computer I'm using atm) cannot read the blank CD's I'm putting in it.  So I can't burn the GParted live CD.  My computer's (the one I'm trying to put Ubuntu on and doesn't have a writable drive) CD drive can read the Ubuntu CD fine.

---

