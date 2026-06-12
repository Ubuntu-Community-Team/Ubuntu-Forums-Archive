---
title: "How to boot from USB on Windows RT/Lenovo Yoga 11? (Secure boot)"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by SargTeX on 2012-12-15
Hey people.

I recently bought a Lenovo Yoga 11 (ARM processor) and I want to install Ubuntu 12.10 on it. I already read that this is possible so...

According to my information, Ubuntu 12.10 supports secure boot. But I can't boot from USB on Windows RT (on Lenovo Yoga 11)... I tested it by:

1. Creating a bootable USB device (looks correctly, used Netbootin)
2. Booting from USB on Windows RT via: Settings -> change pc settings -> general -> Advanced start -> ...boot from usb device (I've had german labels, so the translations might not be exactly)
[U]
And after booting, Windows RT starts normally - seems like the USB device gets ignored.[/U]

Catbuntu adviced my @IRC to disable secure boot. But as I know so far this is only possible @ Windows 8 devices, not on Windows RT.

Any help?

Thank you very, very much :D This is very important for me as I need to develop on Netbeans and am not able to on Windows RT in cause of store/application restrictions (as we know it from windows...)

Best greetings,
SargTeX

---

### Post by rivera151 on 2012-12-16
Hello. I just bought this model and I am waiting for it to arrive. Just a heads up, if i understand correctly, the WIFI driver is incompatible with v >=3.5, so you might be stuck without web if you don't have a usb to ethernet adapter, or a compatible usb wifi adapter.
Can you confirm the wireless hardware model?

Also, check linaro, they have a ARMv7 build of precise, but I'm still not sure what to do with the downloads after downloading, but I'll get there eventually.

---

### Post by oldfred on 2012-12-16
All the articles says that the Windows specification is that on RT the Vendor is not allowed to offer to turn secure boot off. Unless someone has already jail broken it.

       x86 runs Windows 8
ARM run Windows RT
Windows RT has this new touch user interface called 'metro' that only runs apps you buy online from the microsoft app store. It doesn't run anything else. Its a lot like how an ipad works with itunes.
Windows 8 has everything Windows RT has, but it also has an extra tile called "Desktop Mode" where you can run software designed for desktop mode. It will also run software from previous versions of windows in "desktop mode".
            
More Details
[http://www.wired.com/gadgetlab/2012/10/windows8-windows-rt-explainer/](http://www.wired.com/gadgetlab/2012/10/windows8-windows-rt-explainer/)

---

### Post by rivera151 on 2012-12-16
I thought Quantal supports secure boot. Am I mistaken?

---

### Post by oldfred on 2012-12-16
I do not know if the ARM version supports secure boot. Plus hardware is a lot different than typical ARM system.

And we have found many cases where even though it is supposed to work with secure boot on, it only installed with secure boot off. A few systems will not install at all due to vendor UEFI bugs.

Some other Lenovo's have worked.
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

---

### Post by rivera151 on 2012-12-17
Well, I thought about cancelling my order, but then I saw this:
[http://blog.hansenpartnership.com/linux-foundation-uefi-secure-boot-system-for-open-source/](http://blog.hansenpartnership.com/linux-foundation-uefi-secure-boot-system-for-open-source/)

Maybe I'll get it to run, eventually. We'll see.

---

### Post by oldfred on 2012-12-17
Only very specific arm processors and configurations are supported.
[https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)

Of course there would not be a way to install anything other than the ARM. Just becuase your phone has ARM processor does not mean you can install Ubuntu on it.

---

### Post by rivera151 on 2012-12-17
Sorry to keep bothering, but you seem to know what's up. 
1. Is there anything that prevents me from compiling my own UEFI-compliant system from ubuntu sources? I'm willing to try and compile the system, even if as a hobby/learning project.
2. Is this a correct assumption?
I would suspect that the UEFI code is x86 specific, and might not be ready for compilation (must be ported), in which case I probably won't get far. If not, I think I can handle compiling for this system, even if it takes me a while and some drivers are still missing.

---

### Post by oldfred on 2012-12-17
I have not compiled code since z-80 modem needed assembly code changes & recompiling.

I think there is a lot of difference between ARM & x86 which would be re-writing not just recompiling. The Windows RT system will not run any Windows software. It is not Windows and from a marketing standpoint using Windows just confuses users. It only runs software from the Microsoft download center that has been rewritten for ARM.

I think what you are talking about is the same as "jail breaking". The Library of Congress approved jailbreaking for phones for a limited time as a test. Assumption is/was it was your hardware. But it generally is not approved for anything else and the license from Windows I am sure does not allow it. 

Forums code of conduct says we must comply with terms of use from other vendors.

---

### Post by rivera151 on 2012-12-17
I think I get it. Windows 8 devices are allowed to subvert the secure boot, but not RT because of the license specifically stating that you cannot install another OS. HMM. I might have to cancel after all.
Unless of course, installing means intruding into the factory installed hard drive. What if I want to run ubuntu on a sd card? Any way you look at it, its such BS

---

### Post by sigman on 2013-01-16
Hi, is there any update on this?

---

### Post by vitj on 2013-03-01
Did you have any success trying to compile for ARM. I'm in the same boat here, mobile device running Windows RT that I badly want to replace with Ubuntu(anything).

---

### Post by rivera151 on 2013-03-01
The MS agreement with manufacturers of Windows RT tablets specifically states that the manufacturer may NOT provide means to access the UEFI settings (i.e. like BIOS settings, you would set the boot disk/partition here).  Thus, there will not be a way of booting to an alternate partition untill that agreement gets fixed.

Linux Foundation has worked on a workaround to the inaccessible UEFI, so that machines can be booted without having to mess with the UEFI settings, but this is only on x86.  Doing this on ARM opens up possible breach of license terms with MS and exposes the LF to litigation with MS, thus it is unlikely we will see Linux booting on the Yoga 11.

---

### Post by vitj on 2013-03-15
Have you tried booting to a command prompt and turning on legacy boot by running 
> [INDENT]**bcdedit /set {default} bootmenupolicy standard**
[/INDENT]

I have mentioned this here [http://ubuntuforums.org/showthread.php?t=2116345&p=12558522#post12558522](http://ubuntuforums.org/showthread.php?t=2116345&p=12558522#post12558522) but haven't tried it yet.

---

