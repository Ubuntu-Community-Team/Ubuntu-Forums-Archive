---
title: "Will Ubutu 10.04 HDDinstallation delete only the old win7 or the complete data ofHDD?"
date: 2015-02-11
forum: Installation &amp; Upgrades
---

### Post by ekp0001 on 2015-02-11
Hi

Instalation menu has a contradicitive definitions:
1. Delete and use complete HDD (500GB)

2. Win 7 (loader) 85,9GB, Windows Vista (loader)13,8 GB, Windows Vista (loader)108MB will be deleted and Ubuntu 10.04 will be installed

1. sounds like complete deletion at least I am not sure if my 485 GB data of the old Win7 HDD will be deleted too. 

However, I also can choose manual fixing partitions, but there are 4 partitions: /dev/sda1 ntfs 208MB occupied 69MB, /dev/sda2 ntfs 486GB occupied: unknown, /dev/sda3 ntfs 13.8GB occupied 11,6GB,  /dev/sda4 fat 32 108MB,occupied: 33MB. For each I can activate formatting select for unknown filesystems or that a partition will not be used.

When formatting (how?) everything except , /dev/sda2 ntfs 486GB - this must be the actual data form the Win 7 HDD, 
I do not now what to do?   Any help?

Should I use a certain partition as swap file? How big?  Or does UBUNTU do this automatically?

Regards

---

### Post by kansasnoob on 2015-02-12
First of all you don't want to install 10.04 because the desktop version is already EOL and even the server version will be EOL in just a couple of months:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I'd recommend trying your preferred flavor of Trusty (14.04) first and once you've created the live media give the live desktop a try, then while running the live DE use Boot Repair to create a boot info summary:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not run the recommended repair, just create a summary and post the URL here so we can accurately see what your current partitioning scheme looks like.

---

### Post by ekp0001 on 2015-02-12
> **kansasnoob said:**
> First of all you don't want to install 10.04 because ...

thank you
Ubuntu 10.04 was great, but from the day I upgraded to ubuntu 12.04 my notebook became nearly unusable. Extremely often and slowly HDD accesses occurred, that forced me to wait, stopped me to use it and finally damaged the HDD.  Only one application in one window, e.g. browser, did work, but not more. I fear that my slow hardware (ULV Celeron 1.4 Ghz single core with 1GB RAM) did not fit to newer Ubuntu versions. Not right?

---

### Post by ekp0001 on 2015-02-12
I did not find any hardware requirements for the UBUNTU versions ... :-(  so this was my guess.

---

### Post by sudodus on 2015-02-12
There are several flavours of Ubuntu with different desktop environments but the same engine under the hood.

Even if we like Ubuntu 10.04 LTS, we must accept that it has passed end of life. The new long time support release, 14.04 LTS is also quite nice. You should try a flavour with a light or ultra light footprint for an old computer.

Lubuntu - ultra light footprint
Xubuntu - medium light footprint
Ubuntu Gnome - medium light footprint

standard Ubuntu - more eye candy but heavier footprint
Kubuntu - more eye candy but heavier footprint

See the following links 
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it

Old hardware brought back to life
[/URL][URL="http://ubuntuforums.org/showthread.php?t=2230389"]
[/URL]

---

### Post by sudodus on 2015-02-12
> **ekp0001 said:**
> I did not find any hardware requirements for the UBUNTU versions ... :-(  so this was my guess.

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will make it possible to give relevant advice about versions and flavours.

---

### Post by ekp0001 on 2015-02-12
Thank you for you great advice :-)
 My 5 years old BELINEA note book 14"came originally with UBUNTU 10.0 installed, 
 has ULV Celeron 1.4 Ghz single core 
with 1GB RAM, 
internal Graphic but already with HDMI support
Wifi ? Sorry, the specs were on the broken harddisk. no information, except that it did work well with ubuntu 10.04

This slow Celeron did work excellently: My large screen had a HD TV-video from USB-TV-Stick via HDMI and the same time a Youtube video did run on the notebook screen.

---

### Post by ekp0001 on 2015-02-12
Why actually the  ubuuntu 12.04 upgrade did so extremely slow down, if a newer system should not be the reason? I couldn't expect another reason than the new system. That is why I fear any other system could make problems.
... and why should it be not good to use an old ubuntu?  Its only my light-weight freetime- and UBUNTU-Testing computer.  And I hate any change in OS or software.

---

### Post by ekp0001 on 2015-02-12
May be I should come back to my first posing: 

1. Delete and use complete HDD (500GB)

This does not necessarily mean that complete HDD is deleted. I just wanted to make it sure, because the last back-ups are somewhat old.

---

### Post by sudodus on 2015-02-12
> **ekp0001 said:**
> Hi

Instalation menu has a contradicitive definitions:
1. Delete and use complete HDD (500GB)

This option will delete the partitions and file systems and overwrite with the new Ubuntu. But it is no security shredding. Using for example the recovery tool PhotoRec, someone might be able to read some files from the previous system.
> 
2. Win 7 (loader) 85,9GB, Windows Vista (loader)13,8 GB, Windows Vista (loader)108MB will be deleted and Ubuntu 10.04 will be installed

1. sounds like complete deletion at least I am not sure if my 485 GB data of the old Win7 HDD will be deleted too. 

However, I also can choose manual fixing partitions, but there are 4 partitions: /dev/sda1 ntfs 208MB occupied 69MB, /dev/sda2 ntfs 486GB occupied: unknown, /dev/sda3 ntfs 13.8GB occupied 11,6GB,  /dev/sda4 fat 32 108MB,occupied: 33MB. For each I can activate formatting select for unknown filesystems or that a partition will not be used.

When formatting (how?) everything except , /dev/sda2 ntfs 486GB - this must be the actual data form the Win 7 HDD, 
I do not now what to do?   Any help?

Should I use a certain partition as swap file? How big?  Or does UBUNTU do this automatically?

Regards

Do you want to keep Vista? Do you want to keep some persional data from the previous file systems?

It is probably better to create a new swap partition with a size suitable to how you intend to use the computer. I would suggest 1.2 GB.

---

### Post by sudodus on 2015-02-12
> **ekp0001 said:**
> Why actually the  ubuuntu 12.04 upgrade did so extremely slow down, if a newer system should not be the reason? I couldn't expect another reason than the new system. That is why I fear any other system could make problems.
... and why should it be not good to use an old ubuntu?  Its only my light-weight freetime- and UBUNTU-Testing computer.  And I hate any change in OS or software.

Ubuntu 12.04 LTS was developed for new computers, and needs more 'horsepower' that you get with your old Celeron CPU and needs more RAM than 1 GB. A lot of the 'horsepower' is needed for the desktop environment (the graphics), and there are several desktop environments that work well with less than standard Ubuntu needs. Lubuntu 12.04 has already reached end of life, but there are community re-spins (based on Ubuntu 12.04 LTS), that offer support until April 2017, for example ***Bodhi*** and ***LXLE***.

I would suggest these re-spins as the second option. ***First try the newer Lubuntu and Xubuntu 14.04.1 LTS***. If problems with the graphics driver or some other driver, than try those re-spins based on Ubuntu 12.04 LTS.

We can look at your graphics chip later on (but since it is on-board, we can guess that it is an Intel chip).

After end of life, the old Ubuntu version is not supported. When security holes are discovered, nobody will make any patch, so your system will be vulnerable to attacks via the internet. If you do not connect to the internet, it can be OK. Furthermore, it will be very difficult to install programs, because the repositories are no longer maintained at the Ubuntu web servers and mirrors.

---

### Post by sudodus on 2015-02-12
> **ekp0001 said:**
> May be I should come back to my first posing: 

1. Delete and use complete HDD (500GB)

This does not necessarily mean that complete HDD is deleted. I just wanted to make it sure, because the last back-ups are somewhat old.

Editing partitions, creating file systems and installing operating systems are risky operations, so you should ***always backup everything important before starting***. Backup at least all important personal data, and backup Windows too, if you want to keep it.

---

### Post by oldfred on 2015-02-12
All the auto install options may erase entire hard drive, so only use Something Else to reinstall. Then you can reuse the same / (root) partition. If you do not have swap you should or if you do have it, then it seems to automatically reuse it.

One other install option is fallback/gnome panel which also is lighter weight. I always liked and used the old style gnome2 panels. And early versions of Unity were not very good. So I installed fallback which worked very similar to your 10.04 and is lighter weight. I have 12.04 on my 2006 vintage laptop, but it is dual core with 1.5GB of RAM.
 [http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

        12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

    
 Classic, fallback, flash back explanation -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)
How to choose Display manager sessions -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682](http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682)

---

### Post by ekp0001 on 2015-02-12
> **sudodus said:**
> This option will delete the partitions and file systems and overwrite with the new Ubuntu. 

Sorry, I do not understand what tis means "delete the partitions and file systems"  Only system files or any files. All partitions on the HDD are everything, including data I want to save? 

For me meanwhile it seems I can not save the old data, except by staring a virtual ubuntu, copy any wanted file separartely to move it to the new notebook, and later make this HDD complete installation. Isnt it? 

I will sent the screen shots here (actually photographed from the small old notebook screen with the new computer):



> **sudodus said:**
> 
"... someone might be able to read some files from the previous system." 

No problem, I am the former and new user. ;-)

> **sudodus said:**
> 
Do you want to keep Vista? 
The old system was actually Win7 Home, it would not bad to have it, but than there would not much disk space remain for Ubuntu and I fear that this Celeron+only 1GB RAM are too weak for WIN 7. 


> **sudodus said:**
> Do you want to keep some personal data from the previous file systems? Yes, I am here because of this. 


> **sudodus said:**
> 
It is probably better to create a new swap partition with a size suitable to how you intend to use the computer. I would suggest 1.2 GB.

OK, there is a 1,3Gb partition

---

### Post by oldfred on 2015-02-12
This system has all 4 primary partitions used.
Windows uses 3 partitions, a Windows recovery, boot (typically 100MB), and main install. And then you have a Vendor recovery.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by ekp0001 on 2015-02-12
Meanwhile I am sure that non of these partitions is the actual data container I want to save. I begin to select to most important and recently changed files (not covered by an older back up) and copy/transfer them individually to the new notebook.  Later I may delete anything when installing ubuntu.  

Am I right with this?    
hmm - I wouldnt have my old e-mails this way. Saving a several GB file of the Thunderbird filesystem will be required. Accessing this Thunderbird file from the running Ubuntu Thunderbird program in Ubuntu will not be possible I guess ... ? 
Also the firefox browser bookmark file would be important to save and transfer to the new system. But where is it??! Not in application data !

---

### Post by oldfred on 2015-02-12
When I was dual booting Windows XP & Ubuntu, I moved both Thunderbird & Firefox profiles to a shared NTFS partition. I do houseclean both profiles regularly particularly those emails with large attachments. I either save attachment if important or if just the cat video delete it.

 new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Firefox
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

But this is why backup is important.

---

### Post by ekp0001 on 2015-02-12
thank you very much for you all !! :-)

But installing the old Ubuntu 10.04 will not cause problems - or does it?   I only will run firefox, thunderbird , open office, and geedit - will they not work with ubuntu 10.04 ?

---

### Post by Bucky Ball on 2015-02-12
> **ekp0001 said:**
> thank you very much for you all !! :-)

But installing the old Ubuntu 10.04 will not cause problems - or does it?   I only will run firefox, thunderbird , open office, and geedit - will they not work with ubuntu 10.04 ?

They will work, but dated software and no updates. This includes security updates. If you are going to use old, EOL releases, probably best to stay offline.

While 10.04 may work fine, you will not find a lot of support here or elsewhere for it, because, well, it's EOL. ;)

Perhaps see [here]("http://ubuntuforums.org/showthread.php?t=2229730"). Good luck.

---

### Post by sudodus on 2015-02-13
> **ekp0001 said:**
> Sorry, I do not understand what tis means "delete the partitions and file systems"  Only system files or any files. All partitions on the HDD are everything, including data I want to save? 

***All*** files will be deleted.
> 
For me meanwhile it seems I can not save the old data, except by staring a virtual ubuntu, copy any wanted file separartely to move it to the new notebook, and later make this HDD complete installation. Isnt it? 

You can boot a live system from a DVD or USB drive. And from that system you can mount the partitions on the internal drive and copy (alias backup) the files that you want to keep.

See the following link [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by sudodus on 2015-02-13
I agree with Bucky Ball.

After end of life, the old Ubuntu version is not supported. When  security holes are discovered, nobody will make any patch, so your  system will be vulnerable to attacks via the internet. If you do not  connect to the internet, it can be OK. Furthermore, it will be very  difficult to install programs, because the repositories are no longer  maintained at the Ubuntu web servers and mirrors. 				

So, to sum it up, it is a ***bad idea*** to run a linux distro, that has passed end of life.

---

