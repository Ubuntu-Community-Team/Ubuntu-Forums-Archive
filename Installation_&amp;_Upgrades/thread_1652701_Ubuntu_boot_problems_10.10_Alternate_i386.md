---
title: "Ubuntu boot problems 10.10 Alternate i386"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by jaythedogg on 2010-12-25
First, here are my system specs:

WinXP Pro SP2 (Version 2002)
Pentium 4 CPU 1.80 GHz
512MB of RAM (PC100 I believe, although could be 133)
GeForce 4 MX 4000 64MB DDR
Generic PS2 Mouse & Keyboard.
Standard CRT monitor.

Before, when trying to dual boot with XP Pro using Wubi, it failed after install completed, before setup.

Now, since burning a disc with 10.10 Alternate on it, I can complete the install.... Though things have been happening...
I started a new thread so people don't have to sort through the original post.

Here is the chain of events in list form:

1- Put in the disc, rebooted PC from XP Pro sp3.
2- Installed Ubuntu 10.10 Alt using recommended settings/partition
3- Reboot, starts with: No device found (or something) & grub recovery:
4- Reboot a few times, same effect, reinstall Ubuntu
5- Try it with a new partition next to other install.
6- Reboot PC, now grub works, one XP & two Ubuntu options.
7- Ubuntu gets to splash (loading screen, says Ubuntu & has dots to indicate load progress) then freezes.
8- Reboot into recovery mode. Freezes after saying something about hard  disk with some path/file not ready hit M for something or wait... Then  freezes.
9- Put Ubuntu disc back in, attempt repair, no help.
10- Use disc again, check integrity, disc is fine, do rescue, no avail.
11- Completely format drives (two in RAID, first is 40 GB then a 20.5 GB) Reinstall using FULL 40GB Windows went bye bye.
(Note, couldn't load Windows through grub at any point either)
12- Changed out AGP Geforce2 MX 100/200 32MB for PCI Geforce2 128MB  & changed BIOS accordingly. (In case it was a bad AGP driver?)
13- Same problem, would freeze at cursor (single cursor in upper left,  black screen), recovery mode produced same results as #8 in this list.
14- Wipe & reinstall, this time to 20.5 GB drive in hopes that it was 40 GB that went bad.
15-Reboot PC, no grub, just "Hard Disk Error" in upper left, black screen
16- Yanked both drives, the master connector on my ribbon cable was  coming off, reattached & used slave connector on my other spare  drive, 160 GB Maxtor IDE. (Slave is master if no second drive present) -  Note that the previous drives were set to primary & slave via  jumper, so I set my 160 GB as master from cable select via jumper.
17- Reinstalled Ubuntu after clean wipe using the partition tool on the disc. Basic settings, use entire disk for partitions.
18- Reboot & fail. It got to the cursor going from large to small  (assuming graphics software loaded & resolution changes?) &  freeze.
Tried again, same problem.
19- Reboot in to recovery mode via grub & I got a menu... YAY! First  time I have seen it so I almost dropped my Amp (energy) on my keyboard!  (Okay, not really...)
20- Didn't know what to do so I figured it could only be (out of the  list) a graphics issue, going from text based to GUI, chose the low  graphics option this one time & it got me here....

Then oddly enough, Ubuntu updated, like 210MB, so it required restart. I said goodbye to my GUI desktop & on a whim, hit restart.
Here is the expected outcome. Nothing. Back to freezing at boot, black screen with a cursor after resolution change.
Here is the odd part, I took the GeForce 4 MX 4000 64MB PCI card out  & put in this large, no heat sink, wide, looks like Win98 compatible  "Multimedia diamond 64MB DRAM" card... On a whim & powered the  computer up... Guess what? It runs just fine, but in 800x600.
Note: Grub2 (update to grub, I think it is grub) doesn't show up, I  don't have a boot loader now, just straight to the black screen with a  cursor for loading.
I am going to attempt to go download the linux drivers for the GeForce 4  MX 4000 card I have, figure out how to install them & shut down,  switch back & see if it will boot with that card.
If not, I will replace it with this ancient, yet wonderfully working,  booger I have in here now & see if it *chooses* to boot.

Update:

Okay, I don't think it is the graphics drivers. I tried rebooting  without installing a driver & the old card I had in it wouldn't  boot, it would hang like my failed attempts above.
So I tried going back to my GeForce 4 MX 4000, fail. Back to old school  card, fail & got as far in recovery as to get some message about  nouveau not recognising the CHIP. I am baffled here, as it worked last  time the system booted.
So I switched it back to the GeForce 4 MX 4000, tried booting recovery,  fail. Tried regular boot, fail. Tried recovery again & it went  through & allowed me to use the recovery options list....

I don't think I need to select "use failsafe graphics" to get it to  finish booting from there, as from that point I am pretty much in to  GUI, I click continue & use it this time only, then it goes straight  to login...

Please, I implore you, oh Ubuntu gurus, ease my screaming chipsets & tell me what to do!

I honestly can't figure it out.

Thanks.

---

### Post by searchfgold6789 on 2010-12-25
I think it could be the graphics card drivers. Maybe the system is trying to use the nVidia drivers, with the "hunka" graphics card.
Try reinstalling Ubuntu, except with the nVidia card plugged in.

---

### Post by jaythedogg on 2010-12-27
> **searchfgold6789 said:**
> I think it could be the graphics card drivers. Maybe the system is trying to use the nVidia drivers, with the "hunka" graphics card.
Try reinstalling Ubuntu, except with the nVidia card plugged in.

As said before, maybe in the other topic, I have tried it with both cards. I got sick of only being able to boot 1 out of 10 times & finally reformatted, reinstalled Windows XP. Computer runs like a dream now.

Sad really.

---

