---
title: "Cannot boot after fresh install of 12.10"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by rintcius on 2012-11-14
Hi,

I did a fresh install of 12.10 but cannot boot into it now. I tried boot-repair a couple of time but without success. 

From my BIOS, I tried booting into both "ubuntu"  and "WD ..." (my primary hdd) but both give me the black screen with cursor.

The current state of my installation as given by boot-repair is here: [http://paste.ubuntu.com/1358166/](http://paste.ubuntu.com/1358166/)

Last time I ran boot-repair I installed GRUB install devices into: 
/dev/sda
/dev/sdc

This was last output on command line:

```
Creating config file /etc/default/grub with new version
Installation finished. No error reported.
/usr/sbin/grub-bios-setup: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can  only be installed in this setup by using blocklists.  However,  blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
done

```Anyone knows what is wrong? Any help is much appreciated,
Rintcius

---

### Post by oldfred on 2012-11-14
It looks like your sdc has UEFI install with gpt partitioning? But all the other drives are MBR.

Is sdc a SSD and is your system UEFI?

Do you want UEFI/gpt as the way to boot or the old BIOS/MBR method?

If only installing Ubuntu to SSD, you can install in BIOS mode with gpt partitioning but have to then have a small 1MB unformatted bios_grub partition. If UEFI you have to have the efi partition first and gpt partitioning.

gpt partitioning is recommended for SSDs and is required for drives over 2TB.
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

How you boot install CD or flash drive UEFI or Legacy/BIOS/AHCI is how it will install to your system. 

Side issues. 
Is there some reason for the LVM on the 60GB drive?
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
 Unless re-arranging partitions a lot, LVM does not offer much advantage & adds a level of complexity. Backups also become more important.

---

### Post by rintcius on 2012-11-14
Thanks for your reply.
To answer your questions:
- I installed 12.10 on sdc, which is indeed SSD.
- My system is UEFI.
- I guess I would go for the UEFI/gpt way to boot (I didn't know I had that option ;) ). Especially since it's an SSD.
- RE: "How you boot install CD or flash drive UEFI or Legacy/BIOS/AHCI is how it will install to your system. " => I installed via live CD on flash drive UEFI. So I guess that's why sdc is UEFI?
- I thought LVM's snapshotting feature was nice, but after reading your link I think I'll try without LVM.

---

### Post by rintcius on 2012-11-14
By the way: before the install of 12.10 (I had Natty then) the system  booted into sda. Maybe that's why my system is partly BIOS and partly  UEFI.
 I thought to boot into sda again, but if advise is to boot in sdc, I am happy to do that...

---

### Post by oldfred on 2012-11-14
You will have to go into UEFI/BIOS and change settings. 

Not sure if a one time bot key (f12 on my system) will let you alternate between BIOS mode and UEFI mode?

When I installed SSD, I had to turn AHCI on to enable trim. But my old XP install does not have AHCI drivers. So I stopped booting XP. As a test I was able to go into BIOS, turn AHCI off and boot Windows. Then back to BIOS, turn AHCI on and boot from SSD. With all that hassle I do not boot XP :) .

---

### Post by rintcius on 2012-11-14
Hi oldfred, thanks for your help!

I ditched windows after a new Service Pack.. windows refused to boot after that... was too much hassle for me as well :)

I went into boot-repair once again & then selected just sdc as device driver. After that it booted ok!

Thanks again, your help is much appreciated
Rintcius

---

