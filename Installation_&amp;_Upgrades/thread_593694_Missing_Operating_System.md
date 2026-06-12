---
title: "Missing Operating System"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by noteapot on 2007-10-27
I am computer literate have 3 disks in my system but know nothing much about linux

Disk 1 = Vista
Disk 2 = XP
Disk 3 = spare

Default boot disk is Vista but I F8 to get a boot menu to boot from other disks.

I wanted to do an install of ubuntu on the 3rd disk rather than repartion exsiting disks

I downloaded and ran the latest ISO and did everything default partioning disk 3.  I did not see the grub option on first install.

On reboot I did F8 and rebooted from disk 3 and got operating system not found.

I then rebooted found that vista would not boot either  (grub error - sorry didnt note it) so i did an MBR fix  which made vista work again..

I then deleted all partions on drive 3 and renstalled Ubuntu  with default settings for partioning but on advanced settings turned off grub.

After re-install i still get missing operating system.

If i run the partion manager from the install CD I can see two partions on disk 3. One is swap and one is labelled boot.  

I am guessing this is something to do with me not using the default primary disk for installation. Is there a way i can edit a config file somewhere to boot from drive 3 ?    I do not want to use a software boot manager if i can avoid it having trashed disks with these before.

---

### Post by Pumalite on 2007-10-27
Use Alternate CD. Install and point to disk 3 to install grub. Or, disconnect other 2 drives and install normally.

---

### Post by noteapot on 2007-10-27
Sorry what is Alternate CD ? 

I look on the download site and for Intel 32 bit there is only one download .  

Is there no way to say -

" dont use Grub at all but just install on this disk I specify " apart from unplugging the other disks ? 

I can do it but hardly user friendly

---

### Post by Pumalite on 2007-10-27
Well, Linux has a learning curve. Download from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign -Start Download-

---

### Post by oldos2er on 2007-10-27
If you don't install Grub, you'll have no way to boot Ubuntu. It's possible to configure grub to boot all your OSes; there are people on this forum doing so.

 "User friendly" really doesn't apply here--you want three operating systems but do not want to use a boot manager--that is not possible. It's just a question of research, and learning. Google and this forum's 'search' are your friends.

---

### Post by Crandom on 2007-10-28
sevral things could be wrong:

1. Your MBR is corrupted. On the Live CD, go to Aplications, Acessories, Terminal. Type:```
sudo apt-get install lilo
``` to install the LInux LOader. don't worry - we're not going to replace GRUB with this although you could if you wanted. After it has install with all the dependancies as well, type:```
sudo lilo -M /dev/hda3
```ASSUMING THAT YOUR "Disk 3" IS /dev/hda3 - if you had xp preinstalled you may have a backup of xp, called /dev/hda1, in which case choose /dev/hda4. That will repair your MBR if it is broken.

2. Reinstall Ubuntu, but this time when you get to step 7, select the button which says "Advanced" and chouse to install it to```
/dev/hda3
```instead of ```
(hda)
```AGAIN ASSUMING /dev/hda3 IS THE CORRECT DRIVE.

3. GRUB may hate you for not installing on the top partion of your drive. Make a small (50mb) ext3 partion at the top of your drive using GParted and boot from that and install GRUB there, whatever the /dev/hdaX will be, where the X is the number of the partiton.

Hope that helps.

---

### Post by noteapot on 2007-10-29
"User friendly" really doesn't apply here--you want three operating systems but do not want to use a boot manager--that is not possible. It's just a question of research, and learning. Google and this forum's 'search' are your friends."

I guess there are definitions of boot manager.   I dont want to use a software boot manager to manage my XP and Vista systems   when there is an excellent and easy to use boot manager in the firmware of my PC.  

From my  practical point of view putting an open source boot manager that i dont understand in front of paid for software that i earn my living from is a risk  already proved by my breaking Vista using a  default install .  I may be dumb regarding Linux but I want to protect  myself from my dumbness.  

Since there was an option to exclude grub in the advanced options  I assumed it was possible to boot  ubuntu without grub  - my mistake but a fair one i think.

How i solved this was 

1: Make the new disk active from the windows vista disk management software - I had assumed that gpartd did that with the boot flag set  - my mistake. 
2: Disconnected   the XP and Vista drives
3: Installed Ubuntu with default everything and  grub flag set   (see samsung disk problem below)
4: Reconnected Vista and XP drives.
5: Boot to required OS using [F8] bios function
6: Resize Ubuntu partition down and format the rest of the disk as NTFS 

(6) was because all efforts to install ubuntu with anything other than the default partitions failed ( i really think the swap should come first on the disk ) 

I can now boot to any of 3 OS without having to go through grub.

There was also a unique feature of the samsung HD501LJ SATA disk i was using for ubuntu  where it would not allow itself to be recognised as a primary IDE disk in IDE mode in the ASUS  bios without another disk installed.
This could only be solved by setting the bios mode to AHCI while installing Linux to the single samsung disk and then setting everything back to IDE to allow Vista and Xp to boot . To be honest I didnt full investigate this as a cause of installation problems  (24 hours to install an OS was enough) but i note it here in case anyone else encounters this with samsung.

---

### Post by Pumalite on 2007-10-29
'Or, disconnect other 2 drives and install normally.'
It's what I suggested in post # 2

---

### Post by noteapot on 2007-10-31
'Or, disconnect other 2 drives and install normally.'


Which didnt work thus my point about having to make the disk active

---

