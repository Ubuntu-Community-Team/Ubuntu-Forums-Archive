---
title: "root problems"
date: 2005-09-02
forum: Installation &amp; Upgrades
---

### Post by Billyum on 2005-09-02
Last week I managed to install Ubuntu on my aging Toshiba Satellite laptop. Because I wanted a small installation, I followed a suggestion on the Wiki to do an expert install. Everything seemed to go OK, and I installed Ubuntu in less than 1 GB, leaving me about 1.5 GB on my hard drive.

During the installation I was asked to give a root password, and I did. This seems to have led to problems with system administration in Gnome. For instance, this afternoon I tried to run the Synaptic Package Manager for the first time. It did not matter which password I entered, I got the error message: 

     Failed to run /usr/sbin/synaptic
          Child terminated with 1 status

I can open a terminal and become root, but at that point I am mostly lost. I do know some basic commands.

How do I set things up so that I can do administrative tasks in Gnome?

Many thanks,

Billyum

---

### Post by kekocsi20 on 2005-09-03
Hi, 

I am having the same problem, but I think I found the solution. Go to the following link: 

[https://wiki.ubuntu.com/RootSudo?highlight=%28change%29%7C%28password%29](https://wiki.ubuntu.com/RootSudo?highlight=%28change%29%7C%28password%29)

I am going to boot up linux and see if it works.

---

### Post by Billyum on 2005-09-03
Thanks!  :)

I followed this advice:

Warty

In Warty, adding a new user involves editing the /etc/sudoers file. To edit that file, you must use 'visudo' as it will error check the file before exiting. To add a user with the same administration rights as the first user, add the following lines to the file: '$newuser ALL=(ALL) ALL'. Replace the $newuser with the username. 

even though I have Hoary.

Billyum

---

