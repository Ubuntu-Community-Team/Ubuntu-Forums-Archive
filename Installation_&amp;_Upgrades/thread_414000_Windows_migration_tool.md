---
title: "Windows migration tool?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Beliar on 2007-04-19
Hi folks,
I just have downloaded and installed Feisty. First of all, thanks and congratulations to the developers, its one of the best Ubuntu releases and I'm sure, the next will be even better.

However, installed it from LiveCD instead of updating. And I wanted to see how this Windows migration tool works. But although I have a Windows XP Pro partition and also mounted it under /media/winc, it says, that there is no user to import data from. Why that? 

Does it work for anyone??

greets,
Beliar

---

### Post by MGStreak on 2007-04-19
> **Beliar said:**
> Hi folks,
I just have downloaded and installed Feisty. First of all, thanks and congratulations to the developers, its one of the best Ubuntu releases and I'm sure, the next will be even better.

However, installed it from LiveCD instead of updating. And I wanted to see how this Windows migration tool works. But although I have a Windows XP Pro partition and also mounted it under /media/winc, it says, that there is no user to import data from. Why that? 

Does it work for anyone??

greets,
Beliar
Hello there... I have finally decided to take the Ubuntu plunge, and it appears that I am having the same problem: having booted up fine from the Live CD, and being able to access the files on my NTFS Windows partition (only partition I have), the installer's migration assistant reads as follows:

"There were no users or operating systems suitable for importing from."

I still have every intention of firing up Ubuntu (even if it means not using the assistant, and doing it myself!) despite the problem, but I would like to be able to use this assistant if possible.  I'll keep hunting around, however, and if I find any solutions, I'll post them in here.

---

### Post by xflbret on 2007-04-21
Same here. I have Windows XP. I read claims that it has worked for others, but after trying several times with no success I am skeptical of their claims.

Anyway, my NTFS partitions can also be accessed by the LIVE CD, but it's still not working. At first, I thought it was because I had tweaked my XP profiles to be in the c:\users folder rather than c:\documents and settings, so what I did is made a folder named documents and settings and copied my xp profile there, thinking that maybe the programmers or whoever only made it to migrate from documents and settings. Anyway, this was unsuccessful.

I'm sorry to say this, but the migration assistant just doesn't work. There's no way to sugar coat it, it just doesn't work.

---

### Post by MGStreak on 2007-04-21
Well, I found out what *may* have been the culprit in my case: I had the NTFS drive mounted when I first tried to start the install.  I unmounted the drive, and started over... this time it saw the user, and allowed me to import it.  

That being said, the import didn't work out perfectly (not all settings came 'willingly'), but it definitely solved my earlier problem of the 'invisible user.'

Good luck!

---

### Post by cogadh on 2007-04-21
The Migration tool worked fine, in terms of detecting users to import data from. However, once I booted up the new system, none of the imported data I was expecting was there (i.e. none of my Firefox bookmarks, documents, etc.). The Windows migration tool was important, as it was to influence my recommendations to Windows users looking to switch to Linux. Based on what I have experienced so far, I can't recommend Feisty to Windows users looking to migrate onto Linux.

---

### Post by xflbret on 2007-04-21
ok, here's what I tried...

I booted to the windows side, and deleted all my linux partitions. I also ran a chkdsk, and then booted off of my xp cd and ran a fixmbr just to get linux all the way out. i tried it again, and still the migrate tool is useless

i saw one reply to this thread suggesting unmounting ntfs drives, but mine were already unmounted. so, i tried mounting them. also no effect...

this seems to be just a pipe dream

---

### Post by daller on 2007-04-21
> **cogadh said:**
> The Migration tool worked fine, in terms of detecting users to import data from. However, once I booted up the new system, none of the imported data I was expecting was there (i.e. none of my Firefox bookmarks, documents, etc.). The Windows migration tool was important, as it was to influence my recommendations to Windows users looking to switch to Linux. Based on what I have experienced so far, I can't recommend Feisty to Windows users looking to migrate onto Linux.

Come on you guys! - This is the first release with the migration tool built in... Please give it some time to mature!

...and of course you can recommend Ubuntu to Windows users! - A simple backup of data will do the migration trick!

---

### Post by lotacus on 2007-04-21
well i'm sure it's because there were very few if not any people actually testing this feature.

---

### Post by riomx on 2007-04-22
Allright, so what's the general consensus to at least get Ubuntu to recognize that there is an OS or User ?

Leave the drives unmounted and just let it detect Windows XP ?

I'm going through the same problem here.  I can resize my partition using the Ubuntu installation, but after that and on the next step, no OS is detected whatsoever

---

### Post by Jeroensum on 2007-04-24
I had the same problem, a box with Windows XP on it, and a Feisty Live CD. During the Migration 
Wizard no profiles showed up... *dangit*.

After pondering a bit I took my trusty terminal emulator and started poking around. After fireing up 
vim several times to checkout some debuglogs and other files I came to the conclusion that de wizard 
did try and mount the correct drive and partition but was looking in the wrong place. Amongst others it 
tried to access the /users directory. Hmmm...
I apt-got the ntfs-3g package and mounted the /dev/hda1 with RW permissions and moved the profiles I 
wanted to migrate from /dev/hda1/Documents and Settings/  to a new directory users.
I unmounted the drive and tried again... BINGO! there were my precious profiles ready to migrate. 
After the migration all seems fine, in firefox I found my bookmarks, even the dreaded 'teletubby' 
background was in place!

**Here are the steps:**
```

1.) Fire up live CD 

2.) Open up a terminal

3.) sudo gedit /etc/apt/sources.list and remove all comments (#) in front of the 
repositories, and save the file.

4.) sudo apt-get ntfs-3g

5.) mkdir /mnt/win

6.) ntfsmount /dev/<disk and partition number here> /mnt/win

7.) mkdir /mnt/win/users

8.) mv /mnt/win/Documents and Settings/<userprofile here> /mnt/win/users/

9.) umount /mnt/win

10.) start ubiquity from the commandline wih the new-partitioner switch like this:  ubiquity --new-partitioner

11.) after the setup is done do NOT reboot

12.) mount the disk in step 6 again and move the profiles from step 8 back to the 
Documents and Settings folder. Else Windows might throw a tantrum not finding the
profiles.

When booting to Windows you might get a screen that states Windows needs to
perform a checkdisk, let this thing run! Do not abort it since ntfsmount might have
changed a few things Windows can't handle. The checkdisk will niceley fix this.

**UPDATE
I've been doing a couple of these now and the results vary. With Windows XP SP1 all of the above steps are needed. 
When you run Windows XP Sp2 is probably enough to just start ubiquity with the --new-partitioner switch and leave the profiles in the Documents and Settings directory.

==========================================================

Alternativly you can do this in Windows, doing this in Windows has a few advantages and is
probably cleaner but since we're on a Linux forum I tried to keep things linuxy  ;-)


```

Hopefully this helps some ppl out!

---

### Post by riomx on 2007-04-25
Even after enabling the universe repositories, ntfs-3g can't be found as a package to install

---

### Post by Jeroensum on 2007-04-25
Did you run 'apt-get update' ?

---

### Post by riomx on 2007-04-26
> **Jeroensum said:**
> Did you run 'apt-get update' ?


Yeah, it just says "E: Invalid operation ntfs-3g"

---

### Post by riomx on 2007-04-26
Never mind, it worked after I used "sudo apt-get install ntfs-3g"

I can mount drives, but once again, it can't find any users or operating systems to import from.

And since I'm running the Live CD, I'm not going to be able to copy or move my user files.

I give up :D

---

### Post by riomx on 2007-04-26
I don't even really need my Windows settings, but I figured that if Ubuntu could see my Windows installation, I may have a safer chance of dual-booting.

But, if I can set up Feisty and XP to dual-boot, I'm fine with that.

---

### Post by Beliar on 2007-04-26
Well I dont need it really, I can copy my firefox bookmarks via console, but I just wanted to know if it works. And it should work if its part of the official ubuntu installation.

Could it be, that the program is looking into specific folders like C:/(or actually /media/windows or whatever/ 
C:/Documents and dontknow/user/ ? Because in the german version these folders have different names. That would be an explanation. Though kinda cheap...

---

### Post by Jeroensum on 2007-04-26
Even if your profiles aren't detected Ubuntu should detect your Windows installation, this has worked for me since Warty.

After mucking around for a bit I've also been able to do the migration manually, sort of.

After a normal install I can mount windows partitions and import *.pst files (Outlook mail and contacts) with readpst, this turns the *.pst file into an mbox file 
and converts  the contacts into Vcards.  The bookmarks from IE can be imported with some Firefox plugins or can be moved manually. All other files 
can also simply be moved. After getting all the files I reformat the partition to ext3 and mount it (edit fstab) as a regular drive and delete the windows entry from grub.

I agree with Belair on the fact that this migration wizard needs more work. I think that they could have done a better job by not integrating it now but in the next release.
It defenitly needs some development. 

I can't see any language problems in the folders being detected, I've done a dutch and an english setup and the scanned folders seem te be the same 
and should correspond to the folders on the windows parition. Strangeley enough I've now also seen a system which had multiple windows installations, at first 
none of them were detected. 
It seems that the thing here was the detection of the third part of the string  :windows:chain  which alters to a subsequent number when more than one installation is detected. When all three were unmounted and all three partitions were scanned it found:
-:windows:chain
-:windows1:chian
-:windows2:chain
None of them were detected properly... 
After mounting 2 of the three(so they would not be scanned) the third was reckognized and I was able to import profiles...

---

### Post by tashammer on 2007-05-31
i believe that the problem lays with the NTFS. If you were to change the file system back to System FAT32 then the matter should sort itself out. There again i would also check elsewhere that what i said is correct as a matter of verification.

---

### Post by deeZee on 2007-06-10
My Win XP partitions are FAT 32, yet the migration assistant never finds my XP profile.  Actually, it did find my profile once, but it didn't migrate anything.

---

### Post by quini on 2007-08-20
Hi!

Can the windows migration tool be run from the HD once the system is installed, to import settings from other windows users?  If so, how?

TIA  :)

---

### Post by Niniel on 2007-10-05
This is still not working (7.10 B5), same thing - does not detect an installation (when installing from live CD).
Curiously enough, later, during the installation, it complains that it can't migrate anything because it could not unmount a partition. 
If I ignore the error and continue, the installation progresses. But the one time I went back the installation came to a silent yet still complete halt. 

Odd tool. :)

---

### Post by maybeway36 on 2007-10-05
It just was made for feisty, so it's still really new. It did detect my PCLinuxOS partition once, so that's pretty cool.

---

