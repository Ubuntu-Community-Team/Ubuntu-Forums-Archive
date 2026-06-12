---
title: "win7 and ubuntu"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by alton2536 on 2010-03-30
Hi
What is the easist way to duel boot 2 hard drives . I want one with Windows 7 and my original Ubuntu on drive 2. Do i have to install Win 7 first on drive 1 and then install Ubuntu ? Will grub 2 find the win7 drive ?

---

### Post by derekeverett on 2010-03-30
> **alton2536 said:**
> Hi
What is the easist way to duel boot 2 hard drives . I want one with Windows 7 and my original Ubuntu on drive 2. Do i have to install Win 7 first on drive 1 and then install Ubuntu ? Will grub 2 find the win7 drive ?

I realize this reply does not address your question, so I apologize for that in advance...

But are you sure you wouldn't rather dual boot off of one hard drive and use the other as a back-up?

Dual booting can be risky business, in particular if your not real sure of what your doing. Protecting my data would be a priority for myself.

I just wanted to suggest it.

---

### Post by pbpersson on 2010-03-30
Yes, install Windows 7 first - reserve a partition or an entire drive for Ubuntu - then install Ubuntu and tell it what partition or drive you want it to use and make sure it does not touch the Windows drive.

It works great, I have done it here.

---

### Post by bigsmitty64 on 2010-03-30
> **pbpersson said:**
> yes, install windows 7 first - reserve a partition or an entire drive for ubuntu - then install ubuntu and tell it what partition or drive you want it to use and make sure it does not touch the windows drive.

It works great, i have done it here.

+1  :)

Also I believe after all is said and done, you should go into your bios and set the Ubuntu drive to boot first, because thats where grub is installed .

---

### Post by alton2536 on 2010-03-30
Thanks for the help. i have had xp and ubuntu running on 2 internal drives now for 2 years and all has worked well untill i had to use live cd and grub 2 messed everything up!! decided to start a fresh (have full backups , hopfully!)

---

### Post by Mark Phelps on 2010-03-30
I've been doing this for years ... and strongly support the recommendation to have the different OSs organized with each on its own physical drive.

This prevents messing with MS Windows MBRs, prevents having to restore MBRs later, and since GRUB2 can easily find other OSs, it makes it a simple matter to boot from your Ubuntu drive, run "sudo update-grub" and upon reboot, have a GRUB2 menu that include the MS Windows OS option.

---

