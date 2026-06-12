---
title: "EVERY Single North American Mirror is Corrupt?"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by Dauphinfay on 2006-07-27
Ever Since Dapper came out I have been attempting to download and install it. However, every single time I attempt it I am faced with some kind of issue that initially appears as though the burn process didn't work properly or that maybe the download was corrupt. WTH?? So here I am asking if there are others that are experiencing this while I take a precious amount of my time to reinstall Breezy and look to suffer through a long upgrade process. I have downloaded other distros and burned them during this whole process so I highly doubt the problem is with the burn. Quincidentily, the "Check CD" option never completes with Dapper so I have no idea what's wrong. Any clues guesses or winning lottery tickets are appreciated.

---

### Post by catlett on 2006-07-27
All you have to do is run a mid5sum check on your download to verify if the downl;oad was successfull or corrupted.
These are the md5sums for Dapper
> df03811bfc9f2a73672887a36d531965  ubuntu-6.06-alternate-amd64.iso
b2e9120f06d70cc076c1852c6c04654e  ubuntu-6.06-alternate-i386.iso
12bd53a48d7afbcfb0eae6794a1ac02f  ubuntu-6.06-alternate-powerpc.iso
722b8b4a75f977a76a722d4a2b071b19  ubuntu-6.06-desktop-amd64.iso
e2e5e0bfb2edffd2ce02dd77bda4558e  ubuntu-6.06-desktop-i386.iso
410d766d75a3afaa7f04c0c7dbdfd8da  ubuntu-6.06-desktop-powerpc.iso
02772b8b3461c246a2154aa6e699335b  ubuntu-6.06-server-amd64.iso
4c7c835d244453b9a29d397e5cd973fd  ubuntu-6.06-server-i386.iso
c1f9c3dc78572bc2ce76d44776949fcc  ubuntu-6.06-server-powerpc.iso
82da246064785adb7b87e5aa0cb5764c  ubuntu-6.06-server-sparc.isoAfter you download the iso, youy run this command to get the md5sum from the download
```
md5sum /path/and/name_of_iso
```When you press enter the terminal will print out the md5sum of your iso. Match it to the correct version's md5sum and you will know if the download succeeded.

You can also order Ubuntu installation cds for free. Just go to ship_it and request a cd or multiple cds and they will send them to you for free. [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by Herman on 2006-07-27
Yes, I agree with catlett and also, remember to read the manufacturer's specifications for the  blank CDs you buy, and buy a good brand. I seem to have better luck using CD-RWs for software, I don't know why. 
The burn speed of the CD is worth checking, and be sure to set your computer to burn at the slowest speed possible. It will only take a little bit longer.
Watch how you store and handle your CDs too. (No scatches / fingerprints/dirt).
CD drives need cleaning sometimes too and they probably vary in quality as well. Probably they would be affected how well or poorly other parts of the machine (like the power supply) are working as well.
Remember, even a small error like a puctuation mark missing is enough to cause unpredictable operating system problems. 
As long as the operating system installs okay though, you can usually just open 'Synaptic Package Manager' and click on 'Edit'>'Fix Broken Packages'. A lot of times that will fix it, so even if you do install from a less than perfect CD, you can still install Ubuntu.
These are just a few ideas that I hope might help.
 All the best with it, Regards, Herman :D

---

### Post by Dauphinfay on 2006-07-28
Unfortunately, I never tried that since I am using a mac running osx for the download and burn. I still say it is something to do with the mirror since I downloaded the iso from Australia right after I posted yesterday and that worked flawlessly. But just for grins I think that I will try and DL from the north american mirrors later and check the md5sum.

---

### Post by catlett on 2006-07-28
> **Dauphinfay said:**
> Unfortunately, I never tried that since I am using a mac running osx for the download and burn. I still say it is something to do with the mirror since I downloaded the iso from Australia right after I posted yesterday and that worked flawlessly. But just for grins I think that I will try and DL from the north american mirrors later and check the md5sum.

You mkay very well be right. I suggested the md5sum check as a way to find out if it is corrupted or not, not as a suggestion that you are incorrect. Stranger things have happened and you may have just been the first person to post about this one. I would assume the majority of downloads are for i386/amd and there might be an issue with the powerpc download but noone has reported the issue.
So if you don't mind the extra effort, it would be great if you could verify the md5sum of your download.
In mac osx' disk utility, there is a menu option for md5sum checks. It is listed under images in the windows menu titled checksum. Mac is so much better than windows. In XP Pro you can't even burn an iso with the XP cd writing software but in Mac OSX not only can you burn but you can verify md5sums!
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/diskutility00.png[/IMG]

---

### Post by Herman on 2006-07-28
I'm glad you succeeded in getting a good .iso download, Dauphinfay. I don't know how to run an md5sum from a mac, but I imagine there would be a way to do it somehow. EDIT: Oh, catlett has already posted that, thanks, catlett! :D
In Ubuntu it is very simple to check md5sums, but for the information of others possibly reading this, if you don't have Ubuntu installed yet, and you have downloaded the .iso in Windows, you can either use the Live CD to check the md5sum, or install a small app in Windows to do it for you.

1) Use a Ubuntu  or Knoppix live CD and mounting the partition contianing the .iso with that. You would boot the Live CD and open a terminal and mount the Windows partition, for details on 'mounting', [click here]("http://www.users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop").
 Find the path for the .iso and run the md5sum from the live CD. Then verify the .iso in a similar way to what is explained [Here.]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Checking_the_.iso") 

2) This way is easier for the average Windows user who has not had time to acquire any Linux abilities yet. You can download and run [MD5summer]("http://www.md5summer.org/")
For a detailed how-to with illustrations, [*Click Here.*]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Checking_the_integrity_of_your_.iso_in_Windows") 
There are many similar apps available for Windows users.

I could be something to do with the mirror. We do seem to get the same problem here in Australia too sometimes. Often downloading the same file again from the same site will result in a good md5sum, but sometimes I see the same bad md5sum repeated. If the same md5sum is repeated, I think it is that likely the mirror itself has a corrupt copy. If I get a different (or hopefully correct) md5sum after re-trying the same download, I don't know what it is that could have caused a problem. I may be being superstitious, but I think I have better luck when I download at night while I am not using the computer. I just think maybe doing things with the computer at the same time as it's copying might sometimes affect the smooth copying of the download. It shouldn't really, so maybe I'm being illogical to think that.
Regards, Herman :D

---

