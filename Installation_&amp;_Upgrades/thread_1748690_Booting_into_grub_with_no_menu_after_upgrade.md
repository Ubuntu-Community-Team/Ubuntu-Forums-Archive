---
title: "Booting into grub with no menu after upgrade"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Khar136 on 2011-05-03
I had Ubuntu 10 running on vmware machine. It ran fine. I upgraded to version 11, but now when the machine restarts I do not get any menu, I just get his:

    GNU BRUB version 1.98-1ubunutu7
    Minimal BASH-like line editing is supported&#8230;..
    grub>

And that is it! No menu, no list of options, nothing. If I type "ls" I get:

(hd0) (hd0,5) (hd0,1) (fd0)

I can enter "root (hd0,1)" which gives me:

(hd0,1): Filesystem is ext2.

Then typing &#8220;kernel /boot/vm&#8221; and pressing tab shows:

vmlinuz-2.6.32-27-generic vmcoreinfo-2.6.32-27-generic vmlinuz-2.6.35-28-generic vmcoreinfo-2.6.35-28-generic vmlinuz-2.6.38-8-generic vmlinuz-2.6.38-8-generic

There is no /boot/grub/menu.lst but there is /boot/grub/grub.cfg which seems fine as far as I can tell.

Any suggestions on how to fix this pretty please?

Did I somehow end up with an older grub which is looking for menu.lst? I have other machines running Ubuntu and if I boot into them I seem to get a GRUB4DOS etc. slightly different version. The grub version shown above is 1.98 but I read somewhere Ubuntu uses version 2? Actually I found another post which suggests that this is the correct grub version for Ubuntu 11.

How can I tell what menu file grub is looking for where it is looking and why its not finding or using it? It should work...

---

### Post by gabitech on 2011-05-05
Unfortunately I'm getting the same thing after the upgrade, on a Samsung NC 10

---

### Post by Khar136 on 2011-05-05
Ok, somebody please pat me on the back for solving this all by myself, because I impressed myself. Here is how I managed to fix this:

After reading [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2), this is what I did to fix the problem:

_Step A: Get Ubunutu back up_

You can either follow the instructions below which is what I did, or just boot the corresponding Ubuntu live CD and skip to step B.

When you get "grub>" when you restart your computer, enter this:

[B]set root=(hd0,1)
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro
initrd /boot/initrd.img-2.6.38-8-generic
boot[/B]

If you are not sure which hard drive (hd0,1) just enter "ls" to get a list, or refer to the above link on how to determine that. As for the version numbers, type "linux /boot/vmlinuz-" and press tab to get a list of valid image versions. Use the last one (highest number).

With his Linux should boot and come up. Now we have to fix grub, otherwise it wont boot up again next time.

_Step B: Reinstall and repair grub_

Open a terminal window in Ubuntu (via the menu or alt keys). Enter this:

[B]sudo fdisk -l
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo update-grub
sudo grub-install --recheck /dev/sda[/B]

The fdisk command will basically let you figure out to which partition you want to install grub. In my case I could see the main linux partition was on sda1. The above should be standard, other than for "sda1" and "sda". Refer to the above link to determine the values for your machine.

The update-grub will rebuilt your grub menu according to what it should be. There is no menu.lst anymore, but instead a grub.cfg which is automatically maintained. If you get any errors during these commands, refer to the link given earlier.

I still do not know what broke, but the above fixed it nicely for me. Step A should be fairly safe and harmless. Step B you just have to make sure to where you want to install grub.

And after than I can restart my computer, and viola, Ubuntu comes back up with the menu and all.

If this helps somebody, please let me know so I can know its worthwile.

:popcorn:

---

