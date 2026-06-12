---
title: "grub not loading on new install of 12.04.4"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by tom-dean on 2014-03-22
I recently upgraded a research server from 10.04 as a complete new install. I had been using LVM but after loss of a hard drive I decided to move to Raid. The machine was a 2.0 Ghz 16 core (2 8 core options) with 3 1 TB drives and 32GB of ram. I added two more 1TB drives and
started with a fresh install of 12.04.4. I set it up as 978 GB on root (sda1), 32GB swap, and the remaining 4 drives as raid 6 mounted on /home. As far as I can tell, the install went without any hiccups. However it will not reboot. It gets past the bios splash screens to the point where grub should load, and then stops. I boot the cd in rescue mode and execute a shell in /dev/sda1 and everything is fine. I tried changing grub to be console (uncomment the appropriate line) and resintalled grub (update-grub & grub-install /dev/sda1 from within the /dev/sda1 shell). Still nothing. Tried the right shift key, escape key. But nothing but a blank screen. Used f8 to make sure the the correct drive was used to boot from.

---

### Post by kc1di on 2014-03-22
in the /etc/default/grub file are you sure you have the correct resolution set?

---

### Post by tom-dean on 2014-03-22
doesn't setting [FONT=monospace][SIZE=3][COLOR=#000000]GRUB_TERMINAL to "console" disable graphics and use a bios text terminal?

[/COLOR][/SIZE][/FONT]

---

### Post by tom-dean on 2014-03-24
I reinstalled again, this time with a separate 10G partition for /boot. Same problem.

---

### Post by Bashing-om on 2014-03-24
tom-dean;
Try installing grub outside of the raid arrays, so that bios can hand off to that known location. And yeah, that space is lost on the other members of the raid array.
Bios set to boot the drive that grub is installed onto and should then work.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-03-25
Best to see details, but I really do not know RAID.
Standard desktop installer does not include RAID drivers.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by tom-dean on 2014-03-26
Finally solved it. It appears to have been a loose cable.

First of all, grub was installed outside of the raid array. There are 5 drives.
One boot drive containing /boot, / and swap, and 6 drives using software raid6 on /home (i.e. no raid card).

I finally disconnected all of the raid drives at the motherboard and booted using only the boot drive and the dvd drive.
Works fine. Reconnected two of the raid drives. Boots into grub just fine. Reconnected the other two raid drives, boots
fine.

So somehow disconnecting and reconnecting the sata cables on the raid array solved the problem. Note that 
I never touched the cables connecting the boot drive or the dvd drive.  So somehow a loose connector
would allow the drive to past the POST (splash screen was reporting all drives connected and OK), and
the drives were visible and working onto when booting from the CDROM but prevents grub from loading from
a completely different drive.  Bizarre.

---

### Post by tom-dean on 2014-03-26
grub was installed outside of the raid array. I have 5 drives. 1 drive as the boot, root and swap
drive and the other 5 as a raid array on /home.

---

### Post by oldfred on 2014-03-26
I used to have that problem with my old PATA drives. Those 80 or 40 conductor cables would easily be bumped and I would partially disconnect a drive. It still would show, looked like it was connected, but a push on connect then firmly seated connector and it worked. That and how much I hate the old tiny jumpers on IDE/PATA drives is why I converted to SATA.

---

### Post by Bashing-om on 2014-03-26
tom-dean; Hey .

Glad ya got it sorted out. Perseverance pays off !

I too am going through a similar situation of intermittent recognition of drives by the operating system, bios does detect them -I too am considering going through the hassle of purchasing "high quality" locking sata cables and switching them out to see if that addresses the issue. First see what results when I clean install the forthcoming 14.04 release. Just saying I feel for you.

As you have found the problem, please mark this thread solved; 1st post -> thread tools. This aids others seeking a similar solution and helps keep the forum tidy.

Better
[INDENT][INDENT]and happy trails to you
[/INDENT][/INDENT]

---

### Post by tom-dean on 2014-03-26
Can't seem to type strait today. Just to clarify for anyone reading this thread in the future.

[COLOR=#000000]grub was installed outside of the raid array. There are 5 drives. 1 drive (the boot drive) as the /boot, rood and swap[/COLOR]
[COLOR=#000000]partitions and the other 4 as a raid array on /home. So I was not trying to boot off the raid array.[/COLOR]

---

