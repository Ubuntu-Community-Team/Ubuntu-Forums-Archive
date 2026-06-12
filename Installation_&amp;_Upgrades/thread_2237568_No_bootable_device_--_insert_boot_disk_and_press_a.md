---
title: "No bootable device -- insert boot disk and press any key"
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by teobald on 2014-08-02
I installed Ubuntu 14.04 from a live USB on my brand new laptop ACER travelmate P253. There was no OS, only Linpus program that was overwritten by Ubuntu.
It went well but I got the error message:

No bootable device -- insert boot disk and press any key

I checked out the boot order in BIOS, nothing wrong there. So I went for a boot-repair that issued the log [http://paste.ubuntu.com/7928062](http://paste.ubuntu.com/7928062) but it still can't boot. I can use the laptop only in trial mode on the live USB. Finally I re-installed Ubuntu and runned the boot-repair again, same outcome.

Any help would be much appreciated.
Teobald

---

### Post by oldfred on 2014-08-02
It looks like you have signed kernels installed, so it should boot with secure boot on.
But have you tried with secure boot off?

       Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)
      
 Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
      
 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

      
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

     
    
Is Acer now once of those vendors that has modified UEFI to only boot the entry in UEFI that says Windows? There are mulitple work arounds, some better than others depending on system.

---

### Post by aidan5 on 2014-08-02
Hey, I'm having a similar problem, so if I manage to get it working I'll let you know!

---

### Post by teobald on 2014-08-02
the BIOS doesn't allow me to disable the secure boot mode, it's greyed and I see no option how to make it blue

---

### Post by oldfred on 2014-08-02
Microsoft's contract requires Vendors to allow users to turn secure boot off, unless you have a tablet type system which then may only be a Windows system like an iPad is only a Apple system.

Some systems require you to set a UEFI/BIOS password. But if you do that do not ever lose that password as you will not be able to make any changes to UEFI and system may become a brick/doorstop.

---

### Post by teobald on 2014-08-03
This laptop was sold without Miscrsoft or any OS, there was only Linpus which I overwrote with Ubuntu

---

### Post by teobald on 2014-08-03
Problem solved! I changed form Legacy BIOS to UEFI in the BIOS settings (got message "HDD has been blocked by the current security policy", fair enough).
Then installed Ubuntu again (over the previous Ubuntu in my case). Now it boots and works great!

---

