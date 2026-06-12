---
title: "[SOLVED] How do I format harddrive in Ubuntu."
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by stitcher06 on 2007-11-02
I  have installed Ubuntu 7.10 on my laptop and did so by allowing it to use the entire hard drive on installation, wiping out the vista partition.  I love ubuntu, but do desire to put windows  back on as a backup to some specialized windows software we have.  Should've just went with the dual boot, but hindsight is 20/20.  I have been told that I can't do this from my recovery CD's for vista without starting from a clean hard drive.  I've tried to install the vista recovery CD's with ubuntu installed, but it fails.  How can I completely format the hard drive from ubuntu and start over so I can get to a dual boot setup with windows?  Is this even possible now that I've wiped vista completely out?  Thanks!!

---

### Post by snkmad on 2007-11-02
You can boot from Ubuntu Livecd again.
I think gparted is included on it. You can use it to format the entire drive to NTFS.
The Vista installer will see the drive as normal, it should work.

---

### Post by zvacet on 2007-11-02
[http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot]("http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot")

---

### Post by martin622292 on 2007-11-02
i have the same problem . . . thought i'd bypass the technobabble by removing the hd and taking it to a computer store to be wiped for $5 . . . 

now to reinstall vista . . . or windows 2000 . . . all l get is:

                                      grub loading  . . . error 17

in other words, linux is still on the disc 

the techbabble for these items is paralysing . . . so unless something comes of your post i've no choice but to install a new hardrive . . . good luck . . .

---

### Post by stitcher06 on 2007-11-02
I'll be trying your suggestions.  Thanks!!:(

---

### Post by stitcher06 on 2007-11-02
I've tried using the livdcd, but it won't boot from this anymore, just goes to the main login sceen for ubuntu.  I got gparted, but don't see how to partition entire drive to NTFS.  There are 3 partitions for ubuntu and nothing else.  How do I go about formatting the hard drive completely so I can re-install vista and start over with the dual boot for ubuntu?

---

### Post by stitcher06 on 2007-11-02
> **snkmad said:**
> You can boot from Ubuntu Livecd again.
I think gparted is included on it. You can use it to format the entire drive to NTFS.
The Vista installer will see the drive as normal, it should work.
Is the "live cd" the same cd I used to install ubuntu?  Sorry for a really newbie question, but I am.  If it is, it isn't booting from the cd.  When installed, it still boots into the ubuntu system as installed.  I tried gparted from the operating system, but don't understand what to do to start over trying to clean the hard drive and start over.

---

### Post by zvacet on 2007-11-03
> I've tried using the livdcd, but it won't boot from this anymore, just goes to the main login sceen for ubuntu. I got gparted, but don't see how to partition entire drive to NTFS

If you want dual-boot you don´t need to format all hd to NTFS.Just take some free space from existing Ubuntu partition and that free space format as NTFS.Of course,you can remove all partitions and start fresh with win installed first.Your choice.

---

### Post by martin622292 on 2007-11-03
i downloaded supergrub, burned it onto a cd, rebooted, and lo and behold, a menu with windows as an option . . . (it disappeared quickly and i had to return to main menu) . . . it booted into windows vista setup much to my amazement, for i thought i'd overwritten it with ubuntu (i'd also had the disk wiped at the computer store) . . . so i'm in business again . . . martin622292

---

### Post by stitcher06 on 2007-11-03
> **martin622292 said:**
> i downloaded supergrub, burned it onto a cd, rebooted, and lo and behold, a menu with windows as an option . . . (it disappeared quickly and i had to return to main menu) . . . it booted into windows vista setup much to my amazement, for i thought i'd overwritten it with ubuntu (i'd also had the disk wiped at the computer store) . . . so i'm in business again . . . martin622292

Thanks for letting me know that!  I had good luck re-formatting the hard drive last night, but now am getting the grub error 17 when trying to boot vista.  I should've left a partition for ubuntu, but didn't when I reformatted.  I thought it would be easier to start over.  I don't have time to work on it right now, but hopefully in a couple hours after I finish up what I'm doing here.  Thanks for getting back to me.  Glad your system is back in order.

---

### Post by stitcher06 on 2007-11-03
Just wanted to say thanks to everyone for your help.  I'm new to this linux stuff.  I got vista back up and going again.  I must say, the first thing I'll be doing is getting ubuntu back on properly this time so vista can sit unused only when needed for certain software.  Thanks again!!!

---

### Post by zvacet on 2007-11-03
[http://users.bigpond.net.au/hermanzone/p15.htm#17]("http://users.bigpond.net.au/hermanzone/p15.htm#17")

---

### Post by stitcher06 on 2007-11-03
I'm very new at ubuntu, but what everyone told me (and it worked) is to boot from your live cd.  Go to system - administration (I think) looking for a program called Gnome Partition Editor.  Choose your current ext3 space (it's the largest) and reformat to whatever you need, in my case NTFS for windows.  Hope it helps.

---

### Post by stitcher06 on 2007-11-03
If it's not under the administration, it's under the preferences selection of the system tab.  I haven't gotten ubuntu back on my system to look at it quickly for you and be more accurate - sorry.

---

### Post by shaft350x on 2007-11-04
> **martin622292 said:**
> i downloaded supergrub, burned it onto a cd, rebooted, and lo and behold, a menu with windows as an option . . . (it disappeared quickly and i had to return to main menu) . . . it booted into windows vista setup much to my amazement, for i thought i'd overwritten it with ubuntu (i'd also had the disk wiped at the computer store) . . . so i'm in business again . . . martin622292

You had them wipe the drive and you were then able to find Vista on it?  If I'm reading that right, then whatever place "wiped" your drive, did a poor job, lucky for you I guess.  You only got ripped off for what they charged to wipe the drive, and now have a working Vista and Ubuntu machine.  Though if you were just unable to get Vista to load after you tried to reinstall it...then disregard everything I just wrote.  Glad you got your system working!

---

