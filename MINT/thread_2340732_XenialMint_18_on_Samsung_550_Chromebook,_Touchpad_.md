---
title: "Xenial/Mint 18 on Samsung 550 Chromebook, Touchpad Driver Issues"
date: 2016-10-21
forum: MINT
---

### Post by fitzy752 on 2016-10-21
Hi all, I hope it is ok to post in here about Linux Mint 18 based on Ubuntu Xenial, if not please let me know and I can post in their own forums but I thought the same issues would apply to regular Ubuntu as well so may be worth trying here.

I have got a Samsung Series 5 550 Chromebook model 'Lumpy', I have installed SeaBIOS to allow me to replace ChromeOS with Linux (my preference being Linux Mint 18).

For the most part it has worked very well, install went smoothly and without issue, but the only problem I am having is my touchpad not working in Xorg.

I'm a novice when it comes to the technical side of Linux but have used various distros for several years for general use so all my troubleshooting so far is based on forum posts.

Initially, it was not detected at all, I then found out that the Chromebook touchpads/clickpads require the CMT driver from here: [https://github.com/hugegreenbug/xf86-input-cmt](https://github.com/hugegreenbug/xf86-input-cmt)

I was able to easily install this, and when running **modprobe i2c_i801** I then started seeing data coming from the touchpad when running [B]cat /dev/input/mice

[/B]My only issue now is getting the pointer to work in Xorg (I'm using the Cinnamon desktop if it matters on Xorg 1.18). Left clicks are recognised fine when pressing the clickpad, but pointer movement seems to be ignored. Tapping and two finger scrolling are also not working. 

Xorg log file:  [http://pastebin.com/Lg62Rzpg](http://pastebin.com/Lg62Rzpg)
Xinput: [http://pastebin.com/N6By4dhe](http://pastebin.com/N6By4dhe)
Dmesg: [http://pastebin.com/bwrj2w6N](http://pastebin.com/bwrj2w6N)
Lsusb: [http://pastebin.com/4cTb7JCh](http://pastebin.com/4cTb7JCh)
Lspci: [http://pastebin.com/X4U47Sp9](http://pastebin.com/X4U47Sp9)
Xorg config file (model-specific, supplied with CMT driver): [http://pastebin.com/qu1U5pf3](http://pastebin.com/qu1U5pf3)

Can anyone advise what I should be doing next? I'm confident with using the command line, just need to know what to put in there :)

---

### Post by howefield on 2016-10-21
Moved to the "*MINT*" sub forum.

---

### Post by fitzy752 on 2016-10-21
> **howefield said:**
> Moved to the "*MINT*" sub forum.

Apologies.my.spacebar.doesn't.seem.to.be.working.now.lol.-Interestingly.only.on.this.website,other.websites.it.seems.to.work.fine,very.strange.

Thanks.for.moving.the.post,I.should.have.checked.for.a.appropriate.subforum.

---

