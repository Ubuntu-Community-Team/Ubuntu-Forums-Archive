---
title: "replace Vista / XP with Ubuntu"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Sugz on 2008-01-28
Ok so here is the situation.
My friend and I are thinking of Replacing Vista on both our Laptops with Ubuntu as the Primary OS. 
I will probably use VMware later to use XP but ill leave that for now. 
So We are both using Wubi to run Ubuntu Feisty. 

I am doing this because Vista is wasted space, i just dont use it on my Laptop and i would prefer it if  it was gone. 

Im not sure about them but myself, i have just spent a ages getting my Ubuntu installation to the way i like it.
But my friend is willing to wipe out Vista and just have Ubuntu. 

So how would we go about doing this cleanly?

1. Uninstall Vista
2. Install Ubuntu?
*3. Keep current Ubuntu Setup

Any help will be appreciated.
-Sugz

---

### Post by Game_boy on 2008-01-28
The absolutely easy thing to do would be to burn an Ubuntu Gutsy disk (why Feisty?) and select the option in the installer of formatting the entire disk.

To keep your current setup, you would have to turn a Wubi-Ubuntu into a real Ubuntu, and then you still would have Feisty not Gutsy. Wubi is really hard to separate from Windows, and then you'd have to expand the Ubuntu partition over Vista. I would say just use an install disc.

---

### Post by steveneddy on 2008-01-28
I don't know that much about WUBI, but if there is a /home folder, copy that to a flash drive of something and make sure you get your favorite wallpapers and stuff.

Install Ubuntu and then copy the /home folder from the flash drive to the new /home folder that you just installed.

---

### Post by Game_boy on 2008-01-28
> **steveneddy said:**
> I don't know that much about WUBI, but if there is a /home folder, copy that to a flash drive of something and make sure you get your favorite wallpapers and stuff.

Install Ubuntu and then copy the /home folder from the flash drive to the new /home folder that you just installed.

He would still have Feisty though, not Gutsy.

---

### Post by Sugz on 2008-01-28
I think the reason why im wanting to keep feisty is that im familiar with it, i know that it will run on my laptop with no problems whatsoever.
GUTSY, well i'm not sure about using an OS that is still relatively new.

---

### Post by edm1 on 2008-01-28
> **Sugz said:**
> GUTSY, well i'm not sure about using an OS that is still relatively new.

It is only 6 months newer than feisty. Just an updated version with the latest software really. As already mentioned, download and burn the live CD and make sure that it runs on your hardware then it's pretty safe to install.

---

### Post by Sugz on 2008-01-28
Well Wubi runs feisty flawlessly so i suppose i could just get the Wubi version instead.

---

### Post by edm1 on 2008-01-28
I say if Wubi runs feisty flawlessly there's no reason not to do a proper install. You should see hard-drive speed improvements.

---

### Post by Game_boy on 2008-01-28
> **edm1 said:**
> I say if Wubi runs feisty flawlessly there's no reason not to do a proper install. You should see hard-drive speed improvements.

I agree with that.

Gutsy has several new features that you will want, namely NTFS write support (so you can edit external hard drives) and Compiz (awesome). There is practically zero chance of breakage, unlike new versions of Windows.

If you don't want Windows, you CANNOT have Wubi. Wubi depends on Windows.

Just get a Gutsy install disk and use it to wipe every drive you want Ubuntu on.

---

### Post by perixx on 2008-01-28
@Sugz:

**[COLOR="Red"]Before [/COLOR]**doing **ANYTHING** else, I'd suggest do find out if there's some kind of recovery-partition on your friend's notebook. If he has no installation CD (and most laptops don't), you'll have great woe's to go about after you've wiped the entire HDD with Gparted and your friend suddenly decides to switch back to Vi$ta (for gaming or such)!

I don't know if Gparted also recognizes and displays hidden partitions / HPA's (which recovery partitions usually are), though. 
When wiping the HDD with gparted, and there's some strange partition displayed, that you haven't seen before (maybe 5-15 GB's), then best leave it where it is! That is, if there's really no Vista installation CD, otherwise - happy wiping... :]

If your friend is sure he wants to get perma-rid of Vi$ta (**SURE as can BE**)... then you can unlock any existing HPA's (hidden protected area) with 'HDAT2' and reclaim the protected space...

perixx

---

### Post by Sugz on 2008-01-28
Thanks for the info
and im sorry about the double post.

My situation - I have a PC and Laptop, PC == Gaming and Graphics Work
Laptop == Work and Programming

:)

My friends Situation 
Laptop == Work and Programming

But thats really promassing, well i have a 320Gb ext HD so ill backup EVERYTHING even if i think it is irrelevant. 
and ill start this process. 
Wish me luck!

---

### Post by perixx on 2008-01-29
I do!

---

### Post by Sugz on 2008-01-30
Ha, ok this may take a bit longer.. that expected. 
But just a few final thoughts. Is there anyone who haa done the same ie.
Got fed up with windows.
Uninstalled Windows
Installed Ubuntu
installed Windows under VMWare (or similar)?

I think i am hesitant because i have never Completely uninstalled and re-installed an OS onto my HD before.

---

### Post by perixx on 2008-01-30
As I said before, as long as you have your XP/Vista installation CD and backed up all your vital personal data to CDROM, there's nothing much to fear about. You can always re-format the HDD and install Windows again. Or you make a dual-boot, so you can always switch back to XP/Vista temporarily, should you desire to do so. 
Some time ago I've read about MS had release a virtual XP-version that had a limited lifetime of 127 days or so; maybe you can trick this version by clearing out the MBR+Win-bootsector and reinstalling it every 127 days... but apart from a few special applications, the main use of XP is for games now I suppose - if you're no gamer, you can perhaps leave it now and forever.
 
All you need to invest is time... and patience (maybe quite some for the very start) ;)

perixx

---

### Post by Therion on 2008-01-30
> **Sugz said:**
> ... Is there anyone who haa done the same ie.
Got fed up with windows.
Uninstalled Windows
Installed Ubuntu
installed Windows under VMWare (or similar)?
I did pretty much just that.  No need to uninstall Windows, let the Ubuntu installer wipe Windows right out of existence while it formats your drive for you as part of the install process.  

When you're done installing, use Virtual Box if you want/need Windows for something you just can't do in 'buntu (not likely to happen but if it makes you feel better...).  Furthermore,  Virtual Box was a breeze to set up; I mean seriously, if *I* can do it?  Yeah... Anyone can.  I've got a pretty good tut/walkthrough around here somewhere if you need a link for it.  Eh, screw it... Here it is whether you want it or not:  [Getting Virtual Box Up and Running]("http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html")

Dump Windows.  You'll be glad you did.  It's an amazing feeling.

---

### Post by Sugz on 2008-01-30
Thank you for those encouraging words, as for time, this Friday is when its happening :popcorn:

---

### Post by perixx on 2008-01-31
Good luck!

I recommend 
1) using the 'Let Ubuntu use all space of the drive' or 
2) manually specifying about 15GB (ext3) for root partition ('/'), at least >25GB (ext3) for '/home' partition and twice your RAM's size for a swap partition (e.g. 1GB=>2GB. In any case, GRUB get set up in the MBR (on 'hd0').

This way, you should have enough temporary space for installation files and addidional programs/upgrades on root + a large /home for games, films and temporary backups - preventing root from a harmful 'overflow'.

perixx

---

### Post by Sugz on 2008-01-31
OK, i just went to make sure that the newely burned CD is OK
now remember im using Wubi currently, whenever i select my boot options as CD/DVDR drive i keep on getting the GRUB OS selction screen.]
Is this WUBI overiding the CD boot?

---

### Post by Sugz on 2008-02-01
OK
so i have downloaded both Linux 7.06 and 7.10 and NONE WORK WHEN TRYING TO BOOT THEM UP!!!
I have used a program to check checksum and both return Different.
SO HOW CAN I MAKE SURE THAT DOWNLOAD AND BURN ARE SUCCESSFUL??

PLEASE help:confused:

-SUGZ

---

### Post by perixx on 2008-02-01
Hi sugz,

Did you make sure that the md5 sum on the Ubuntu download page reads the same as the output of the following terminal-command?
```
md5sum /path/to/UBUNTUIMAGE.iso
```
Where you need to specify the path for your Ubuntu-image (or 'cd' there) first. 'UBUNTUIMAGE.iso' is just a placeholder for your downloaded .iso file, of course. 

For easier verification, you can copy the md5 sum in your browser and then paste it under the output of the command with your mouse's middle button. There might be a way to compare directly, but I don't know it... if anyone does, please post here!

Btw. it's possible to use sh1 checksums the same way instead, if there are some given strings: ```
sh1sum /path/to/UBUNTUIMAGE.iso
``` SH1 sums are considered to be safer than md5 sums, so I've read.

If you fail to get correct checksums by downloading your .iso via http/ftp download, you could try to download via bittorrent instead... or you might use the alternative install CD (haven't used it myself, though).

perixx

---

### Post by Sugz on 2008-02-01
Thank you All for your contribution to my problem.
Now i have a Fully working 7.10 Install :)
But.. 
whilst i was installing icon themes and such from my backup External HD, the backup Folder  disappeared without a trace?

How can i recover this is possible?

---

### Post by perixx on 2008-02-02
Hm, I can only guess. Did you MOVE the folder to its new destination, perhaps?

perixx

---

### Post by Sugz on 2008-02-04
Many thanks to all those who helped. 
I am now happily running Ubuntu Gutsy 7.10 :guitar:

---

### Post by joshdudeha on 2008-02-04
Yay, glad for you
I'm about to get rid of the hell called windows
and just totally re-format everything for 7.10.
gonna do it when me dad gets home (not cos he knows anythign about computers, but to check he's ok getting rid of windows )
then ill be free as anything.
Like a whole new computer again!!!
I shall post to see how it goes ^^

---

### Post by Sugz on 2008-02-04
Excellent choice sir!
However, time is needed to get it workinf the way you want it ie. Customization. if you look on the member cafe forum in the desktop screenshots section near the back, you will see a picture of my desktop.
I can tell you everything you need to know about how to get it to look like that.
And also i can suggest some rather good apps to make you feel more at home in Ubuntu
All the best
-Sugz

---

### Post by joshdudeha on 2008-02-04
Aww cheers!!
I got it running.
And it is so different to 6.06
I love it !!
It feels so good not to have windows either.
Thanks everyone for support over the past month.
You've all been great!
Thanks as well sugz - I may require help some day. 
x

---

### Post by Sugz on 2008-02-05
Absolutely no problem :) in fact i have convinced a few other people to do the same thing

---

### Post by joshdudeha on 2008-02-05
Ah good!
I hate using the computers at school now :(
All windows xp
They are all blind to the real world haha
Nah, it doesn't matter.
But i love ubby so much.
Got compiz working yesterday 
on my 64mb onboard graphics xD
works with no problems
Im so happy
Keep going in and out of the cube haha
How is everyones linux going ? XD

---

### Post by rich41952 on 2008-02-22
Ok, slightly different question.......I have XP on my "C" drive, and installed Ubuntu 7.10 on my "D" drive (dual-boot) I am using an external drive for backup storage. I want to make the move and completely remove XP.........I can't find ANY reason to keep it:) My question is, can I have the live CD wipe my "C" drive where windows lurks, install Ubuntu on that drive, and still somehow access the previous Ubuntu installation I have on "D"? Thanks in advance! One more deserter from the Borg!

---

### Post by Sugz on 2008-02-24
Hmm, well it should be the same principle, you insert the live CD, boot and the installation process can Reformat your drive, install Ubuntu with no strings attached. 
I can see why you should not be able to use your previous installations if it is on a different drive. 
But thats my opinion, and i am in no way shape or form an experienced Ubuntu user when it comes to the installation process
Best of luck 
_Sugz

---

### Post by rich41952 on 2008-02-24
Thanks!  I guess I'll just bite the bullet and install on my "C" drive and configure it all over again (I'm getting good at that......:))  I can't believe Linux was out there buried under all the Windoze peeps misinformation. After years with Microsuk the computer was pretty boring.......now it's interesting all over again! I'm retired, and re-installation is so easy that I can drive it til I break it and start over and be back up where I was in no time.

---

### Post by scrooge_74 on 2008-02-24
You can even tell the new install that your /home folder is on the D: drive so to speak, and can even have both copies of Linux able to run one in C and one in D drive

---

### Post by rich41952 on 2008-02-24
Ok, thats what I needed to know. Now I can have one installation to learn on, and one to get stuff done. Thanks a lot!

---

### Post by anachreon_ on 2008-02-24
> **Sugz said:**
> Ha, ok this may take a bit longer.. that expected. 
But just a few final thoughts. Is there anyone who haa done the same ie.
Got fed up with windows.
Uninstalled Windows
Installed Ubuntu
installed Windows under VMWare (or similar)?

I think i am hesitant because i have never Completely uninstalled and re-installed an OS onto my HD before.

HEhehe yeah, lots of people, myself included.  About a year and a half ago, now.

---

### Post by rich41952 on 2008-02-24
Well, Windows has crashed so fiercely on me a few times that I had to re-install it from the disc, and believe me, it's a nightmare compared to installing Ubuntu. There's a learning curve on Linux, especially for an old fart like me.......(Hint........numbers in my screen name r my DOB....hehehe). I've used the last 3 versions of Ubuntu, and each one just gets better and more stable. I was just always too chicken to dump windows in case I had to get online after somekinda Ubuntu crash to find help. I've found out how to recover from any kind of crash I've had so far, so it's goodbye Bill Gates for good. Plus, you guys are 500% better than anykind of Microsuk "support" that probably works out of a storefront in Bangladesh.

---

### Post by perixx on 2008-03-17
> **rich41952 said:**
> Well, Windows has crashed so fiercely on me a few times that I had to re-install it from the disc, and believe me, it's a nightmare compared to installing Ubuntu.

Absolutely ^^) 

I've been doing a little investigation about this latey, and I've finally manged to find something that suits my needs: **ntfsclone**!
So far, I've set up a completely updated and optimized-to-the-fullest XP (size: 3.2GB on 40GB partition), that I've cloned into a disk image-file of exactly 3.2GB!

It took me about 3 days to iron out all possible pitfalls (was doing some heavy registry optimizations along the way), but: recovering into a working XP system is a matter of 10 minutes now - I could even have several 'stacked' XP clones on one HD, if I wanted to :mrgreen:


perixx

---

