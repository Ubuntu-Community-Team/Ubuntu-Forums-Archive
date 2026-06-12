---
title: "Installation problems with ubuntu 8.0.4.1"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by TenshiKiri on 2008-08-07
Hey all, I downloaded Ubuntu 2 days ago and tried to install it on 2 of my machines.
On the first one, it got installed like a beauty, fact is I am writing through that specific installation atm.

On the 2nd pc though.... with BOTH X32 and X64 installation disks - _not server editions_, after the initial choice of language and installation type, all I get is this:
> 
Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)_

Any ideas?
The setup of the pc in question is:
*Asus a8v-mx
AMD Athlon 64 3200+
2 Giga ram
Sata hdd 120GB

*edited. mixed gpu manufacturer with mobo ^^"

---

### Post by TenshiKiri on 2008-08-08
bumpity bump!

---

### Post by coffeecat on 2008-08-08
I might not be able to help you much, but the busybox shell is often a result of the live CD tripping over some aspect of the hardware it can't cope with. So...

Are you sure that's a MSI a8v-mx motherboard you've got there? Googling 'msi a8v-mx' came up with [this page]("http://www.digital-daily.com/motherboard/via_vs_ati/"), so which is yours? :wink:

If it's the **Asus** AV8-MX, then you've got the Via  K8M800 chipset which should pose no problem at all. My (older) home-build has a m'board (not Asus) with that chipset and I've had no problems with any distro that I've tried - except for one thing. Although there are SATA connectors on my board, when I tried with a SATA drive, I ran into all sorts of problems - can't remember exactly what now - and I went back to using an IDE drive. Of course, this might be a problem peculiar to my board and/or BIOS version, but I notice that you are using a SATA drive. Have you tried with an IDE drive?

---

### Post by url00 on 2008-08-08
I'm having the same problem, but I won't be able to use anything but SATA. Does this mean I can't install ubuntu?
[B]
System Specs:[/B]
[I]Asus P5Q Motherboard
Intel Core 2 Quad Q6600
Nvidia GeForce 9600 GT
2 Gigs of RAM
SATA hard drive with 80 GBs[/I]

**Other notes:**
Using Vista on a 120 SATA hard drive right now.

---

### Post by nitsujol on 2008-08-08
i have the exact same problem.

my motherboard is ASUS P5Q Pro ATX LGA775 P45 DDR2 2PCI-E16 Crossfire 3PCI-E1 2PCI SATA2 Sound GBLAN eS.
HD = Western Digital Caviar SE16 640GB SATA2 7200RPM 16MB Hard Drive
wireless = Linksys WMP54G Wireless PCI Adapter 54MBPS 802.11G
ati 4870 = video card
intel 9450 = CPU
RAM = Corsair XMS2 TWIN2X2048-6400C4 2GB 2X1GB PC2-6400 DDR2-800 CL 4-4-4-12 240PIN Dual Ch


i have tried and tried but can't install ubuntu (or kubuntu which is my prefered flavour) to this pc but it all installs fine on older laptop.

is SATA the problem?


please help!

---

### Post by coffeecat on 2008-08-08
**url00** and **nitsujol**, I didn't say that SATA was a problem when installing Ubuntu. I was merely observing to the OP that SATA was a problem with my particular motherboard and that was one thing that could be considered. SATA is not a problem in itself with Ubuntu or Linux. I have another self-built machine with two SATA drives and Ubuntu installed to that as easily as anything.

You both have a different motherboard and possibly a different chipset. May I suggest you both start your own threads as your problem(s) may well be different? Give details of which installation media you used, exactly what problem you encountered and what the error messages were and try to give comprehensive details of your hardware. The motherboard chipset is important. Give that if you can. You should be able to find details on the manufacturer's website, or perhaps somewhere in Windows.

**Edit**: also, I suggest you both search for your motherboard using the forum search facility. Asus seems to be a popular make around here and you might get some useful information from threads that are more relevant to you.

---

### Post by TenshiKiri on 2008-08-08
Thnx coffeecat for the notice. It is in fact Asus / I got mixed up with the gpu manufacturer ^^"
Sata was the thing that crossed my mind too especially because it is the only difference in setup i could imagine between the two configurations.
Ill try with ide as soon as i manage to aquire a couple more free gigabytes on it and repost any info.

P.s. I tried installing with liveCD from windows os but it hangs right after it reaches the end of "creating image drive" or sth similar. and produces an error dialogue of "unable to access disk" BOTH by having mounted it as image through daemon tools and by physically accessing it from the disk drive.

---

### Post by nitsujol on 2008-08-08
> **coffeecat said:**
> **url00** and **nitsujol**, I didn't say that SATA was a problem when installing Ubuntu. I was merely observing to the OP that SATA was a problem with my particular motherboard and that was one thing that could be considered. SATA is not a problem in itself with Ubuntu or Linux. I have another self-built machine with two SATA drives and Ubuntu installed to that as easily as anything.


thank you for your reply! 

I was not quite accurate as i should have been 

i meant i had similar mb to url00. the only common thing i can see is SATA and i wondered if that was the problem somehow (although I know so very little about hardware that i am guessing widly in desperation to try and use ubuntu).

EDIT - for ASUS p5Q PRO there is a possible fix which i'll try later when i get ome from work - [http://vip.asus.com/forum/view.aspx?id=20080624021821000&board_id=1&model=P5Q&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20080624021821000&board_id=1&model=P5Q&page=1&SLanguage=en-us)

:popcorn:

---

### Post by dado_eyad on 2008-08-08
hi everyone i have the same problem 
my pc
motherboard:msi 945pl neo
processor:Pentium(R) D CPU 3.40GHz
ram:1.00 GB
hard disk:wd 160 GB sata2
graphic card:NVIDIA GeForce 7100 GS

you can see the eror in the img 



[http://www.lastown.com/files/dl.php/download/334/d498efcec0c90fcd0e453a54b1d78325/ABCD0004_1.jpg](http://www.lastown.com/files/dl.php/download/334/d498efcec0c90fcd0e453a54b1d78325/ABCD0004_1.jpg)

---

### Post by dado_eyad on 2008-08-09
HELLO!!!!!!
any body here???

it seems like no one cares about this problem :confused::confused:

---

### Post by meitnerium on 2008-08-18
You have to add the options all_generic_ide on grub boot (if you delete quiet splash at the same times, you will have more information about the boot)

At least, it worked for my Asus P5Q motherboard. After the install, I added the same options to /boot/grub/menu.lst

---

