---
title: "Ubuntu 10.4-64bit Install SATA RAID not supported"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by mutineer612 on 2010-04-30
I had problems with the 10.4 live CD, hanging at a purple screen during boot.  I remember having problems with previous installs 8.04 and 9.04 where I needed the Alternate CD.  

In my situation using and HP ML-310 G4 64bit Intel Pentium-D, I have a SATA RAID controller with 2 80GB drives.  I had to disable the SATA raid in the BIOS, and at the install menu hit F6 and select 'acpi=off'.  During the install at the 'Detect Disks' step when prompted to 'Activate Serial ATA RAID devices' I had to select 'No'.    

This would allow me to setup and partition the drives without raid.  Unfortunately for me Ubuntu does not appear to have plans to support SATA RAID aka 'Fake' RAID.  

Other than this issue at install everything else is working as expected.  Hopefully this helps others avoid the frustration.

---

### Post by MerfMerf on 2010-05-02
I just tried getting 10.4 (64bit) installed on dual velociraptors in raid-0 and failed miserably. This might just be the cause.

I could find the array (as well as the raided storage array) and was able to format a swap partition without any problems. However formating ext4 partitions failed with the very uninformative message "Failed to create ext4 filesystem on [Disk identifiers]" or something similar. Also tried using ext3 instead just in case, but got the same message (Right at the beginning of installation. About 15% in or so).

Anyone (or mutineer612 in particular) able to confirm an actual lack of support for this is a likely cause of my troubles? I'm thinking the massage was very vague so am thinking (hoping) there may be some other reason for my troubles then actual lack of support.

Also, if it is in fact a lack of support for SATA RAID on the 64bit version, I have to ask; is it the same for the 32bit version or would using that be a plausible workaround allowing me to get Ubuntu onto the above mentioned RAID-0 array?

/MerfMerf - And yes, it was intended as a dualboot setup.

---

### Post by fuzzybannana on 2010-05-04
Did you make a new partition or just formated? For me the problem was partition (same error). Work around I found do make partition using parted rebooting, and just formating during installation.

Plz let me know if this help.

---

### Post by Deihmos on 2010-05-04
> **MerfMerf said:**
> I just tried getting 10.4 (64bit) installed on dual velociraptors in raid-0 and failed miserably. This might just be the cause.
 
I could find the array (as well as the raided storage array) and was able to format a swap partition without any problems. However formating ext4 partitions failed with the very uninformative message "Failed to create ext4 filesystem on [Disk identifiers]" or something similar. Also tried using ext3 instead just in case, but got the same message (Right at the beginning of installation. About 15% in or so).
 
Anyone (or mutineer612 in particular) able to confirm an actual lack of support for this is a likely cause of my troubles? I'm thinking the massage was very vague so am thinking (hoping) there may be some other reason for my troubles then actual lack of support.
 
Also, if it is in fact a lack of support for SATA RAID on the 64bit version, I have to ask; is it the same for the 32bit version or would using that be a plausible workaround allowing me to get Ubuntu onto the above mentioned RAID-0 array?
 
/MerfMerf - And yes, it was intended as a dualboot setup.
 
Exact same experience. Itr worked fine with 9.10 but 10.04 killed it and thiat was suppose to be the final build. Really disappointed that such bugs make it to a final product.

---

### Post by Aviator_100 on 2010-05-05
Yes I have same problem. Sil3112 SATA RAID bios

---

### Post by dino99 on 2010-05-05
thats why devs need to know bugs before the final release. If nobody report bugs in alpha/beta/rc development, they cant test every config on earth  ;)

---

### Post by teeedubb on 2010-05-05
Im having the same issue as merfmerf. Nforce 430 sata fakeraid with ubutu 10.04 x64. 
If noone has posted a bug report by tomorrow ill post one, this isnt an isolated issue. Ive had a few drinks tonight and I thinks itll be best if I do it sober.

---

### Post by dino99 on 2010-05-05
[http://www.google.com/search?client=ubuntu&channel=fs&q=fakeraid%2Blucid&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=fakeraid%2Blucid&ie=utf-8&oe=utf-8)

search "raid" into synaptic may help

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)

---

### Post by teeedubb on 2010-05-05
> **dino99 said:**
> [http://www.google.com/search?client=ubuntu&channel=fs&q=fakeraid%2Blucid&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=fakeraid%2Blucid&ie=utf-8&oe=utf-8)

search "raid" into synaptic may help

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)

The first two links dont shed any light on the issue at hand. The third makes it seem more likely that this is a bug.

---

### Post by Deihmos on 2010-05-05
> **dino99 said:**
> thats why devs need to know bugs before the final release. If nobody report bugs in alpha/beta/rc development, they cant test every config on earth ;)
 
This bug was reported a long time ago during the beta right through to the RC. It was never fixed.
 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050?comments=all](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050?comments=all)

---

### Post by nix.peter on 2010-05-05
This frustrates me very bad. I know the devs work very hard and know way more than i'll ever know about making an operating system, however how can this problem still exist?

In 9.10 there are no issues at all during installation with various raid setups, yet in the new almighty 10.04, i cant even get the install started, and one time that i did, grub was so corrupt i just gave up.

I'm not bashing Ubuntu, i really like Ubuntu a lot but this issue needs to be fixed!

---

### Post by ronparent on 2010-05-05
HANG ONTO YOUR HATS, GUYS - I made an install of 10.04 to a raid0!!!

There were and still are complications, but I can and do run a dual boot with Win7. I had almost given up after trying the Alpha2 thru RC without a solution in sight. My main problem was mostly fixed with the update to the 2.6.32.21 kernal which allowed my signature machine to boot without the nodmraid parameter  (I couldn't figger how to install to a fakeraid if I had to use that parameter to boot).

Now the cautions. If you need to create partitions that will result in more than four total primary partiotions on the raid0 drive you will get the error referenced in the 1st post. Best use a prior version, maybe 9.04 or before, to create and extended partition to install to. Note that gparted in 10.04 doesn't see the raid even when /dev/mapper is populated. For some reason the partitioner run from ubiquity does see the raid drive so the installer will run properly.

Secondly, the grub install will have a fatal failure if set for bootloader on the default raid drive. I was able to fix by using another grub on another install to boot the raid0 install and setup the grub to write a MBR on a non raid drive (which I set in bios as the boot drive).

There are a bunch of other factors which I am still trying to untangle enough to write a coherent bug report. Don't expect to be able to use gparted to do anything with the raid0 (or the new Disk Utilty for that matter)! Neither will see the raid - only unallocated drives. 

I guess the bottom line is that if you are lucky you can install and operate 10.04 in a raid system. There are still bugs, pitfalls and pratfalls involved however. I've subscribed to this thread and will jump in if I can help. Good luck.

---

### Post by teeedubb on 2010-05-06
This [post]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050/comments/57") on details of a workaround that worked for me. Im posting this from my ubuntu x64 installed on a nvraid raid 0 array.

---

### Post by ronparent on 2010-05-06
teeedubb: Your fix is one of a variety of fixes that may be needed for specific circumstances. In my case I did not need to resort to renaming the sysbolic links. As a matter of fact the drives had been previously used on an nvidia controller and I had anticipated that they would need to be assigneed new symbolic names when installed on my current unit. They weren't! Instead the old meta data was still recognized by the new controller? Everything worked right anyway - don't ask me why. If anything this highlights the inconsistent ways dmraid may cope with differnt fakeraid implementations. 

If anything, incidently, I resent the 'fakeraid' designation which seems to relegate it to second class acceptance if any within the linux community. I consider it a perfectly valid approach which has always worked perfectly for me in all of my windows installations.

---

### Post by nix.peter on 2010-05-06
I'm certainly not going to give up, just at this moment in my life I cant quite mess around for hours trying to get this to work.

Thanks for all the information guys, maybe we can get somewhere.

And I too agree the so called fake raid seems to work great for me in both windows and Linux, and I don't quite want to just give that up to install.

My biggest problem is that in 9.10 it installs on any raid setup PERFECT. In 10.04 its HELL. I just don't get how it can work great in a previous version and not in the next version?

I still love Ubuntu though.

---

### Post by teeedubb on 2010-05-06
> **nix.peter said:**
>  and one time that i did, grub was so corrupt i just gave up.


Something like this happened to me too, and its happened on a few installations. It seems as grub was being installed to the usb drive I installed from. Booting the pc with the usb drive inserted would bring up the desktp install where I would reconfigure grb and evrything works now

---

### Post by MasterShihoChief on 2010-05-06
i am having the exact same problem as u guys with my alienware laptop. I have jmicron jmb36x biosraid but i get that unhelpful cannot setup partition 15% into installation as well. I posted for help on the beginner forum but got no answer there, so i will subscribe to this thread in hopes, someone finds a solution

---

### Post by evilive on 2010-05-17
> **MasterShihoChief said:**
> i am having the exact same problem as u guys with my alienware laptop. I have jmicron jmb36x biosraid but i get that unhelpful cannot setup partition 15% into installation as well. I posted for help on the beginner forum but got no answer there, so i will subscribe to this thread in hopes, someone finds a solution

I too had the same issue installing on my alienware m17.  I did get it to work by using a Karmic live cd and setting up the partitions there first, then installing Lucid after to those partitions.  Hope this helps.

---

### Post by green_earth on 2010-05-17
Well, throw me in the mix too. Another impediment to fully utilizing Ubuntu x64 on my main system aside Win7 x64. I have Ubuntu 10.04 on an older laptop working great, but would like to spend some quality time with Ubuntu, but am not going to give up the peppy performance of my raid array on my nVidia based Gigabyte motherboard. I'll monitor this post, and hope something comes up. An old  version of Knoppix views every raid array I've ever tried it on, by the way, when I've troubleshot computers for friends... what's up with this issue and Ubuntu?

---

### Post by ronparent on 2010-05-20
green_earth: I have sympathy for your problem. The only reasons I've installed 10.04 on my raid0 array are that my win7 is installed on a separate ssd and my mbr is on a separate SATA. I otherwise would personally have found it too risky to install to the raid0 if it were the only drive on my system. Your caution is well justified. A 10.04 install on a raid0 is too quirky. A mis step could wipe out the raid partition tables.

That said I am very pleased with my 10.04 install to the raid0. It is fast and sofar has worked flawlessly. And, although the raid partitions were not recognized by the 10.04 gparted, in my case they were recognized by the ubiquity partitioner! I as very surprised and pleased that it installed easily on a raid0 ext3 partition - up to a point. At the end the grub2 install had a fatal failure and couldn't write the mbr. This is the most serious quirk I encountered. I was able to fix using the live cd to write the mbr to a separate SATA drive. My sytem boots normally to either win7 or lucid. I wouldn't have done it if I hadn't had the spare raid0 set to install to.

Bottom line is that I would not recommend trying to install lucid to a raid0 set unless you have an extra disk pair to experiment with. The problem may not be within dmraid so much as how its implementation within Ubuntu is inconsistent. Until it becomes consistent and compatible with all the basic system tools it is not really usable (ie nautilus now finally recognizes and makes raid0 drives mountable, however, gparted does not recognize raid0 partitions - the reverse of all prior Ubuntu releases).

---

### Post by syngiun on 2010-05-20
Same issue here. I have two systems with intel ICHxR chipsets. 

1. Asus Maximus Formula (X38 ICH9R) with 2x320GB RAID0 currently under win 7. 

2. Asus P5Q-E (P45 ICH10R) with 4x500GB RAID0 previously functional under win 7.

Ubuntu 10.04 and nearly every other mainstream distro (except fedora 13 beta) has failed in properly installing to the raid setups. 

Ubuntu install can't create ext4 on the array. I tried every combination including turning off the raid BIOS and letting the installer setup a softRAID. Still not able to create ext4 on the array.

Maybe I'll try the 9.x > 10.04 upgrade route. Does anyone know if the 10.04 upgrade will break the raid array?

I have extremely fast throughput under win 7, especially with the 4x500 array. I have had benchmarks well past 350 MB/s. That's faster than the best SSD's on the commercial user market. I'd like to completely ditch windows, but until Linux easily supports boot from raid0 functionality, I refuse to give up on having incredibly fast data access for the sake of telling M$ to go to hell.

If any devs read this, first I thank you for your previous work, and second, I hope easy fake raid suppport happens as soon as possible.

---

### Post by ronparent on 2010-05-20
How many primary partitions do you have on the raid) setup you are trying to install Ubuntu to?

---

### Post by syngiun on 2010-05-22
I started by deleting an re-creating the array in sata raid bios. I tried letting the installer take the entire disk automatically and various manual partition schemes. The installer wouldn't even create a manually designated single ext4 as the only partition.

---

### Post by ronparent on 2010-05-22
Try installing to a raid partition pre-created with a prior distribution (or a prior distro live cd). I had same lack of success with trying to install to ext4 on a raid drive with 4 primary partitions already on it. After placing pre-formatted ext3 partitions in an extended partiton I was able to install normally.

---

