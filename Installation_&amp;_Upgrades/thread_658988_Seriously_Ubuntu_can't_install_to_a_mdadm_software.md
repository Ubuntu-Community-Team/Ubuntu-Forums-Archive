---
title: "Seriously? Ubuntu can't install to a mdadm software RAID array?"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Fed on 2008-01-05
Hi folks.

I wanted to switch one of my machines to Ubuntu today. It's got two Seagate 10K SCSIs on an Adaptec card (non-RAID), so I've been using a mdadm RAID1 array which uses the two drives. However, once I get to the partition editor/manager part of the install, /dev/md0 is not shown. The two drives are, but no array. Is there any way to manually give it a device (md0) to use, or some shortcut to open up advanced options, something? Anything?

Thanks!

---

### Post by Fed on 2008-01-06
So does anyone know how to make it install to the mdadm array? I'm guessing the "alternate desktop" CD might enable me to do this, and I guess the server edition CD would work, but I still have trouble believing the regular one can't install to /dev/md0, and I'm still not sure if the alternate  desktop CD would in fact be my solution and I'm not exactly jumping at the chance to waste another CDR. And I'm guessing the server edition might not have a GUI etc. There really should be a "learn more" or "details" link on the download page about how the versions and the alternate desktop CD differ.

---

### Post by JimTDI on 2008-01-06
Check this page out:  [http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)  It explains a bit about the difference between versions.  You are correct, the server version has no GUI.

You do need the alternate install CD to do software RAID.  My experience is with Feisty and older releases, so I can't say for sure about Gutsy (7.10), but the partitioner in the alternate installer lets you create software RAID partitions.

CDs are cheap - go for it!!

Hope that helps.

---

### Post by Fed on 2008-01-07
Thanks a lot, I just didn't want to waste a CDR out of principle (plus they're getting really rare, its all DVDRs now :p). Anyhoo, thanks for your input and I'll try the alternate CD today, although its a bit of a shame that I have to lose the GUI and user-friendly installer to get something like software RAID going. I've been going through a phase of trying out pretty much every linux distro I could think of, and so far opensuse takes the cake for the installer, it's absolutely great (this isn't criticism for the Ubuntu team, who have done a great job, just an observation and perhaps something to look at).

And just for the record, using the normal Desktop CD, I decided to go one step further. I took two old drives, and when I got to the desktop, I did apt-get install mdadm, created a new array, and the installer still failed to see that. I doubt it would take much effort or space to get the partitioner in the normal Desktop CD to at least see and be able to install RAID arrays (and not create them).

Thanks again, just thinking out loud there, maybe my experiences could be used to improve Ubuntu :)

---

### Post by JimTDI on 2008-01-10
Hey... no problem!  So how did your install go? :)

I've now installed Gutsy with RAID1  to dual 160GB drives.  Put Grub on both drives so I can boot to either.  This weekend I will test yanking a drive out of the Raid array, booting, and then letting it rebuild.  Will do the same with the other drive after it rebuilds, and will let you know how it goes.

Yeah, the text installer leaves a little to be desired, but it's just that, a text installer.

---

### Post by Fed on 2008-01-10
Thanks for asking, but the install didn't go well, I eventually gave up. I've installed Ubuntus before, and I've even installed Debian very recently, so I was no stranger to that text-based installer but for reasons beyond my knowledge it consistently failed during the Select and Install Packages phase. Ubuntu asks very few questions, to make the install easier for people no doubt, so I didn't even Select packages, it just tried installing whatever it's configured to. However I just kept getting the error that said something along the lines of "a part of the install process has failed" without any specifics, and threw me back to main setup overview where I could try again. However it always gave that error. Just didn't seem like it was worth my time eventually.

---

### Post by JimTDI on 2008-01-12
I had similar problems when the text installer in Ubuntu detected my network settings as DHCP.  When I cancelled auto-detect of the network in the installer, and then manually configured the network in the installer, everything then worked for me.  Sorry to hear it didn't work for you...

---

### Post by Fed on 2008-01-13
That was the only thing I could figure as well - something wrong with the internet. I had to select some setting which made it ask me more questions just to switch from DHCP to static, which I then did, but it still failed. I was quite irked that I couldn't even select the mirror to use manually :/ Oh well, I guess Ubuntu is great for putting Linux on the desktop for the mainstream folks, but for me I can't help but feel that ease of use has hindered flexibility too much. I'm not saying anything is wrong with it at all and I admire what it's trying to achieve, it's just that I came to the conclusion that it's probably not for me. It's OK, no harm in trying. Tried Fedora 8 the other day and was quite impressed, opensuse and it are currently my favourites.

Thanks a lot for your sentiments :)

---

