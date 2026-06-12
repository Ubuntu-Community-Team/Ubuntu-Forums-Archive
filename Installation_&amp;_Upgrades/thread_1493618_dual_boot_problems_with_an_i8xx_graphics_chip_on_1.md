---
title: "dual boot problems with an i8xx graphics chip on 10.04"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by adenewton on 2010-05-26
I'm having no end of problems trying to get 10.04 onto my older Toshiba Satellite A50 laptop that I use as a spare laptop round the house for when my girlfriend is hogging mine.

The laptop previously dual booted with XP and Xubuntu fine.

I wanted to give Lubuntu a go to see if it's performance was better on this older hardware. When installing I got the black screen of death, and also got the same problem with the Xubuntu CD. 

Research pointed me in the way of this article:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I was able to boot the Lubuntu Live CD using the instructions outlined in method A.

Once installed however I rebooted and Grub seemed to be knackered. Just sent me to a recovery console of which I had no idea what to do. 

As I could no longer boot into Windows either I reinstalled Xubuntu 9.10 and all was fine.

I decided yesterday to give it another bash this time connecting to my wireless from the live cd hoping it would download an update to fix this problem.

Nadda, Grub this time did show and I was able to boot into XP, but upon picking my Linux distro I now get an unrecognised device error with a long string of charachters and then it dumps be back into the grub menu, choosing the recovery mode version does the same thing.

Windows continues to boot fine.

So, any further suggestions. I'm fairly ok as long as you give me good instructions on what to and have been using Ubuntu on my desktops and laptops for over 2 years now but it's more a case of using it because it works, rather than getting my hands dirty under the hood, so any terminal commands that are needed, please write concise instructions.

Hoping someone can help. It's not the end of the world if I have to stick to Xubuntu 9.10 but it would be a shame if it means that version is the end of the road for Linux on that hardware.

---

### Post by dino99 on 2010-05-26
boot with nomodeset on the boot line

if thats work, 

sudo gedit /etc/default/grub

select the line ended with quiet splash

and change by: nomodeset quiet splash

then

sudo update-grub

---

### Post by adenewton on 2010-05-26
> **dino99 said:**
> boot with nomodeset on the boot line

if thats work, 

sudo gedit /etc/default/grub

select the line ended with quiet splash

and change by: nomodeset quiet splash

then

sudo update-grub

From the Live CD? Or from editing the grub command?

I can't even boot Xubuntu because it comes up with the unrecognised device then a long string (Which I assume is the ID for my Xubuntu partition) 

I can get the exact message tonight when I'm not at work!

---

### Post by adenewton on 2010-05-26
> **dino99 said:**
> boot with nomodeset on the boot line

if thats work, 

sudo gedit /etc/default/grub

select the line ended with quiet splash

and change by: nomodeset quiet splash

then

sudo update-grub

OK, I have no idea where you want me to enter nomodeset. I have pressed e on the grub menu to edit but I don't know where to add it.

The exact error when attempting to boot into Xubuntu is as follows:

error: no such device: 'long string of chars which I assume if the ID of my partition with Xubuntu on'

Press any key to continue.

---

### Post by davidmohammed on 2010-05-26
usually the "no such device" error message is due to grub not understanding where to find the ubuntu installation. 

Suggest, boot from the live CD.

in a terminal type

sudo blkid

note the long string of characters which corresponds to where you have installed ubuntu - normally /dev/sda1.

e.g. sudo blkid on mine gives
/dev/sda1: UUID="91abadf7-37aa-4581-872c-790d090e2d79" TYPE="ext4" 
/dev/sda2: UUID="62D0807ED08059E5" TYPE="ntfs" 
/dev/sda4: UUID="d752d6e9-e0d6-4e31-ac1b-99c13a76d305" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="d5de6cfd-d9c7-4d95-adf0-4763a9399bb3" TYPE="swap" 

reboot - edit your grub line to replace the string of characters with the string you have noted.

---

### Post by adenewton on 2010-05-27
Hi David thanks for the reply.

The UUID that Grub has is correct.

What I did notice and I'm not sure if it's important is that my partitions go from sda1 (which is the XP partition as it was my understanding that installing Windows first was better practise because of it wiping out Grub when it's installed after Linux) and the next partition is sda5, which is my Xubuntu partition, followed by sda6 which is my swap partition.

I would have assumed there is no problem in it skipping straight from sda1 to 5, but wonder if it's having an impact.

I'm temped to wipe the disk completely and set up the partitions again, but the thought of re-installing XP and downloading all the updates is quite frankly depressing!!

---

### Post by kansasnoob on 2010-05-27
Sounds like it could be a bug:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Try Step 1 of that guide to find out.

---

