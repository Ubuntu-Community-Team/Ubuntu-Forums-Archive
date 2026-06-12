---
title: "Vista won't boot after installing Ubuntu 8.04"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by PlasticCup on 2008-05-23
I had a working dual-boot of Vista and Ubuntu 7.10 (iirc), but Ubuntu stopped working after switching video cards (just a black screen after loading the kernel) and I needed it for some printer drivers (which weren't available for Vista. So I installed Ubuntu 8.04 over the old one, using the same partitions, thinking that it would work fine, but now Vista will not boot.

Every time I select Vista/Longhorn(loader) in the GRUB menu, it starts booting (the regular text I see, reseting boot device etc.) but then suddenly another GRUB menu appears, definitely not the same and not using my configurations (I left it at default after reinstalling Linux, but this one has the cyan "pretty" colours enabled and defaults to boot option 3 (being "Other OSes)).

Some things worth noting: it says GRUB4DOS at the top, I'm assuming this has to do with the fact I tried booting Vista.

It also displays some error message to the right of this, if you need the info I'll post it.

Also Ubuntu will not boot from this GRUB4DOS menu, as it will hang in the screen with the Ubuntu logo and the orange bar moving side to side, not moving onto the one with the orange bar filling, and after several minutes (not measured exactly, I usually walked away in frustration at this point) showing me a command line with "initramfs" or something similar.

The Vista installation disc will not repair my Vista install as it doesn't find any problems ( D:< ), and I've also already tried SuperGrub, but that won't fix it either >.>

I hope I've sufficiently explained my problem, any help is welcome, any suggestions will be attempted, just probably not today as I have an exam in a few hours and after that a nice long work-evening >.>

---

### Post by itix on 2008-05-23
I interpret this as the old grub lingering in the system. It was a wierd problem though.

Did you delete the partition completely befor installing 8.04 or did yu just "update" the old system??

My best bet is to reinstall 8.04 and see if it install grub correctly.

---

### Post by PlasticCup on 2008-05-24
Thanks for the reply.

I have two Linux-related partitions on my hdd, one root and one swap, which together are 5 GiB. It's what I had from my 7.10 install, so I just formatted the root one (couldn't check the format box with the swap one) and installed 8.04 over it. I've also reinstalled 8.04 a few times for several reasons (one being that I couldn't boot it from the GRUB4DOS screen, but hadn't realised it could be booted from the first GRUB screen, so I thought it was screwed and reinstalled it >.>)

Still Vista won't work though D:

---

### Post by itix on 2008-05-24
You know the Gparted partitioning tool on the live CD??
Use that to delete both the Ubuntu partition and the swap, and install on the largest continous space. That'd be the wise thing to do. I think your problem right now is either too little space or dual swaps (or the wrong swap type). Either case, just reinstall ubuntu and use the GParted live CD.

---

### Post by PlasticCup on 2008-05-24
I don't really get what you mean.

When I (re)installed (not sure) 8.04, I deleted both Linux partitions and made one large (5GiB) ext3 partition for the root. Then it whined to me that it didn't have a swap partition, so I used 256 MiB off the 5 GiB to make a swap partition and the rest for root. Is that approximately what you mean?

Or do you mean remove the partition when in GParted, then use the "Guided" installation thingy? I guess this is what you mean, so I'll do it now, as I don't see it could do any harm.

---

### Post by itix on 2008-05-24
I mean that there is this wonderful option called "guided - install on largest continous free space" that I guess is your safest bet. Delete the old swap and ext3 partition and let ubuntu configure the new ones.

---

### Post by PlasticCup on 2008-05-24
Yes, that's what I remembered in my last part of my post ;)

Doing it as we speak, on the LiveCD now (I do really like that about Linux, the LiveCD).

---

### Post by itix on 2008-05-24
Yes, I know. It's wonderful for saving data from a destroyed operating system. All you need is an external drive and a Live CD ;)
A linux Live CD and a super grub disc should be in everyones cd-stack.

---

### Post by PlasticCup on 2008-05-25
Alright, reinstalled using "Guided - largest unused space" option, made no difference. However, I now cannot even start to boot Linux from the GRUB4DOS screen, as it cannot mount the partition or sth similar (forgot the exact message). 

I studied the message in the top of the GRUB4DOS screen a bit, and I noticed it said "Memory: 649K/3326M, CodeEnd: 0x3D7BC". I don't know what the CodeEnd means, but it seems like somewhere between GRUB and Vista my RAM isn't recognised properly, which is also confirmed by the "initramfs" command line interface I was faced with when booting Linux from GRUB4DOS before the last reinstall (I was told by a friend who also uses Ubuntu that initramfs only comes up if you don't have enough ram to boot Ubuntu).

So I ran memtest for a couple of hours (while I was working) and came back after 9 hours to see it had passed 7 times without errors.

Any ideas based on this new info?

---

### Post by fmartinez on 2008-05-25
If your still getting the option to boot from GRUB4DOS that means you still have that other boot loader installed. You propbably have a bootloader on the MBR and one on the primary partionion (just my guess). 
-- Have you tried recovering windows from a recovery disk?
I would suggest attempting to recover windows first then use the windows partitioner to free up some space for Ubuntu and go for the reinstall. The same way that was suggested previously. 
-- The other memory thing seems like you may have a bab memory block that maybe the reason your having trouble booting up. 
When you do the recovery it should clear that up.

---

### Post by PlasticCup on 2008-05-25
Well with memtest running over 9 hours, passing 7 times with NO errors, it would seem the memory is not faulty, right?

Also, I'd rather not reinstall Vista, as I have a lot of data I wouldn't want to lose, any suggestions for keeping that?

---

### Post by PlasticCup on 2008-05-25
Okay, little update. It does indeed seem that GRUB has been installed onto the Vista partition, because even when I remove GRUB from the MBR using the SGD, booting results in being faced with the GRUB4DOS screen from which I cannot boot >.>

So I restored GRUB using the same SGD and now am back in Ubuntu. Any suggestions on how to restore my Vista installation? I cannot "upgrade" Vista (keeping my files and such) because you have start the installation disc from Windows for that >.<

---

### Post by itix on 2008-05-25
There have to be some way to search and destroy grub4dos or override the normal grub to your windows partition, I just don't know how. Reintsalling grub won't help.

I wonder if... hmmm.

Could you post the menu.lst-file here. Just go to *apps => acessories => terminal* and type *gedit /boot/grub/menu.lst*

The parts I need are the vista and ubuntu menu entries that are located in the bottom of the textfile. It's somehere below the line "##Begin debian automagic list, etc etc"

---

### Post by PlasticCup on 2008-05-25
It is solved. I googled a bit, and stumbled upon a Microsoft Help article on restoring non-booting Windows installs. Turns out you can restore the boot with the Vista install dvd with the built-in command prompt using a program called bootrec.exe. This can restore the MBR to the default Vista one, and also restore your partition boot thingy, so I used that and Vista now boots. It did, however, remove my Vista activation, so I'll have to re-enter that, but apart from that, problem solved! :D

---

### Post by vikas.sriv14 on 2009-06-18
I have got the same problem .
Can somebody tell me exactly what to do from the Vista install DVD since i don't know much about windows.

---

### Post by merlinus on 2009-06-18
Better to ask this question in a windows forum, no?

Anyway, try booting from the install cd, select recovery (or restore) and fixmbr (or fixboot).  Or something along those lines.

---

### Post by raymondh on 2009-06-18
> **vikas.sriv14 said:**
> I have got the same problem .
Can somebody tell me exactly what to do from the Vista install DVD since i don't know much about windows.

boot into the install disk > select the language, etc > choose repair > select command prompt > type 

```
bootrec.exe/FixMbr
```

If OK, you should be greeted with "successful".  Quit.

Sometimes, there is a need to restore the boot sector.  In that case,

```
bootrec.exe/FixBoot
```

Good luck,

---

### Post by raymondh on 2009-06-18
> **PlasticCup said:**
> It is solved. I googled a bit, and stumbled upon a Microsoft Help article on restoring non-booting Windows installs. Turns out you can restore the boot with the Vista install dvd with the built-in command prompt using a program called bootrec.exe. This can restore the MBR to the default Vista one, and also restore your partition boot thingy, so I used that and Vista now boots. It did, however, remove my Vista activation, so I'll have to re-enter that, but apart from that, problem solved! :D


Well done on the Vista.  

-Backup those vista files.
-Check if you can boot into Ubuntu

---

