---
title: "[help] ubuntu 7.10 don't go on after the boot layer"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by ganjone on 2007-12-01
Hello .. then explain my problem.
My PC is composed of 3 Hd one from 4 Gb. With SO Another from 320Gb. In ext3
A new and just assembled from 400Gb. Just formatted nrfs.

After connecting it Hd from 400 I get the following error:
[B]
BusyBox v 1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell  (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _ [/B]

And then points can't go on.
How can I fix?

---

### Post by Pumalite on 2007-12-01
Post your specs. If you can boot a Live CD, post:
sudo fdisk -lu

---

### Post by ganjone on 2007-12-01
> **Pumalite said:**
> Post your specs. If you can boot a Live CD, post:
sudo fdisk -lu

i can't boot a live CD... 

	
When I try to boot the PC with the live cd the error is the same...:(

---

### Post by Pumalite on 2007-12-01
Try the Alternate CD.

---

### Post by ganjone on 2007-12-01
also tried with 7.04 .. Same result

---

### Post by Pumalite on 2007-12-01
Have you tied your CD's in a different computer?

---

### Post by ganjone on 2007-12-01
Yes, I do explain .. Then with the cd that I am using ubuntu installed on my pc composed of one hd for O.S. And another in ext3 for database .. Then when I link in third Hd ntfs I see the error ..
I also tried to connect the DVD  (for the boot from Cd) and the Hd in ntfs but always the same mistake ..

---

### Post by Pumalite on 2007-12-01
So, your Live CD has worked in another computer?. You have finished the install and has been able to boot through Grub?

---

### Post by ganjone on 2007-12-01
It works perfectly. Both my PC than on other computers that I have here at home ..:confused:

---

### Post by Pumalite on 2007-12-01
You will have to give me the complete specs of the computer in which this Live CD doesn't work.

---

### Post by ganjone on 2007-12-01
this is the Motherboard--------> ** asus a7n266-Vm **

CPU------------------------------->** AMD atlon xp 1800+   **

Hd 1(primary master )----------> **fujitsu 4Gb. whith O.S.**
Hd 2 (primary slave) ------------> **seagate barracuda 400Gb ntfs (error)**

DVD(secondary master)-------> **LG model:  gsa-h42n**
Hd 3 (secondary slave)--------> **seagate barracuda320Gb ext3(data) **

You need anything else?

	
Thank you for your help ..

---

### Post by Pumalite on 2007-12-01
'
Hd 2 (primary slave) ------------> seagate barracuda 400Gb ntfs (error)'

What's the error exactly?

---

### Post by ganjone on 2007-12-01
I wrote error near the primary slave  to report that when I connect this Hd I have the error:
> **ganjone said:**
> 
[B]
BusyBox v 1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell  (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _ [/B]


---

### Post by Pumalite on 2007-12-01
After connecting it Hd from 400 I get the following error:

BusyBox v 1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
You don't get this message just connecting a hard drive. What did you install , where, and how?

---

### Post by ganjone on 2007-12-01
I do not have to install anything.

I wanted to acknowledge this  HD by my  pc. to make my works...

---

### Post by ganjone on 2007-12-01
and if I buy an external box for my Hd. there are a possibility to read that Hd like external ???

---

