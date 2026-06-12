---
title: "Weird VirtualBox problem in Intrepid"
date: 2008-07-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ASULutzy on 2008-07-12
I'm not sure if this is an issue with Intrepid, Microsoft Windows, or VirtualBox, but I'll present the information I have anyway.

In both Intrepid Alpha 1 and Intrepid Alpha 2 (both 64 bit) using the most up to date VirtualBox, I am unable to successfully boot into my Windows XP .vdi image. The XP.vdi works to boot Windows XP in my 32 bit Hardy install, but for some reason when I try to boot into it on my 64 bit Intrepid install, it blue screens and returns me to the Windows menu of 
boot into safe mode
safe mode with networking
etc....
start windows normally
And no matter what I pick it BSOD's immediately and restarts the VM. 

Running virtualbox in a terminal hasn't been very helpful as I don't know if there's anyway to get a verbose mode or something.

Any help would be greatly appreciated, as I do .NET programming for a living which I use my XP virtual machine for, and I'm concerned that when 8.10 is officially released I may have to reinstall my VM with all my development tools.

The evidence sort of points as Microsoft Windows as the culprit to blame (since Intrepid/VirtualBox are booting the image, and then Windows is BSOD'ing) but figured I'd ask anyway. Thanks again!

---

### Post by Gina on 2008-07-12
Wouldn't it be easier to dual-boot Ubuntu and Windows?

---

### Post by dinxter on 2008-07-12
there was a bug that sounds exactly like yours that cropped up the early virtualbox 6 releases that was related to hardware virtualisation support if i remember correctly. it was cured for most people i though with the 6.2 releases (now in intrepid) . if you're on that release already it may be worth investigating some of the virtualbox settings in the general->advanced catagory anyway as it sounds more like a virtualbox bug than a problem with your windows image.

---

### Post by dinxter on 2008-07-12
specifically try disabling either/or of the new pae/nx support, vt-x/amd-v and sometimes the hard drive controller can be changed to sidestep bugs. also note that io apic must be enabled if it was enabled on the original windows install image

---

### Post by cariboo on 2008-07-12
If you look at this page here:

[http://www.ubuntu.com/testing/intrepid/alpha2](http://www.ubuntu.com/testing/intrepid/alpha2)

and look under **caveats**. You will have an answer to your question.

Jim

---

### Post by ASULutzy on 2008-07-13
Gina, I do have a dual-boot setup, but I don't really like Windows quite as much as I do Ubuntu for my day to day needs, so while at work I just boot into Ubuntu with a Windows VM for Visual Studio.

dinxter, I will try fiddling with all the VB options.

Jim, I was unable to find anything under caveats that specifically related to what I mentioned. Those folks were all having issues using Hardy or Windows as a host and booting into Intrepid; my problem is the exact opposite (sort of). I can boot my XP as guest inside of Hardy, but when I try to boot XP as guest inside of Intrepid it BSOD's.

I'll try to change various options in VB and report back.

---

### Post by ASULutzy on 2008-07-13
Weird, I swear I changed nothing but now it seems to be working fine. Oh well, shouldn't look a gift horse in the mouth!

---

### Post by caryb on 2008-07-13
I'm in the process of creating a image of my Xp partition, why not because I like Windows but am a IT Engineer that needs some functionality built into windows to do my job. I will have by the end of the day a working Kubuntu & Xp running in Vbox on dual monitors, this will give me the best of both worlds. A great O/S & a legacy one to get me by till I can remove Microsoft from my networks.

Why the rant? because some of us unfortunately require Windows to do our jobs & dual booting is a pain in the backside.


Cary

---

### Post by cariboo on 2008-07-14
I just had a look a the caveats again and I could have sworn there was something in there about XP freezing at login with Virtualbox too.

Oh well:)

Jim

---

### Post by Gina on 2008-07-14
Ah yes - I can see the benefits of VM :)  I'm fortunate in needing MS Windows only very rarely so dual-boot on one machine suffices.

---

