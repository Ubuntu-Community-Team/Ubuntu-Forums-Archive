---
title: "Fakeraid install issues"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by LinuxAlexs on 2013-11-20
Hello

I'm trying to install Ubuntu Studio 13.10 64 bit version on a PC that already has multiple Windows installations.
To make life easier (and I tried it before without creating partitions though windows in case anybody asks) I created the swap file and root partition with Acronis Disk Director for Windows.

I placed in the setup CD, booted off it and here is what I see in terms of partitions, notice the duplication of the volumes.

[IMG]http://i42.tinypic.com/jjr29v.jpg[/IMG]

So please notice I am using a Dell XPS 8100 and what you are seeing here is mirrored drives. I suspect my machine is probably using FakeRaid. 

Afterwards I tried again this time using the nodmraid option and this time the hard disks were not detected at all (empty screen).

I appreciate there is documentation out there on the net, however it appears to be a minefield (too much documentation!) and it is difficult to know where to look, and the documentation I looked at didn't work or confused me. 
The documentation is often also assuming I know how to drop out and drop into the command shell at will (which I don't).

Could anybody give me a hand please?

Thankyou!

Alex

---

### Post by LinuxAlexs on 2013-11-21
Anybody?

Many thanks...

---

### Post by LinuxAlexs on 2013-11-22
Er a little help please would be very much appreciated....

[IMG]http://www.fullgifs.com/wp-content/uploads/2013/08/Animated-cartoons-classic-help-tied-gif.gif[/IMG]

(Dancing baby next).

Thanks :).

---

### Post by LinuxAlexs on 2013-11-23
Well I politely posted the same question in 2009 and got no reply then either...
I guess nobody is going to reply to this looking at the track record (was I being perceived as rude or something?)....

So here are some tap dancers for your enjoyment...

[IMG]http://stream1.gifsoup.com/view6/2198270/fred-astaire-tap-dancing-o.gif[/IMG]

Thankyou Ubuntu forums!

(Dancing baby postponed, but coming soon...)

---

### Post by LinuxAlexs on 2013-11-23
As promised here is not one but two dancing babies... 

Each one to represent the confusion I have after trawling through the fakeraid FAQ...

[IMG] http://3.bp.blogspot.com/-Kb2T-OnCw5s/UIFC8Esc1JI/AAAAAAAABfo/m6BqJ-OYtaI/s1600/dancing_baby_b1.gif[/IMG]

[IMG] http://3.bp.blogspot.com/-Kb2T-OnCw5s/UIFC8Esc1JI/AAAAAAAABfo/m6BqJ-OYtaI/s1600/dancing_baby_b1.gif[/IMG]

---

### Post by LinuxAlexs on 2013-11-23
[dupe'd]

---

### Post by ameyvprabhu on 2013-11-23
I have the same problem, now started on reading things to fix it myself.
2 x 1 TB HDDs - A RAID 0 array and a RAID 1 array

---

### Post by LinuxAlexs on 2013-11-23
Yeah I think there's some hating of FakeRaid going in or something...

Anyway I took the plonge - was extremely risky. I installed on the first partition listed of dupe listing. Note the partition must be marked something like /dev/**mapper** and have the word ARRAY contained in it.

The risk paid off and everything works. It's interesting if you run Ubuntu of the CD (without hard drive) grub detects the partitions just fine (which lead me to take the risk thinking the install routine cannot cope).
Conclusion - There's clearly an issue with the install software.... Select the first partition of the two and everything should sort itself out. I did nothing else special. And backup in case I'm wrong (yes it was russian roulette and no doubt it wil be the same for the next user).

Good luck ! :)

p.s.

It took me 4 years to install Ubuntu is this a record?

---

### Post by oldfred on 2013-11-26
RAID (and LVM) have not been supported in the desktop installer. Thru 12.04 you had to use the server install or for desktops they had a alternative installer that had the extra RAID drivers.
After 12.04 they have done away with the alternative installer and will add the drivers and install capability into the desktop installer. But they did not make it into 12.10, nor 13.04. I believe 13.10 has LVM and LVM with encryption.

Not many use RAID on desktops, many server installs are.

       [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
> The consolidation of desktop installation media into a single image  means that some installation options that were previously available on  the alternate CD have no direct replacement on the desktop image. 


[LIST]
[*]Users  who were installing using the alternate CD to install with LVM or  full-disk encryption can now use the desktop image for this. 
[*]To  install LTSP, please install using the Ubuntu Server 12.10 image, then  add ltsp after installation.  You can also continue to install with  Ubuntu 12.04 LTS media and upgrade to 12.10 from there. 
[*]There are several options for installing using software RAID.  You can: 
[LIST]
[*][install using the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), distributed from the 'debian-installer' directory on the mirrors; 

[*]install using the desktop CD and migrate the disks to RAID post-install; 
[*]install with the [Ubuntu 12.04 LTS alternate CD]("http://releases.ubuntu.com/12.04/") and upgrade. 

[/LIST]
[/LIST]


---

