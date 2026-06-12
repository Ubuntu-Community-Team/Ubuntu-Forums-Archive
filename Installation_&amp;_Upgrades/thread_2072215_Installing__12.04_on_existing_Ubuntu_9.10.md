---
title: "Installing  12.04 on existing Ubuntu 9.10"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by irohaphoto on 2012-10-17
Hello

Finally fixed my net book which had a cracked screen. This note book PC is an Acer aspire one and I am using Ubuntu 9.10 on it. The problem is I couldn't get the wireless configured so I decided to download a fresh Ubuntu 12.04 from Ubuntu.com and install it on a USB disk as per instructions on the Ubuntu.com site. I installed it on the computer with Ubuntu 9.10.

After installing 12.04 on my USB disk a message came up saying it was successfully installed  and could be used on any computer. So I tried double clicking on the wubi icon on the USB and got this error:

An Error occurred while loading the archive

Command Line Output

Archive:  /media/PENDRIVE/wubi.exe
[/media/PENDRIVE/wubi.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/PENDRIVE/wubi.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/PENDRIVE/wubi.exe or
          /media/PENDRIVE/wubi.exe.zip, and cannot find /media/PENDRIVE/wubi.exe.ZIP, period.


I also tried changing the boot order on startup and got this error:

SYSLINUX 3.63 Debian-2008-07-15 EBIOS Copyright (C) 1994-2008 H. Peter Anvin
Unknown keyword in configuration file.
boot:

I put the USB into a PC with windows and the wubi file boots fine.

I would appreciate any suggestions as to what I could do to solve this. Thanks

Ben

---

### Post by bcbc on 2012-10-17
You can't run wubi.exe from Ubuntu - by default it tries to open this as an archive. 

Wubi.exe is the Windows ubuntu installer and can only be run from Windows.

To install Ubuntu 12.04 directly to your machine, you need to boot from the USB stick, and... since you said that this failed, it is likely that the ISO you used is bad or that there was some issue creating the USB stick. Try creating it again, and also try to boot from the USB on another machine to see if there is a machine specific issue or to confirm that the USB is bad.

Your other option is to upgrade the 9.10 install. You'd need to upgrade to 10.04 first, and then you can upgrade directly to 12.04 from there (since 10.04 is an LTS). Note: this would take a lot longer than a fresh install.

---

### Post by irohaphoto on 2012-10-17
Thanks for your reply.
As far as I know there is no problem with the install to the USB because I tried it on windows but if I tried booting it from USB on windows there will be options to abort the install, right?

I think the best option is to upgrade the 9.10 install to 10.04 then 12.04. Since there is no internet connection on that notebook PC would I do this by creating a bootable USB for 10.04?

Just wondering can I create the USB disk from windows using the desktop iso file? or does it need to be ubuntu specific?
thanks

---

### Post by bcbc on 2012-10-17
> **irohaphoto said:**
> Thanks for your reply.
As far as I know there is no problem with the install to the USB because I tried it on windows but if I tried booting it from USB on windows there will be options to abort the install, right?

I think the best option is to upgrade the 9.10 install to 10.04 then 12.04. Since there is no internet connection on that notebook PC would I do this by creating a bootable USB for 10.04?

Just wondering can I create the USB disk from windows using the desktop iso file? or does it need to be ubuntu specific?
thanks

Yes I meant boot from the USB on the windows machine (not while running windows). And yes it won't do anything to your machine - you can select "Try Ubuntu" and it will boot to a live desktop without making any changes.

If you want to upgrade without an internet connection I recommend using the Alternate ISO. You can download one for 10.04 and one for 12.04 and that should be all you need. [https://help.ubuntu.com/community/PreciseUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD](https://help.ubuntu.com/community/PreciseUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD)

But again - Upgrading twice will take exponentially more time that doing a fresh install of 12.04, so unless you have important data/programs/setup you want to keep, the fresh install is easiest.

PS another thing would be to boot from the Ubuntu 12.04 USB on your machine to make sure the wireless works now, otherwise you'll be stuck with the same problem connecting.

---

### Post by irohaphoto on 2012-10-23
Thanks. I'll try the alternate install for 12.04 before trying the 10.04 then the 12.04

---

### Post by irohaphoto on 2012-10-23
Just wondering when upgrading from 9.10 is it possible to skip 10.04 and goto 12.04 once I put the iso for 12.04 on the desktop and run this in command? Or do I have to upgrade to 10.04 first?


sudo mkdir -p /media/cdrom 

sudo mount -o loop ~/Desktop/ubuntu-12.04-alternate-i386.iso /media/cdrom

---

### Post by bcbc on 2012-10-23
> **irohaphoto said:**
> Just wondering when upgrading from 9.10 is it possible to skip 10.04 and goto 12.04 once I put the iso for 12.04 on the desktop and run this in command? Or do I have to upgrade to 10.04 first?


sudo mkdir -p /media/cdrom 

sudo mount -o loop ~/Desktop/ubuntu-12.04-alternate-i386.iso /media/cdrom
You have to upgrade to 10.04 first.

---

### Post by irohaphoto on 2012-10-24
Ok I successfully ran the update and no errors but on reboot I get a new purple desktop but the version of Ubuntu is still 9.10. How do I know if all went well? Is it 10.04 or is it still 9.10?

---

### Post by bcbc on 2012-10-24
What do these commands return?
```
cat /etc/lsb-release
uname -r
```

---

### Post by irohaphoto on 2012-10-29
> **bcbc said:**
> What do these commands return?
```
cat /etc/lsb-release
uname -r
```

```
cat /etc/lsb-release

```

Gives me:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"

and ...

```

uname -r
```

Gives me ...

2.6.32-38-generic 


So does that conclude that Ubuntu 9.10 - Karmic Koala in  System>About Ubuntu 
is actually incorrect?

---

### Post by bcbc on 2012-10-29
I haven't heard of that problem for 10.04, but it's happened in other releases: [http://askubuntu.com/questions/19639/why-documentation-says-release-is-11-04-instead-of-10-10](http://askubuntu.com/questions/19639/why-documentation-says-release-is-11-04-instead-of-10-10)

I'd believe the kernel and lsb info

---

