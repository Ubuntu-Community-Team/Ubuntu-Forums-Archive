---
title: "Trouble installing from USB drive."
date: 2016-04-14
forum: Installation &amp; Upgrades
---

### Post by neil40 on 2016-04-14
I have an old asas eeepc 900 and following discussion in another thread [http://ubuntuforums.org/showthread.php?t=2320383](http://ubuntuforums.org/showthread.php?t=2320383)
I was able to get my machine to boot from an usb pen drive.
The pendrive was prepared using Startup disk Creator and I am attempting to install the 32 bit Trusty Tahr version. 32bit image
I have performed the ISO download and preparation of the pen drive twice to no avail
i first of all ge the message

menuc32 : not a CPM32R image
Pressing tab as googled advice suggests produces a list

unetboot indefault ubnentry0 and similar ones to ubnentry5

working thgouth to ubnentry1 that did do something in that it took me through to a new version of  Ubuntu
It did not install though as rebooting took me back to 12:10 my old version.

What am I doing wrong and how to I fix it?

---

### Post by oldfred on 2016-04-14
Are you trying to use Ubuntu or Lubuntu.
Full Ubuntu on old or lightweight systems is not recommended. Pretty much need 2GB of RAM and better video card/chip to run Ubuntu.
 [http://lubuntu.net/](http://lubuntu.net/)

---

### Post by neil40 on 2016-04-14
Does that make any difference to the problem though? I won't be running this machine at full power. I need to have the most mainstream and the most up-to-date system. Upgrading things is a problem. It doesn't have a working screen for example and will be used as a machine for a special project.
It will be mostly running scripts and holding files. but I need to upgrade it so help solving the problem is most welcome

I find if I use less mainstream systems I can't get help when I want it.

---

### Post by oldfred on 2016-04-14
If you want a server version, then not sure if any real difference.
It is just the gui with Ubuntu will be so slow as to be unusable, where Lubuntu should be fine. My old laptop, I did use Ubuntu but immediately installed fallback or gnome-panel which then worked well.

---

### Post by mörgæs on 2016-04-15
> **neil40 said:**
> 
I find if I use less mainstream systems I can't get help when I want it.

Why do you think so? Here you will get help using anything in the Buntu family, sometimes also when using other distros.

---

### Post by neil40 on 2016-04-15
> **mörgæs said:**
> Why do you think so? Here you will get help using anything in the Buntu family, sometimes also when using other distros.


The answer is rather obvious as even here I have aksed a question and got no real help with it at all.
For reference I have managed to get Lubuntu installed what ever is causing the problem doesn't happen with that BUT and it is a really big BUT it doesn't do what I want and there are bits missing from it that I cannot easily get installed that prevent me from doing what I want to do.
So what I would like is for someone with expertise to look at my original problem and help me solve it.
Ubuntu will not install. Lubuntu will be is useless. There has got to be some problem with Ubuntu in regards to my system.
I have now downloaded the image and put it on the USB drive THREE TIMES and tried every option offered on the menu.

---

### Post by oldfred on 2016-04-15
If you have it installed, then this thread is solved.

But you have not said what your other issues are so we cannot help. 
But any issue other than installing Lubuntu should be in a thread with issue in title.

The repository for Lubuntu & Ubuntu are the same, so any missing bits are available either way.

---

### Post by neil40 on 2016-04-15
I have to say I am feeling rather frustrated. **The problem is not solved. **I have not been able to perform the installation that I wanted to perform. I think it is reasonable to say that when someone replies saying a problem IS solved and it isn't that they haven't been reading too diligently. I again appeal for help in solving the problem as I orignally asked it. There seems to be a faction here that is promoting Lubuntu for what ever reason. I don't want Lubuntu I want Ubuntu that is what i asked for. We have had umpteen replies but none that are on-topic and helping me to solve the problem. So can I have some help please!

---

### Post by LukeMorrison on 2016-04-15
As someone who has used Ubuntu on a netbook with somewhat better specs (1.6 Ghz processor, 2 GB RAM), it still struggled with Ubuntu.  I then installed Xubuntu on it with better results.  Which pieces of Ubuntu are you missing?  We may be able to help you install those parts.

---

### Post by sudodus on 2016-04-15
eeepc 900 does not have enough horsepower for standard Ubuntu because of the desktop environment. It might work, but rather slowly.

Xubuntu and Ubuntu MATE are two flavours of Ubuntu with medium light desktop environments, XFCE and MATE.

Lubuntu is a flavour of Ubuntu with an ultra-light desktop environment, LXDE.

This is the reason that we recommend these flavours (instead of standard Ubuntu). I am helping a friend to maintain Xubuntu on that very model (eeepc 900). It works well for him, It would be faster (for example playing video better) with Lubuntu, but Xubuntu is better for him.

-o-

The error output you state in your first post indicates problems due to a mismatch between Unetbootin and the version of Ubuntu, that you want to install. I would recommend [mkusb](https://help.ubuntu.com/community/mkusb) in linux or [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) in Windows. These tools ***clone*** the iso file, and that method is very robust.

See the following link and links from it for more details: [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by neil40 on 2016-04-16
> **sudodus said:**
> eeepc 900 does not have enough horsepower for standard Ubuntu because of the desktop environment. It might work, but rather slowly.

Xubuntu and Ubuntu MATE are two flavours of Ubuntu with medium light desktop environments, XFCE and MATE.

Lubuntu is a flavour of Ubuntu with an ultra-light desktop environment, LXDE.

This is the reason that we recommend these flavours (instead of standard Ubuntu). I am helping a friend to maintain Xubuntu on that very model (eeepc 900). It works well for him, It would be faster (for example playing video better) with Lubuntu, but Xubuntu is better for him.

-o-

The error output you state in your first post indicates problems due to a mismatch between Unetbootin and the version of Ubuntu, that you want to install. I would recommend [mkusb]("https://help.ubuntu.com/community/mkusb") in linux or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows. These tools ***clone*** the iso file, and that method is very robust.

See the following link and links from it for more details: [Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Thank you. That worked for me. I used mkusb on my other Ubuntu machine which I am using to type this. As for performance that is fine for what I want it for. As a test it is playing some music on youtube for me perfectly well. It is fast enough for what I want. In fact I don't see it as slow at all. I now need to install the stuff I need to run on it. The one thing is that you have to be careful which USB port you put the drive as the BIOS doesn't bring up the correct options unless you have the right one as I document in the other thread mentioned at the start of this one. To err is human but to really foul things up you need a computer.  :-)

---

### Post by sudodus on 2016-04-16
Congratulations to a working system :KS

Please ask here if you have more questions about installing. Otherwise, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

I will look at your other thread, and you are welcome to create new threads if/when you need help with another problem.

---

