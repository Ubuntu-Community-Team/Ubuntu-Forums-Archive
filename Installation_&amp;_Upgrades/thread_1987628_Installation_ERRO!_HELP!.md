---
title: "Installation ERRO! HELP!"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by Ineedtechhelplol on 2012-05-26
Okay, i used a USB stick to install ubuntu because i didnt have a cd, anyways once i got it installed i removed my USB stick becuase it was finished it restarted and everything went smoothly till it tried to reboot up and it goes to a black screen with a Flashy _  underscore anyways now when i put the USB back in and boot from it ubuntu works if i remove the Stick while ubuntu is on it continues to work, anyways is there a way to fix this because i need my USB back but i cant use my system without it i Installed Ubuntu on a Windows XP and removed Windows XP and Ubuntu used my whole hard drive how can i fix this now?

---

### Post by darkod on 2012-05-26
Boot ubuntu with the stick connected, open terminal and check which disk is /dev/sda and which /dev/sdb, whether the hdd or the usb, with:

sudo fdisk -l (small L)

Then, depending what letter is the hdd, just do:
sudo grub-install /dev/sdX

Replacing the X with the letter.

Reboot without the stick and it should work.

---

### Post by kc1di on 2012-05-26
go here and download boot repair and run it. think it will fix the problem for you.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Ineedtechhelplol on 2012-05-26
> **darkod said:**
> Boot ubuntu with the stick connected, open terminal and check which disk is /dev/sda and which /dev/sdb, whether the hdd or the usb, with:
 
sudo fdisk -l (small L)
 
Then, depending what letter is the hdd, just do:
sudo grub-install /dev/sdX
 
Replacing the X with the letter.
 
Reboot without the stick and it should work.
 
I dont even know how to open Terminal, ive never used Linux before this is my first time.

---

### Post by Ineedtechhelplol on 2012-05-26
> **Ineedtechhelplol said:**
> I dont even know how to open Terminal, ive never used Linux before this is my first time.
 
 
I found terminal i tried to install Boot-Repair
Sudo ask for my password wont let me type fails password entry and turns off terminal
 
so now what?

---

### Post by darkod on 2012-05-26
Click the ubuntu logo in the Unity bar on the left, that will open the general Dashboard. It has a search line on top.

Start typing terminal and it will show you below all programs found that include that search phrase.

---

### Post by darkod on 2012-05-26
When it asks for your password did you enter it? Don't get confused that the cursor doesn't move, it does that when you are entering passwords.

Just type in your password again and hit Enter.

And I still prefer you do it manually with the grub-install command as opposed to boot-repair, but the choice is yours. The end result should be the same. And you have more work installing boot-repair and running it.

---

### Post by Ineedtechhelplol on 2012-05-26
> **darkod said:**
> When it asks for your password did you enter it? Don't get confused that the cursor doesn't move, it does that when you are entering passwords.
 
Just type in your password again and hit Enter.
 
And I still prefer you do it manually with the grub-install command as opposed to boot-repair, but the choice is yours. The end result should be the same. And you have more work installing boot-repair and running it.
 
okay i used Boot-repair now it boots from the hard drive but everytime it boots it goes to the flashy _ and then Grub comes up and tells me to select from a list of 4 or 5 things Ubuntu with linux something is the top one how do i get it to just directly boot to ubuntu without all this other stuff?
 
and sorry for all these questions never used ubuntu so yea lol

---

### Post by darkod on 2012-05-26
Well, I told you to do it manually and not with boot-repair. :) That tool is very good, but since I can't promise what exactly it will do, I can't tell you when to use it.

Run the boot-repair again but this time don't run any repair. Just use the option to create the boot info script output and it will give you a link where it will post it. Give us that link here so we can look what you've got and give you more precise instructions.

There is nothing bad in being new to linux (or any other OS for that matter), welcome.

---

