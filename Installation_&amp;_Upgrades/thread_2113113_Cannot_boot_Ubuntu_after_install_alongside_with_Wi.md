---
title: "Cannot boot Ubuntu after install alongside with Windows 7 Home 64bit"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by shestero on 2013-02-06
I fail to install Ubuntu alongside MS Windows 7 Home edition 64-bit on my just bought new Asus ZenBook Prime UX21A with 128G SSD.

First of all using 32-bit 12.04 LTS disk and external USB DVD drive I installed Ubuntu “alongside” Windows. All seems to be fine but after reboot no option to boot Ubuntu appears and Windows was so serious damaged that unable to boot. Hopefully it was able to repair itself or may be more correct to reinstall itself anew.
Now nevertheless I had some result – the volume was split by two and Windows was located only in the first.
I boot the DVD tried to install Ubuntu second time into second volume anew, reformatting it into ext2 (it was mentioned as sda5). That's time the Windows survey, but still nothing like GRUB Ubuntu option appears not during boot nor in the list of available systems to boot inside Windows (when you setting up the loader by Windows).

Thirst of all two dummy question:
1. What distributive should I use? Here [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime) mentioned, that if I have Windows 64-bit I am to use 64-bit Ubuntu (“NOTE: Ubuntu 12.04 64-bit is necessary in order to get UEFI dual booting with the stock Windows 7 image”). In download page I have to choose either Intel-32 or AMD-64 architecture iso, but my hardware is 64-bit with Intel CPU... 
What's there: [http://sourceforge.net/projects/ubuntu-secured/files/](http://sourceforge.net/projects/ubuntu-secured/files/) ?
May be I should better wait for 12.04.2 LTS which is expected in a week?
2. Here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) mentioned that I shouldn't mix UEFI and Legaci mode. But I cannot find how to switch this modes or how to detect which one I really need (although most possible UEFI).

---

### Post by Mark Phelps on 2013-02-06
> **shestero said:**
> I fail to install Ubuntu alongside MS Windows 7 Home edition 64-bit on my just bought new Asus ZenBook Prime UX21A with 128G SSD.

First of all using 32-bit 12.04 LTS disk and external USB DVD drive I installed Ubuntu “alongside” Windows. All seems to be fine but after reboot no option to boot Ubuntu appears and Windows was so serious damaged that unable to boot. Hopefully it was able to repair itself or may be more correct to reinstall itself anew.
You used the option to shrink Win7 using the Slider, right? That has been know to sometimes corrupt Win7 and render it unbootable.  Would have done better to come here and ask, first.

And, while anything is possible, it's very unlikely that Win7 will be able to repair the damage you did to it.  In that case, had you asked here, I would have told you how to create a Win7 Repair CD for free, which you would have now to repair the damage.

> 
1. What distributive should I use? 
The "AMD" 64-bit works with Intel processors, as well.
> 2. Here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) mentioned that I shouldn't mix UEFI and Legaci mode. But I cannot find how to switch this modes or how to detect which one I really need (although most possible UEFI).Don't work with UEFI, you will have to wait for someone else to answer that.

---

### Post by oldfred on 2013-02-06
You can post this. If you have an efi partition and drive is gpt then you have UEFI. Windows only boots from gpt partitioned drives with UEFI.

       sudo parted /dev/sda unit s print
    
How you boot install media from UEFI/BIOS menu is how it will install. If UEFI switch is on you should get two choices - one UEFI and the other BIOS. In BIOS mode you should only get BIOS boot. Then it installs in that mode.

---

### Post by shestero on 2013-02-07
> **Mark Phelps said:**
> You used the option to shrink Win7 using the Slider, right? That has been know to sometimes corrupt Win7 and render it unbootable.  Would have done better to come here and ask, first.

Yes, I do the slidering. But I've checked Internet before and found several optimistic article (“how to install Ubuntu”) which tell in a way that this very operation is safe and easy. Nor installation program warn me. I am sure that if it really sometimes corrupt Windows, developers should put some noticeable warning there.
...Only having some previous experience with Linux make me to do complete copy of SSD (sda) using dd before the installation (I didn't use this save point yet).

> **Mark Phelps said:**
> The "AMD" 64-bit works with Intel processors, as well.
Don't work with UEFI, you will have to wait for someone else to answer that.
But do all the binaries in this installation were optimized for AMD instructions? I am afraid/suspect it'll cause loosing performance if I use AMD binaries on Intel CPU (?)
Do binaries for Intel-64 exist somewhere?
What is ubuntu-secure-remix-12.10-64bit.iso (available through the link I mentioned in my first letter)?

---

### Post by shestero on 2013-02-07
> **oldfred said:**
> You can post this. If you have an efi partition and drive is gpt then you have UEFI. Windows only boots from gpt partitioned drives with UEFI.
[...]    
How you boot install media from UEFI/BIOS menu is how it will install. If UEFI switch is on you should get two choices - one UEFI and the other BIOS. In BIOS mode you should only get BIOS boot. Then it installs in that mode.

My drive is GPT, so I have UEFI.
I install the Ubuntu from DVD pressing ESC and choosing the external USB drive to boot. This (called “BBS (BIOS Boot...) menu”(?)) I used in many other notebooks to boot them not from default drive. Am I right and if no how I should boot the DVD  correct?

I find no UEFI/Legacy switch in BIOS. 
But I find the settings of some “boot options” list, where each option are associated with efi-file. There is only one option there now - “Windows”.

---

### Post by Mark Phelps on 2013-02-07
> **shestero said:**
> Yes, I do the slidering. But I've checked Internet before and found several optimistic article (“how to install Ubuntu”) which tell in a way that this very operation is safe and easy. Nor installation program warn me. I am sure that if it really sometimes corrupt Windows, developers should put some noticeable warning there.

It really does corrupt Windows -- as evidenced by the scores of folks who posted here after doing what you did only to find their Windows corrupted.

Developers don't read these forums, so why should they pay attention to ANYTHING that is said here?

---

### Post by oldfred on 2013-02-07
The 64bit is a standard and only a few things are different between them. 

       The binaries for AMD64 will also work on processors that implement the Intel 64 architecture (formerly EM64T), i.e. the architecture that Microsoft calls x64, and AMD called x86-64 before calling it AMD64. They will not work on Intel Itanium Processors (formerly IA-64).
       
 [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)
     
    
It is a bit of history on why AMD set the standard. Originally Intel licensed AMD as a second supplier as Vendors did not want only one vendor. Intel elected to create the totally incompatible 64bit version (Itanium) which required all new operating systems and software. AMD created a 64 bit with 32 bit capability backwards compatible based on Intel License. Intel sued that license did not cover that, lost and then since AMD was selling  lots of compatible chips made chips that also matched standard.

---

### Post by shestero on 2013-02-09
Still I have no clear road view; what should I do now?
How can I start installation in right mode?

I decided wait 6 days for 12.04.2 LTS AMD64 and try to install it into my second volume (just repeat what I have done with new DVD).

---

### Post by oldfred on 2013-02-09
You have a way to boot in either UEFI or BIOS, so there are switches somewhere. It may just be a UEFI on/off or BIOS/legacy/CSM or other compatibility setting with old systems. 

Once 12.04 is updated it should also work.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)

    
Asus with Windows 8 and UEFI
       Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

    
Older Asus with Windows 7 & UEFI,  newer versions of Ubuntu install a bit easier
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
(Phoenix Tiano). The every-other boot problem is a bit decieving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up. Yes, a stand-alone install of Win 7 SP1 has the exact same problem as Ubuntu. I suspect this is a Phoenix/Acer issue but who knows.
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)

            efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

### Post by shestero on 2013-02-16
I cannot find BIOS/UEFI switch in my notebook UX21A.
I also cannot find QuickBoot/FastBoot and Intel Smart Response Technology (SRT) switch. 

Today I sucessfully installed new Ubuntu-12.04.2 TLS AMD-64 using instructions: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
The only note that I find no boot-repair in it (althrough the article told that it should be "already included").

Just after installing the computer could boot Ubuntu but fail to boot Windows from GRUB menu ( [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383) ). (But COULD boot Windows from "BBS" menu coming by ESC! I can't really catch the logic of new fasion booting system). 
I boot it from USB DVD and boot-repair in default automatic mode fixed the problem with GRUB.

Everything seems ok now, only the screen brightness keyboard shortcuts (Fn+F5/F6) not working.

Thanx.

---

