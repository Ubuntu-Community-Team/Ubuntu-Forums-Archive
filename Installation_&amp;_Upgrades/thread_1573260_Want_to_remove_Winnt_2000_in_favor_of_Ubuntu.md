---
title: "Want to remove Winnt 2000 in favor of Ubuntu"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by cam1498 on 2010-09-12
I have an old win2000 machine for basic needs / web access etc. for my kids to learn on. The machine was trashed by a virus, which I scrubbed but left the machine in disarray. (getting access denied on a lot of shortcuts like my computer etc..)
 
I have nothing important left on the box so I thought my best bet would be to trash windows altogether in favor of linux. I would like to do the whole thing online if possible instead of getting install cd's. 
 
(I tried creating a dual boot with a usb stick, It's NG because of the access denied issue)
 
I am a newbee to Linux. I do have some tech skills. I am a software tester so I'm not afraid of experimenting.
 
If I get this right, my company has other "useless" machines that I may be able to salvage this way for donation to schools in my area.
 
(750mb ram plenty of hd space)

---

### Post by Joe of loath on 2010-09-12
There's no online install for Ubuntu as such, unlike Debian which can do a netinstall. However, that still requires an install CD.

Just download the install iso, burn it to CD and install it :) Alternatively, you can make an install USB stick (Don't bother with dual boot USB's, too much trouble) and install from that.

---

### Post by Rubi1200 on 2010-09-12
Personally, I recommend downloading and burning to CD the latest Ubuntu version.

First test it as a LiveCD to make sure everything is compatible with your hardware.

Then, use the partitioning tool on the CD, called GParted, to wipe the drive clean, preparing it for Ubuntu.

Run the Ubuntu installer, remove the CD, reboot and voila!

Here are some links that may help:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://ohioloco.ubuntuforums.org/showthread.php?t=801404](http://ohioloco.ubuntuforums.org/showthread.php?t=801404)
[https://help.ubuntu.com/community/Beginners/FAQ](https://help.ubuntu.com/community/Beginners/FAQ)

Good luck!

---

### Post by rory526 on 2010-09-12
hi.
Xubuntu might run a little better with 750Mb memory than Ubuntu.
It's the same operating system with a lighter graphical user interface.

I'm not sure what you mean by doing it online. The usual way is to download and burn the install cd and then boot from it and install.

Please correct me if I've misunderstood.

The Xubuntu install cd is available here: [http://www.xubuntu.org/getubuntu#lucid]("http://www.xubuntu.org/getubuntu#lucid")

Also, burn the disk at the slowest speed available.

---

### Post by cam1498 on 2010-09-12
Thanks for the quick responses. 
I should have added that I wish not to burn to cd. The machine I'm dealing with doesn't have a burner so that means a bunch of back and forthing between machines which I'm tryin to avoid but if I have to, oh well.
 
To prove what a lightweight I am, I thought Ubuntu was light enough for this machine.
 
Thanks again people.

---

### Post by Joe of loath on 2010-09-12
Regular ubuntu would run fine on 750mb, our main desktop has that much memory and it's fine.

Can it boot from USB?

---

### Post by rory526 on 2010-09-12
> **Joe of loath said:**
> Regular ubuntu would run fine on 750mb, our main desktop has that much memory and it's fine.

Can it boot from USB?

I'm using 931mb with just firefox running. The recommended system requirements for 10.04 are 1Gb of RAM.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Joe of loath, I think you might be using an older version of Ubuntu, am I right? 

Ubuntu 8.04 only requires 384MB. I'm unsure for how long more it will be supported, but it might be a good solution here maybe.

p.s. It's supported until April 2011. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Joe of loath on 2010-09-13
I think you have something wrong, I'm running 10.04 with FF and banshee (two biggest memory hogs ever), and I'm using less than 600mb. A clean boot uses about 300mb.

---

### Post by cam1498 on 2010-09-13
Yes I can boot from a usb - how big a stick and what should I use?

---

### Post by Joe of loath on 2010-09-13
Any stick bigger than 1gb will work.

What you'll want to do is download the iso image and also download unetbootin for windows. Open unetbootin with the USB stick plugged in, browse for the iso, and click the button to extract the iso to the USB stick. It should then boot from USB, although it won't be persistent like if you'd used the USB creator from inside ubuntu.

---

### Post by mörgæs on 2010-09-13
On such a machine Lubuntu would be a good choice:

[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

Xubuntu is not much lighter than a regular Ubuntu.

---

