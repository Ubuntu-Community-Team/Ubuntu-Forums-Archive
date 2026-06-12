---
title: "Bios-Grub: 12.04 dual boot windows 8/EasyBCD"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by joey22 on 2013-02-17
I was trying to install Ubuntu 12.04 LTS alongside Windows 8 on my new laptop having the following partitions:

[LIST]
[*]/boot (sda6)
[*]/ (sda7)
[*]/home (sda8)
[*]swap (sda9)
[/LIST]
I had set the device for bootloader partition installation to sda6. I later on plan to use EasyBCD to add Ubuntu to my windows MBR. As I have done before and it always worked like a peach.

Now I got the message that it will probably not work and that I need the bios-grub partition instead of the /boot partition. I get why (GPT/EUFI)...

If I convert my /boot partition to the bios-grub partition at sda6;
Does it still require me to set my boot loader installation to sda6 if I want Grub on another partition than the MBR?
Will  it leave my MBR intact?
Will grub2 install on sda6?
Will I still be able to work with EasyBCD from windows selecting the option GRUB2?

Thanks in advance!

---

### Post by darkomano on 2013-02-17
EasyBCD is violating Microsoft Copyright pretending easyldr is its own product.
easyldr is ntldr a Microsoft development !
 
Neosmart company are software crooks, they just steal foreign work.
 
DO NOT USE THEIR SOFTWARE !
 
EasyBCD violates also grub4dos copyright - neogrub/autogrub is grub4dos.
No copyright notice. No GPL compliance. 
 
I wonder why the community is tolerating Neosmart software crooks all these years.
 
It seems there is some kind of omerta (keep secrets or you die - Italian mafia).
 
---------------------------------------------------------------
The answer to question is 
1. EasyBCD does not know about UEFI/GPT.
2. There is another booting sequence with UEFI/GPT - no MBR code, no partition boot code. This is beyond EasyBCD.

---

### Post by oldfred on 2013-02-17
@darkomano
While with UEFI, I see no reason for EasyBCD, I think you are wrong. 
ntldr is only for XP.
grub4dos is available for anyone to use, but they have modified it so it is not the standard grub4dos.
Supposedly the newest EasyBCD will work with UEFI, but again it is not required.

With UEFI you also have gpt partitioning. The only MBR is to have one partition table entry to tell old partition tools that drive is fully used. The MBR can be used in gpt to boot in BIOS mode but with UEFI in use for Windows you have to install Ubuntu in UEFI mode to easily dual boot.
You only need a bios_grub partition if installing Ubuntu in BIOS mode (I use it for my BIOS system with gpt drives).

How you boot install media is how it will install. So boot flash drive in UEFI mode not BIOS/Legacy/CSM or whatever your system calls it.

Most new systems do not need a separate /boot.

The efi partition is designed to be used by many systems. It is like having an unlimited number of MBR each designed to boot an install. Each folder is in effect an MBR. But some UEFI systems only boot Windows (bad UEFI design).

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
For systems that only boot Windows, boot repair will rename files to make it work.
       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    
Grub also has a bug in creating correct UEFI chain entries. Boot-Repair will fix.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by darkomano on 2013-02-17
@oldfred
 
>  
grub4dos is available for anyone to use, but they have modified it so it is not the standard grub4dos.


 
1. Can you please give me the source/reference where Neosnart / EasyBCD license confirms that they use grub4dos as source.
 
2. Can you please give me the link of the modified grub4dos source. (GPL)
 
3. Can you please give me the link/source where Neosmart states that they have renamed ntldr to easyldr.
 
PLEASE DO NOT DEFEND SOFTWARE CROOKS.
 
My statement that there is some kind of omerta for Neosmart / EasyBCD seems confirmed.
 
Wikipedia: ([http://en.wikipedia.org/wiki/Omert%C3%A0](http://en.wikipedia.org/wiki/Omert%C3%A0))
**"Omertà**[[1]]("http://en.wikipedia.org/wiki/Omert%C3%A0#cite_note-1") ([/]("http://en.wikipedia.org/wiki/Help:IPA_for_English")[&#629;]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[&#712;]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[m]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[&#603;r]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[t]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[&#601;]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[/]("http://en.wikipedia.org/wiki/Help:IPA_for_English"); [SIZE=2]Italian pronunciation: [/SIZE][[omer&#712;ta]]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_Italian")) is a popular cultural attitude and [code of honour]("http://en.wikipedia.org/wiki/Honor_code") that places heavy importance on a deep-rooted "[code of silence]("http://en.wikipedia.org/wiki/Conspiracy_of_silence_(expression)")", non-cooperation with authorities, and non-interference in the illegal (and legal) actions of others....."
 
-------------------------------------------------------------------------
About UEFI/GPT - a protective MBR does not have information about partitions (the whole disk is one partition), there is no MBR boot code.
Mixed MBR's are not standard.

---

### Post by oldfred on 2013-02-17
@darkomano
Please direct your questions to EasyBCD. We are here to help users with Ubuntu and this is joey22 thread to help him not discuss other issues.
Do not hijack anothers thread.

Also you agreed to this to be part of this forum;
Ubuntu Forums Code of Conduct
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
> Attacks and derogatory terms of any kind are not welcome. This includes  references to other operating systems and the companies that produce  them.



---

