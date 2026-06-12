---
title: "Using LILO instead of Grub"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by VK2XCI on 2006-07-30
G'day all.
Celeron 800, 20Gb HDD, 256Mb of 133mHz SDRAM. First 9.5Gb of the HDD has Win2K SP4. Remainder currently has Mandrake 9. Dual boot is handled by LiLO.

I want to replace Md9 with Dapper. There is nothing on that partition I need to save, so a complete Default install is possible. Except... I have had problems with "grub" on a previous occasion, hanging partway through the first boot, denying me Win2K or Hoary and necessitating a reinstall of Mdk9 simply for the LiLO to get Win2k back.

I guess the question is... tadaaa....
How do I install Dapper in place of Md9 using LiLO in place of grub?


TIA

---

### Post by adamkane on 2006-07-30
There isn't too much info on LILO with Ubuntu, and It's been two eternities since Hoary.

I was a believer in LILO, when I used to use SuSE, but GRUB works just fine with Ubuntu and dual-boot.

There are many tools that work very well with Ubuntu, and this is a result of the choices that have been to develop certain tools rather than others.

---

### Post by VK2XCI on 2006-07-31
> **adamkane said:**
> There isn't too much info on LILO with Ubuntu, and It's been two eternities since Hoary.

I was a believer in LILO, when I used to use SuSE, but GRUB works just fine with Ubuntu and dual-boot.

There are many tools that work very well with Ubuntu, and this is a result of the choices that have been to develop certain tools rather than others.

(Added)Do you actually dual boot with Windows? How large is your Windows partition? 

Your right, it has been two eternities. A quick check shows it was "Breezy" that gave me all the grief!:oops: 

How do others manage a Windows partition greater than 8.xx Gb. I probably display my ignorance here but I believe that was the problem with Win2K/Breezy/grub? It hung at stage 1.5 as I remember:confused: 

LiLO sure does make it easy, although I understand there is a Grub2 under development?

---

### Post by adamkane on 2006-07-31
I have dual-boot on my mother's PC, but I'm still in denial in regard to using Windows, so I won't be much help.

Here's some good info though:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It shows how to choose LILO, if you like, and also shows how to install Dapper, if you already have Windows installed.

If you have problems, this is probably the most common thing that Ubuntu users deal with, so I'm sure there are knowledgeable people around to help.

I don't think there is an 8GB issue anymore, but hopefully someone can confirm this for me.

Just keep replying to your posts, until someone contributes.

---

### Post by VK2XCI on 2006-07-31
> **adamkane said:**
> I have dual-boot on my mother's PC, but I'm still in denail in regard to using Windows, so I won't be much help.

Here's some good info though:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Snipped....

Just keep replying to your posts, until someone contributes.

 Thanks Adamkane,
The link is excellent and in the usual way led to another, and another and....

I'm not exactly a Linux noob, been at it since Red Hat 5.2! It seems that each new distro is dumbed down just a little more untill all those wonderful choices which are Linux simply dissappear.

I might do a text based install of Debian, just to remind myself how much fun it is. ](*,)  
Sheesh, what was I thinking :-&

I'm going to take a punt and install it from the Desktop CD. It'll either work or it wont. Might make a Windows emergency recovery CD first. Otherwise I guess it's another download... the  "Alternate" Install CD.

---

### Post by VK2XCI on 2006-07-31
> **VK2XCI said:**
> Thanks Adamkane,
The link is excellent and in the usual way led to another, and another and....

I'm not exactly a Linux noob, been at it since Red Hat 5.2! It seems that each new distro is dumbed down just a little more untill all those wonderful choices which are Linux simply dissappear.

I might do a text based install of Debian, just to remind myself how much fun it is. ](*,)  
Sheesh, what was I thinking :-&

I'm going to take a punt and install it from the Desktop CD. It'll either work or it wont. Might make a Windows emergency recovery CD first. Otherwise I guess it's another download... the  "Alternate" Install CD.

Well,
Here we are from my brand new, updated, Dual Boot Dapper Drake Installation. And it went more or less like a dream. I messed up the formatting a little 'cause I wanted to put a FAT32 partition in to share some documents from NTFS. Also a separate /home partition. Anyway the installer crashed and I had to redo a fair bit of work.

It appears that the previous problem with grub is resolved. I rtfm'd everything I could find and it appeared to be a BIOS translation problem. 1 BIOS update later it all seems to work!

There are some problems with the monitor resolution which bear investigating... an X prob I think.

---

### Post by adamkane on 2006-08-01
Very similar to my mom's installation. No sound on her machine at the moment, but I haven't invested the time to fix it.

---

### Post by intangir1999 on 2006-11-28
I recently tried installing dual boot on my system that has win2k on the first hd (as master) and completely clean 250 gig as second.  Tried putting SUSE 10.1 on the second (installed fabulously) and kept getting pesky Grub ERROR 18 on it and it wouldn't boot up from the second drive.  Even on the Expert mode of Boot Rescue, it gave me an error when I tried using LILO instead (something about 8gig limit for cylinder) I didn't know what was going on and after 2 days of trying to get it to load up I ended up putting winxp on it.  Oh well, I'll have to settle for using vmware for now.  733 Mhz of pure computing power baby!  *lol* ](*,)

---

### Post by adamkane on 2006-11-30
You have to be sure to install grub/lilo on the MBR, which is at the beginning of your first hard drive. 

The boot menu then points to your root or boot partition for each OS.

---

