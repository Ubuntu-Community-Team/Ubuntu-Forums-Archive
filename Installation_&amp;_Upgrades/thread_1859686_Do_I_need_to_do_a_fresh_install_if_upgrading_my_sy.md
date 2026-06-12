---
title: "Do I need to do a fresh install if upgrading my system?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by c-m on 2011-10-14
I'm about to upgrade the motherboard in my HTPC, including moving from an old Nvidia 6200 graphics card to an Intel X4500HD.

Now I know on windows that usually involves a fresh installation. But since drivers on Linux are all built into the kernel, does that mean that I can just pop in my old HDD and i'm good to go?

Obviously X will complain about the gfx drivers, but I can sort that from the terminal.

---

### Post by apollothethird on 2011-10-14
> **c-m said:**
> I'm about to upgrade the motherboard in my HTPC, including moving from an old Nvidia 6200 graphics card to an Intel X4500HD.

Now I know on windows that usually involves a fresh installation. But since drivers on Linux are all built into the kernel, does that mean that I can just pop in my old HDD and i'm good to go?

Obviously X will complain about the gfx drivers, but I can sort that from the terminal.

The latter has been my experience.  I installed Ubuntu on a usb pen drive which I often takes between various computers and laptops that has just about everything different.  As long as the computer's bios have a USB boot device option, it boots without problems.

From time to time I have options to fine tune for some hardware differences, but it always works.

I also often take internal hard drives between various computers after system upgrades or other events and don't experience major problems.  A few times the nic boots up to eth1 instead of eth0 or the graphics doesn't have the same resolution as on a previous hardware configuration, but it's never something that simple fine tuning doesn't easily resolve.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by c-m on 2011-10-14
Cool. That just makes everything so much easier.

---

### Post by c-m on 2011-10-14
Doesn't work. I'm getting this error on boot:

GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

Any ideas?

---

### Post by apollothethird on 2011-10-15
> **c-m said:**
> Doesn't work. I'm getting this error on boot:

GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

Any ideas?

You appear to have some glitch with your userid.  You can try creating another user account and run it from there.  Be sure to give the user account sudoer access.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by c-m on 2011-10-15
Can't boot the system, so there is no way of creating another account. 

The system boots straight into GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

The only option then is to restart the system.

---

### Post by apollothethird on 2011-10-15
> **c-m said:**
> Can't boot the system, so there is no way of creating another account. 

The system boots straight into GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

The only option then is to restart the system.

Try booting to the Live CD.  Mount your Ubuntu partition, then chroot to that partition.  Then try to create a new account.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

