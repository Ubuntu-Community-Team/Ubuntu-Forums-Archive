---
title: "Installation To 133GB Thumb Drive 14.04"
date: 2015-09-13
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-09-13
Hello,

Can Ubuntu 14.04 be installed to a Thumb Drive? I've already burned 14.04 to an 8GB Thumb Drive using UnetBootin; but this is not really an install. It's just the LIVE DVD; and neither updates nor software installations persist. I've recently purchased a 133GB Thumb Drive and would like to install Ubuntu to it. This way, I can simply carry my entire build with me, on my key chain, at all times. This would have great advantages for International travel; and security. I'd much rather bring this through International Customs, than a complete laptop. The likelihood of a search of my personal papers is greatly reduced. If this is not currently possible, I would like very much for it to be in the near future. I will most certainly be an early adopter.

Thanks, Hannibal

---

### Post by sudodus on 2015-09-13
Yes it is possible. I have done it many times. Disconnect the internal drive and install into the pendrive like you would install into an internal drive.

Good luck :-)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by coljohnhannibalsmith on 2015-09-18
> **sudodus said:**
> Yes it is possible. I have done it many times. Disconnect the internal drive and install into the pendrive like you would install into an internal drive.

Good luck :-)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

I've been trying this but the installer keeps experiencing a read only file system error. I've used two different thumb drives, the last being significantly faster than the first. Is the media the problem, or is it something else?

Thanks, Hannibal

---

### Post by sudodus on 2015-09-18
Please describe exactly what happens - and the error output.

You help us help you if specify your computer (more data than in your signature)

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

You can also post the output of the following commands, when the pendrives are connected.

```
df

sudo lsblk -fm

sudo parted -ls
```

and it is good to know if you are running in BIOS mode or UEFI mode. See this link and links from it and check if you run in UEFI mode.

[FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by MartyBuntu on 2015-09-18
Make sure you understand the performance limits (and there are quite a few...even with USB 3.0) of the installation that you've described.

---

### Post by yancek on 2015-09-18
You could use unetbootin or other similar software to create a Live CD on a flash drive with persistence thus giving you the ability to install additonal software or save changes.  Given the size of the usb drive you have, it would make more sense to do an actual install.  When do you get the message about a read-only filesystem, at what point in the install?  What is on the 133GB drive currently?  Is it unallocated space?  Does it have any partitions?  Is it formatted?

---

