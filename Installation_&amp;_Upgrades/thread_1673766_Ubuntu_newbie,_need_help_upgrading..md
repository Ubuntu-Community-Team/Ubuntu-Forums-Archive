---
title: "Ubuntu newbie, need help upgrading."
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by xWoodie on 2011-01-22
I'm having a hard time with a computer that was given to me yesterday.  I was able to wipe it out and put Ubuntu 8.04 LTS Desktop Edition.  I have explored a bit, but don't have the hang of this new operating system yet (I've always used Windows).  I would like to upgrade to the latest version of Ubuntu, but need help.  I'm not savvy with computers, but I am very interested in them and would love to learn more.

If anyone can provide any helpful links or tutorials, I would really appreciate it. :D



Note:  This was a free computer, so I'd like to learn about Ubuntu and get hands-on experience with it.  If I like it, I will use it on my better laptop.  I still don't know how to even get the latest versions of Java or Adobe Flash Player working yet. :-(


I'm brand new to this site, so I will check this post every 15 minute or so and hope someone ha information for me.

---

### Post by presence1960 on 2011-01-22
Your best bet is to do a clean install of either 10.04 or 10.10. Download the iso from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") and burn it as an image to disk. Then boot the CD and install.

---

### Post by xWoodie on 2011-01-22
> **presence1960 said:**
> Your best bet is to do a clean install of either 10.04 or 10.10. Download the iso from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") and burn it as an image to disk. Then boot the CD and install.
I know that from the BOOT menu, I can choose removable devices like USB drives.  Would I be able to use one of those in place of a CD?

---

### Post by kitchenguy on 2011-01-22
Yes, if you go to System --> Administration Startup --> Disk Creator, you can choose a USB thumb drive as a place to make a bootdisk and select the new image of Ubuntu to use.

It is really handy to have one on USB because when another computer breaks you can at least recover your data by booting with Linux and copying it - your friends will love you.

---

### Post by presence1960 on 2011-01-22
> **xWoodie said:**
> I know that from the BOOT menu, I can choose removable devices like USB drives.  Would I be able to use one of those in place of a CD?

YES if your BIOS supports booting from USB, which it seems to do since it has an USB entry in the boot menu.

---

### Post by xWoodie on 2011-01-22
> **kitchenguy said:**
> Yes, if you go to System --> Administration Startup --> Disk Creator, you can choose a USB thumb drive as a place to make a bootdisk and select the new image of Ubuntu to use.

It is really handy to have one on USB because when another computer breaks you can at least recover your data by booting with Linux and copying it - your friends will love you.
I read that on a Google link, but cannot find that application on my computer.  I think it's because I'm running 8.04.

---

### Post by kitchenguy on 2011-01-22
Apologies, I hoped that was not the case.  There was a solution to it here:

[http://ubuntuforums.org/showthread.php?t=1287540](http://ubuntuforums.org/showthread.php?t=1287540)

and you could substitute the newer version (10.10) for the version they are talking about (8.04).

You can always upgrade from the "Update Manager" System --> Administration.

You may need to set this.  In the Update manager click Settings and then go to the Updates tab and down the bottom there are settings for upgrades - select Normal Releases and then reload and check and apply the updates.

---

### Post by xWoodie on 2011-01-23
I'm using an HP Compaq nx9010, which I think is too old to boot from a USB stick.  I also cannot get it to boot from a CD first when I burn the io to one.   So....just re-install 8.04 and update?

---

### Post by kitchenguy on 2011-01-24
It has been a while since I used 8.04 but it should be fine.

When it is running you click on "System --> Administration --> Update Manager"

This brings up security updates etc as well as upgrades.  Select them all and click Install Updates (it will ask for your password).

The advice from [presence1960]("http://ubuntuforums.org/member.php?u=657448") is the best - by doing a clean install, but if you had issues doing that, then this is worth a try.  I am not much good with hardware but getting laptops to boot from CDRom can be hard, sometimes you need to hit the F12 key (or something similar, the splash screen right at the start should list the keys to use) to bring up a boot selection menu, from there you can choose your CD drive.

Also in your original post you mentioned flash player - there is a lot of info about this here

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) 

which will tell you how to get it going and there is also a link at the bottom for Java.

You can also go to [http://www.medibuntu.org/](http://www.medibuntu.org/) for additional stuff.

Good luck!

---

