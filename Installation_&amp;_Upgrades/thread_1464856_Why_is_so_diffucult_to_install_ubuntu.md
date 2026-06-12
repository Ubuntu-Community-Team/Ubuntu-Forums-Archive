---
title: "Why is so diffucult to install ubuntu??"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by ferjonathas on 2010-04-28
I have no experience with the lunix softwares, but I heard its really nice so i thought of giving it a try.  But unfortanally i had no luck installing it since its different from windows.
 
I downloaded the ubuntu 9.10 from this web site, tried to install it but no luck.  So downloaded a booting device that someone here told me to do, but still no luck.  I suceefully made a boot disk from my hd but i get stuck with the commands line.
 
on windows I usally go...  from C:/ i would go to E:/ then i would write a command like E:/dir find the file im looking for and install it..
 
but now on lunix its completly different, i have no clue what the commands are..
 
what is the easiest way to install ubuntu.. im able to use a cd and i have downloaded the 9,10 version.. but i cant install it 
 
HELP>..

---

### Post by QIII on 2010-04-28
Are you trying to install Ubuntu as a stand-alone operating system, or in Windows with WUBI?

---

### Post by ferjonathas on 2010-04-28
I want to install a fresh copy on my pc... I want to try ubuntu in one of my laptops..

---

### Post by QIII on 2010-04-28
Do you want to completely replace Windows, or do you want to retain both Windows and Ubuntu?

---

### Post by ferjonathas on 2010-04-28
I want to replace windows with ubuntu.. but i cant figuere out how to do that

---

### Post by lisati on 2010-04-28
When you have downloaded Ubuntu you can put it on a CD, see here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then, with the newly created CD in your disk drive, restart your computer. Be sure to check that your computer is set to boot from CD.

After a short delay you should get a list of options which includes things like "Try without installing" and "install".

Hope this helps.


Edit: apologies for the brevity: "real life" is a bit distracting at the moment, Mrs Lisati wants me to cook lunch and there are some people across the road working on the power lines.

---

### Post by QIII on 2010-04-28
If you machine's BIOS is set to boot from the CD drive first, simply place the disk in the drive, shut down and restart.

You will be presented with a menu.  Choose install.  The installation process is very simple and very quick, but that does not mean you might not have questions.

When you get to the "Partition" screen, the simplest thing for you to do would be to use the "Use Entire Disk" option for now.  As you get used to Ubuntu, you will have more understanding of the process of partitioning.

Stay by another machine in case you run into problems so you can ask for help here.

EDIT:  Thanks, lisati!  Getting too used to this.  I wrongly assumed that the OP had already created a LiveCD...  Bad me!

---

### Post by emoguitarist06 on 2010-04-29
> **QIII said:**
> If you machine's BIOS is set to boot from the CD drive first, simply place the disk in the drive, shut down and restart.

You will be presented with a menu.  Choose install.  The installation process is very simple and very quick, but that does not mean you might not have questions.

When you get to the "Partition" screen, the simplest thing for you to do would be to use the "Use Entire Disk" option for now.  As you get used to Ubuntu, you will have more understanding of the process of partitioning.

Stay by another machine in case you run into problems so you can ask for help here.

EDIT:  Thanks, lisati!  Getting too used to this.  I wrongly assumed that the OP had already created a LiveCD...  Bad me!

This is exactly What I suggest also! Change your bios to boot from CDROM and then Choose Install and at Partition Choose "Use entire disc" and it will warn you that you'll be formatting your hardrive.

---

### Post by uncleV on 2010-04-29
Well having LiveCD it's wise to try Ubuntu without installing, loading it directly from the CD.
This way you will find if there are problems with Ubuntu on your machine _without destroying the previous operating system_.


So I suggest you first *"Try without installing"*. If you feel there are no problems then reboot and install. (naturally Ubuntu is slower when in LiveCD session)
But if you encounter problems you just reboot, pull out the LiveCD and go back to Windows.

Please don't overlook the following:
Before burning the disk do the *md5sum* check of the .iso file. Burn at the slowest speed.
Before installing do the *"Check disk"* from the LiveCD menu.

---

### Post by cascade9 on 2010-04-29
> **lisati said:**
> Edit: apologies for the brevity: "real life" is a bit distracting at the moment, Mrs Lisati wants me to cook lunch and there are some people across the road working on the power lines.

Wow, its busy, Busy, Busy! in Porirua. :lolflag:

I only get distracted by gunfire, very large groups  of drunks or the cat telling me that the dinner service is Sadly Lacking thes days.

> **uncleV said:**
> Please don't overlook the following:
Before burning the disk do the *md5sum* check of the .iso file. Burn at the slowest speed.
Before installing do the *"Check disk"* from the LiveCD menu.

I agree on 'slow speed burning' (though I tend to avoid the absolute slowest). But md5checksumming? o.O 

Dont get me wrong, its a good idea, and a usefull tool, but I never bother unless I have a problem. I tend to asdise prople to do the same, and use 'check disc for defects' if there is a problem. I know lots of people who have had a lot of 'what heck am I doing' moments with md5checksums, its not as easy a process as it should be.

BTW, I've always wondered how hard it would be for the burning programs to have a built-in comparison (add file, add checksum, compare). Probably wouldnt be much use for me, but for 1st timers looking to do things the 'right' way, or for people offering advice on how to do it the right way, it would be a a handy tool....

---

### Post by dmp2010 on 2010-05-04
I agree. It's so difficult to install. I downloaded Ubuntu 9.1 and the latest 10.04. Neither works. I checked the files using *md5sum *and both failed. I downloaded using Torrent, that failed too. I have Fedora 12 on one my laptop computers. It worked fine. Only reason I am trying to go from Fedora to Ubuntu is because I have read some preference of Ubuntu for Home Theater PC.

---

