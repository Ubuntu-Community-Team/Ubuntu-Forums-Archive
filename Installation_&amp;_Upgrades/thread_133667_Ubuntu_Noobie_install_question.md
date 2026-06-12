---
title: "Ubuntu Noobie install question"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by riversr on 2006-02-20
I have a problem getting Ubuntu installed. I have some experience with Linux based systems but not very much.

I am trying to install from a V5.10 install CD. For some reason the system that I have will not boot from the CD. I have verified that my burned CD is good(booted it on a diff system), and I know that the CD drive is OK because it works just fine when I run Windows on this server. I am assuming that there is some problem in my BIOS or something that prevents it from booting. I am looking for an alternative way to install Unbuntu. From working on previous Linux installs I know there was a way to create a bootable floppy. Is it possible for me to create such a floppy, boot from it and then install from the Ubuntu CD?

Thanks for any help!

---

### Post by Coelocanth on 2006-02-20
Have you checked your BIOS? Is there an option to boot from CD? If so, ensure it's enabled as the first boot device.

---

### Post by riversr on 2006-02-20
Sorry, I forgot to mention that. Yes I have set the CD to boot first, before floppy and hard disk, but it just ignores that setting and boots the hard disk anyway as if the CD wasn't there. Booting from the floppy works fine.

---

### Post by kane82 on 2006-02-20
im a total noob to linux but i have done exactly the same thing and my machine wont boot the image from cd - bios is all fine - not sure what ive done wrong

---

### Post by riversr on 2006-02-20
Resolved my problem by using a software boot for the CD. Downloaded it here:
[http://www.bcdwb.de/bcdw/bcdl150z.zip](http://www.bcdwb.de/bcdw/bcdl150z.zip)

Used WinImage to burn it to floppy and then boot floppy which in turn boots the CD. Works great!

---

### Post by kane82 on 2006-02-20
I found the problem i had you need to "using Nero" create image of the iso file then burn that.. it will then boot from cd

---

### Post by Resurrection on 2006-02-20
Right about Nero, most people forget to use Nero Burning Rom or in my case I have Nero (7 I think?) with SmartStart and all that, and you have to dig around on SmartStart where it says "Copy and Backup" and click on Burn Image to Disc.   Some folks try to burn as a Data CD, and that won't work.

My first burned disc didn't work, but that was because I was an idiot and burned it too fast, even though I knew better than to do so.  Guess I was in a hurry.

---

