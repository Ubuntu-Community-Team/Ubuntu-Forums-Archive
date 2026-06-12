---
title: "DELL Latitude D630 - Boot splash error"
date: 2008-08-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xens on 2008-08-07
I've got a strange screen during the startup, instead of having the ubuntu logo.

[[IMG]http://img172.imageshack.us/img172/9272/dsc00463qw7.th.jpg[/IMG]](http://img172.imageshack.us/my.php?image=dsc00463qw7.jpg)

I'd like to report this bug but I don't know witch package is faulty. Can someone give me some advice ? After the startup GMD appears correctly the shutdown screen is working, only the bootsplash is faulty.

Thanks, Xens

---

### Post by douham on 2008-08-07
I've had this happen to with my custom desktop machine. I think it's something to do with the neww drivers and X. I might check my gconf file though and see if a bug has been reported.

---

### Post by xens on 2008-08-08
Thank's for answering but it's before loading X it's during the slpash screen.

---

### Post by Miguel on 2008-08-08
It's either the framebuffer driver (vesa 99% sure) in which case you'll probably have to file a bug against linux-image-whatever_is_in_intrepid or usplash. Do you use non-default resolution for usplash? Have you changed the tty's resolution in /boot/grub/menu.lst using vga=791 or similar? If the answers to both of these questions are no, I'd file against the kernel.

EDIT: Do you have an intel graphics card? If kernel modesetting is enabled for intel cards, it's then a kernel bug (i think)

---

### Post by SnowPunk98 on 2008-09-18
My issue might be similar, I have a Dell Latitude D830 and upgraded from Hardy. It locks right when Ubuntu starts to load, mine looks different than this though.

I do have an Intel chipset.

---

### Post by autocrosser on 2008-09-19
That's a well-known bug to me---look at:  [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

You are having one of the symptoms--alternating red/white & green/black that is a framebuffer problem. Another part of the problem is:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269)

Usplash is not drawing correctly & I am guessing that after freeze we will see some action on this--it all started with a update to Usplash & I'm betting that it is not calling the framebuffer correctly. I have just set my menu.lst to "noslpash" until this is resolved.

---

### Post by SnowPunk98 on 2008-09-19
I actually just updated from the recovery console and was able to boot, no wireless though :(

---

### Post by denitroid on 2008-09-19
I have a problem much like that however I just get a black screen does everything else work fine?

---

### Post by SnowPunk98 on 2008-09-19
No wireless but I think there is a bug for the card I have.

---

