---
title: "Custom Ubuntu Server ISO - The CD on /dev/sr0 is not an Ubuntu CD"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by ruffEdgz on 2010-03-12
What I am going to tell you has worked for the Alternative Ubuntu ISO but I would like to see if I can do this for the Server Ubuntu ISO. I need to pass along some ideas as no one else seems to have tried it this way on this forum (other have been using preseeds but I don't think this way).

[LIST]
[*]Been using this Ubuntu Doc as reference for this: [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
[*]Downloaded ubuntu-9.10-server-i386.iso from Ubuntu's site: [http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors](http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors)
[*]Mounted the ISO to my computer: **mount -o loop Download/ubuntu-9.10-server-i386.iso /mnt/ubuntu/**
[*]Copy files from the mounted ISO to my HDD: **cp -rf /mnt/ubuntu/* /opt/ubuntu-server/**
[*]Once the files were on my HDD, I started to edit files that would help using a special preseed I wanted to configure
[*]I changed directories to /opt/ubuntu-server/preseed/ and created a file called test.seed
[*]I edited the test.seed file with the example found here: [https://help.ubuntu.com/9.04/installation-guide/example-preseed.txt](https://help.ubuntu.com/9.04/installation-guide/example-preseed.txt)
[*]Saved it and changed directories to /opt/ubuntu-server/isolinux/ 
[*]Started the edit the text.cfg (holds the labels for installing ubuntu)
[*]Here is what I appended to the end of the file:
---
label test-install
  menu label ^Install Test Ubuntu
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/test.seed debian-installer/locale=en_NZ console-setup/layoutcode=us initrd=/install/initrd.gz quiet --
---
[*]Save the file and change directories to my home directory: **cd ~**
[*]I then start the ISO creation process: **sudo mkisofs -D -r -V "Custom Install CD" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o custom.iso /opt/ubuntu-server/**
[*]It successfully makes the ISO in my home directory called 'custom.iso'
[*]I start a test of the ISO with: **qemu -cdrom custom.iso -boot d -m 512**
[*]The emulation starts and gets to the Ubuntu Installation Screen, I select the 'Install Test Ubuntu' option and it starts to load up
[*]The process looks like its taking shape but then I get a red screen saying: **"The CD-ROM drive contains a CD which cannot be used for installation"**
[*]I checked /var/log/syslog and it says something simular: **"The CD on /dev/sr0 is not an Ubuntu CD!"**
[*]For a second test, I thought I would update the /opt/ubuntu-server/md5sum.txt with a more up-2-date checksum: **find . -type f -print0 | xargs -0 md5sum > md5sum.txt**
[*]I deleted the old 'custom.iso' and recreated it with the same result
[/LIST]

The question I have is: how can I make my custom ISO a trusted Ubuntu CD or where on the CD does it check to see what is a trusted Ubuntu CD?

Any thoughts, ideas or questions would be great. Thanks!

---

### Post by jeezet on 2010-03-22
Hi,

Two things came to mind, though maybe not definite answers:

1. cp -rf copies/removes existing files, but does it pick up all files (also the hidden ones) for you? In other words, have you checked that all files got copied out? I prefer to [use rsync to get an exact copy]("https://help.ubuntu.com/community/InstallCDCustomization#Copy the CD to your hard drive").

2. did you try to run/install the image with another virtual machine host? Like, for instance [Virtualbox]("http://www.virtualbox.org/wiki/Downloads"), [Parallels]("http://www.parallels.com/computing/") or [VMWare]("http://www.vmware.com/support/product-support/fusion/")?

I know your question drives towards getting a trusted Ubuntu CD, but having been struggling with custom installs for the past two weeks - I have never had a trust-issue with these images. And have been using same sources as you have.

Kind regards,
Jeroen.

---

### Post by ruffEdgz on 2010-05-25
> **jeezet said:**
> Hi,

Two things came to mind, though maybe not definite answers:

1. cp -rf copies/removes existing files, but does it pick up all files (also the hidden ones) for you? In other words, have you checked that all files got copied out? I prefer to [use rsync to get an exact copy]("https://help.ubuntu.com/community/InstallCDCustomization#Copy the CD to your hard drive").

2. did you try to run/install the image with another virtual machine host? Like, for instance [Virtualbox]("http://www.virtualbox.org/wiki/Downloads"), [Parallels]("http://www.parallels.com/computing/") or [VMWare]("http://www.vmware.com/support/product-support/fusion/")?

I know your question drives towards getting a trusted Ubuntu CD, but having been struggling with custom installs for the past two weeks - I have never had a trust-issue with these images. And have been using same sources as you have.

Kind regards,
Jeroen.

Thanks for the reply and sorry for the late one on my part... busy with other linux problems with work and so on :P

I totally understand what you are saying so I am going to try what you purposed and report back what I find. I got one to work and idiot me forgot what I did so I will try and retrace my steps and share them here once I'm done.

Anyone else has any ideas, I'm all ears :D

---

### Post by mbmather on 2011-03-21
I too am stuck here... any found an answer?

---

### Post by zakchambers01 on 2012-06-12
I've been building a custom iso and came up against the same problem.

Turns out its because I copied the extract original ubuntu iso from one place to another without thinking about hidden files.  There is a hidden folder in the root called .disk.  Make sure thats there and the message will go away.

---

