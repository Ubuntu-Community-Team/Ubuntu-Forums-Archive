---
title: "Ubuntu On Acer Aspire One Cloudbook 14."
date: 2015-12-09
forum: Installation &amp; Upgrades
---

### Post by juan53 on 2015-12-09
Hi
I've purchased a brand new Cloudbook 14 in order to wipe out Wos10 and to install Ubuntu, but I have an issue during the installation.
Stepts I tried:
Of course I got a x64 Ubuntu ISO
I loaded it into a USB CDROM unit.
I changed rebooting order.
I changed UEFI mode to Legacy.
I rebooted the laptop.
The instalation by default started, but when ISO extraction ends, nothing else happens. The instalation freezes without showing any dialog.

Then I restored comuter.
I entered again into BIOS, I changed legacy mode to UEFI mode, and then, I added a password in order to disable safety reboot.
Then I tried to install by default again.
Same result, the instalation freezes without showing any dialog.

I guess Microsoft again is playing naughtily.
Could you please help me? Thanks a lot, for your time and effort.

---

### Post by sudodus on 2015-12-10
Welcome to the Ubuntu Forums :-)

You wrote 'The instalation by default started, but when ISO extraction ends, nothing else happens.'

- Please describe ***in detail*** what you see on the screen! This will help us understand what is happening.

-o-

- Are you able to run a live session 'Try Ubuntu'?
- Have you checked with md5sum, that the download was good?
- How did you create the DVD disk?
- Did you check that the DVD disk is good (the checksum of all the installed files)?

Maybe there are problems with the driver for your graphics.

- What is your graphics chip/card?

---

### Post by juan53 on 2015-12-10
Actually I'm triying to install a recogniced variant of Ubuntu, Ubuntu-mate.
When I put de disk into the CDROM and reboot the laptop, a gray screen is shown. In this screen, you can see a keyboard logo. If you press any key, a menu appears with the options: try without installing, install ubuntu-mate, check installation disk...
I tried both of two options: try without installing and install ubuntu-mate. When any of both options are selected, CDROM starts his job and another screen with the logo and some dots is shown. In that point, after some seconds of "progress", the process stops, frozen in that screen. No instalation dialog appeared, and nothing else happens. Then I have to reboot in a rude manner.
I checked the disk, and it's O.K., also checked md5 and it's correct too.
I create the disk using Windows10 ISO burning.
The graphic card is integrated in the motherboard, which is Intel made. The laptop has not been modiffied. You can check out all the technical data in this link (from Acer store):
[http://us.acer.com/ac/en/US/content/model/NX.SHGAA.003](http://us.acer.com/ac/en/US/content/model/NX.SHGAA.003)

I wrote about this problem in this foro, because I understand that this issue is common to both distros.
Thanks for answering =)

---

### Post by sudodus on 2015-12-10
I suspect problems with the graphics (or less likely with the wifi). Usually Intel graphics work well, but some new intel graphics chips need a boot option, or if it is very new, need the newest version of Ubuntu to get the newest kernel and its hardware drivers.

So you could try [Ubuntu-MATE 15.10](http://cdimage.ubuntu.com/ubuntu-mate/releases/15.10/release/) or even the next version (which is in an early development stage), [Ubuntu MATE Xenial Xerus](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/108452/downloads) to become the next LTS release 16.04 in April.

---

### Post by juan53 on 2015-12-10
The version I tried is Ubuntu 15.10, but I am going to try to install 16.04 version, and I'll give you back a feedback.
Thanks for answering =)

---

### Post by sudodus on 2015-12-10
If Ubuntu MATE Xenial Xerus (to become the next LTS release 16.04 in April) does not work, you should try some boot options. See these links

[Is the computer running in UEFI mode or in classical BIOS mode?](http://ubuntuforums.org/showthread.php?t=2230389&p=13370798#post13370798)

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

See this link to [a post by *oldfred* for details about boot options for Intel graphics](http://ubuntuforums.org/showthread.php?t=2305646&p=13403459#post13403459)

---

### Post by juan53 on 2015-12-12
Well, after trying present and past versions of Ubuntu Mate and Ubuntu, I realize that those don't fit. I'm not and advanced user and I don't see myself mitigating stability errors. So I decided to wait to the final release of v16.04.
Users of this model can install if they wish Linux Mint 17.3 (I don't pretend to make publicity of other distros, but showing, at least, a provisional solution.
Thanks for your time, atention and effort.

---

### Post by Den_S. on 2015-12-25
Look here: [https://wiki.archlinux.org/index.php/Acer_Cloudbook](https://wiki.archlinux.org/index.php/Acer_Cloudbook)

I've tried those kernel parameters with 15.10 and it's working beautifully.

---

### Post by nicolas.bernaerts on 2015-12-30
I've gone thru the same trouble while installing Ubuntu 15.10 on the Acer Aspire One Cloudbook 431.

I've succeeded to run it after some UEFI tweaks.
These are explained on my blog : [http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)

As a result, Ubuntu is running very smoothly on this little laptop.
Bye bye Windows ...

---

### Post by ken75 on 2016-04-04
I was looking at purchasing the Acer Aspire One Cloudbook 431 and installing Ubuntu 15.10 on it and came across your detailed article explaining the installation process via UEFI but was curious as to whether or not you had tested the Bluetooth stack yet and if so was it compatible "out of the box" or was there additional configuration needed?
[COLOR=#222222][FONT=Verdana]> **nicolas.bernaerts said:**
> I've gone thru the same trouble while installing Ubuntu 15.10 on the Acer Aspire One Cloudbook 431.[/FONT][/COLOR]

I've succeeded to run it after some UEFI tweaks.
These are explained on my blog : [http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)

As a result, Ubuntu is running very smoothly on this little laptop.
Bye bye Windows ...

---

