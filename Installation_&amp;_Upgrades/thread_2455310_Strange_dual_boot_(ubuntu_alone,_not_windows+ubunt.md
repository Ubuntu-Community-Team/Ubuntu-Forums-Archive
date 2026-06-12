---
title: "Strange dual boot (ubuntu alone, not windows+ubuntu)"
date: 2020-12-17
forum: Installation &amp; Upgrades
---

### Post by nolerab on 2020-12-17
Hi,
I have an issue...
After wrong manipulation on Ubuntu (I think it's installation,remove of python3 in a bad way) strange things are done when I boot...(and terminal dosen't work anymore :-())
There's a first boot then purple screen then a new boot and the I enter in Ubuntu (18.04)
Using Disques, I notice that there's two strange peripherical : dev/mmcbblk0boot0 and dev/mmcbblk1boot1
I think (but I'm not sure...) that my issue comes from here...
Which one may I remove ? Both ?
A little help would be fine !
PS : excuse my english...
[ATTACH=CONFIG]287568[/ATTACH]

---

### Post by mIk3_08 on 2020-12-17
can you elaborate more further of what is exactly happen during your installation.
can you give some more details, so that the people in the community forum can easily help you with your concern. 
By the way thanks a lot for sharing your concern.

---

### Post by nolerab on 2020-12-17
So... I installed Ubuntu 18.04 instead of Windows (not in dual boot, Ubuntu alone). Installation was great. So I decided to install Python3. Good. But it was not python3 by default. So I tried a few things to do it without success.
Then I installed Spyder. So I noticed Terminal was not running anymore. I tried (again... sorry) some things... No success...
Finally, I rebooted. 
Ubuntu started but in a recovery mode (or maybe not, for sure there was only the shell without GUI)... I succeed to re-install the Ubuntu Desktop. But Terminal was always not running. 
I tried to reboot and I noticed this strange dualboot... And those strange dev'.
My idea is to re-install Ubuntu once again but I can't access the BIOS with the usual keypad and my USB live doesn't want to start...
I know, I'm not a linux's genius #-o... But I like it ! :D

---

### Post by oldfred on 2020-12-17
Your MMC is a type of drive, often used on low cost/inexpensive systems.
Your two partitions, an ESP - efi system partition as FAT32 and / (root) as ext4 are the standard default install for UEFI systems.

You should not need to do anything with python. And if you do, it can lead to major issues as python3 default version is used internally for many system activities. Changing that often breaks system. 

If system has fast boot on, which is an UEFI setting that assumes no system changes, you may not have time to press any key to get into UEFI or UEFI boot menu. You may be able to do a full cold boot where you totally shutdown system, if laptop remove battery and drain power. If tablet you may have a reset button or pin hole reset to force change to defaults. You then often have to redo UEFI setting changes.

---

### Post by nolerab on 2020-12-17
Hi. Thanks for your answer...
Too late... I did bad stuff with python3 and I guess it's the source of my problem...
I remove the battery but nothing better.
I tried to use boot repair but I can't launch it from a Live Usb... The computer don't want to start on LIve USB. I can't access to Grub with "e". I can't access to BIOS with the defualt keypad...
Is it possible to format the HD to re-install Ubuntu ?

---

### Post by oldfred on 2020-12-17
You need to be able to boot USB live installer.
Sometimes it gets corrupted and needs to be recreated. UEFI will only recognize correctly configured USB devices as bootable.
With UEFI you press Escape key after UEFI/BIOS screen and before grub menu normally appears to get grub menu. Some have to try multiple times.
Grub with UEFI has a menu choice that should boot into UEFI.

---

### Post by nolerab on 2020-12-18
Me again...
Can't start with Boot-repair on live USB... There's no keypad to access UEFI menu...
Because of my strange double boot ? 
When I start there's the logo of the computer then a purple screen then again the logo of computer then Ubuntu is launching...
I tried to press different keys at diffeent moment but without success :-(

When I installed Ubuntu I chose try Ubuntu then there was a icon on the Desktop : install Ubuntu.
Is it possible to obtain this icon once again ?

---

### Post by tea for one on 2020-12-18
> **nolerab said:**
> Can't start with Boot-repair on live USB... There's no keypad to access UEFI menu...
Because of my strange double boot ? 
When I start there's the logo of the computer then a purple screen then again the logo of computer then Ubuntu is launching...


After Ubuntu has launched and you have logged in, you can reach the UEFI set up as follows:-

Open a terminal [COLOR="#0000FF"]or[/COLOR] Ctrl Alt T
```
sudo systemctl reboot --firmware-setup
```

---

### Post by nolerab on 2020-12-18
> [COLOR=#000000]After Ubuntu has launched and you have logged in, you can reach the UEFI set up as follows:-[/COLOR]

[COLOR=#000000]Open a terminal [/COLOR][COLOR=#0000FF]or[/COLOR][COLOR=#000000] Ctrl Alt T[/COLOR]
[COLOR=#000000]Code:
[/COLOR]
[COLOR=#000000][FONT=&quot]sudo systemctl reboot --firmware-setup[/FONT][/COLOR] Great ! It worked. I entered in BIOS menu, chose Boot Option #1 UEFI : Built-in EFI, I disabled Boot Option 2 and Fast Boot. There is no UEFI USB or something else (USB choice is only in the Fast Boot)
My computer starts in a EFI Shell...
What must I do now ?
Sorry to be dumb... That's not easy but I try to listen :P And in english it's quite more difficult :-)

---

### Post by CatKiller on 2020-12-18
> **nolerab said:**
> So I decided to install Python3. Good. But it was not python3 by default.
Assuming you're eventually able to boot an Ubuntu USB, so that you can wipe what you've got and start over, Ubuntu 20.04 LTS uses Python 3 by default.

---

### Post by nolerab on 2020-12-18
> [COLOR=#000000]Assuming you're eventually able to boot an Ubuntu USB, so that you can wipe what you've got and start over, Ubuntu 20.04 LTS uses Python 3 by default.[/COLOR]
That's what I want !
How can I boot on LiveUSB from the UEFI Shell so ?

---

### Post by tea for one on 2020-12-18
> **nolerab said:**
> Great ! It worked. I entered in BIOS menu, chose Boot Option #1 UEFI : Built-in EFI, I disabled Boot Option 2 and Fast Boot. There is no UEFI USB or something else (USB choice is only in the Fast Boot)
My computer starts in a EFI Shell...
What must I do now ?
Sorry to be dumb... That's not easy but I try to listen :P And in english it's quite more difficult :-)

Even fluent English speakers often misunderstand each other, especially with PC terminology, acronyms etc...........:)

If you are in [COLOR="#0000FF"]Internal EFI Shell[/COLOR], type **exit** and you may reach the Boot Menu.

It's very difficult to give exact advice about the UEFI set up on PCs because every vendor has different configurations.

In a nutshell, in order to re-install completely, you need:-

Ubuntu installation USB stick
PC configured to boot from USB first

As you do not have a working device at the moment due to your Python misadventure, there is little choice other than to persevere with the UEFI USB settings until you manage to boot a **live** session.

---

### Post by nolerab on 2020-12-18
OK. I'm searching again...
I'll tell you.

---

### Post by nolerab on 2020-12-19
I'm happy.I finallay succeeded to find how to boot on a USB. It was on the UEFI/BIOS menu. I could reinstall Ubuntu 20 without porblem. It works ! I'm happy :D :D
Thank you very much for your support 
I promise, Iwon't touch python 3 anymore... I'm afraid of Snake right now :lolflag:

---

### Post by tea for one on 2020-12-19
That's good news - Don't forget to mark the thread as solved (to help other users with similar problems).

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

