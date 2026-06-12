---
title: "Problem with installation via Wubi"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by StandbyExplosion on 2010-12-22
Hey everyone, this is my first post, and I hope that it will be an easy  problem to solve... I have downloaded the most recent release of Ubuntu  via Wubi (10.10) It downloads perfectly well and then says to reboot  Windows to finish the installation.

Upon restarting I select Ubuntu from the Dual Boot option, and I am then  face, after about 10 seconds, with a message that reads: "(initramfs)  mount: mounting /dev/sda on /isodevice failed: Invalid argument Cannot  mount /dev/sda on /isodevice"

If I type in the command to exit (exit), then I get another message that  states /scripts/casper-premount/20iso-Scan: line 5: Cant open /dev/sr0:  No medium found.

I am under the assumption that this means it cannot find the drive with  the installation files on, however I have checked and ran a chkdsk on  the drive (E) to find and solve any problems and there were none.

Any help would be greatly appreciated!

Many Thanks,
R.G. :smile:

P.S.
My system if it will help:
AMD Athlon 6000+ Dual Core Processor
Nvidia 9600GT Video Card
4GB 800Mhz DDR2 RAM
The drive for Windows is 1TB Samsung
Drive for Ubuntu and Wubi Western Digital 250GB

---

### Post by bcbc on 2010-12-22
Hi welcome to the forums. You don't need to double post - the mods don't like it and you'll get a double dose of confusing answers ;)

So... what make/model pc do you have?

Did it go straight to that message, or was there a 'Completing the installation, press ESC for more options" message as well.

---

### Post by StandbyExplosion on 2010-12-22
Sorry for the double post, I put it in beginner and then realised it should have gone into "Installation".

This is one of my own build PC's and the specs are above...

I do get the message saying about pressing "Esc"

Thank you for your reply :)

---

### Post by bcbc on 2010-12-22
Wubi copies all the files to the drive that it installs from. So, I'm not sure what the issue is.

Is there a reason you want to install with Wubi and not the usual install?

In general to install wubi, I just place wubi.exe and the downloaded .iso file in the same folder and run wubi.exe. That seems to work the best. If you have a 10.10 .iso you need the wubi.exe for 10.10 (the one on ubuntu.com is 10.04.1). You can get it off the .iso (if you burn it to CD or mount it) or just copy from [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

Wubi has issues with grub updates so avoid updates to packages grub-pc and grub-common.

Hope that helps.

If there is any more error messages or something else that might help identify your problem, please post back. But I'd try reinstalling first.

---

### Post by StandbyExplosion on 2010-12-22
I am going to have another try, I am using Wubi as I thought it would be an easier way to install even though I am sure that I could try it the usual way. I will post back soon with more information on how it went the second time around.

I may have gotten a mix up with the versions of Ubuntu, I used Wubi to download the file for me so I assumed that it would be the correct one. I know that now to get the 10.10 I need to get it from the .iso Thanks again :)

---

### Post by bcbc on 2010-12-22
> **StandbyExplosion said:**
> I am going to have another try, I am using Wubi as I thought it would be an easier way to install even though I am sure that I could try it the usual way. I will post back soon with more information on how it went the second time around.

I may have gotten a mix up with the versions of Ubuntu, I used Wubi to download the file for me so I assumed that it would be the correct one. I know that now to get the 10.10 I need to get it from the .iso Thanks again :)

To be fair the Ubuntu.com website tells you it's 10.10, but if you select the windows-installer option it doesn't mention anywhere that it's now 10.04.1. So it's not you ;)

You don't have to get if off the .iso. You can just download wubi.exe from the site I linked to previously. It's definitely better to download the .iso separately though - as a) it's quicker than letting wubi.exe do it; b) if you need to reinstall you don't have to download it again; and c) you should create an Ubuntu CD as a rescue disk in any case.

Also note, there are issues with Wubi and Grub2 (the bootloader Ubuntu uses) - avoid updating packages grub-pc and grub-common if you get prompted. 

Wubi is OK to use to try out Ubuntu, but if you think you'll be using it long-term, a partition install is better.

Final note: often with nvidia cards you need to supply a "nomodeset" boot option with the latest releases (10.04 and 10.10). I'll just give you the link now in case you have issues: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by StandbyExplosion on 2010-12-24
Okay, so it turns out there may be a problem with Ubuntu recognising my SATA drives, I found a similar thread to this that explained how to boot if this problem occurs, I managed to install Ubuntu onto the other HDD however the instructions were not clear on how to finish off the modification to the Boot loader. I have subsequently re-formatted the Hard Disk and will endeavour to try again at a later date. 

Thank you for your help bcbc!! 

R.G.

---

### Post by dino99 on 2010-12-24
about real installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

about sata: into bios, choose ahci or compatible (better)

---

### Post by theasprint on 2010-12-24
Hi,

Not sure if this concerns or is related to your problem but:

I have also met another user with the /isodevice problem.
At the end, the user "confessed" that he used Daemon Tools to mount the .iso file, which he thinks it's possible to install that way. 
But the truth is: ITS NOT.
* It's ok, I'm not criticizing you. Just wondering if you also did that, which caused the /isodevice problem.

But since you have already re-formatted the HDD, then I might as well suggest another guide on dual-booting Ubuntu with Windows 7 (I feel the one dino99 gave is quite under-detailed)
[http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

---

### Post by StandbyExplosion on 2010-12-24
@dino99

I am familiar with using the BIOS, whereabouts will that setting be found for the SATA?

Many thanks

R.G.

---

### Post by StandbyExplosion on 2010-12-24
I found the setting for ahci, there was no "compatible" mode unfortunately. Once I had selected AHCI I could no boot windows... Perhaps you knew this would happen and that is why you said compatible would be best. So I am still stuck on the SATA thing... Unless I have done something wrong... Bios set back to SATA for the time being.

Many Thanks
R.G. :)

---

### Post by StandbyExplosion on 2010-12-24
Okay... Got the drivers required for Windows to run AHCI, Evrything is going fine, does that mean now that I will be able to have another go at installing Ubuntu and it should work fine?

Many Thanks Once Again,
R.G.

---

### Post by linfidel on 2011-02-09
I'm a long-time Ubuntu user, and have it installed on an older computer. I also have a Windows XP computer, which is newer and faster (but still a couple of years old).

I have thought about switching Ubuntu to the newer system, but I wanted to try it out first, so I decided to try Wubi instead of a dual boot.  Why?  Because it's much easier to uninstall, of course.  I don't see why some of you don't understand that.  How do you easily uninstall if it's dual-boot, in a way that is foolproof?  Of course it can be done, but it's not that easy, especially for a novice.

Anyway, wubi (on 10.04 live CD) failed at 99.9%, after installing the iso, etc, with the same error that's been reported for the past few versions: invalid argument.

I have a theory that I will test, that it is not handling multiple drives correctly.  I see in the log that it fails to read some files, but there is no drive letter specified.  Most failures I see reported are on drives other than c:, yet I see developers saying things like "wubi should create an iso on C:\ubuntu\... which is not true if you install on a different drive.  So maybe they are only testing with a single drive system.

Has anyone tested this?  I'll try running from the hard drive, and report back if successful.

---

### Post by dino99 on 2011-02-09
I don't see why some of you don't understand that.

and now ?

---

### Post by bcbc on 2011-02-09
> **linfidel said:**
> Has anyone tested this?
uh yes. 

The answer to your problem lies in the log file.

---

### Post by linfidel on 2011-02-09
> **dino99 said:**
> I don't see why some of you don't understand that.

and now ?
??? What does that mean?

My quote refers to people that ask things like Why don't you just do a regular install, or dual boot, etc. and don't understand the purpose of wubi.

and then ?

---

### Post by linfidel on 2011-02-09
> **bcbc said:**
> uh yes. 

The answer to your problem lies in the log file.

no it doesn't.  The symptoms lie in the log file.  I have yet to find an answer.  The log file only says it can't find certain files.  But I've validated the CD, and the md5sums match, so if it can't find the files, then there is a problem with the installer.  

Have you been reading my log files?  If so, perhaps you can give me the answer.  Or something more constructive than your smug remarks. 

I simply asked if anyone has tested the installer using alternate drives, not the installer itself.  Obviously, they don't release it with no testing, and hopefully, you didn't interpret it that way.  After all, I've been using Ubuntu for 4 years, as you can see, so it's not like I'm a detractor putting it down.

---

### Post by bcbc on 2011-02-09
> **linfidel said:**
> no it doesn't.  The symptoms lie in the log file.  I have yet to find an answer.  The log file only says it can't find certain files.  But I've validated the CD, and the md5sums match, so if it can't find the files, then there is a problem with the installer.  

Have you been reading my log files?  If so, perhaps you can give me the answer.  Or something more constructive than your smug remarks. 

I simply asked if anyone has tested the installer using alternate drives, not the installer itself.  Obviously, they don't release it with no testing, and hopefully, you didn't interpret it that way.  After all, I've been using Ubuntu for 4 years, as you can see, so it's not like I'm a detractor putting it down.
Sorry I couldn't resist that ;) 

Yes you can install wubi on another drive. I've installed it many times on an external usb drive.

Why don't you post or pastebin the log file and I'll take a look. You're right it's not always a clear cut answer but there are usually a few more clues than 'invalid argument'.

The easiest way to install wubi is to download the desktop ISO and the corresponding wubi.exe into the same folder and run it from there.

---

### Post by StandbyExplosion on 2011-02-10
Okay, I have fixed the problem... I really hope other people with this problem will be able to look at this as well as it is a fairly simple fix...

I gave up with Wubi and have done a full install via restarting with bootable media. I added the line pci=nomsi to the boot loader just after the words "quiet splash" and this has worked!

Ubuntu recognised my Sata drives for the first time and I am now up and running! :D

However I have tried editing Grub to keep it set at this however I cannot seem to do this although I know it is possible.

Many thanks for your replies guys, I now have a solution!

Thanks again! :D :D

---

### Post by bcbc on 2011-02-10
> **StandbyExplosion said:**
> Okay, I have fixed the problem... I really hope other people with this problem will be able to look at this as well as it is a fairly simple fix...

I gave up with Wubi and have done a full install via restarting with bootable media. I added the line pci=nomsi to the boot loader just after the words "quiet splash" and this has worked!

Ubuntu recognised my Sata drives for the first time and I am now up and running! :D

However I have tried editing Grub to keep it set at this however I cannot seem to do this although I know it is possible.

Many thanks for your replies guys, I now have a solution!

Thanks again! :D :D
Edit the grub defaults:
```
gksu gedit /etc/default/grub
```
make this change:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"
```
regenerate grub.cfg:
```
sudo update-grub
```

---

### Post by StandbyExplosion on 2011-02-10
I definately want all of that in quotation marks? 

"quiet splash pci=nomsi"

Thank you for your reply :D

---

### Post by bcbc on 2011-02-10
> **StandbyExplosion said:**
> I definately want all of that in quotation marks? 

"quiet splash pci=nomsi"

Thank you for your reply :D

Yes - according to the resident expert ;)

See the [Grub2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275")
> For the GRUB_CMDLINE_LINUX_DEFAULT and GRUB_CMDLINE, quotation marks are required (single or double) if the entry is more than one alphanumeric entry. For example, quiet splash requires single or double quotes, while an entry such as quiet would not.

---

### Post by StandbyExplosion on 2011-02-10
Brilliant, Thank you :P Will give it a go shortly! :D

---

### Post by StandbyExplosion on 2011-02-10
Yes! Thank you so much! :D

Brilliant help from everyone... One last question though.

How do I mark this thread as solved? :P

---

### Post by bcbc on 2011-02-10
Good to hear! 

Click on Thread Tools and you'll see a *Mark thread as solved* option at the bottom.

---

### Post by StandbyExplosion on 2011-02-10
Thanks again everyone, especially bcbc!

Looking forward to years of Ubuntu use now! :D

Thanks again.

R.G.

---

### Post by linfidel on 2011-02-10
> **bcbc said:**
> Sorry I couldn't resist that ;) 

Yes you can install wubi on another drive. I've installed it many times on an external usb drive.

Why don't you post or pastebin the log file and I'll take a look. You're right it's not always a clear cut answer but there are usually a few more clues than 'invalid argument'.

The easiest way to install wubi is to download the desktop ISO and the corresponding wubi.exe into the same folder and run it from there.I did what you said, and after a couple of false starts, actually got it to install, tested it, and then deleted it.  It insisted on having a disc in the CD drive, and it also insisted on a 64 bit ISO; I started with a 32 bit one, and it ignored it and tried to download a new one, so I cancelled and gave it a 64-bit ISO that I already had. 

It made me glad I didn't do a full install, as it was much easier to uninstall the wubi app than prepare, then clean up a regular install.  Unfortunately, the system I was testing is an AMD motherboard with ATI graphics card, and the ATI drivers are no longer supported, so I had to choose between dual monitors or desktop effects, and I wanted both.  So, I'll have to wait and buy a new system if I want to upgrade my older one.  I'll avoid ATI this time.

The log file really wasn't much help, to me.  It didn't make sense, although it might to someone who knows how wubi works.  The relevant part said:
```

02-10 08:23 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
02-10 08:23 DEBUG  TaskList: # Cancelling tasklist
02-10 08:23 DEBUG  TaskList: New task check_iso
02-10 08:23 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
02-10 08:23 DEBUG  CommonBackend: Searching for local ISO
02-10 08:23 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-10 08:23 DEBUG  TaskList: New task get_metalink
02-10 08:23 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO

```

I had no idea why it would need to download an ISO, and I couldn't find the python sources to look at the code.  But I think there may be a problem reading CDs burned with certain versions of Nero, which is what I used originally to burn them.  I download on my windows system, because I have a nice download manager on it, and it's faster and easier - usually.

Anyway, sorry if I was too touchy, but I had read too many remarks from people acting like the person was doing something wrong for wanting to use the CD in a way it was designed to be used (not just this thread, I've read a few others).

---

### Post by bcbc on 2011-02-10
@linfidel,
I recommend starting a new thread for yourself if you have more questions about Wubi. This one's done and dusted. But I'll make a few points here...

1. I've noticed that 'requiring a CD thing'. Just go to Update Manager, Settings, and uncheck the CD from the software sources. It's probably a bug that should be reported.

2. Wubi will use a 32-bit .iso in the same folder provided it's the correct release. If it rejects it then it will download a new one - and in that case it defaults to 64-bit for machines that are 64-bit capable.

3. Errno 22 - as you've already discovered the relevant bug reports you know as much as anybody about what is going on there. If you'll look at the dates on the reports you'll probably have figured out that there is no fix in the works. I believe it can be related to the burn e.g. with Nero, but also some Optical drives.

4. Yes a lot of people say negative things about Wubi. Some of it is valid - some of it is flame-bait.

PS here's the wubi code [http://bazaar.launchpad.net/~ubuntu-installer/wubi/trunk/files/head:/src/wubi/](http://bazaar.launchpad.net/~ubuntu-installer/wubi/trunk/files/head:/src/wubi/)

---

