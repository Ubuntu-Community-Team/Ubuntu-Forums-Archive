---
title: "Error:file not found when booting after 10.10 update"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by acornty on 2011-03-22
hello everyone, i have a dual boot system set up right now through wubi. the installation went fine. but then i tried to upgrade ubuntu from 10.04.2 to 10.10. the update went fine, no errors. but afterwards when i restarted my computer and selected ubuntu, it said "error: file not found" it didn't even get to grub. this has happened numerous of times trying to upgrade in the past. can someone tell me why this keeps happening? 

p.s: i have vista installed as the other side of the dual boot.

---

### Post by bcbc on 2011-03-22
See the Wubi megathread: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Problem #2, Solution #2 or #1 - then the Permanent Fix.

---

### Post by acornty on 2011-03-23
> **bcbc said:**
> See the Wubi megathread: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Problem #2, Solution #2 or #1 - then the Permanent Fix.

huh, I'll try that.thanks. i have one more question though. i had an actual dual boot system set up a while ago by partitioning my drive and installing ubuntu. but for some reason when i would boot into windows it would boot into the windows recovery environment. if i ever go back to an actual dual boot, would there be a way to fix this? i recall trying updating grub, but i don't think it did anything. 

EDIT: so i went to this thread([http://ubuntuforums.org/showpost.php?p=10264157&postcount=33)](http://ubuntuforums.org/showpost.php?p=10264157&postcount=33)) which file does the use want me to edit?

---

### Post by bcbc on 2011-03-23
> **acornty said:**
> huh, I'll try that.thanks. i have one more question though. i had an actual dual boot system set up a while ago by partitioning my drive and installing ubuntu. but for some reason when i would boot into windows it would boot into the windows recovery environment. if i ever go back to an actual dual boot, would there be a way to fix this? i recall trying updating grub, but i don't think it did anything. 

EDIT: so i went to this thread([http://ubuntuforums.org/showpost.php?p=10264157&postcount=33)]("http://ubuntuforums.org/showpost.php?p=10264157&postcount=33%29") which file does the use want me to edit?

Grub isn't very good at differentiating the recovery partition from the actual Windows partition - on Vista or 7. So it seems it just lists the first as the main one and the second as the recovery. The way you can tell is to look for the boot flag (you can see it on the output of "sudo fdisk -l") and then match the partition with the boot flag with the grub entry e.g. "Vista recovery (on /dev/sda2)" - so ignore the text.

Regarding post #33 - everything you need should be in Post #1. Unless you are now getting a grub prompt, in which case it's fairly simple to boot Wubi.

---

### Post by acornty on 2011-03-23
> **bcbc said:**
> Grub isn't very good at differentiating the recovery partition from the actual Windows partition - on Vista or 7. So it seems it just lists the first as the main one and the second as the recovery. The way you can tell is to look for the boot flag (you can see it on the output of "sudo fdisk -l") and then match the partition with the boot flag with the grub entry e.g. "Vista recovery (on /dev/sda2)" - so ignore the text.

Regarding post #33 - everything you need should be in Post #1. Unless you are now getting a grub prompt, in which case it's fairly simple to boot Wubi.

ok thanks, I'll see what happens :P.

---

