---
title: "Boot-Repair-Disk : THE 'must-have' rescue CD !"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2011-08-24
Here is ZE Rescue Disk that you should keep close to your computer ! :guitar:
**Functionalities:**
- runs automatically [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") rescue tool at start-up
- light LXDE environment in order to repair even old PCs with little RAM

**Download:** [official website]("https://sourceforge.net/p/boot-repair-cd") (md5 is on [this page]("https://sourceforge.net/projects/boot-repair-cd/files/")). Then burn it on CD or put it on USB key via Unetbootin.

**Use:**
1) Insert the Boot-Repair-Disk and boot the PC
2) Select "Recommended repair" --> solves the majority of bootsector/GRUB/MBR problems

[IMG]http://pix.toile-libre.org/upload/original/1367951460.png[/IMG]

[Official website of Boot-Repair-Disk]("https://sourceforge.net/p/boot-repair-cd/home/Home/")

---

### Post by ottosykora on 2011-08-24
well yes, but what does it repair? Grub2, Grub legacy, mbr made by windows or some UEFI things or what is it for exactly?

---

### Post by YannBuntu on 2011-08-24
it can do all you said, and more :)

- reinstall and update GRUB (1 and 2)
- purge GRUB
- choice to place GRUB in MBR or partition
- restore generic Windows (XP, Vista, Seven) MBR   (other tools I know don't work with Vista/Seven)
- restore original MBR (required when computer has MBR-tatoo)
- auto detect separate /boot
- detect RAID, GPT EFI
- compatible Debian, Ubuntu and derivatives
- can be used in live-CD, live-USB and installed session (see [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) )
- compatible whatever the architectures (32/64bits) of OS detected on the pc
- automatically solve several GRUB/Wubi bugs
- generate BootInfoScript report (automatically uses the very last script) in 1 clic
- repair filesystems (linux AND windows)
- a nice and intuitive GUI
- ...
- most important of all : automatic selection of best choices to repair the boot in 1 click !

Boot-Repair is free (GNU-GPL), and will soon be included in Debian repositories.

---

### Post by SES1 on 2011-08-24
What exactly is the expected result? I was having boot issues and was stuck at the grub promt and after running this disk I just get a black screen after reboot saying: ```
No System Disk or
Disk I/O error
Press a key to restart

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
``` 

I almost had the issue resolved after a day of working on it and now I'm afraid things are worse. :(

---

### Post by YannBuntu on 2011-08-24
Hi SES1,
first check the md5sum of the ISO you downloaded, you can find the md5 by clicking on the (i) icon of this page: [https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/), and the tool to check the md5 [here]("http://bipede.info/bipede/index.php?check-iso-devient-check-file-integrity").
If it is correct, please burn the CD with a slow speed.
Then boot on the CD, you should see this screen appear:
[IMG]http://pix.toile-libre.org/upload/img/1313341695.png[/IMG]

Then choose 32 or 64bits, according to your PC architecture. This will run Boot-repair automatically. No change will be made on your PC boot until you click the "Apply" button.
Then select the "First repair", or go to "Advanced options" for customized repair. If any doubt, select the "Create BootInfo" and indicate us the URL so that we can advise you.

---

### Post by SES1 on 2011-08-25
Thanks for your response. I ran the boot info script and this results are posted in this other thread: [http://ubuntuforums.org/showthread.php?t=1832261]("http://ubuntuforums.org/showthread.php?t=1832261"). From what I can tell now, it is a software issue not seeing the partitions on my disk rather than strictly a grub issue as I thought before. Beyond that, I don't really know what's going on.

---

### Post by gizmojo on 2011-08-25
I am trying to install Ubuntu 11.04 on my laptop. I've actually removed Win7, and reformatted the Hard Drive. I have one large partition on the drive. I've installed Ubuntu from Ubuntu live on my flash drive. When I attempt to boot the computer from the hard drive, I get the "error: no such device:" message.

I downloaded the Boot-Repair tool and installed it on another flash drive with unetbootin. When I start the computer from Boot-repair, I get to the start menu, but no matter which boot option I choose, I get Boot Failed!  Unknown file system type on /dev/loop0.

---

### Post by YannBuntu on 2011-08-25
Hello gizmojo, and welcome among us ! :)

Please follow the ISO md5 check steps I described in my previous message.
You can also install Boot-Repair on your flashdrive's Ubuntu, as described in the Documentation: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by princetrey12 on 2011-08-26
I used unetbootin to put it on a USB and checked the md5 but I keep ending up on a "initramfs" prompt

---

### Post by YannBuntu on 2011-08-26
hello princetrey, I just checked with Unetbootin and I don't have this error. As an alternative, you can try [Ubuntu Secured]("https://help.ubuntu.com/community/UbuntuSecuredRemix") (it's an Ubuntu ISO containing Boot-Repair) via [LiliUSB creator]("http://www.linuxliveusb.com/") or via USB-Creator (the tool included by default in Ubuntu).

---

### Post by princetrey12 on 2011-08-26
I'm on my phone but I took a picture of the screen with the error message on it. Is there anyway I could send it to you.

---

### Post by YannBuntu on 2011-08-26
Yep, my email is yannubuntu ATTT gmail DOTTT com

---

### Post by princetrey12 on 2011-08-26
I sent it

---

### Post by YannBuntu on 2011-08-26
i received it, thank you. This appears to be a Debian-live error, I will check further.
In the meantime, please try Ubuntu Secured as described in my previous message.

---

### Post by milandroid on 2011-09-03
Hi, I just reinstalled windows on a ubuntu machine.

I burned boot-repair disk into a usb drive and boot from that. after selecting 32bits 
session it started to scan my system. But remain quiet since the dialog box disappeared.

I also tried to install boot-repair in my ubuntu and ran it. But it always crash when ```
=> [[ PY ]] =>  RETOURCOMBO_partition_booted_bymbr: sda1 (Windows 7) , TARGET_PARTITION_FOR_MBR becomes 1
``` appeared on the terminal screen as the last line.

---

### Post by YannBuntu on 2011-09-03
Hello Milandroid,
Boot-Repair is now broken, until all icons become green on the following page:
[https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)

(Launchpad sometimes take several hours to accept an update)

Please retry when all icons are green. This should be in about 4 hours.

---

### Post by Scooby-2 on 2011-09-22
Just to warn others that may (like I did) think this CD is easy to use and can do everything - it can leave you with an un-bootable system. I had a single-disk setup with Clonezilla, XP, Vista, Xubuntu 10.04 and a common data partition but the boot menus were messy (because I don't understand the booting process, I guess). I used GAG boot manager to choose Win XP or Xubuntu. The XP option went straight to XP - the only option that did what it should. Choosing Xubu took me to a sub menu - from here I could choose Xubu or Vista. Taking the Xubu option would then take me to Linux. Taking the Vista option brought up a third menu - from which I could choose Vista or a "previous version of Windows" (XP, of course). I think that this situation came about through adding OSs incorrectly though in my own defense I did try to follow documented procedures. I have never upgraded Xubu to 11.04 because I know it screws up booting even further and I never got the Clonezilla partition to boot.

After downloading and running "Boot-Repair-Disk : THE 'must-have' rescue CD" the "must have" in my case seems to mean I "must have" done something wrong. Text ran up the screen so fast I have no idea what it did, but at the end it appeared to be happy with itself and told me to reboot. I had a nice clean Grub menu replacing the old GAG one. Vista was still missing, but I wasn't worried. I tried the option to go into XP - before starting it ran scandisk on the C:\ drive for ages, then  rebooted itself again. I still had my nice new Grub menu, and I took the XP option again. Once more it went straight into scandisk before  starting - but this time it ran on my data and Vista partitions before  finally it loading up into XP. From XP I could see the data and Vista  partitions in "My Computer" and I could access the files OK. Scandisk did  report that it found errors on all three partitions, which it said  successfully repaired.

I then tried to reboot to check out the Linux/Vista installations. However, the grub menu has now gone and I get:

no module name found
Aborted. Press any key to exit

Pressing a key clears the screen and replaces the text with:

Non-System disk or disk error
replace and strike any key when ready

Booting from my GAG CD - all the partitions are all shown but the only OS that I can boot is XP. Attempts to boot from Vista's partition gives:

BOOTMGR is missing
Press Ctrl-Alt-Delete to restart.

However the machine is frozen at this point, needing a power cycle to restart. Attempting to boot Xubu gives:

no module name found
Aborted. Press any key to exit

I do not know about the Xubu installation as I only have an installation CD, not a Live one. (I live in the middle of nowhere with a slow Internet connection so downloading one is out of the question until Monday!)

Frightening stuff. I am hoping to start a restore of the entire drive (about 9 hours required - not a massive disk but a slow interface), and I am going to live with my multiple menus while I try to learn the boot process!

As a sideline, pages that the links in the line:

**Download:** [direct link]("http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download") (md5 is on [this page]("https://sourceforge.net/projects/boot-repair-cd/files/")).

do not show what the MD5 checksum should be, they just take you to the ISO download. Again, perhaps foolhardy of me because I used a download that may be corrupt. however, I couldn't find what the MD5 checksum should be, even after searching on Google for it.

---

### Post by YannBuntu on 2011-09-26
@Scooby-2 : to get the md5, just click on the (i) icon. Please indicate your Boot-Info URL so that we can help.

---

### Post by Borunco on 2011-09-26
I just wanted to say i have used boot-repair from the down load and have installed it on all my computers. The program has worked perfect every time i have used it. two days ago i burned the new rescue cd and used it. DUDE AWSOME JOB, thanks for the work you have done here. keep up the great work
borunco ):P

---

### Post by Scooby-2 on 2011-09-27
> **YannBuntu said:**
> @Scooby-2 : to get the md5, just click on the (i) icon. Please indicate your Boot-Info URL so that we can help.

Thank you for the response, YannBuntu. Please excuse my ignorance but I do no know what an "(i) icon" looks like.... sorry. I also tried searching the page text for "MD5" and "sum" but without success.

In the meantime I used a live CD to get on the internet to try and figure out what to do. I opted to try and recover Vista, so I booted from the installation disc and took the option "Repair your computer" after entering after entering language, time/date format and keyboard layout. It found the Vista partition and successfully recovered it, but failed to see the XP installation. I then used a program called Neosmart, which recovered both my Xubuntu and XP partitions successfully.

What I have now is my original GAG menu, but only the Vista option works (BOOTMGR missing from the XP option, no module name found for the Xubu option). However, the working Vista option takes me to another new menu from which I can choose, and then load, XP. I can also choose the Xubu option - and that takes me to the GRUB2 boot menu I used to have, from which I can then boot into Xubu.

The upshot is that my menus are still a mess but I can access all 3 OSs! 

FYI the output from bootinfo is at [http://paste.ubuntu.com/697478](http://paste.ubuntu.com/697478) if you want to see the output from a screwed up system! BTW I never was able to install Clonezilla successfully - it just gives a black screen with a flashing cursor at the top lhs of the screen.

---

### Post by YannBuntu on 2011-11-25
**@all:** I just updated Boot-Repair-Disk ISO with last version of Boot-Repair.

---

### Post by sprintexec on 2011-11-25
I recently mangled the partitions on my Aspire 4810 and could only get back in using a live CD. After much searching I found Yann's post(s), contacted him and had first class help. I am happy to recommend his expertise to you, and also wish to thank him for his valuable support. 
Yann I now have a dedicated Ubuntu partition on the Acer and plan to do the same on other installs on my desktops. Once again thank you. :cool:

---

### Post by YannBuntu on 2012-01-13
**@all:** I just [updated Boot-Repair-Disk ISO]("https://sourceforge.net/projects/boot-repair-cd/files/") with last version of Boot-Repair. If you own an older CD or USB, **it is recommended to update your disk** to avoid application update break.

**@sprintexec:** thanks for the comment, happy Ubuntuing :)

---

### Post by ubuntubrian on 2012-03-15
I'm trying to reset the grub menu on a usb drive so it will boot. It is a clone of my HD which is set to boot from the first HD and so I think the cloned drive is finding my HD instead of booting itself. I downloaded and burned the Boot-Repair-Disk but it doesn't boot and my HD boots up again. I tried booting a GParted cd and that booted fine. Any ideas for both issues?

---

### Post by ubuntubrian on 2012-03-15
And I tried the Ubuntu-secured-remix 64bit, which is what my chipset is, and it won't boot either. The drive spins and there is a long pause while the cursor blinks and then it boots the HD. Again, the GParted cd boots fine so I have no clue as to what is happening.

---

### Post by YannBuntu on 2012-03-16
Hello UbuntuBrian,

did you check the md5 of your ISOs before burning them ? did you burn them with minimum burning speed ?

For information: Ubuntu-Secured-11.10 is based on Ubuntu-11.10 , and Boot-Repair-Disk is based on Debian-Stable. That means you should have the same problem with an Ubuntu or Debian CD, please check.

Last idea: create a live-USB (eg. via UnetBootin, because Ubuntu USB-creator doesn't work with Debian/Boot-Repair-Disk)

---

### Post by ubuntubrian on 2012-03-16
Thanks for the response. I am able to boot an Ubuntu Maverick live cd. I did check the md5 and it was good and I burned at 10x. I could try a lower burning speed but that still doesn't explain why I can't boot the ubuntu-secured cd.

In any case, I was able to correct my particular problem of not being aboe to boot a usb drive that is a clone of my HD. turns out both drives had the same UUID so with a little editing and help from my local Linux group I was able to correct the problem. Still would be nice to have the Boot-Repair Cd handy in case!

---

### Post by graeleight on 2012-04-23
I downloaded the ISO and created working disk. I get the first menu and after selecting it about a minute later I get a a black screen with a white box. The top of the box has the debian swirl and the word debian. The input box is asking for userid? 

What do I use?

---

### Post by YannBuntu on 2012-04-24
**@graeleight:** maybe your PC is too recent for Boot-Repair-Disk (based on Debian stable). Please try to run Boot-Repair from Ubuntu Secured Remix (based on Ubuntu 11.10).

**@ubuntubrian:** sorry for the late answer. For information Maverick (=10.10) is obsolete now. Please can you try to boot on Ubuntu 11.10 and tell me if it works?

---

### Post by YannBuntu on 2012-05-05
A new Boot-Repair-Disk ISO is available. Same download link !

---

### Post by kdane4 on 2012-05-05
Thanks Yannubuntu for this wonderful tool.. Saved me a lot of times from grub problems and I usually refer it to people who's having boot problems. :)

Im gonna download the new version now because its really handy!! 

Thanks again!!

---

### Post by mtbreaux on 2012-05-11
FIRST, thank you for developing a way to repair your ubuntu installation without a reinstall. I know that resources like ubuntu would not be around with dedicated people like you supporting the different needs of the community.

SECOND, This is a brand new installation and I have tried twice to do the minimal installation and each time this boot issue has happened. I am hoping for a way to get this to work on my desktop. The box is a supermicro whitebox with two 500GB drives in a raid 1 array. I will use this as a desktop in my server room at work so I don't have to run back to my desk anytime I need to look something up. It will also serve as a way to connect via serial cable to any of my switches, routers, etc. I know none of this really matters but want you to have a full picture. I downloaded your iso and burned it and it boots perfectly fine into boot-repair but it doesn't find the OS. 

The pastebin is here: [http://paste.ubuntu.com/981823/](http://paste.ubuntu.com/981823/)

I can see from the log it finds the hard drives but it seems to not be able to tell it is a RAID. It does give me some weird message about installing dmraid but then gives me another about how dmraid can interfere with MDraid. I have tried it with dmraid installed and not installed. Any help is greatly appreciated.

---

### Post by oldfred on 2012-05-11
@mtbreaux
I do not know RAID, but report is showing Windows on sda and Linux on sdb. Normally with RAID it will at least show identical partition layouts for both drives. Are you sure you have RAID?

What type of RAID, BIOS or "fakeRAID"? or a hard ware type?

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)
Software RAID w/mdadm driver
[https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html)
[https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html)

For RAID, you have to use the alternative installer or server installers as they include the extra drivers, where the standard desktop does not include RAID as for desktops it is not common. (nor in my opinion required, but some use it).

---

### Post by mtbreaux on 2012-05-11
Ok makes sense. I will just use softRAID instead of the fakeraid ICH9 controller. Thanks for your help!

---

### Post by YannBuntu on 2012-05-30
**@all:** i just updated the Boot-Repair-Disk ISO with the very last version of Boot-Repair.
[https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by cigtoxdoc on 2012-07-04
With all due respects to the creator, I just ran into some problems trying to recover the 64-bit version of 12.04 LTS.

You software wants to connect to the Internet to do a repair.  Your software tells me it CANNOT connect to the Internet.  HOWEVER, the ICEWEASEL browser you included with your ISO image CAN CONNECT with the Internet.  I would send you the output of your trouble file, but your softrware won't connect to a printer or let me save to  USB.  I tried using my YAHOO account and I tried using one of my webmail accounts, but ICEWEASEL blocks the login.

I am done loading another image of your software.

John

---

### Post by drs305 on 2012-07-04
John,

Check in one of the  /tmp subfolders for a file called something like "log1" (you can look at the timestamp to figure out which subfolder and file). From what I recall, I found a copy of the script results there with a name containing "log" in the title. I think there were 2, with the original "log" or lower number "logX" being the log before Boot Repair ran the fix, and the "logX+1" being the results after the repair attempt.

YannBuntu may log on to give you more accurate information.

---

### Post by YannBuntu on 2012-07-04
**@cigtoxdoc:** do you use Wi-Fi? if yes, please try wired connection. Even with this problem, you can click "Create BootInfo" and indicate us the BootInfo summary that will appear.

**@all:** Boot-Repair uses this command to detect internet, do you know a more reliable one?
```
[[ "$(wget -T 10 -q -O - checkip.dyndns.org)" =~ "Current IP Address:" ]] && echo connected || echo no-internet

```

**@drs305:** the log is located in /tmp/boot-sav-XXXXX , but it's easier to get it via the "Advanced options" -> "Backup partition tables, boot sectors and logs" button

---

### Post by cigtoxdoc on 2012-07-04
My PC was hooked to the Internet using a hardwired ethernet cable.  No Wi-Fi here.

How about setting your program so that it activates Eth0 by default?

John

---

### Post by YannBuntu on 2012-07-05
Boot-Repair can't act on the network (this is the job of the NetworkManager tool), it just can check if Internet is connected or not.

Do you have the same problem when using Boot-Repair from a Ubuntu12.04 (or [Ubuntu-Secure-Remix 12.04]("https://help.ubuntu.com/community/UbuntuSecureRemix")) ?

---

### Post by cigtoxdoc on 2012-07-05
> Boot-Repair can't act on the network (this is the job of the NetworkManager tool), it just can check if Internet is connected or not.

I do not understand what you mean.  I am not a IT professional.  Again, if ICEWEASEL can find the internet, what can't your software find it?

> Do you have the same problem when using Boot-Repair from a Ubuntu12.04 (or Ubuntu-Secure-Remix 12.04) ?

I am using Ubuntu 12.04 (64-bit).  My 32-bit Ubuntu 12.04 are working fine and can afford to mess with them.

Again the question:  first time I used your software, it gave results better than expected.  How do I make your software give the same GNU GRUB menu on boot that it did the first time I used it?

John

---

### Post by YannBuntu on 2012-07-05
> **cigtoxdoc said:**
> if ICEWEASEL can find the internet, what can't your software find it?

As written in my last post, it's a problem of Boot-Repair which wrongly thinks there is no internet connection.
I just added an option in Boot-Repair's PPA (package boot-sav >=94, will be available in ~30min) to workaround this problem:

[IMG]http://pix.toile-libre.org/upload/original/1341502747.png[/IMG]

To use it, run Boot-Repair, update it, click "Advanced options" and untick the "Check internet" option.


> **cigtoxdoc said:**
> How do I make your software give the same GNU GRUB menu on boot that it did the first time I used it?

We need your logs. Please run Boot-Repair's "Recommended repair" (untick the "Check internet" option if necessary), and indicate the URL that will appear. If still not good, run B-R, click "Advanced options", click "Backup partition tables... logs", save the ZIP file somewhere and attach it to a new thread [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=333") (and indicate the link to this thread here please).

---

### Post by YannBuntu on 2012-08-20
@all: I improved internet detection, and removed the "Check internet" option.

---

### Post by YannBuntu on 2012-09-17
**@all:**
I need your help to continue improving Boot-Repair:
[http://ubuntuforums.org/showpost.php?p=12239465&postcount=538](http://ubuntuforums.org/showpost.php?p=12239465&postcount=538)

Thanks in advance ! :)

---

### Post by YannBuntu on 2012-10-03
New wallpaper for Boot-Repair-Disk:

[[img]http://pix.toile-libre.org/upload/img/1349271115.png[/img]](http://pix.toile-libre.org/?img=1349271115.png)

It's a picture CC-by from Steve-A-Johnson. I hope you like it :)

---

### Post by YannBuntu on 2012-10-12
Dear all,

in order to improve the compliance with Debian standards, i disabled the proposal to update the software at the startup of Boot-Repair.

So from now, the update procedure (from Boot-Repair-Disk) becomes:

connect internet, update your package list, remove boot-sav and install boot-repair:
```
sudo apt-get update; sudo apt-get purge -y --force-yes boot-sav; sudo apt-get install -y --force-yes boot-repair
```

or download the last ISO

---

### Post by SuperFreak on 2012-10-13
I have an UEFI Bios and a working bootable system. My boot time is about 45 seconds which seeems slow to me as I use an SSD for my OS. Is there a way of speeding up boot time?

---

### Post by YannBuntu on 2012-10-13
> **SuperFreak said:**
> I have an UEFI Bios and a working bootable system. My boot time is about 45 seconds which seeems slow to me as I use an SSD for my OS. Is there a way of speeding up boot time?

probably, but that's not the job of Boot-Repair. Please open a new thread for this.
(if i were you i would press Esc during the boot in order to see if there are any errors during the boot log)

---

### Post by YannBuntu on 2013-05-06
[B]*************************************************
*************           NEW:   Boot-Repair-Disk-64bit            *******************
******* [https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/) ****
*************************************************[/B]

compatible with UEFI / SecureBoot / LVM /RAID .... like Linux-Secure-Remix, but lighter ;)

---

### Post by arpanaut on 2013-05-07
@YannBuntu

Hey Man, just gotta say Thank You for this utility!
Today I just installed 13.04 on a brand new Lenovo H430, Win8 pre-installed, Uefi and upon reboot it would only boot to Win.
Installed Boot Repair on a live session, I ran the one click repair and Ubuntu booted just fine.
I didn't have time to check out the Win boot yet, as family member was impatient to get back to using Ubuntu. Ha!
Tomorrow I will have time to explore further and will report back.

EDIT: First Windows option in grub works fine.

Just gotta say, You Rock Man!!!

Also my after paste URL output Kept saying to report these messages to you, Is this good enough:
[http://paste.ubuntu.com/5640114/](http://paste.ubuntu.com/5640114/)  Or do you want it emailed to you?

The community wiki documentation is excellent and guided me very well, but one thing stands out...
On a system with uefi win8 pre-installed, that already has an efi partition it needs to be made clear that a new efi 
partition is not necessary and grub should be installed onto the existing efi partition.  This did not seem to be stated in any documentation, I found one small reference on Ask Ubuntu. It seemed to be the logical choice to me but might not be to less experienced users, and have seen people creating another efi part. (as per seemingly correct instructions) and getting into trouble.

Thanks Again, and this should be a default utility on the release iso, if not in the release itself.
Keep up the good work!

aside: Seems that the Lenovo bios/uefi on this system is easily adaptable to booting Linux in secure boot mode.

p.s. oldfred, You Rock Too... I would not have had the confidence to get this done without the documentation you provide daily concerning uefi. Kudos!

---

### Post by gmcauley on 2013-06-03
Is there some way to use boot-repair without an internet connection?

I just tried the 'Recommended Repair' and a message pop-up saying if I continued with repair without an internet connection, the system would be un-bootable.

I installed 12.04.2 LTS alongside Windows7 and could but I could not get a network connection during the installation, and the system is booting directly into Windows.

---

### Post by oldfred on 2013-06-06
Yann answered here on Internet connection issue:
[http://ubuntuforums.org/showthread.php?t=1769482&p=12679630#post12679630](http://ubuntuforums.org/showthread.php?t=1769482&p=12679630#post12679630)

---

### Post by gmcauley on 2013-06-06
> **oldfred said:**
> Yann answered here on Internet connection issue:
[http://ubuntuforums.org/showthread.php?t=1769482&p=12679630#post12679630](http://ubuntuforums.org/showthread.php?t=1769482&p=12679630#post12679630)

Thanks @oldfred. I was confused by the similarity of the threads.

---

### Post by Catbells on 2014-04-03
I downloaded the iso and copied it to a memory stick.  My laptop didn't automatically boot from it.  Your link to a tool to check the md5sum didn't help me very much.  A Windows 8 upgrade has put my GRUB out of use and I can't run any linux software until I've persuaded Boot Repair to run. It would be wonderful, if I could put my memory stick in a USB slot, start up my laptop and, instantly see Boot Repair pop up.

(I don't think I have a BIOS because the computer support man who I paid to create my dual boot system said I had UEFI but he found something called Legacy and, I think I saw somewhere on the Internet that UEFI replaces BIOS.  My user manual said that my BIOS would appear if I pressed F2 during start up.  I tried that and a DOSy box asked me to enter my password.  The manual didn't tell me what my password was.  :confused: @_@ )

> **YannBuntu said:**
> Hi SES1,
first check the md5sum of the ISO you downloaded, you can find the md5 by clicking on the (i) icon of this page: [https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/), and the tool to check the md5 [here]("http://bipede.info/bipede/index.php?check-iso-devient-check-file-integrity").
If it is correct, please burn the CD with a slow speed..

---

### Post by oldfred on 2014-04-03
Legacy/BIOS/CSM all are the UEFI booting in the old BIOS boot mode. 
New UEFI systems can be set for either BIOS or UEFI. And how you boot install media is how it installs.

You can also boot Ubuntu and easily add Boot-Repair to the Ubuntu flash drive or DVD installer. Best to boot in same mode as install, but you do not have to just to run BootInfo report, so we can see details of your system.

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Catbells on 2014-04-04
Thank you OldFred, I understand better about UEFI now.

I went to [https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media) and got as far as:-
> You should see a new file called ldlinux.sys in the root directory of your flash drive. (Note that it is a hidden file, you might not see it in Windows Explorer; try dir /a F: from a command prompt). Now you can boot from your USB drive
The difficulty is that my new laptop (the would-be dual-boot one) didn't boot from my USB drive.  Boot Repair didn't start.

---

### Post by oldfred on 2014-04-04
You just about have to be able to go into BIOS to make or change settings. If password has been set you need that. Otherwise I just about have to assume this is not your computer.

---

### Post by Catbells on 2014-04-10
I'm in! Thank you for your help, Oldfred.  Boot-Repair encountered problems which I have e-mailed to [email]boot.repair@gmail.com[/email].  If I don't get a reply, I'll be asking for help again.

In the meantime, I have tips for other users for whom a Windows upgrade has overwritten their GRUB menu.  Try an internet search to download winMD5sum to check the MD5 and unetbootin to make your USB flash drive bootable (syslinux didn't seem to work for me, but Boot Repair gives it a mention as though its the preferred one) both worked in my Windows 8.1.  My BIOS offered a way to set its choice of key (my BIOS wanted F12) to press at the start of boot to choose where to boot from.  I also enabled boot from disk but, don't know whether that was strictly necessary.

---

### Post by oldfred on 2014-04-10
Post BootInfo link here.
Yann got a job and had a baby, so he is not as available as he once was. I have not seen him in Forum for ages.

---

### Post by Catbells on 2014-04-10
It's wonderful of you to take an interest, Oldfred.  This is what I e-mailed Yann.

Boot Repair told me:
    [INDENT]       "Locked-ESP detected. You may want to retry after creating a         /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot         flag). This can be performed via tools such as gParted. Then         select this partition via the [Separate /boot/efi partition:]         option of [Boot Repair]."
     [/INDENT]     I didn't really understand it and, did as I was told - or tried       to. I hoped it would make more sense when I looked at gParted. I       found the Boot Repair Menu and its gParted menu item. Only it       didn't open, I tried twice. Then I typed gparted in XTerm.  It       said something about root privileges.  I tried "sudo gparted"        gParted wouldn't start because there was a segmentation fault and       I shutdown my laptop.  It occurred to me that Boot Info might be       useful so I booted into Boot Repair 64 bit again.  Boot Info said       to e-mail you [http://paste.ubuntu.com/7227472/](http://paste.ubuntu.com/7227472/).        Hope you are able and willing to help.  I mentioned the different       sessions in case you were expecting to see the gParted in the Boot       Info text.
    
     Boot Repair was booted from a USB flash drive which also had an       old Ubuntu Live CD on it.  I used syslinux on it to make it       bootable.  It worked in that I was able to boot a trial of Ubuntu       but not Boot Repair.  I deleted everything except the syslinux and       boot-repair-disk-64bit.iso.  Boot Repair wouldn't boot.  I used       unetbootin to make it bootable and, it worked, hope this isn't what prevented Boot Repair working.

---

### Post by oldfred on 2014-04-10
You show /ubuntu folder in efi partition which would not be a locked efi?

Boot-Repair picks up on this issue.
 grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477)

Boot-Repair is just a script that runs in the Ubuntu live installer or can be a full ISO bootable repair installer. If you have live installer without persistence you will have to download each time you reboot or may have to reinstall every time.

The locked efi, is something in the FAT32 efi partition. Supposedly there is no way to lock that and it is only FAT32, so some bug in FAT32 partition? 
A few have been able to run chkdsk from Windows on the efi partition and fixed it.
But most have just had to fully back up the entire efi partition - it is not large. Then totally delete it with gparted in live system, and then recreate it and restore data from backup.
The efi partition is a FAT32 formatted partition with the boot flag (if using gparted). It is only on gpt partitioned drives and you can only have one efi partition per hard drive.

---

### Post by Catbells on 2014-04-14
Thanks again Oldfred.
[http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html](http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html) told me that to run chkdsk in Windows 8.1, I had to open File Manager, right-click on C: drive, Properties, Tools tab, click on the Check button.  I did this 4-5 times and each time, it said that there were no errors.  Then I shut-down, booted from Boot Repair and ran it following instructions.  It said it worked but that I should make sure I was booting from the file it named.  I shutdown, rebooted and went into my BIOS.  There seemed to be somewhere to change which file but it was greyed out. I exited the BIOS, waited and saw the beautiful sight of my GRUB menu, made my choice and saw the even more beautiful sight of my Ubuntu desktop.

Many thanks for your help :KS

Your signature says to close the thread when answered.  My issue is definitely answered but I think you would like me to leave the thread open for others with boot problems.

---

