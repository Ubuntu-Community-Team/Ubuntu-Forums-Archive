---
title: "alternate CD integrity test fails"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by DrScum on 2008-09-29
I have downloaded xubuntu-8.04.1-alternate-i386.iso from two different mirrors and burned to disk. Both disks fail the integrity test.
Is there another way to install Xubuntu on a PIII 500mHz Machine with 500MB of RAM? The desktop version doesn't work, I tried that.

---

### Post by Partyboi2 on 2008-09-29
> **DrScum said:**
> I have downloaded xubuntu-8.04.1-alternate-i386.iso from two different mirrors and burned to disk. Both disks fail the integrity test.
Is there another way to install Xubuntu on a PIII 500mHz Machine with 500MB of RAM? The desktop version doesn't work, I tried that.
Did you check the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") after you downloaded the ido? Maybe burn the iso at x4 or less speed if you have not already.

---

### Post by DrScum on 2008-09-29
checked checksum of the .iso file and it came out ok
burned at lowest possible speed (12x) supported by my burner
cd integrity check still comes out negative. The message is that some gimp-help-file fails the checksum verification and that either the file or the cd are corrupted.

Any suggestions?

---

### Post by Partyboi2 on 2008-09-29
Try another program like [[COLOR=Blue]imgburn[/COLOR]]("http://www.imgburn.com/") that allows you to burn at a lower speed. If you have passed the md5sum then the downloaded file is ok and the problem is something to do with the burning part.

---

### Post by DrScum on 2008-09-29
hard for me to believe, since I burned on two different machines, one a Linux desktop and the other a windows laptop. But I'll try what you're suggesting and will burn another CD.
Thanks.

---

### Post by jacktar on 2008-09-29
Mine also failed the integrity test, however it installed ok. Have you tried to use it ?

---

### Post by DrScum on 2008-09-29
Yes, only the fact that an install failed with two different CD's made from two different images made me do the integrity check.
The install stops at "select and install software" with a red screen telling me that one of the steps failed.

I wouldn't bother so much but I have an old machine (PIII 500mHz, 512MB RAM) which I would like to use as internet router. The connection to the network needs to be through WLAN and Xubuntu supports the WLAN card (SMC 2802W V2 EU) out of the box (whole other series of posts regarding that card).

On this old machine an install using the desktop CD doesn't work so I need the alternate CD and I am afraid now that the alternate CD has a bug not detected so far since nobody ever uses it.

Thus I either need the alternate CD or I need another lightweight distro supporting my card out of the box since I am not savvy enough to make it work manually with another distro (tried Vector Linux so far but to no avail).

---

### Post by Nebutron on 2008-09-29
> **DrScum said:**
> checked checksum of the .iso file and it came out ok
burned at lowest possible speed (12x) supported by my burner
cd integrity check still comes out negative. The message is that some gimp-help-file fails the checksum verification and that either the file or the cd are corrupted.

Any suggestions?
I would consider a couple of things.  First, ask yourself how confident you are in the condition of the two CD  burners you have used.  If highly confident in that, consider what is the quality of the blank CD's you are using.  I had a lot of trouble with cheap Memorex CD's not burning correctly.  Switched to a better quality CD and magically, no more problems.  Good luck!

---

### Post by NovaAesa on 2008-09-29
> **DrScum said:**
> The message is that some gimp-help-file fails the checksum verification
If this is the only file that failed, then it should still be able to install correctly. The only problems you may encounter would be if you were to try using the help system for The GIMP.

---

### Post by HiDef4Ever on 2008-09-29
I'm also having "Integrity test failed" on an older PowerEdge 1550 (PIII 1.0GHz 1024MB RAM) using the 8.04.1 server install image. I've tried two spare cd drives with the same result. Also, the install fails about a quarter of the way through with a corrupt file error. But if I run the CD integrity checker on a more modern machine, it sumchecks ok.

---

### Post by Nebutron on 2008-09-29
> **DrScum said:**
> The desktop version doesn't work, I tried that.

When you refer to trying the Desktop version and it doesn't work, I presume you are referring to the LIVE CD??  If so, what exactly happens when you attempt to use the LIVE CD?

---

### Post by HiDef4Ever on 2008-09-29
I've attached a scsi cd drive to the PE 1550 and it passes the integrity test with flying colors. I'll attempt an install later or perhaps tomorrow and post the result.

---

### Post by Herman on 2008-09-29
For best results when downloading your Ubuntu 'Alternate' CD or any other files, it is best to use BitTorrent or the wget command instead of just downloading the file through your web browser. 
I used to be in the habit of downloading via a web browser and sometimes I was lucky and other times not so lucky. 
The wget command or BitTorrent can even download very large files such as .iso files to make a DVD with, and they always get the complete file even if the connection gest reset.  There is hardly any chance you will end up with a corrupted file if you use BitTorrent or wget.

You need to begin with an .iso file with the correct md5sum before you'll be able to burn a CD which will pass the integrity test.

You need to buy good quality CDs and keep them clean and free from scratches. 
I have experienced problems from bad batches of CDs. Good quality brands of anything have consistent quality control, but cheap brands may produce bad batches or borderline batches when a machine goes a little bit out of adjustment or something like that at the factory. Reputable brands cost more because they throw out all the borderline products or sell them under a cheaper label. And they pay their staff better, so are able to retain good staff who know how to keep the machines adjusted properly. Borderline CDs might still be okay for music, but for software, especially when it is compressed enough to fit an entire operating system and all the programs for it on one CD, we need to use good quality media.

Sometimes wiping a CD with a soft cloth dipped in denatured alcohol, (methylated spirits), wiping gently from the center towards the outside can clean a CD even if you can't see any dirt on it with the naked eye. If it's a CD-RW, re-burning might then result in a valid disc. This has happened to me.

The optical lense in the DVD/CD drive also needs to be clean.
Most computers suck dust in through any openings in the case, including the CD/DVD drive, because the fans mainly blow outwards, creating a negative pressure, (slight relative vacuum), inside the case.
(Besides the possibilty of dirt being put in on dirty CDs or DVDs.)
 Dust, smoke or an oily film (once again, invisible to the human eye), may interfere with the proper function of the optical lense.
Sometimes these lenses are easy to access and clean since in some types of DVD/CD drives, they slide out each time we open the tray. The downside is, then they are also more exposed to the elements, so if a person coughs or sneezes while the CD try is open... well, you can use your own imagination.
Other types of CD/DVD drive need to be physically removed from the machine to clean the lense properly. A few have a hatch on the top so you can reach the lense with a Q-Tip dipped in denatured alcohol, (cotton bud dipped in metho), without dis-assembling the entire unit.
Most of them need to be dismantled and cleaned properly and re-assembled again. Not a job for the average computer user, and the cost of getting a technician to do it will probably exceed the price of a new optical drive. 
However, if you're handy, you may be able to do it yourself and save some money. A tip (hint) is to poke a .8mm x 25 mm metal rod into the tiny hole in the front to push on the mechanism the releases the tray, so it can be dragged open by hand, allowing the front cover to be unclipped, and then the rest of the box can be opened. 
Use a vacuum cleaner or a tin of compressed air to remove any dust and other foreign matter. (I have found some strange objects in old CD drives!, LOL).
Clean the optical lense with a Q-Tip dipped in denatured alcohol, (cotton bud dipped in metho).
Then re-assemble the unit and hope you can figure out how it all goes back together again. With a little patience and perseverance you can do it. 
This has happened to me several times since I live in a dusty climate, (the dry and dusty Australian outback).

Regards, Herman :D

---

### Post by cariboo on 2008-09-29
I agree with Herman. Clean your cdrom drives manually, do not use those cd cleaners you see at Wal-Mart or other discount stores. Back when I repaired consumer electronic equipment I saw lots of cd drives rendered useless by cd drive cleaners.

Jim

---

### Post by DrScum on 2008-09-30
Thanks guys for your input. I believe if burning a CD would be such a tough task as you describe it, much less disks would be burned successfully.

In this particular case within a time frame of about two days I downloaded about 10 iso files of various Linux distros, burned them on CD's from the same batch and exactly the two Xubuntu came out bad. Moreover, after discovering the problem I downloaded from yet another mirror and burned at slowest possible speed and it came out bad again. What are the chances of that? By now I believe that either there is a problem installing Xubuntu on the particular machine I am trying to install it on or that there is a bug in the image which causes the machine I am trying to install on to act weird.
The facts are: I did install Vector Linux, PCLinuxOS and LinuxXP on the very same machine and it worked fine.
I did install from the Xubuntu 8.04.01 alternate CD on other machines and it worked fine.
I guess we gave it a college try and I am ready to call it quits at this point.
Thanks for the input again

---

### Post by zvacet on 2008-09-30
From your last post I can see that you are willing to give up with Xubuntu.It is one more thing you can do.If you still have Xubuntu iso file on your HD download same iso (Xubuntu alternate CD) with torrent and point download to the folder where your iso is.Torrent will just check your iso and replace coruppted files with good ones.After that check md5sum and disc integrity and if all goes well install Xubuntu.

---

### Post by DrScum on 2008-10-01
zwacet,

the problem doesn't seem to be the fact that the .iso is corrupt. The md5sum of the .iso file comes out clear. 
The facts imply that the CD created from the .iso file gets corrupted. 

However, analyzing the posts above it apparently can happen that on one machine the integrity check comes out ok whereas on another machine it doesn't. Thus the integrity check does seem to include the hardware of some sort and in my case I am afraid that the hardware of my old machine doesn't seem to fit together with the Xubuntu 8.04.01 alternate CD. 

Don't worry, I am not giving up on Xubuntu, just for this machine another distro seems to be a better choice.
Thanks for all the input guys, I'll keep you posted in case I find a more satisfactory explanation.

---

### Post by bindkeeper on 2008-10-02
I think I got the same problem. I downloaded the iso image, cheked the md5sum and its okay. But the integrity chek fails.
I spend 5 cd's on that all of them didn't pass the integrity check. I tried to install from that cd's with no good.


So i tried a debian dist from debian.org and it install fine.

I also burned a damn small linux on the same burner and it work fine.

I didn't get a chance to check the xubuntu image on other PC but I tend to think its the image and not the burner.

Right now I'm using the Debian with Gnome but I want a Xubuntu on that PC.

---

