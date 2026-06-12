---
title: "rescue grub2(&amp;can't be known by WIN7)"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by Charlie FCW on 2011-05-21
i just have my mobile HD splited to 2 vols.one NTFS and one EXT3.however it can't be known by WIN7 (the whole disk) and i tried to reboot twice but it didn't work.then i installed ubuntu10.10(formatted it to EXT4) but it can't run with the information 'rescue grub2'.my files are still 'alive' but as they are quite important i wish anyone could help me.

---

### Post by Charlie FCW on 2011-05-21
no one help?

---

### Post by enkrypt3d on 2011-05-21
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Here's some useful reading...

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

And this will get your windows install back ^

Did you format the entire drive as ext4? If so your windows install is gone... Hopefully you had 2 separate partitions setup so you could try fixing the windows install MBR and then boot into a live CD and run update-grub.

---

### Post by Hedgehog1 on 2011-05-22
If those links don't lead you to a solution, please do the following so we can figure out the status of your PC:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by enkrypt3d on 2011-05-22
> **Hedgehog1 said:**
> If those links don't lead you to a solution, please do the following so we can figure out the status of your PC:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

I Tried this method but while using the live cd the system is so slow (and the internet) that it took me several attempts to get the results file... then i tried copying the results.txt to a usb thumb drive and it wasn't there when I tried booting back into windows....... ugh

---

### Post by Hedgehog1 on 2011-05-22
> **enkrypt3d said:**
> I Tried this method but while using the live cd the system is so slow (and the internet) that it took me several attempts to get the results file... then i tried copying the results.txt to a usb thumb drive and it wasn't there when I tried booting back into windows....... ugh

enkrypt3d,

I thought we were trying to fix **Charlie FCW**'s PC? I don't follow the purpose of your last post in that effort.  Am I missing something?

***The 'Confused' Hedge***

---

### Post by enkrypt3d on 2011-05-22
> **Hedgehog1 said:**
> enkrypt3d,

I thought we were trying to fix **Charlie FCW**'s PC? I don't follow the purpose of your last post in that effort.  Am I missing something?

***The 'Confused' Hedge***

haha sorry for the off topic post - i was referring to my other post about dual booting on an ssd... :)

---

