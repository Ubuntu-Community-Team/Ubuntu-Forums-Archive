---
title: "Dual OS on SSD and HDD"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by BloodyDream on 2012-12-03
have'm building a computer within the next few weeks, and I'm finishing up the last few things. I want to have Linux and Windows available. I originally was going to go with only Ubuntu, but then I realized it would be easier to run games and stuff from Windows. I bought a 90GB SSD for a boot drive, this is big enough for windows, but it isn't preferred. What I want to do is have Windows on the HDD and Linux on the SSD. I want to install Windows on the SSD first and then replace it with Linux so that I don't have to install the drivers, which worked on my other computer. Then I want to install Windows on the HDD. The HDD is 2TB so I want to partition 1TB to Windows and Windows files, and the other 1TB to Ubuntu files. This may not e described very well, if it isn't then I'll clarify it on when I'm on my computer.

---

### Post by mikewhatever on 2012-12-03
Why exactly are you going to install Windows, and then replace it? Why not install the way you want to right away?

---

### Post by BloodyDream on 2012-12-03
Because that saves me from having to find and install all of the individual drivers. At least that's my hope.

---

### Post by oldfred on 2012-12-04
If you build you own computer most of the vendors provide Windows drivers. With Ubuntu you do not get nor need any drivers. Or like the nVidia drivers, you download them if needed from the repository.

I have a 64GB flash drive and used gpt partitioning as suggested by the Arch site. You only have to have gpt with drives over 2TB or UEFI booting. Windows will only boot from UEFI systems from gpt partitioned drives. 

My 64GB has two / (root) partitions. One for my current install and the other for my next or testing install. Swap (which is almost never used with my 4GB RAM), and almost all data is on my rotating drives. My install is 9GB including 2GB for /home. My /home is only that large as I do not move .wine for Windows Picasa to my data partitions.

       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
            [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by orb9220 on 2012-12-04
"90GB SSD for a boot drive, this is big enough for windows, but it isn't preferred."

Whaaaat? 90gb is plenty even for a triple boot system. Have a Win7,Winxp and Mint 14 in less than 80gb.

"I want to install Windows on the SSD first and then replace it with Linux so that I don't have to install the drivers, which worked on my other computer." 

Again confused I am. You aren't thinking that your windows drivers are used by Linux are you?

Personally plenty room and would install Win7 first taking half for it and then install linux on other half of the ssd.

And the 2TB as my data drive for both. All my music,pics,movies,etc...

But that is just me.
.

---

### Post by BloodyDream on 2012-12-04
Thanks a bunch Oldfred. I'll check that out. And I can just run Ubuntu straight off without even downloading any drivers or anything? 


"Whaaaat? 90gb is plenty even for a triple boot system. Have a Win7,Winxp and Mint 14 in less than 80gb."

Everyone I've talked to uses at least a 120GB. That is what is most commonly recommended.  


"Again confused I am. You aren't thinking that your windows drivers are used by Linux are you?"

Well no, not exactly. I talked to a guy about installing Ubuntu and he was telling me all of these drivers and stuff to download, I told him that all that I did the other time I installed was just install and replace Windows, and he said that since the drivers were already pre-installed with Windows that that was why. I guess he was just full of crap or something? haha

I'm definitely just going to keep the two separate, with Ubuntu on the SSD. I will eventually buy another SSD for Windows 7 or 8 and then clear it from the HDD.

---

