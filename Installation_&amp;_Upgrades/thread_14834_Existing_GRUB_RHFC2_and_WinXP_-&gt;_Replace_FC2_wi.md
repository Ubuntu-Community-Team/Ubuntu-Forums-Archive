---
title: "Existing GRUB RHFC2 and WinXP -&gt; Replace FC2 with Ubuntu"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by stardotstar on 2005-02-10
Hi all, I have done a bit of searching on this but I feel the need to put this question directly:

I have successfully installed Ubuntu on a dedicated Dell Notebook and am impressed; since I am running a Debian Stable server I want to use Ubuntu for my dev server and notebooks...

I have been using RedHat for years and currently have FedoraCore2 on my dual boot WinXP machine (a work one and one that I must be very careful of - not to blow XP away - mainly due to the detailed setup than data backup... anyway)

What do you think is likely to happen if I run the Ubuntu Installer and attempt to completely blow away the existing FC2 paritions and replace with a clean Ubuntu install?  Should the existing configuration of GRUB continue to work (or I mean can it be configured during install to recognise the XP after replacing the existing GRUB config and RedHat?)

Please advise - I am not that good on this boot stuff but havn't been bitten hard for a while so I am twice shy!

Thanks in advance,

Will.*

---

### Post by Buffalo Soldier on 2005-02-10
In my opinion if the Windows XP entry in /boot/grub/menu.lst remains the same, GRUB should have no problem booting it.

---

### Post by stardotstar on 2005-02-10
So... I can back up my menu.lst, do a standard install and the installer will allow me to configure the menu.lst before the reboot?

Does it detect the XP install as part of the process (my current install was on a clean system) or would I ignore the XP part till I booted into Linux the first time and then replace the menu.lst file at that time.  Then I would just have to be careful about the partitions during the install setup I take it?

(actually that is sounding ok  :-)  I think  :-? )

Thanks for the reply

---

### Post by Buffalo Soldier on 2005-02-10
From my personal experience, Ubuntu installer detected my WinXP. After installation, I had no problem rebooting into my WinXP. But others have not been so fortunate. I guess I was lucky that my harddisk and BIOS wasn't giving me too much problem.

My advice is that to browse through the forum and lookout for post of people having problem booting into WinXP. And compare their hardware with yours.

I can't guarantee anything but seeing that you manage to dual boot WinXP-Fedora, I think you'll be fine.

Anyway, try posting your hardware spec. Hopefully someone can give a better advice than my "guesses".

I'm using MicroStar motherboard (MS-6734), Phoenix-Award BIOS, and 20GB Samsung harddisk.

---

### Post by stardotstar on 2005-02-11
[QUOTE=Buffalo Soldier]From my personal experience, Ubuntu installer detected my WinXP. After installation, I had no problem rebooting into my WinXP. But others have not been so fortunate. I guess I was lucky that my harddisk and BIOS wasn't giving me too much problem.

My advice is that to browse through the forum and lookout for post of people having problem booting into WinXP. And compare their hardware with yours.

I can't guarantee anything but seeing that you manage to dual boot WinXP-Fedora, I think you'll be fine.

Anyway, try posting your hardware spec. Hopefully someone can give a better advice than my "guesses".

I'm using MicroStar motherboard (MS-6734), Phoenix-Award BIOS, and 20GB Samsung harddisk.[/QUOTE]
 I'm going to give it a go this weekend - and I'll post my config/specs/hardware and how I went with either a cry for help or a gasp of relief :-)  thanks for the input guys!

Will.*

---

### Post by Wim Sturkenboom on 2005-02-11
I installed it on a laptop next to WinXP and did not encounter problems. Also installed it next to Win98SE on a desktop and did not have any problems.

Just keep a copy (or printout) of your current menu.lst so you have something to compare against in case of problems.

---

### Post by stardotstar on 2005-02-12
For reference, the installer detected XP just fine and configured GRUB without any problems or intervention.

Well done and thanks for the encouragement guys! I am stoked.

Will

---

