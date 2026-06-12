---
title: "How should I partition my Hard Drive?"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by nicol_bolas on 2008-07-22
I am reinstalling Ubuntu after trashing it yesterday for Arch that I can't get to work(yes I gave up already). I did like that it set up different partitions for /, /home, /swap, and /temp which I liked. So I was wondering how I divide up the space on my 76 GB hard drive? Also I have 512 MB of Ram.

Thank-you very much,
Nicol Bolas

---

### Post by tamoneya on 2008-07-23
I usually dont bother with the /temp partition.  I do it something like this.

swap = double the amount of RAM = 1 GB
/ = 6 GB I err on the side of caution since I hate having to go and repartition things.  Currently I am using half of that and I have a fair amount of crap installed.
/home = everything that is left = 69 GB

---

### Post by logos34 on 2008-07-23
> **tamoneya said:**
> i usually dont bother with the /temp partition.  I do it something like this.

Swap = double the amount of ram = 1 gb
/ = 6 gb i err on the side of caution since i hate having to go and repartition things.  Currently i am using half of that and i have a fair amount of crap installed.
/home = everything that is left = 69 gb

+1

---

### Post by Sef on 2008-07-23
> swap = double the amount of RAM = 1 GB
/ = 6 GB I err on the side of caution since I hate having to go and repartition things. Currently I am using half of that and I have a fair amount of crap installed.
/home = everything that is left = 69 GB

I would make / 8 - 10 GBs.

---

### Post by pdwerryhouse on 2008-07-23
Is this a server or a desktop? If it's a desktop, I'd have a much bigger / partition - maybe even 20Gb, because it gets large over a period of time, as you install more and more software.

I'd also recommend using LVM, so that you can adjust the sizes of your partitions should you need to.

---

### Post by nicol_bolas on 2008-07-23
> **pdwerryhouse said:**
> Is this a server or a desktop? If it's a desktop, I'd have a much bigger / partition - maybe even 20Gb, because it gets large over a period of time, as you install more and more software.

I'd also recommend using LVM, so that you can adjust the sizes of your partitions should you need to.

It is a home computer.

---

### Post by logos34 on 2008-07-23
I disagree on the 10-20 GB for / -- that just seems excessive considering a separate /home.  I've got Ubuntu Studio x64 8.04 installed (everything except the graphics pkgs), and a fair amount of crap installed, but I'm only using 5.4 gb out of 6.7 gb--and that's counting the debs stored in /var/cache/apt/archives.  

You've only got limited disk space so I'd go with ~ 6-8 range  max for  /.  (unless you're going to put just gobs of apps on it)

---

### Post by kajillin on 2008-07-23
a fresh install of ubuntu will run you 5+ gb of space, so anything 6+ is fine due to your limited hd space. and like the others said dont bother with the /temp just a waste of a partition (but ppl say the same thing about having a /boot partition, which i have) and double for swap

---

### Post by nicol_bolas on 2008-07-23
Well I am going with 7 GB for /
1 GB for /swap
and the rest for /home

Thank-you for your help,
Nicol Bolas

---

