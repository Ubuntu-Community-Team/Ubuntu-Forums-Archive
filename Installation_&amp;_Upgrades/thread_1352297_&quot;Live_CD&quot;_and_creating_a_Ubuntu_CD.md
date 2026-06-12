---
title: "&quot;Live CD&quot; and creating a Ubuntu CD"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by tcwild on 2009-12-11
I almost feel sheepish about posting this; but here goes...

I've seen so many references to a "Live CD"; but nothing that states (with any real meaning) exactly what that is. I have 9.10 installed and running on my laptop, no real issues. Is the "Live CD" the ISO I burned (and used to install the OS) after downloading? 

One issue I do have is installing some of the tools I'd like to have. When I attempt to install things like a "Partition Editor" (don't recall the exact name; but can get it), I get a message that I need to insert the "Ubuntu CD..." to proceed. The above mentioned CD doesn't work, and I don't see anything that tells me how to create that CD (assuming it's possible).

Thanks for any/all responses. Ubuntu rocks!

---

### Post by darkod on 2009-12-11
Yes, LiveCD is the standard Desktop CD / image.
As for partition editor, if you mean Gparted, in terminal try:
sudo apt-get install gparted

---

### Post by dhavalbbhatt on 2009-12-11
> **tcwild said:**
> I almost feel sheepish about posting this; but here goes...

I've seen so many references to a "Live CD"; but nothing that states (with any real meaning) exactly what that is. I have 9.10 installed and running on my laptop, no real issues. Is the "Live CD" the ISO I burned (and used to install the OS) after downloading? 

One issue I do have is installing some of the tools I'd like to have. When I attempt to install things like a "Partition Editor" (don't recall the exact name; but can get it), I get a message that I need to insert the "Ubuntu CD..." to proceed. The above mentioned CD doesn't work, and I don't see anything that tells me how to create that CD (assuming it's possible).

Thanks for any/all responses. Ubuntu rocks!

As darko says, the LiveCD is the desktop installation CD that you probably burnt and used to install Ubuntu.

With regards to the installation of GParted and the message that you are getting - can you be a bit more specific about things like when are you getting the message? I am assuming you are getting the message because if you go to System-Administration-Software Sources, then you may have "checked" the boxes right at the bottom of the first tab (can't remember exactly what they are, but if the checkboxes next to the "get software from CD" (or a variant there of) are checked, then Ubuntu will also look for the Ubuntu CD when trying to install any software, instead of just getting it from the repositories that you have selected). If that is indeed the case, then uncheck those boxes and try running the command that darko provided.

Hope that helps.

---

### Post by emigrant on 2009-12-11
Live CD is the image you burnt to your cd. its called by that name because unlike windows OS cd, with this live cd you can take a tour on the system without actually installing it to a machine. and if you feel you should go with it then you can install it.
as for the partition editor which is called gparted it should be installed by default in karmic and is accessible through System>adminsitration>gparted

---

### Post by tcwild on 2009-12-11
> **darkod said:**
> Yes, LiveCD is the standard Desktop CD / image.
As for partition editor, if you mean Gparted, in terminal try:
sudo apt-get install gparted

Thanks for the quick responses. 

Here's the terminal response:

[B][I]$ sudo apt-get install gparted
[sudo] password for ron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dmraid kpartx libdmraid1.0.0.rc15
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils ntfsprogs
The following NEW packages will be installed:
  dmraid gparted kpartx libdmraid1.0.0.rc15
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 479kB/627kB of archives.
After this operation, 4,395kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main gparted 0.4.5-2ubuntu1 [451kB]
Media change: please insert the disc labeled                                   
 'Ubuntu-Studio 9.10 _Karmic Koala_ - Release i386 (20091027)'
in the drive '/cdrom/' and press enter
[/I][/B]
I put the LiveCD into the drive, press enter, and get this:

[B][I]Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main kpartx 0.4.8-14ubuntu2 [27.9kB] 
Media change: please insert the disc labeled                                   
 'Ubuntu-Studio 9.10 _Karmic Koala_ - Release i386 (20091027)'
in the drive '/cdrom/' and press enter
[/I][/B]
I know we're close!

---

### Post by darkod on 2009-12-11
I wasn't aware you are using Ubuntu Studio. Are you inserting the same disc from which you installed?
The Desktop CD (or LiveCD) is not Ubuntu Studio.

---

### Post by tcwild on 2009-12-11
> **dhavalbbhatt said:**
> As darko says, the LiveCD is the desktop installation CD that you probably burnt and used to install Ubuntu.

With regards to the installation of GParted and the message that you are getting - can you be a bit more specific about things like when are you getting the message? I am assuming you are getting the message because if you go to System-Administration-Software Sources, then you may have "checked" the boxes right at the bottom of the first tab (can't remember exactly what they are, but if the checkboxes next to the "get software from CD" (or a variant there of) are checked, then Ubuntu will also look for the Ubuntu CD when trying to install any software, instead of just getting it from the repositories that you have selected). If that is indeed the case, then uncheck those boxes and try running the command that darko provided.

Hope that helps.

Perfect, thanks! Unchecking the box was the solution.

---

### Post by tcwild on 2009-12-11
> **darkod said:**
> I wasn't aware you are using Ubuntu Studio. Are you inserting the same disc from which you installed?
The Desktop CD (or LiveCD) is not Ubuntu Studio.

True. Are their fundamental differences? 

I installed Studio as much for 'fun' as anything, and don't really need it. Grub shows two entries for Ubuntu (plus the two 'recovery' entries) in the Boot menu. 

Is it possible to uninstall Studio without messing things up?

---

### Post by dhavalbbhatt on 2009-12-11
> **tcwild said:**
> True. Are their fundamental differences? 

I installed Studio as much for 'fun' as anything, and don't really need it. Grub shows two entries for Ubuntu (plus the two 'recovery' entries) in the Boot menu. 

Is it possible to uninstall Studio without messing things up?

GRUB showing two entries does not really equate to 2 Ubuntu installations in all cases. It could also be a case of two separate kernals. Can you post a screen shot (or just type that up for the community to take a look at)?

---

### Post by tcwild on 2009-12-11
> **dhavalbbhatt said:**
> GRUB showing two entries does not really equate to 2 Ubuntu installations in all cases. It could also be a case of two separate kernals. Can you post a screen shot (or just type that up for the community to take a look at)?

I would; but I just did a completely fresh install of 9.10. No Studio, no XP partition. Everything is back up and running perfectly.

Thanks everyone for the quick answers.

Now - HOW DO I MARK THIS THREAD AS 'SOLVED'?

---

### Post by darkod on 2009-12-11
> **tcwild said:**
> I would; but I just did a completely fresh install of 9.10. No Studio, no XP partition. Everything is back up and running perfectly.

Thanks everyone for the quick answers.

Now - HOW DO I MARK THIS THREAD AS 'SOLVED'?

No problem, you're welcome. Above the first post, in Thread Tools.

---

### Post by tcwild on 2009-12-12
> **darkod said:**
> No problem, you're welcome. Above the first post, in Thread Tools.

Done. 

I tried to get comfortable with Linux (Red Hat, 6.3 I believe) many years ago, and just couldn't get there Ubuntu is a genuine competitor for current desktop OS's in my humble opiniion. Aside from some technical issues on some hardware I don't actually need to use with this machine, it is perfect so far. Plug-n-Play works as well with everything I have as any other OS I have (and better than most). 

Good stuff, and the guys on this forum are nothing short of awesome.

---

