---
title: "Severe Installation Errors"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by sinistermilk on 2005-10-13
installation Failed to install base system
"initrd-tools package" to my comp and now i can't do anything at all
for instance when i try to boot the computer
I get a Grub Error 15

The only used of my computer is with a live cd.

I was attempting to install 5.10 i386
on a slave diskseaparate from my other os

I have check the cds integrity it is fine
also the md5sum matched up as welll

please help me i dont know what to do and can't use anything but live until this issue is resolved

---

### Post by sinistermilk on 2005-10-13
please some help my computer is inoperable with the live cd i canh't use my hard disk at all.

I'm frightened to death.

---

### Post by byronclark on 2005-10-13
Booting the install cd with "linux acpi=off" resolved this problem for me.

---

### Post by Pumpino on 2005-10-13
Boot from a Windows boot floppy, get to a DOS prompt, and type fdisk /mbr.  Then reboot.

---

### Post by AgenT on 2005-10-13
[quote=Pumpino]Boot from a Windows boot floppy, get to a DOS prompt, and type fdisk /mbr.  Then reboot.[/quote] 
Why would you want him to do that? This would totally overwrite his boot record (grub!) making it impossible for him to get into Linux. You are assuming he is running Windows in which case he would then be able to only use Windows. 

If the acpi trick mentioned above fails, you can try to re-install grub. But the problem sounds like a misconfigured grub. 

Not exactly sure what the command for re-installing grub is though. To reinstall grub (if you can't boot into recovery mode) would require a LiveCD of some kind.

---

### Post by jones_jj on 2005-10-14
Sinister-

I just want a little more clarafication just for my own sake.  You said you were trying to install 5.10 and the whole install failed all together?  So 5.10 was not able to install at all?

What other OS do you have running on your computer?

Thanks for the clarafication

---

### Post by sinistermilk on 2005-10-14
thanks for the efforts

yes it failed to install

"wasn't able to install base system"

I've tried to install it countless times at this point but to no avail.

using "linux acpi=off" fail top change anything either

I plan to try Edubuntu or kubuntu this weekend if the situation doesnt change

and the other OS is win XPsp2

---

### Post by yerffej on 2005-10-15
I had this exact same problem. After several hours screwing around with Grub, reinstalling etc. it turned out that by just changing the boot sequence of my 2 hard drives in the BIOS resolved the problem.

---

### Post by Vladas on 2005-10-15
Hello.
I have also the problem while installing ubuntu 5.10. During installation of it to my noname laptop (pentum M 1,6Gh 512 RAM) , I get: unable to install initrd-tools. check /target/var/log/bootstrap.log. HD contains partitions only created by ubuntu installer, so I don not have other OS . I have also tried linux scpi=off option be it did not help either. I must say, that this laptop had a windows xp sp2 before on other 60GB HD, but I have changed it to a new 80 GB HD in order to have a working system in case of failure. I do not know if that will help, but I have also tried to install a lilo and a grub boot loaders after I failed to install a base system. These steps also failed giving me an error with something like "can not install ... on /target/". I am pretty new to linux so I have no ideas how to fix this.

---

### Post by DukeNuke2 on 2005-10-15
[QUOTE=Vladas]Hello.
I have also the problem while installing ubuntu 5.10. During installation of it to my noname laptop (pentum M 1,6Gh 512 RAM) , I get: unable to install initrd-tools. check /target/var/log/bootstrap.log. HD contains partitions only created by ubuntu installer, so I don not have other OS . I have also tried linux scpi=off option be it did not help either. I must say, that this laptop had a windows xp sp2 before on other 60GB HD, but I have changed it to a new 80 GB HD in order to have a working system in case of failure. I do not know if that will help, but I have also tried to install a lilo and a grub boot loaders after I failed to install a base system. These steps also failed giving me an error with something like "can not install ... on /target/". I am pretty new to linux so I have no ideas how to fix this.[/QUOTE]
same problems here on a msi 925xe motherboard with 160 gb sata harddisk.... any help would be nice....

---

### Post by RawMustard on 2005-10-15
did you try noapic like the advanced boot options mention?

---

### Post by DukeNuke2 on 2005-10-15
[QUOTE=RawMustard]did you try noapic like the advanced boot options mention?[/QUOTE]
just tried the "noapic" option.... same problem:

"An error was returned while trying to install the initrd-tools package on target system.

Check /target/var/log/bootstrap.log for details.

This file dosen't exist..... :(  HELLLLLP!!!

---

### Post by RawMustard on 2005-10-15
Can you give us a better run down of your systems setup, ie what kind of drives you have, what your motherboard is, whether you're using raid, sata, how many cd/dvd's you have, how they are connected?

I know these may be daunting questions, but under these circumstances, we need a little more info in order to help you out more?

---

### Post by DukeNuke2 on 2005-10-15
[QUOTE=RawMustard]Can you give us a better run down of your systems setup, ie what kind of drives you have, what your motherboard is, whether you're using raid, sata, how many cd/dvd's you have, how they are connected?

I know these may be daunting questions, but under these circumstances, we need a little more info in order to help you out more?[/QUOTE]
the problem is solved :D
i have a dvd drive and a dvd burner. i always used the dvd drive and failed to install, now i used the burner and everything went fine :)
in fact i'm writing this out of ubuntu.....yeah! thnx to all!

---

### Post by tenjin on 2005-12-03
Hi,

Same problem on a Dell Dimension 4100 P3 machine. 512Mb RAM, noname 20Gb IDE HDD.

Any ideas?

Cheers

D.

---

### Post by tenjin on 2005-12-03
Hi,

I have just successfully installed 5.04 (Hoary) on the same machine.

So, we clearly have a problem with Breezy.

Not sure if this helps, but I created the following partitions in all cases and in this order on the HDD:

/
/var
swap
/home

Any ideas?

Cheers

Darren.

---

### Post by bwog on 2005-12-03
@sinistermilk: What Byronclark said will give you windows back. You can then try to install with different bootparameters. 

You can also post a new thread with details of your hardware (this one cluttered with too many other questions). 

Try also to search for ubuntu and your chipset or motherboard too see if someone else has resolved your problems.

---

### Post by djjazzy on 2005-12-13
I had the same problem on a HP Vectra 1Ghz desktop with 512MB RAM and 20GB HD, entering linux acpi=off at grub boot prompt sorted me, cheers......Jeff

---

### Post by apletosu on 2005-12-14
I just had the same problem - always stopping in the same place - initrd-tools. I re-burned the CD image at 4x (was at 10x before) and then the installation went flawlessly. I was burning on a CD-RW but I don't think it makes a difference.

Conclusion: slower is better :) There was no problem with the image per se - just with the CD writing speed

---

### Post by excyberlabber on 2006-01-15
I am having the same problem (install breaks at initrd-tools) on an old IBM thinkpad 21 with a pIII and 20gb hd.  linux acpi=off  froze the install, linux vga=771 noapic nolapic had the same break on the initrd-tools.  I will try re-burning the install cd at a lower speed next, and report back if it worked.

OK!  Reporting back:  I burned the cd at a slower speed, and it worked!!  I had tried all kinds of special boot configurations but nothing changed the outcome - until I burned a new cd at a slower speed.  Very grateful for apletosu's post.  I burned the original cd at 32x, and today I burned it at 8x, the slowest speed of my cd burner.

---

### Post by gomaaa on 2006-01-17
I have also had problems installing to a SATA hard drive and I believe there are several other people having similar difficulties.  I have tried to collect links to some of these issues and describe my own problem in the following thread:

[http://ubuntuforums.org/showthread.php?p=664688#post664688]("http://ubuntuforums.org/showthread.php?p=664688#post664688")


I hope that a general solution can be found!

gomaaa

---

### Post by b4k4 on 2006-01-26
I am struggling witth the same problem. Installation aborts at initrdtools. I have tried burning CDs at single speed on two different machines. I have had the same failed install using  Edubuntu CD also. The failure has happened on two different machines:

Sempron, 512, 40G, LG DVD-rw, MSI mobo

P4, 2G, 40G Hitachi, Asus CD-rw, Aopen mobo

I have tried the suggested boot options

Any further help?

I can install Hoary on one of these machines (haven't tried the other) Can I upgrade Hoary to Breezy without using CD? When I tried with CD it hung at configuring gcc.

---

### Post by b4k4 on 2006-01-26
I forgot to mention that my HDD are not SATA

---

### Post by JELaVallee on 2006-02-10
I've been using Hoary for almost a year now and decided to upgrade it to Breezy and add a dual boot / partition for the impending Dapper.  Sigh...

My hardware is an IBM T43p (see sig) with an SATA drive architecture.  I'm regretting that... really... I am...

So I have one of the last install discsets from my latest ShipIt CD bag (20+ out to friends and family!).  The installer failed consistently with the initrd error.  The LiveCD failed about 50% of the time while checking the udeb packages MD5's.  DMA isn't an issue as this DVD-RW is seen as a SCSI device (/dev/sda0).

So, I give up and try a new discset a friend had... same issue...

Then I try an iso burn on CD-R... 16x failed... 4x succeeds!!!???

Now I'm definitely happy to have Breezy up and running and my /home and /opt restored and VMWare playing ball and I can even burn CD's now... BUT, I think this is an issue that never should have made it to the final gold pressing of the Ubuntu Breezy official discsets.

After a general poll of friends I gave the discset too, several also reported issues with this on systems with fairly stock hardware.  ACPI/DMA solved two of those issues, the third one is still a mystery.  I recommended that he try my DL'd iso and we'll see... he seemed pretty disheartened by the whole experience, esp. after my "Year of Ubuntu Proselytizing" to everyone who'd listen... 

In general, I'm feeling that Dapper will be seriously hosed if it has this bad of an installer hiccup problem.  Warty and Hoary had installers that never came close to this level of frustration for me.

My rant is done here... back to real work...

hrumph,
Etienne

---

### Post by dark_to on 2006-02-24
I tried burning 4x but failed. The solution for me was to set up the date in the motherboard, as explained in  [https://launchpad.net/distros/ubuntu/+source/ubuntu-keyring/+bug/13881](https://launchpad.net/distros/ubuntu/+source/ubuntu-keyring/+bug/13881)
Salu2 from Spain

---

### Post by Marsolin on 2006-03-07
I've had the same issue with the Debian install CD.  For both I'm having the problem while installing on VMWare Workstation after having remastered the CD.  Even rebuilding the iso without making any other changes is causing the problem.  I may have a different issue than others (or not), but the end behavior is that I get a failed to install to target error during install.

---

### Post by pfctdayelise on 2006-04-19
Wow... I just had this problem too. Talk about freaked.

Installing on a NEC VERSA S940 notebook, trying to do an 'expert' install to set up separate partitions for Windows XP SP2 (preinstalled), Ubuntu (Breezy), data ('/home') and the little 'swap'thing.

Since my machine is new I thought I wouldn't bother to backup, but I guess creating a boot disk is a separate, highly recommended procedure. Oh well, living on the edge! :eek: 

Anyway finally got the partition stuff sorted (thanks to [this page]("http://users.bigpond.net.au/hermanzone/p14.htm")), then had this problem. Found this thread and commenced REALLY freaking out. Wasn't too impressed since I have a Shipit CD, so there shouldn't be any burn-rate problems...

I went back and redid the partition stuff, well actually didn't change anything but made it go through the several-minute process of making them up again, and this time... with breath-holding and pleading and begging... it worked fine!

So huge thanks to whoever suggested redoing the partitioning. No idea why it works, but finally, it just works...

---

### Post by ushio81 on 2006-04-29
I got exactly the same initrd-tool problem. I've tryed to redownload the CD, to re-burn at 4x but nothing...always the same problem. I've tryed to change boot order too...nothing....

WE NEED HELP! :(

---

### Post by VoiceOvGod on 2006-05-01
[QUOTE=pfctdayelise]

I went back and redid the partition stuff, well actually didn't change anything but made it go through the several-minute process of making them up again, and this time... with breath-holding and pleading and begging... it worked fine!

[/QUOTE]

Usually the pleading and begging does work...

I got a few Kernel Panic errors when attempting to install from my shipit CD.

I've been trying all weekend to get a clean install, but somehow, something goes wrong. usually in the package installation stage after the reboot.

---

### Post by alatopi on 2006-05-02
Hi!


I'd just like to mention (for statistics' sake at least) that I had similar problem when I first installed Ubuntu yesterday. While installer was installig base system it hung up with error message like: "unable to install initrd-tools" etc. Same problem with two different machines.

In my case problem was solved by burning new installation cd with slower speed and not using cd-rw (as I did the first time around). Strange though that so many different problems seem to produce this same error-message.


Topi

---

### Post by zakarth on 2006-05-16
Hey folks, 

Running a beige g3 powerpc and I thought I'd mention that I was having the same problems with initrd-tools with Breezy. Burning at 4x certainly fixed it after I coastered two other CD's >:O 

That being said, here's a clue for the curious out there. Checked the /var/log/messages and it appears to fail installing the kernel because of a dependency on the zlib package. I tried to confirm this for myself and for whatever odd reason I get an I/O error when I try to read the zlib package off of the CD. 

I have zero idea why it works when you burn it at a lower rate but I think it's odd that the file would be incrementally the last file on the CD if you follow the tree structure. (That's just wild speculation and so take it with a grain of salt)

---

