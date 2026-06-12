---
title: "back door dual boot"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by rw1968 on 2010-10-07
Hello all.
I have a laptop (Dell Latitude E4300) with a single HDD currently running windows. I would like to run Ubuntu, but I need a windows machine too. I'm not normally a fan of dual boot, but at this time I can't really see an alternative (except perhaps buying another laptop)

There is not really enough space on the internal HDD to do a conventional dual boot, and I would really rather leave the windows installation well alone anyway.

The Dell does not support booting from eSata, but does support boot from USB.

My idea is to do an ubuntu installation which has /boot on a USB stick and / on an eSata drive. I can then use the USB stick as a 'key' to boot Ubuntu, but the Ubuntu root fs will be on the eSata drive.

I'm not quite sure how to go about this - anyone got any hints / tips or ideas?

---

### Post by ronparent on 2010-10-07
If you can set the bios boot order so that the usb drive boots first, then install Ubuntu on the usb drive, and install the grub boot loader on the MBR of the usb. Then with the usb plugged in you will get a boot menu and can boot either system. With the usb drive disconnected you will boot directly to windows.

Just one comment. The usb memory stick is convenient and often can be plugged into any computer so that you can carry a 'computer' around with you in your pocket. But it is a bit slow. A usb hardrive is faster if slightly less pertable. I have found both fun options. Good luck.

---

### Post by Ix Oh Yeah xI on 2010-10-07
pendrivelinux.com
I never hit any problems running a persistent os from usb, a little slower perhaps, but usable.  I'm not experienced enough with it to know if you can read home folders from specific drives, but sounds possible.

---

### Post by psusi on 2010-10-07
Why involve a usb stick?  Just install Ubuntu on the external disk and tell the computer to boot it when you feel like it.

---

### Post by pricetech on 2010-10-07
OP says his laptop doesn't support boot to esata, which his external drive is.

---

### Post by psusi on 2010-10-07
Oh, that's hard to believe.  He should check again.  If it can boot from an internal sata drive it should be able to boot from an external one.  It doesn't really know the difference.

---

### Post by rw1968 on 2010-10-07
Thanks for your replies so far.
I would really like to have my ubuntu root file system on the eSata drive for performance reasons - however, the laptop will not boot from the eSata port.
Thats why I came up with the idea of /boot on a usb stick, and / on the eSata.
I can't see a reason why that wouldn't work, but I am unsure of how to get there.

I could use a usb drive, but I really don't want to sacrifice the performance.

I'll start looking into it properly over the next few days - if I make any progress I'll let you all know.

Thanks.

---

### Post by rw1968 on 2010-10-07
Psusi - you're right - it is hard to believe - but I have checked and even done a bios upgrade to make sure that Dell haven't 'corrected their mistake' since I bought the laptop.
eSata boot is not supported according to the documentation and the bios menus.

---

### Post by psusi on 2010-10-07
Did you just try plugging in the drive and seeing if it shows up on the boot menu?  It should just see it as a second internal disk.

---

### Post by rw1968 on 2010-10-09
Yes tried that - it will not boot from eSata.

However, although the bios can't boot from eSata, I don't see why grub won't recognise it so I'm going to try grub on a USB stick booting ubuntu on the eSata.

My theory is that without the usb stick, it will boot from the internal HDD. With the usb stick I will configure grub to boot the ubuntu installation on the eSata HDD. As long as the ubuntu install does not touch the internal HDD I should be fine.

This sounds more feasible than my previous idea - opinions anyone?

When I get round to it I will post any interesting results here.

---

### Post by ottosykora on 2010-10-09
>Oh, that's hard to believe. He should check again. If it can boot from an internal sata drive it should be able to boot from an external one. It doesn't really know the difference.<

very common, the external ports are often made via different sata port and booting is there disabled permanently.

---

### Post by psusi on 2010-10-09
> **ottosykora said:**
> >Oh, that's hard to believe. He should check again. If it can boot from an internal sata drive it should be able to boot from an external one. It doesn't really know the difference.<

very common, the external ports are often made via different sata port and booting is there disabled permanently.

Usually it is simply one of several ports on the controller that is simply wired to an external port.  The bios usually scans all ports on the controller for drives and doesn't care which ones are internal or external.  When you hit the right key it just gives you a list of all the drives it found to boot from.

---

### Post by louieb on 2010-10-09
Don't see any reason why you idea of putting /boot and grub on a USB drive and putting / (root) on the esata drive won't work.  Don't think it will hurt anything to try. You should be able to install without modifying anything on the internal drive. 

You'll have to use manual partitioning during the install.  I would suggest you use Gparted to set up the partitions on the USB and eSATA drives prior to doing the install. 

During the install you would select manual -  and tell the the installer which partitions to use for / and /boot.

When you get to the install summary page - be sure to use the <Advanced> button. There you tell the installer to put Grubs IPL code in the MBR of the USB drive. (You will want to do this because by default the installer will put the GRUB IPL code in the MBR of the internal drive).

---

### Post by Hairyloon on 2012-12-03
Mine is an E4300. I am sure I have had it boot from an external HD. I don't have one here, but I'll try later to check.

I've been wondering about installing an OS on an SD card. Anyone know if that will work?

---

### Post by oldfred on 2012-12-03
Back when this thread was working you could not boot from an SD card. But some newer computers may. Or check into plop. Best to start a new thread for details.

necromancy 
Closed, necromancy. Old thread closed.

From the Ubuntu Forums Code of Conduct.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

