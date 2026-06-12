---
title: "Dual boot: Purple screen of death when trying to boot Win 8.1"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by gome2 on 2014-09-05
Hi to all! ):P

First of all I wanted to thank this community because it helped me a lot (before I even got a member) with setting up my girlfriends neat ubuntu laptop! 

Now I have run into some problems.. and am hopping someone can help me. I know there have been and are numerous threads about dualbooting issues..but i haven't found a solution yet.

**_My setup is:_**
[LIST]
[*]Windows 8.1 installed on SSD 
[*]Ubuntu 14.04 installed afterwards on 1 TB Harddrive from Live-CD. 
[*]All in legacy mode. 
[*]fastboot is off. 
[*]Windows should not be in hibernation mode. 
[/LIST]

**_My Problem is_:**

Ubuntu boots well from grub. But if I try Windows (one of the three entries..:confused:?!) it hangs up in a purple screen..fan is blowing like hell, but nothing happens.. (should start from ssd, so why is the fan exploding :D?)
[U]

**What i have tried:**[/U]

[INDENT]Boot repair:
[/INDENT]
[INDENT=2]I'm gettin asked if my HDD (Ubuntu on) is a removable.
[/INDENT]

[LIST]
[*][INDENT=2]selecting no --> nothing changes. Windows not bootable  -->[ http://paste.ubuntu.com/8257164/]("http://paste.ubuntu.com/8257164/")[/INDENT]
 
[*][INDENT=2]selecting yes --> my laptop boots right into Windows..skipping grub --> [http://paste.ubuntu.com/8257282/](http://paste.ubuntu.com/8257282/)[/INDENT]
 
[/LIST]
[INDENT=2]
with boot repair disc back to ubuntu--> [http://paste.ubuntu.com/8257344](http://paste.ubuntu.com/8257344)

(I think this looks all a bit messed up know.. :( )[/INDENT]
[INDENT]
I tried video fixes in boot repair:[/INDENT]
[INDENT=2]from a post of oldfred:
> You may be able to do this from Boot-Repair.
 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply
[/INDENT]
[INDENT=2]
also setting the resolution (Grub GFXMODE) to native 1920x1080 did not give any results
[/INDENT]
[INDENT]
[/INDENT]


_**Probably helpful:**_

Output of */etc/default/grub*:

[INDENT]> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

[/INDENT]
 


hm.. I think I got every step I made covered..

with all the downsides, it's good to know that i CAN acces both OSs.. :p

 I still really do like Ubuntu and would like to use it even more (besides I have to in a not too far future) ..so any help is greatly appreciated!! :)

Kind regards,
Gome


PS: I hope all guidelines are followed (my first forum post ever) and i chose the right sub forum..

---

### Post by LostFarmer on 2014-09-05
There are some items in the boot-repair report that I do not understand why its there.
> 559 Presence of EFI/Microsoft file detected: /mnt/boot-sav/sdb3/EFI/Microsoft/Boot/LrsBootmgr.efi
560 Presence of EFI/Boot file detected: /mnt/boot-sav/sdb3/EFI/Boot/bootx64.efi
/dev/sdb3       1,950,453,168 1,953,525,167     3,072,000   2 XENIX root 
 Is there a EFI folder in sdb3 ? if so was Win8 first installed as an EFI boot with hdd GPT ?  Why do you have a XENIX file system ? (does not really mater)

With boot-repair set for no removable hdds: (Win will not boot)
at grub menu: (commands to be typed in is in **BOLD** then press enter at each line)
press **c**  to get into the command mode.
**ls  **to see what hdd is listed for the SDD hdd.  (the one with only 2 partitions)
[B]insmod part_msdos
insmod ntfs
set root='hdx,msdos2'[/B]  (x=SDD hdd # from above ls command)
**chainloader +1**
**boot**

Does it boot ?

Need to ask , when you have the 1t hdd set as removable ,will grub boot into Win ?  (will need to press what ever key for your comp to get bios boot menu and select the 1t hdd.) 'F2,F12, esc some common keys'

What brand/make is the comp and is it a lap , desktop or ?

---

### Post by gome2 on 2014-09-08
Hi,
Thanks for you quick reply! I had no Internet access the last days..so please excuse my delay :)

> **LostFarmer said:**
> 
What brand/make is the comp and is it a lap , desktop or ?
**Lenovo Y500 Laptop.**

As there was still Windows booting, I tried the following first.
> **LostFarmer said:**
> 
Need to ask , when you have the 1t hdd set as removable ,will grub boot into Win ?  (will need to press what ever key for your comp to get bios boot menu and select the 1t hdd.) 'F2,F12, esc some common keys'

When HDD selected in boot menu, nothing happens. black screen of death :D Grub doesn't show up.. (after 2 minutes..)  :(


So next I would (again) run the boot-repair-disc and switch back to ubuntu to check your other suggestions..
BUT the question arises - wouldn`t it just be easier to have fresh clean install of the two OSes? probably with wubi.exe...?
I really do consider this step..Could be much faster than searching around for some half baked solution...what do you think? the ploblem is, that still with an clean reinstall I dont't have the guarantee that everything would work out fine..
If I installed everything new.. should I have UEFI activated again?

Or just try your suggestions? (My problem is, that all the boot related stuff on my laptop seems like beeing really messi..and hopefully this will not at some time fall back on me..)

> **LostFarmer said:**
> There are some items in the boot-repair report that I do not understand why its there.

 Is there a EFI folder in sdb3 ? if so was Win8 first installed as an EFI boot with hdd GPT ?  Why do you have a XENIX file system ? (does not really mater)

With boot-repair set for no removable hdds: (Win will not boot)
at grub menu: (commands to be typed in is in **BOLD** then press enter at each line)
press **c**  to get into the command mode.
**ls  **to see what hdd is listed for the SDD hdd.  (the one with only 2 partitions)
[B]insmod part_msdos
insmod ntfs
set root='hdx,msdos2'[/B]  (x=SDD hdd # from above ls command)
**chainloader +1**
**boot**

Does it boot ?


Any second thought on rather installing everything new?  --> Ubuntu would be on the SSD, which would be very cool as well! :guitar:  :D

---

### Post by carl4926 on 2014-09-08
A valid question was asked about the original windows 8 install. Was it originally efi on gpt?
That at least would be standard.

IMO: You would be better using efi. But the partition tables must be gpt for windows 8

Having said that. It should work in legacy mode

If it were my install (and assuming you have the windows dvd)
I'd install windows in to a single partition, but you have to give it a poke in the right direction to achieve that. If you can spare room on the ssd for ubuntu /
and then create a /home on sdb ?

---

### Post by gome2 on 2014-09-08
I'm sorry..I don't know exactly anymore... I think it probably was an efi installation..and switching had something to do with install on SSD (msata)? oh man.. 

I could install windows on HDD no problem, so ubuntu would have the total 120 GB SSD!

So you would recommend installing Windows in (u)efi mode, then installing Ubuntu (wubi or clean-from-cd?) and normally it should work out..or is there anything in my hardware causing the failure? (I guess not)


is it possible to have a SHORT explanation of differences of legacy and uefi? and do you possibly have a site with an explanation on what can go wrong.. I know *you can google..* but since here are PROs present, one could have something in his bookmarks..thank you :)

---

### Post by carl4926 on 2014-09-08
wubi is no more I think

---

### Post by gome2 on 2014-09-08
thank you carl!
 i'll try a clean install to be sure every drive is in gpt mode and so on.. hopefully this works out (there is so much information out there..) 
So hopefully my next comment is from Ubuntu running on SSD and windows dualboot! ;)

---

### Post by grahammechanical on 2014-09-08
I do not see anything in either of the Boot Repair reports to suggest that Windows 8 is installed in EFI mode. But I do see this

> [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    in partition 112 [COLOR=#AA22FF]**for**[/COLOR] .
 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    in partition 112 [COLOR=#AA22FF]**for**[/COLOR] .

Grub is on both drives so that whichever one has boot priority it should load a Grub boot menu.

And this

> [COLOR=#666666]===================[/COLOR] Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sdb5 into the MBRs of all disks [COLOR=#666666]([/COLOR]except USB without OS[COLOR=#666666])[/COLOR].
Additional repair will be performed: unhide-bootmenu-10s

And this in both reports

> update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found Windows 8 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR] on /dev/sda1
Found Windows 8 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR] on /dev/sda2
Found Windows 8 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR] on /dev/sdb1
Found Windows Recovery Environment [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR] on /dev/sdb3
Unhide GRUB boot menu in sdb5/boot/grub/grub.cfg

could the presence of 3 Windows boot loaders be messing things up? Which windows boot loader are you selecting from the Grub menu? My guess and it is a complete and utter guess is that you need to load the Windows in sda2 because sda2 is the only partition with this

>    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


I do not think that Windows will load without winload.exe being run.

Regards.

---

### Post by gome2 on 2014-09-08
Hi [						 					]("http://ubuntuforums.org/member.php?u=1087323") 				 				 					 						 	[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"),

I tried every entry..not working. :(
this is so messed up with the tree entries... You are right about that.

So .. I'm backing up my data at the moment and will do a clean install.. for users with the same problems - I'll report back on how it went and what steps it took..probably needing help from the forum again.. :(

---

### Post by carl4926 on 2014-09-08
You can read the efi info for Ubuntu here
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Read it carefully

---

### Post by gome2 on 2014-09-10
I've reinstalled everything.

Set BIOS to EFI Mode.
started with win 8 installing on 1TB HDD (second drive)--> updates updates updates--> win 8.1 
Installed Ubuntu 14.04. 64bit from Disc to the SSD.

this is my current state: [http://paste.ubuntu.com/8307462/](http://paste.ubuntu.com/8307462/)

Unfortunetely Windows is not booting from grub and showing me some error (no purple screen..)
This is already known as *bug #1091464*. see below for bug report.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

The thing is that my secure boot is disabled..was so as default in my BIOS settings.. so again some confusion :)

BUT: as I have a dedicated button to get in to BIOS/Boot selection,  I can (If HDD selected) boot *almost* directly into Windows..

Would you guys replace GRUB with the solution mentioned in post #11 in the bug report (installing *rEFInd boot manager*)? I would probably mess things up again..and am reasonably fine with how it's working..

Anyways, a big THANKS to all who have contributed and tried to help!!

---

### Post by LostFarmer on 2014-09-10
[QUOTE}Unfortunetely Windows is not booting from grub and showing me some error[/QUOTE]  what error ?  It might point to the problem.
I do not see anything in the boot-repair report that is bad.

You may want to try adding linux menu in the Win8 bcd store boot option.  You will need to do a web search on how, best to use Win commands not a third party method.  You would need to change the comps EFI boot order and place Win8 first.  Not hard to do with linux 'efibootmgr' command.  I am also sure it can be done via Win 8.   You would be booting into Win8 boot menu first , and selecting linux would boot into grub.

I have read the rEFInd boot manager should work but not in all cases.

---

### Post by gome2 on 2014-09-11
Thanks for you answer!
> **LostFarmer said:**
> > Unfortunetely Windows is not booting from grub and showing me some error  what error ?  It might point to the problem.

I hope you can read this error:
[ATTACH=CONFIG]256349[/ATTACH]

> **LostFarmer said:**
> I do not see anything in the boot-repair report that is bad.
At least that's nicely set up right now.. :)

> **LostFarmer said:**
> You may want to try adding linux menu in the Win8 bcd store boot option.  You will need to do a web search on how, best to use Win commands not a third party method.  You would need to change the comps EFI boot order and place Win8 first.  Not hard to do with linux 'efibootmgr' command.  I am also sure it can be done via Win 8.   You would be booting into Win8 boot menu first , and selecting linux would boot into grub.

I have read the rEFInd boot manager should work but not in all cases.
ok.. do you know or have any reference in what cases rEFInd won't work? this option (besides the fact, that i actually do not really want to replace GRUB..fearing the potentially mess with a ?broken? bootloader..) seems cleaner to me than having two bootloaders booting into each other (I know this is how it goes..but for booting to ubuntu, which is my primary used OS from now on, it's a bit cumbersome..).

Do you think trying rEFInd could potentially mess things up again? if not I think I would try this method first!

---

### Post by LostFarmer on 2014-09-11
from your pastebin:

```
efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0004,0002,0003,2001
Boot0000* EFI Network 0 
Boot0001* EFI Network 0 
Boot0002* Windows Boot Manager    HD(2,96800,32000,d5277145-d79d-4120-9be6-ef43b711c2c5)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS...
Boot0003* Ubuntu    HD(2,96800,32000,d5277145-d79d-4120-9be6-ef43b711c2c5)File(EFIubuntugrubx64.efi)RC
Boot0004* ubuntu    HD(2,96800,32000,d5277145-d79d-4120-9be6-ef43b711c2c5)File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device    RC
```

You have 2 boot entries for ubuntu , Boot0003 would be for secure boot off and Boot0004 for secure boot on.
First would try both entries to see if Win8 would boot , then try with secure boot enabled.

The error message, do not know if it is from grub or comp's efi firmware.  Would check if there is a newer grub.
My interpretation of error would be Win's bootmgfw.efi can not be found.  

Have no knowledge about rEFInd or using Win8 to boot linux, only minimal reading. Some posts on rEFInd [http://forums.linuxmint.com/viewtopic.php?f=46&t=97221&sid=1b6a62984d75e4433e4aa4d7467bd19b&start=200](http://forums.linuxmint.com/viewtopic.php?f=46&t=97221&sid=1b6a62984d75e4433e4aa4d7467bd19b&start=200)

---

### Post by oldfred on 2014-09-11
You have an Ubuntu install on a MBR drive, but using UEFI from the gpt drive to boot. I used to think that was impossible but someone else has the same configuration and I think it worked.
But much better to either use just gpt partitioning and UEFI or MBR partitioning and BIOS. And with Ubuntu you can use gpt partitioning and boot in BIOS mode. 

I also then like to have an efi partition at the beginning of every drive so each drive could be booted without the other drive. Otherwise if boot drive fails you can only boot from your Windows repair or Ubuntu live installer. Several users posted when traveling and had no repairCD or flash drive and could not boot or fix system.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by hossein4 on 2014-12-14
hi all, I have same problem with my friend's "lenovo z510", I read all your suggestion but I can't solve this,do you have any other idea?

---

### Post by oldfred on 2014-12-14
@hossenin4
I doubt you have exactly this thread's issue. He had mixed BIOS boot and UEFI boot in what should be an impossible configuration, the way his was configured.

Best to start your own thread and post link to summary report from Boot-Repair.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

