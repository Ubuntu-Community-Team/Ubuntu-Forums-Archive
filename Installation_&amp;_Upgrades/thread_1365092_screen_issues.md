---
title: "screen issues"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Orion_PKFD on 2009-12-26
Hi all again,

After installing ubuntu 9.10 images and the desktop view is grainy and weird. What may be causing this?

I would appreciate your help,

Best regards

---

### Post by taurus on 2009-12-26
Maybe it has something to do with your graphic card?  What do you have and have you installed a driver for it?

---

### Post by Orion_PKFD on 2009-12-26
I installed it on an Asus laptop with NVIDIA Geforce GT220M. I haven't installed anything yet because I dont know what I need to do :( Will I need to install something?

Regards

---

### Post by Orion_PKFD on 2009-12-27
Guys, please help over here:confused:

---

### Post by Orion_PKFD on 2009-12-27
I went to system>administration>hardware drivers and installed the driver (it is better now, but still isn't as perfect as it is on Win7), but it is not the same I see at NVIDIA's website. I ype this: *sudo sh NVIDIA-Linux-x86_64-190.53-pkg2.run* but a message appears and says that I need to close an X app or something like that. 

Am I doing something wrong?

---

### Post by realzippy on 2009-12-27
Log out,then press Alt+ctrl+F2,then stop gdm:

[B]sudo /etc/init.d/gdm stop
[/B]
if on Karmic:

**sudo service gdm stop**

then run your *sudo sh NVID.....*

---

### Post by Orion_PKFD on 2009-12-27
Hi,

I'm on 9.10. What  Alt+ctrl+F2 does?
And what am I doing with: [B]sudo service gdm stop?

[/B]Sorry about the questions;)

---

### Post by realzippy on 2009-12-28
Download the 195.22 driver to your **Desktop**....
then install it:

1.Log out
2.Press Alt+Ctrl+F2
3.Log in at shell (username&password)
4.Type:
  [B]sudo service gdm stop
[/B]
5.Type:
**cd Desktop**
6.Type
  **sudo sh NVID** *(hit"Tab" to autocomplete!)*
7."YES" to all asked questions during installation
8.Type:
  **sudo reboot**

---

### Post by Orion_PKFD on 2009-12-28
It is the same as after I installed one with "administration>hardware drivers", but it is good enough I think. When I'll want to processed images or something like that I'll use Win7

Thanks

---

### Post by Orion_PKFD on 2010-05-01
> **realzippy said:**
> Download the 195.22 driver to your **Desktop**....
then install it:

1.Log out
2.Press Alt+Ctrl+F2
3.Log in at shell (username&password)
4.Type:
    
5.Type:
**cd Desktop**
6.Type
  **sudo sh NVID** *(hit"Tab" to autocomplete!)*
7."YES" to all asked questions during installation
8.Type:
  **sudo reboot**


Whenever I do an update (the automatic ones) which needs to restart the laptop, I need to do the "quoted" again and again and again...I never figured out why.

Today, after doing the update, I tried to do** "sudo service gdm stop**" but it says unknown or something like that.

Anyone knows how to fix this?

Thanks

---

