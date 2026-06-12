---
title: "Installation finished.. Restart and no grub!"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by guru369 on 2006-10-28
I just finished installing 6.10 and after the installation finished I restarted my PC.
But... Windows just came up!! No Grub Menu!

My Partision Layout is as followed:

2 SATA drives: 1 160GB and 1 200GB

SATA0: 160GB 1 Partition NTFS.
SATA1: 200GB First Partition NTFS (Windows Installation) second Partition 40GB of Ext3 (Ubuntu Installation) Third Partition 6GB Linux-Swap. All the rest in not allocated.

I tried looking though the forums for answers but found none.

Thanks in advance for any help!

Dekel

---

### Post by AgenT on 2006-10-28
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

It appears like you made Windows your default operating system in GRUB.

What probably happened is that your forgot to press ESC to access the grub menu and choose Ubuntu. If you do not see the "press ESC for grub menu" message it means that your grub timeout is very low, maybe even 0 seconds and so grub does not wait for your action.

You will need to update your grub config and 1) increase grub timeout (minimum 5 seconds) and 2) make Ubuntu your default operating system. See the GrubHowTo linked above for details.

Another suggestion is to remove Windows and be done with it. That would be the sensible thing to do. :twisted:

---

### Post by guru369 on 2006-10-28
I affraid its not the case...

I tried during bot to click the ESC key mulltple time no grub window.

I would like to point out that during the Ubuntu install I manualy partitioned my drive. i.e 40 ext3 and 6GB for swap..
I didnt create a boot partition... I am not sure but could that be the problem?

I tried sudo grub-install /dev/sdb (Where Ubuntu and windows are installed)
And I got an error that it was unable to find a suitable boot partition...?!?! or block device.

I must say that fdisk -l shows all my drives and partitions.

dekela

p.s. as for my windows installation... What can I do I am a F.E.A.R addict.. I need it for the game..;-(

---

### Post by AgenT on 2006-10-28
> **guru369 said:**
> I didnt create a boot partition... I am not sure but could that be the problem? It appears that you answered your own question:> **guru369 said:**
> 
And I got an error that it was unable to find a suitable boot partition...?!?! or block device.
You can use fdisk to set your boot partition.

You should take the time to read the fdisk manual before you proceed as a mistake here can ruin your partitions:
```
man fdisk
```Or if you are willing to risk it, read on without reading the man page.

What you need to do is start fdisk:
```
sudo fdisk /dev/sdb
m
<enter>
```The option 'm' shows a help menu with the options you need. If you notice, the first option is to "toggle to bootable flag". You use this option to set the boot flag. Make sure you set the boot flag on the correct partition (the one with grub on it).

Also remember: you need to "write changes" after you make your changes. If you just quit, your changes will not be written and will not take affect.

---

### Post by Herman on 2006-10-28
guru369, 
What if Grub is installed okay, but it went to the MBR on your second hard disk rather than to the first hard disk?
You could test that by pressing your 'F8' or 'F12' key at the right time before your computer boots up to have it try t bot from the other hard disk, just to see what happens.

Regards, Herman :D

---

### Post by guru369 on 2006-10-29
Update:

I was able to resolve this with the help of **dabaR **from ubuntu IRC.

It seems that the grub-install process during ubuntu installation didnt finish or something.
I loaded the live CD again and did the following:

```

#>sudo grub

grub>root  (hd1,4)
grub>setup
grub>quit

#>reboot

```

This seem to fix the problem and grub was loaded.

I dont know if thats a bug but it will sure help anybody who has the same issue.

dekela

---

