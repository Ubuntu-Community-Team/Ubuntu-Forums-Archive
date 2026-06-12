---
title: "Need Help"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by cystemic on 2010-08-17
Kind of in dire straits here. I'm a ubuntu noob and a few months ago i installed ubuntu from a usb on a second hard drive and ran both windows 7 and ubuntu on the one pc. Then windows 7 started lagging a lot and I finally got the blue screen of death. I took it to the tech guy and when he gave it back, he said he'd taken memory from the ubuntu hard drive. When I turned it on, the VAIO screen came up and then something about a no grub... I stuck in my ubuntu usb and it loaded my trial ubuntu, turned out he'd formatted the entire F drive where ubuntu was. I'm trying to re-install it on the F drive but it keeps saying no root system is defined or undefined. I would really love it if someone could help me out, heck I'd just be happy to get my windows 7 back.

---

### Post by blob dob 11 on 2010-08-17
Do you have a Windows 7 installation DVD around? If you put that in you should be able to re-install Windows. When your starting the computer up it should say in the corner something like ''boot options'' and a key beside that. Press that key (on mine it's F12) insert the installation DVD and select boot from CD/DVD drive. Follow the prompts and you should be able to re-install Windows 7. Same applies for ubuntu, just use an Ubuntu CD instead of a windows one.

---

### Post by cystemic on 2010-08-17
I only have the ubuntu usb and i finally figured out where to change the root in the partition, so it's installing now, thankyou for your help :)

---

### Post by 3Miro on 2010-08-17
If you have a Windows 7 CD the above will work, if not:

Start the system with the Ubuntu USB/LiveCD and go to Apps -> Accessories -> Terminal. Then type:
```
sudo fdisk -l
```

This will list all the hard drives and how they are partitioned and so on. This should clarify what the current situation is. Post the results if you have hard time understanding them. This error sounds like the entire partition table has been shot.

If you had some very important information on the hard drive, then you should try to run some sort of a recovery program. Look up Ubuntu and HDD recovery. If you had nothing important, you can just reinstall Ubuntu telling it to automatically use the entire hard drive. This will wipe out everything and leave only Linux on. (Also, if you plan on using both Ubuntu and windows 7, note that it is easier to install windows 7 first and then Ubuntu as opposed to the other way around).

---

