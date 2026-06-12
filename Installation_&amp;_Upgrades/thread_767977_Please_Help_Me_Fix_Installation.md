---
title: "Please Help Me Fix Installation"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by whoeva on 2008-04-26
Hello, I'm hoping some kind soul(s) would like to help me try and get me back onto ubuntu using my new PC. I did briefly try Gutsy but ran into problems so waited for this new version but seems I still have problems.

I have 2x500gb SATA drives in a raid 0 which has my windows XP, games and other files spread across 4 partitions.
I wasn't sure how to go about putting Hardy on my raid so I just installed it onto the other drive I have in the PC. This is a 400gb IDE drive that 2 partitions and 20gb unallocated.

Firslty I couldn't boot the 64bit Live CD install but clicking the button that "helps you boot from Live CD" enabled me to get it installed onto the IDE drive. I set it up on a 10gb partition with 2Gb swap and the remainder for a home partition. The grub was installed to default (hd0).

Upon rebooting I got the grub 21 error and could boot neither. I managed to fix the mbr using windows disc and I can now boot XP and also ubuntu but instead of going to a desktop ubuntu (after loading for ages) gives me a message:

BusyBox v1.1.2 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ASH)
and then has a (command?) line of:

(initramfs)

I cannot now boot from the Live CD at all but I can boot from my old Fiesty or Gutsy disc so if people need any info I can get in there to get it.

I did try the find /boot/grub/stage1 command but it was not found. Tried mounting as read in another thread but got an error upon trying to chroot.
 
What I'm wondering is can I easily fix this installation or should I just wipe clean the ubuntu partitions and reinstall but this time around putting grub on the IDE drive rather than the hd0? Would this still enable me to dual-boot or do I need to change the boot drive order in the BIOS everytime?

Also is it going to be possible for the ubuntu installation to be able to read any of the files from my Raid drives?

What is the best option?

Any help here would be highly appreciated as I've been away from ubuntu for too long now and my new PC is raring to have a go at it.

---

