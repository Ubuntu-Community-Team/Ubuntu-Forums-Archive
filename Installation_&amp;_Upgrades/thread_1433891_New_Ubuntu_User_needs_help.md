---
title: "New Ubuntu User needs help"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by cdzo72 on 2010-03-19
Hello all, new to Ubuntu and the forum, so please bear with me.

I have a laptop which I'm going to want to be able to run Ubuntu on.

I have Ubuntu installed on an external HDD which I connect to the laptop via USB, as fas as that goes, all is good.

Question 1: While in Ubuntu running off the external hard drive, how can I mount or run Windows if need be while in Ubuntu, or at least access the Windows partition on the internal HDD on my laptop. I can see it in Ubuntu, but when I try to access it, Ubuntu asks me for an authentication, which I have no idea what to put in the box.

Question 2: As I said, I have Ubuntu installed on an external hard drive connected via usb. How can I run Ubuntu or mount that Ubuntu while in Windows.

I forgot to mention that I'm running Windows 7 Ultimate 64 bit. The Ubuntu installation is 32bit.

Thanks ahead of time for any help and info you guys may offer.

---

### Post by Ozymandias_117 on 2010-03-19
> **cdzo72 said:**
> I have Ubuntu installed on an external HDD which I connect to the laptop via USB, as fas as that goes, all is good.

Question 1: While in Ubuntu running off the external hard drive, how can I mount or run Windows if need be while in Ubuntu, or at least access the Windows partition on the internal HDD on my laptop. I can see it in Ubuntu, but when I try to access it, Ubuntu asks me for an authentication, which I have no idea what to put in the box.

Question 2: As I said, I have Ubuntu installed on an external hard drive connected via usb. How can I run Ubuntu or mount that Ubuntu while in Windows.

Answer 1. The authentication is just the password you entered into Ubuntu when you installed it.

Answer 2. You can't run ubuntu inside windows (You can install it inside windows using wubi, but you still have to reboot to switch so... it's not exactly "inside" windows) The only way to get ubuntu inside windows is Virtualbox (free) or VMware (Not free)

Answer 2.5. Windows doesn't natively understand the linux filesystem, you will have to install a third party program to be able to see the hard drive in windows. (Sorry, I don't know of one, I don't use windows ;))

---

### Post by Chesamo on 2010-03-19
I believe, Ozzy, he's looking for a way to share files.

For getting files off your Windows partition (while in Ubuntu), just enter your password when prompted.

For getting files off your Ubuntu partition (while in Windows), that depends on the filesystem you are using. I'm not aware of any program that can read ext4, though if you're lucky and selected ext3, you can use FS-Driver:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

However, since I am not a native Windows user, I can't vouch for the quality of that "driver".

---

