---
title: "ubuntu and vista dual boot"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by dutchmarc on 2008-12-01
Hi,

I have read through a bunch of threads trying to figure out thsi problem, but none seem to be exactly the same. I am a lunix newbie so am pretty lost.

The problem I have is that when installing ubuntu on my system (with vista already installed), I keep getting grub erros when the system is restarted.

I have a raid0 system (could be a "fake" one since its a dell pc), but if I remopve the raid to have 2 individual disks, it is unable to recognize any disk at all. So I think I definitely need the raid volume there (Even looked in bios settings and am unable to change settings there). 

Installing ubuntu after creating a empty partition works fine. It seems to have no problem whatsoever to install it from either the live cd or alternate cd. but when the system reboots I get a GRUB1.5 error (seen 21,15,7 so far) and am unable to access either ubuntu or windows.

Reading up in other topics, it seems that raid configurations aren't that great for this, but since my options seem slightly limited I don't think i have a choice.

Any help would be greatly appreciated

Thanks

---

### Post by theozzlives on 2008-12-01
I would say install Ubuntu as your host system with Vista in a virtual box [http://www.virtualbox.org]("http://www.virtualbox.org")

---

### Post by dutchmarc on 2008-12-01
never knew that one, sounds interesting. think it would work with windows already installed and ubuntu runnign in virtual box?

---

### Post by caljohnsmith on 2008-12-01
With fake RAID, as far as I know you have to go through special steps in order to install Grub properly; if you can change your BIOS setting so that your drives are non-RAIDed and recognized as individual drives by Ubuntu, I think that's the easiest solution. But if you want to give fake RAID a try, you could give [this tutorial]("https://help.ubuntu.com/community/FakeRaidHowto") a go. Let us know how it goes. :)

---

### Post by dutchmarc on 2008-12-01
definetly cannot switch raid of in bios unfortunately. Am not even 100% if it is fake raid, but ill try that tutorial and see what happens. Thanks for the info

---

### Post by theozzlives on 2008-12-01
> **dutchmarc said:**
> never knew that one, sounds interesting. think it would work with windows already installed and ubuntu runnign in virtual box?

You could try that, I think they make VB for Vista, or if you stick the Ubuntu disk in with Windows running, it gives you the option of installing under Windows.

---

### Post by dutchmarc on 2008-12-01
> **theozzlives said:**
> You could try that, I think they make VB for Vista, or if you stick the Ubuntu disk in with Windows running, it gives you the option of installing under Windows.

yeah tried that the second time, which also failed miserably for some reason. just not having a lot of luck with it.

---

