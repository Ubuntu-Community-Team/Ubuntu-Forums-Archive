---
title: "dual-boot install ok until use Windows"
date: 2006-04-09
forum: Installation &amp; Upgrades
---

### Post by matth1j on 2006-04-09
Hi- trying out Linux for the first time, I've managed to install Ubuntu 5.10 off the installation disk alongside Windows XP Pro, and it looks ok. That is, on power-up GRUB offers me the choice of the various Ubuntu options and XP. If I choose Ubuntu, it's fine.

However, if I choose XP, the first time it's also fine. However, after quitting XP, from then on I can't do anything. That is, it doesn't even get as far as GRUB- it just keeps restarting.

The first time this happened, I reinstalled both XP and Ubuntu, but it didn't help. The next time, I discovered the Windows recovery console FIXMBR command, which at least allowed me to boot up into XP ok without re-installing it.

At one point I tried removing the DVD drive, just to see if it could be causing a problem. This didn't fix it, but the behaviour changed slightly- it hung with GRUB displaying error 21. This might just have been due to the missing DVD drive.

System info: ECS K7S5A, Duron 1.6, 512mb, 80Gb Maxtor (master) + 6.4Gb Fujitsu (slave), XP Pro. Maxtor is NTFS, with partitions of approx 74Gb and 6Gb. I'm installing Ubuntu onto the Fujitsu, which is an older drive,  probably slower than the Maxtor. I'm creating a 5.5Gb ext3 root partition with the remainder for the swap partition.

Any suggestions would be very welcome :confused: 

Cheers
John

---

### Post by Kapre on 2006-04-09
John - Welcome to Linux. Nice seeing that we have the same specs (motherboard and ram wise - coz my CPU is only 1.3 G). Anyways, do you have 3 HD (Master, slave and XP) or you have Ubuntu (Maxtor - Master), XP (slave)? If you just have 2, make sure that when you install Ubuntu, let it handle the partitioning (of the slave? - if this is where you want to install it); giving is a bigger swap sometimes makes an error.

K

---

### Post by matth1j on 2006-04-09
Hi Kapre- thanks for the reply.
[QUOTE=Kapre]Anyways, do you have 3 HD (Master, slave and XP) or you have Ubuntu (Maxtor - Master), XP (slave)? If you just have 2, make sure that when you install Ubuntu, let it handle the partitioning (of the slave? - if this is where you want to install it); giving is a bigger swap sometimes makes an error.[/QUOTE]
I have 2 physical HDs:

1) Master- Maxtor 80Gb IDE 133, 2 partitions:
1a) 74GB NTFS, Windows XP Pro installation and most programs/files
1b) 6Gb NTFS, Windows swap file and some other files (mainly photos)

2. Slave- Fujitsu 6.4Gb IDE 33, for Ubuntu only

The last time I tried it, I partitioned the Fujitsu manually into a 5.5 Gb primary root partition and the remainder (~1Gb) into the logical swap partition. However, I think I let Ubuntu do it automatically at least once, but it didn't seem to make any difference.

Also, at first I had the Fujitsu (IDE 33) on the 2nd IDE as the slave to the DVD drive, so it wouldn't slow down the main Maxtor (IDE 133) drive on the 1st IDE. Then I read in some post somewhere that this might be causing the problem, so I switched the Fujitsu onto the Maxtor's IDE, which is where it is now.

John

---

### Post by Kapre on 2006-04-09
John - Thanks for the info. Let's try to do it like this. Try installing "server" 1st on your slave (make sure it is slave to the 1st HD and not the DVD - or make it master on the DVD). Post what happens. 

I'm not sure if making it slave to the 1st HD would slow your 1st HD.

K

---

### Post by matth1j on 2006-04-09
[QUOTE=Kapre]John - Thanks for the info. Let's try to do it like this. Try installing "server" 1st on your slave (make sure it is slave to the 1st HD and not the DVD - or make it master on the DVD). Post what happens. 

I'm not sure if making it slave to the 1st HD would slow your 1st HD.

K[/QUOTE]
Ok- did a server installation onto the slave (Fujitsu 6.4Gb) drive, selecting the "erase drive and let Ubuntu do partitions" method (but not using the LVM, whatever that is).

Seemed ok, selected Ubuntu from GRUB list and got basic command line interface. Logged out, reset PC manually (not sure how to reboot) and repeated - back into Ubuntu command line.

But... reset PC again and this time chose Windows. Went in to Windows ok. Used Windows to restart PC- this time, as before, never got into GRUB - PC just kept restarting until I inserted the Windows XP disk and went into the recovery console and ran FIXMBR. ](*,)

Do you think it might be something to do with what type of NTFS volumes are in use on the master (Maxtor 80Gb) drive? At the moment they are 'simple dynamic'.

---

### Post by matth1j on 2006-04-09
...and I forgot to say that I do get one error message during Ubuntu start-up:

ldm_validate_privheads(): Cannot find PRIVHEAD 1

although it doesn't cause any obvious problems.

---

### Post by matth1j on 2006-04-10
If it's something to do with GRUB, perhaps I should try LILO :-k 

If I do a simple Ubuntu server re-install, what command(s) should I enter to replace GRUB with LILO?

---

