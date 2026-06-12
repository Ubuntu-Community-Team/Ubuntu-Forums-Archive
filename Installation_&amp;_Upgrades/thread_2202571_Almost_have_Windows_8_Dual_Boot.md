---
title: "Almost have Windows 8 Dual Boot"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by jauyong on 2014-01-29
Hi,

I almost have dual boot going with Windows 8. I have them both installed, but on start up if I don't hit F12 I get this screen:
[http://i.imgur.com/0L87bAb.jpg](http://i.imgur.com/0L87bAb.jpg)

If I do hit F12 right away I get this screen. I am able to boot windows from this option. Or see the third screen shot for when I select the first ubuntu option.
[http://i.imgur.com/ifphSKE.jpg](http://i.imgur.com/ifphSKE.jpg)

If I select the first ubuntu from the above SS I get this and am able to load both windows and ubuntu:
[http://i.imgur.com/sVFsqGZ.jpg](http://i.imgur.com/sVFsqGZ.jpg)

I want to know if this is as good as it gets? Any suggestions? Should I do a boot repair via these steps:

[COLOR=#333333][FONT=UbuntuRegular]**REPAIRING THE BOOT**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]After finishing the installation, if you happen to have Windows 8 disabled from booting and it only boots to Ubuntu, do not worry. In Ubuntu after it boots, open a Terminal and type the following:[/FONT][/COLOR]
sudo add-apt-repository ppa:yannubuntu/boot-repair  
sudo apt-get update
sudo apt-get install boot-repair
[COLOR=#333333][FONT=UbuntuRegular]Now run boot-repair[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Boot Repair will mention that we have some GRUB error, that we have an EFI system and that Ubuntu rocks. Since Ubuntu rocks (It does not work if Ubuntu does not rock! ^^), just click on **Apply** so boot repair fixes everything. Now reboot and you should see Windows 8 and Ubuntu side by side.




[SIZE=3]Thanks for you help people!

- Jason[/SIZE][/FONT][/COLOR]

---

### Post by fantab on 2014-01-30
Your system has UEFI boot and if I am not mistaken both Windows and Ubuntu appear to be installed in UEFI.
BUT your second screen-shot of 'Boot Manager' says that you've 'Boot Mode' set to "legacy". That seems to be the problem.

**Change the 'Boot Mode' to UEFI/EFI.**

If that doesn't help then start by posting the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by jauyong on 2014-01-31
you were right! thanks for the help!

---

