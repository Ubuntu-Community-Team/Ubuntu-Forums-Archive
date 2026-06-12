---
title: "Asus EEE PC restore causes grub rescue"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by cyris69 on 2010-02-11
I had windows XP and Ubuntu installed on my Asus 1000HE and the hard drive is failing so I need to RMA it. They told me to restore it to factory defaults which I just press F9 at boot 3 time and Ghost takes over and reformats, creates 2 partitions and installs XP on one of the and the other is for another OS or just storage if needed.

I did that now I get a grub rescue prompt when I boot my netbook. Is there a way that grub installed itself to my PE partition that's a hidden partition that came with the netbook? I've taken the drive out of the netbook and put it into my desktop and formatted both main partitions but not the restore one. Yet I still get the grub rescue prompt, how can that be?? I can't even boot from flash drive or get to bios it just goes straight to the rescue.

I need to send the netbook back but can't unless its restored. Can someone please help me?. Right now I'm on the 9.10 live flash drive I made on my desktop and my only hard drive attached it the netbooks.

---

### Post by cyris69 on 2010-02-11
I'm going to attempt a new installation of Ubuntu from the live cd on my main partition and see if that helps. Then if I can get it to not give me a rescue screen I'm going to try the restore once more.

---

### Post by cyris69 on 2010-02-11
Nope, doesn't work. I can boot Ubuntu just fine and I can see my restore boot option in grub and once I run it it just does the same thing giving me the rescue. How am I suppose to fix this?? Buy a new hard drive or pay for ASUS to repair it? 

I guess this is why I never kept Linux on any of my PCs, I'm not ruling out user error but I've taken my share of Linux classes. I've ran out of ideas other than reinstalling ubuntu again, making a windows 7 bootable flash drive then overwrite the ubuntu partition with win 7 then run my restore which is a hell of a lot of work to do but I'm out of options unless someone can guide me in the right direction.

---

### Post by darkod on 2010-02-11
Get a ubuntu live usb stick close by, the one you can boot from, it can be the same you installed from.
Do the asus restore thing once more, it will wipe the hdd and restore XP. The thing is, it doesn't wipe the MBR of the hdd and that's where grub remains are.
So, to get rid of that, after XP is restored, boot with the ubuntu stick, Try Ubuntu option, and in terminal do:

sudo fdisk -l

to confirm the internal hdd is called /dev/sda. If it is, do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

If it's called something else than /dev/sda just use that in the second command. Ignore any warnings. This will install generic windows mbr on your hdd MBR. Reboot without the ubuntu stick and check whether XP will just boot.

---

### Post by cyris69 on 2010-02-11
Thanks for the reply, I will try this when I get back from my A+ class. Now once that's done can I do the restore again to get rid of Ubuntu from my netbook?

I have to install Ubuntu again then as soon as I do that I can boot the restore partition from GRUB but that's when it all happens, once its been restored I get the grub rescue command line on boot I can't access anything including BIOS or pressing Esc repeatedly to get to a boot menu.

I might be able to get more access by putting the drive into my desktop again, I think it let me choose a boot device unlike the netbook after teh grub issue.

---

