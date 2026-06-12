---
title: "new install help"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by cob111 on 2011-11-15
Hi,
I'm running Windows 7 Starter on my netbook and would like to also be able to use Ubuntu on my machine. I have some questions that perhaps you can help me with. First, is Ubuntu a full version of Linux? I want to be able to do Perl scripting, shell scripting, grep, AWK, etc. Second, I am looking at the Ubuntu.com website and there is a link ([http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)) for downloading Ubuntu for windows. Can I just download Ubuntu via that link andrun Ubuntu? Will I be running it inside Windows or will it automatically create a partition and install Ubuntu in the new partition? If it doesn't automatically create a partition for Ubuntu is there anyway I can automate this process? Is it better to run Ubuntu inside Windows or "alongside" it (via a partition). Finally, should I consider downloading Ubuntu to a thumb drive a booting it from the stick? Thanks in advance.

---

### Post by Mark Phelps on 2011-11-15
Regardless of what approach you choose, do NOT let the Ubuntu installer shrink your Win7 install by using the "slider".  Doing so risks corrupting the Wint OS partition and rendering it unbootable.  And since you probably do NOT have a Win7 Repair CD, and with a netbook, no way to use one even if you did have it, if Win7 gets corrupted, you've pretty much lost use of it.

Instead, if you want a traditional dual-boot (with Ubuntu in its own partition), then do the following:
1) Use the Win7 Disk Utility to shrink the Win7 OS to make room
2) Do NOT create a partition in the new space
3) Reboot into Win7 on your netbook a couple of times after this to allow it to make any filesystem adjustments.

If you have an external drive, and you want to be doubly-sure that nothing bad happens to Win7, then do the following (after you do the resize using the Win7 Disk Management utility):
1) Go to the Macrium Reflect website, download and install the FREE version of MR.
2) Use the backup feature to back off the Win7 install to an external drive.

NOW, you can restore Win7 in just a few minutes -- if you need it back.

Linux is an operating system kernel; Ubuntu is a Distribution (known as a "distro") of Linux that comes with some applications and desktops.  So, yes, it is a Full version.

Wubi installs Ubuntu from INSIDE MS Windows, but it does not RUN from inside MS Windows, it just uses Windows to handle the boot.  Once Ubuntu is up and running, it behaves the same as a regular installation.

As to which to use (wubi or traditional dual-boot), boot into Win7, use the Disk Management utility to look at the "drives" (what microsoft calls partitions) on your netbook.  IF you already have the maximum of 4, do NOT create anymore partitions.  Instead, you will need to come back so we can figure out which partition to remove.

---

### Post by cob111 on 2011-11-15
Thanks for the quick response. I haven't done the download/install yet so I am curious as to how I prevent the Ubuntu installer from shrinking my Win7 install by not using the "slider".

---

### Post by darkod on 2011-11-15
1. As far as I know, it's very full version od Linux. Personally I have only done Java programming on it, I guess you could do all that you need. Also, depending whether you are using some kind of IDE, the Netbeans IDE installs just fine on ubuntu.

2. Yes, you can create a bootable usb stick from the iso.

3. Definitely NO to wubi (installing inside windows). It will be more like virtual machine, and can often break down with some update or similar because it is made to work inside windows which is not the natural environment. Install it as dual boot in its own partition, especially for serious work.

For win7 take a look at your hdd and make a plan. The first important thing to research is that you already don't have 4 primary partitions created, because as minimum you will need to create one extended partition with two logical inside for ubuntu.
When shrinking windows partition to make unallocated space on the disk, best do it with windows Disk Management, then reboot few times to run checks if it wants. Then proceed with the ubuntu install into the unallocated space.

---

### Post by cob111 on 2011-11-15
Thanks. I've never done a partition for a dualboot system. So that I get it right is there any step by step tutorial online that I can follow?

---

### Post by darkod on 2011-11-15
This is the only I could find quickly:
[http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html](http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html)

Note that in this tutorial they manually create only the main, / partition. It's better to create a second, swap partition too. In this case the field "use as" would be swap space, and there is no mount point to set.

You can search for other tutorials too, for older versions it should be similar and maybe you can find more of them. 11.10 is still relatively new.

---

