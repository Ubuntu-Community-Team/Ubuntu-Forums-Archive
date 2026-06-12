---
title: "Ubuntu 12.04 won't see raid 0"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by offerlam on 2013-02-22
Hi all,

Server: HP310e Gen8
disks: 4 3TB disk in raid 0 (I know the risks!!)
OS: Ubuntu server 12.04.2

When i set up the disk in a raid 0 my ubuntu installation still see each 3TB disk seperatly..??

In other words in does not see the logical raid 0

what do i do? I thought the 310e Gen8 was certified??

/Casper

---

### Post by albandy on 2013-02-22
> **offerlam said:**
> Hi all,

Server: HP310e Gen8
disks: 4 3TB disk in raid 0 (I know the risks!!)
OS: Ubuntu server 12.04.2

When i set up the disk in a raid 0 my ubuntu installation still see each 3TB disk seperatly..??

In other words in does not see the logical raid 0

what do i do? I thought the 310e Gen8 was certified??

/Casper

Probably your raid device is a fake raid device. For example, My HPZ600 Workstation has a fake raid device:

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode]

and disk are detected separately 
So there is no difference between doing a software raid or a fake raid.

But for example, my HP380-DL G7 has a real raid device:
05:00.0 RAID bus controller: Hewlett-Packard Company Smart Array G6 controllers

And is detected as raid.

---

### Post by darkod on 2013-02-22
If you are not using a dedicated card, +1 for using mdadm SW raid. Much better than any fakeraid unless you plan to dual boot (can't see much point dual booting a server).

But even if it's only a fakeraid it should detect it and ask you to activate it during installation. If you did the installation first and the raid later, you might need to activate it running from the server OS booted up:
sudo dmraid -ay

---

### Post by offerlam on 2013-02-22
Hey Guys,

I came to the same conclusion and im currently explorering the software raid option.. 

I will post back how it goes..

If any can supply a guide for Ubuntu server 12.04.2 it would very much appreciated since the one i could find was for version 9 dot something..

Thanks!

Casper

---

### Post by darkod on 2013-02-22
You need to suppy some info.

1. Are you installing the desktop OS but plan to run the machine as server, or the server OS?
The server cd has mdadm included, the live desktop cd. The install with mdadm raid will be different depending what you are installing.

2. You are looking for a guide for creating mdadm arrays or general ubuntu server guide?

I don't have any recent mdadm guides since using the server cd is very intuitive, and doing it on the command line with the live cd is very easy too.

The 12.04 LTS server documentation is here:[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

It mght include mdadm instructions in the Installation section, etc.

---

### Post by offerlam on 2013-03-05
Hey guys

After many attempts to get software raid up and going (im not linux expert) we have chosen to go ahead a buy a dedicated controller card instead .. this should work? as fare as i know I get this problem because im using the HP 310e gen8 onboard controller

Thanks for  all your help!!

Casper

---

### Post by darkod on 2013-03-05
The onboard controller should allow you not to use raid, only to pass the disks. Same like the desktop motherboards that have raid option but you don't have to use it if you don't want to.

Are you sure you were trying to set up the mdadm raid correctly? Where did it fail?

---

### Post by offerlam on 2013-03-06
Darkod i think you misunderstand my post.. :)

I ment that the onboard HP raid controller og the HP server. I'm not talking about the Linux software raid.

What started all this was that i made the raid through the HP onboard disc controller but that wasn't reconized by the Ubuntu installation.. so i had to turn to software raid.. i can't get it to work.. or my boss my won't give me the time to get it to work since its much cheaper to just but a dedicated controller card to use for hardware raid.. which allso performs better than software raid..

Casper

---

### Post by darkod on 2013-03-06
That's exactly what I meant. mdadm is very easy to make it work. Where did it fail?

A dedicated raid card might seem like the easy way out, but apart from additional cost you are also tying yourself up to a particular hardware card. For example, if it dies, you need to use the same model to get your array working and even then it might fail.

With SW raid you can read it on any linux machine, not only ubuntu.

But at the end of the day, the choice is all yours (or your boss's). :)

---

### Post by offerlam on 2013-03-08
It fails in the sense that i don't know what i'm doing... can you give me clear good guide to setup a raid 5 using software raid and 4 disc in a single patition which i then can install ubuntu server on... 

I have created raids and all that but im sure how to partition them. Actually i was expecting that you had to make your raid and then install ubuntu on it and that was it.. 

I know the subject says raid 0 but that was with the HP controller which can't provide raid 5 - with the software raid i can..

---

### Post by offerlam on 2013-03-08
allso in regards to buying a dedicated controller for raid... do i have to get one that is certified for ubuntu? i don't think so since the raid controlle creates the raid at a lower layer then the one the ubuntu system is running on and so ubuntu will just be presentet with the raid as one disc...

---

### Post by darkod on 2013-03-08
> **offerlam said:**
> It fails in the sense that i don't know what i'm doing... can you give me clear good guide to setup a raid 5 using software raid and 4 disc in a single patition which i then can install ubuntu server on... 

I have created raids and all that but im sure how to partition them. Actually i was expecting that you had to make your raid and then install ubuntu on it and that was it.. 

I know the subject says raid 0 but that was with the HP controller which can't provide raid 5 - with the software raid i can..

Give me a few hours max, and I will post something to help you get going.

---

### Post by darkod on 2013-03-08
OK, lets start. First of all, this is only a discussion and you can ask further questions if you don't understand something.

One of the main things you need to consider is that SW raid doesn't work like HW raid or fakeraid. With HW raid and fakeraid you create one or more raid arrays and then partition them further. With SW raid the arrays are assembled from partitions by the OS itself, so you need to have physical partitions for every partition you plan to have, it has to be separate arrayd device (md device). That might require a more detailed advanced planning on your side.

Another interesting option to use is LVM, Logical Volume Manager. It allows to have one or more physical devices as a base for the Volume Group and the Logical Volumes you create. The LVs are like partitions and you can expand and shrink them dynamically without formatting. Expanding is completely online, while you have to do shrinking offline but you still don't format the LV (and don't lose any data). It has to be offline to shrink the filesystem, only because of that.

I don't know how you feel about LVM but many people use it on servers especially if you want to split the system on many partitions and can't decide the size of each one at the time of installation. You can create them smaller and grow them online later as you need.

If you want to go with plain simple mdadm and one big / partition with everything on it, I would recommend at least having a small 1GiB /boot partition to make sure it's on the beginning of the disks. Also, I'm not sure /boot can be on raid5, so it's best to have a small raid1 device for it.

This simple setup would be:
1. For 3TB disks you have to use gpt table because msdos supports up to 2.2TB.
2. On gpt disks you need a small bios_grub partition so that grub2 can install correctly.
3. All partitions (mount points) need a separate physical partition on the disks.

I would start with the ubuntu desktop live cd and prepare the partition from live mode in advance. It has GUI tools but I prefer using parted in terminal because it gives you option to work with the unit you want.

Lets assume your four disks will be /dev/sda, /dev/sdb, /dev/sdc and /dev/sdd. For all of them, using terminal and parted, prepare the partitions first:
```
sudo parted /dev/sda
mklabel gpt #(new gpt table)
unit MiB #(change unit to MiB)
print #(to check the total MiB size of the disk, look below for the calculation)
mkpart GRUB 1 2
set 1 bios_grub on
mkpart BOOT 2 1026
set 2 raid on
mkpart ROOT 1026 X
set 3 raid on
mkpart SWAP X X+2048
```

When you are creating the ROOT and SWAP partitions, the X value you will need to calculate in advance depending on the total MiB size of the disk. It's best to leave approx 20MiB at the end, just in case some of the disks are not identical in MiBs. So, the X value would be approx (total MiB of /dev/sda)-2068.

I used 2068MiB to leave 2048MiB (2GiB) for swap at the end of each disk and approx 20MiB unused.

Note that you calculate X only for sda. On the other three disks you use exactly the same partition start/end points in mkpart, you don't calculate it any more. This is so that the partitions are identical on the disks, the start/end points match.

After you do the above on all four disks, you have the partitions ready. Boot the machine with the server CD and when you reach the partitioning step select Manual. When the list with partitions opens it will already show the created partitions. You can go directly to the Configure Software RAID option at top, and create the md devices.

The first device will be md0, level raid1, number of devices 4. from the menu that shows, select sda2, sdb2, sdc2 and sdd2. In text menus you select with Space bar, not Enter. After you have the four partitions selected as members, select OK.
Then make the second device, md1, level raid5, number of devices 4, members sda3, sdb3, sdc3 and sdd3. That's it, exit the SW raid configuration.

Now in the partitions list you will see your new raid devices (usually on top). Select the md0 1GiB device you made for /boot, in the Use As select ext4, mount point /boot, finish.
Then select the md1 device, again Use As ext4, mount point / and finish.
Select one by one sda4, sdb4, sdc4 and sdd4 and set them Use As to swap area. That will use all four partitions as swap, no need to raid them.

That's it.
Important NOTE: Do not select or format the first partition on any of the disks. The partition needs to be RAW, without any filesystem, that's how grub2 uses it.

When the end of the install is reached you should see a message that grub-install will install grub2 to all disks. That is usually done automatically so that the server can boot regardless which disk fails. If you have grub2 on only one disk, it can't boot if that disk fails even though raid5 can work with single disk failed.

That should get you going. If you want to implement LVM, the above doesn't apply, you need slightly different partitioning of the disks and different options during the install.

This is just a guidance, you can decide to have small / partition too, and then have large /home and /var partitions which would mean more physical partition (remember, each for every md device that you want to be separate mount point).

When reading all this it might look complicated, but when you have the process on a monitor in front of you it's actually rather intuitive. The main thing is to plan the md devices (separate mount points) in advance, and whether or not you will use LVM because it changes things.

Any questions, fire off... :)

---

### Post by offerlam on 2013-03-08
Hey Darkod,

Great stuff!!! you seem to know your stuff... and i can really use this. I may have errored when i didn't boot the live cd and create the partition first... 

when comparing soft ware raid and hardware raid do you know the pro and cons?

/Casper

---

### Post by darkod on 2013-03-08
Compared to fakeraid built into BIOS/board, the pros are all on mdadm side because fakeraid is also type of SW raid and it ties you up to the board model. If it does, you can hardly recover your data.

A proper HW card has some advantage because it has its own CPU and memory, so I expect it to be little faster in the calculations of parity. But on the other hand it ties you up to a specific HW model too. Not sure if data is recoverable even if you again buy the same card. Or how long the process will take.

With mdadm, you can literary move the disks to another machine in 5mins, and you have the raid up and running. This is because the OS assembles the raid, not any HW component. Also, it's very flexible and you can easily change raid5 to raid6 in the future for example, without any data loss. The reshape of the array will take time, but you don't need to move the data, destroy the raid5, make new raid6, and move the data back. That would take even longer.

---

### Post by offerlam on 2013-03-08
> **darkod said:**
> Compared to fakeraid built into BIOS/board, the pros are all on mdadm side because fakeraid is also type of SW raid and it ties you up to the board model. If it does, you can hardly recover your data.

A proper HW card has some advantage because it has its own CPU and memory, so I expect it to be little faster in the calculations of parity. But on the other hand it ties you up to a specific HW model too. Not sure if data is recoverable even if you again buy the same card. Or how long the process will take.

With mdadm, you can literary move the disks to another machine in 5mins, and you have the raid up and running. This is because the OS assembles the raid, not any HW component. Also, it's very flexible and you can easily change raid5 to raid6 in the future for example, without any data loss. The reshape of the array will take time, but you don't need to move the data, destroy the raid5, make new raid6, and move the data back. That would take even longer.

Valid points... 

what are your thoughts on LVM vs Software raid?

The LVM thing sounded intrestining and i suppose a LVM volume is just as safe as a raid 1 5 6 10 or what ever as long as its not raid 0

---

### Post by darkod on 2013-03-08
Actually LVM is not a replacement for raid. On a server, you would usually create one big raid device and use it as physical device for LVM. In that case, you don't create physical partitions for each mount point, you have one large raid device.

So, in the above example when you select the md1 large device, in the Use As you don't select ext4. Instead you select Physical Device for LVM.

Then in the partitioning list at the top you will see the option Configure LVM (where Configure SW raid is), and you create one Volume Group and minimum one Logical Volume. If you want more separate mount points you create LV for each. When you are finished with that, back in the partitions list will be the new LV devices. You then select them one by one and set their Use As to ext4 and the needed mount points.

Imagine it as mdadm assembling the big raid5 array from your four big partition, but not to use it "directly". Instead that md1 device serves as foundation for the VG (LVM), and the LVs are what you use directly with mount points.

---

### Post by offerlam on 2013-03-08
ok.. i think i will try it with the lvm thing...

another thing... when i make my raid 5 and choose 4 disk 0 disk for hot standby it still only gives me 9TB when i make the raid... since i have 3TB on each disk so in my world it should have been 12TB?

---

### Post by darkod on 2013-03-08
No, in raid5 one disk is used for parity data. That's why it can keep working if one disk fails. The total usable space of N disks in raid5 is N-1. 9TB is correct.

---

### Post by offerlam on 2013-03-10
> **darkod said:**
> No, in raid5 one disk is used for parity data. That's why it can keep working if one disk fails. The total usable space of N disks in raid5 is N-1. 9TB is correct.

I know its N-1 but i could just swear that i have set up a raid 5 with more disc on a  SAN before... but i guess i must remember wrong then...

I will give this another go sometimes next week when im at work and have the time.. thanks so fare..

---

### Post by MAFoElffen on 2013-03-10
> **darkod said:**
> That's exactly what I meant. mdadm is very easy to make it work. Where did it fail?

A dedicated raid card might seem like the easy way out, but apart from additional cost you are also tying yourself up to a particular hardware card. For example, if it dies, you need to use the same model to get your array working and even then it might fail.

With SW raid you can read it on any linux machine, not only ubuntu.

But at the end of the day, the choice is all yours (or your boss's). :)
+1 with darko

Some hard-RAID cards are a pain. Some make things transparent and easy. I have an IBM XSeries server... If I have a problem with Hard-RAID, I have to boot off the CD to run the config utilities for it. The on-controller BIOS util is just a status, see what's going on affair. PITA.

In the server world, I think LVM is handy if I keep it on hardware RAID, have a DOM0 host to DOMU virtual hosts that I am leasing out. (And they change in size requirements or go away.) The only handy part about it is that you can extend and shrink a logical volume, adjust the size of the file system, add disks to it or take away, delete volumes, etc... very flexible, changes quickly and on the fly.... But also a bit touchy, finicky and not for the light hearted. They don't do recovery very well. Yes, you can take a snapshot and the backup LV will track every change from that snapshot... Myself- I use LVM for tests(Within a physical volume on RAID), but I don't trust it's hardiness for production. The physical volume or logical group goes down and you're screwed. MDADM is better for that and IMO more flexible.

So the big difference in admin speed is it takes under a minute to double the size of a Logical volume, where it seems to take forever to grow a RAID array or for it to rebuild. But that is just it, it can rebuild dependably...

You said you had onboard. Was your onboard- HP Smart Array P420/1GB FBWC Controller (RAID 0/1/1+0/5/5+0)? If so, that is hard RAID... That was an option card for that server. The other 3 where Dynamic Smart Array controllers with RAID... but I'm not familiar with those. I do know that they only did RAID)0 and RAID1- unless you bought a 512MB cache upgrade to do RAID5 on them. Other than that, I don't think that server board bios itself had a 'fake-raid" in it's bios... But I don't have that particular "Generation"... Out of the 10 test servers here at home, one of mine is a HP Proliant DL380 G3... So it's a bit older. 

Does your Controller card BIOS have in-BIOS configuration? I'm wondering if it has the drivers to see the logical drive in your card... as I see hardware drivers and software utilities for Suse and RedHat... And I don't know how lspci ID's that card... to check if there is a kernel driver for it...

On hard-raid, pass-through drives in setup are called "JBOD", which stands for "Just a Bunch Of Disks". 

I do RAID. Mostly RAID 5 or 5EE.

---

### Post by MAFoElffen on 2013-03-10
I guess I should translate my last post and explain... Ubuntu is pretty good at finding common hardware RAID devices without a user having to load additional external drivers during the install. (Usually) Most of the time this goes along as transparent during the install. A lot of "common" controllers are opensource and so available... Sometimes not and then you have to pop out to a shell to install a driver for the system to "see" it.

Easy is not true for others Distro's. Example- Loading Solaris or Oracle Linux (Both RHEL) on my same boxes and I always have to load drivers for the system to see those Hardware RAID drives... unless I pass them "through" as not RAID (JBOD) for the system to see without those specific drivers. Just something to think on.  You still have to set them up as that. In RAID, for RAID type, instead of RAID0 or RAID1 (etc), usually JBOD is there as a RAID type. 

Example, today setting up an IBM XSeries server. In Solaris, I start and it says it has no drives. I load their Live Image, it says the ServeRAID driver is missing, then asks for a repo or drive path for the driver for it to install. What I used in that was that it gave me the driver package "name" of what it needed for that device. That way I could make sure I have that driver package for my install. Of course in a text install, you have to pop to a shell to do that manually. I usually have drivers for a specific box copied on to a USB thumb-drive and keep that for each server. Oracle Linux Server r6, same way. Have to load the specific RAID Card driver for the system to see the RAID logical drive. Same box, Ubuntu see's that logical drive fine in the Partitioner... but it did "find" a driver for it when it did the hardware probes... 

Like I did, a way to work things out on a system is too use that Distro's LiveCD image (Your case Ubuntu) to use for diagnostics and to be able to work out the details of what you need and how to make it work. Get the driver working in the LiveCD image. Then have it locally available to use for the install.

Like darko said... Unless you 'really" need that for production / real world commercial support, mdadm is a lot easier to setup.

---

### Post by offerlam on 2013-03-11
Hi Darko and MaFoElffen,

Thanks for you input MaFoElffen!! 

but :(

My boss is persistant in wanting to use a controler despite me pointing at the screen on your inputs and singing the song of easy recovery if we have a failure and all that jazz ...

So taking what MaFoElffen says i would need to find a controller that supports raid 5 and which Ubuntu server 12.04.02 has drivers for. Can you recommend any? Been looking at the compatibility list and search the forums but couldn't find any list for Raid controllers?

---

### Post by darkod on 2013-03-11
Something like this?
[http://www.ubuntu.com/certification/catalog/category/RAID/](http://www.ubuntu.com/certification/catalog/category/RAID/)

But that list is very short, I'm sure it works on many more components. Since the boss insists, you can consider one of the LSI models.

---

### Post by MAFoElffen on 2013-03-11
You know there is utilities and tutorials on converting rhel packages to .deb (debian) right? So you can convert the drivers for what you have to a debian package or compile them from source. But if your card doesn't have the option module for RAID5... Yes would recommend a better card.

I do mostly Linux and UNIX server support.

My recommends- Adaptec, then LSI...

I love LSI cards! I've always felt that they are the industry standard for RAID cards. They always seem to be the one that set the standards in new technology that everyone else then copies or emulates. Sidenote on that list- 3ware, MegaRaid & LSI are the same entity now.

But for HP Servers, I lean towards the Adaptec Cards. Reason why? "Some" HP servers have something different about their BIOS keyboard interrupts. In the past, I've had some problems (with some boxes) putting LSI cards in HP servers. They come up fine, but then when you go to hit their BIOS hotkey to configure them, the Main system's BIOS intercepts it (for their use) causing some kind of conflict and you can't get into the RAID card's BIOS. You can still get in after it boots via software configuration management... But if you do have a problem like that, it's hard to "disaster manage" that server if it doesn't boot to a OS prompt.

But like I said, that is only with some HP Servers with some LSI cards. There was a LSI firmware microcode update that was supposed to address that. But after burning those update images to card BIOS, I still have some LSI cards that still don't work with some of my HP Servers. So if you try an LSI card on it, make sure you can return it if it ends up having that conflict problem. That conflict doesn't have anything to do with how it functions, just in being able to manage it through the hotkeys. Those same cards of mine are working just fine in other servers. I think the LSI cards have more features, but they have to work with what you have right? LSI cards come with drivers for rhel Linux and source that you can compile for debian... Although they say that, I haven't had one not seen by debian or Ubuntu, so they seem to be covered by the Ubuntu repo's drivers. But... read on...
 
Adaptec has a reputation of being more open to "opensource" with their driver code to Linux and UNIX. And there are so many Adaptec cards out there working on everything... Their Series 6 and Series 7 cards are directly supported with debian and "ubuntu" drivers and software packages from them through Ubuntu 12.04LTS (so far):
[http://www.adaptec.com/en-us/products/](http://www.adaptec.com/en-us/products/)
For a production box I would go with their Series 7 cards, for end-of-life factors... It is what is their current production line. Their older 2 through 5 series cards came with Ubuntu drivers, but they stopped direct "flavored" driver download support from them for those cards at Ubuntu 11.04. I still think those older cards are supported directly by drivers in the Ubuntu Repo's, by AAC.

Whatever you get, 64bit PCIE, battery backed BIOS... able to configure with both the onboard BIOS and the software utils... Alerts through BIOS or software monitored. Able to do RAID5, RAID5EE and maybe even RAID6. As with other system alerts, I have my RAID status alerts (both mdadm and hardware RAID), SMART status and storage capacity alerts emailed to "me" from my systems.

---

### Post by offerlam on 2013-03-12
> **MAFoElffen said:**
> You know there is utilities and tutorials on converting rhel packages to .deb (debian) right? So you can convert the drivers for what you have to a debian package or compile them from source. But if your card doesn't have the option module for RAID5... Yes would recommend a better card.

I do mostly Linux and UNIX server support.

My recommends- Adaptec, then LSI...

I love LSI cards! I've always felt that they are the industry standard for RAID cards. They always seem to be the one that set the standards in new technology that everyone else then copies or emulates. Sidenote on that list- 3ware, MegaRaid & LSI are the same entity now.

But for HP Servers, I lean towards the Adaptec Cards. Reason why? "Some" HP servers have something different about their BIOS keyboard interrupts. In the past, I've had some problems (with some boxes) putting LSI cards in HP servers. They come up fine, but then when you go to hit their BIOS hotkey to configure them, the Main system's BIOS intercepts it (for their use) causing some kind of conflict and you can't get into the RAID card's BIOS. You can still get in after it boots via software configuration management... But if you do have a problem like that, it's hard to "disaster manage" that server if it doesn't boot to a OS prompt.

But like I said, that is only with some HP Servers with some LSI cards. There was a LSI firmware microcode update that was supposed to address that. But after burning those update images to card BIOS, I still have some LSI cards that still don't work with some of my HP Servers. So if you try an LSI card on it, make sure you can return it if it ends up having that conflict problem. That conflict doesn't have anything to do with how it functions, just in being able to manage it through the hotkeys. Those same cards of mine are working just fine in other servers. I think the LSI cards have more features, but they have to work with what you have right? LSI cards come with drivers for rhel Linux and source that you can compile for debian... Although they say that, I haven't had one not seen by debian or Ubuntu, so they seem to be covered by the Ubuntu repo's drivers. But... read on...
 
Adaptec has a reputation of being more open to "opensource" with their driver code to Linux and UNIX. And there are so many Adaptec cards out there working on everything... Their Series 6 and Series 7 cards are directly supported with debian and "ubuntu" drivers and software packages from them through Ubuntu 12.04LTS (so far):
[http://www.adaptec.com/en-us/products/](http://www.adaptec.com/en-us/products/)
For a production box I would go with their Series 7 cards, for end-of-life factors... It is what is their current production line. Their older 2 through 5 series cards came with Ubuntu drivers, but they stopped direct "flavored" driver download support from them for those cards at Ubuntu 11.04. I still think those older cards are supported directly by drivers in the Ubuntu Repo's, by AAC.

Whatever you get, 64bit PCIE, battery backed BIOS... able to configure with both the onboard BIOS and the software utils... Alerts through BIOS or software monitored. Able to do RAID5, RAID5EE and maybe even RAID6. As with other system alerts, I have my RAID status alerts (both mdadm and hardware RAID), SMART status and storage capacity alerts emailed to "me" from my systems.

what would you prefer to use in a server production environment? Hardware Raid Adaptec or Linux (Ubuntu server) Software raid?

---

### Post by offerlam on 2013-03-12
Guys I'm in all secreacy trying to get software raid to work... don't tell anyone :P my boss won't know the difference anyways.. i want this to work.. 

what i have done so fare is that i have bootet into the ubuntu server install, NOT live cd, and made the following during the patitioning fase:

made one partition marked as boot and made bootable 2Gb
made one partition on all the drives 1 through 4 marked for swap 2Gb
Made one raid5 4 disk 0 spare marked as EXT4 with root partition

When i get to the Grup boot loader is stalls and says

An installation step failed. you can try to run the failing item again from the menu or skip it and choose something else. The failing step is: Install the grup boot loader on hard disk

What do i do? im stuck?

---

### Post by darkod on 2013-03-12
If I remember it corectly (reading many threads here), you are using 3TB disks with gpt table which means you also needs a small 1MiB UNFORMATTED partition with the bios_grub flag. Grub2 can't install on gpt disk without it. I guess that's the reason it's failing.

See one of my previous posts for the suggested disk layout/partitions. I think it was in this thread. :)

---

### Post by MAFoElffen on 2013-03-12
> **offerlam said:**
> what would you prefer to use in a server production environment? Hardware Raid Adaptec or Linux (Ubuntu server) Software raid?
I think either is fine. 

These would be my leanings for a production environment. Remember that "darko" has production experience also.

Higher-end RAID cards- Really can't beat them. But if I go that way, I keep two similar cards handly or a fallback server that was clustered. Reason? (PRO) If you have a controller failure, on high-end cards you can swap cards and copy back the RAID config and away you go. If have a drive failure within your logical drive, it will pause for a moment, ask what you want to do, then if not caught, time-out, mark the drive as a fault, continue, while rebuilding your array with a spare (if you set up with a spare...). But sometimes in rare instances the controller is "too smart" about false errors. Fault tolerance is settable. Work to do all that functionality is negligible. Price is a consideration- $500 -$2000 for new. You need drivers to see it. Although for myself, I get used or refurbished which the cost is 50-70% off. 

Most of the test servers I have at home (10 of them) came with hardware RAID. For most of them, they are a no-brainer. Boot into the on-board BIOS, set them up and go, depending on what OS I am running. Funning that my highest end server is the most PITA to set-up, but that is just an IBM thing. Hardware RAID is well supported by MS Sever 20xx. Most are well supported by Linux, but you have to have a compiling experience/skillset to do it.

Software RAID gives you the flexibility and adaptability of going RAID without the cost or the technology. Think that you can go RAID0, 1, 10, 5, 50, 6, 60... without any extra hardware. Cost is free, Experience and skills in setting up is higher. MDADM is available to install on just about any Linux distro. Once setup, that array can go on and be reused on any box of any hardware config, even on a low-end PC with a Pentium or Athlon as a backup.. set MDADM, read the drives and away you go again. Lower-end cards don't have functionality to shrink, add, grow an array or change RAID types for a migration. (Software RAID does without having to add anything).

Concerns. Drives still fail on either. Functionality is already built into a card, but that functionality is static, meaning what is there is all it's going to have, unless the vendor adds modules or adds something into the firmware. You can add functionality to madadm as you go on, via scripting and your imagination... this again depends on experience and building on your skill-set. You don't need any special specific hardware drivers beyond the basic mdadm package.  You can still go this way by setting your smartarray to jbod and no additional cost.

Software mdadm, a lot of things are commandline and manual. That is both good or bad, depending how you look at it. Sometimes you want the control and the chance to mark a drive out as a fault on your own, instead of automatically. Sometimes, you don't want to start degraded... But having things do things automatically are also a blessing if you aren't there physically to get around those things when then happen. The only way to get around those kinds of things when you aren't physically there, or to add functionality on alerts and such, is through scripting.

I know that really didn't answer that "for" you... but it should give you enough to investigate and mold to how "you" do business.

---

### Post by MAFoElffen on 2013-03-12
> **darkod said:**
> If I remember it corectly (reading many threads here), you are using 3TB disks with gpt table which means you also needs a small 1MiB UNFORMATTED partition with the bios_grub flag. Grub2 can't install on gpt disk without it. I guess that's the reason it's failing.

See one of my previous posts for the suggested disk layout/partitions. I think it was in this thread. :)
+1

I even do that for desktops... Translation, I leave 1MB unalloctaed ahead of the first partition. So does "darko."

---

### Post by darkod on 2013-03-12
> **MAFoElffen said:**
> +1

I even do that for desktops... Translation, I leave 1MB unalloctaed ahead of the first partition. So does "darko."

Strictly speaking that's not the same. I also leave 1MiB unused before the first partition, but in this case I am talking about a small 1MiB partition with RAW format (no filesystem) and bios_grub flag. It's needed on gpt disks since grub2 can't fit on the MBR and needs additional small space for its code.

---

### Post by offerlam on 2013-03-16
Guys thank you so much for your input.. 

I didn't know Darko did production as well, it was never mentioned as fare as i remember :) sorry darko :)

I have put some time aside thursday to give this another go and starting to be quit good at avoiding my boss questions :P

---

### Post by offerlam on 2013-03-19
> **darkod said:**
> If I remember it corectly (reading many threads here), you are using 3TB disks with gpt table which means you also needs a small 1MiB UNFORMATTED partition with the bios_grub flag. Grub2 can't install on gpt disk without it. I guess that's the reason it's failing.

See one of my previous posts for the suggested disk layout/partitions. I think it was in this thread. :)

Darko... HELP!! :) Or anyone else for that matter :)

I know i'm not going about this excatly the way you suggestet. As fare as i know you wanted me to load the live cd and run the MD commands. Being stubbon and really wanting to learn this i really want to do this through the Ubuntu installer.. hope thats ok?

so gathering from you suggestion i suppose from the view in the ubuntu installer you are talking about the "Use as: Reserved BIOS boot area"?

When i made this partition on SDA with 1 MB space and set the "Use As:" to "Reserved BIOS boot area" i got a new error from grup saying it couldn't load on the SDB.. 

So i thought i just had to make the same patition on SDB but then i got the old error.. can you provide me with any more info?

Help me Obi Wan Kenobi, you are my only hope :)

---

### Post by darkod on 2013-03-19
What old error are you talking about? Does it allow you to make the Reserved BIOS boot area partition on sdb too? If it does, all should be fine during grub2 install.

This is why I prefer parted, it's much more precise for partitioning. Make sure sdb has gpt table too, not msdos table.

Also, if by ubuntu installer you mean the desktop live cd don't forget you need to add the mdadm package first so it can install SW raid. Did you install with SW raid or you tried installing on the hdd directly?

---

### Post by offerlam on 2013-03-19
Hi Darko and thanks for the quick response.. 

I have attached (hopefully i did it right) two pictures.

The first picture error.jpg is the error im  talking about which is the same error as i asked about before in this thread.. 

The second picture is called Partition setup.jpg and is a picture from the Ubuntu installation wizard with my partition setup. I was hoping if you could confirm weather or not it is correct or not. In doing so answering your own questions in your previous post :)

/Casper

---

### Post by darkod on 2013-03-19
Oh man, how many times did we say IDENTICAL setup on all disks? :)

You have biosgrub on two disks only. I think by default grub2 will try to get installed on all disks members of the raid since in this case is all disks. Of course it will fail when it tries sdc and sdd since you never did the biosgrub partition. You need it on all disks.

I think this is what's hapenning. I can't be 100% sure since the error message doesn't include info on which disks it failed, but from your partition list it seems clear.

---

### Post by offerlam on 2013-03-19
> **darkod said:**
> Oh man, how many times did we say IDENTICAL setup on all disks? :)

You have biosgrub on two disks only. I think by default grub2 will try to get installed on all disks members of the raid since in this case is all disks. Of course it will fail when it tries sdc and sdd since you never did the biosgrub partition. You need it on all disks.

I think this is what's hapenning. I can't be 100% sure since the error message doesn't include info on which disks it failed, but from your partition list it seems clear.

Hey :)

I have tried biosgrup on all disks aswell.. and that didn't work either.. same error..

Maybe i did something wrong.. Im currently home so i don't have access to the mashine here but i will try that tomorrow if i get the chance.. just to be sure I have tried it.

But i take your answer that besides the two missing biosgrup partition everything looks fine?

/Offerlam

---

### Post by darkod on 2013-03-19
Yeah, it looks good. Now looking at it the second time, I'm not sure you have the bios_grub flag on the biosgrub partitions. Not sure if it's all the way to the right so it can't be seen on the image, or it's not there.

What we can see on the image is the biosgrub label on the partition, together with raid and swap labels on the other partitions. But the label doesn't mean anything. Grub2 looks for the bios_grub flag to know which partition to use. I think you can have a look at the flags on the partition by selecting it with Enter, then besides the Use As and Mount Point options, there should be a Flags option. Select it and make sure you activate the bios_grub flag.

This could be the reason it's still refusing the install grub2, if the bios_grub is missing. It should be in the partitions list next to the partition, all flags are shown if a partition has any.

If you go the parted way I posted earlier, you will easily check if the flag is there or not by printing the layout of a disk. You should be able to do the same in the installer since you insist on using it for partitioning. :) Just make sure you look into the Flags option.

---

### Post by offerlam on 2013-03-20
> **darkod said:**
> Yeah, it looks good. Now looking at it the second time, I'm not sure you have the bios_grub flag on the biosgrub partitions. Not sure if it's all the way to the right so it can't be seen on the image, or it's not there.

What we can see on the image is the biosgrub label on the partition, together with raid and swap labels on the other partitions. But the label doesn't mean anything. Grub2 looks for the bios_grub flag to know which partition to use. I think you can have a look at the flags on the partition by selecting it with Enter, then besides the Use As and Mount Point options, there should be a Flags option. Select it and make sure you activate the bios_grub flag.

This could be the reason it's still refusing the install grub2, if the bios_grub is missing. It should be in the partitions list next to the partition, all flags are shown if a partition has any.

If you go the parted way I posted earlier, you will easily check if the flag is there or not by printing the layout of a disk. You should be able to do the same in the installer since you insist on using it for partitioning. :) Just make sure you look into the Flags option.

I would say i have the flags are set.. 

Now i have tested it with a grup bios partion on every disc in the server. Actually i recreated alle partitions so they all appear in the same order on all the disc..
And it still fails on me.

I have attached 4 pictures

Partition list: is the list of how my partition are set currently. The should make you smile :P

Bios flag: Is the picture that document that i have set the reserved for bios flag besides the run as. I can't set this partition as bootable. I have pushed enter and nothing happens.. 

Swap Flag: just to show you how swap is setup

Error: is to show the error i get.. 

I'm starting to think something else is wrong. I found this blog describing, what i would think, is my problem but handles it another way. I have asked for  help there aswell without any answer yet. Perhaps you could decifer what they want.. 

[http://stinebaugh.info/installing-ubuntu-server-12-04-lts-using-hardware-raid1/](http://stinebaugh.info/installing-ubuntu-server-12-04-lts-using-hardware-raid1/)

He is addressing raid1 but in the comments people are asking about raid5 and the solution should be someone the same as to raid1

---

### Post by offerlam on 2013-03-20
Duh forgot the pics :P

---

### Post by darkod on 2013-03-20
Hmm, do this test. Boot the machine with a desktop live cd, open terminal and post the output of:
```
sudo parted /dev/sda print
```

Lets get that out of the way. :) Don't do any changes in the partitioning, leave it as it is. Just post the output of that command.

---

### Post by offerlam on 2013-03-20
wilco!

brb with information.. need to make a livecd and all that jazz

---

### Post by offerlam on 2013-03-20
> **darkod said:**
> Hmm, do this test. Boot the machine with a desktop live cd, open terminal and post the output of:
```
sudo parted /dev/sda print
```

Lets get that out of the way. :) Don't do any changes in the partitioning, leave it as it is. Just post the output of that command.

OMG!!!! this is starting to give me..MORE.. gray hairs... 

I have tried making a livecd and boot it.. I have used the windows tool aswell.. tryed with both debian livecd which fails both with cd and usb.. tried the livecd guide by ubuntu and used the before mentioned windows usb live cd tool (lili) and both tried with the desktop and server version ... 

the last part gives me the error /casper/vmlinuz: file not found

I'm SO hoping this is related to my grub problem???

---

### Post by darkod on 2013-03-20
Hmm, not sure what is hapenning but I've seen other people mention the vmlinuz error too. Is this the 12.10 or the 12.04 LTS image? Use the LTS, it doesn't really matter but it should be better. Make sure the ISO file is not corrupted during download, I usually use torrent since it checks for corruption during download. And burn the cd at low speed, 8x or 10x max, not the maximum of the cd/burner. If it's an OS install cd, burn it on low speeds to minimize errors which do happen when burning but are ignored unless they are critical.

What did you use to create the usb, unetbootin or universal usb installer? On windows you can try with universal usb installer first, other options are pendrive linux and unetbootin. On win7/win8 make sure you start the program as administrator, not with the double-click. Unless you start it adminsitrator windows might not write the boot sector correctly due to security implemented with win7.

EDIT PS. If all else fails, if I'm not mistaken you can switch to terminal during the server install. Start a new install and when reaching the manual partitioning page, press Ctrl+Alt+F1 for tty1. I think it was that combination of keys. It should open a terminal where you can try running the parted command above. You won't be able to copy/paste the output since you won't be in live mode, but note down if the bios_grub flags are present on partition #1 on all disks or not. Typing exit should close the tty1 and bring you back to the installer screen.

---

### Post by offerlam on 2013-03-20
> **darkod said:**
> Hmm, not sure what is hapenning but I've seen other people mention the vmlinuz error too. Is this the 12.10 or the 12.04 LTS image? Use the LTS, it doesn't really matter but it should be better. Make sure the ISO file is not corrupted during download, I usually use torrent since it checks for corruption during download. And burn the cd at low speed, 8x or 10x max, not the maximum of the cd/burner. If it's an OS install cd, burn it on low speeds to minimize errors which do happen when burning but are ignored unless they are critical.

What did you use to create the usb, unetbootin or universal usb installer? On windows you can try with universal usb installer first, other options are pendrive linux and unetbootin. On win7/win8 make sure you start the program as administrator, not with the double-click. Unless you start it adminsitrator windows might not write the boot sector correctly due to security implemented with win7.

EDIT PS. If all else fails, if I'm not mistaken you can switch to terminal during the server install. Start a new install and when reaching the manual partitioning page, press Ctrl+Alt+F1 for tty1. I think it was that combination of keys. It should open a terminal where you can try running the parted command above. You won't be able to copy/paste the output since you won't be in live mode, but note down if the bios_grub flags are present on partition #1 on all disks or not. Typing exit should close the tty1 and bring you back to the installer screen.

I have chosen to move with you BusyBox idea since im most familier with that.. 

but neither sudo nor parted is a valid command in the Busybox terminal??

EDIT:

I tried the livecd with ubuntu 12.04 LTS and used the usb tool suggest on the ubuntu site. Its called LILI

---

### Post by darkod on 2013-03-20
Try creating a usb with universal usb installer. And make sure you are trying to boot from the usb of course. :)

If that doesn't work, I have no idea. You might have a bad ISO, so the cd and usb both don't work.

---

### Post by MAFoElffen on 2013-03-20
@ offerlam

Sent you a PM...

---

### Post by offerlam on 2013-03-21
@ Darko

Just got one major step forward

I rebooted the server and restarted the installation wizard meaning non of the options I had chosen before was picked. During partion i made the partitions reserved for bios on each disc as we have talked about before and now it worked!!!

It seems like the grup installation part haven't seen the changes i made when it erroed and so a reboot was nessesary.. thats my assumption anyway - don't know if you agree?

One, maybe lesser, problem left.

The installation continues and it spits out the CD and asks you to remove the cd from the drive - your normal installation behaviour..

I reboot expecting to see my ubuntu server to start op but then the boot says it can't find an OS installed and jump to trying PIX boot... :( 

So my installation succeeds but something goes wrong that does my server doesn't boot the os.. 

any suggestions?

---

### Post by darkod on 2013-03-21
Sounds like a limitation of the board that it doesn't want to boot if there is no boot flag on at least one partition. Windows needs the boot flag but linux doesn't use it, so often it's not set during install. But many boards are made with MS in mind (surprise, surprise) and don't boot in that situation.

Try setting a boot flag on some partition, for example sda2 partition and see if it will boot in that case. There is no need to reinstall. But if you can't boot in any live mode, not sure how you will set the boot flag.

---

### Post by MAFoElffen on 2013-03-21
> **darkod said:**
> Sounds like a limitation of the board that it doesn't want to boot if there is no boot flag on at least one partition. Windows needs the boot flag but linux doesn't use it, so often it's not set during install. But many boards are made with MS in mind (surprise, surprise) and don't boot in that situation.

Try setting a boot flag on some partition, for example sda2 partition and see if it will boot in that case. There is no need to reinstall. But if you can't boot in any live mode, not sure how you will set the boot flag.
I'm thinking, whatever is the root partition, mark as bootable.

Darko- I'm going to include you in the PM discussion...

---

### Post by offerlam on 2013-03-22
OK I got it working and i couldn't have done it without you two guys... A BIG HUG ALL AROUND!! ok maybe thats a little too pink :)

Anyways.. THANKS!!

For other posters and desperate people :)

You need to make a "reservered for bios" partition on EVERY disk
You need to make a boot partition - you make that by creating a EXT partition and mount it as boot.
You need to turn off the HP raid controller in the bios by switching to Sata. I went with legacy sata but there is another sata option that might work..

Just one more question.. 

In regards to the required boot partition:

I have 4 disk SD a b c d - currently i have installed the boot partition on SDA. Now if that disk dies (SDA) i have a raid5 and so would survive it but i assume my system would still crash because SDA was the disc with my boot partition - is this correct? and if yes how should i circumvent it? create a boot partition on all discs?

---

### Post by darkod on 2013-03-22
Did you create the partition and used it as /boot or you only created it so you can put the boot flag on it?

If you used it as /boot that was a wrong decision. Yes, if sda dies it will not boot even though raid5 can work without one disk. But ubuntu can't work without /boot.

What you should have done is make the identical partition on all disks and make a raid1 md device from all four partitions (yes, you can make raid1 with four partitions) and use it as /boot. In that case the same files will be on all four disks and it will work without any one of them. But not without two disks since that is raid5 limitation and your / will still be raid5.

---

### Post by MAFoElffen on 2013-03-22
I think I found something in their doc's last night. It said the B120 does not have it's own processor, so uses the system processors for RAID. Doing that, I'm starting to think that controller uses an Intel ICH*x* chipset, which is considered as fakeRAID. Looking at the MS Server 2008 manuals on that server and that controller... If you set the BIOS: SATA mode to AHCI on an HP server with that controller, it's going to ask for an additional driver... In other doc's it said that if set to AHCI, then it sees a ICHx chipset and if not it loads a more generic type controller driver.

It also said somewhere else:
> 
NOTE: When the SAS-enabled riser board with the Smart Array B320i controller is installed in the server, the embedded Smart Array
B120i controller is automatically disabled. In the absence of another storage controller or an expander backplane, front drives operate
in AHCI or Legacy mode. In these two modes, the drives are not part of a hardware RAID or a member of a logical drive. The Locate,
Drive status, and Do not remove LEDs in the drive carrier are disabled.

Since you are not installing another RAID card, you have to turn it off and put it into those modes manually. So, here's something to try to get around that.

his gets into this area:
> 
[FONT=Ubuntu Beta]With some motherboards (rare), using AHCI may be a problem when using Ubuntu. If it works properly with AHCI, keep this mode because it provides enhanced performances, but if it doesn't, switch to IDE mode (normally more compatible). Don't forget that your motherboard has two different SATA controllers, so you have to configure the one handling the SATA port where your hard disk drive is connected. Look at "PCH SATA Control Mode" and/or "GSATA3 Ctrl Mode" options in "Integrated Peripherals" section of your BIOS. Don't hesitate to test AHCI mode if the controller is already set up in IDE mode. If your hard disk drive is connected to the GSATA3 controller from Marvell, you may also try to connect it on a port handled by the Intel PCH controller.[/FONT]


Go into the system system BIOS. Go to where you set the embedded SATA controller options. The note on that is going to say something like "Enable Dynamic Smart Array Controller B120i"... At that option there should be 2 or 3 modes:
This option will be there:
- Enable Dynamic HP Smart Array B120i RAID Support
You do NOT want to select this...

The other option or options will be:
- Enable SATA Legacy Support
This next option may or may not be there:
- Enable SATA AHCI Support (HP Tech says this option was removed for some newer servers... so may not be there)

So it looks like you need first try AHCI enabled, If it doesn't then try SATA legacy.

Going by what the SUSE install docs say for that server, unfortunately, this may affect "how" it is installed and the hdd type drivers Linux installs/loads when it installs. So changing that mode in BIOS may affect how an installed system acts. As I saw "somewhere" in your server's Linux doc's for that controller, that option needed to be set before the Linux install process. (I think that was in the SUSE install doc's, when using mdadm.)

Hope that info helps...

EDIT--- I see you found that on your own while I was writing this....

---

### Post by MAFoElffen on 2013-03-22
Additional to darko... and reading back through...

How many partitions are you using for RAID5? I remember you saying you had 4 3TB disks and you were going 3+1 spare. 

I may be wrong. (Sort of like saying, I'm no doctor, but...) Wouldn't it make more sense to go with smaller partitions (for example 7+1), so that when you it's assembled you end up with more storage and with a smaller spare. That way you aren't losing so much space? 1/4 of your total storage seems a bit for a spare... And would take forever to rebuild, right?

In RAID5 you use about 25% for parity. So with the 3+1 at 3x3TB, you are at around 6.75TB usuable. With 7+1, you end up with  7.85TB usable, with a 100% faster rebuild time. 

Sorry- Just thinking out loud.

On the boot issue, I'm thinking that you did several things at once... And just changing the SATA mode might have enabled the boot to work. So it may boot into a RAID5 with that option set in BIOS now. I have to agree with Darko, whichever way, if set to a boot to/on only one disk, if that disk goes down, it's dead. If still not working to RAID5, then mirror it so you have a backup avenue.

---

### Post by darkod on 2013-03-22
How would you make the 8 partitions? Instead of 4, you make 2 partitions on each disk? Wouldn't that put way too much pressure on the disk since instead of writing "once" it actually writes "twice" on different physical sectors at the same time on each disk.

I wouldn't really do that. I haven't gone into too much investigating, but it looks like the disks will be closer to failure like that.

I don't recall any more if one disk was planned for spare, I thought all 4 will be part of raid5 without spares. Hence the 9TB device shown in few partitioning images before. 3 x 3TB usable + 3TB parity.

---

### Post by MAFoElffen on 2013-03-22
You're right of course on possible performance issues, but not in practice.. My mind wanders today because no sleep last night. (I just finished converting IBM ServeRAID Manager for 12.04lts and newer, packaging it debian and installing it on my IBM Xseries Server... Now works great through shh on current Ubuntu!)

Hard to write in two places on the same disk at one time. If it were HardRAID, that is not possible. On Software RAID it is possible to have multiple partitions on same disk and have one raid array with even just one physical disk. I do it all the time with mdadm in virtual for server dev testing... And:
> **kragen said:**
> Linux software raid is more flexible than hardware raid or true raid because rather than forming a raid arrays between identical disks, the raid arrays are created between identical partitions. As far as I understand, if you are using hardware raid between (for example) two disks, then you can either create a raid 1 array between those disks, or a raid 0 array. Using software raid however, you could create two sets of identical partitions on the disks, and for a raid 0 array between two of those partitions, and a raid 1 array between the other two. If you wanted to you could probably even create a raid array between two partitions on the same disk! (not that you would want to!)

The process of setting up the a raid array is simple:

[LIST=1]
[*]Create two identical partitions
[*]Tell the software what the name of the new raid array is going to be, what partitions we are going to use, and what type of array we are creating (raid 0, raid 1, etc...)
[/LIST]

mdadm manages the caching between the the partitions... But since striping between physical disks is faster... You are right in that it may turn out slower.

---

### Post by darkod on 2013-03-23
Mike, another important thing that I didn't think of last night. You will create a raid5 from 8 partitions instead of 4, right?

But raid5 tolerates only one member failure to keep working and if any physical disk fails you lose two members since you have 2 partitions on each disk that are members of the array. If any disk fails the array will fail which is no raid at all.

Unless you are talking about two separate raid5 arrays of 4 partitions each, but that's a different matter, and in that case you still dedicate 2 partitions to parity (one for each array), not 7+1 in your example above.

The quote in your last post talks about flexibility that you can have 2 partitions on two disks each, and make one raid0 and one raid1 arrays which is more flexible than HW raid. I agree with that, but not with all partitions on the same disk to be membes of the same array. Different arrays, yes. Otherwise it's not much protection against failure.

---

### Post by MAFoElffen on 2013-03-23
LOL! Statistical probability... 

Always remember: "RAID Is Not Backup."

It would scare you, but there is more likelihood of a failure from an URE read /write error on large data stores than a total physical drive failure. The likihood of encountering a URE is once every 11.3TB's. In a 3TB disk, that's 1 in 4 total disk (full) reads. In a running RAID, this is not a problem as it reads, sees the URE, goes to other redundant parts of the RAID, reads good data, goes on as it rewrites to the sector where the URE occurred, that it read from. The probability varies when there is a failure and it has to rebuild, hence the Big Read... Talking about a good read:
[http://www.standalone-sysadmin.com/blog/2012/08/i-come-not-to-praise-raid-5/](http://www.standalone-sysadmin.com/blog/2012/08/i-come-not-to-praise-raid-5/)

I feel safer when I find those bad sectors and can mark them out, than some large storage where I haven't found them "yet."

But since we are talking software RAID, you are not constrained to technology within a hardware bios...You can migrate to RAID50, RAID6 or RAID60 without having to buy another controller. With RAID6 you can have 2 members fail and run...

Even with LVM... I run LVM with virtual guest hosts, you can run LVM with created synced backup pseudo parity. Backup LVM partitions track individual incremental changes from the time/point of creation.

Back-to.... is was concern on large (3TB) members being more likely to have a failure than a total physical disk failure.... But then again, people do it all the time, right?

---

### Post by offerlam on 2013-03-25
Hey Darko

I will make the boot as you mention - Thanks.. 

In regards to the ways i could make the RAIDS...

I really appriciate the info and it is certainly something to think about in the furthur but for now i keep think i will keep my Raid5 design as it is cause i really need to get past this and get on with the IDS projekt :)

But thanks again guys.. you did good allround.. 

Mike check my pm :)

---

### Post by Mauritz_Nordkvist on 2013-10-09
Hi,

To get RAID5 working on internal controller you need to purchase 512 Mb FBWC memory module to it.
But the internal controller is not fast in Windows 2012 or Redhat compared to a software Raid with Ubuntu 13.04 when turning the controller to a SATA AHCI mode and use Software RAID. Software RAID in ubuntu is 20-30 Mb/s faster for read and writing 5-7 Mb/s when using 6 disks as RAID5 in test with Windows 2012, Redhat and Ubuntu.
Only issue is that I have only got the server to boot and working correctöy with Ubuntu kernel 3.8.0.19. All other newer kernels gives kernel panics after a while or won't boot at all.

But now when VMWare has released Hypervisor 5.5 that is working fine now with this platform I will make all installations using Hypervisor 5.5 instead of Ubuntu Server with VMWare Workstation as Hypervisor 5.0 and 5.1 did not work correctly on HP DL/ML 3*0e models that was the reason to start using Ubuntu on this platform..

Just my 5 cents.

KR
/M

---

