---
title: "Can't Boot"
date: 2015-05-10
forum: Installation &amp; Upgrades
---

### Post by ShanePunk123 on 2015-05-10
Recently I installed ubuntu 14.04. I run the setup through Wubi and the setup completes but everytime I try to boot into the OS my screen just becomes black as if computer has been shut  down but the CPU is still up and running.... Check the Video --------> [https://www.youtube.com/watch?v=11AyUNQbxhk](https://www.youtube.com/watch?v=11AyUNQbxhk)

---

### Post by dino99 on 2015-05-10
Wubi is no more maintained since a while, and probably unusable nowadays.
Either try ubuntu via virtualbox, or do a real installation
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by hakuna_matata on 2015-05-10
IHMO your issue is not a Wubi issue.

Maybe you can solve it, [URL="https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot"]editing_the_GRUB_2_menu during boot:
[/URL]
The GRUB 2 menu is the purple menu. Press 'e' for edit mode. Change the line beginning with "linux". Maybe this line is splitted in more than one line with '\'

For your black screen try to use different boot options:
```
linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=1234567890ABCDEF loop=/ubuntu/disks/root.disk ro [COLOR=#ff0000]nomodeset[/COLOR]
```
After changing press F10 to boot

If you see a black screen again, try another boot option:
```
linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=1234567890ABCDEF loop=/ubuntu/disks/root.disk ro [COLOR=#ff0000]xforcevesa[/COLOR]
```

For [bug 1317437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437") it could be also helpful to use rw instead of ro:
```
linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=1234567890ABCDEF loop=/ubuntu/disks/root.disk r[COLOR=#ff0000]w[/COLOR]
```

---

### Post by ShanePunk123 on 2015-05-11
Now after doing what you told, I'm facing this error in the images attached.... it says something like press s to skip mounting and I press s then it asks for ubuntu login... I enter the username and password which I made during installation but it says invalid ubuntu login

---

### Post by Bucky Ball on 2015-05-11
As mentioned, Wubi is no longer supported by Canonical or officially by these forums, although, naturally, it is up to you what you choose to use. You won't get much help for Wubi here, apart from perhaps hakuna_matata and a few others. No one uses it any more or remembers much about setting it up or fixing it (if it is at all fixable). 

Good luck. If you want information on installing a supported release in a dual-boot, virtual machine or standalone Ubuntu install, please let us know and we'd be glad to give what help we can.

PS: Even when it was supported, Wubi was never intended as a long-term solution. It was intended so you could 'try before you buy' prior to installing Ubuntu to hard drive on its own partition. All flavours can be tried from the install media so there wasn't much point and then UEFI arrived and it doesn't work with that and no-one is interested in maintaining it so ... obsolete, but up to you.

See [here]("http://ubuntuforums.org/showthread.php?t=2229766") for staff recommendations re. Wubi.

---

### Post by ShanePunk123 on 2015-05-11
Alright I'll try a thumb drive installation today and let you know how it goes... Thanks

---

### Post by hakuna_matata on 2015-05-11
> **ShanePunk123 said:**
> it says something like press s to skip mounting
IMHO there are two different issues:

The "black screen" issue which does not depend on Wubi and the "serious errors" issue (aka bug [1317437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437")) which depends on Wubi.

I wanted to avoid the following situation:

        
[LIST]
[*]You get a black screen with Wubi
[*]Everybody says, "Don't use Wubi!"
[*]You don't use Wubi
[*]You get a black screen again
[*]You are deeply disappointed
[*]You don't use Ubuntu
[/LIST]
 
So it could be helpful to know some workarounds for issues which are not depending on Wubi and then you can easily install Ubuntu without Wubi. 

If you get a working installation with Wubi, it is really no problem. There are  excellent tools to migrate a Wubi installation to real partitions: [MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi")

Nevertheless, it is the right goal to install Ubuntu without Wubi but there are different ways to reach that goal.

---

