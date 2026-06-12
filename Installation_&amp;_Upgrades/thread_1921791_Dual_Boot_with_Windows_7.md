---
title: "Dual Boot/ with Windows 7"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by brooklynzoo81 on 2012-02-07
Hello all.  I am trying to get back into Linux and setup Ubuntu x64 on my main PC.  But my main PC already has Windows 7 x64 in a Raid 0 array.  However i do have a 1TB spare drive in the machine.  I wanted to know if it would be possible to install Ubuntu on the 1TB drive without removing the raid setup with windows 7?  If i am able to do this what would i need to do in grub to get this going? 


Thanks.

---

### Post by darkod on 2012-02-07
There should be no problems installing it on the 1TB disk. But to have more control where the bootloader goes I would use the manual partitioning option (Something Else from the menu).

Set the partitions as you want and set the bootloader to install on the same 1TB disk.

Then just go into BIOS and set it to boot from it.

I haven't tried this setup but I think it should be able to detect your win7 and make an entry in the grub boot menu for it.

---

### Post by brooklynzoo81 on 2012-02-07
Thanks darkod for the reply back.  I will give this a shot tonight if i can.

---

### Post by brooklynzoo81 on 2012-02-09
Finally had a chance to do this tonight.  It does work but not a big fan of having to select which drive to chose during boot up.  Ubuntu didn't recognize my raid setup.

---

### Post by LinuXofArabiA on 2012-02-09
Could you please give more details as to the options you chose in your partitions - 'Type of partition, logical or primary', 'Mount type, where did you mount the partition'. I need this info to help with my installation.

Thanks

---

### Post by darkod on 2012-02-10
> **brooklynzoo81 said:**
> Finally had a chance to do this tonight.  It does work but not a big fan of having to select which drive to chose during boot up.  Ubuntu didn't recognize my raid setup.

When you install ubuntu on fakeraid, it's recommended to use the alternate install cd, not the standard desktop cd. It has better raid and lvm support.

Even though you are not installing on raid, if you want it to "see" the win7 raid I wonder if it's better to use the alternate cd. During the beginning of the installation that cd detects a fakeraid and asks you if you want to activate it. Maybe it's this process of activation that is missing so it doesn't detect it right now.

---

### Post by brooklynzoo81 on 2012-02-10
Actually I did fail to mention that I used both the regular cd and the alternate cd.  It did ask me if I wanted to activate the raid and I say yes but it only saw one drive instead of two, while using the alternate cd.  

@Linux of Arabia.  I really didn't chose any custom lay out I just let it do it for me automatically. It picked my raid as sdaa 150GB only saw one drive. And sdac for my 1.5TB which I have Ubuntu installed on it now.

---

### Post by Mark Phelps on 2012-02-10
> **brooklynzoo81 said:**
> Finally had a chance to do this tonight.  It does work but not a big fan of having to select which drive to chose during boot up.  Ubuntu didn't recognize my raid setup.

An alternative, if you end up being unsuccessful in enabling OS selection using GRUB, is to do that using EasyBCD.  You can get that from the NeoSmart Technology forums.

Download and install it in Win7.

You will have to experiment with adding a boot entry, as there are a lot of options and I don't personally know which ones (if any) will work with raid.

---

### Post by ronparent on 2012-02-10
A program called **dmraid** is essential to access the raid drives. I have found that, typically, Ubuntu does not install dmraid when Ubuntu itself is not installed on the a raid drive. Thus after the install you won't see the Windows partitions on the raid.

Solution is to simply install it (ie **apt-get install dmraid**). This step will make all raid drives on your computer completely accessible to your Ubuntu install. 

Also, contrary to prevailing beliefs, the latest releases of Ubuntu install fine with the regular cd and the alternate cd shouldn't be needed for a simple install.

---

### Post by darkod on 2012-02-10
> **ronparent said:**
> 
Also, contrary to prevailing beliefs, the latest releases of Ubuntu install fine with the regular cd and the alternate cd shouldn't be needed for a simple install.

The install as install is fine, but grub2 install to the MBR seems to fail sometimes (not always). At least according to threads here on the forum including using the latest versions. I might be wrong though.

---

### Post by brooklynzoo81 on 2012-02-10
Thank you all for in the information.  I will be trying this in the next few days.

---

### Post by ronparent on 2012-02-10
darkrod - your original post was absolutely correct. The key issue is shown at this point: > Finally had a chance to do this tonight. It does work but not a big fan of having to select which drive to chose during boot up. **Ubuntu didn't recognize my raid setup**. This occurs because dmraid was not installed with Ubuntu (this should not be allowed to occur when a raid is present on the system). 

Assuming at this point that Ubuntu boots normally with no evidence of Windows or any raid partitions the problem is simply that dmraid is not installed to the system. Installing dmraid remedies this problem and reinstalling grub will get Widows onto the grub menu. A grub reinstall is poinless, however, until the dmraid is operational.

---

### Post by brooklynzoo81 on 2012-02-10
Here are my results below.  I already have dmraid installed but this happened.

# dmraid --a yes
ERROR: isw: wrong number of devices in RAID set "isw_cejgjebaaj_RAID0" [1/2] on /dev/sdb
RAID set "isw_cejgjebaaj_RAID0" was not activated

---

### Post by ronparent on 2012-02-11
This doesn't sound good. It appears the raid set is 'broken'. If so all of your data and the win install on the raid is lost - that is one of the unfortunate aspects of a raid 0. It most likely would have occurred because something was written to sda alone - possible if sda had been treated as 'unallocated space'. This is what it appears to be if you look at it in linux without dmraid activated. As a matter of fact both sda and sdb which are parts of the raid set will appear as 'unallocated space' in gparted separately from the formatted raid drive. You have to recognize this and avoid any partitioning actions on those drives or the raid will be corrupted.

I would disconnect the non-raided drive to check. If the raid0 has been corrupted you will have no choice but to recover or reinstall Windows, and recover all data from backup. I hope the situation is better than what appears.

---

### Post by brooklynzoo81 on 2012-02-14
My Windows 7 raid 0 works fine.  However if i do want to go into Ubuntu i still have to select the other drive on boot up.

---

### Post by ronparent on 2012-02-14
If I follow you right, you boot normally to windows if the raid is selected as the boot disk. To boot to Ubuntu you have to separately select the other drive in bios to boot it. However you don't have windows in that boot menu.

This is probably your best situation! You merely have to reinstall grub to the boot loader of the new disk so that windows is picked up in the menu. Now that you have dmraid installed the raid drive should be automatically recognized.

To reinstall grub,  follow these instruction - [https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands](https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands)

The section on reinstalling grub should do it. Post if you have further problem.

---

