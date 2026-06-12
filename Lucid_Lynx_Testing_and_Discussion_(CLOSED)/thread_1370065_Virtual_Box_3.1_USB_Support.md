---
title: "Virtual Box 3.1 USB Support"
date: 2010-01-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by FatalChaos on 2010-01-01
Has anyone gotten USB support working? USB automounting and w/e works fine on lucid lynx for me, but my virtual box (windows XP) guest can't mount my usb external hd. I have the guest additions installed, and added myself to the vbox user group.

---

### Post by Menthu_Rae on 2010-01-01
Have you checked under disk management to make sure the drive is being assigned a drive letter?

Right click my computer > manage > disk management > right click on drive > assign drive letter.

---

### Post by xebian on 2010-01-01
You need to get the debs direct from Virtualbox.org to get USB support.  The repos version does not.

---

### Post by kevpan815 on 2010-01-01
I Will try it out tomorrow.

---

### Post by Gina on 2010-01-02
Yes, you need the PUEL version (Personal Use End Licence or something) rather than the open-source verson.  This has to be downloaded fron their website.  I have this version working fine with USB in 9.04 (Jaunty) and XP as guest.  Only problem I have is with LAN support which seems to die with one app I'm using.

---

### Post by FatalChaos on 2010-01-02
The version I have installed is the PUEL version, I installed vbox from the sun repository. I don't think it has to do w/ assigning the drive a letter, nothing appears in the devices->usb section. At one point I got an error saying it couldn't find hal or usbfs support, but that error appeared once and hasn't appeared since.

---

### Post by cariboo on 2010-01-02
Have you got the guest additions installed? When you have vbox running go to the Devices menu and select Install Guest Additions.

---

### Post by Seventh Reign on 2010-01-02
USB Support in VBox is hit or miss.  It works great one day, you reboot and the next day it doesnt work at all.  There is no rhyme or reason for it.  It just works when it wants.

---

### Post by portis on 2010-01-24
This could be due to a kernel problem.
usbfs seems to be disabled in recent kernels.
see this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507824)

---

### Post by nanog on 2010-01-25
> USB Support in VBox is hit or miss. It works great one day, you reboot and the next day it doesnt work at all. There is no rhyme or reason for it. It just works when it wants.
I've never had a problem with usb support that reading the virtualbox user manual could not fix. 


virtualbox has not used the usbfs for recent kernels for some time.  perhaps this has something to do with hal being deprecated.

---

### Post by moviemaniac on 2010-01-25
USB initially didn't work for me in lucid too - all I had to do (amd have to do every time prior to a reboot due to some bug) is to attach my user to the "vboxusers" group.

---

### Post by nanog on 2010-01-25
Vbox developers are working on a usb fix for 10.04. It seems they are using hal to manage usb devices (/dev/bus/usb). Deprecation of hal in 10.04 caused usb to break. Reinstallation of hal does not fix this problem because hal is now being run differently in 10.04.

[http://forums.virtualbox.org/viewtopic.php?f=7&t=27181](http://forums.virtualbox.org/viewtopic.php?f=7&t=27181)

[http://www.virtualbox.org/ticket/5996](http://www.virtualbox.org/ticket/5996)

---

### Post by erkiha on 2010-02-18
it is possible to use usb in lucid on vbox by running:
```

hald --daemon=no

```
in terminal before vbox.

---

### Post by portis on 2010-02-19
Thanks, it works.

> **erkiha said:**
> it is possible to use usb in lucid on vbox by running:
```

hald --daemon=no

```
in terminal before vbox.

---

### Post by nanog on 2010-02-20
erikha, thanks from me too.

---

### Post by SeePU on 2010-03-01
Did you (guys) install VirtualBox in Lucid?

I am wondering if you did but if so, then which edition did you choose?

Karmic 9.10 ed. or 'Linux x86' (or 64-bit) ed.?

---

### Post by erkiha on 2010-03-01
I downloaded karmic 64bit from [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/). Installs and works fine in lucid.

---

### Post by lekzz on 2010-03-02
USB still working for me on Lucid updated from Karmic. hal is not (yet?) removed by update from Karmic.

Also after purge / reinstall of hal it's still working for me. (wanted to get rid of hal, but ran into vbox/usb problems). And i use it on a daily basis.

Guess i'm lucky it's still working for me. Hope they find another way soon though because i want to get rid of hal.

---

### Post by captive on 2010-03-26
> **erkiha said:**
> it is possible to use usb in lucid on vbox by running:
```

hald --daemon=no

```
in terminal before vbox.

It does not work for me. My problem is to access usb devices using vbox, but this was done using something like
```
none 	/proc/bus/usb	usbfs	devgid=121,devmode=664	0	0
```
in fstab. The point is there's no /proc/bus/usb on lucid, and running hald does not change things..

---

