---
title: "USBuntu + 4GB Thumbdrive: Can I Make a Live Partition + a Data Partition?"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by maharbA on 2007-12-27
I just got a 4GB USB thumbdrive and I would like to use it as a LiveCD (LiveUSB). Since it's a whopping 4 gigs, though, I'd still like to use that bountiful space for storing pics/vids/music that I'd like to walk around with.

I've read a bunch of tutorials that use extra space to save configurations, etc. but I haven't seen one that gives me a data partition.

I don't even know if it's possible: for example, how would that drive appear if I put it in my friend's Windows PC or my Mac -- or if I plug in into my friend's PS3 (now that the PS3 plays Divx vids)? Would it show up as an Ubuntu LiveCD (LiveUSB) plus a regular USB drive? How would that look in BIOS when I'm booting off of it? When I boot it I want to see the data partition mount as a regular R/W drive.

I'm not too concerned with saving any config changes. One of my Ubuntu boxes is still completely default (except codecs) -- on second thought, maybe I'd like to keep codecs since I'll be dragging around divx vids and mp3s.

So I guess I want a LiveUSB drive AND a regular (if slightly smaller) USB thumbrive. Two drives in one.

I'm not exactly new to Linux but I am new to customizing LiveBootables. I'm also eager to learn. For those reasons, I would love any helpful explanations of commands (or explanations of why what I want is impossible).

Thanks everyone!

---

### Post by schaumkeks on 2007-12-27
If you want a USBuntu you might have already read the wiki article [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I once accidentally inserted my usb pendrive with two partitions while Windows XP was running and it suddenly rebooted. After that my hard disk failed to boot again. Although the hard disk failure surely was the result of a very long live, [Windows has problems with more than one partition on external drives]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent#head-0977f1117374135da452bd135c75f8d9fcd5bf68") as you can read in the article.

So, I really recommend to buy a second usb stick for data transfer. They are not expensive anymore.

---

### Post by maharbA on 2007-12-27
Well, if that's true, I'll probably get another drive for live-booting since 4 gigs is a bit excessive.

---

### Post by aselya1 on 2008-01-16
What it sounds like you want to do is make your first partitition for "normal" flash use, i.e. shuttling files, whatever. The best way to do that and still have a live persistent USB drive is to follow the Alternate Partition Layout instructions here: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent#head-0977f1117374135da452bd135c75f8d9fcd5bf68](https://wiki.ubuntu.com/LiveUsbPendrivePersistent#head-0977f1117374135da452bd135c75f8d9fcd5bf68) . There are still a few problems with Live Persistency as a whole in Ubuntu, but its still pretty awesome! If you have any questions, ask me or these are good resources: 
[http://wiki.ubuntu.com/LiveUsbPendrivePersistent](http://wiki.ubuntu.com/LiveUsbPendrivePersistent)
and for using GRUB, which I recommend:
[http://ubuntuforums.org/showpost.php?p=2893694&postcount=133](http://ubuntuforums.org/showpost.php?p=2893694&postcount=133)
[http://ubuntuforums.org/showpost.php?p=1229101&postcount=158](http://ubuntuforums.org/showpost.php?p=1229101&postcount=158) .

---

