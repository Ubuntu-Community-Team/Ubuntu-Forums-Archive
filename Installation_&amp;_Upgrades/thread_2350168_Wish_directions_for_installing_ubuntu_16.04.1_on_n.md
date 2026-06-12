---
title: "Wish directions for installing ubuntu 16.04.1 on new windows 10 computer"
date: 2017-01-21
forum: Installation &amp; Upgrades
---

### Post by alvinmoneypit on 2017-01-21
I couldn't easily find directions to do this on this forum.

I bought a new Lenovo 310-15ABR running by AMD12 7th gen.  I wanted to install ubuntu 16 out of the box, but it wouldn't autoplay.  So I completed the windows10 install as prescribed without setting any passwords or usernames except naming the computer.  The Ubuntu 16.04.1 disk I created still would not autoplay and I don't know how to make it play through windows. I had tried booting it from startup but could not find anyway to set boot order, as the Lenovo apps has no method for doing so and the conventional methods I used in the past to configure BIOS and UEFI have not worked so far.  

Anything you have on this will be appreciated as I'm not sure if wiping the drive is preferential or even possible having been infected with windows 10.

---

### Post by wildmanne39 on 2017-01-21
*Thread moved to **Installation & Upgrades**.*

---

### Post by Mark Phelps on 2017-01-22
You can NOT install Ubuntu from inside Windows, so you do NOT want the Ubuntu disk to autoplay.

To install Ubuntu, you first have to use Disk Management in Win10 to shrink down the largest partition to make some room for Ubuntu.  Do NOT use the Ubuntu installer to shrink the partition using a side-by-side installation as this risks corrupting the Windows filesystem in the process, and since that will then prevent Windows from rebooting, that will make it really hard to fix.

After you have the unused space set aside, then BOOT from the Ubuntu disk and install that way.

---

### Post by alvinmoneypit on 2017-01-22
Mark,
Thanks for your reply, but I wanted to erase windows anyway.
I solved the problem on my own by searching for "BIOS" in the Windows start search box on the lower left side.  This brought up a number of clickable links, one of which indicated something like "additional input drives".  I clicked on this and it displayed the on board hard drive, the USB ports, the HDMI port and the DVD drive.  All of these are indicated by their specific model numbers and may be difficult to discern what they actually are.  I clicked on the icon I thought was the DVD drive and the autoplay began.  I successfully installed Ubuntu 16.04.1.  I'll mark this thread as 'solved'.

---

