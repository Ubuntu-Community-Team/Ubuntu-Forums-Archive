---
title: "MDADM email alerts When raid mirror is broken"
date: 2019-02-01
forum: Installation &amp; Upgrades
---

### Post by crissedemarde on 2019-02-01
Hi,

I've been strugling with this for weeks.

I have a functional Raid1, I want to (mainly) get an email alert when a ssd dies.
Very simple right? That's what I thought

I used msmtp AND ssmtp after ward without any success. 

-In both cases ( I reinstalled the whole setup twice for those suspecting conflicts), I can send emails with the command line.
-In both cases the command 
sudo mdadm --monitor --scan --test -1
Works and sends an email with the array status.
- in both cases, mdadm monitor daemon is a running process..

BUT when I UNPLUG one drive.... Nothing happens, No warning no email... nothing.
Of course if I check cat /proc/mdstat, I can see the _U status indicating that the software knows I broke the array, but doesn't feel like sending an email today.


Any help?

Thanks for your time

Crisse

---

