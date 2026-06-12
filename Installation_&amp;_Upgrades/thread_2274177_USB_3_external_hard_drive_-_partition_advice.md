---
title: "USB 3 external hard drive - partition advice"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by mrwaistcoat on 2015-04-18
I've got a 500gb USB3 Samsung ext hard drive.

I've installed a few buntu distros onto it for use with a 64 bit laptop with windows 7 (I don't want to touch the laptop hard drive)

Performance is excellent, but after several reboots I keep losing the whole system

I'm thinking I'm going wrong with my partitioning....

I've given 8gb to swap - is swap necessary for ext hard drive, and if so, is 8gb sensible? The laptop has 4gb ram

*I've seen conflicting advice as to whether to use ext2, ext3 or ext4*

I'm guessing I'm experiencing shut down/power issues causing data loss?

Any advice appreciated.

Also, is what I'm doing even possible for a stable OS?  There is very little info on this following many google searches

Many thanks

---

### Post by gordintoronto on 2015-04-18
You should be able to run a stable OS from an external hard drive. However, I'm not convinced that Linux has solid support for USB 3 *ports*. If it were my system, I would use EXT4, have an 8 GB swap, and plug the drive into a USB 2 port.

Please explain the "shut down/power issues"? Do you have difficulties doing a clean restart into a different environment?

I'm currently running Xubuntu 15.04 (pre-release) from a 32 GB USB 3 flash drive, plugged into a USB 2 port. It has been solid for almost a month. Performance is quite acceptable.

---

### Post by mrwaistcoat on 2015-04-19
Cheers

"shut down/power issues" is a guess. Reason being ubuntu has died upon reboot (usually after I've installed lots of things) and I've had to do 3 reinstalls.  I've been experimenting with the partitions. I suspect the OS has died because the usb3 lead has come out too soon.  USB3 is certainly  miles faster than flashdrive - I'm playing the latest steam games with no lag

the project is to enable me to have my massive google play music collection and other files in one place.  It seems as fast as internal drive

currently using ext4 - fingers crossed all will be OK this time! I've now created a second partition also with ubuntu on, so hopefully that will help me rescue lost data if it happens again

I'm thinking I should regularly back up, but that will mean buying a second ext hard drive!

---

### Post by mrwaistcoat on 2015-04-21
> **gordintoronto said:**
> You should be able to run a stable OS from an external hard drive. However, I'm not convinced that Linux has solid support for USB 3 *ports*. If it were my system, I would use EXT4, have an 8 GB swap, and plug the drive into a USB 2 port.

Please explain the "shut down/power issues"? Do you have difficulties doing a clean restart into a different environment?

I'm currently running Xubuntu 15.04 (pre-release) from a 32 GB USB 3 flash drive, plugged into a USB 2 port. It has been solid for almost a month. Performance is quite acceptable.

Yes, when I've changed desktop environment the system would not then restart. I'm now using Ubuntu Mate on Ext4 , with 8gb swap, and so far all is stable.  I had tried flashdrive install but thought the speed was laggy.  CPU usage at 1% with this distro! Have added Wallch and compiz, and CPU still only at 2.5%, so I'm delighted.  

USB3 seems to work extremely fast - I'm surprised it's not more popular. 500gb Samsung device was only £30....

I've decided to use systemback to keep my basic setup stored on a flashdrive, so I can easily restore if the USB3 dies again.  Hopefully it won't - simply because Ubuntu Mate is the only linux I've not wanted to tweak - it's virtually perfect for me as it is!
:)

---

