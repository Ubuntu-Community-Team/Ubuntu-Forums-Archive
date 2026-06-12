---
title: "Ubuntu 16.04, 17.04, Mint 18.1, 18.2 and the Nvidia boot issue"
date: 2017-09-17
forum: Installation &amp; Upgrades
---

### Post by freak111 on 2017-09-17
I have been attempting for over a week (off and on) to install Linux on my system. It is a clean install on a Samsung EVO SSD, i7 with a Nvidia 970GTX. This has been a nightmare of epic proportions. Either the Installation will crash installing grub or will refuse to boot upon completion, or the installation will refuse to boot at all.

I have finally gotten 17.04 to install by removing quiet splash and replacing it with **nomodeset**. Then it promptly hangs on reboot and I get a purple bar at the top of the screen with green hash marks. I have read and attempted several fixes including inserting **noveau.nomodeset=0** at the end of the linux line, but it still will not boot.

The easy way around this is to purchase an AMD video card and go on my way, but the 970GTX is less than a year old. 

There has got to be a better and easier way than to fight with this over and over again to no avail. I would appreciate any suggestions you can give on this subject.

I did read a suggestion about doing a network install, but I am so far away from the router and my wifi card does not like the generic install drivers.

---

### Post by Bucky Ball on 2017-09-17
Welcome. Deep breath. You say you have 17.04 installed? That's a start. You can boot and get to a list of options at a boot menu? If so, then you sound like you know how to edit the kernel line. Select the kernel you want to boot, hit 'e' and, after the line that ends with 'quiet splash', or something like it, give it 'quiet splash nomodeset'.

This is the option you used when you managed to install. It may be the one that works now. Once at a desktop, install the GPU driver from 'Additional Drivers'. If you don't get that far, let us know where you do get. 

I'm using that same card on my AV workstation (in fact I'm using an i7 and I think a Samsung Evo, too). Rocking card. ;) Thing is, I had no problems with it on 16.04 (Xubuntu-core). :-k

(PS: Just a thought. You say this is a brand new SSD? Might pay to boot the install media and 'Try Ubuntu'. Once at a desktop, launch Gparted and format the SSD with one big partition or format with the partitions you are intending to use for your install. When that's done, hit the install icon on the desktop, choose 'Something Else' (I think it's still called that) when you get to the partitioning section and see how you go. You are still probably going to hit the hurdle of the vid card, though. Hopefully 'nomodeset' will get you through that. Good luck.)

---

### Post by ajgreeny on 2017-09-17
I am unable to figure out whether or not you have installed the correct nvidia driver after installing Ubuntu.

Once you have booted the first time into your installed Ubuntu using nomodeset boot option, go to Additional Drivers and install the recommended driver shown there.  You should then be able to boot straight into the GUI as your 970GTX will be using the correct driver.

---

