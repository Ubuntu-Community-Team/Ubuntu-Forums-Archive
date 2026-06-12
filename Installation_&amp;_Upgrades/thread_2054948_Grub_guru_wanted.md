---
title: "Grub guru wanted"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by nocomp on 2012-09-08
hi folks,
well,i have to admit, i just can t figure out how to solve my probleme, i though i knew enough linux since all these years, (but, in life, sometimes you end to a BUT) i just can t get the bloody box booting.
This is my boot info fromm boot-repair:
[http://paste.ubuntu.com/1192177/]("http://paste.ubuntu.com/1192177/")

the box is a eeepc, on wich i have xp, a version of ubuntu sda6 and bt5 sda5

The linux i ve installed is an iso i ve created with remastersys, it boot all right on vmware or as live cd, but when i installed it, i get an error when installing grub2, so i had no other choice to install it without bootloader.

So the question is quite simple, how can i do now, for get the boot on sd6 working?
i really eed this working cause it s a backup from a box that crashed, i hope you have some clues for help
me out
as the title said:
grub guru wanted!!

thxx for your time
best regards

---

### Post by darkod on 2012-09-08
You also have /dev/sda4 as EFI partition but you don't seem to be using UEFI boot. Be careful if that is getting into the way for a normal boot process. It's eaither the old type BIOS boot, or UEFI boot. This looks like BIOS boot but in that case the EFI partition shouldn't exist and in any case it shouldn't be at the end of the disk. EFI partition always needs to be the first one. Were you moving some partitions around?

Even with the EFI partition there, lets see if we can get your ubuntu grub2 working. Can you boot ubuntu right now or not? There is a grub2 installed on /dev/sda, can you use that and boot ubuntu?

Also I notice that this is 10.10. That version is already end of life and the repositories are closed, so it will be difficult installing packages. You will need to use the archived repositories, or better upgrade to the latest 12.04 LTS. I think you should be able to use the 12.04 cd and upgrade directly instead of upgrading online in which case you can only go one version up. Are you planning to upgrade or not? In that case any grub2 issues are irrelevant, do the upgrade first. 10.10 will not have any updates or security updates any more.

---

### Post by nocomp on 2012-09-08
hi,
thxx a lot for your help
well the box boot, but when i boo sd6 i get grub> or initramfs

i would like to upgrade but i cant, the live cd is 10.10 and you can t upgrade a live cd cause fs is full.
what option can i have for be able to boot this sd6 ?
thxx for your time

---

### Post by darkod on 2012-09-08
I am not talking about upgrading your cd. Download the ISO image of the latest 12.04.1 LTS and make a cd from it. Use this cd to upgrade the 10.10 which is on the hdd to 12.04.1. It's best to have a full backup before trying the upgrade.

If you receive the grub> prompt, you can try booting sda6 with something like:
```
insmod part_msdos
insmod ext2
set root=(hd0,6)
linux vmlinuz root=/dev/sda6
initrd initrd.img
boot
```

See if that works. But even if it does, with a version already EOF you will start to see issues. I would think about upgrading with a cd ASAP.

---

### Post by nocomp on 2012-09-09
hi darkod
i ve downloaded the last version, now a question remain:
how can i with the live cd upgrade what s on sd6 without be able to boot this partition?
best regards
herve

---

### Post by nocomp on 2012-09-09
SAVED!!!!!!!!!!!!!!!!!!!!!!!!!
this is what saved me, the only solution that worked, the chroot method
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

