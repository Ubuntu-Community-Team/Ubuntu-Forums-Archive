---
title: "Installing on a Western Digital My Book Essential 1.5TB USB drive"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by agaskins on 2009-12-23
I have installed Ubuntu 9.10 on my new Western Digital My Book Essential 1.5TB external USB drive (white light model). I made sure to install Grub to the USB drive (SDC). Yet when I boot up there seems to be no attempt to boot from the drive. I tried this with an older 320GB USB drive I had and it worked fine.

Any help here would be greatly appreciated!

Thanks,
-Adam

---

### Post by presence1960 on 2009-12-23
> **agaskins said:**
> I have installed Ubuntu 9.10 on my new Western Digital My Book Essential 1.5TB external USB drive (white light model). I made sure to install Grub to the USB drive (SDC). Yet when I boot up there seems to be no attempt to boot from the drive. I tried this with an older 320GB USB drive I had and it worked fine.

Any help here would be greatly appreciated!

Thanks,
-Adam

Can your BIOS boot from USB? If so you need to go into BIOS and set the USB to boot before the internal hard disk.

If that does not work do this: Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external plugged in that has ubuntu on it. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by agaskins on 2009-12-23
> **presence1960 said:**
> Can your BIOS boot from USB?

Thanks for the reply! My BIOS can definitely boot USB devices. I regularly use other USB enclosures and thumb drives. I also did this exact same procedure on a 320gb PATA drive in a USB enclosure and it worked fine. It just seems like the My Book isn't even getting hooked in to the boot process, despite explicitly specifying grub be installed to the drive at the last step of the install process (just like I did on the old USB drive that did work).

I will still do the other steps using your script and post the results here later today!

Thanks,
-Adam

---

### Post by Akavashi on 2009-12-23
As Presence said above, configure your bios (usually by pressing the delete button when you turn your computer on) to boot USB Removable Disks. Otherwise you can do the temporary option by pressing ESC, F10 or F12 and opening the Boot Menu (depending on what the startup process tells you), then select your USB.

---

### Post by presence1960 on 2009-12-23
> **agaskins said:**
> Thanks for the reply! My BIOS can definitely boot USB devices. I regularly use other USB enclosures and thumb drives. I also did this exact same procedure on a 320gb PATA drive in a USB enclosure and it worked fine. It just seems like the My Book isn't even getting hooked in to the boot process, despite explicitly specifying grub be installed to the drive at the last step of the install process (just like I did on the old USB drive that did work).

I will still do the other steps using your script and post the results here later today!

Thanks,
-Adam

OK, just checking even the obvious. You would be surprised at what some people do. I will wait for your results from the script as that will shed light on not only your setup but what is going on when you boot.

---

### Post by agaskins on 2009-12-23
> **presence1960 said:**
> OK, just checking even the obvious. You would be surprised at what some people do. I will wait for your results from the script as that will shed light on not only your setup but what is going on when you boot.

Presence1960,

Here are the results of the boot info script you asked me to run [attached].

By the way, I believe my SDA & SDB devices look funky because that is part of a 'fake-raid' array on this machine, which fwiw is an HP XW8200.

Thanks!
-Adam

---

### Post by presence1960 on 2009-12-23
> **agaskins said:**
> Presence1960,

Here are the results of the boot info script you asked me to run [attached].

By the way, I believe my SDA & SDB devices look funky because that is part of a 'fake-raid' array on this machine, which fwiw is an HP XW8200.

Thanks!
-Adam

Ahhhh, I see you have RAID, that could be the problem. I am sure there is a workaround but I have almost no RAID experience or knowledge.

It says GRUB is installed on MBR of sdc. You can try reinstalling GRUB to MBR of sdc again. Boot from the 9.10 Live Cd with external disk plugged in & choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo mount /dev/sdc2 /mnt
```
next run from terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sdc
```
Reboot & try to boot Ubuntu. If successful update GRUB menu by running in terminal ```
sudo update-grub
```

If that does not work then I suggest starting a new thread with a description that includes what type of RAID you have in the title of the thread- that way those knowledgeable in RAID set ups may see that. Sorry I can't be of more help, but I believe I can point you in the right direction to get the help you need.

---

