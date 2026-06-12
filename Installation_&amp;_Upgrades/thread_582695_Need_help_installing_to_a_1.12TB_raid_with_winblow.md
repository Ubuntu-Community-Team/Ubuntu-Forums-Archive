---
title: "Need help installing to a 1.12TB raid with winblows"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Skypednikku on 2007-10-20
I have 4 HDD and i have them raided for network storage with my dads Winblows machine and i also have winblows on here to(GAMES).
And the drives are raided together and when i attempted to install it just saw all the drive indavidually and that reli confused me so i left well enough alone and right now im on the live. SO WHAT DO I DO???? 
OH yea UBUNTU 7.4 gusty 64bit.:mad::confused::(

---

### Post by xcafeus on 2007-10-20
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Thats the correct guide. Its seems to be ok with Feisty but with Gutsy??? I wouldnt say so... It definetely has issues. Maybe we need to wait until an expert updates the guide.

I have a two disk RAID0 and although the guide (with some improvising from my side) seems to work there are some issues upon booting... I log in with my user name and I do not have sound (even if there is sound at the login screen) and there are admin menus missing... also the terminal looks weird.

check this out:

[http://ubuntuforums.org/showthread.php?t=582543](http://ubuntuforums.org/showthread.php?t=582543)

Good morning and good luck :)

---

### Post by Skypednikku on 2007-10-20
N/A info...
MB ASUS CROSSHAIR 
HDD  1x 80 1x 160 2x 500 Raided
Processor AMD x2 4400+ AM2
Latest ubuntu 7.04 (I think)
followed above advice and now i can see the raid but now i cant do anything. 
NTSF File sys with winblows.

---

### Post by xcafeus on 2007-10-20
the guide explains not just how to see the raid but how to install the OS as well, including how to partition your RAID array... if your array is all NTFS you must follow the fdisk instructions to partion it ...first make an EXTENDED partion and then 3 logical drives in that (/boot, swap (with "sudo mkswap /dev/mapper/whatever_your_array_is_named") and reiserfs) ..follow the rest of the guide afterthat step by step and with caution)

---

### Post by Skypednikku on 2007-10-20
I am running gusty not the other one and i cant use ubuntu for that entire raid(Id love to) but i have to back up my dads junk and manage a Wi/FI network... And i tried almost all of the guide and Gparted crashed So i will wait for a more advanced help. But thank you you got me one step closser to a succesxsful install.:)

---

### Post by xcafeus on 2007-10-21
> **Skypednikku said:**
> I am running gusty not the other one and i cant use ubuntu for that entire raid(Id love to) but i have to back up my dads junk and manage a Wi/FI network... And i tried almost all of the guide and Gparted crashed So i will wait for a more advanced help. But thank you you got me one step closser to a succesxsful install.:)

I did not use GParted but command line fdisk. It worked like a charm and Im dual booting with Windows XP on the same RAID0 array... Im posting from Ubuntu now ;) ...I had some small issues after 1st reboot but managed to solve them myself... it seems that nobody is using soft RAID0....

good luck and dont give up ;)

---

### Post by Skypednikku on 2007-10-27
Unable to edit NTSF partion.... using fdisk. NOW WHAT?:confused:

---

### Post by xcafeus on 2007-10-29
what do you mean? what is that you want to do? in my case I had windows xp installed on the whole array..I used perfectdisk to defrag the raid array and then uding fdisk under ubuntu livecd I created an extended partition and then 3 logical drives (/boot, /, swap) as shown in the guide. Then I followed the rest of the instructions step by step. My NTFS works fine and the dual boot with windows is flawless.

---

### Post by Skypednikku on 2007-10-29
It says unable tom read the contents of the arry and then it gives me no option under fdisk. I may not be doing it right.... but When it comes to command lineing The best i ever did was  in dos and it was the format command and even then i screwed it all up. I ment to format A: and i formated C: So do you have any mor advice? Perfeably for a noob!:confused::confused::confused::confused::confused::confused:

---

