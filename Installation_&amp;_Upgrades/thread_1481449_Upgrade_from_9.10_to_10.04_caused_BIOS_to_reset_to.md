---
title: "Upgrade from 9.10 to 10.04 caused BIOS to reset to default"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by _Scoridd on 2010-05-12
My Laptop is Lenovo T60. I have 2 partitions C:\ (~60 GB) D:\ (~5 GB) 
 
On C:\ is Win XP and a Wubi install of Ubuntu.
D:\ is just for storage.
 
This is what happened during my upgrade - apologies it's so long and not all info is 100% accurate - I'm reciting from memory as best I can.
 
Upgrade from 9.10 to 10.04 (release not beta) – stopped at a certain point in the installation (around 60% I think). Ubuntu would then not boot. Replacing c:\wubildr and c:\wubildr.mbr with the ones in c:\ubuntu\winboot\ sorted this issue out. 
 
Next, I kept on getting a exclamation mark in a triangle warning that the system is out of date. Upon opening the upgrade manager it tells me system is up to date. So, I terminal’d "sudo aptitude update" then "sudo aptitude upgrade"
 
sudo aptitude update – completed, no issues
 
sudo aptitude upgrade – was generally ok but upon identifying the Ubuntu kernels and my windows xp, a few lines after it reported something like "unrecognised block ?????????, 23????????f, ??????????" (this isn’t exactly what it reported but something very similar). At the end of the upgrade, terminal told me upgrade was successful but there was one warning.
 
Now, what happened next is where things really started to go wrong.....
 
System started up fine, selected Ubuntu in the windows bootloader - but before it got to the Grub menu selector the computer froze and everything went black – like it turned off but power light was still on.
On start up, before any start up screen appeared, computer warned – "LAN device not initialised or corrupted"
Then, "Intel Boot Loader cannot begin – restarting" - the computer restarted and took me straight to BIOS set up.
 
In the BIOS, I disabled the LAN device and enabled all extended memory checks and diagnostic mode. This stopped the previous warnings and allowed me to get to the OS selection screen. Selecting windows started the boot, showing the windows xp start up screen but almost immediately Blue Screen of Death.
 
Selecting Ubuntu done weird things. The computer froze and everything went black – like it turned off but power light was still on. Never reached Grub menu or the Grub CLI. 
 
After lots of BIOS setting changes, failed start ups and worrying system beeps, I realised what was happening....
 
Everytime I tried to boot Ubuntu it would do this weird freezing thing then when the computer rebooted, all the BIOS settings had been returned to default. The "LAN device corrupt" error I was getting was something to do with my default BIOS/LAN Device config.
 
Windows wouldn’t boot and Win XP boot disk wouldn’t recognise my hard drive because the BIOS setting were repeatedly returned to default (so my SATA HD was returned to AHCI mode). Changing my HD to compatibility mode, I was able to load the Win XP boot disk and do a ‘FIX MBR’. I also ran ‘fdisk –l’ which completed ok but did return ‘There were one or more errors’. Knowing that Windows XP is generally freaked out by the wizardry that Wubi performs, I put this down to the EXT2 disk image created by Wubi and ignored it.
 
I can now boot Windows XP normally. If I try to boot Ubuntu, it takes me to the GRUB CLI. If I type ‘boot \[TAB]’, I get a list of directories which looks like my Ubuntu install. However, I am now very cautious of what to do next (full back up is my first port of call!). I think I will remove the Wubi install and install Ubuntu 10.04 on it’s own partition. However, I wanted to post this so I could get an insight into what might have happened or help anyone else who might have the same issue.
 
I am fairly new to Linux and admit that it could have been something I done but it seems that nothing I done was too out of the ordinary. In the interest of learning, can anyone suggest what might have happened here? It’s worrying that the failed Ubuntu boot caused a default of my BIOS settings.
 
Also, can anyone tell me - can I boot from the live CD then mount the root.disk from my Wubi install? Or if I install Ubuntu on a separate partition and keep a copy of the root.disk from my Wubi install. Is there any way I can access it and extract the files? 
 
Thanks – Ubuntu rocks but Wubi has been a royal pain the ar$e.

---

### Post by _Scoridd on 2010-05-12
Ok, sorted. I'm back in Ubuntu as I'm typing this. I spoke to a friend at work today who told me of similar issues with his Ubuntu Server.

On resolving, it appears many of my problems were with the Grub update. After a fair bit of searching, I found the answer by doing this.... 

[http://www.omaregan.com/?p=583](http://www.omaregan.com/?p=583)

which was a fix for one boot only - and then this....

[http://www.omaregan.com/?p=608](http://www.omaregan.com/?p=608)

Which seems to have sorted it (touch wood). Still, no idea what the BIOS resets were all about. I guess the update done some funky stuff to the boot sectors and my Lenovo was particularly allergic to the changes. I'd still be interested to know if anyone can shed any light on the subject.

---

