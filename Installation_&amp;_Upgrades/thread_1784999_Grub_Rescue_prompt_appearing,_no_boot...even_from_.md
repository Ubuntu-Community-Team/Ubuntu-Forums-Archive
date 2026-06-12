---
title: "Grub Rescue prompt appearing, no boot...even from live cd"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by MeetM on 2011-06-17
I had 250gb hard disk with dual boot, xp and ubuntu 10.10....
Yesterday, i tried to upgarde my ubuntu 10 to 11 from a live cd....b4 doing so, i used a win software EasyBCD to fix the mbr....but it didn't work properly..and i ignored it(my biggest mistake)...and deleted the ubuntu partion from the windows device manager...so when i rebooted my PC, i got this...

error: no partion found ...(or something like that)
grub rescue>...

i read many threads on this forum......
they all said to boot with a live cd....
i tried that but this too didn't work!
It just displays "Booting from Live CD" for few minutes and again displyas the same above error...
What should i do now????
Its ok if i m not able to recover my data back...i hv sycnd my docs on the internet...
Plz help. thanx

---

### Post by mörgæs on 2011-06-17
> **MeetM said:**
> 
What should i do now????

First of all you should not double post. It is not very respectful to the (maybe) two groups of people trying to help you.

---

### Post by pricetech on 2011-06-17
If you're not worried about your data, then wipe the drive with whatever will boot.  If you had Windows, your Windows boot disk should let you wipe the partitions and start fresh.

DBAN will wipe it too.

Once wiped, if you still have problems booting with the Ubuntu CD, I suggest you check your download and reburn.

---

### Post by YesWeCan on 2011-06-17
You'll need to restore a standard MBR so XP will boot. Some options:
1) Use a Windows CD to run fixmbr if you have one.
2) Boot a live Ubuntu CD and install and run lilo:
[COLOR=DarkGreen]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]   #assuming sda is your Windows drive
3) Install Ubuntu to another device and Grub to the same device. Boot it and run '[COLOR=DarkGreen]sudo update-grub[/COLOR]' to scan your other drives and add XP to its boot menu. Reboot the device and choose XP. Once in XP open a terminal and fix the MBR (probably fdisk /mbr or something - you'll have to Google for it).
4) I think you can boot XP directly from the grub rescue prompt. I can't remember how to do this but this is the very best option. I'll try to find out.

---

### Post by YesWeCan on 2011-06-17
I Googled for a bit and then tried reading the official Grub Manual but I started to feel the life-force draining from my body.

My best guess is that you need these commands at the rescue prompt, assuming XP is the first partition on the drive:
[COLOR=Navy]set root=(hd0,1)
chainloader +1
boot[/COLOR]

---

### Post by MeetM on 2011-06-18
m really sorry sir.....i m a newbie here......so i was a bit worried that my problem wont be noticed under this category. So i posted the same in the general...I m exteremly sorry and i m deleting that post now..thanx

---

### Post by mörgæs on 2011-06-18
There is nothing wrong with learning. Welcome to the fora.

---

### Post by MeetM on 2011-06-18
ok...i hd Ubuntu 10.10 installed...but i now have CD of ubuntu 11...so will it be ok if i boot with this cd???

---

### Post by MeetM on 2011-06-18
i tried set root=(hd0,1) ......but didnt work 4me

---

### Post by Quackers on 2011-06-18
As YesWeCan suggested earlier, I would suggest that you get XP booting again first (unless you wnat to forget about XP altogether).
Do you have a Windows XP repair disc? If so run fixmbr from the command prompt in the repair console and then reboot to see if XP boots again.

---

### Post by MeetM on 2011-06-18
ok...i ll try it tommorrow(aftr 12hrs) and let u know...coz i have xp cd now. Thanx!

---

### Post by MeetM on 2011-06-19
I tried booting XP Sp2.....but no luck....

it shows something like this.....

Verifying DMI pool data........
Boot from CD _ (and the cursor blinks for about 15secs)
error: no such partition...
grub rescue>

please help! can there be a problem with my CD ROM? but the indicator on the CD ROM blinks and even the disc spins inside...can i remove my hard disk from PC and put in some other PC and then boot the CD? will it help?

---

### Post by Quackers on 2011-06-19
Is your bios set to boot from the cd before the hard drive?

---

### Post by MeetM on 2011-06-20
Ya...obviously......anyways i ll try and replace my cd rom with my friend's and then see what happens.....a kind of busy these days so unable to repaiar it in one shot....

---

### Post by MeetM on 2011-06-23
Hey, it worked..........i replaced my cd rom with a working 1 and booted the xp cd and it was so easy.........didn't even had to write any commands........windows showed me that there is already xp installed and an unknown partition.........i just frmatted the unknown partition and rebooted.....it worked fine.......thanx guys!

---

### Post by Yoru A. on 2011-11-07
hello guys :) i'm having a similar problem :( i had ubuntu 10.04 installed side by side with win7, but i removed it from windows coz i was having troubles with it -.- i want to reinstall it but when i want to specify the partitions...well, before i got a slider bar where i could do it :S now i get this...partition table i honestly don't know how to use ;_; i don't want remove win7 from this computer, but i can't start it with win7 coz it takes me to the grup rescue prompt...i read somewhere i could set root to the device that had win7 in it...but i can't do that either XD i'm really sorry if this question seems stupid but, how can i fix this? i mean, set the partition with win7 so the comp starts with it, from the grub rescue prompt??
i tried 
set root =(hd0,1)
boot

but then i get a message saying "uknown command 'boot'
:( help please?


EDIT: oh i fized the boot problem ^^; sorry, went into panic mode...i'd still like to know how i get the slider to specify the partitions back...but i think i'll google that or look into the formus :P thanks!

---

