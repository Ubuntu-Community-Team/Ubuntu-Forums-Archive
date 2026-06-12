---
title: "How to dual boot Win 8 on ASUS Zenbook Prime (UX31A)"
date: 2013-02-05
forum: Installation &amp; Upgrades
---

### Post by annnomius on 2013-02-05
i will describe in this post how i created a dual boot installation of windows 8 pro and ubuntu 12.10 x64 on the asus zenbook prime, model ux31a. i am posting this in the hope that it might be useful for someone else trying to do the same, or maybe provide some ideas for people stuck trying to make a similar dual boot system.

i started with a ux31a that had win7 and ubuntu and bought the win8 upgrade package. i downloaded win8 pro onto a usb stick--here i had to use unetbootin to create a bootable usb stick because the ubuntu startup disk creator does not properly deal with udf files! :mad:

also, before installing, i updated the bios version to 216 (most current version). this was easy to do by just putting the bios file on another flash drive, then booting into the bios and updating from there :p

anyway, once i had a bootable win8 pro installer on the usb stick i did the following:
1. boot from usb stick (through uefi menu--press and hold esc key on startup)
2. choose custom install
3. delete ***_all_*** drive partitions (make sure you have backed up files already!!)
4. create a new partition for win8 (i chose 100gb because i wanted more than 1/2 for ubuntu). this automatically created 4 partitions:

[LIST]
[*]partition 1 is the windows recovery partition (300mb)
[*]partition 2 is the windows system (100mb)
[*]partition 3 is msr (reserved) (128mb)
[*]partition 4 is primary (97.1gb)--the main windows partition
[*]remainder of the disk (about 150gb) was left unpartitioned (to be used later for ubuntu)
[/LIST]
5. choose partition 4 for the install

after the windows install, i took a usb stick with ubuntu 12.10 64 bit, secure edition for the ubuntu installation. according to other posts, the secure edition is not necessary (just a 64 bit 12.10 should work), but this is what i used.

initially, i could not boot from the usb stick and had a panic attack :eek:
there is **no** option to turn off secure boot or fast boot in the bios (at least version 216) so i thought i was stuck with only win8 permanently on the machine :evil:
the trick here was step 6:
6. in windows 8, open the control panel, choose system & security-->power options-->choose what the power buttons do-->change settings that are currently unavailable-->**deselect** "turn on fast startup". after this i was able to boot off a usb stick again. interestingly, i could not boot off a usb stick after _restarting_ win8, i could only boot from the usb stick from a cold boot (then pressing esc key to get to uefi boot menu).
7. boot from usb stick and choose custom install for ubuntu.
8. leave 1st 4 partitions alone (should be /dev/sda1=ntfs, sda2=efi, sda3=unknown, sda4=ntfs) and create /dev/sda5 as /, ext4, 145gb. create /dev/sda6 as swap, 2gb. you might choose different partition options for ubuntu here.
9. put bootloader installation on /dev/sda5.

i don't bother to use grub for booting windows--that is what uefi is for! i have setup the boot order in the uefi (bios) menu to boot the ubuntu partition first. if i want to boot into windows, all i have to do is hit esc at bootup and choose the windows partition. i think this is far easier than having grub try to manage the windows boot process.

i hope this helps others setup similar systems or avoid similar problems

::ann

---

### Post by annnomius on 2013-10-23
i just recently upgraded to windows 8.1 and had a glitch, so i will describe that and how i overcame it in the hope it may help others with a similar situation...

i started with the system described above and did an upgrade to windows 8.1. the windows upgrade went smoothly of course, but in the process it hosed the grub bootloader, because when i chose to boot ubuntu, it just a showed a "grub rescue" prompt.
(i'm disappointed windows still tries to stomp on other operating systems, but i'm also disappointed the grub rescue "tool" is utterly opaque! :frown:)

the following recovered ubuntu for me:
1. at the grub rescue prompt, type "ls" to list the different disk partitions
2. type "set prefix=(hd0,gpt6)/boot/grub" because gpt6 was my linux partition (checked from gparted in the usb stick ubuntu boot--as an aside, i don't remember /dev/sda6 as being my linux partition--perhaps win8.1 added an extra partition ? :confused:)
3. type "set root=(hd0,gpt6)"
4. type "insmod (hd0,gpt6)/boot/grub/x86_64-efi/linux.mod"
5. type "linux /vmlinuz root=/dev/sda6 ro"
6. type "initrd /initrd.img"
7. type "boot"
8. once into ubuntu, open a terminal and run "sudo grub-install"

note that i tried a few other ways to recover before i got the above recipe, and they failed. perhaps if i had done them slightly diferently it would have worked, but again i will list for reference:
-boot ubuntu from usb stick and repair from there. i could boot, but could not get grub-install to fix the problem (various errors, and even after using --force it still did not work)
-run "sudo update-grub" once into ubuntu. even though update-grub executed successfully, the grub rescue prompt still showed up at boot

::ann

---

