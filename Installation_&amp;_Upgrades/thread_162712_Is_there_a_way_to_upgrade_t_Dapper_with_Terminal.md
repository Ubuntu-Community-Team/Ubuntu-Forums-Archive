---
title: "Is there a way to upgrade t Dapper with Terminal?"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by zxcvbnm on 2006-04-19
I was wondering if i could upgrade to Dapper Drake...If not will the Beta release tommorow let me

---

### Post by az on 2006-04-19
Change the instances of breezy to dapper in your /etc/apt/sources.list file:

sudo nano /etc/apt/sources.list

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Punterfpc on 2006-04-20
I have a new question. It may seem kinda silly, but, it would save me some time.

I have downloaded the latest Dapper ISO, but, I'm an idiot and forgot that you can just apt-get dist-upgrade. Is there a way to upgrade from the CD? Like, for instance, set the repositories to the CD or something? :confused: 

I would like to know because I already downloaded the entire ISO and downloading another 500+ MB would be a pain in the butt. 

Thanks in advance.

-Kyle

---

### Post by Punterfpc on 2006-04-20
Sorry, found the answer already. But, for anyone else with the same question, Here's the answer:

Yes! You *can* update your distro with a cd by simply commenting all repositories except the CD-ROM entry. If you don't have your CD listed in your /etc/apt/sources.list then all you have to do is:

1)Insert Dapper CD 
2)Open terminal by going to Applications > Accesories > Terminal 
3)Type in:

sudo apt-cdrom add
sudo apt-get update

Now, making sure all your other repositories are commented out (have a # in front of them...), simply do the same ol' same ol':

sudo apt-get dist-upgrade

Mine installed without a hitch. 

I had to re-install EasyUbuntu, but, that's okay... it's easy... (duh...)

---

