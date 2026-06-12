---
title: "Ubuntu toshiba satellite a210 Failed to install Software &amp; Upgrade"
date: 2020-03-05
forum: Installation &amp; Upgrades
---

### Post by martintian on 2020-03-05
Hello ,


On my Toshiba satellite a210,  I can NOT upgrade the ubuntu version 
and install & update software. 


1) I try to upgrade to latest Ubuntu Version using USB stick, the system don't boot from USB, even I already configured the boot from USB  in the BIOS.
Looks like the laptop boot just ignores the USB stick.


I can do this successfully several years ago, at that time,   I installed Ubuntu Linux to replace windows.


2) I can not install any software, such as Opera browser, etc.. I
can't update  the Ubuntu software center. and when I try to install the software using command line, report defect packages.




$ uname -a
Linux joymartin-Satellite-A210 4.2.0-36-generic #42-Ubuntu SMP Thu May 12 22:03:27 UTC 2016 i686 athlon i686 GNU/Linux


joymartin@joymartin-Satellite-A210:~$ uname -v
#42-Ubuntu SMP Thu May 12 22:03:27 UTC 2016
joymartin@joymartin-Satellite-A210:~$  lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily


Thanks

---

### Post by CelticWarrior on 2020-03-05
Welcome.

Preamble:
Ubuntu 15.10 is EoL, end of life, not supported, since mid-2016. Yes, of course, you can't install additional software because the online repositories no longer exist and it seems that on top of that you also have broken packages, probably due to "experiments"... Your OS hasn't received any security update since 2016 and because of that it's very dangerous to use connected to the internet.

Any attempt to release upgrade is out of the question! You could have upgraded some time *after* the release of Ubuntu 16.04 (LTS, supported for 5 years) and *before* yours expired. Had you do that you wouldn't have this problem now.


What to do now:
Backup your personal files if you haven't done that yet (you should, of course). And then install from scratch a supported version, do not try an upgrade without formatting the root partition (if you have a separated /home it's fine, that can be reused although not really recommended because it also contains settings that you may no longer need and can create problems with newer software versions).
In order to install from scratch you need to boot installation media so, let's focus on that:

How did you make the installation media? And please post your hardware specifications.

---

### Post by crip720 on 2020-03-05
The OP seems to be having problems booting from USB stick, think someone will need to help with booting before he can upgrade as he tried to do.

---

### Post by CelticWarrior on 2020-03-05
> **crip720 said:**
> The OP seems to be having problems booting from USB stick, think someone will need to help with booting before he can upgrade as he tried to do.

Exactly. That's why I ended with that.

---

### Post by safaia on 2020-03-06
Yes, this is exactly the problem, can NOT boot from USB stick or external CD-Driver, looks like there are some setting 
in the installed UBUNTU which block to start from external equipment. I already setup to boot from USB stick in the BIOS,
but when start , it just ignore it, go straight to the harddisk boot. Because it can NOT boot from USB stick or external CD-ROM,
thus I can NOT reinstall any OS. I suspect is there is some specific setting in the installed UBUNTU OS.

---

### Post by CelticWarrior on 2020-03-06
@safaia, are you the same user as the OP? If so you shouldn't have duplicated accounts. Please contact the admins to fix that.
If not then you should open your own thread.

> looks like there are some setting in the installed UBUNTU which block to start from external equipment (...) I suspect is there is some specific setting in the installed UBUNTU OS

No, there isn't. This is completely wrong. Only users without the very basic understanding of the boot process would consider such an irrational hypotheses.
Actually, BIOS or UEFI, boots *before *any OS. Whether or not it can boot external installation or live media has nothing to do with the installed OSes or a blank drive. Keep that in mind for the future, otherwise you'll be always following troubleshooting dead-ends. Again, ***How did you make the installation media?***

---

### Post by safaia on 2020-03-06
I created a [create bootable Ubuntu Live USB]("http://ubuntuhandbook.org/index.php/2013/07/how-to-create-bootable-ubuntu-live-usb-with-unetbootin/") following the procedure at [http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/](http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/)
I can use this bootable Ubuntu Live USB to work as OS to start my [hp elitebook 840 laptop]("https://www.bing.com/search?q=hp+elitebook+840+laptop&FORM=R5FD"). But can NOT repeat the same things with this[h=2]Ubuntu toshiba satellite a210,[/h]This toshiba laptop just ignore my USB stick, bypass it and go to the harddisk OS directly. I missed some things ?

---

### Post by CelticWarrior on 2020-03-06
> **safaia said:**
> I created a [create bootable Ubuntu Live USB]("http://ubuntuhandbook.org/index.php/2013/07/how-to-create-bootable-ubuntu-live-usb-with-unetbootin/") following the procedure at [http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/](http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/)
I can use this bootable Ubuntu Live USB to work as OS to start my [hp elitebook 840 laptop]("https://www.bing.com/search?q=hp+elitebook+840+laptop&FORM=R5FD"). But can NOT repeat the same things with this**Ubuntu toshiba satellite a210,**

This toshiba laptop just ignore my USB stick, bypass it and go to the harddisk OS directly. I missed some things ?

According to that old guide you created a full Ubuntu installation in a USB stick ("install real Ubuntu OS USB drive"). This NOT the same as a live USB...

HP EliteBook 840 is a modern UEFI based computer;
Toshiba Satellite A210 is an old BIOS based computer.

An **installed OS** (not applicable to an actual live USB) **made for one won't work on the other**. There's a way to make it boot in UEFI and Legacy modes but I'm afraid it's too complex for even average users.

---

### Post by safaia on 2020-03-06
Thanks very much,
The problem is with [COLOR=#000000]Toshiba Satellite A210,[/COLOR]
1)Now I know I am wrong because I think the Live USB and Installation USB is same thing. On [COLOR=#000000]HP EliteBook 840, [/COLOR]Every time when I boot  with this Live Ubuntu USB, it asked me if I want to
install the OS, that make me think this Live USB can also be used to install the OS. I will follow the guide to generate a installation USB and retry. 
2) But on this [COLOR=#000000]Toshiba Satellite A210,
I also try to install OS such as [/COLOR]puppy linux, same things happened , just bypass the USB installation stick. I did use the same USB stick to install puppy linux on my [COLOR=#202124][FONT=&quot]Dell[/FONT][/COLOR][COLOR=#202124][FONT=&quot] Inspiron 1150 successfully.
[/FONT][/COLOR][COLOR=#202124][FONT=&quot]I will  create a installation UBUNTU usb stick and retry, hopefully this time will be OK. 
Thanks for all the help.[/FONT][/COLOR]

---

### Post by safaia on 2020-03-06
Hello CelticWarrior ,
Thanks for the advice. will follow and correct it.

---

### Post by safaia on 2020-03-06
On [h=2]toshiba satellite a210,  I failed to upgrade the current OS 15.10 to new version.[/h]1) If run the command :

/usr/lib/dpkg/methods/update/update -manager -d
get a lot of 404 error messages such as```

W: Failed to fetch mirror://[mirrors.ubuntu.com/mirrors.txt/dists/wily-updates/restricted/binary-i386/Packages]("http://mirrors.ubuntu.com/mirrors.txt/dists/wily-updates/restricted/binary-i386/Packages")  404  Not Found [Mirror: [http://ubuntu.mirror.globo.tech]("http://ubuntu.mirror.globo.tech/")
```
2)  If run the update from GUI, ```

error message" Failed to download repository information, check your internet connection.
```
( Note: the internet is OK, I can browser  the website)
```

Satellite-A210:# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily
```

---

### Post by CatKiller on 2020-03-06
15.10 hasn't been supported for nearly 4 years. The repositories are long gone. The time to upgrade from it was Spring 2016. Do a fresh install of a supported LTS release.

---

### Post by mörgæs on 2020-03-07
Why are you creating another thread?

If it's difficult to boot from USB one can also boot from CD. See the *old hardware* link for more information. 

Don't install Ubuntu on a Satellite A210. X/Lubuntu 19.10 is a better option.

---

### Post by Impavidus on 2020-03-07
15.10 has been long dead. Its successor, 16.04, isn't dead yet, but is old. Such an upgrade isn't recommended. It's better to use a fresh install of 18.04 or 19.10, the latter if you want to move on to 20.04 soon after its release.

Furthermore, your output refers to something-i386, suggesting you run a 32 bit system. Support for 32 bit systems is rapidly falling. You can't upgrade a 32 bit system to 64 bit, so that means a fresh install. Ubuntu 18.04 is the last Ubuntu release still supporting 32 bit systems. Google tells me that your laptop came with 2GiB memory and supports up to 4GiB. The lighter flavours of 18.04 and 19.10 will be happy with 2GiB of memory, but you may wish to increase it to the max anyway.

---

### Post by guiverc on 2020-03-07
I'll provide

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Yes release-upgrading is an option if you switch your `archive.ubuntu.com` to `old-releases.ubuntu.com`, fully upgrade your system before opting to `do-release-upgrade`, but I'd re-install using 'Something-else', use your existing partitions but not format them as it's far faster and it allows you to skip releases (ie. you can re-install 18.04 in a single step, instead of needing two jumps, ie. the release-upgrade to 16.04, reboot then the next release-upgrade to 18.04, both release-upgrades will take longer than the single re-install).

---

### Post by coffeecat on 2020-03-07
@martintian/safaia, no cross-posting please. Multiple threads about the same issue cause confusion and dilute community effort. I have merged your two threads, so that those helping can see what others have advised.

I have also disabled the martintian account which you had already managed to half-disable anyway by changing the email and not re-activating.

Lastly, I have edited your first post in the second thread, now post #11 in this merged thread, to remove spurious non-standard fonts, and to include BBCode code tags. Please use code tags for terminal output (link in my sig if you need it) for clarity. You lose columnar spacing if you paste directly into the body of your post, and non-standard fonts make this even more difficult to read.

---

