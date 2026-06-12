---
title: "Beta Cataylst Driver for ATI"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by helliewm on 2008-10-15
Seee here [http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1]("http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1") Anyone with an ATI 4850/70 Graphics Card now has a Beta Catalsyt driver in the repositories that is compatible with Xorg 7.4. It seems AMD did not want to lose Ubuntu customers due to Intrepid using Xorg 7.4.

This Beta Driver should work for other ATI cards too. I only mentioned 4850/4870 as I have a 4850 card. It is a general ATI Catalyst Beta Driver so should work on most modern ATI cards.

It was released into the  Intrepid Repositories last night.

Helen

EDIT: Remember to do sudo apt-get update and sudo apt-get upgrade FIRST, before following my instructions, as this ATI Catalyst Beta Driver has literally only just hit the Intrepid Repositories.

---

### Post by helliewm on 2008-10-15
I installed the ATI Catalsyt drivers as per Phoronix article above in Synaptic Package Manager.

Then I used the command:

sudo aticonfig --initial -f

I rebooted and the ATI drivers work brilliantly with Intrepid and Xorg 7.4.

Helen

---

### Post by olskar on 2008-10-15
Glad to hear! But is it only for ATI 4850/70?

---

### Post by helliewm on 2008-10-15
No I don't think it is I only mentioned 4850/4870 as I have the 4850 card. It is the next ATI Catalyst Driver so should work with other ATI cards.

Remember to do sudo apt-get update and sudo apt-get upgrade first as its literally just hit the repositories.

Helen

---

### Post by syxbit on 2008-10-15
this is great news!
unfortunate that ATI is being secretive though :(

---

### Post by olskar on 2008-10-15
> **syxbit said:**
> this is great news!
unfortunate that ATI is being secretive though :(

Yeah but it's better then nothing :)

---

### Post by lacanadio on 2008-10-17
Works for me out of the box on a Dell Inspiron 1721 w/Radeon 1200. Compiz up, some hitches, but not many. Thanks for getting the beta out of ATI!

---

### Post by syxbit on 2008-10-18
i can't get compiz working on my 4870 properly.
i either use metacity which works.
or compiz, which works, but i get MAJOR tearing in vidoes.

---

### Post by biasquez on 2008-10-18
catalyst beta support mobility radeon 9700 too?.. because i have problem loading fglrx module..

---

### Post by ercdvs on 2008-10-18
Did this bork hibernate for anyone else?

  640.580738] PM: Creating hibernation image: 
[  640.584208] PM: Need to copy 138844 pages
[  640.584208] PM: Normal pages needed: 128031 + 1024 + 24, available pages: 112085
[  640.584208] PM: Not enough free memory
[  640.584208] PM: Error -12 creating hibernation image


Was fine before.. only change being the new ati driver

---

### Post by inportb on 2008-10-18
Oh, the ati driver worked just fine in my case; it was fglrx that broke hibernation and suspension.

---

### Post by ercdvs on 2008-10-18
> **inportb said:**
> Oh, the ati driver worked just fine in my case; it was fglrx that broke hibernation and suspension.

I just pulled fglrx out.. and hibernate works again..  how can you use the ati driver seperate from fglrx ?

---

### Post by Mazza558 on 2008-10-18
It works here but it's pretty slow for me (about the same as the FOSS one)

---

### Post by ktp on 2008-10-18
It is pretty slow for me too...I am even thinking about going back to open source driver.

---

### Post by alienexplorers on 2008-10-18
Will this driver work with an old Radeon 9250.  I would like to try it, but I am not sure what I need to do to set it up.

Tried it and it screwed up my system.  Luckily I got it fixed am I am back on "ati" driver.

---

### Post by energycore on 2008-10-19
> **syxbit said:**
> i can't get compiz working on my 4870 properly.
i either use metacity which works.
or compiz, which works, but i get MAJOR tearing in vidoes.

Same for me :)

Lucky i'm not a big fan of compiz.

---

### Post by ktp on 2008-10-19
> **alienexplorers said:**
> Will this driver work with an old Radeon 9250.  I would like to try it, but I am not sure what I need to do to set it up.

Tried it and it screwed up my system.  Luckily I got it fixed am I am back on "ati" driver.

I guess it is not supported:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
> The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500.

---

### Post by Isilion on 2008-10-19
Does that beta ATI driver works for ATI radeon 9800 pro? I have problems with Catalyst 8.10 in Xubuntu 8.04. Details at this thread:

[http://ubuntuforums.org/showthread.php?t=766699](http://ubuntuforums.org/showthread.php?t=766699)

(if you know whats, the problem, submit reply in that thread, please. Thanks)

---

