---
title: "Installation question"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Spleeny on 2008-05-13
Hello all,

I am a total noob at this.  I've got the xubuntu-7.10-desktop-i386 iso burned and it boots fine on my Toshiba A105-S2061 laptop.  (There's no sound and no wireless, but I would figure I could work with that once I had it installed.)

The problem is that I can't get it installed in the first place - I click the Install button, and the installation goes fine until it gets to 15% at the "Installing system" window, during the "Detecting file systems..." stage.  Any clue why?

Thanks in advance for any help!

---

### Post by Rocket2DMn on 2008-05-13
Sounds like it's not picking up your hard drive.  However, you should install the latest version of Xubuntu, 8.04 Hardy Heron - [http://xubuntu.org/get](http://xubuntu.org/get)
Before you burn the disc, check the md5sum, then burn at a slow speed like 4x to help prevent write errors
[HowTo md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")
To find the hash to check the md5sum against for Xubuntu, you need to check the file called MD5SUMS which is available at the mirror you download from ( ex: [http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/) )
Xubuntu hashes are not posted on the Ubuntu Hashes page.

---

### Post by Spleeny on 2008-05-13
Excellent, I'll try that.  Thanks for the quick response!

---

