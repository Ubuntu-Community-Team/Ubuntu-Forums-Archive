---
title: "Followed Broadcom instructions, now won't boot!!!"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2006-06-24
I am reduced to using my Windows desktop because now neither of my Linux installations on my Compaq R3240 laptop will boot.

First I installed a new, fresh Dapper-64 using the DVD that I downloaded and burned. I installed to an unused portion of my hard drive, creating a new ext3 partition of 8 GB for it. This worked just fine. It set up Grub with the following options:

Ubuntu, kernel 2.6.15-25-amd64-generic
Ubuntu, kernel 2.6.15-25-amd64-generic recovery mode
Ubuntu, kernel 2.6.15-23-amd64-generic
Ubuntu, kernel 2.6.15-23-amd64-generic recovery mode
Ubuntu, memtest
Other operating systems
Ubuntu, kernel 2.6.12-10-amd64-generic default (on /dev/hda2)
Ubuntu, kernel 2.6.12-10-amd64-generic default (on /dev/hda2) rec. mode
Ubuntu, kernel 2.6.12-9-amd64-generic default (on /dev/hda2)
Ubuntu, kernel 2.6.12-9-amd64-generic default (on /dev/hda2) rec. mode
<and one more Breezy set but I didn't write down the 12-x-amd64 number>
Ubuntu, memtest

If I just let it boot the new Dapper (the top one) it worked fine. I could also scroll down and choose any of the Breezy installations and that would boot fine. I played around with the new Dapper for several days. It seemed very nice. Finally I decided to upgrade the old Breezy installation. Before doing so I took a 60 GB USB pocket drive and a friend's custom-made Linux rescue CD to copy the entire Breezy installation. I have that as a total fail-safe backup. 

I booted the old Breezy and opened Update Manager. It said that there were a number of packages that could not be updated, but if I used "sudo apt-get dist upgrade" from the command line it would do everything. Like a fool, I used the command line. The result was that it stopped in the middle and asked me what I wanted to do about some file or another. One of the options was to get more information about the choices. I chose this letter and it displayed a couple more pages of stuff I didn't understand. There was no indication of how to continue or return to where I was, so I though "Ctrl-z gets me out of man pages," so that is what I did. This presented me with "apt-get dist upgrade halted by user command." Aaargh! This was halfway through the upgrade. I restarted the upgrade (and chose the default this time when presented with the same choice) and it continued, but gave constant errors. Lots of times it said it couldn't remove a folder because the folder wasn't empty, among other error messages. When it was finally done I tried to boot to it and it came up, but lots of applications wouldn't work. I finally figured out that I had dozens of unmet dependencies. By reading the forums I found a command to fix them from the terminal, and it worked for all bit ia32-libs. I read all the forum entries about this but none of the things that worked for others will work for me. At this time the Breezy-sort-of-converted-to-Dapper will not boot except in recovery mode. I have spent hours trying everything I can find on how to get rid or or fix ia32-libs, but to no avail.

Meantime I could always boot into the new Dapper installation. I continued playing with it, using Automatix, for example, to get stuff working that would never work in Breezy. I was so impressed that I decided I would just wipe my old Breezy partition and install Dapper fresh, then copy all my home stuff back and install all my old apps fresh. The new Dapper also automatically found and mounted the old Breezy partition (hda2), so I made another copy of /home on the new Dapper. (Hda1 is the swap and the new Dapper is on hda3.)

There was just one thing that I wanted to check on before wiping the old Breezy and that was getting the Broadcom 4306 working. I had it working on the Breezy installation with ndiswrapper, but it was not automatically working in Dapper. I found a page somewhere here with instructions. Unfortunately, I can't find the page any more, now that I have had to move to my Windows computer. The first part said to sudo apt-get install fwcutter, but when I did it said I already had the latest. The next step was to install some bcm43xx driver other than the bcm43xx driver -- it was a file that started with "a" (Damn I wish I could find those instructions again!). There was a command to use with this "a" file that would find the right driver or something. I ran the command. I think I was supposed to reboot afterwards. When I rebooted it hung right after the Nvidia screen came up. (Automatix had previously installed the Nvidia video drivers for me.) I did "sudo nano /etc/X11/xorg.conf" and edited the "nividia" line to just "nv," thinking that what I had done with the wifi must have created a conflict with the Nvidia driver. Changing the line to "nv" should go back to the open source video driver. I saved the changes and rebooted. This time the Nvidia screen did not come up, but it still hung at about the same place. In other words, the Nvidia driver has nothing to do with the problem.

Then I tried booting the second Dapper option listed above (the "23" version). This also hangs right after the video came up. It won't boot even in recovery mode -- I get:

[38.415355] 8139cp: 10/100 PCI Ethernet driver v1.2 (March 22, 2004)
[38.726949] Kernel panic - not syncing: PCI - DMA: high address but no IOMMU

So, booting the first Dapper in recovery mode, I tried "sudo apt-get remove ndiswrapper." This seemed to uninstall ndiswrapper. After booting in recovery mode one of the last lines I always get is that it is loading ndiswrapper version 1.8. Even after uninstalling ndiswrapper I still get that line. Don't know how it can be loading it after I uninstalled it. 

I also uninstalled bcm43xx-fwcutter, but that, too, failed to have any effect.

So here I sit with both my Ubuntu-64 installations hopelessly broken. I can't find the page I got these instructions on because it was bookmarked in Firefox on the new Dapper, not on this Windows computer.

If you haven't guessed yet, I am far from a Linux guru. Some questions:

1) When it boots in recovery mode hundreds of lines scroll by at the speed of light. Is there a way to pause this display so I can read what it is doing, and maybe find an error message that would give me a clue? Or a way to page back up after it boots in recovery mode?

2) I'd just as soon get the new Dapper working again, mostly because I have a lot of mail that I have saved there since screwing up my old Breezy. Plus it would be nice to get my bookmarks in Firefox back so I could find that instruction page again. Is there a way to reinstall without wiping out the new installation? Something like Windows "Repair" option?

3) Does anyone have any other ideas how to get things working again without totally wiping out the new installation and reinstalling Dapper from scratch?

---

