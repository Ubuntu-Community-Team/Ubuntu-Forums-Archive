---
title: "Fresh install Hardy, update problems"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by PgTips on 2008-06-20
Just completed a fresh instal of Hardy - no problems. Connected to internet and opened update manager. Informed of loads of updates so went ahead and clicked install. Now have a number of broken packages so went to Synaptics Package Manager to fix. Seem to have a number of OpenOffice packages  that are listed as broken.Asked SPM to fix but getting "An error occured", " The following details are provided:"
 
E: /var/cache/apt/archives/libcame|1.2-11_2.22.2-Oubuntu2_i386.deb:corrupted filesystem tarfile-corrupted package archive

I am a relative newbie so any help would be greatly appreciated.:confused:

---

### Post by Pumalite on 2008-06-20
Try this:
sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by avtolle on 2008-06-20
> **Pumalite said:**
> Try this:
sudo apt-clean
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

Do the above commands one at a time, in the order Pumalite gave them. Post back any error messages.

---

### Post by PgTips on 2008-06-20
sudo apt-clean = command not found

---

### Post by PgTips on 2008-06-20
sudo dpkg etc returns a long list mainly citing dependency problems with open office stuff

---

### Post by PgTips on 2008-06-20
final command returns another long list ending up with " E: Unmet dependancies, Try using -f."

---

### Post by avtolle on 2008-06-20
Missed this the first time around, s/b```
sudo apt-get clean
```
Give that a try again.

---

### Post by PgTips on 2008-06-20
Sorry must be a bit slow here. Exactly what to type please? Confused by [/code

---

### Post by PgTips on 2008-06-20
just gets me the prompt ( machine with problem is a desktop - doing this on my old laptop which is running hardy brilliantly)

---

### Post by avtolle on 2008-06-20
Should just give you a prompt. Now, run each of the other commands Pumalite posted again and see if the corrected one made any difference. Sorry about the error, caught it and edited it as soon as I could, but you saw it first. :-(

---

### Post by PgTips on 2008-06-20
this is making more sense now. it seems to be loading a lot of archive files.

---

### Post by PgTips on 2008-06-20
loads of "failed to delete", error processing",
"read only file system", unable to access dpkg status area" etc.etc.

I am going to have another try and if it doesn't work I might do what worked on this laptop - upgrade from 7.10. I still have the cd that I installed 7.01 from so it shouldn't be a problem BUT reading the posts on this forum suggests that there may be something badly amiss and it could be that waiting for 8.10 would be the better thing to do!

---

### Post by Pumalite on 2008-06-20
I have 4 Hardies. All working fine. 2 32 bit and 2 64 bit in different arquitectures.

---

### Post by PgTips on 2008-06-20
I have just started a fresh install from a dvd issued with Linux Format magazine which produced a fine working system on the desktop machine before I tried to run Update Manager. This time I will not do any updates until you advise me what to do.

Ok stage 1 is complete ie the system is running fine from "live cd". All functions seem to be working inc OO.o and sound, audio etc.now I'm going to click on "install icon. It is 2244hrs.
Setting the time zone is like being "warped" into the future! Have had to select London by scrolling the list - the map is unuseable with a mouse!
have selected 1st default partitioning ie Guided resize SCSI1((0,0,0), partition #1 (sda)and use freed space
New partition size Ubuntu 8.04 98% (110.3GB)

[this drive is nominally 120GB and is the only HD in the machine]
[ I am informed that the resizing could take a long time but this machine needs to know I can be quite patient before I start kicking it !]
That wasn't too bad it is now 2259 and it wants my name etc.
I have just clicked "install" at 2301
It tells me "Partitions Formatting" and the bar shows 5%, thereis no activity from the Hdd LED and I notice that the mouse pointer will not respond. The system clock at the top right hand of screen is still showing 1101 but this machine which is a laptop running hardy ok is now showing 12.07 (local).
I'll post this and browse around for a while until something else happens!Ho Hum!

---

### Post by PgTips on 2008-06-20
Ok! It's 10 mins later and things haven't changed ie the "Installing System" window shows exactly what it did and the machine seems to be asleep (except for its fans of course)Time now as I leave for another browse 1221hrs local

---

### Post by Pumalite on 2008-06-20
What are your specs? And what iso are you using?

---

### Post by PgTips on 2008-06-20
Its a QDI motherboard with 700Mhz cpu, 750GB, Nvidea  (can't remember which), was successfully running 7.10, upgraded to 8.04 online was fine and worked ok but then had to use machine for another purpose. Decided to do "fresh" Install from dvd provided by Linux Format magazine - worked fine until I then tried to do updates using Update Manager when aformentioned problems started. It is now 1233 local and Installing  System window is exactly the same as was!

---

### Post by Pumalite on 2008-06-20
Install using the Alternate CD. Download the iso from here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
256 MB of RAM or less>Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/)
Do md5sum and burn at 4x or less.

---

### Post by PgTips on 2008-06-20
ok will try that. I think I have had enough for tonight. Many thanks for your patience and help. I will keep you informed.

---

### Post by PgTips on 2008-06-20
The Desktop has 750 MB RAM so should have no probs with Ubuntu ?

---

### Post by kayakfisher on 2008-06-20
Have also tried upgrade, dpkg does not recognize --configure -a;
it also returns an error ivman error -1 message.
There are not any other broken packages or files that I've found.
This upgrade has now taken 25 continuous hours; locked-up at 1 minute before "cleaning" and still will not play a simple DVD.
No wonder so many stay with Mic**S**t this OS is not ready for use except by overrated/overpaid geeks with too much time on their hands.

Gone kayak fishing, the big fish are at High Island Texas.

---

### Post by PgTips on 2008-06-20
Can't entirely agree with you. Earlier versions have run fine! This just has teething probs. One thing you don't get once you have a running version is all the crap and dreaded blue screens and corrupted registers that the gates and windows firm puts out with all their offerings. AND you don't get tied into using expensive OS and apps software! Best of all - you don't have to scrap perfectly good legacy hardware 'cos the support gets pulled and the corrupt conspiracy needs to keep us all buying replacement kit and software that spies on us!

And no I am not a paranoid schitzophrenic!

You paddle yours and we'll keep paddling ours but we'll be free before ya!

---

### Post by Pumalite on 2008-06-20
> **PgTips said:**
> The Desktop has 750 MB RAM so should have no probs with Ubuntu ?
You can go for 8.04 Desktop.

---

### Post by PgTips on 2008-06-20
Hi agin,

decided to have one more try before going to bed. Opened up desktop and unplugged everything in sight (old tecchy trick) and reconnected, cleaned dvd and drive and got a clean re-install from the LinuxFormat DVD. this post is being typed on the said machine (time 0239 local).
The update manager tells me there are 248 updates I can install. The question is: dare i try installing the updates or will i get back to the situation I had before?
I don't intend doing anymore until I get some advice and now that i seem to have my system back up and running (even if it needs updating) I am definitely logging off and going to bed in the next fwe minutes. Look forward to reading any replies later. Many thanks again.

---

### Post by Pumalite on 2008-06-20
A good system is one that can update without problems. So, go for it and if you have problems again, try a different iso. We can further investigate if you have hardware incompatibilities. You have to be able to update your system.

---

### Post by PgTips on 2008-06-21
I am going to consider my problem SOLVED :)
I did try the updates and all went reasionably well apart from being informed of 6 broken packages. This was easily fixed this time round by Synaptics package manager. The system is now up and running quite sweetly and all appears functional - I am operating it now for this post. It would be nice to have a definitive analysis of why I had the problems. Might be an intermittent hardware issue for instance. However, I do thank you for your interest and help - very much in the spirit of "community" I think. To others who may have been following this thread the lesson is perhaps "perseverance"! This IS a great OS and worth taking the time to learn!
As somone once said; "In a world of open systems who needs windows and gates?"

---

