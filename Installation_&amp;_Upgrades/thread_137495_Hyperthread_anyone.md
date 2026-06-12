---
title: "Hyperthread anyone?"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by mac3791 on 2006-02-28
Ubuntu newbie here. I am trying to get hyperthreading to work on my P4 3.0 HT. I have the statement 'ht=on' in my /boot/grub/menu.lst.  I have the default 2.6.12-9-386 kernel. Do I need the 686-smp version? If so how do I get it?

---

### Post by newuser111 on 2006-02-28
yes install the linux-686-smp package via synaptic

it works fine with HT cpus

I'm curious where did you read to put "ht=on" in /boot/grub/menu.lst

---

### Post by mac3791 on 2006-02-28
go it from this thread: [http://ubuntuforums.org/showthread.php?p=232632#post232632](http://ubuntuforums.org/showthread.php?p=232632#post232632).

---

### Post by newuser111 on 2006-02-28
i use a smp kernel and cat /proc/cpuinfo shows 2 cpus, I did not put ht=on in menu.lst, just install the 686-smp kernel should work fine

---

### Post by mac3791 on 2006-02-28
I am trying that now. Synaptic doesnt show a linux-686-smp package. Is there a way I can get it?:-k

---

### Post by newuser111 on 2006-02-28
try sudo apt-get install linux-686-smp

failing that try sudo apt-get install linux-image-2.6.12-9-686-smp

---

### Post by mac3791 on 2006-02-28
Didnt work. It complains that it cant find either of them.:(

---

### Post by newuser111 on 2006-02-28
thats weird, i thought kernels were in the standard repos

maybe you only have the cdrom in your sources.list

what does it say when you do sudo apt-get update?

try sudo gedit/etc/apt/sources.list and uncommenting the # hashes for the urls

---

### Post by mac3791 on 2006-02-28
I got it to work. I upgraded a bunch of packages after my OS installation. I never rebooted. So I decided to reboot, afterwards I was able to download the kernel package, thanks for the help :-D

---

