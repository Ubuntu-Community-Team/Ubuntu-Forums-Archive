---
title: "How can I resize my ubuntu 11.04 partition?"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by kronospear on 2011-05-06
I have 2 hard drives and my ubuntu is installed in the second hard drive. I made ubuntu only 15gb and I want to resize the partition to 50 gb. How can I do this easily? Should I use the installation cd? Please yell me the instructions. :)

---

### Post by Quackers on 2011-05-06
What is your current partition setup on the hard drive which has Ubuntu on it? Maybe a screenshot of your gparted screen for that drive would help. 
You may need to install gparted first (via synaptic package manager).

---

### Post by kronospear on 2011-05-06
> **Quackers said:**
> What is your current partition setup on the hard drive which has Ubuntu on it? Maybe a screenshot of your gparted screen for that drive would help. 
You may need to install gparted first (via synaptic package manager).

Ok. I'm gonna have it as soon as I get the power back on

---

### Post by MAFoElffen on 2011-05-06
> **kronospear said:**
> Ok. [COLOR=Red]I'm gonna have it as soon as I get the power back on[/COLOR]
I hate when "that" happens ](*,)

If you are not changing the logical order of the partitions, what I would do then is to boot on a GParted LiveCD and use Move/Resize to do it.

---

### Post by kronospear on 2011-05-08
> **MAFoElffen said:**
> I hate when "that" happens ](*,)

If you are not changing the logical order of the partitions, what I would do then is to boot on a GParted LiveCD and use Move/Resize to do it.

Hmmm. So when I resize it using gparted, will it delete all my data, break the ubuntu os or do nothing other than resize the partition

---

### Post by willz06jw on 2011-06-19
The answer is most likely no -- I am about to do the same thing myself.

---

### Post by willz06jw on 2011-06-19
After I resized the partition, it screwed up how the computer booted.  I then used the Rescatux Live CD to auto-fix grub (the bootloader) --- now it works perfectly!

Rescatux Live CD is available at: [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

Have a good one,
Will

---

