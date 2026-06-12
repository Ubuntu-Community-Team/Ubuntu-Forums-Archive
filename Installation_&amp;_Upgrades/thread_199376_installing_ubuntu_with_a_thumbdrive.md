---
title: "installing ubuntu with a thumbdrive"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by spartan777 on 2006-06-18
i need to install ubuntu on a thumbdrive. i have a gig stick, and i wouldn't have expected it to be this hard to find a method of doing this. the only way i've found is to install debian from a thumbdrive, and then change the repos and install ubuntu. even trying to get debian onto a thumbdrive is a bear. i could get dsl to boot from my gig stick, but i am uninterested in installing that. what i have is a rackmount server without a floppy or cd drive. just ethernet and usb ports, so my only other option is to buy an ide to usb adapter.

i think it would be incredibly useful to have ubuntu boot off, and install from a usb memory stick. with most new thumbdrives larger than cd's, i'd think that only nominal work would have to be done to modify a ubuntu liveced iso into something anyone could simply write to a thumbdrive, and then boot from it. if you could make use of this sort of thing, please vote in the poll.

---

### Post by jpkotta on 2006-06-18
The wiki is your friend.  

[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)
[https://wiki.ubuntu.com/Installation/FromUSBStick](https://wiki.ubuntu.com/Installation/FromUSBStick)
[https://wiki.ubuntu.com/Installation/Netboot](https://wiki.ubuntu.com/Installation/Netboot)

---

### Post by Lord Illidan on 2006-06-18
10x for the link, my dad's been pestering me for it, but I didn't think he was serious.

DSL seems better though, faster, for thumbdrives.

---

### Post by spartan777 on 2006-06-18
wow thanks. i guess google can't find everything ;) i checked the forums too, don't know why i forgot about the wiki.

now they just need a little script for ubuntu or from automatix for this. this is another reason i'm trying to learn python this summer.

---

### Post by spartan777 on 2006-06-18
sorry, but the wiki page doesn't work completely. it has directions for breezy, and the dapper release is quite different being a livecd and all. i will probably just do the breezy thumbdrive install, and then upgrade to dapper. thanks though.

---

### Post by spartan777 on 2006-06-27
i tried the instructions for the thumbdrive install using the ubuntu 5.10 install, but i won't work.

---

### Post by scxtt on 2006-06-27
you should check out [www.slax.org](www.slax.org) -- you'll want a much smaller distro if you're planning on using a 1GB flash drive, or you'll want a bigger flash drive (probably +3GB) ... they also have directions to do this ...

---

### Post by cotcot on 2006-06-27
Is this what you are looking for ? :

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28liveUsb%29]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28liveUsb%29")

---

### Post by spartan777 on 2006-06-28
[QUOTE=cotcot]Is this what you are looking for ? :

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28liveUsb%29]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28liveUsb%29")[/QUOTE]


i did this how-to, the whole way, only difference was i used knoppix 5.0 and qtparted to partition it. when i boot from the thumbdrive, right after my pc posts, i get only a flashing cursor. nothing else. any idea what went wrong. i am at my wits' end.

*update: i was able to finally get everything to work, but i had to use knoppix 5.0 to partition, ubuntu would fail, something about the partition table unreadable. they just need to fix ubuntu now. oh, and my server i was trying to install it doesn't support booting from thumbdrives. it was worth about $10,000 and doesn't support booting from thumbdrives.

---

