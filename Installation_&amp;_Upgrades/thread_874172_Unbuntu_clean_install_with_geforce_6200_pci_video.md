---
title: "Unbuntu clean install with geforce 6200 pci video"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by Hackit on 2008-07-29
Ok to start my mother board is abit lg-95z.

It has on board video and it has been fine for over a few months.

Well i need a dvi out so I bought a nvidia geforce 6200 pci card, I have installed the card and I'm trying to do a clean install.

the computer boots fine, i see the language screen, then select install.

it starts and then after 3 minutes the scrolling orange bar stops, i have left iot waiting fir an hour, no change.

I tried again using safe video, same issue.

Am i out of luck with this card?

Thanks

---

### Post by spiderbatdad on 2008-07-29
This card should run well on Ubuntu. Possibly requiring driver upgrade. Your boot issue seems to be something other than the card.

Perhaps bring up the grub menu at start up (if it is hidden) and press F6 for other options. Delete "--quiet splash" from the end of the kernel options line, so that you can see where the boot process is hanging.

[http://ge.ubuntuforums.com/showthread.php?t=842149](http://ge.ubuntuforums.com/showthread.php?t=842149)
[http://ubuntuforums.org/showthread.php?t=235220](http://ubuntuforums.org/showthread.php?t=235220)

---

### Post by Hackit on 2008-07-29
ok it seems to stop here;
[ 223.310327] agpgart: detected 7932k stolen memory

---

### Post by Joeb454 on 2008-07-29
Did you try booting in safe graphics mode?

---

### Post by Hackit on 2008-07-29
just did same thing it just stops at the same point.
i have even reset the bios to fail safe.

---

### Post by Hackit on 2008-07-29
Ok i just plugged the old monitor in and used the VGA connector, stops at the same point.

Think i'll remove the video card and see if the onboard still works.

---

### Post by Hackit on 2008-07-29
before i tried the onboard video i hit the reset button,

I noticed it looks like i have usb and pci using irq 9.

Not sure what to do next.

---

### Post by Hackit on 2008-07-29
ok issue is resolved, the abit board has 2 pci slots.

I have a gigabit card in one it's been there since day one, well i changed the cards around now my video is perfect and no gigabit, so it looks like i have a bad pci slot :(

---

### Post by Hackit on 2008-07-29
wow now every time i reboot it says

ubuntu is running in low graphics mode


ran this : sudo dpkg-reconfigure xserver-xorg

still the same any ideas?

---

### Post by steve45377 on 2008-08-26
I am having either the same issue or a very similar one. I have the GeForce 8400GS PCI video card. I try and boot Ubuntu through the LIVE-CD and it freezes up about 3 blocks in on the progress bar. I can boot up from the LIVE-CD just find using the onboard graphics. My system specs are:   

HP Pavilion a1000y
2.8 Ghz Celeron D
2 GB Ram
160 GB Hard Drive

This issue also occurs with openSUSE. If any one can help me resolve this issue I would be extremely thankful, I have been trying to get linux on my computer for a while now.

---

