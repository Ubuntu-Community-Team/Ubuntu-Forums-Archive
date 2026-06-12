---
title: "Questions installing from USB (following ubuntu guide)"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by thatswhatshesaid on 2007-08-21
I am trying to install Ubuntu on a laptop with no cd-rom or floppy drive.  I am following this [guide (link)]("https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html") .  Just to be clear, my goal is to boot to the usb drive and install ubuntu onto the laptop (not to install ubuntu on the usb drive and run ubuntu from it).  I have a 1 GB usb drive that I am using for this.

It looks like there are two ways to do it from the guide.

**Method 1**: download "boot.img.gz" and run "zcat boot.img.gz > /dev/sdc1"
Problem: I ran the command but how do I get the ubuntu ISO on there?  After running zcat... the drive only has around 7MB of free space.

**Method 2**: do it manually
Problem: The guide says to download vmlinuz, initrd.gz, and syslinux.cfg from the Ubuntu archives.  Where are the Ubuntu archives?  (Am I supposed to burn the cd and pull the files from there or, install a package to get these files?)

I thought I had a decent handle on using Ubuntu but all the installs I have done were using the regular and alternate cds.  I feel like I am just missing something really obvious here.:confused:

Thanks all,

---

### Post by thatswhatshesaid on 2007-08-22
I got it working now using the steps in this [guide (link)]("http://technowizah.com/2006/11/ubuntu-how-to-ubuntu-edgy-from-usb.html").  I'm not sure what exactly caused one to work over the other but this worked for me YMMV.  Hopefully this can save someone else a headache.

---

