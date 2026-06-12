---
title: "Can I Replace Windows with Ubuntu in HP-700 Win 8.1"
date: 2015-06-29
forum: Installation &amp; Upgrades
---

### Post by Duplin on 2015-06-29
I bought a new HP Envy-700 from Best Buy yesterday that was preloaded with Win 8.1...which I absolutely hate.  I have tried pretty much every option I could find to dual boot.  I can get Uubuntu 14.04 to install with no problem, but no matter what I do, I can only boot to Windows.  I did the enable/disable secure/legacy thing, and the installation went fine...until it was restart time...then same old Win 8.1.  I've reinstalled Ubuntu twice now, no help.

I don't really want Win on my computer.  My question is, if I select the replace/use the entire hard drive for the Ubuntu install option, will that screw things up worse...or will it load Ubuntu since there is no other OS on the drive?  I created a complete recovery disc.  If I can't get this fixed within a day or two, the machine goes back to Best Buy and I'll buy a white box again off eBay...which I should have done anyway.

Thanks very much for any advice.

Dennis

---

### Post by oldfred on 2015-06-29
HP has modified UEFI to boot by description and only valid description is "Windows". That is not UEFI standard. But one user recently posted that in a new HP was a convoluted way to enable other boots. Have you updated UEFI to newest version from HP?
But most with HP use one of several work arounds that have been found.
If dual booting you can still boot the /EFI/Boot/bootx64.efi entry which is a hard drive entry. We just make that file really be grub, it often is a copy of Windows own efi boot file.

If totally removing Windows you can just change the UEFI description from "ubuntu" to Windows for the grub entry. That may be preferred as a major grub update will create new grub efi files and have to be copied again.

If you need details on copying grub to /EFI/Boot they are in link in my signature and also other HP users:
       HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 

 Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

This user said the bcdedit worked with dual boot.
 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)

[URL="http://ubuntuforums.org/showthread.php?t=2131886"]
[/URL]

---

### Post by Duplin on 2015-06-29
Update:  OK, I gambled and it worked.  I used the 'use entire disk' option in Kubunu 14,04, and it rebooted as it should have.  I tried shut down and restarted three times each..all is well.  Take that, HP...

---

### Post by oldfred on 2015-06-29
Glad to see it worked without issue, that seems to be something new with HP.

I am thinking of a new laptop later this year & HP was off the list, but now I may have to rethink that.

---

### Post by Duplin on 2015-06-29
> **oldfred said:**
> Glad to see it worked without issue, that seems to be something new with HP.

I am thinking of a new laptop later this year & HP was off the list, but now I may have to rethink that.

Yeah, I'm pretty happy about it.  I haven't had Windows on my computer for 4 or 5 years, been using Ubuntu or Kubuntu LTS versions.  It'll take 2 or 3 hours now to get everything back to my tastes, but well worth the effort.  While I had Win, I tried Lightroom trial version...my personal opinion is Darktable is just as good, is MUCH easier to grasp...and it's free.  Both Ubuntu and Kubuntu, and probably other distros I have tried, are so stable now I really don't see why people continue to funnel money to Microsoft.

Anyway, thanks again for the advice and have a good day.

---

