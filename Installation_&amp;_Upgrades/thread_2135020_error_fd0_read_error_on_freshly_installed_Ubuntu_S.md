---
title: "error fd0: read error on freshly installed Ubuntu Server 12.04"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by orhanaslan on 2013-04-12
Hi,
I just installed Ubuntu Server 12.04.2 LTS on a virtual machine. During system boot I receive** error fd0: read error**. I repeated the installation on another machine and received the same error. I downloaded the iso file again and installed it but no luck. System continues and boots after this error but why I am receiving this error on a fresh installation?
Note: **I have used Guided LVM Partitioning-Used entire disk**

---

### Post by MAFoElffen on 2013-04-12
There is a number of ongoing bugs at launchpad on this since 9.04... and in grub2. Please join one of those bugs so it gets some focus. (Example bug# 441835) Most don't use floppies so don't even notice. Me, I still have drivers and patches on floppies for some of my older test servers.

Here is how I got mine working:
```

sudo vim /lib/udev/rules.d/80-udisks-rules

```
At around line #170 you'll see this code:
```

##############################################################################################################


# PC floppy drives
#
KERNEL=="fd*", ENV{ID_DRIVE_FLOPPY}="1"


# USB floppy drives
#
SUBSYSTEMS=="usb", ATTRS{bInterfaceClass}=="08", ATTRS{bInterfaceSubClass}=="04", ENV{ID_DRIVE_FLOPPY}="1"


# ATA Zip drives
#
ENV{ID_VENDOR}=="*IOMEGA*", ENV{ID_MODEL}=="*ZIP*", ENV{ID_DRIVE_FLOPPY_ZIP}="1"

##############################################################################################################



```
Change the ENV value of the drive you want to edit from "1" to "0"... For example:
```

##############################################################################################################


# PC floppy drives
#
KERNEL=="fd*", ENV{ID_DRIVE_FLOPPY}="0"

```
Save and exit. Then restart udev like this:
```

sudu service udev restart

```

Like I said, it fixed my problems. Hopefully it will for your's also.

---

### Post by orhanaslan on 2013-04-12
Hi,
There is no file called **80-udisks-rules** under /lib/udev/rules.d/

---

### Post by MAFoElffen on 2013-04-13
> **orhanaslan said:**
> Hi,
There is no file called **80-udisks-rules** under /lib/udev/rules.d/
```

mafoelffen@maferr-ubuntu-1:~$ ls [COLOR=#000000]/lib/udev/rules.d/80-udisks.rules[/COLOR]
[COLOR=#006400]/lib/udev/rules.d/80-udisks.rules[/COLOR]

mafoelffen@maferr-ubuntu-1:~$ ls  /lib/udev/rules.d/80*
/lib/udev/rules.d/80-drivers.rules       /lib/udev/rules.d/80-udisks2.rules
/lib/udev/rules.d/80-mm-candidate.rules  [COLOR=#006400]/lib/udev/rules.d/80-udisks.rules[/COLOR]

```

---

### Post by Doug S on 2013-04-13
I don't have that file either (server 12.04.2), nor any similar string in any file in the directory. I have always had some floppy error during boot up, on servers with a floppy. I never cared about the error, and boot always continued fine.

---

### Post by MAFoElffen on 2013-04-13
You are right!?! I just looked on my main desktop- 12.10 Desktop, 64bit, x86_64, there. First server- 12.04LTS Server 32bit, i686, there... Second server 12.10 Server 64bit, x86_64, NOT THERE... I can't check the other 8 servers at the moment. Presently moving them from the garage to the spare room (new computer room). 

Aha! Maybe that is why there is an error message. I never noticed on my 64bit servers if it was there or not. Honestly, my older servers that I use the floppies on are dual processor single core Xeon's and one with dual-processor Pentium 4's running 32bit sys'es. On all my 64bit servers I used USB thumb-drives, so I never noticed. My 64-bit desktops have that file...

On desktops, I just go to user settings > privileges > and select the "floppy" check box... For some reason, user privileges are set at default as not using floppies. I guess they think that is a secure issue? But if you follow other's security reasoning, if someone has "physical control" of a sever...

---

