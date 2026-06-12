---
title: "Black Screen During 10.04 Install"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by t.mil on 2010-05-27
I've been trying to install Ubuntu 10.04 on my Dell XPS 630 but every time i select INSTALL or TRY UBUNTU when booting from the cd, all i get is a black screen with a white blinking cursor.  I have tried various options in the F6 menu but nothing has worked.  I know the CD is working because I was able to install it inside Windows and dual boot, but I wish to do a fresh install.

---

### Post by ronparent on 2010-05-27
What is your graphics chipset?

---

### Post by t.mil on 2010-05-27
NVIDIA GeForce 8800GT

---

### Post by mad_bald_guy on 2010-05-27
Maybe try a different version. If you tried th 32 bit go to the 64 bit. Also trying a live USB drive might be worth trying. I have a compaq that for whatever reason won't boot ubuntu from CD or DVD, it does what you are describing. It works fine with USB. I hope this helps, and I welcome anyone to correct me if there is better advice. 

-noob

---

### Post by ronparent on 2010-05-28
It sounds like a graphics problem, but unlikely for nVidia? When you hit f6 the boot line will be displayed. Hit <end> and backspace to erase quiet splash. The error is probably at the end of the boot process so the screen will probably turn black before you see the last message, but sometimes dropping the splash command in itself will let it boot. Post on how you make out.

---

### Post by t.mil on 2010-05-28
still nothing after removing the quiet splash

---

### Post by ronparent on 2010-05-28
While scrolling onto the screen where did the boot process stop?

---

### Post by t.mil on 2010-05-28
as soon as i pick an option from the boot menu it just goes to the black screen with white blinking cursor

---

### Post by ronparent on 2010-05-28
Let's try again. When booting, do rhe f6 and use spacebar to select the **noapic nolapic** options and hit end (to move the cursor to the end of the bootline) and backspace to erase the ** quiet splash**, now what scrolls on the screen and where does it stop.

---

### Post by t.mil on 2010-05-30
still just a black screen with blinking cursor

---

### Post by ronparent on 2010-05-30
This is a tough one. The boot process never begins or you would see at least some text scrolling. To take a hint from mint - try individually the parameters **irqpoll** and **noapci**. Beyond this I am running out of ideas with no scrolled text on the screen at all to clue us. 

It wouldn't have anything to do with an existing install within windows, would it? That does sound unlikely because nothing seems to prevent multiple installs within the same computer or drives.

---

