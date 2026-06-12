---
title: "Dual boot fail, live cd and boot-repair fail"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by SixOfOne on 2012-05-05
Simple problem, or so I thought, Windows XP crashed on a HDD running it and Ubuntu 11.04.
HDD is 640 gig, 200 for windows, 210 for Ubuntu and the rest NTFS storage area.
I knew that installing XP again would wipe the MBR so Ubuntu didn't appear as an option, but as i had both the live cd and the boot-repair cd to boot into i thought i would be fine..

Sadly this isn't the case,
1-boot to boot-repair and it hangs forever on searching, tells me to wait a few minutes, you can wait forever and nothing happens.
2-boot to live cd , instal and run boot-repair and the same thing happens.

Live cd allows me to see everything, but i can't seem to be able to fix the MBR.

So accepting i'm a Linux novice, but can take instructions, can anyone help me repair the MBR

Thanks in advance

For the record, i bought another HDD, 1T, installed XP first into a 300gig partition, created a second 300 gig partition for storage, an 8 gig swap, 20 gig / and the rest 180gig? /home.

As XP cant deal with Sata, i had to set the bios to native EIDE which was fine. Xp installed flawlessly, but i had problems with Ubuntu, turns out having dual monitors confused it and i had to go into the bios and chose "onboard graphics" to get see the installation.
For whatever reason, i can choose Ubuntu but it goes so far and the screens both go black..... doesn't matter if i choose PCI or onboard graphics.

I must be doing something different, as the pc in its current config has successfully installed both before.

---

### Post by oldfred on 2012-05-05
Your native IDE mode may prevent the system from booting beyond a certain point on drive.

I gave up on Windows when I converted to AHCI for my new SSD. Supposedly you can install SATA & AHCI drivers for XP but it is a lot easier to do as part of the install. SATA drives worked with my XP but AHCI does not.

Post link to results from Boot_Info.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by SixOfOne on 2012-05-06
Here is the result of the Boot Script Info, took time as i had to do it manually because Boot-Repair still refused to fire up.

What Boot-Repair does in order
1-check for updates
2-updates
3-scans system (OS prober)
4 scans system........ hangs forever here


Results.txt ended up being 21kb, forum limit is 19.5kb so i had to zip it.

Also the following may or may not be helpful

210 GB NTFS /dev/sdb1   (windows)
10 GB swap  /dev/sdb5
200 GB ext4 /dev/sdb6
extended 210 GB /sdb2
220 GB NTFS /dev/sdb3   (storage)

2nd drive
500 GB /dev/sda1

Win XP is for gaming, pure and simple, the rest of my PC needs are looked after by Ubuntu. Unfortunately Play on Linux / wine/ crossover have limited success.

---

### Post by oldfred on 2012-05-06
You installed grub to your sda1 data drive and it is trying to boot from that.

You have the Windows boot loader in sdb. You need to install grub to sdb and make sure BIOS is booting from sdb.

Boot repair should let you install it correct.

or liveCD:

sudo mount /dev/sdb6 /mnt

#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

Windows also thinks it is on rdisk(0) or first disk - see boot.ini. Grub tries to do a drivemap to make Windows still think it is first.

---

### Post by SixOfOne on 2012-05-06
Ok, will try that when i get home from work.

thanks

---

### Post by YannBuntu on 2012-05-06
> **SixOfOne said:**
> What Boot-Repair does in order
1-check for updates
2-updates
3-scans system (OS prober)
4 scans system........ hangs forever here

After "Scans system (os-prober)", there should be:
4 "Scans system (mount). This may take several minutes"
5 "Scans system. This may take several minutes"
6 "Scans system. Please wait few seconds"
7 Main window appears

Where does it hangs?

Also, please could you open a terminal, then type:
```
sudo boot-repair -d
```

then indicate the last output lines before freeze  ("pulsate" lines are not important)

These informations will help me understand why Boot-Repair hangs.

For solving your problem, please follow Oldfred advice.

---

### Post by SixOfOne on 2012-05-07
Yannbuntu, you are correct, there is a system mount check as well :)
From ....check updates/update/scan sys osprober/scan sys mounts takes under a minute, then takes 4-5 mins on scanning systems (this may take a few minutes) then hangs on scan systems (please wait a few seconds).. at the time of writing had been in this mode for 15 minutes.

---

### Post by SixOfOne on 2012-05-07
Here is the last section in terminal for "sudo boot-repair -d"

Hope it means something to you  :)

---

### Post by SixOfOne on 2012-05-07
Oldfred,

attached is the message i got following the instructions you gave.
remember i'm a novice, so i won't recognize any mistakes or missed bits :)

Cheers

---

### Post by YannBuntu on 2012-05-07
Thank you. Your log means that your system hangs when Boot-Repair is doing a "hash parted && sudo parted -l" command, which is strange. I have no clue how to solve that. Thanks anyway for your feedback.

EDIT: concerning your answer to oldfred, you mistook (forgot the last part) when typing the "sudo grub-install --boot-directory=/mnt/boot /dev/sdb" command indicated by oldfred, please retry.

---

### Post by oldfred on 2012-05-07
You have to mount the partition then update it.

```
sudo mount /dev/sdb6 /mnt

sudo grub-install --boot-directory=/mnt/boot /dev/sdb

```

---

### Post by SixOfOne on 2012-05-07
> **YannBuntu said:**
> Thank you. Your log means that your system hangs when Boot-Repair is doing a "hash parted && sudo parted -l" command, which is strange. I have no clue how to solve that. Thanks anyway for your feedback.

EDIT: concerning your answer to oldfred, you mistook (forgot the last part) when typing the "sudo grub-install --boot-directory=/mnt/boot /dev/sdb" command indicated by oldfred, please retry.

Thanks YannBuntu, I've been doing long hours, its 4 am and at the moment i can't see any difference between what i typed and what Oldfred wrote.

This bit "sudo mount /dev/sdb6 /mnt" i presume mounts sdb6, disk manager showed it already was.

Its a steep learning curve, i will try again tonight.

Again thank you for your time.

---

### Post by YannBuntu on 2012-05-07
You forgot a space before "/dev/sdb". You typed:
```
sudo grub-install --boot-directory=/mnt/boot/dev/sdb
```

The correct commands are:
```
sudo mount /dev/sdb6 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdb
```

(copy/paste is safer)

---

### Post by SixOfOne on 2012-05-08
Thanks,
I will get there ;)

---

### Post by SixOfOne on 2012-05-08
YannBuntu and Oldfred,  Thanks to both for your assistance.  I retried with the appropriate spaces and still got nowhere, so i looked to google and several forum solutions. 

One of them was [https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot) and another was on along similiar lines as far as chroot went. I followed instructions blindly substituting my sdb details, i figured i was at the point of reinstalling so had nothing to lose.  

I was getting lots of "is this dev mounted" replies, something about "aufs" and also about not specifying format? (ie ext4 or ntfs)

Then following the Grub2#ChRoot directions, i exited out, and retried Oldfreds original instructions and they worked :) (by this time i had tried to install grub on every drive and partition :rolleyes:)

I do apologize for not being able to be more specific, but in truth i had my laptop open googling every new thing that was coming up in terminal on my desktop pc .... looking at responses, then trying them. As i said i felt i had nothing to lose, all was backed up.

If i wasn't time and sleep poor due to work commitments, i may have been able to work out what tripped it in my favour , but for now i'm just happy it's all working again.

---

### Post by YannBuntu on 2012-05-08
Good job :)
I'm a little sad we can't understand what was blocking... maybe next time !

---

