---
title: "Bootable USB stick doesn't get recognized by Computer"
date: 2020-04-22
forum: Installation &amp; Upgrades
---

### Post by dhiaagr on 2020-04-22
Hi all,
I have Ubuntu Desktop on a bootable USB stick that normally works, checked it on two computers, and its boots a-ok.
But on the third one, with a broken Ubuntu Server, it doesn't get recognized and doesn't show up on the Bios Boot Menu.

The computer displays Grub with no command working.

Any hints to what should I diagnose would be of greate appreciation. Thank you ( :

---

### Post by CelticWarrior on 2020-04-22
How was that USB made?

---

### Post by dhiaagr on 2020-04-22
Hi CW, thank you for replying.
Good question.
First, on the startup disk utility from another Ubuntu machine, to no avail.
Then using Etcher on a Linux Mint machine, to no avail.
Then, on unetbootin on a Linux Mint machine, to no avail.
Then, by a dd command, to no avail.

I also used different USB keys, all Philips and high quality.

---

### Post by kc1di on 2020-04-22
Does the machine in question see other usb devices or sticks when plugged in?

---

### Post by dhiaagr on 2020-04-22
Hi kc1di,

Not a single USB stick appears on the boot menu.
I tried 4 different ones, that work on other machines.

---

### Post by CelticWarrior on 2020-04-22
>  		 				 				 		 			 				[INDENT] 					Hi CW, thank you for replying.
Good question.
First, on the startup disk utility from another Ubuntu machine, to no avail.
Then using Etcher on a Linux Mint machine, to no avail.
Then, on unetbootin on a Linux Mint machine, to no avail.
Then, by a dd command, to no avail.

I also used different USB keys, all Philips and high quality. 				[/INDENT] 			
  			   		


So how was it done in the end? All I read is "to no avail" for everything (and without specifying what the problem or problems was/were). And each and every one should work for the purpose.


> Not a single USB stick appears on the boot menu.
I tried 4 different ones, that work on other machines. 				

Are you sure that machine CAN boot from a USB?

---

### Post by ActionParsnip on 2020-04-22
Did you MD5 test the ISO you downloaded, or use torrents so that you know the file is good?

---

### Post by kc1di on 2020-04-22
It sounds like that machine is having a problem recognizing USB ports.  could be a bios problem Have you checked the bios to make sure usb boot is enabled?
If the stick works ok in other machines It doesn't sound like a bad burn.
It may be helpful to tell us what machine it is and as much info as you have on it.  Processor ram make model etc.

---

### Post by dhiaagr on 2020-04-22
Hi everybody;

I finally resolved the situation by applying a hard reset on the Bios, guided by the manufacturer recommendation.
It's been so long since I worked on cheap hardware, I forgot everything about hard resets. I'm not sure what caused this issue in the first place.

Just afterwards, the usb sticks showed up, and the install ran smoothly.
Thank you for your help, everyone ( :

@CW: Apologies for not being clear; I meant that I burned the ISO using all the situation I cited without the USB stick showing up.

edit : For future reference :
Machine is : 
Low range HP laptop.
AMD 64 Dual Core.
4 Gigs of Ram.
Archaic bios.

---

### Post by kc1di on 2020-04-22
Glad you got in going , enjoy :)

---

