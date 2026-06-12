---
title: "Ubuntu and Win7 Dual Boot- Help Needed"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by miketino on 2012-09-19
okay, so i installed ubuntu on a desktop using a bootable USB, using this tutorial: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

so as the tutorial explains, i created a seperate partition on my hard drive, then created the usb boot drive, and installed it from that. this is where i think I started to go 'off-piste'. I selected the 'install next to' option to dual boot it with windows 7, and after it installed everything was fine, however it never asked me where i wanted to install it to, although im kind of sure its on the new partition, and when in ubuntu, the windows partition comes up at the side as a removable device i guess. 

Ubuntu is running great, however, and this is my problem, when i boot the computer up, i dont get the bios screen that i am accustomed to with other dual boot OS's, instead it takes me straight into ubuntu, into the Ubuntu os screen where i can choose past versions of ubuntu etc, and it also has two windows 7 options, which when selected take me to the pc manufacturers windows 7 recovery suite.
I really need windows 7 alongside Ubuntu, so i would like to uninstall ubuntu and reinstall it when i know more what i am doing, and could have probably used Wubi. 
so, how do i go about uninstalling?

any help would be greatly appreciated, thanks

also, its 64 bit in case that matters

---

### Post by darkod on 2012-09-19
That screen you are getting is not the ubuntu os screen, that's only the bootloader. Since windows bootloader can't boot linux, it's usually much better to use the included grub2 bootloader.

It will also create an entry for windows, in fact for all windows type boot files it can detect in the computer. That's why it creates one entry for the recovery partition too, since that partition has boot files.

But the other windows entry should be your win7 and should work. It doesn't ?

One option is if the win7 install is somehow corrupted, so when selecting the entry it is opening some type of repair screen instead of booting it.

Are you sure you want to remove ubuntu that soon?

---

### Post by miketino on 2012-09-19
okay, thanks, i did only check one, but i just assumed if it wasnt the first one, it wouldnt be the second, i'll check now.

i fully intend to reinstall it anyway, but i'd just rather set it up exactly how i want it before i start spending time changing settings and stuff, i want to have ubuntu as my main os, but i do need windows some times as i play games and produce a bit of music

---

### Post by miketino on 2012-09-19
okay, thanks, i did only check one, but i just assumed if it wasnt the first one, it wouldnt be the second, i'll check now.

i fully intend to reinstall it anyway, but i'd just rather set it up exactly how i want it before i start spending time changing settings and stuff, i want to have ubuntu as my main os, but i do need windows some times as i play games and produce a bit of music

---

### Post by darkod on 2012-09-19
Whether it's the first or second will depend whether the recovery partition is before or after the win7 system partition on the disk. The grub2 os-prober checks them in order.

If you want to uninstall, you can, but that would involve putting the win7 bootloader back to the MBR. For that, you better boot win7 once and make a rescue cd. That can help you do basic repair but not reinstall the whole OS (you have the recovery partition for that).

Once you have win7 booting with the windows bootloader, you can delete any ubuntu partitions left on the disk, if you want to remove it.

---

### Post by miketino on 2012-09-19
thats worked great, cheers dude. i was really scared for a moment i'd lost my windows haha, i've decided im going to keep the ubuntu as it is for at least the week then decide whether i keep it or change it, but thanks again for helping me with my stupid mistake

---

