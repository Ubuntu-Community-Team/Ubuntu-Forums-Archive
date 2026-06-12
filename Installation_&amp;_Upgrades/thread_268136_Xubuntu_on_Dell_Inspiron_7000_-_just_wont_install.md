---
title: "Xubuntu on Dell Inspiron 7000 - just wont install"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by jarthurs on 2006-09-29
I've just wasted an afternoon trying to install Xubuntu onto a Dell Inspiron 7000 laptop (PII 366MHz 128Mb). I initially ran the Desktop CD which seemed to work OK but the install failed. So I decided to try with the Alternate CD. But its got progressively more frustrating over the course of the afternoon.

At first it would get through all the install steps and during the kernel install it would freeze at 73% (install xubuntu splash). Tried again and got past this point but then it announced it couldn't install Grub, tried Lilo and this refused to install as well. Having blanked the system with a GParted CD just to clear out any rogue stuff that might be upsetting the install. Now I cannot get past the point after setting the system time and the user details because it now reports each time that there is no CD-ROM or valid mirror configured.

Trouble is all I keep reading about is people who've installed Xubuntu on their old Inspiron 7000 and it works just fine. I'm writing this message from a DamnSmallLinux install and it works fine, I'd just rather be using xubuntu.

 ](*,)

---

### Post by ash211 on 2006-09-29
Have you tried checking the media?  Make sure that the MD5 sum or your ISO file is correct.  See [https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto) for help.

---

### Post by jarthurs on 2006-10-02
Just checked the MD5 sum and it's reporting the CD is fine. However I noticed on console 4 there was a long list of read errors so it looks like the CD-ROM drive on the old laptop is screwed. 

I set a mirror and got it all the way to the end of the install, it managed to download all the packages rather than fail to read the CD. However once I get to the end I get...

Unable to install GRUB in (hd0)
Executing 'grub-install (hd0)' failed

This is a fatal error.

Looks like it's fallen at the final fence. Anyone suggest a way of getting GRUB to comply?

Regards,
Jason.

---

### Post by jarthurs on 2006-10-02
Having just failed to install again, I decided to try fdisk to see if the drive was OK. It fdisk'ed OK and having deleted the partitions and run the install again (without the CD) from the mirror it installed perfectly.

Now replying from Xubuntu on my old Inspiron 7000 PII 366MHz.

Regards,
Jason.

---

### Post by primogif on 2008-01-13
Pardon my ignorance.  I read your post of using "mirror" to install Ubuntu on your Dell Inspiron 7000.  I have the same laptop computer.  When I tried to isntall Ubuntu after downloading it and burning it to a CD, I ran into difficulties.  The first screen had an icon for "INSTALL", which I clicked.  Then my CD drive kept running for a second or two, then stopping.  6 hours later it came up with the screen to choose a language.  Two banners also opened up.

But I couldn't do anything, because the mouse was frozen!

So I was interested in installing from a mirror, but need to know how to do that.  I don't know if my CD drive is having issues.

Thank you.



> **jarthurs said:**
> Having just failed to install again, I decided to try fdisk to see if the drive was OK. It fdisk'ed OK and having deleted the partitions and run the install again (without the CD) from the mirror it installed perfectly.

Now replying from Xubuntu on my old Inspiron 7000 PII 366MHz.

Regards,
Jason.

---

