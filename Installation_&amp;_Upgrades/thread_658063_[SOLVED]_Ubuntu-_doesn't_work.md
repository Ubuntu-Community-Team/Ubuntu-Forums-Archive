---
title: "[SOLVED] Ubuntu- doesn't work"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by carterrocks on 2008-01-04
I booted the CD, checked for errors just in case using the option on the menu.  There weren't any then I proceeded to the install it.  I clicked on the install icon.  Which took ages but it eventually loaded a small window giving me the option to cancel.  So i waited and waited then that disappeared but then a warning box popped up telling me that there is a problem with some file (GNOME i think), it asked if i wanted to delete it or not.  I didn't and waited forever but the installer just stopped and didn't do anything after that.  Please, please help!

---

### Post by njparton on 2008-01-04
List your hardware please.

---

### Post by carterrocks on 2008-01-04
dell dimension DE051 Intel Celeron 2.80GHz 2.79 GHz, 256 MB of RAM

I think that's it, i'm a total n00b

---

### Post by PmDematagoda on 2008-01-04
I think 256Mb of RAM is too much to run Ubuntu properly let alone run the Live CD which requires at least about 384Mb of RAM to work properly. 

I would suggest that you install either [Xubuntu]("http://www.xubuntu.org/get") or [Fluxbuntu]("http://wiki.fluxbuntu.org/index.php?title=Get"), both of which would work great on 256Mb of RAM. But since Fluxbuntu is lighter than Xubuntu, Fluxbuntu would work much better on your PC than Xubuntu would.

---

### Post by carterrocks on 2008-01-04
I actually have an Xbuntu live disc but I noticed it didn't have the inbuilt partition thingy like Ubuntu and I'm really concerned about losing XP.  So how do I partition my hard rive?

---

### Post by PmDematagoda on 2008-01-04
> **carterrocks said:**
> I actually have an Xbuntu live disc but I noticed it didn't have the inbuilt partition thingy like Ubuntu and I'm really concerned about losing XP.  So how do I partition my hard rive?

Actually the Xubuntu 7.04 Live CD(The others must too) does have a partitioner, what version of Xubuntu do you have?

---

### Post by meindian523 on 2008-01-04
In case it doesn't,you can use the GParted Live CD [here]("http://gparted-livecd.tuxfamily.org")

---

### Post by njparton on 2008-01-04
> **carterrocks said:**
> dell dimension DE051 Intel Celeron 2.80GHz 2.79 GHz, 256 MB of RAM

I think that's it, i'm a total n00b

Are you sure about your RAM???

That's not very much for a modern PC!

Are you sure you're not confusing system RAM and graphics card RAM. I'd expect you to have 2048 or at least 1024 MB of system RAM.  I don't think Dell sell PC's with less than a gig?

---

### Post by amdalex on 2008-01-04
Edgy Eft works fine on one my computers with 256mb of RAM.:)

---

### Post by carterrocks on 2008-01-04
> **njparton said:**
> Are you sure about your RAM???

That's not very much for a modern PC!

Are you sure you're not confusing system RAM and graphics card RAM. I'd expect you to have 2048 or at least 1024 MB of system RAM.  I don't think Dell sell PC's with less than a gig?

The computer's like 4 years old lol and I'm pretty sure Xbuntu or the version which i've got (not to sure, i downloaded in last January 07) doesn't have the built in partitioner.  If the distro does have it in built doesn't it usually say something about free space, just guessing as fedora and ubuntu do. I'll just have use GParted- need to track down a CD first.

---

### Post by Bigglesw on 2008-01-04
I have the same problem.  The installation stops at 15%.

Its a Toshiba Portege 7200.  I have no idea how much ram it has.  It runs PCLOS OK.

I have tried making a second ISO disk, but it stops at the same place after bout and hour +

Not very impressed so far for the chart topper.

Any ideas people.

BTW I have tried install with partitioning and whole disk install and tried it form safe and done a disk check.

Cheers

---

### Post by carterrocks on 2008-01-05
> **Bigglesw said:**
> I have the same problem.  The installation stops at 15%.

Its a Toshiba Portege 7200.  I have no idea how much ram it has.  It runs PCLOS OK.

I have tried making a second ISO disk, but it stops at the same place after bout and hour +

Not very impressed so far for the chart topper.

Any ideas people.

BTW I have tried install with partitioning and whole disk install and tried it form safe and done a disk check.

Cheers

How's that the same problem?

---

### Post by Bigglesw on 2008-01-09
> **carterrocks said:**
> How's that the same problem?
Errrr because it is freezing at 15%!!

---

### Post by Pumalite on 2008-01-09
Follow these guidelines:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
256 RAM or less>Xubuntu Alternate CD:[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Do md5sum, burn at 4x or less

---

### Post by Bigglesw on 2008-01-10
Thanks for the reply.  I will try that.

I have sucsessfully installed 6.06 but it won't find my broadcom WiFi card and the system tools are missing so i can't get any further with that.

Will 7.01 install over 6.06 now do you think?

---

### Post by astabeno on 2008-01-11
Use the alternative install CD instead of the live desktop CD.  I put 6.10 on a lot of computers with 256MB Ram with the Alternative Installation and it worked great, but the Live CD would not load since it relies on RAM so heavily.

---

### Post by Bigglesw on 2008-01-11
Hi

I have now done 6.06, I could not see a version between that and 7.01.  DO you have a link.  Will it get my BCM43xx wifi going?

BTW the live 7.01 runs live.

---

