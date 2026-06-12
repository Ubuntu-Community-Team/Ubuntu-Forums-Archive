---
title: "Gparted and DMRAID problem"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by dschultz on 2007-04-05
I've been a Windows user all my life and am currently a Network Administrator for a grocery supply company. I'm great with all flavors of Windows.

At home I have a powerful system that I recently installed Windows Vista X64 Premium on. I can't say this enough, Vista is total garbage. I've never been so unhappy with a Windows O/S in all of my life. I've had it, enough is enough. I'm moving to Linux. After reading through countless web pages full of opinions on which version of linux to install and I've decided to go with Ubuntu.

I had almost no problems installing Ubuntu on my laptop. The only problem is my built-in camera and I can live with that. I already spent hours digging around only to discover the camera is just not supported because nobody has ported the drivers for the camera's chipset. Okay, I need to get to the point here...

My desktop PC has been a real challenge and I'm at the point of frustration. So, here I am signed up for the forums and posting my challenge:

I have a SATA raid controller on the motherboard. If it's fake... okay great... I can live with that even though I dropped $200 on the MB thinking it was going to be blazing fast. I want to install Ubuntu 6.10 on the desktop. I have 3 SATA drives plugged into the SATA RAID 1,2,3 slots on my mother board. Drive 1 is 300gb, Drive 2 is 300gb, and Drive 3 is 400gb. In the raid controller which loads a config in the bios during POST I was able to group all three hard drives and set them up for a Raid-0. I know, I'm living on the edge with Raid-0 but I'm going for performance here.

I first tried the standard Live CD install and when Ubuntu loaded up from the CD, I went with the little "INSTALL" shortcut on the desktop. This gave me an option to install on ONE of the three drives... so.. it doesn't see the raid-0 array as one big 1 Terabyte drive... choosing manual doesn't help.

I read that 7.04 supports SATA raid better than 6.10. I downloaded the CD, burnt and did the "Install" shortcut from the desktop. Same thing, doesn't see it as a RAID-0 array. I only have the option of installing Ubuntu on 1 drive.

I found THIS guide for installing my SATA raid-0 while booted into Ubuntu live. I followed each step, very carefully and in the order the steps are presented. When I start up GParted I do NOT see the raid array as the guide shows. Instead, I only see the 3 separate drives. So, this guide doesn't do anything for me because it dies when I try to look for the /dev/mapper/XXXX in GParted.

I went ahead and did the sudo dmraid -ay command and it displayed:

RAID set "SIL_ahaeaeccajch" already active

When I browse to "/dev/mapper/" I can see that SIL_ahaeaeccajch is in there but it has a red [X] over it.

I found a guide that says I needed the "Alternate Live" CD so I downloaded that and burnt that to CD. When I got to the part where I setup the drives I was very confussed. Boy do I miss the ole fashioned FDISK in dos... anyway... have hours and hours of looking around, researching, and reading through countless guides I sort-of figured out that I need to setup each drive as RAID - K with mount option turned ON and each drive needs to be LOGICAL as opposed to PRIMARY. Now, I get my raid array showing up as a nice big 1 Terabyte drive but... when I create the SWAP partition... it tells me that the other 985gb are Unusable... *sigh* So I cannot create the swap and /root on the 1TB raid-0 drive I created in the confusing gui-shell linux thingy. I know I'm a noob and I'm willing to go through hell and back in order to start using linux even though I know I'll continue going through hell to get my programs and games to work (wish it were easier). The only option I see at this point is to ask for help or just forget using my nice raid feature and install Ubunto on 1 of my 3 disks and let the others just... do nothing? I'd really like to take advantage of this raid config and have a nice big 1terabyte drive instead of it being broken up into pieces. I could go out and buy a SATA raid controller for my PC too if that would help. Any advice would be appreciated. Thanks for reading my verbose post.

---

### Post by PWill on 2007-04-12
> **dschultz said:**
> I've been a Windows user all my life and am currently a Network Administrator for a grocery supply company. I'm great with all flavors of Windows.

At home I have a powerful system that I recently installed Windows Vista X64 Premium on. I can't say this enough, Vista is total garbage. I've never been so unhappy with a Windows O/S in all of my life. I've had it, enough is enough. I'm moving to Linux. After reading through countless web pages full of opinions on which version of linux to install and I've decided to go with Ubuntu.

I had almost no problems installing Ubuntu on my laptop. The only problem is my built-in camera and I can live with that. I already spent hours digging around only to discover the camera is just not supported because nobody has ported the drivers for the camera's chipset. Okay, I need to get to the point here...

My desktop PC has been a real challenge and I'm at the point of frustration. So, here I am signed up for the forums and posting my challenge:

I have a SATA raid controller on the motherboard. If it's fake... okay great... I can live with that even though I dropped $200 on the MB thinking it was going to be blazing fast. I want to install Ubuntu 6.10 on the desktop. I have 3 SATA drives plugged into the SATA RAID 1,2,3 slots on my mother board. Drive 1 is 300gb, Drive 2 is 300gb, and Drive 3 is 400gb. In the raid controller which loads a config in the bios during POST I was able to group all three hard drives and set them up for a Raid-0. I know, I'm living on the edge with Raid-0 but I'm going for performance here.

I first tried the standard Live CD install and when Ubuntu loaded up from the CD, I went with the little "INSTALL" shortcut on the desktop. This gave me an option to install on ONE of the three drives... so.. it doesn't see the raid-0 array as one big 1 Terabyte drive... choosing manual doesn't help.

I read that 7.04 supports SATA raid better than 6.10. I downloaded the CD, burnt and did the "Install" shortcut from the desktop. Same thing, doesn't see it as a RAID-0 array. I only have the option of installing Ubuntu on 1 drive.

I found THIS guide for installing my SATA raid-0 while booted into Ubuntu live. I followed each step, very carefully and in the order the steps are presented. When I start up GParted I do NOT see the raid array as the guide shows. Instead, I only see the 3 separate drives. So, this guide doesn't do anything for me because it dies when I try to look for the /dev/mapper/XXXX in GParted.

I went ahead and did the sudo dmraid -ay command and it displayed:

RAID set "SIL_ahaeaeccajch" already active

When I browse to "/dev/mapper/" I can see that SIL_ahaeaeccajch is in there but it has a red [X] over it.

I found a guide that says I needed the "Alternate Live" CD so I downloaded that and burnt that to CD. When I got to the part where I setup the drives I was very confussed. Boy do I miss the ole fashioned FDISK in dos... anyway... have hours and hours of looking around, researching, and reading through countless guides I sort-of figured out that I need to setup each drive as RAID - K with mount option turned ON and each drive needs to be LOGICAL as opposed to PRIMARY. Now, I get my raid array showing up as a nice big 1 Terabyte drive but... when I create the SWAP partition... it tells me that the other 985gb are Unusable... *sigh* So I cannot create the swap and /root on the 1TB raid-0 drive I created in the confusing gui-shell linux thingy. I know I'm a noob and I'm willing to go through hell and back in order to start using linux even though I know I'll continue going through hell to get my programs and games to work (wish it were easier). The only option I see at this point is to ask for help or just forget using my nice raid feature and install Ubunto on 1 of my 3 disks and let the others just... do nothing? I'd really like to take advantage of this raid config and have a nice big 1terabyte drive instead of it being broken up into pieces. I could go out and buy a SATA raid controller for my PC too if that would help. Any advice would be appreciated. Thanks for reading my verbose post.

I don't know a lot about RAID, but here is what I do:
I installed Ubuntu to my 60GB HD, and mounted it at "/"
I then mounted my 320GB HD to "/home/"
I think that is your best option. You can mount different drives to different parts of the system, and they will still be on the same filesystem.

---

