---
title: "boot manager"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by Kenneth David on 2012-07-23
I would like to install ubuntu but is there any way to do so with windows handling booting duties or is the only way to let ubuntu do that?
also can the full install be done to an sd card and boot to that?

---

### Post by oldfred on 2012-07-23
Only a few computers directly boot sd cards. Does your BIOS allow that? More allow booting from USB flash drives, but again you have to check BIOS. Most systems in the last 5 or 6 years boot flash drives. Some see the flash drive as a hard drive not a USB device.

You can install to hard drive but use the flash drive to boot. We tend to like grub2 and most in this forum use grub2. I boot from hard drives but also have grub2 in a flash drive that can boot several of my installs on the hard drives.

A few have posted this works, but I do not know much about it.
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Understand that using EasyBCD, you have to install grub2 to a partition which is not recommended. It has to convert to hard coded address to find the rest of grub2 to boot. On a major update the address may change preventing booting. You need to be prepared to reinstall grub2 to the partition in that case.

---

### Post by Kenneth David on 2012-07-23
I kinda take it you're saying just let ubuntu install its self and live with their boot manager. 
also my laptop is 64 bit. shouldn't iI use the 64 bit version of ubuntu? it recommended 32 bit.


> **oldfred said:**
> Only a few computers directly boot sd cards. Does your BIOS allow that? More allow booting from USB flash drives, but again you have to check BIOS. Most systems in the last 5 or 6 years boot flash drives. Some see the flash drive as a hard drive not a USB device.

You can install to hard drive but use the flash drive to boot. We tend to like grub2 and most in this forum use grub2. I boot from hard drives but also have grub2 in a flash drive that can boot several of my installs on the hard drives.

A few have posted this works, but I do not know much about it.
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Understand that using EasyBCD, you have to install grub2 to a partition which is not recommended. It has to convert to hard coded address to find the rest of grub2 to boot. On a major update the address may change preventing booting. You need to be prepared to reinstall grub2 to the partition in that case.

---

### Post by rplantz on 2012-07-23
> **Kenneth David said:**
> I kinda take it you're saying just let ubuntu install its self and live with their boot manager. 
also my laptop is 64 bit. shouldn't iI use the 64 bit version of ubuntu? it recommended 32 bit.

I dual boot using the Windows boot manager so that I can get into Windows repair mode if need be. I'm running 64-bit versions of both Windows 7 and Ubuntu 12.04. Actually, I'm triple booting my desktop machine, Windows 7, Windows 8 RP, and Ubuntu 12.04.

First, you need to choose the manual partitioning and select the partition where you want Ubuntu installed. Then there is a place where you have to select "advanced" (I forget the exact name). Then you tell it to put the boot manager in the partition where Ubuntu is being installed. This prevents if from writing over the MBR.

Then I used EasyBCD in Windows 7 to add the Ubuntu OS to the Windows 7 boot manager.

I'm sorry that I cannot give all the precise details here. I haven't done it for a few months and forget all of them. But this should at least point you in the right direction.

Oh, don't forget to back up your Windows info before trying this. I have learned over the past 50 years that the best way to prevent problems is to have a back up. Conversely, not having a back up causes problems. At least it seems that way. Sort of a corollary to Murphy's Law.

---

### Post by oldfred on 2012-07-23
The only reason they still recommend 32bit is that 25% of users only have 32bit hardware. Very few applications do not work in 64 bit. I think some just had issues with skype and Oracle database. Both just converted to 32 bit so we are not sure if it was solvable or not.

---

### Post by Kenneth David on 2012-07-23
I'm getting some great answers thank you all. please keep them coming as you can tell I'm a rookie at this. 
I did install ubuntu last year on my other machine but i didn't like the boot manager. i prefer to let windows do that. don't ask it's just my preference. 

so based on the response i think i need a little more help.

[COLOR=Red]"I dual boot using the Windows boot manager so that I can get into  Windows repair mode if need be. I'm running 64-bit versions of both  Windows 7 and Ubuntu 12.04. Actually, I'm triple booting my desktop  machine, Windows 7, Windows 8 RP, and Ubuntu 12.04.

First, you need to choose the manual partitioning and select the  partition where you want Ubuntu installed. Then there is a place where  you have to select "advanced" (I forget the exact name). Then you tell  it to put the boot manager in the partition where Ubuntu is being  installed. This prevents if from writing over the MBR.[/COLOR] [COLOR=Red]

[COLOR=Black]If someone knows more specific what the name and location of this is i would appreciate it. [/COLOR]

Then I used EasyBCD in Windows 7 to add the Ubuntu OS to the Windows 7 boot manager.[/COLOR] [COLOR=Red]"[/COLOR]

I could also use an explanation on what exactly this is and what it does. 

I will forget about the sd card and install an ssd in a couple months but for now i would like to get this working.
I also have a 600 gb hd on here what would you recommend as a partition size? 100? 150?

---

### Post by oldfred on 2012-07-23
If you have two hard drives there is no issue. Install each system to different drive. You keep the Windows boot loader on the Windows drive and grub2's boot loader on the Ubuntu drive. Ubuntu will let you boot both, but you can use BIOS or one time boot key (f12 on my system) as booting to choose which drive to boot.

I think the links I posted have a lot more detail on EasyBCD. Have not looked in ages, but posted recently and someone thought they helped a lot.

If installing to another drive or partition, you have to use manual install or Something else. Otherwise grub2 just defaults to installing to sda.  See Herman's link  for screenshot:

Installer has not changed hardly at all. Manual install is now something else and just about everything else is the same:
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

Current installer, but all are automatic and will install grub2's boot loader to sda.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

---

### Post by Kenneth David on 2012-07-23
I will be installing on one hd. I just plan on replacing this one with a ssd.

---

