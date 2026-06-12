---
title: "Samsung Series 9 900x3d Cant Install"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by Sulle on 2014-12-30
Hey guys, i am currently so annoyed of my windows 8 that i actually have been thinking about selling this laptop if i cannot install ubuntu on it.

I have tried to install Ubuntu using an USB stick,CD,Wubi and Unetbootin . 

But both options fails me everythime. 

The problem is that its hard to get it to boot from on or the other, and when i get it to run. The installer comes up and gives me some options, like.

Try or install ubuntu
Install ubuntu
Memorytest 
Etc
etc

But if i try to install or just to try it, it just restarts.



So now im crawling on my knees here, begging you guys for some help.

Is there an easier way, or a right way to install Ubuntu on my laptop?. I dont want dualboot. I want a pure Ubuntu System !.

---

### Post by sudodus on 2014-12-30
0. Installing operating systems is risky, so ***backup*** at least your personal files (pictures, documents ...) to an external drive or to the internet cloud ***before*** you start!

1. Are you sure, that you want to remove Windows? There might be some  program, or some peripheral device, that needs Windows. At the very  least, ***prepare recovery disks of Windows***, so that you can restore it, if  you change your mind. Or you can consider making a compressed cloned  image of the whole internal drive with Clonezilla.

2. It is easy to install Ubuntu, if you can switch off UEFI (to run in BIOS mode, alias CSM). But it is also possible to install alongside Windows in UEFI mode in most but not all computers. I am not sure that your UEFI system allows that. Try to find out by browsing and learning the UEFI-BIOS menu system. See these links and links from them:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

---

### Post by Sulle on 2014-12-30
I finally got it to work, i had to put the bios to LEGACY. and choose to ONLY boot from CD "used old 8.10" Cd. Then after i had 8.10 installed. 

I could then install the newest version. Thnx alot Sudodus for you help :)

---

### Post by sudodus on 2014-12-30
Congratulations :KS

You are welcome, and please come back with new threads, if/when you have new questions about Ubuntu, some application program or some task.

---

