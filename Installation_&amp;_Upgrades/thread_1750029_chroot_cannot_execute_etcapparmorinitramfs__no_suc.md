---
title: "chroot: cannot execute etc/apparmor/initramfs : no such file or directory"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by tattwood833 on 2011-05-05
Hi there, 

after what seemed a succseful upgrade, I found all I was getting was a blank screen.

So I started following these very useful instructions elsewhere in the forum
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) 

Of course what I didn't realise that my screen wasn't "blank" just "black" - as in the cursor was present and in full working order, and I was fairly certain there was stuff going on behind the black screen as normal - the hard drive light flashes etc.

so with <CTRL><ALT><F1> I can get into a terminal, and the kernel seems to be all fine, except for this one error message at the top

chroot: cannot execute etc/apparmor/initramfs : no such file or directory

Now, on a daily basis I've dutifully booted up and done a sudo apt-get update and sudo apt-get upgrade hoping that a few new packages might sort this out, I also attempted to reinstall the apparmor-profiles package, no joy there either...

so what *is* initramfs? and is this the reason I get no graphical interface other than a mouse cursor on a black screen?

Can anyone help?:confused:

Thanks!

Tom x

---

### Post by tattwood833 on 2011-05-05
so, i've done some noodling around...

and i tried sudo update-initramfs

which seemed to do something...

I still have the black screen plus cursor

but now when I drop to the terminal I get this error

mount: mounting none on /dev failed : no such device
w: devtmpfs not available falling back to tmpfs for /dev

so this is new, what does this mean?!

I really don't know what I'm doing now, and feel quite out of my depth! HELP!

Tom xxx

---

### Post by tattwood833 on 2011-05-06
I've sorted the whole thing!

duh!

the grub hadn't update boot/vmlinuz-2.6.31-17-generic and /boot/initrd.img-2.6.31-17-generic to 38-8

horrah though.

t x

---

