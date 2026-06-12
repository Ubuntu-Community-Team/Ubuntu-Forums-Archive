---
title: "fd0 error, Error on drive that doesn't exists."
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by RSahlgren on 2008-03-25
When I am gonna start Ubuntu with a CD which i burned. I have installed Ubuntu from windows. In the CD it's a file which installs over windows. And I turned the computer off.. choose Ubuntu to boot.. waited some minutes and got the error with fd0. Buffer I/O error on device fd0. But i don't have any floppy disk. And in the bios it says it's "not installed".

Anyone can help me with my problem? It would be nice to have an anwser as soon as possible.

---

### Post by dannyboy79 on 2008-03-25
found this solution by using google, hopefully it works for you.

"Hello all. I ran into the same error with 7.10. I fixed it by pressing F6 at the screen asking weather you want to install, go into oem mode etc. I fixed it by pressing <F6> and adding

floppy=off

to the boot line. Im still unsure how this Dell thinks it has a floppy, but aparently it does.

EDIT: gparted hangs for a bit, but works after a couple miniuts."

---

### Post by RSahlgren on 2008-03-25
> **dannyboy79 said:**
> found this solution by using google, hopefully it works for you.

"Hello all. I ran into the same error with 7.10. I fixed it by pressing F6 at the screen asking weather you want to install, go into oem mode etc. I fixed it by pressing <F6> and adding

floppy=off

to the boot line. Im still unsure how this Dell thinks it has a floppy, but aparently it does.

EDIT: gparted hangs for a bit, but works after a couple miniuts."

It's like this now.. computer starts. Then it asks what OS i wanna boot, i choose Ubuntu, then what?

---

### Post by dannyboy79 on 2008-03-25
when it asks what you want to boot in grub, you should be able to hit F6 when you have ubuntu highlighted. that should bring you  to various lines, you'll then want to highlight the boot parameters line, then hit F6 again, then go all the way to the end of the boot line and add floppy=off. the boot line should look something like this.

 /vmlinuz-2.6.20-16-generic root=UUID=522585f4-bbc8-4214-b6b4-a56504723995 ro quiet splash floppy=off

then we need to edit your /boot/grub/menu.lst so that each of the boot lines have the floppy=off added to them so you don't have to do this everytime you boot up.

I am running Feisty so you're may be a little different.

---

### Post by RSahlgren on 2008-03-25
I don't know which to edit. There is multiplied lines. I will post them here:

find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
commandline
reboot
halt

Which one to edit?

---

### Post by RSahlgren on 2008-03-25
I have now did as you told me and i get several errors now:

Call Trace:
[<c0188cde>] vfs_rename+0x3de/0x480
[<c018abf6>] sys_renameat+0x1e6/0x220
[<c0183cbe>] sys_stat64+0x1e/0x30
[<c018ac57>] sys_rename+0x27/0x30
[<c01041d2>] sysenter_past_esp+0x6b/0xa9

What now :/

---

### Post by dannyboy79 on 2008-03-25
wow, this one is over my head. sorry I can't help. you can remove the floppy=off from the boot line but you'll just be back to where you were.

---

### Post by RSahlgren on 2008-03-25
I am doing a memory test right now. So I am gonna see how it will be...

EDIT: The memory test didn't come out with anything.. So what to do now?

Also the computer which i am installing on is a Dell Latitude C600.

---

