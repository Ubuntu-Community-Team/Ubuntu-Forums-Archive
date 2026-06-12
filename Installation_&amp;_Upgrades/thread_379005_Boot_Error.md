---
title: "Boot Error"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by bparham on 2007-03-08
I have a two hard drive system, to prevent corruption of Windows I switch the drives for installation, placing the Dapper drive in the first or primary position. Installation went great. Here is where it starts to get complicated, I added another partition for home; system started just fine, everything was working; but when I swap the drives I can't get the system to mount the /home partition, thus stopping the boot process. Below is the error I am receiving...

fsck.ex3: Bad magic number in super-block while trying to open /dev/hda3

The superblock could not read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>

I believe I know the error, the system is pointing to the wrong hd, it should be looking for /dev/hdb3. Where do I go to correct this? I adjusted /boot/grub/menu.lst to point to /dev/hdb1, which prior to the new home partition worked just fine. Also, while I'm at it, where can I find the pointer in grub for the swap directory? I believe it may be using my Windows drive as a swap partition. 

Any and all help is greatly appreciated!

---

### Post by chewearn on 2007-03-08
The file you are looking for is:
/etc/fstab

---

### Post by Herman on 2007-03-08
Hello bparham,
I agree with AstalaVista, you need to edit your /etc/fstab file with the correct details of your hard disks and partitions. This web page might help, [Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")
    > I have a two hard drive system, to prevent corruption of Windows I switch the drives for installation, placing the Dapper drive in the first or primary position. Installation went great. Here is where it starts to get complicated, I don't think Ubuntu would have 'corrupted' your Windows install. You have made things a little bit more complicated for yourself than normal. If you had installed normally, this would have been already done for you automatically. 
Good luck, I hope it works out well for you. 

Regards, Herman :)

---

### Post by bparham on 2007-03-08
Perhaps, but wouldn't the installation process have installed grub on my windows drive? 

Anyway, editing fstab worked, the system now boots into Dapper as the secondary boot preventing my wife from having to bother with anything different.

---

### Post by confused57 on 2007-03-08
> **bparham said:**
> Perhaps, but wouldn't the installation process have installed grub on my windows drive? 

Anyway, editing fstab worked, the system now boots into Dapper as the secondary boot preventing my wife from having to bother with anything different.

You could have left your Dapper drive as the primary drive & added an entry to boot Windows:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by bparham on 2007-03-08
I ran into that problem earlier, my original Windows HD would not function as a secondary drive no matter what I did. The only way to get both HD's to work was to place the Linux drive second, to boot into Linux without installing grub on the Window's HD I go into the set-up menu and select the secondary drive. This has worked fine and it keeps the Linux system out of the way of my wife.

---

### Post by Herman on 2007-03-08
> Perhaps, but wouldn't the installation process have installed grub on my windows drive?  Ubuntu would have 'installed grub to MBR' but it wouldn't have touched any part of your Windows filesystem.
When grub is 'installed to MBR', that does not really mean that grub is inside your MBR. What it means is that a small (less than 446 bytes) code is written there to make the MBR point to Grub in the Ubuntu disk or partiion. That part of grub is called 'stage1', and it replaces the old 'stage1' you had there to make the MBR point to Windows NTLDR.
There is an optional part of grub called 'stage1_5 which is written to the next 15 sectors of the first track of the hard disk, after the MBR. The first track of the hard disk is normally empty, being reserved by convention for this type of use. 
Neither the MBR,or the rest of the first track of the hard disk are part of your Windows partition or filesystem.

When the MBR points to Grub, you will be automatically given a menu with an entry in it to give you the chance to boot Windows any time you like, by selecting that item from your grub menu. Then Grub will point to your Windows bootsector and 'chainload' it, and you can boot Windows. The grub menu can be customized to behave in any way you like. You can have Windows boot by default, and have the grub menu hidden if you want. See my Grub Page in my sig link for more details.
> Anyway, editing fstab worked, the system now boots into Dapper as the secondary boot preventing my wife from having to bother with anything different. Okay, I'm glad that worked for you (I knew it would), and you have your computer the way you like it.

I understand what you mean about your wife liking Windows because she's used to it. Most people are like that, it takes a while for people to be convinced to change the way they do things once they get comfortable with a certain set of procedures. Switching to something new requires a little extra thinking, when you really just want to get on with things and get something done easily.
My wife was like that for a long time too, but now she loves Ubuntu, and hasn't booted her Windows XP for weeks or maybe months now. There is just so many more things you can do with Ubuntu once you know how. My wife really likes music, and she prefers 'Music Player' in Ubuntu to 'Windows Media Player'.

When you say 'to prevent corruption of Windows', it might be an fashionable thing to say in a Windows forum, but in a Linux forum it seems more than a bit rude and insulting. 
It's up to you what you want to say, you can say anything around here. 
You would increase your chances of receiving the kind of help you want if you refrain from insulting the favorite operating system of the people you want help from.

Actually what I found out a long time ago is that Ubuntu protects Windows from contamination. When I used Windows on the internet I used to need all sorts of antispyware and anti adware apps, and of course an anitvirus/firewall suite. Then as well you have your defragmenter and regular Windows maintenance apps to run, Many of these things need to be allowed on the internet, or they nag you for an update. Some things nag you to buy the paid-for version, etc. 
Adaware, especially, used to be one of my favorites, it always found plenty of trash that my computer used to gather on the internet. It was a regular job rounding it all up, quarantining it and deleting all that. 
One day I decided, okay, I'm not going to use Windows for the internet anymore, and I'll see what happens. So I did one more rigorous session of updateing, scanning and cleaning in Windows XP. Then I used Ubuntu for the internet exclusively for one week, and kept Windows off-line. 

At the end of that week I ran all the scans possible in Windows XP and guess what? 

Windows had not one bit of trash in it. It was still as clean as a whistle. So I kept Windows off the internet and after never finding any more trash in Windows ever again, I switched completely to Ubuntu. It sure saves me a lot of time not needing to have to check that all those anti-this-and-that apps are up to date and running scans all the time. It save me a little money too.
But the best thing is I can relax now and not need to worry about the newly invented adware and spyware and other malware that the antivirus and anti-adware people don't know aboput yet. A Windows computer can be infected with malware for quite long periods of time without the owner's knowledge. Just because all those scans fail to recognize a threat does not mean that your Windows system is clean. It just means the threat hasn't been identified yet. I had a potentially bad one once that I found out had been in my computer for six months before it was detected.

So Ubuntu doesn't 'corrupt' a Windows installation at all, quite the reverse in fact, it can be used to protect it, and shield it from harmful exposure to the hazzards of the internet..

Regards, Herman :)

---

### Post by Herman on 2007-03-08
> I ran into that problem earlier, my original Windows HD would not function as a secondary drive no matter what I did. The only way to get both HD's to work was to place the Linux drive second, to boot into Linux without installing grub on the Window's HD I go into the set-up menu and select the secondary drive. This has worked fine and it keeps the Linux system out of the way of my wife. Possibly you have some problem in your CMOS (BIOS or more likely the way you have your hard drives plugged into your motherboard, or with your hard drive's jumper settings.

Nevermind, we're gald you're here, Welcome to Ubuntu. :)
Regards, Herman :)

---

### Post by Herman on 2007-03-08
Here is a link to Ubuntuclips.org, where you will be able to view some videos that will help you and your wife learn how to do a few basic everyday things in Ubuntu,

**[[B]ubuntuclips.org** | video howtos for human beings]("http://ubuntuclips.org/")[/B]



My wife and I certainly enjoyed watching some of those videos. I hope they make more of them. Great job there, Allan Pope, and others who are contributing to that project. Very good, excellent! :) 
I learned quite a few tips and tricks from those myself. Those should be a big help to anyone getting started with Ubuntu. They should make the initial learning process much more fun.   :)

Regards, Herman. :)

---

