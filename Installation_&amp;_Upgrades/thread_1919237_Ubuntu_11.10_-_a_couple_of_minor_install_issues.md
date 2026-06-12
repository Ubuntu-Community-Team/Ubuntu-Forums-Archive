---
title: "Ubuntu 11.10 - a couple of minor install issues"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by Nick_C on 2012-02-02
Just installed ubuntu-11.10-desktop-amd64.iso but have a couple of comments on items noticed during install:

1). There was no option available, as far as I could see, to select or even confirm which disk to install on.  In my case it installed the boot loader onto the wrong drive, trashing the existing bootloader without warning, I had to change the boot disk in the BIOS before it would boot.  It also proceeded to install itself on a different drive and partition to the one I had intended for it

2). No option was available to choose what software to install.  I only wanted a bare minimum of system tools but have ended up with Office and multiple other accessories.  These were not needed as this is to be used as virtualization host only.

Nick

---

### Post by mikewhatever on 2012-02-03
1. This is odd. You should have had a screen that looks like this:
[http://pix.toile-libre.org/upload/original/1312973605.png](http://pix.toile-libre.org/upload/original/1312973605.png)

The last option would let you select or create partitions for Ubuntu as well as modify the default boot loader location.
Check out the graphical installer howto for more info.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

2. The graphical installer is intentionally designed to be simple fast and user friendly. It just installs the a predefined set of packages and asks for reboot. I am sure most new users can appreciate it. For those who want a different setup, there is always the Alternate CD or the Mini ISO.

---

### Post by Nick_C on 2012-02-03
> **mikewhatever said:**
> 1. This is odd. You should have had a screen that looks like this:
[http://pix.toile-libre.org/upload/original/1312973605.png](http://pix.toile-libre.org/upload/original/1312973605.png)

The last option would let you select or create partitions for Ubuntu as well as modify the default boot loader location.
Check out the graphical installer howto for more info.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

2. The graphical installer is intentionally designed to be simple fast and user friendly. It just installs the a predefined set of packages and asks for reboot. I am sure most new users can appreciate it. For those who want a different setup, there is always the Alternate CD or the Mini ISO.

Thanks Mike, I didn't know that Alternate or Mini CDs existed I will look into it further and try one of those.

As for that install screen I do remember seeing that screen but assumed that 'Install Ubuntu alongside them' would give me options about where to install it alongside them but obviously not.

Cheers,
  Nick

---

### Post by Nick_C on 2012-02-04
Well I have now downloaded the alternative CD (ubuntu-11.10-alternate-amd64+mac.iso), however again this has installed many accessories which I don't need.  Is there any way select what gets installed and installed just a bare minimum with a GUI, disk tools, network, NTFS access and KVM?

Thanks,

---

### Post by darkod on 2012-02-04
The alternate installs the same as the desktop, with a difference that it has a text based installer and offers raid and lvm support.

The Minimal CD (Minimal Install) is what you want but only if you have more experience with ubuntu. I say this because the minimal cd installs basically just the core, without GUI, etc. You need to start adding things manually.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Otherwise, if you want more control about partitioning and where the bootloader is installed, you need to use the manual partitioning option (called Something Else in the latest version). That will allow you to create partitions manually and select to which disk the bootloader goes.

---

### Post by mikewhatever on 2012-02-05
AFAIK, there is an option to install the command line system with the Alternate CD. If memory serves me right, it was under F4.

---

