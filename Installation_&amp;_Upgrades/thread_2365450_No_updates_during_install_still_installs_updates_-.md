---
title: "No updates during install still installs updates - fails if offline"
date: 2017-07-06
forum: Installation &amp; Upgrades
---

### Post by frackers2 on 2017-07-06
When installing lubuntu 16.04.01 iso, one of the questions if an internet connection is available is whether to "Download updates while installing...". This is greyed out if no internet connection.
Leaving this unchecked, I still see the following downloads occurring.

 > 
GET /ubuntu/pool/main/l/language-pack-en/language-pack-en_16.04%2b20161009_all.deb 
GET /ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_16.04%2b20161009_all.deb 
GET /ubuntu/pool/main/f/firefox/firefox-locale-en_54.0%2bbuild3-0ubuntu0.16.04.1_amd64.deb 
GET /ubuntu/pool/main/h/hunspell-en-us/hunspell-en-us_20070829-6ubuntu3_all.deb 
GET /ubuntu/pool/main/s/scowl/wbritish_7.1-1_all.deb 
GET /ubuntu/pool/main/l/linux/linux-image-4.4.0-83-generic_4.4.0-83.106_amd64.deb 
GET /ubuntu/pool/main/l/linux/linux-image-extra-4.4.0-83-generic_4.4.0-83.106_amd64.deb 
GET /ubuntu/pool/main/l/linux-meta/linux-generic_4.4.0.83.89_amd64.deb 
GET /ubuntu/pool/main/l/linux-meta/linux-image-generic_4.4.0.83.89_amd64.deb 
GET /ubuntu/pool/main/l/linux-signed/linux-signed-image-4.4.0-83-generic_4.4.0-83.106_amd64.deb 
GET /ubuntu/pool/main/l/linux-meta/linux-signed-generic_4.4.0.83.89_amd64.deb 
GET /ubuntu/pool/main/l/linux-meta/linux-signed-image-generic_4.4.0.83.89_amd64.deb 
GET /ubuntu/pool/main/l/linux/linux-headers-4.4.0-83_4.4.0-83.106_all.deb 
GET /ubuntu/pool/main/l/linux/linux-headers-4.4.0-83-generic_4.4.0-83.106_amd64.deb 
GET /ubuntu/pool/main/l/linux-meta/linux-headers-generic_4.4.0.83.89_amd64.deb 
GET /ubuntu/pool/main/g/grub2/grub2-common_2.02%7ebeta2-36ubuntu3.11_amd64.deb 
GET /ubuntu/pool/main/g/grub2/grub-common_2.02%7ebeta2-36ubuntu3.11_amd64.deb 
GET /ubuntu/pool/main/g/grub2/grub-efi-amd64-bin_2.02%7ebeta2-36ubuntu3.11_amd64.deb 
GET /ubuntu/pool/main/g/grub2/grub-efi-amd64_2.02%7ebeta2-36ubuntu3.11_amd64.deb 
GET /ubuntu/pool/main/g/grub2-signed/grub-efi-amd64-signed_1.66.11%2b2.02%7ebeta2-36ubuntu3.11_amd64.deb 
GET /ubuntu/pool/main/s/shim/shim_0.9%2b1474479173.6c180c6-1ubuntu1_amd64.deb 
GET /ubuntu/pool/main/s/shim-signed/shim-signed_1.28%7e16.04.1%2b0.9%2b1474479173.6c180c6-1ubuntu1_amd64.deb 


In addition, there are lots of searches 'by-hash' of the repositories. 

All fine and dandy except if an attempt is made to install without an internet connection the inability to download all the grub and shim packages causes the install to fail with the well known "The 'grub-efi-amd64-signed' package failed to install into /target/.

Checking the squashfs system in casper I see that only the i386 version of grub is installed in the amd64 iso image. Is this the reason for the failure or it is something else?

---

### Post by mörgæs on 2017-07-09
People should always install using a wired internet connection. There are no advantages in doing otherwise.

---

### Post by frackers2 on 2017-07-09
I have a colleague in China trying to install but the great firewall really screws things up. Also I have another colleague who has a PC on a private network which is designed specifically to NOT have internet access (security is important to some of us).
What really hacks me off isn't that the install downloads something, it's that if the squashfs filesystem is updated to the latest version(s) it still goes out and downloads it. This indicates to me that something is broken. I'm willing to fix it if only I can find the broken piece!

---

### Post by mörgæs on 2017-07-10
> **frackers2 said:**
>  I'm willing to fix it if only I can find the broken piece



Do you mean sending a proposed bug fix to the developers? If that's the case then first step is to see if the development version (17.10) works the same way.

---

### Post by frackers2 on 2017-07-10
> **mörgæs said:**
> Do you mean sending a proposed bug fix to the developers? 
If I can isolate where the problem is. Finding documentation on Ubiquity and Casper is like trying to find rocking horse manure.

---

### Post by johndough2 on 2017-07-11
Hi

Could the problem, in part, be that the iso is too small or wrong.  EG: If I get a distro to install and want proper Queens English and a UK keyboard and it is not contained within the iso then a network download is the only option.  

So maybe a second iso is needed, much like the old Red Hat was a 2 CD set, unless you weren't in the US and had a 3 CD set, the third being an international language one i believe.

Download and create a new iso image, mugging off Libreoffice to give the necessary space, and putting Libreoffice on a second disk along with stuff like adobe etc.

Using an 8 gig usb stick?

---

### Post by ubfan1 on 2017-07-11
The "downloads" appear to be off the install media, not a network download.  The problem may be that the install media was created on a non-UEFI system, and gets created without the UEFI version of grub (That is probably a bug), so gets into trouble with a UEFI install.  I saw something about mkusb along those lines, but I need to do some testing myself.   I do still tend to do installs without the networking because of history -- many times a proprietary driver was needed for the wireless, so it couldn't work anyway, and that hung things up.  Solution, recreate your install media on a UEFI system, and optionally, join the bug (there must be one ).

---

### Post by frackers2 on 2017-07-12
If the ISO is too small or wrong then its a problem with the standard lubuntu 16.04.01 image as that is what I've used as a reference. I'm booting off an 8G USB stick.
Since the image only contains i386 uefi-grub (this is in the amd64 image) I assume its a problem in the original imaging but I've tried splitting out the squashfs, chroot'ing into it to update the grub packages and putting it back together and it behaves the same.

---

### Post by johndough2 on 2017-07-13
Hi

Well to avoid to much egg on face...

OK, 

I assumed that this was a problem with installing remotely and the package selection was wrong.  In that you wanted en-gb and the install had en-us.

This next bit wont solve your problem, but you could install something else.  You could try something different to achieve the required end result.

Build it yourself, SuSE Studio   or ubuntu UCK 2.x

Then it will contain the right packages.

---

### Post by vasa1 on 2017-07-13
@johndough2, please use quote tags and appropriate attribution if you're quoting anything. Thank you.

---

### Post by frackers2 on 2017-07-13
> **johndough2 said:**
> Hi

This next bit wont solve your problem, but you could install something else.  You could try something different to achieve the required end result.

Build it yourself, SuSE Studio   or ubuntu UCK 2.x

Then it will contain the right packages.

UCK 2 is abandonware, the front page of SuSE Studio doesn't even say what it is!! (I had to go to Wikipedia to find out) but you're right in one respect. If I want something that will install offline then I need to leave Ubuntu and find something that has been properly tested. Shame as when it is installed it does everything I want but no good to me if I post a USB stick to someone and they can't use it.

The choice of packages isn't the issue - its the fact that it MUST have an internet connection to complete the install process and even when no updates are requested, packages are still downloaded. In other words, its broken...

---

