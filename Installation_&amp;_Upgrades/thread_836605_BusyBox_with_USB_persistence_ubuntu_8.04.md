---
title: "BusyBox with USB persistence ubuntu 8.04"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by unity1 on 2008-06-21
You may have to give me some slack as I'm new at Ubuntu and linux in general altough have done the 3 day introduction to SUSE 10 2 weeks ago.

I've manage to install 8.04 within windows and all works fine (using it now in fact). I've been trying to create a USB bootable version using a 1Gb stick. I've followed the guides and created 2 partitions, mounted the ISO in loop back, copied the files over etc. This is working as I can use the USB device to boot and get the Ubuntu menu.

Now if I select 'Live' it boot fine just as the Live CD.

Problem is if I select persistent is starts to boot the drops out to a BusyBox screen. From reading other posts here I've looked at the casper.log and get the following 

/init: /init: 1: cannot open /dev/scd0: No medium found
/init: /init: 1: cannot open /dev/scd0: No medium found
mount : Mounting /dev/sdb2 on /cow failed: Invalid argument
Can not mount /dev/sdb2 on /cow

Further google found (link below) which seems to suggest 8.04 with persistence does not support ,mode=755 in 'mount /dev/sda2 -o rw,noatime,mode=755 /cow'


[http://blog.mc-thias.org/?title=ubuntu-8-04-hoary-persistent-on-a-usb-st&more=1&c=1&tb=1&pb=1](http://blog.mc-thias.org/?title=ubuntu-8-04-hoary-persistent-on-a-usb-st&more=1&c=1&tb=1&pb=1) 


Its not clear where this is but believe I've located the file in the initrw.gz file in the casper folder. Tried to edit it (gedit), select save and the 'update archive'. This however does not seem to actually update it. I've also tried  extracting the archive and editing the file (which is then ok) but if I create a new archive I get a initrw.tar.gz. If i leave this as is or rename it to initrw.gz and put it on the USB stick it fails to load the kernal at all and hangs even if live selected.

TBH I dont know if editing this file will fix the problem or what I'm doing wrong in doing so but any help would be useful.

---

### Post by unity1 on 2008-06-21
This seems to be a known bug. Case of not seeing the wood for the trees.

There are 'patched' copies of initrd.gz avaliable.

Pendrivelinux have one :)

wget pendrivelinux.com/downloads/u8/initrd.gz

---

### Post by mistere23 on 2009-03-16
Try the instructions on this [blog]("http://ubuntuliving.blogspot.com/2008/11/missing-operating-system-step-by-step.html"): 

I was having a similar problem and finally got booted into Ubuntu after following the steps there, booting into the live "disk" option and then installing from there.  Good luck!

---

