---
title: "Ghosting dual boot system (Ubuntu - Windows XP)"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by Lólindir on 2007-06-26
Hi!

We are currently experimenting with a dual-boot Ubuntu - WinXP system in the school where I work. Therefor I installed one system and now we want to place this system on all the other pc's. We normally use Norton Ghost for it because it has network support.

The basic system we want to Ghost has 4 partitions:
1. WinXP
2. Ubuntu SWAP partition
3. /boot partition (EXT3)
4. / partition (EXT3)

This system works well.
When we try to copy this system to another pc however (via Norton Ghost), the newly created system will not boot: GRUB error 17! It seems to be an issue with Norton Ghost and Grub.

After some research I did the following:

1. Start up Ubuntu live CD
(I can see and access all my partitions)
2. Open a console
3. Running the following commands.
    [I]sudo grub
    root (hd0,2)
    setup (hd0)
    quit[/I]
4. Reboot

Now I can access GRUB during startup and boot from the Windows partition.
However when I choose Ubuntu I get an error during startup. It tells me to manually scan the harddrive with fsck.

So I did try to run fsck -f -p, but this was not possible because it should be a manual scan (without the -p option). So I did a manual scan without -p flag, but than I get this error:

[I]e2fsck 1.40-WIP (14-Nov-2006)
Resize inode not valid.  Recreate<y>?[/I]

What does this mean?
I tried 'yes' but than I get this error whole the time:

[I]Group XX 's inode table conflicts with some other fs block.
Relocate?[/I]

I get hundreds of it, even more I think.

I did try *fsck -f -y* but than I ended in an infinite loop which I could not end.

What 's happening and how can I fix this error?
If it 's not possible to fix, how can I ghost the basic pc to all the others (if possible by using the network)?

Thanks a lot!

---

### Post by nyvalbanat on 2007-06-26
Which version of Ubuntu are you using? Since Edgy, it has switched to using UUID's to identify partitions (check /etc/fstab if it uses UUID's or /dev/* identifiers). This was done because bios can arbitrarily assign device identifiers, which could throw off the boot loader (or something to that effect). 

Assuming your hardware is identical on all boxes, I wonder if the problem is related to this somehow.

---

### Post by Lólindir on 2007-06-29
Sorry for the late reply, very busy...
I 'm using Ubuntu Feisty, hardware is identical.
Meanwhile, I have resolved the problem in a tedious way:

Someone has advised me to use partimage. The problem is that it can only backup individual partitions, not entire disks. So I 've setted up a partimage server and I made backups of each partition (4) on the server from the basic computer.

I 've used Norton Ghost to ghost every computer, resulting in a configuration which could not boot. However, when doing this, the partitions are setted correctly on each computer (exact the same size as the basic computer).

After this I used partimage on each computer to replace the faulty partitions by the correct partitions which are on the partimage server.
I 've also restored the MBR from the partimage partitions, however GRUB did not startup correctly on each pc.
I started-up the pc's which still didn't startup correctly (a GRUB issue) with an Ubuntu Live CD in order to manually re-install GRUB.
After doing this, all the pc's did start-up correctly.

Now I 'm wondering: is there a solution to make a network image of the entire disk  instead of each partition separate? I tried to do this with Clonezilla, by setting up a DRBL server in Ubuntu and let each pc do a Network-boot (PXE-boot). The clients did get an IP-adres from the DRBL server, but after this I did get an error message: file not found! So I couldn't boot the clients and I couldn't try this solution...
Does someone has a (step-by-step) DRBL howto? (How to let DRBL work correctly by using Ubuntu and let each client start-up correctly via PXE-boot.)

Thanks for the advice!

Ciao!

---

