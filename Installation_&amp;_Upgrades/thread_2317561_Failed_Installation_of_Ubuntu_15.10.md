---
title: "Failed Installation of Ubuntu 15.10"
date: 2016-03-17
forum: Installation &amp; Upgrades
---

### Post by smartem on 2016-03-17
Hi,

I try to install Ubuntu 15.10 on laptop with Intel processor, i% vPro, with SSD disk, in clasic mode, disabled UEFI.

But I download Ubuntu installation DVD with extension AMD,  ubuntu-15.10-desktop-amd64.iso.
This is automatically selected version, because I download installation on my other comp with AMD processor. 
Is it maybe this mistake which crash installation?
Is there different version for Intel processor and how to download it?

I got this message when installation failed:
Ubiquity 2.21.37 
Crash
Ubiquity crashed with dbus.exceptions.DDBusExcpetion in call_blocking():org.freedesktop.Netwrok.Manager.Settings.PermissionDenied:No session found

Do you have any idea?

---

### Post by ajgreeny on 2016-03-17
The AMD64 iso files are for both AMD and Intel 64bit processors, so you can stop worrying about that immediately.

Try installing again but this time uncheck the tick box network connection, and do not ask for third party packages or updates to be installed as you install the OS; they can all be added later and it is not needed for the installation to be successful.  The whole installation will also be much faster.

Have you checked that the iso file you have is a good one by comparing the md5sum?  See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by oldos2er on 2016-03-17
The amd64 version is for both Intel and AMD processors, so you have the right one.

---

### Post by linuuxi on 2016-03-17
Why not try the 14.04 version. Most people download and install it with no problem while the 15.10 version is more problematic I think.

---

### Post by smartem on 2016-03-18
Hi,

thanks for answers.

I change in Bios installation on UEFI, but it crash again.

Than burn DVD again and it was successful. Bad DVD...

But now I have other problem, after installation Ubunutu doesn't wont to boot.
After I remove USB CD drive from which I installed it, it cannot detect any OS.

Boot order start with OS boot manager, than HD...but nothing.

Any idea how to fix Boot sector?

---

### Post by smartem on 2016-03-18
Hi,

I change from AHCi mod, and now I have option from boot sequence to choose UEFI.

I navigate to grob.uefi   and start Ubuntu.

How to make this boot sequence permanent, to not press F9 every time when I boot laptop?

---

### Post by ajgreeny on 2016-03-19
See Boot-Repair in my signature below and follow the instruction to run the Boot-info-script.  This will show you a pastebin link which you can post back here and will help us diagnose what is going on.

Do not at this stage accept the default repair; just run the boot-info-script.

---

