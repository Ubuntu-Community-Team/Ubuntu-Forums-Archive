---
title: "Installing 20.04 on USB drive"
date: 2020-11-16
forum: Installation &amp; Upgrades
---

### Post by michael239 on 2020-11-16
Hi everybody

It&#8217;s been ages since I had to post a question on Ubuntu Forums. That in itself proves the quality of Ubuntu.
Therefore this question may look a bit &#8216;easy&#8217; or obvious-, certainly for one who knows the answer.
I wanted to create a fully working Ubuntu 20.04 for use on desktop computers on an external (USB) drive. I found that the utility/program MKUSB does the trick. It worked fine.
To create it MKUSB used ubuntu-20.04.1-desktop-amd64.iso.
But what I see know is the 20.04 &#8211; how must I put it &#8211; &#8216;trial&#8217; installation, not the fully installed program. It asks to install 20.04.
Now, before I want to proceed with that (I&#8217;m of the very suspicious kind) I would like to know whether the install program will restrict it&#8217;s activities to the external drive (SDB) where it is running? Will it not try to modify anything whatsoever on my internal drive (SDA) where 20.04 has been already installed? No chance it will screw up my desktop?
Please bear with me ...

---

### Post by CelticWarrior on 2020-11-16
MKUSB uses dd underneath to make "live" or "live with persistence" USB media. It isn't a full installation and no, you also can't install to the same USB.
You can use that USB to boot a live session from it and then install wherever you want, including in ANOTHER USB drive.

---

### Post by sudodus on 2020-11-16
+1

I'll add some details (including a link with more links) to the answer by CelticWarrior.

The easiest alternative (with for example mkusb) is to clone from the iso file to a USB drive and get a live-only drive. Things will not be saved, so I don't think this is what you want.

The next alternative is to use mkusb to create a persistent live drive. This is also rather easy, and you get a system that is portable and you can install application program packages as well as save files. But you cannot upgrade the kernel and the kernel drivers.

It is more complicated to install Ubuntu like into an internal drive, but into a USB drive, but it is not too difficult, and this way you can also get a portable system (between computers). Such an installed system can be updated & upgraded like any installed system, also the kernel and its drivers can be kept up to date. I think this is what you want, and you can find advice via [this link](https://askubuntu.com/questions/1267370/can-i-install-ubuntu-in-a-usb-stick-and-run-it-as-my-learning-machine-will-it-r/1267376#1267376) and links from it.

---

### Post by tea for one on 2020-11-16
> **michael239 said:**
> 
Now, before I want to proceed with that (I’m of the very suspicious kind) I would like to know whether the install program will restrict it’s activities to the external drive (SDB) where it is running? Will it not try to modify anything whatsoever on my internal drive (SDA) where 20.04 has been already installed? No chance it will screw up my desktop?


If you are the user of your external drive in a live session on your own PC, then anything that happens to your installed OS is in your own hands.
You are your own gatekeeper. 
Of course, you could make a mistake, then you would need the live session to correct the error.

---

### Post by ActionParsnip on 2020-11-16
Just install to the USB as you would an internal drive. The physical medium is irrelevant. Just remember to install GRUB to the USB stick as well

---

### Post by michael239 on 2020-11-17
Well, the above comments by ‘tea for one’ and ‘ActionParsnip’ put my mind at ease and I’m going to try the install – very carefully and watching every single step in the process.
I was thinking :
- If the installer would jump to my internal hard disk, then it would most probably give some warning like ‘Ubuntu 20.04 is already installed’.
or
- If the installation on the USB drive can’t be done, it would indicate that as well.

Thanks for your comments and I will post here how it went.

---

### Post by tea for one on 2020-11-17
When installing Ubuntu onto another disk, grub will be controlled by the last installation.

Therefore, you will need your latest grub to boot previously installed Ubuntu systems.

This can be repaired but it can also be avoided.

If possible, can you [COLOR="#0000FF"]de-activate, isolate or physically remove[/COLOR] your internal SSD/HDD?

Some UEFI Set Up choices allow de-activation of devices without physical removal.

Make sure you have backups of your data before you start another installation - this is essential.

---

### Post by oldfred on 2020-11-17
If UEFI, best to partition in advance & be sure to include an ESP - efi system partition on external drive.
Use gpt partitioning for UEFI, but you also can use gpt for BIOS/CSM/Legacy if you include a bios_grub partition.
When first changing from BIOS to UEFI, I included both ESP & bios_grub as first two partitions on every new drive including flash drives.

Then with installer choose Something Else install option. Choose (change button) your ext4 partition for / (root). 

Very old bug, but still current:
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

### Post by C.S.Cameron on 2020-11-17
> **CelticWarrior said:**
> MKUSB uses dd underneath to make "live" or "live with persistence" USB media. It isn't a full installation and no, you also can't install to the same USB.
You can use that USB to boot a live session from it and then install wherever you want, including in ANOTHER USB drive.

You can install Ubuntu to the same drive, the Live USB was booted from, Just boot the Live USB toram:
[https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from](https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from)

---

### Post by C.S.Cameron on 2020-11-17
**How to Create a Full Install of Ubuntu 20.04 to USB Device Step by Step**
Several examples:
[https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

### Post by michael239 on 2020-11-18
Thanks to all of you for the ample advice.
As I am not a &#8217;guru&#8217; in this matter, it will take me a lot of reading before I proceed with any of it.
So you may not hear from me for a couple of days, but &#8216;I&#8217;ll be back!&#8217;

---

### Post by DuckHook on 2020-11-18
@michael239

Please refrain from posting with nonstandard fonts or formatting. Such practices make it hard to read your posts, especially on mobile screens or small devices. Please use only the default fonts and styles.

---

