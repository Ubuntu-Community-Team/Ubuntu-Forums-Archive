---
title: "Installing from mounted iso to hard drive"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by marcerickson on 2012-11-21
I have a PIII 750 MHz ThinkPad with 128MB RAM.  CD drive is worn so it won't properly boot a Live CD, and it doesn't support booting from USB.  I'm a newbie to Linux, but a highly experienced Windows administrator.

Using the power of Google, I've booted from a Damn Small Linux Live CD, mounted the USB flash drive, and mounted the Lubuntu 10.04 Lucid Lynx Minimal Install .iso.  If I'm correct I have also removed all partitions on the hard drive - there should be no MBR or partition tables (this was formerly a Windows 2000 machine).

What now?  Would it be easier to mount the full 10.04 Lucid Lynx .iso and install that way?  If so, how do I start the installation (I think I can figure out how to unmount and remount the USB drive and .iso)?  I've spent a day scratching my head and I know something's possible but being new to Linux I can't figure it out.  I have another Linux box available so I could do a network install if necessary - but the ThinkPad doesn't have a floppy drive.

I'm not scared of the command line but understand very few Linux commands - I mostly type them in by rote.   I'm looking for the easiest way to do this so that I hopefully retain some of the knowledge in case I want to do it again.  ;-)

Thanks to all for the help.

---

### Post by oldfred on 2012-11-21
I do not think mounting will give you a way to run the installer. Someone that knows internals may  be able to change to loop mount ISO and mount as cdrom, but I do not know enough. 
You can try something like this that I saved, but I was experimenting with getting alternative or server versions to install with grub2 and the loopmount, but it kept losing path and I tried going to a terminal in the middle of the install and reloading paths.

       If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like, doubt that DSL needs sudo? Change to exact name of ISO and path you have it on flash drive, not ~/Desktop.
sudo mount -o loop ~/Desktop/ubuntu-10.04-alternate-i386.iso /media/cdrom0

    
       Grub does not loopmount alternate
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926)

    
The minimal install is smaller than DSL and should boot and let you install. May work a bit better if you have partitioned in advance so you have a swap to use by the install.

---

### Post by snowpine on 2012-11-21
Recommend to recycle such an old computer and upgrade to something meeting the following minimum specs:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

128mb is not enough for any member of the Ubuntu family (except possibly Ubuntu Server if your needs are very modest).

---

### Post by marcerickson on 2012-11-21
Recycle?  Exactly what I'm trying to do here.  ;-)

This is going to be a net surfing and email computer for a teenager.

---

### Post by zvacet on 2012-11-22
You can try [Bodhi linux]("http://www.bodhilinux.com/about_bodhi.php") [Puppy linux ]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm") or [Slitaz.]("http://www.slitaz.org/en/about/")

---

