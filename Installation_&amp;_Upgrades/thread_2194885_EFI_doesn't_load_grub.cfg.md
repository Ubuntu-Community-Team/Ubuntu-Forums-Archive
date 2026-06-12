---
title: "EFI doesn't load grub.cfg"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by asharaghotham on 2013-12-21
i have installed kubuntu 13.10 on a machine which was preinstalled with windows 8. Both are installed in EFI mode on a GPT partition. After installation I get i grub prompt and nothing happens. 
I tried boot repair but that doesn't help as well. I notice the file EFI/kbuntu/grub.cfg which has these contents.


search.fs_uuid b23e10fb-2d9c-4784-a385-eca0f1f251c1 root hd0.gpt4
set prefix=($root)/boot/grub
configfile $prefix/grub.cfg

If i type these 3 lines manually, i get the grub menu and i can boot.
I know this should happen automatically, any idea how to do this?

---

### Post by oldfred on 2013-12-22
Not sure exactly what issue really is, but some have created a grub.cfg in the efi partition that is just what you typed or just a one line config file setting as a work around. The efi version of grub then finds grub.cfg in ubuntu folder in efi partition and loads the grub.cfg in the install.

A couple of users posted grub.cfg similar to this.
      >  configfile (hd0,gpt4)/boot/grub/grub.cfg


   found that putting grub.cfg into /EFI/ubuntu works, even when grubx64.efi is in /EFI/Boot

    

---

### Post by shaan7 on 2013-12-23
I think I know what is wrong, Kubuntu 13.10 had a bug which leads to what you are seeing here ([https://bugs.launchpad.net/ubuntu/+source/kubuntu-settings/+bug/1242417](https://bugs.launchpad.net/ubuntu/+source/kubuntu-settings/+bug/1242417)). This is listed under "Known Problems" on [http://www.kubuntu.org/news/kubuntu-13.10](http://www.kubuntu.org/news/kubuntu-13.10)

To fix this you have two options-

**Option1: I prefer you use this option if you have an internet connection**-
Steps-
1. Boot into kubuntu using the method you said. Then, connect to the internet using the network manager icon on the bottom-right of the screen.
2. Press the "K" menu on the bottom-left corner, and type "**muon**", you will get an option "**Muon Package Manager**", open that.
3. Click on "**Check for Updates**" [http://i.imgur.com/5Tdkkwf.png](http://i.imgur.com/5Tdkkwf.png) . It will connect to update servers and download around ~20MB of information, wait.
4. Once it is done, click "**Full Upgrade**" and then "**Apply Changes**" [http://i.imgur.com/wtCyUYW.png](http://i.imgur.com/wtCyUYW.png) . It will start downloading and installing updates. This may take some time depending on your Internet connection.
5. Once the upgrade is done, restart the computer. This time you should get the boot menu.


**Option2: (Use this if Option1 didn't work or you don't have an Internet connection)-**
1. Boot to kubuntu, press the "K" menu on the bottom-left corner, and goto "**Computer**", you will something like this [http://i.imgur.com/4M8WSVi.png](http://i.imgur.com/4M8WSVi.png)
2.  Click on the "**Root**" option. You will get a File Manager (called  Dolphin) window which will look like this (but different because this is  my computer) [http://i.imgur.com/lqCnoFh.png](http://i.imgur.com/lqCnoFh.png)
3. On the devices section on the left, you will see all the drives that you have. Click on each of them and find out the one which has a folder called **EFI**, go inside this folder.
4. In the **EFI** folder, you have a folder called **kubuntu**, make a copy of that folder and call it **ubuntu**
5. Now reboot, you should be able to get the grub menu.

Hope that helps :)

---

### Post by asharaghotham on 2013-12-23
yes it works! 
Thank you .

---

