---
title: "Fluxbuntu live CD fails to boot"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by Patb on 2007-11-21
Hi. My Fluxbuntu "Gutsy" live CD fails to boot.  Any suggestions would be appreciated.  

I downloaded the iso image at [http://releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso](http://releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso). Checked the md5sum was correct. Burned the iso image to CD (tried several CDs). Checked my CD drive worked okay with other bootable disks. I'm using reasonably up to date hardware, an LG brand ATAPI CDRW drive, CPU Celeron 2.40GHz.  Other Ubuntu flavours work fine, so it seems to be the iso image file rather than my hardware.  I've done a lot of searching. I can read all the files on the CD - it's just the booting that seems to be missing.  

Is there anything else I should check?  Has anyone else seen this problem? 

Thanks in advance. Pat.

---

### Post by kellemes on 2007-11-21
What do you mean with "fails to boot"?
It's bypassing the disk at all?
Or it hangs somewhere along the line?
Anyway.. you can always try the alternate installCD.. just tick the checkbox at the downloadpage.

Edit: Have you burned the ISO-file? Or have you burned the ISO-image?
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by Patb on 2007-11-21
Thanks for the reply, Kellemes.  
> What do you mean with "fails to boot"?
I mean the boot process assumes the CD is not a bootable CD.  It doesn't hang.  The CD spins a little and then gets bypassed and booting takes place from the HDD.  The BIOS boot sequence is CDROM/Floppy/HDD.  If I put any other bootable CD in the drive it will boot okay, which is why I think my hardware and boot settings are okay.  

And yes, I definitely burned the iso image, not just the iso file.  (Good question though, "Been there, done that..." :))
> You can always try the alternate installCD
Yes, but I would have to use the classic Ubuntu CD (which I have already tried and could use).  As far as I'm aware Fluxbuntu is only available as the "live CD".  It doesn't come in the 'alternate' form.  I would be quite comfortable doing a "manual" install but I cannot get the CD to boot.  I can boot to another system and see the files on the CD but it does not appear to be a "bootable CD".  

Any ideas would be welcome.  

Cheers, Pat.

---

### Post by kellemes on 2007-11-22
Well, to be honest I don't know what's going on here.. :(
I hope someone else can help..

---

### Post by ugm6hr on 2007-11-22
I'm afraid I can't help either, but thought I'd detail my experience.

I haven't tried the latest 7.10 Fluxbuntu, but I had the same problem with Fluxbuntu6.06.  The CD md5 etc was OK, but it wouldn't boot on any computer of mine.

I gave up and used the Alternate Xubuntu instead.  A minimal install may be better for you: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Patb on 2007-11-22
No worries.  Thanks again, Kellemes.  

A minor update:

I created a boot floppy with the "Smart Boot Manager" (sbm.bin) with guidance from [http://ubuntuforums.org/archive/index.php/t-121518.html](http://ubuntuforums.org/archive/index.php/t-121518.html).

By starting boot from this floppy, sbm enabled me to designate the CD drive as the drive to boot from.  The computer then booted as expected from the CD, leading to the start up menu where there is the option to install Fluxbuntu.  (There was no option to 'start' Fluxbuntu by the way, but only to install, check the CD, memory test, etc.  The menu did not look like a "live CD" but an "alternate CD" but I guess that is another issue).  

So, using sbm on a floppy, I can at least cajole my system into booting from the CD but that's not really satisfactory.  The CD is in fact bootable when forced, so why does my system not just boot from this CD like it does from any other bootable CD?  That remains a mystery.  

Cheers, Pat.

---

### Post by Patb on 2007-11-22
I agree, ugm6hr, and thanks for sharing your experience.  I think it might be best to simply do a minimal install from one of the more mainstream Ubuntu variants and build from there.  I find the Fluxbox window manager great myself.  

Cheers, Pat.

---

### Post by louieb on 2007-11-22
I'm 50% at getting the Fluxbuntu CD to boot. P2-400 /384MB ram no go - got a weird flicker at the 1st screen and it refused to   do anything else. P4-2.1GHZ / 1GB memory installed without a hitch. Go figure. Really wanted to try it out on the older slower PC I guess I'll just have to do a server install on that one and add Fluxbox later.  
Did get PCFluxboxOS to install on the P2-400 - its pretty nice and it come with Synaptic too.

---

### Post by Splarz on 2007-11-23
i have the same problem: i was looking for my problem with google when i discovered i wasn't alone ;) i do not want to install fluxbuntu 'cos i have already ubuntu with gnome, xfce and fluxbox: my aim was to test the differences between my fluxbox and that live's environment, which seems to be quiet different... so i would need the live cd!
does anybody know something more?

---

### Post by hey2222 on 2007-11-23
Solution! Well maybe, I don't really know why but it will boot if you burn it to a dvd. I burned two CDs of fluxbuntu and they wont boot, but when i burned it to a dvd it works. Very weird indeed.

---

### Post by kaiju on 2007-11-26
hey, hey2222! :P

thanks for letting us know your experience. however, i must say that using a dvd instead of a cd didn't work for me. fluxbuntu still acts like a regular cd without anything bootable on it. (needless to say that i've been testing many small distros lately and none of them had this problem).

btw. would anyone happen to know who the people behind fluxbuntu are? it's just strange that their site and especially their use of words (i mean that strong taste of marketing) differ so much from what i've seen on other linux-related sites...

---

### Post by Inxsible on 2007-12-14
I was looking for a live cd too. It seems that their installer cd does not get you into the "live" mode.

I wanted to see how it looked before installing it. But I guess I will go with Zenwalk - which I really like too.

---

### Post by breaking on 2008-01-20
> **Patb said:**
> Hi. My Fluxbuntu "Gutsy" live CD fails to boot.  Any suggestions would be appreciated.  

I downloaded the iso image at [http://releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso](http://releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso). Checked the md5sum was correct. Burned the iso image to CD (tried several CDs). Checked my CD drive worked okay with other bootable disks. I'm using reasonably up to date hardware, an LG brand ATAPI CDRW drive, CPU Celeron 2.40GHz.  Other Ubuntu flavours work fine, so it seems to be the iso image file rather than my hardware.  I've done a lot of searching. I can read all the files on the CD - it's just the booting that seems to be missing.  

Is there anything else I should check?  Has anyone else seen this problem? 

Thanks in advance. Pat.Add me to the list.  I can't get the CD to boot either.  I tried different types of media, including DVD's but this live CD just won't boot for me.

---

### Post by josh.on.linux on 2008-01-27
I was expecting a live CD as well, as that's what they talk about on their good-looking but terribly slow website.

I have chosen to test drive *Fluxbuntu* in a virtual machine using *VirtualBox*.  Not quite as hassle-free as a live CD, but still a way to test the OS w/o possible harm to my running system. :-)

Josh

---

### Post by Jeztastic on 2008-02-02
I am having a similar problem but with the minimal ubuntu install someone mentioned in this thread. Any help appreciated!

---

### Post by confused57 on 2008-02-02
The only way I could get the Fluxbuntu cd to boot was by using a Smart Boot Manager floppy:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by djringjr on 2008-02-11
The problem can and has been fixed with a remaster of the iso.  But no one has put the iso up on the official download mirrors.

See [URL="http://ubuntuforums.org/showpost.php?p=4033517&postcount=10"]http://ubuntuforums.org/showpost.php?p=4033517&postcount=10
[/URL]

There is a torrent for this iso though (my torrent program won't work!) 
[http://www.mybittorrent.com/info/1140178/]("http://www.mybittorrent.com/info/1140178/")

If someone could have the fluxbuntu people post this iso instead of the real release candidate one, people would be happier.

Best

David

---

### Post by kaiju on 2008-02-12
confirming what djringjr said. the remaster does the trick, and its easy too, if you follow the instructions from the post.

ive also asked about this on #fluxbuntu at freenode, and ive been told that it cant be fixed in the release candidate.
people who cant get the official iso to work will have to remaster it or download the remasterd iso from here (this is a new york server though, so remastering might be faster)
[http://66.150.224.105/unofficial/](http://66.150.224.105/unofficial/)

---

### Post by louieb on 2008-02-12
> **confused57 said:**
> The only way I could get the Fluxbuntu cd to boot was by using a Smart Boot Manager floppy:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

+1 That how I finally got the CD to boot on my P2-400mHz.

---

### Post by Cariboo1938 on 2008-02-21
Originally Posted by confused57  View Post
The only way I could get the Fluxbuntu cd to boot was by using a Smart Boot Manager floppy:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)
> **louieb said:**
> +1 That how I finally got the CD to boot on my P2-400mHz.
Is it better than downloading the remastered iso?:confused:

---

### Post by confused57 on 2008-02-21
> **Cariboo1938 said:**
> Originally Posted by confused57  View Post
The only way I could get the Fluxbuntu cd to boot was by using a Smart Boot Manager floppy:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Is it better than downloading the remastered iso?:confused:

It's probably a matter of personal choice, I don't believe either method is better than the other...I just happened to have a copy of Smart Boot Manager on floppy that I had used with an older pc.

---

### Post by Cariboo1938 on 2008-02-21
> **confused57 said:**
> It's probably a matter of personal choice, I don't believe either method is better than the other...I just happened to have a copy of Smart Boot Manager on floppy that I had used with an older pc.OK, confuse57 and thanks for the reply. 
I only asked because I didn't know how and where to get 'Smart Boot Manager'.
Maybe it is a good idea to have a boot floppy like that. 
Can you, please, give me an hint how to get it?

---

### Post by confused57 on 2008-02-21
> **Cariboo1938 said:**
> OK, confuse57 and thanks for the reply. 
I only asked because I didn't know how and where to get 'Smart Boot Manager'.
Maybe it is a good idea to have a boot floppy like that. 
Can you, please, give me an hint how to get it?
Glad to help...here's the Ubuntu Documentation for SBM:
[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

I initially made SBM in Windows...rawrite is gui & easy to use.  It might even be easier in Ubuntu:
[http://ubuntuforums.org/showpost.php?p=3330416&postcount=7](http://ubuntuforums.org/showpost.php?p=3330416&postcount=7)

---

### Post by Cariboo1938 on 2008-02-23
> **confused57 said:**
> Glad to help...here's the Ubuntu Documentation for SBM:
[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)
I initially made SBM in Windows...rawrite is gui & easy to use.  It might even be easier in Ubuntu:
[http://ubuntuforums.org/showpost.php?p=3330416&postcount=7](http://ubuntuforums.org/showpost.php?p=3330416&postcount=7)
Hello, I'm still not able to boot Fluxbuntu. I have an older computer with no OS installed. When I try to boot the fluxbuntu7.10-remastered CD I get this message:> Boot from ATAPI CD-ROM:
Grub Loading Failure...
stage 1.5.
Grub loading, please wait...
Error 22
Here ends the boot sequence and nothing more happens!
What could be wrong, any ideas?

Then I tried to get SmartBootManager installed and I tried to follow the instructions as mentioned in the given links above, but I dont know how to get the "sbm.bin" file. The [DOWNLOAD]("http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201") site only shows "btmgr-3.7-1.i386.rpm, btmgr-3.7-1.src.rpm, btmgr-3.7-1.tar.gz, sbminst, sbminst.exe".
Can somebody give me a step by step instruction, please?

---

### Post by confused57 on 2008-02-23
> **Cariboo1938 said:**
> Hello, I'm still not able to boot Fluxbuntu. I have an older computer with no OS installed. When I try to boot the fluxbuntu7.10-remastered CD I get this message:
Here ends the boot sequence and nothing more happens!
What could be wrong, any ideas?

Then I tried to get SmartBootManager installed and I tried to follow the instructions as mentioned in the given links above, but I dont know how to get the "sbm.bin" file. The [DOWNLOAD]("http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201") site only shows "btmgr-3.7-1.i386.rpm, btmgr-3.7-1.src.rpm, btmgr-3.7-1.tar.gz, sbminst, sbminst.exe".
Can somebody give me a step by step instruction, please?
Download the sbminst to your Desktop:
```
cd Desktop
chmod +x sbminst
./sbminst -t us -d /dev/fd0
```

First you need to use the Floppy Formatter program to format your floppy as FAT.


I don't think you have to preface the above commands with sudo.

Added:  I used Floppy Formatter in Dapper to make an SBM floppy, but it appears Feisty & possibly Gutsy don't have this...you can install kfloppy from Synaptic, then use kfloppy to format your floppy with  DOS filesystem.

---

### Post by Cariboo1938 on 2008-02-23
Hello confused57 and
Thank you so much for your fast response.
I FAT-formatted a floppy
I downloaded 41KB sbminst
I changed mod for sbminst 
I executed ./sbminst -t us -d /dev/fd0
and there was no warning or error when executing the commands. 
Although, it seems 
```
./sbminst -t us -d /dev/fd0
```didn't do anything to the floppy...
When I try to boot from the floppy I get this message:
> This is not a bootable disk. Please insert a bootable and press any key to try again...
What did I miss?

---

### Post by confused57 on 2008-02-23
> **Cariboo1938 said:**
> Hello confused57 and
Thank you so much for your fast response.
I FAT-formatted a floppy
I downloaded 41KB sbminst
I changed mod for sbminst 
I executed ./sbminst -t us -d /dev/fd0
and there was no warning or error when executing the commands. 
Although, it seems 
```
./sbminst -t us -d /dev/fd0
```didn't do anything to the floppy...
When I try to boot from the floppy I get this message:

What did I miss?
When I executed ./sbminst -t us -d /dev/fd0, I was asked if I really wanted to install sbm to /dev/fd0 (y,n)?  The floppy drive spun for a little bit...then I received a message sbm installed successfully.  I was then able to boot my pc with the sbm floppy and Fluxbuntu cd inserted...the floppy booted sbm, which allowed me to boot the fluxbuntu cd.  I had no problem installing sbm to floppy on either Dapper or Feisty(had to use kfloppy to format as DOS with Feisty).

Maybe the floppy you used was defective...I'm not sure what the problem is, I would recommend trying it again.  How is your floppy mounted in fstab?

---

### Post by Cariboo1938 on 2008-02-24
I tried it again, using 'kfloppy' to format the floppy (No errors, no bad sectors)
 ....same thing....no reaction to command ./sbminst...

> **confused57 said:**
> 
..............How is your floppy mounted in fstab?
This is fstab for the floppy:> /etc/fstab...
# Optical Devices and Floppy
/dev/hda        	/media/cdrom0   udf,iso9660 	user,noauto               0       0
/dev/hdb        	/media/cdrom1   udf,iso9660 	user,noauto               0       0
**[COLOR="Magenta"]/dev/fd0        	/media/floppy0  auto       rw,user,noauto,exec 	      0       0[/COLOR]**

I think it's OK! 
Or has "user" to be "us"?
How can I check if the file 'sbminst' is OK?
What exactly does ' ./ ' mean or do?

---

### Post by confused57 on 2008-02-24
I found another method to install SBM to floppy that you can try...download the sbm.img from here:
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

Download to your Desktop, then:
```
cd Desktop
dd if=sbm.img of=/dev/fd0
```

Your floppy entry in fstab is same as mine, so that's not the problem.  I suppose the .zip extension was added to the sbminst file when you attached it...otherwise the file looks OK.  I'm not sure why, but you need to preface an executable script with ./ to run it...if you try it without the ./ linux thinks the first entry is a command(which isn't recognized as so).

I don't have the floppy mounted when installing sbm...

Note:  Gutsy & Hardy both have gfloppy(Floppy Formatter), it's just Feisty that doesn't.

---

### Post by Cariboo1938 on 2008-02-24
> **confused57 said:**
> I found another method to install SBM to floppy that you can try...download the sbm.img from here:
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)
Download to your Desktop, then:
```
cd Desktop
dd if=sbm.img of=/dev/fd0
```

Here we are - there we go...!:-\" 
Thank you, confused57, that does the trick!;)

> **confused57 said:**
> I suppose the .zip extension was added to the sbminst file when you attached it... 

Exactly, I changed the name adding the extension .zip to work around the limits for attachments.

> **confused57 said:**
> 
I don't have the floppy mounted when installing sbm...

I had the floppy mounted before I executed the 'dd'-command. 
Otherwise I got a message "input/output error" during the write process....

> **confused57 said:**
> 
Note:  Gutsy & Hardy both have gfloppy(Floppy Formatter), it's just Feisty that doesn't.

What is the exact package name for the Floppy Formatter?
I couldn't find it with the Synaptic Package Manager.

---

### Post by confused57 on 2008-02-24
Glad the dd alternate method worked for you.  Floppy Formatter is in the gnome-utilities package and is already installed...right-click on Applications...select "Edit Menus", click on "System Tools" in the left window pane, then place a check-mark for "Floppy Formatter"(gflopppy) in the right window pane.
This will automatically add Floppy Formatter to the menu...Applications---System Tools---Floppy Formatter.

---

