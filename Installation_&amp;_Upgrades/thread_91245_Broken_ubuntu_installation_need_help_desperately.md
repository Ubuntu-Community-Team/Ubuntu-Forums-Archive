---
title: "Broken ubuntu installation need help desperately"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by linux_newbie on 2005-11-16
Hi everyone,

I am new linux user and have Ubuntu Hoary 5.04 installed on my Dell 600m laptop. It was working fine but I accidently deleted the /lib/modules directory and now I cannot boot in Ubuntu. It comes up with modprob: Fatal error messages.

is there a way that I can fix this problem. I need to desperately fix this without formatting since all my important files are on this partition.

is there a repair option for ubuntu installation without formatting.

---

### Post by dcast on 2005-11-16
you could try using a live cd and mounting your hdd

---

### Post by az on 2005-11-16
There are many ways to do it. 

One way is to boot the installer, Press CTRL-ALT-F@ to get to the console.  If I can assume that your linux install in on hda5 then chroot into hda5

mount /dev/hda5 /mnt
(I do not know the exact path right now)
cp /pool/l/linux-image/linux-image-2.6.12-9-386 /mnt/home/you/

chroot /mnt


and then reinstall the kernel

cd /home/you

dpkg -i linux-image*

---

### Post by linux_newbie on 2005-11-17
[QUOTE=azz]There are many ways to do it. 

One way is to boot the installer, Press CTRL-ALT-F@ to get to the console.  If I can assume that your linux install in on hda5 then chroot into hda5

mount /dev/hda5 /mnt
(I do not know the exact path right now)
cp /pool/l/linux-image/linux-image-2.6.12-9-386 /mnt/home/you/

chroot /mnt


and then reinstall the kernel

cd /home/you

dpkg -i linux-image*[/QUOTE]
I tried this but nothing came up when I did CTRL-ALT-F@.

My linux install is on hda3. I can get to the commandline and not able to start the gnome or kde.  

Is there a way that I can mount the ubuntu installation CD and then do the above steps ?

I tried sudo mount /dev/hdc and got a messae that unknown filetype iss09660.

I appreciate your responses but I still cant get it to work

Thanks

---

### Post by az on 2005-11-18
Aw crap!

I made a typo.  sorry.

CTRL-ALT-F2

---

### Post by linux_newbie on 2005-11-19
I figured it out:

1. On the installer command type 'rescue' (without quotes).
2. Follow the on screen instructions.
3. It will give you an option to mount the cd to your hard drive
(for me the mounting did not work)
So I went back to the console and invoked the console which is which a bash like shell. Here i mounted the /dev/hda3 to /target

copied the /pool/main/l/linux-source-2.6.10/linux-image-*.deb to /target/home/<username>

chroot /target/home/<username>

did dpkg -i linux-image-*.deb

Came up with a error tat /proc not mounted. Then mounted /proc using the instruction in the error message which was something like mount /proc none /proc (its not exact)

and ran dpkg -i linux-image-*.deb again and this time it worked.
(it did downgrade my linux image to whatever was there on the CD but it worked for me and I was able to boot again)

Thanks a lot everyone for promptly replying to me. :D

---

