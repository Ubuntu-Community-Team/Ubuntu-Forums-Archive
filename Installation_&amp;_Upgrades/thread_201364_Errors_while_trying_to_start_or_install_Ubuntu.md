---
title: "Errors while trying to start or install Ubuntu"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by Adjutant on 2006-06-21
Hello, I've got a problem trying to get Ubuntu to work on my PC.

Whenever I chose the first option to "Start or install Ubuntu", I always end up with the error "<0>Kernel panic - not syncing: Fatal exception in interrupt"

Then I tried the second install option of "Start Ubuntu in safe graphics mode" and it ends up freezing when it gets to "Loading hardware drivers..."

I'm using the i386 installer on my Pentium D 820 computer. I'm not sure, but I think that might be relevant.

Any help is appreciated.

EDIT: Also, some told me elsewhere to "run the text-only installation disc instead." How would I do that?

---

### Post by bukwirm on 2006-06-21
The text-based installer is on the "alternative install CD". The iso for this image is available here: [http://ubuntu.cs.utah.edu/releases/6.06/]("http://ubuntu.cs.utah.edu/releases/6.06/")
Scoll down to the bottom half of the screen.

---

### Post by Adjutant on 2006-06-21
Hey guys, I got the installation done. But I'm getting that problem again....

It get's stuck on "Loading hardware drivers...."

I don't know what to do. Erased everything on my PC (typing from my laptop), it only has Ubuntu on it, which won't even load up. Can anyone help me with this issue. I've got no idea what's wrong, I did a search and I found a thread, so it is a known issue and hopefully someone's working on it because I haven't been able to find a solution anywhere.

Can anyone point in the right direction? I'm kind of lost, first-time linux user.

---

### Post by bodhi.zazen on 2006-06-22
Ubuntu is broken right now. If it is not working try another version of Linux.

Consider PCLinux or Mepis or Kanotix

Re-try Ubuntu in a few weeks once it has stabalized. Ubuntu has been rock solid in the past and hopefuly it will stabalize again.

If you want to persue Ubuntu I will need more information to help you. Try booting with a live CD and look at your Ubuntu partition. If there is data on the system the problem may be with GRUB (your boot loader).

First, If Ubuntu is the only OS on the computer, at the time of Ubuntu install you should install GRUB to the MBR (Master Boot Record).

Second, could you post the contents of your /boot/grub/menu.1st file.

---

### Post by manicka on 2006-06-22
[QUOTE=bodhi.zazen]Ubuntu is broken right now. If it is not working try another version of Linux.
[/QUOTE]

Broken is a strong term and not accurate. There are some issues with the desktop cd install on some machines, but they are fixable through the use of the alternate image and a text based install or by using the many solutions offered on these forums.

Stick with Ubuntu, it has never looked better :)

---

### Post by bodhi.zazen on 2006-06-22
manika:

Not true. My Ubuntu system is broken with no fix in sight.

Your own site states: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

" Make sure you type  dist-upgrade  rather than  upgrade , because  upgrade  will totally hose your machine and render it completely unbootable. (Why? This warning would have a lot more impact if someone could explain it!)"

Althouh I used synaptic my Ubuntu system seem totally hosed and the solution is not "fixable through the use of the alternate image and a text based install or by using the many solutions offered on these forums." as you say. There is no solution on the forums I can find.

Any system that becomes totally hosed using standard update techniques (synaptic) has some serious issues.

If you know of a solution I would be eternally grateful.

---

### Post by rcarring on 2006-06-22
Can you boot into safe recovery mode using the Breezy kernel?

---

### Post by Adjutant on 2006-06-22
[QUOTE=bodhi.zazen]First, If Ubuntu is the only OS on the computer, at the time of Ubuntu install you should install GRUB to the MBR (Master Boot Record).

Second, could you post the contents of your /boot/grub/menu.1st file.[/QUOTE]

Alright, I don't know how to do either of those, but I imagine it would be kinda hard to explain it to me over the internet. I'll try and play around with the installer see if I can do that.....

Well, I been loking elsewhere as well, asking questions and such. So far I've been recommended that I remove all my USB connections then try again...didn't help. 

Then I was told to try to remove my graphics card, and reinstall it later after I have installed drivers for it..... haven't tried it yet. (I'm using a 6200 nvidia, btw. someone noted that they were able to boot ubuntu without having to remove his video card). 

And finally, I was told to try and turn off acpi, which I have no idea how to do.

also, I'm downloading ubuntu breezy at the moment, going to try that too.

I really really wnt to try out Ubuntu. I been able to run the liveCD on my laptop, and it seems pretty good and not as difficult as I imagine from that brief encounter with it. I just wishe it would work on my PC. If nothing works, I'll just try another distro. :(

---

### Post by bodhi.zazen on 2006-06-22
First, to install Ubuntu use the "alternate CD" rather then the live CD. After the system installs you will get to a menu asking where to install GRUB, chose MBR (may be the default choice, I do not recall).

Your menu.1st is easier. Boot with the Live Ubuntu CD (any live cd will do). Open /boot/grub/menu.1st with any editor (nano, Kate, Abiword, OpenOffice). Cut-and-paste contents to Ubuntu forums.

---

### Post by Adjutant on 2006-06-22
[QUOTE=bodhi.zazen]Your menu.1st is easier. Boot with the Live Ubuntu CD (any live cd will do). Open /boot/grub/menu.1st with any editor (nano, Kate, Abiword, OpenOffice). Cut-and-paste contents to Ubuntu forums.[/QUOTE]


I figured out how to do the first one, however, the problem is, I can't boot Ubuntu at all. With or without a Live CD. =( So I cannot check.

I'm taking out my graphics card right now, let's see if that solves anything.

I've already tried booting with acpi=off and dma=off

I tried using live CD for breezy, same problem....

I've already got PClinuxOS downloading on this laptop if none of it works.

---

### Post by Adjutant on 2006-06-22
Ok, I just took off my video card and modem card off my PC and ubuntu is working!

I'm not sure which of these two pieces of hardware was going wrong with my ubuntu, but I'm guessing it was the video card.

Now I'm getting an x server problem, but I think I'm getting this problem because I installed ubuntu with my computer while I was still using my video card. I'm going to try and reinstall ubuntu on my machine and hopefully problems are solved.

I am most certain this will solve my problem because I just loaded Ubuntu with the live CD with no problems.

My video card is a GeForce 6200 by the way. It's weird, because someone reported that their 6800 did make it thru ubuntu.

Anyways, I'm glad I go through this problem. Now one more thing stands, how do I make my video card work now? Do I have to install the drivers first then install the hardware? And how do I install the drivers?

Thank God for 4chan, sometimes those guys just really know how to do things right.

Edit, think i'll post this critical piece of information for reference on why it didn't work

> Chingon !cEPW06zQ8s 06/21/06(Wed)23:06 No.99401 

Unless you have linux drivers installed for ATI or nvidia (no Ubuntu installer includes them AFAIK), you must remove your AGP/PCI/PCI-E card and use onboard until you've installed the proper drivers.

Follow instructions carefully. When you're done, put your GPU back in its original place; it might take a while for "loading hardware drivers" to finish btw.

---

### Post by bodhi.zazen on 2006-06-22
Adjutant:

Good news, and bad.

Good news is you do not need to boot ubuntu to read the menu.1st. If you boot PCLinux or Mepis it will mount your hard drive. The mount point may vary and will either be /mnt/hdax or /media/hdax where x is the number of the partition.

Partitions are /dev/hdax and are mounted with:

mount /dev/hdax /mnt/hdax

Thus menu.1st will be located in:

/mnt/hdax/boot/grub/menu.1st

Nice on video driver issue. You need to install the navidia driver(many, if not most versions of Linux, including Ubuntu, do not come with the navidia drivers).

---

