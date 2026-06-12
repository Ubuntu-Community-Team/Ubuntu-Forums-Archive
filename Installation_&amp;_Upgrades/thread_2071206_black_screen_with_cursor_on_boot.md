---
title: "black screen with cursor on boot"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by lryansjr on 2012-10-14
hello the problem i have is that i am trying to boot ubuntu off of a usb external hard drive. it has 2 partitions but only 1 14GB is used for ubuntu. i have tried the linux live usb installer run from my laptop and that seems to work as the laptop will boot from the hard drive just fine. the system that i want to use it on has no internal hard drive ( its being RMAed now ) so i used the F8 boot menu the bios reads the drive fine but all i get is a black screen with a blinking cursor i even let it run for about 10 mins to see if it would load but it did not. does anyone know what is going on or how to fix it ?

---

### Post by martialartist81 on 2012-10-14
I'm actually having this exact same issue, however, mine's far more trouble-shot than yours.  Here's my low-down:

Installing 12.04.1 (tried USB loader, CD and DVD installations) all experience the exact same blank screen with blinking cursor.

- Originally, I was getting large screens of text dumps, like the kernel was labeling IRC's for the drives and such.  It would hang on a couple different spots, however, I don't have that off-hand.  What I did try, was to remove the USB WiFi adapter that I have.  That took away the text dump walls, however, brought me back to the Blank-screen-blinking-cursor.

- The initial "purple splash" screen with keyboard logo = (person) on the bottom of the screen does show up.  After approx. 15-25sec, it goes to the blank-screen-blinking-cursor.

- Swapped CD/DVD drives that I've attempted to boot from, doesn't matter what the drive is, experiencing the same issue.

- Swapped usb slots (both front, three of four in the back), same issue.

- Checked md5sum and its a correct match.

- Able to load the iso to Oracle VirtualBox AND QemuManager and create VM's without issue (both DVD and CD versions).

I'm open to suggestions and thoughts.  Hopefully someone will point out where I'm missing!


UPDATE:

I was able to get 11.10 64-bit installed without as much of a single hiccup using USB.

To lryansjr, you might want to try that route and "upgrade" the installation once you installed it.

---

### Post by lryansjr on 2012-10-14
I have not even been able to get to the purple screen, one major differance is that i have no cd drive. now i may be doing something wrong in the installation but i am trying to boot from the usb drive alone, no internal HDD or cd rom drive. i am semi new to ubuntu and new to using it off usb. is there a way to install it using my laptop to the usb drive then boot it on a PC with no cd rom drive?

---

### Post by amillionsheep on 2012-10-14
I am getting the cursor at boot as well; however, I had 12.04 running fine on this same netbook after upgrading from 10.04. I installed a different HDD (with Win 7) and used a USB drive to overwrite the Win 7 install and install 12.04 by itself on this HDD. The ONLY way I can get in to this install is by booting to the installation USB (pendrive) and it somehow loads the 12.04 install from the HDD (very weird).. I don't want to have to use a USB drive to boot to my HDD everytime. Does anyone have a clue what is going on?

---

### Post by martialartist81 on 2012-10-15
> **lryansjr said:**
> I have not even been able to get to the purple screen, one major differance is that i have no cd drive. now i may be doing something wrong in the installation but i am trying to boot from the usb drive alone, no internal HDD or cd rom drive. i am semi new to ubuntu and new to using it off usb. is there a way to install it using my laptop to the usb drive then boot it on a PC with no cd rom drive?

If you're using a "netbook" or similar, you might want to dig around and see if others have the same hardware/model that you do and have gotten Ubuntu (and whatever version) to work.  

Have you tried loading 11.10 to a USB and seeing if it'll load the LiveCD that way yet?  That's how I got mine to work; had to update the install after I booted into it and now I'm up and running.  Annoying little extra steps, but hey... fixed the problem.

---

### Post by martialartist81 on 2012-10-15
> **amillionsheep said:**
> I am getting the cursor at boot as well; however, I had 12.04 running fine on this same netbook after upgrading from 10.04. I installed a different HDD (with Win 7) and used a USB drive to overwrite the Win 7 install and install 12.04 by itself on this HDD. The ONLY way I can get in to this install is by booting to the installation USB (pendrive) and it somehow loads the 12.04 install from the HDD (very weird).. I don't want to have to use a USB drive to boot to my HDD everytime. Does anyone have a clue what is going on?

It's possible (though without a LOT more detail, this is just a guess) that you've installed Ubuntu to the actual pendrive.  If that's not the case, then I'm scratching my head for you as well.

Here's what I'll ask:

- Are you using one physical HDD (assuming so), and if so, can you see the partitions when you boot into Linux?

- Can you still boot into Windows without issue (and the pendrive not plugged in)?

- There's a possibility that grub installed away from the MBR (Window's Master Boot Record) and that could be why you're unable to load to grub boot menu (giving you the option to choose Windows or Ubuntu to load).

- Surf around in that USB stick... wonder if grub installed there (and/or the OS installed there; not unheard of, especially since I did the same thing not 6mo ago by mistake!)

---

### Post by lryansjr on 2012-10-15
> **martialartist81 said:**
> If you're using a "netbook" or similar, you might want to dig around and see if others have the same hardware/model that you do and have gotten Ubuntu (and whatever version) to work.  

Have you tried loading 11.10 to a USB and seeing if it'll load the LiveCD that way yet?  That's how I got mine to work; had to update the install after I booted into it and now I'm up and running.  Annoying little extra steps, but hey... fixed the problem.

its not a netbook its a destop PC that i am building but the HDD was bad so i had to RMA it. it has no cd drive so i cant boot from a live cd, its odd because the laptop i am using for this post boots fine from the same installation but it has a internal HDD with windows 7

---

### Post by martialartist81 on 2012-10-15
Oh, I understand.

From this point, without a working HDD, there's not much you can do other than try and run a LiveCD off of the USB.  

Try and use a USB of 11.10 and see if that'll load.  You could also try to load a beta of 12.10 and see if that works too.  Since 12.04 doesn't work, I'd suggest going after another version to see if that will.  

Otherwise, keep troubleshooting hardware.  If you have anything (other than a keyboard or mouse) plugged into a USB slot, unplug it (webcam, wifi adapter, etc).  Then reboot and boot into the USB and see if that gives you anything different/new to work off of.

---

### Post by amillionsheep on 2012-10-15
When I boot to the installation USB, it takes me to the 12.04 install on the HDD. Once there I can use it like normal (I even eject the USB pendrive). I checked the partition and there seems to be just one (320gb ext4). I wiped Win7..

EDIT: Yes it is just one 320gb HDD in a AAO D250 netbook. I took the 160gb drive out that has a dual setup of Win7 and 12.04 (upgraded from 10.04) and it boots fine. This fresh install of 12.04 on the 320gb HDD is what is giving me issues..

---

### Post by martialartist81 on 2012-10-16
Check the USB stick... see if GRUB installed to that instead of your MBR.

That's really the only thing that I can think of... but then again, I'm still not that hugely savvy with installs yet.

---

### Post by amillionsheep on 2012-10-17
Grub is on the pendrive, but it just has the pendrive menu you see at first boot to the installation USB..

---

### Post by martialartist81 on 2012-10-17
If the Pendrive has grub installed on it, rather than grub being installed on the HDD, that's why it won't boot to Ubuntu unless the USB is plugged in.

---

