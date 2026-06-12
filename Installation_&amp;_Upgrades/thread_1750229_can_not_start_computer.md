---
title: "can not start computer"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by lisamae on 2011-05-05
Hi there, 

sorry I am a beginner with linux and pretty much know nothing. I installed ununtu last year in november and since today it has been great. 

It has stopped booting completely. a list of Ubuntu options comes up, including some recovery mode ones but none of them work. For example Ubuntu, with linux 2.6.35-28 generic

when i choose one of the options i get a long message. this is the last part of the message

" BusyBox v1.15.3 (Ubuntu 1:1.15-3- 1ubuntu5) built in shell (ash) Enter help for a list of built in commmands. 

(initranfs). "

I tried entering help, but that was not much use. 

Any help or directions would be greatly appreciated. I feel completely lost. 


This is my computer details and I installed the latest version of Ubuntu at the time Netbook remix 10.10 I think it was.
**[COLOR=#000000][FONT=Arial]Asus EeePC 1005PX 25,7 cm (10,1 Zoll) Netbook (Intel Atom N450, 1,6GHz, 1GB RAM, 250GB HDD, Intel GMA 3150,0[/FONT][/COLOR]**


Thanks so much!

---

### Post by dino99 on 2011-05-05
try:

- recovery mode to boot then select "repair package"

or into a terminal:
sudo initramfs -u -k

if you can boot on another kernel, try too (its good to have at least 2 kernel to boot from grub menu)

---

### Post by lisamae on 2011-05-05
thank you for your reply. 

I have tried all your options but none of them have worked. 

when i boot up, there are 6 kernels to continue that i can select in a terminal environment. for each of the 6 kernels, there is a normal and recovery mode, so 12 options total. none work.

i also tried the command sudo initramfs -u -k, said sudo not found. so i tried initramfs -u -k and it said initramfs not found.

Are there any other options? I am feeling a little lost. 

thanks heaps!

---

### Post by cstoh on 2011-05-08
I find that  a command like

sudo initramfs -u -k

sometimes does not work well. I prefer to run "sudo su" then login with your password. Then issue command "initramfs -u -k"

---

