---
title: "Ubuntu Install on External messed with my internal"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Shadi Ramadan on 2010-05-08
Hello!

I installed the latest Ubuntu on my 1TB external hardrive, and when I removed the external and restarted to load windows 7...  An error appeared saying Grub Error.. and I could not load windows!!!
I temporarily fixed the problem by installing Ubuntu on a tiny partition on my laptop's internal hardrive so that it would fix and reinstall grub.

Why did installing ubuntu ever mess up how my internal booted?
Why does it not ask to install grub?
How can I completely remove ubuntu from my internal and make it so that my laptop automatically loads Windows 7 first as it did when I bought it?

Thank you!

Shadi

---

### Post by raymondh on 2010-05-08
> **Shadi Ramadan said:**
> Hello!

I installed the latest Ubuntu on my 1TB external hardrive, and when I removed the external and restarted to load windows 7...  An error appeared saying Grub Error.. and I could not load windows!!!
I temporarily fixed the problem by installing Ubuntu on a tiny partition on my laptop's internal hardrive so that it would fix and reinstall grub.

Why did installing ubuntu ever mess up how my internal booted?
Why does it not ask to install grub?
How can I completely remove ubuntu from my internal and make it so that my laptop automatically loads Windows 7 first as it did when I bought it?

Thank you!

Shadi

Hello Shadi,

By default, grub will install on the HD that is set to boot first in your bios unless you tell the ubuntu installer (usually in step 7 of the install process) to install grub elsewhere. Not knowing your install process, I assume that you installed grub in the mbr of your internal HD. When that happens, and since you unplugged the external, a grub error occurs. 

Do you have a windows install disc? Not a recovery disc? If you google, look for steps on how to fix the MBR using a windows install disc/command prompt. I know neosmart has a Downloadable file that will allow a user to fix the mbar in vista.   LILO will also do it. You will have to burn the image to a cd.  

Once you have your system back to original configuration, you may now re-install grub2. This time, install it in the mbr of the external HD. Again, googling "reinstall grub 2" can provide guidance. 

With this setup, grub in the external, you will only be able to access ubuntu if the external is plugged in. And it has to be a quick bios change in bootup to make sure the external boots first before the internal. 

Am sorry if I sound vague. I am mobile right now and cannot provide links. 

Best,

Raymond

---

### Post by raymondh on 2010-05-08
Update..... I see in launchpad that ubiquity in lucid has a bug that installs grub in all the HD's. If that were the case, a workaround I can think of is to make sure (in step 7, I believe) that grub is installed in the intended HD. in that step, you click on 'advanced'. 

At least that's how I remember it in previous ubuntu versions :)

---

