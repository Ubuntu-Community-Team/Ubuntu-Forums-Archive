---
title: "reinstall 10.04 Lucid Lynx"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Chuck_N on 2010-05-15
I upgraded from 9.10KK to 10.04LL recently. The process did not go well. 
I was first instructed to update KK, which I did. The update and subsequent 
upgrade had various difficulties, the specifics of which I do not recall.  10.04 ran,
with various errors and abnormalities, for a couple days.

I have a Compaq Presario, SR1503WM with 750 meg of RAM. I normally boot to Ubuntu
on my primary harddrive, but can redirect to a Win2K boot from the other drive.
I'm in Windows now, sending this.

If I do a normal boot now, to Ubuntu, and select FF or Opera, I get
"Could not Locate Remote Server". 
It suggests I uncheck "Work Offline". I do and this still gets me  nowhere.

I went to System/Admin/Network Connections and all of the tabs were  empty.
In the WIRED tab, I clicked on ADD and a new  WiredConnection1  was  established,
and,after reboot,  is still there, but it does nothing. 

I have a cable connecting me to the modem, haven't tried to install  wireless yet.
This has been sufficient for months, and as I said, still works for  Windows.

I think I should go ahead and ReInstall 10.04LL. I upgraded without an  install disk. 
No idea how to REinstall. I'm thinking the only way
will be to download the installer to windows desktop, build an ISO disk, and use it to
install. 

Any suggestions on what I should do?

---

### Post by Catharsis on 2010-05-16
Just download the LiveCD and see how it works with your hardware. If you don't see any problems, backup your data and install it over the broken Lucid.

---

### Post by Chuck_N on 2010-05-16
okay, I set my computer to download a version of 10.04LL this morning.
got the job done. Now I go back and look and see it was a BETA from a couple
months ago. Okay, it's in the trash.

now I plan to download  
[ubuntu-10.04-desktop-i386]("http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.iso")

from the Ubuntu site.

The plan is to build the liveCD and later to install.

My question is:  since I have two harddrives, and I'm operating now
on the _alternate_-boot drive, win2k, if I download the iso and use it to
build the CD, then later when I boot with the liveCD, will I be able to
decide to install 10.04LL on the _other_ drive, the primary boot drive, 
currently holding a crippled  9.10KK-upgraded-to-10.04LL ??????

I can hardly believe I was able to phrase that paragraph; Remember, I'm 
a newbie with Linux/Ubuntu.

-Chuck_N

---

### Post by Catharsis on 2010-05-16
Hah, well done. You sound like a veteran! :P

Before you burn the iso, make sure you check that it was downloaded correctly:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

For the hard drives-- yes you can install Ubuntu onto either drives. 

If you want, you can actually remove the Windows harddrive before you boot the LiveCD-- then it'll definitely not install it there! You can also try disabling the Windows harddrive in BIOS, but this is a bit too techie for both of us, I think.

If you can't do either, make sure you check which harddrive is which while in the LiveCD so you can install to the right one (i.e. sda, sdb, sdc, etc):
```
sudo fdisk -l
```
The NTFS will be Windows; Linux will be Lucid.

---

### Post by Chuck_N on 2010-05-16
[COLOR=Red]> **Catharsis said:**
> Hah, well done. You sound like a veteran! :P

Before you burn the iso, make sure you check that it was downloaded correctly:[/COLOR]> **Catharsis said:**
>  [COLOR=Red]
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)[/COLOR] [COLOR=Red]

For the hard drives-- yes you can install Ubuntu onto either drives. [/COLOR] [COLOR=Red]

If you want, you can actually remove the Windows harddrive before you boot the LiveCD-- then it'll definitely not install it there! You can also try disabling the Windows harddrive in BIOS, but this is a bit too techie for both of us, I think.[/COLOR] [COLOR=Red]

If you can't do either, make sure you check which harddrive is which while in the LiveCD so you can install to the right one (i.e. sda, sdb, sdc, etc):[/COLOR] [COLOR=Red]
```
[COLOR=Lime]sudo fdisk -l[/COLOR]
```[COLOR=Lime]The NTFS will be Windows; Linux will be Lucid.[/COLOR][/COLOR]

I find that quite complicated, but I think I can do it, with the exception of the green stuff, which I cannot make sense of.  Sounds like the easy way is to disconnect the secondary boot drive; no problem    
I just checked out the MD5SUM link. That is a super-complicated mess too. No way will I try that tonight; I need SOME sleep before fishing at 6am. 

So, it's checksum first; if okay, use the ISO to build the CD; then bootLive and check out the operation;  then, later, use the LiveCD to install 10.04LL on the boot drive with the secondary disconnected. Right? Whoops, if I install without the secondary in place, will I be able to get a secondary boot later?
-Chuck_N

---

### Post by Catharsis on 2010-05-17
MD5SUM is just a way to check that the file downloaded correctly, i.e. didn't get corrupted or anything. If the hash from the one you downloaded matches the hash that Canonical gives as the correct one, then it's fine.

Yeah just disconnect the Windows harddrive. Easy fix.

---

### Post by Chuck_N on 2010-05-17
if I install without the secondary connected, will I be able to get a  secondary (Windows) boot later?

---

### Post by Catharsis on 2010-05-17
Hmm, not sure. Probably not, now that I think of it. Good question.

---

### Post by Chuck_N on 2010-05-17
okay, I finally got a good download of the ISO file (the third one)
and confirmed with  MDSums.

Now I need to find a program to write to CD which works on win2K. I think I can
do that okay.

Why would I want to set up a partition, or do formatting, as indicated before:
     [COLOR=Lime]Code:[/COLOR]
     [COLOR=Lime]sudo fdisk -l[/COLOR] 
[COLOR=Lime]The NTFS will be Windows; Linux will be Lucid.[/COLOR]


[SIZE=2]I am totally lost on this......[/SIZE]

                                                                                                  
                                                                        [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9312189")

---

### Post by Catharsis on 2010-05-17
> **Chuck_N said:**
> Why would I want to set up a partition, or do formatting, as indicated before:
     [COLOR=Lime]Code:[/COLOR]
     [COLOR=Lime]sudo fdisk -l[/COLOR] 
[COLOR=Lime]The NTFS will be Windows; Linux will be Lucid.[/COLOR]

That was just to tell you which drive was which, so you don't accidentally install Ubuntu over the Windows drive instead of the broken Lucid one. It should be pretty intuitive in the installer though. Just make sure you backup first.

---

### Post by Chuck_N on 2010-05-17
okay, I got the CD running; it feels solid, looks good. Got to GOOGLE search and email fine.
Tried a few games and applications. 

now how do I go about backing up what is on  sda  before I install to it from the CD?

---

### Post by Catharsis on 2010-05-17
You'll need an external harddrive, CD, or some other external media. Or you can look into Ubuntu One. Then just drag-n-drop what you want to keep to the external media.

P.S. What's sda? Is that the Linux hdd or the Windows one?

---

### Post by Chuck_N on 2010-05-17
no, SDA is my primary boot drive, on which I had a working Ubuntu.

I DON't want to intall to the windows drive, SDB


When I install to SDA will it wipe out everything there,
and I will then have a  Ubuntu boot drive  identical to what I see now 
          when I boot from the CD?

---

### Post by Catharsis on 2010-05-17
Most likely yes. There's a very small chance that it'll act differently once you install it, but that's very unlikely.

The installer will give you options of how you want to install Lucid onto sda. If you choose to use the entire drive, it'll erase everything on sda and install Lucid onto it.

P.S. There are reports floating around the forums from people saying they can't boot into Windows after installing Lucid. I haven't looked at them because I don't dual boot, but you might want to look into that issue and see if it will affect you/if there are any fixes for it before you install.

---

### Post by Chuck_N on 2010-05-17
I have emails with   .pps  and   .jpg   attachments.
they open fine.

i have some with   .wmv  attachments  and some with  .htm  attachments
which have called for multiple plugins
which I have done
and they still do not work.

I should be able to do that while running from CD, should I not ?

---

### Post by Catharsis on 2010-05-17
The .htm files shouldn't need a plugin; they're just HTML files, which should open in the browser.

.wmv should play with the proprietary multimedia codecs installed. sudo apt-get install ubuntu-restricted-extras.

---

### Post by Chuck_N on 2010-05-17
The  .htm  linked to a page with a video on it; the videos are the problem.

---

### Post by Catharsis on 2010-05-18
Installing ubuntu-restricted-extras will solve that too. Probably just needs Flash.

---

### Post by Chuck_N on 2010-05-18
> **Catharsis said:**
> The .htm files shouldn't need a plugin; they're just HTML files, which should open in the browser.

.wmv should play with the proprietary multimedia codecs installed.
         [COLOR=Red]sudo apt-get install ubuntu-restricted-extras[/COLOR].

I submitted this, as it stands.   response:  [COLOR=Red]ubuntu-restricted-extras  [COLOR=Black]could not be found.[/COLOR] 

[COLOR=black]Also I installed QuickJava and restarted Firefox, but the program still won't run and says I need Java

I still have no sound.

Also, cookies are apparently non-operational, still.  I have to sign in to everything every time I restart.  Sites that I've
been to multiple times still do not appear in the dropdown when I hit the first letter.  

I'm not doing well at all.


[/COLOR]   [/COLOR]

---

### Post by Catharsis on 2010-05-19
System->Administration->Software Sources. Make sure "Main", "Universe", "Restricted", and "Multiverse" repositories are all checked.

---

### Post by Chuck_N on 2010-05-26
okay, I have time to work on this again..........

I think I'm ready to try to install the 10.04 on my drive A from the liveCD.
The options I get are a) Install side by side   (which I do not want)
                           b) Erase & use entire disk  (which I do not want)
               and  c) specify partitions.
When I use  c)   it shows  sda1(39 gig)  (which I think is where I want to install)
                           and  sda5 (723 meg) swap partition (which I think is responsible for booting to win2K)
                          and sdb1  ntfs   which I assume is my win2K drive.


Attempting to install to sda1,  I get   No Root File System is Defined  and no real option to do anything
                                                                     about it, that I can see.


I attempted to install to  sda5  and to  sdb1  and got the same error message on  each.

                                        Here I am............. stuck again.

---

### Post by Catharsis on 2010-05-26
sda1 and sda5 are the partitions on your linux harddrive. The swap space is for pagefiling (virtual RAM). Ubuntu uses a separate swap partition, which is what sda5 is.

Under the manual install, check the box under sda1 that says "format". This will wipe your old Ubuntu install and reinstall Lucid onto it. Make sure the mount point for this is "/".

I don't think you have to do anything with the swap partition. Just make sure it's marked as "swap" (I think it's a dropdown menu or something).

You'll get to review your changes, and then install. Just make sure you don't touch anything in sdb (your Windows harddrive).

I think that's how it goes. I'm not super familiar with the installer though, so don't be surprised if it doesn't look 100% like what I said.

---

### Post by Chuck_N on 2010-05-27
I started an install from the liveCD.
before I can check FORMAT  and then indicate mount point
I have to make a choice between
ext4    ext3    ext2    reiserts    jfs    xfs    fat16     fat32

I don't have a clue......which one?

---

### Post by Catharsis on 2010-05-28
> **Chuck_N said:**
> I started an install from the liveCD.
before I can check FORMAT  and then indicate mount point
I have to make a choice between
ext4    ext3    ext2    reiserts    jfs    xfs    fat16     fat32

I don't have a clue......which one?

ext4.

---

### Post by Chuck_N on 2010-05-28
I spent a half hour trying to find info on that
so I wouldn't have to ask

.......... I seem to run into so many non-intuitive things
that I can't work through on my own.

so what's   ext4    and why do I choose it ?

Jeez, I'm so frustrated; after all these months, I'm sitting here yet
with a crippled system
running from a new liveCD  'cuz my Ubuntu can't get to the web
and my Windows is now kaput.

Okay, here goes, I'll try to reinstall from the liveCD

---

### Post by Chuck_N on 2010-05-28
okay, much good news

  
reinstall from liveCD worked flawlessly. It feels good to be able to boot into Ubuntu again
and have full capabilities and speed, unlike the liveCD boot.   
   I WAS able to identify the  secondary (Windows) boot drive and have the option to boot there
 (although Windows needs repair and I have no win2k disk with which to fix it.  But I digress......)

It took a while but I got the sound and video working. 

I'll let you know what else I find..............

---

### Post by rtimai on 2010-08-26
This is the end of the thread? Just wanted you guys to know that I read through the whole thing from beginning to end, and it READS LIKE A SUSPENSE STORY, haha! I'm glad it turned out at least semi-okay, able to boot into both Linux and Windows. 

I must say, posted information about partitioning options when installing or attempting to re-install Ubuntu LUCID is fragmentary and conflicting. I'm looking for records of actual experiences, like this one. 

Myself, I was considering creating a separate logical partition and then moving the /home folder to it. Now I hear that with single HD systems there is no advantage to doing so, and that (told by an Ubuntu installation developer) that the new Lucid LiveCD allows reinstalling Ubuntu over an existing Lucid installation, and that unchecking the Format Partition option will preserve user folders and settings -- similar to Windows re-installation behavior. Yet the OFFICIAL documentation does yet not reflect this new information. This whole situation is very confusing.

Anyway this thread was a good story, and I'm glad it turned out happily.

---

### Post by Chuck_N on 2010-08-26
[COLOR=Magenta]> **rtimai said:**
> This is the end of the thread? Just wanted you guys to know that I read through the whole thing from beginning to end, and it READS LIKE A SUSPENSE STORY, haha! I'm glad it turned out at least semi-okay, able to boot into both Linux and Windows. 
I must say, posted information about partitioning options when installing or attempting to re-install Ubuntu LUCID is fragmentary and conflicting. I'm looking for records of actual experiences, like this one. [/COLOR]> **rtimai said:**
>  [COLOR=Magenta]
Myself, I was considering creating a separate logical partition and then moving the /home folder to it. Now I hear that with single HD systems there is no advantage to doing so, and that (told by an Ubuntu installation developer) that the new Lucid LiveCD allows reinstalling Ubuntu over an existing Lucid installation, and that unchecking the Format Partition option will preserve user folders and settings -- similar to Windows re-installation behavior. Yet the OFFICIAL documentation does yet not reflect this new information. This whole situation is very confusing.[/COLOR] [COLOR=Magenta]
Anyway this thread was a good story, and I'm glad it turned out happily.[/COLOR] 

A suspense story, huh?   You should read my thread
_Computer freezing up_  which now has  4553 views and counting....
It's a complete novel.
130 entries and I still have gotten nowhere in preventing blackouts
I've pretty well decided that it's a video thing, not a processor freeze up,
but have not yet found a solution.

---

### Post by rtimai on 2010-08-26
Chuck_N, I searched the forums for your username and didn't find a thread titled "Computer freezing up." Feel free to post the link here.

---

### Post by Chuck_N on 2010-08-26
> **rtimai said:**
> Chuck_N, I searched the forums for your username and didn't find a thread titled "Computer freezing up." Feel free to post the link here.


Looking for some light reading, huh ?  No idea why you didn't find it,
but let's not start a new thread over it.   8-)

[URL="http://ubuntuforums.org/showthread.php?t=1442684"]
http://ubuntuforums.org/showthread.php?t=1442684[/URL]

that should do it.

---

