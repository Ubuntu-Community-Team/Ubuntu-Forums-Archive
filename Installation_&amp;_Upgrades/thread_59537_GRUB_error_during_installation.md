---
title: "GRUB error during installation"
date: 2005-08-24
forum: Installation &amp; Upgrades
---

### Post by balaji on 2005-08-24
I was installing Warty - the GRUB loader installation went upto 50% and then stopped with some error. After that i installed LILO onto the MBR. After that, system automatically booted into linux - then ubuntu didnt recognize my username for some reason - so i was locked out of my computer.

my system has win xp - so formatted c: and reinstalled windows - now my system is super slow - i have no clue why this is happening.

is it a cd problem?how can i install ubuntu properly? also, should i format my disk again(windows partition)?

---

### Post by balaji on 2005-08-25
I'll explain the sequence of steps i did:

1. booted with the ubuntu install cd

2.all smooth until partition step

3. I chose "manually edit partition"
        i selected a 5 GB partiton

         format the partition: yes      
          file system: ext3
          mount point: /
          boot flag: off

        another 300 MB partition  as swap

4. Base system got installed

5. Grub went upto 50% - then stopped with some error(cant remember what that was - forgive me - i'm a newbie)

6. LILO got installed in MBR

7. after that windows did not boot - LILO loaded linux directly

8. at the ubuntu login screen - i gave my username and password. but it did not accept that and kept asking again and again - i don't know why this happened either.

hopeless situation - cant boot into windows or ubuntu

9. after that - formatted my c: with win xp cd and reinstalled windows. system booted but was terribly slow - again a puzzler.

10. i formatted the linux partition using partition magic - now speed is back to normal.

back to square one - no linux, only windows.

can someone help me out? 

 ](*,)

---

### Post by balaji on 2005-08-25
my linux partition is the first one on the hard disk - windows on second one. will that cause a problem with windows?

---

### Post by rubenjavier on 2005-08-25
I have the same problem, the installation goes fine until GRUB needs to be installed, It gives me an error no matter where I tell it to be installed, it can't be installed on the primary boot record or in any other partition/HD on my machine
the weird thing its that I've already installed ubuntu in another 3 different machines with no problems (including a laptop)
In the laptop ubuntu is in a secondary partition of the only HD and GRUB is on the primary boot record
One the other two machines ubuntu is on a secondary partition on the 2dn HD of each machine and GRUB is on the primary boot record of the First HD while windowsXP is on the first HD
in my machine I had XP on the first HD and Ubuntu on a secondary partition of a 2dn HD (just like the other machines I've installed) the only difference is the motherboard (msi kt6v on my machine while the other where intel), and the HD are both set to be LBA on my machine too... what can be happening?
why can't I install GRUB on my machine... I used to have SUSE in this same pair of HDs with GRUB but I formatted them and reinstalled WinXP and now Im trying to instal ubuntu in the same HD were i used to have SUSE 9.2 (when I had SUSE with this same HDs and same partitions I had them on a different mother board)
any help would be appreciated
thanks

---

