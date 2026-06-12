---
title: "Seeking advice for properly installing and configuring Ubuntu in a new PC build"
date: 2016-07-26
forum: Installation &amp; Upgrades
---

### Post by giga+bytes on 2016-07-26
[COLOR=#222222][FONT=Verdana]I just ordered the components for a mini desktop PC build (hooray!), so I would like some help writing a list of details for installing Ubuntu (solely Ubuntu, no windows at all) on it while waiting for the components. This includes configuring the BIOS for Ubuntu, then installing, updating and configuring Ubuntu.

The specs: ASRock AM1H-ITX, Athlon 5350, GSkill Ripjaws X 8GB DDR3-1600 (single stick), Intel 540s SSD. It will be used exclusively for office-type use. I have a gaming PC for everything else.

I bought a Lenovo laptop a couple months ago for the purpose of starting to adjust the family to Ubuntu (from Windows), and because it has an AMD processor I installed Ubuntu 14.04 LTS (not dual-boot, I replaced the factory HDD with a new SSD for a solely Ubuntu system). This new build is also AMD-based, plus I need to have the same version and flavour of Ubuntu as the laptop so I can manage things more efficiently (I am the house techie), so I will be installing the same Ubuntu 14.04 LTS.

*Note*: the laptop is used for general web browsing and Linux gaming, which is why I figured it would probably be best to get the full Ubuntu, but if another flavour would work fine for the purposes of both of these computers, and provide any worthwhile benefits, then I'll consider making the change.

Unfortunately our initial experience with Ubuntu has not been terrific, for the laptop often freezes with green lines across the screen, sometimes restarts itself for no reason, and will not install Ubuntu base updates because they are from "unauthenticated source". A few days ago I[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]found out that[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]I somehow missed disabling secure boot, but I have not yet fresh-installed Ubuntu to see if that fixes anything. I want to make sure I configure and install everything the proper way with this new PC right from the start, so I can use it for a while to verify it has none of the problems the laptop does, then fresh install Ubuntu in the laptop the same way. Hopefully this will give us the stable reliable Ubuntu computers we were hoping for.

So.. some questions I can think of at this moment[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]are:

>Does BIOS mode (UEFI/Legacy) make any difference at all?

>Should I install the open source or proprietary graphics driver? (originally went with the open source for the laptop, but was having so much trouble I went with the proprietary, which lessened the problems though introduced complaints about third-party drivers)

>Can I select the best server/repository to get updates from straight away? (with the laptop, the first location it got updates from caused problems. I had to search online for a solution, which led me to somehow telling Ubuntu to locate the best place to get updates from, then it finished updating and [/FONT][/COLOR]*[COLOR=#222222][FONT=Verdana]supposedly[/FONT][/COLOR]*[COLOR=#222222][FONT=Verdana]fixed the errors the first place caused)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]
>Do I need swap space? (I gather from an article about swap that with 8GB RAM and no memory-heavy programs or games, swap is not needed)

>For a backup I plan to use rsync, and only backup the user data, not the entire installation. Is that a good plan, or is there a better program or method?

>For a firewall (for the laptop) I followed an article in the forums about Ubuntu security to configure incoming & outgoing ports, but I am not sure if it is still sufficient or if there is a more up-to-date security configuration I should follow? (I want excellent protection from all possible threats, so please point out any programs or configurations/settings I need or can consider)

I know there is more I have thought of, but do not remember right now. Advice, and experience from members with similar builds, is welcome and appreciated![/FONT][/COLOR]

---

### Post by giga+bytes on 2016-07-26
[I][B]Success!!!
[/B][/I]
I have been trying to start this thread for several days and was getting concerned I would not be able to get help before the components are delivered!

---

### Post by mook765 on 2016-07-27
So many Questions, i will answer only your first question (UEFI/Legacy).
 As your computers are pretty new, they should ship with UEFI. So it depends on the firmware of the computer if UEFI allows you to boot in legacy mode or not. If not, you have to install in UEFI-mode. If  Legacy-boot is Supprtted by the firmware, you can choose.
So what to choose then?
Both modes will work. UEFI-mode enables you to access harddiscs with more than 2 TB capacity, in Legacy-mode you are limited to that.
UEFI give you the ability to have an unlimited number of primary partions on your drive, in legacy-mode you can have three primary partitions and an also unlimited number off logical partitions.
For the things you plan to do with your machines, i think it is not important wich mode you choose, both modes will fit your needs.
maybe you should choose legacy-mode, as it is better supported by ubuntu...
Wait a while to get some more information from the Gurus her on this site...

---

### Post by mook765 on 2016-07-27
For the sawp-thing:
it is not a good idea to have a swap on your ssd-drive.
It is also not a must to have a swap-partition.

---

### Post by Bucky Ball on 2016-07-27
Just a point: If you are running just Ubuntu there is no reason whatsoever to use UEFI unless you want to. Just because the motherboard has it you are not forced to use it. If you would like to install in Legacy mode, please do. 

You have many questions. Have you created an install disk or USB and tried Ubuntu in a 'live' session? When you boot from the install media you will be offered the option 'Try Ubuntu without installing'. This will not alter your hard drive in anyway.

If you haven't already, I suggest you try the live session and then you will have some questions we can give definitive answers to. At the moment, not sure what you'll need to do as you don't have the machine and you've asked many questions in the one thread which will be difficult to answer in the one place (we generally stick to one question per thread here for clarity).

IMHO, for now, best to try the live session on a machine you already have, when you've put the new one together, try it in a live session on that and see what happens. Decide whether you are going to use legacy or UEFI to install Ubuntu and install (there is an icon on the desktop of the live session). 

Once you are installed there may not be the need to do anything except enjoy your machine. The most important part at this point is probably deciding whether you are going to use [legacy or UEFI]("http://askubuntu.com/questions/446968/legacy-vs-uefi-help") and researching how if you're not sure.

You should also have a think about how you are going to partition your disks. It is important to have a plan before diving in. Are you going to let Ubuntu use a whole drive and install 'automagically', creating its own partitions and sizes? Would you like to [manually partition]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") the disk and make your own sizes for the partitions?

You are going to need two partitions at least. They will have the mountpoint in Ubuntu of / and /swap.

/ = where the OS goes. 
/swap = like a Windows paging file. Only needs to be 2Gb.

There are many permutations and what's best for you depends on your setup. You can also add a /home partition. If you don't do this, a /home directory will be created inside the root partition (/) instead. Obviously, this makes a difference to how big / is going to be. If you have /home as a directory inside / then / will need to be large as all your personal data will be going there. If you are keeping your data on a separate partition, /home or a /data partition, / only needs to be 15-20Gb. 

Best to [research this]("https://help.ubuntu.com/community/HowtoPartition") also as the way Ubuntu deals with partitions is different to Windows. Just keep in mind that you *must* have / (at least 15Gb to be safe, larger if you're expecting to keep large amounts of personal data and you have no /home or data partition) and /swap (2Gb) partitions, the rest is pretty much up to you.

As mentioned, OS on the SSD, /swap on a HDD. This is not so necessary anymore as SSDs are more robust than they used to be, but still better to go this way.

Just a tip for the future which will get you better support: one question per thread. It is unlikely you will get all these answered in one place. ;)  

Good luck.

[Bit more info:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by giga+bytes on 2016-07-27
Okay, one question per thread, noted. I mainly put them all in the one thread because of the posting problem, so if I finally did manage to submit the thread then could not submit another at least the main questions would be there before all the components are here.

That is the information I was looking for regarding BIOS mode. If there is any reason at all, which there clearly is, to install in Legacy rather than UEFI, then that is what I will do, if it is an option with the motherboard I bought.

I will mark this thread as solved and (hopefully) start new threads for the rest of my questions.

---

