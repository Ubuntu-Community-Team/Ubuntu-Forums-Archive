---
title: "Can't install Win7 on Oracle VM with Ubuntu"
date: 2015-01-12
forum: Installation &amp; Upgrades
---

### Post by vincej on 2015-01-12
There appears to be one of those internminable catch 22's. 

In order to install Win7 on Virtual box I need to have some Win7 AHCI drivers which are not present on the install CD. 

In order to make the drivers available I have to have a shared folder ( I presume ) 

In order to have a shared folder I have to have guest additions installed. 

You can not install Guest Additions through apt-get, you have to present the Host with an ISO image

When you try to present the ISO image through the guest drives dialogue you have to disconnect the primary DVD drive ... and boom you no can no longer install windows !! 

I am certain that my work flow has to be wrong, but I will be damned if I can see how or where. 

Ohh ... and the official docs off the Ubuntu site are absolutely wrong. If you download the guest additions they remove VirtualBox. 

So anyone with some help ??? 


Many Thanks !!!

---

### Post by TheFu on 2015-01-13
I've never had this issue. The AHCI stuff **is** in the base Win7 install, in my experience.

You can connect up multiple "virtual" DVD drives to a VM - assuming that when you say "Oracle VM" you really mean virtualbox. I've never needed that.

Perhaps your machine config isn't good?  [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) provides all the settings so virtualbox works and isn't slow.

---

### Post by MAFoElffen on 2015-01-13
Agree with Fu.

First panel of "New, Create VM" has the environment settings. Select Windows as the OS, then the version in the next combobox. When you do that, the VM application adds the appropriate virtual appliance drivers to work with that. (Behind the scenes.)

---

### Post by vincej on 2015-01-15
I have tried everything under the sun. I have also been on the VirtualBox forum and they don't the answer either. 

Every time I just use the defaults I get a message from Windows: "A driver is missing from a CD/DVD". WEll I am flummoxed as it appears AFTER Win7 had started, so, it is reading the DVD. 

Theoretically, it should just run using the defaults. The only thing I add is extra memory and I reduced the swap. 

If anyone has the slightest idea PLEASE LET ME KNOW. 


Many thanks !!

[ATTACH=CONFIG]259257[/ATTACH]

---

### Post by TheFu on 2015-01-15
> **vincej said:**
> 
Theoretically, it should just run using the defaults. 

Actually - No, you shouldn't. The defaults are not tuned.  The link above has been working for people around the world for years. It takes 30 minutes to try it and there isn't anything to be lost. These are just VMs after all.

Since I don't use virtualbox anymore, I won't test it.  KVM is my preferred virtualization hypervisor these days and has been for a few years.  OTOH, virtualbox is probably the least evil choice (they are all evil) for desktop-on-desktop virtualization.

---

### Post by vincej on 2015-01-15
Ok great - can some one anyone give me a Virtualbox Windows 7 recipe WHICH THEY KNOW AND HAVE TESTED to work on Ubuntu 14 ??

---

### Post by SeijiSensei on 2015-01-16
I'd be suspicious of your installation medium.  Is it a generic version of Win7, like the [OEM versions]("http://www.newegg.com/Product/Product.aspx?Item=N82E16832416806"), or one shipped by the machine's manufacturer and custom tailored to the machine you are using?  I've never had a problem installing an OEM version in VirtualBox.

---

### Post by vincej on 2015-01-16
Thank you for your reply. First, I tried installing the OEM version shipped with my Dell desktop. However, it does say on the disc that the required drivers are on a separate disc. I tried to load those drivers, but Ubuntu would not read the disc, so that effort failed.  Then I downloaded a copy from howtogeek.com.. That also failed for the identical reason. 

I am stumped. 

thanks

---

### Post by TheFu on 2015-01-16
Sorry - I assumed you were using either a retail Windows or volume license Windows.

OEM Windows is tied to the hardware it was shipped on.  Trying to run an HP-Windows on Dell hardware doesn't work.  During install, it verifies the BIOS/MB claims to be what that vendor is allowed.  I don't think using OEM installs have worked inside VMs since WinXP. Vista and Win7 were definitely tied to the hardware. [https://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/re-use-windows-7-product-from-a-broken-laptop/fac50654-9ac7-4173-a4dd-22f8efebcece](https://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/re-use-windows-7-product-from-a-broken-laptop/fac50654-9ac7-4173-a4dd-22f8efebcece) explains more.

Microsoft Retail copies will work and Microsoft volume licenses, Developer Pak and Virtual Machine versions will work in VMs too.  Also, you can download a trial of Win8.1 directly from Micsosoft which will work for 30 days too.

---

### Post by vincej on 2015-01-16
Thanks for that. So for the sake of clarity, are you telling me that a downloaded version should also not work and I will have to purchase a copy ? 

Thanks

---

### Post by vincej on 2015-01-16
Additionally my OEM copy will not work on a Windows guest even on the same hardware since the guest is considered a "different" computer ?

---

### Post by TheFu on 2015-01-16
If the motherboard appears to be different to the installer (like a hardware VM will), then it won't work. The license is for 1 copy, installed on the machine it was purchased one. If you want some different license, contact Microsoft.

Sadly, Microsoft doesn't have a "like-a-book" license of which I am aware. They license by install count.

I do recall MSFT selling "family pak" licenses - think they had 3. Sorry, don't quote me on those. The last time I purchased anything with Windows was about 7 yrs ago.  License tracking is a main reason we don't deploy Windows in my company too, but none of this helps you.

If you download an 8.1 installer from Microsoft which provides a 30-day trial, it will work for that period. Of course, you can purchase a license key.  If you install a non-OEM version, I don't think your key will work.  OEM keys are locked to OEM installs. Ive been burned by this.

---

### Post by MAFoElffen on 2015-01-16
I'm not saying this, but... I have a mentor that teaches M$ Server classes (2012). He uses that same Eval disk on Hyper-V, then took a snapshot. Setup as how he wanted. Rearm 3 times (limit). Reloads that snapshot.

Anyways, I see by from your recent post that you **are** using Orable VM branded Virtual Box, which they do call that Oracle VM Desktop. 

I just checked through my Oracle Account, and the packages they have for their latest release (4.3) says it supports Ubuntu 13.04 and below (now at 14.10), Fedora 18 and below (now at 21), etc... but supports their current Oracle Linux 7. VirtualBox (unbranded, but still from Oracle) is at Version 4.3.20 and says it supports 14.10 and below......

I understand that just like Fedora to Red Hat, Ubuntu to Debian, etc. The newer code is a type of test bed. I'm not using branded, but I have no problems with the unbranded in my tests... And I do a lot of installs and testing (mostly on other hyper-visors, but still some on VirtualBox). 

Just a suggestion, maybe you might try the newer unbranded version = one that says they support current versions of Ubuntu? Makes sense to me.

---

### Post by vincej on 2015-01-16
Thanks for that. I don't follow the whole branded vs unbranded thing. I just go to package manager. It offers me "non-free Oracle VirtualBox" adn it juts hit install 

Something which I have discovered from the posts above: attempting to install OEM Windows discs can not work, as the VB does not present the same hardware as if it was a host.

---

