---
title: "Your installation CD-ROM couldn't be mounted..."
date: 2004-11-02
forum: Installation &amp; Upgrades
---

### Post by ValKov on 2004-11-02
Can not install Ubuntu Linux on an IBM ThinkCenter PC. I have this message:
Your installation CD-ROM couldn't be mounted. This probably means that CD-ROM was not in the drive. (It [COLOR=DarkRed]was ![/COLOR]) If so you can insert it and try again.
Any idea how to fix this problem ?

---

### Post by mercurus on 2004-11-03
[QUOTE=ValKov]Can not install Ubuntu Linux on an IBM ThinkCenter PC. I have this message:
Your installation CD-ROM couldn't be mounted. This probably means that CD-ROM was not in the drive. (It [COLOR=DarkRed]was ![/COLOR]) If so you can insert it and try again.
Any idea how to fix this problem ?[/QUOTE]
 If you have multiple optical drives, boot into the BIOS and disable whichever one is NOT going to contain the Ubuntu CD. Also, when Ubuntu first starts, press F1 and check to see if there are any kernel options you need to pass to make your CD drive recognised.

Cheers
mercurus

---

### Post by ghc on 2004-11-03
I have also had this problem with an IBM ThinkCentre. I only have one optical drive. This particular model of ThinkCentre is using a chipset that does SATA as well as one PATA port, if that is relevant.

---

### Post by moabin on 2004-11-04
Hii,
Did you figure out this problem?,I'm getting the same error on a Dell at work...tried noacpi and nolapic  and every other code I thught would be usefull, but nothing....
The LG CD-RW drive I have is about 4 years old though....

---

### Post by francis on 2004-11-04
I got my CD recognizedl on my Dell Opitiplex with
"linux pci=off" 
However I do not have a successful install yet!

---

### Post by DarkLotus on 2005-02-07
I am having this same problem with an IBM Netvista Desktop PC.  Any ideas yet?

---

### Post by DarkLotus on 2005-02-07
I figured it out.  For whatever reason, Ubuntu doesn't like the Lite-On drive that came standard.  I put in a plain old NEC drive and it worked fine.

---

### Post by rsms-tsp on 2005-02-07
I also have an IBM Netvista and have the cd mounting problem during installation.

Has anyone over come this problem without replacing the cd drive?

Thanks in advance for any help.

---

### Post by DarkLotus on 2005-02-08
[QUOTE=rsms-tsp]I also have an IBM Netvista and have the cd mounting problem during installation.

Has anyone over come this problem without replacing the cd drive?

Thanks in advance for any help.[/QUOTE]

Does the light on the drive light up when it says it is searching for your cd rom?  If so, try replacing the drive and I bet it will work.  You should be able to get a CD-Rom for pretty cheap if you don't have an extra one.

---

### Post by Nezzles on 2007-02-25
I realise that I'm adding this reply almost 2 years after someone last replied but I came across this thread while trying to get Ubuntu to load from my IBM NetVista computer. I thought I'd add my two cents in case others come across this thread.

When I tried to boot Ubuntu off the CD, I'd get the black screen with the white cursor at the left-top corner flashing. It wouldn't progress to anything else.

Like the others suggested, I changed my CD Drive and now Ubuntu can load on my NetVista. :)

---

### Post by ReneJ on 2007-03-19
I just built a PC for my Fiancee and I am trying to install Edubuntu on it. I used the Lite-On drive out of an IBM NetVista and I am getting the same error. I guess I'll have to try swapping it out as well.

Rene

---

### Post by minhaz4u on 2007-09-30
Hi...I'm an old member of Ubuntu Forum..have not been using Ubuntu for quite some time..but now I'm back :)

I've used Ubuntu ver 5.10...n It was kool...I really liked it!

Now when I try to install Ubuntu 7.04 for AMD 64bit...It shows the same error u guys used to have "Your installation CD-ROM couldn't be mounted" n installation stops right there...

Is there any solution for this? It can't be the Installation CDs' or Files' problem...I've hash checked it already n tried writing on CDs with the lowest writing speed...still no difference :( 

Plzzzz help...I really wanna explore this version of Ubuntu...

---

### Post by minhaz4u on 2007-09-30
PLzz help!!! :-) Luks like no one is interested in this topic ...

---

### Post by mpolly on 2007-12-10
I found an answer that worked for me on another thread. After the CD boots and you're presented with the different options e.g. Install to Hard disk, Install a LAMP server, etc... select option F6. Append the following to the boot string

ide=nodma

That worked perfect for me!

---

### Post by aaronfay on 2008-06-26
Again, this answer probably also comes late, I tried installing the alternative 8.04, same issue, couldn't mount the cd-rom.  Replaced my lightscribe (3 days old) with the one out of my wife's machine, and I finally got past that step in the installation.

Cheers, 
af

---

### Post by Kidaf on 2008-06-26
You could try to install it from your hard drive with the Alternate CD, so there will be no need to get the drive to even bother: [http://ubuntuforums.org/showthread.php?t=782603](http://ubuntuforums.org/showthread.php?t=782603)

If you already got some version of ubuntu (or other distro with GRUB) it shall be easier. Else, just get a tuto on installing GRUB.


Hope it helps.

---

### Post by gerih on 2008-06-26
Hi All,

I am not sure that I am writing this msg into the correct post, but please somebody help me to install ubuntu 804.
I am newbie and I have never used linux before, but now I would like to be linux-fan.
Describtion of the issue (I think it's the same...):
When I tried to install ubuntu, I always got an error message about cd-rom (no common cd-rom drive detected). This problem occurs after language, keybord settings and something... (I don't remember clearly).
I have already tried to install with alternate CD, change the CD, burn the CD again and modify the DMA in BIOS... but I am not a lucky man in this topic, because I experince same issue.
I have read a lot of forum about it, but I couldn't find any solution.
Please advice:confused:

Thanks, Geri

---

### Post by gerih on 2008-06-29
Hi,
nobody answered to my post, but in the meantime I could solve my problem...
The ubuntu install process couldn't mount my cd-rom, because it couldn't see any mount point. Why couldn't see? I have to spend a lot time on it, but finally I changed my HDD. After that everything worked fine!
Conclusion:
The ubuntu don't like my Samsung 160Gb HDD...
But now I enjoy ubuntu OS!

---

