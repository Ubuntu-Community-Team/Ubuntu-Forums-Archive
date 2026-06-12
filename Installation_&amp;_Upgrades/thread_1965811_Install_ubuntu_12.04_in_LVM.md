---
title: "Install ubuntu 12.04 in LVM"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by magiza83 on 2012-04-26
Hello,

I've an installation of ubuntu 11.10 server with LVM + ubuntu desktop, now I want to install ubuntu desktop 12.04 but I want to use the partitions and LVM I have, because I want to save all my data that is in the lv home.

How can i do it? time ago I was looking information to do it in 11.10 but I was not able to find it, finally I decided to install ubuntu server and after it I installed ubuntu desktop packages. But this is a hard work and I was hopint to find a way to do it directly in ubuntu desktop.

Thanks & Regards.

---

### Post by darkod on 2012-04-26
If you wanted the Desktop OS with LVM you went the wrong way. You need to use the Alternate Install cd for that and you can install with LVM. There is no need to install the Server OS just for the LVM.

So, now you want to install the 12.04 over the 11.10 and keep the existing home LV right?

Try the alternate cd, it should offer you the option to install onto the same root partition and use the same /home without formatting it.
First make sure the alternate installer will see the existing LVM. Don't try to create a new LVM if it doesn't see the current one because that might destroy your data, I am not sure.

---

### Post by magiza83 on 2012-04-26
Thanks for the fast reply!

So, If i don't get it wrong, I have to install the alternate cd and with it I will have desktop environment, right? 

Sorry about my doubts but I'm not expert in linux desktop environment.

Regards.

---

### Post by darkod on 2012-04-26
Yes. The ISO files with names like ubuntu-XXX-desktop-XXX.iso and ubuntu-XXX-alternate-XXX.iso both install the same desktop OS.
The difference is that the -desktop- can run the cd in live mode and has a GUI installer (graphical), while the -alternate- can't run in live mode and has text based installer. But the alternate has support for raid and lvm during install.

As always with linux, you do have other options for example. The liveCD can also read LVM but if you add the package first and activate the LVM. This is a procedure to do it:
[http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/](http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/)

If you do that first and then click on Install Ubuntu you should be able to do it with the standard liveCD too. Keep that link, it's also useful if you ever need to get data out of your LVM using only a live mode.

And here are all images of 12.04:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

You can see you have the -alternate- -desktop- and -server- images for both 32bit and 64bit.

---

### Post by magiza83 on 2012-04-26
Thank you very much!!! this has solve a lot of doubts I had about it.

I will keep this link in case of disaster :)

Regards!

---

### Post by circle on 2012-05-02
I just tried installing ubuntu 12.04 LTS in lvm with the standard livecd (desktop) but failed too.

here is what i did:
[LIST=1]
[*]Boot the host with live CD
[*]Install lvm2 package (apt-get install lvm2)
[*]create 2 partitions (sda1 for /boot, sda3 for lvm)
[*]create the the pv, vg, lv accordingly
[*]run the installer on desktop
[*]set the partition layout manually (sda1 => /boot, /dev/mapper/vg000-lv00_root1 => /, ..)
[*]proceed to the remaining steps of the installer
[*]before rebooting, i manually mount the lv accordingly, chroot inside and install lvm2 package
[*]reboot the computer
[/LIST]

but the computer doesn't boot :(

i noticed that the installer doesn't directly install on the created lv (e.g. [FONT="Courier New"]/dev/mapper/vg000-lv00_root[/FONT]). instead, it created a new partition inside the lv (e.g. [FONT="Courier New"]/dev/mapper/vg000-lv00_root1[/FONT]) and install on the new partition). after rebooting, it the partition was not automatically detected for some unknown reason. There are only [FONT="Courier New"]vg000-lv00_root[/FONT] but not [FONT="Courier New"]vg000-lv00_root1[/FONT] inside [FONT="Courier New"]/dev/mapper/[/FONT]. Failing to auto detect the partition inside the lv may be why the system cannot boot.

Interestingly using fdisk can actually confirm that the [FONT="Courier New"]vg001-lv00_root1[/FONT] partition exists in the volume [FONT="Courier New"]vg001_lv00_root[/FONT], the other lv are similar.

Is it a bug or did I mix up something? Any help?

Thanks!

---

### Post by circle on 2012-05-02
I just tried installing ubuntu on lvm with the standard livecd (desktop) but failed too.

here is what i did:
[LIST=1]
[*]Boot the host with live CD
[*]Install lvm2 package (apt-get install lvm2)
[*]create 2 partitions (sda1 for /boot, sda3 for lvm)
[*]create the the pv, vg, lv accordingly
[*]run the installer on desktop
[*]set the partition layout manually (sda1 => /boot, /dev/mapper/vg000-lv00_root1 => /, ..)
[*]proceed to the remaining steps of the installer
[*]before rebooting, i manually mount the lv accordingly, chroot inside and install lvm2 package
[*]reboot the computer
[/LIST]

but the computer doesn't boot :(

i noticed that the installer doesn't directly install on the created lv (e.g. [FONT="Courier New"]/dev/mapper/vg000-lv00_root[/FONT]). instead, it created a new partition inside the lv (e.g. [FONT="Courier New"]/dev/mapper/vg000-lv00_root1[/FONT]) and install on the new partition. after rebooting, it the partition was not automatically detected for some unknown reason. There are only [FONT="Courier New"]vg000-lv00_root[/FONT] but not [FONT="Courier New"]vg000-lv00_root1[/FONT] inside [FONT="Courier New"]/dev/mapper/[/FONT]. Failing to auto detect the partition inside the lv may be why the system cannot boot.

Interestingly using fdisk can actually confirm that the [FONT="Courier New"]vg001-lv00_root1[/FONT] partition exists in the volume [FONT="Courier New"]vg001_lv00_root[/FONT], the other lv are similar.

Is it a bug or did I mix up something? Any help?

Thanks!

---

### Post by circle on 2012-05-02
> **circle said:**
> I just tried installing ubuntu on lvm with the standard livecd (desktop) but failed too.

here is what i did:
[LIST=1]
[*]Boot the host with live CD
[*]Install lvm2 package (apt-get install lvm2)
[*]create 2 partitions (sda1 for /boot, sda3 for lvm)
[*]create the the pv, vg, lv accordingly
[*]run the installer on desktop
[*]set the partition layout manually (sda1 => /boot, /dev/mapper/vg000-lv00_root1 => /, ..)
[*]proceed to the remaining steps of the installer
[*]before rebooting, i manually mount the lv accordingly, chroot inside and install lvm2 package
[*]reboot the computer
[/LIST]

but the computer doesn't boot :(

i noticed that the installer doesn't directly install on the created lv (e.g. [FONT="Courier New"]/dev/mapper/vg000-lv00_root[/FONT]). instead, it created a new partition inside the lv (e.g. [FONT="Courier New"]/dev/mapper/vg000-lv00_root1[/FONT]) and install on the new partition. after rebooting, it the partition was not automatically detected for some unknown reason. There are only [FONT="Courier New"]vg000-lv00_root[/FONT] but not [FONT="Courier New"]vg000-lv00_root1[/FONT] inside [FONT="Courier New"]/dev/mapper/[/FONT]. Failing to auto detect the partition inside the lv may be why the system cannot boot.

Interestingly using fdisk can actually confirm that the [FONT="Courier New"]vg001-lv00_root1[/FONT] partition exists in the volume [FONT="Courier New"]vg001_lv00_root[/FONT], the other lv are similar.

Is it a bug or did I mix up something? Any help?

Thanks!

Some updates. I am able to mount those partitions inside lv with the [FONT="Courier New"]kpartx[/FONT] utility but that's not done automatically by the bootloader so the computer is failing to boot.

I even tried to manually format those LV before running the installer, but the installer just force me to first create new partition inside the LV and reformat that for me again.

So it sounds like if wanting to install on LVM, the alternative CD must be used? :confused::confused::confused:

---

### Post by darkod on 2012-05-02
Well, it's much better and simpler to use the alternate. But it can't be done with the liveCD too.

I think you are missing a step after step 4. Did you create filesystem on the LV before starting the install? Since you are using the live cd I am not sure if it can do it correctly during install. It's better to create it yourself.

And in my test machine I did recently I never needed to chroot and install the lvm2 package. It worked fine without that step.

To create a filesystem from live mode on the LV, before you start the install, do something like:
sudo mkfs.ext4 /dev/vg000-lv000_root

NOTE: It's not mistake that /mapper/ is missing above. Use only /dev/VolumeGroup-LogicalVolume.

Do that for all LVs that you might have (root, swap, /home, etc).

In the installer when you enter manual partitioning there will be like two devices, the LV and underneath the created filesystem. Install on the filesystem. That's it.

---

### Post by circle on 2012-05-02
> **darkod said:**
> Well, it's much better and simpler to use the alternate. But it can't be done with the liveCD too.

I think you are missing a step after step 4. Did you create filesystem on the LV before starting the install? Since you are using the live cd I am not sure if it can do it correctly during install. It's better to create it yourself.

And in my test machine I did recently I never needed to chroot and install the lvm2 package. It worked fine without that step.

To create a filesystem from live mode on the LV, before you start the install, do something like:
sudo mkfs.ext4 /dev/vg000-lv000_root

NOTE: It's not mistake that /mapper/ is missing above. Use only /dev/VolumeGroup-LogicalVolume.

Do that for all LVs that you might have (root, swap, /home, etc).

In the installer when you enter manual partitioning there will be like two devices, the LV and underneath the created filesystem. Install on the filesystem. That's it.

Thanks darkod. I figured out the problems at last. There are a couple of problems causing the issue.

First of all, I created the LiveUSB on a 1G flash drive only and I have made a 128MB persistence storage there in case I want to store some temporary config script to be used next time. But that was a mistake because the space is easily get used up by logs or maybe also packages I installed (e.g. lvm2). The insufficient space made the installer failing to write some logs in certain action, thus throwing exceptions which result in incomplete installation and maybe some unexpected behavior in the installer. So one should either use a bigger USB flash drive or should not create persistence storage.

Secondly, I actually did try creating the filesystem before running the installer in order to prevent it creating partitions inside the volume for me but the computer didn't boot up either. That made me think that creating FS before installer didn't mean to work but in fact it is caused by my mistaken of forgetting to mount the /boot to /target/boot before chroot-ing and install LVM. That made the LVM package failed to change some config in the /boot folder (maybe for loading kernel module?).

After I realizing all these, I tried again and it succeeded at last.

And yes, using the alternative CD is definitely a easier way for setting up things like this. I tired that in 7.04 or something indeed. This time I am just a bit lazy to download the alternative CD again and being a bit geeky of wanting to try new things out... :guitar:

Anyway, thanks all and hope this info helps other.

---

