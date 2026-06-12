---
title: "Stuck at Installation Type"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by nerdgirl on 2011-10-27
Hi!

I have a new computer and I want to try Ubuntu. I am going with Xubuntu because that's what a friend of mine at school uses. She doesn't know what to do here either though. I am stuck at this screen. When I click next it says something about a root partition? This is a Desktop computer with an AMD 64-bit processor and a 250gb harddrive, I don't know anything else specific but I can try and find out if it helps.

I tried google and searching the forums and found a lot of guides like [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) but I can't find anything about this. This is my screen, please tell me what I should try next or if there is something I can read that is specifically about this problem! Thank you =)

Please be patient with me I am not super computer savvy...
[IMG]http://i.imgur.com/xWCFX.png[/IMG]

---

### Post by Quackers on 2011-10-27
Welcome to UF :-)
You have a couple of choices.
You can either delete the ext2 partition that you have already created, then use the "use the whole disc" option in the installer.
Or you can double-click on that ext2 partition (might be better as ext4 actually) and then give it a mount point of " / " from the mount point drop-down window on the next page.
This will cancel out the root system error.

---

### Post by nerdgirl on 2011-10-27
I had GParted open and made the ext2 hoping it would fix it (not really knowing what I am doing I suppose) but no luck. =(

I deleted the partition and let it do it's changes, but I ran through the installer again and I still came to the same window. I tried to reformat it as ext4 and had the same thing. I am not seeing a mount point drop-down, should it be on GParted or this install program? I also never got a "use whole disc" option on the installer, although I would be more than glad to let it format the drive and start from scratch.

I also found another page that said to run sudo apt-get remove rmraid (or something like that) but it didn't work as the installer just hung when I ran it. I have rebooted again and tried to run the installer on that same unformatted disk now and still no luck =(

---

### Post by Quackers on 2011-10-27
So the hard drive now has no partitions?
Which version are you installing and what options do you see?

---

### Post by nerdgirl on 2011-10-27
> **Quackers said:**
> So the hard drive now has no partitions?
Which version are you installing and what options do you see?
Right now it says "unformatted" and no partitions.

I am trying to install Xubuntu 11.10 (just downloaded it last night). It gives me the option to choose my language, and then the "preparing to install" screen, and then the one that I have in my original screenshot. The computer I am working on isn't connected to the internet right now but the other two screens I see look like these (just, not this version):


[IMG]http://i.imgur.com/g6Rpe.png[/IMG][IMG]http://i.imgur.com/wUQxZ.png[/IMG]

---

### Post by Quackers on 2011-10-27
After clicking on forward you should next see the screen in screenshot 1, then after that one you should get the screen in screenshot 2. At that screen choose the "erase disk and install ubuntu".
If you aren't getting to those screens then you should check the md5sum of the downloaded iso file and/or check the cd/usb for errors.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by nerdgirl on 2011-10-27
Ok, I am not getting that screen at all. I will verify the disc and report my status later today. Thank you for the help =)

---

### Post by Quackers on 2011-10-27
You're welcome. Good luck :-)

---

### Post by nerdgirl on 2011-10-27
Home now my disc passed the check, but just to be sure I burned it with a different burner on a different type of disc. Same results, I am still getting the blank screen and definitely no "use whole disc" option. 

I read somewhere that my disk needs to be formatted as a logical partition to mount as /. The option to format it that way is greyed out unless I format it as an extended partition, and *then* a logical partition. Even doing so creates no results.

Perhaps something is in the BIOS? I am not sure what else to check... =(

---

### Post by ankspo71 on 2011-10-28
Hi,
There is at least one other user having a similar problem and it was reported as a bug in Ubuntu 11.10:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/878568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/878568)
(The link include similar screenshots too)

Read post 2 and 3 in the above link. The user posted a solution to the problem that might help you too (that is, if your hard drive is being flagged as raid too). 

Note: The Disk Utility application is already installed in Ubuntu but not in Xubuntu. To use this application in Xubuntu you will need to install "gnome-disk-utility" then you can find the application at Start Menu > Settings > Disk Utility. It can be found in Ubuntu Software Center by searching for "gnome-disk-utility" or "Disk Utility".

Hope this helps.

---

### Post by nerdgirl on 2011-10-28
Yes, I think that is my problem. I will try these methods, thank you! (Marking as solved for now.)

---

### Post by querolus on 2012-08-30
Hi,

I'm having exactly the same issue with Ubuntu 12.04.1. However i don't know exactly what do i have to change in my partitions configuration so i can see them in the installation type screen.

Could you tell me how were you able to solve it? I looked in the bug page but i did not understand exactly what was going on with the 'raid drive' and how to solve it.

Please understand that i'm new with Ubuntu and need detailed explanations...

Thank you

---

