---
title: "Installing with Intel Matrix Storage (FakeRAID) on seperate drive - still boot vista?"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by atconc on 2007-11-27
Hi All

I recently built myself a new system, that I was planning to install Ubuntu on in a dual boot configuration with Windows Vista, I even went to the extent of switching from my usual preference for ATI video cards to Nvidia as I had heard the Linux drivers were much better.  I also decided to take the plunge and go for a RAID 0 setup to try and get some faster disk IO going on.  Unfortunately I didn't research this part of things in advance, just set up the "RAID" controller in the motherboard and installed Vista, Leaving 20 gig of free space for my Ubuntu install. 

 I went for the convenience of getting my windows install set up how I like it before I started to play with Ubuntu - this is something I don't really want to go through again. 

I can boot from the live CD but the installer doesn't recognise my Fake RAID, I've read the guides to get ubuntu booting from the fake RAID and I'm pretty daunted by them, so I'm wondering if it would be easier to just install Ubuntu on a seperate drive (I have an old 80gb IDE drive lying around).

What I need some advice on is the following:

what will happen to my system if I go ahead and install ubuntu on the IDE drive, will grub know about the vista install on the RAID array and let me boot to it? (I'm guessing not). 

Does it actually make things easier to put the Ubuntu install on the IDE drive?

Is there a guide to getting Ubuntu to see the RAID array once it's actually  installed

Thanks in advance for any help

System Specs are

Intel Core 2 Duo E2140 "LGA775 Conroe" 1.60GHz - running @2.8Ghz
Gigabyte GA_P35C_DS3R (Socket 775) PCI-Express
4 GB ram (4 x 1GB in dual channel)
2x160GB WB SATA drives
Nvidia PCIe graphics

---

### Post by can8dnSix on 2007-12-04
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)
Martti Kuparinen <martti.kuparinen@iki.fi> wrote this white paper; Is a good article for you question. Unless you are wanting to install and dual-boot windows on the same set of drives, that could complicate things but I am sure it is doable one way or another. 

Can8dnSix

---

### Post by atconc on 2007-12-04
Thanks for the link, I will definitely keep the link as a good reference, but it doesn't really fit what I am trying to do, I wanted to get Ubuntu installed in the free space on my already existing RAID 0 array.  

At the moment I installed ubuntu on a separate IDE hard drive with the other drives disconnected and am using the BIOS boot menu to choose which device to boot from, this has at least enabled me to play with Ubuntu although I don't think it's the most elegant of solutions.

---

### Post by Pumalite on 2007-12-04
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

