---
title: "Ubuntu - Increasing space"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by jamal6008 on 2008-10-14
Hi

I am very new to ubuntu. I installed ubuntu through windows and gave 8GB available to it. Now its full and I want to increase it. Is there any way to do it except installing it all over again? Ubuntu is on different drive than windows and I have also freed up around 30GB on the drive ubuntu is, I just need ubuntu to associate that 30GB as its space.

Please help me

Thanks

---

### Post by BobJoe on 2008-10-14
sure, i had to do the same thing. now this entirely depends on the windows you have. if you have xp, get a 3rd party program like partition magic. if you have vista, just right click on the computer and click manage. resize the windows partition by however much. when it finishes (dont try jumping the gun), you need to reboot and start windows again (sometimes programs have boot stuff you have to do). then you need the original ubuntu live cd. this is because ubuntu locks its hard drive (dunno why). either burn one or find your previous one. the more recent the better. on the live cd, go to system > adminstration > gparted or partition editor. then just expand your ubuntu hard drive to however much. gparted is nightmarishly slow, so 30gb might take overnight. :)

---

### Post by Victormd on 2008-10-14
I think his is a Wubi install, not a normal dual boot.
If it is in fact a Wubi install, Ubuntu is installed on a "virtual drive" kind of like a program in windows, so you would need to reinstall and set the HD to the size you want (BobJoe's post won't work in this case) - Someone please correct me if I'm wrong.

If it's a dual boot, then follow BobJoe's post...

---

### Post by jamal6008 on 2008-10-14
I think my ubuntu is dual boot. I installed it through windows but when my computer boots I have to choose either to go in ubuntu or windows...? When I installed ubuntu the most I could choose was 10GB I am not sure why was that, I had total free of 14GB maybe because of that???

---

### Post by Victormd on 2008-10-14
I'm saying that it's [Wubi]("http://en.wikipedia.org/wiki/Wubi_(installer)") because you installed from inside windows. You didn't have to partition your HD and choose mount points, it was all done from an installer in windows (right?). This will still give you the choice to boot to windows or ubuntu, so theoretically it is a dual boot, but the concept I'm talking about is a bit different.
 
The dual boot install that I'm talking about uses the live CD to boot into a live version of ubuntu and install from there.

If you installed through a live CD, then you can use a partition editor/manager to resize your partitions, otherwise, you'll need to reinstall and choose a larger partition.

If your install was in fact a wubi install and you need to reinstall, I would suggest installing through a live CD. This will be a bit different (not as straight forward as the Wubi install) but you won't have size limitations (i.e., 10GB max that you were give before).

---

### Post by jamal6008 on 2008-10-15
Thanks for your help. Is it hard to install it the other way or is it almost the same? Will I need a separate partition which is empty for installing like this? Isn't there a way to install it again but without the 10GB limit Can't it be increased because the moment I installed this I had 14GB free on that drive so this might be the reason.

---

### Post by Victormd on 2008-10-15
It's not hard to install using the Live CD. You will need to create at least 2 partitions, one for the Ubuntu file system (what ever size you want) and the other for your swap partition (512MB to 2GB are enough). Then proceed with the install (I'm being simplistic here, you will need to make some choices, i.e., when the partition manager comes up, you should choose MANUAL and point to the partitions you've created; but it's not hard). Remember to always backup your data when creating partitions...

If you want to do the Wubi install again without the 10GB limit, you will need to defrag your HD using something like [JkDefrag]("http://www.kessels.com/Jkdefrag/"). It's a command line defrag software that can group all your files at the begining of the disk, leaving a bigger chunk for you to use. The arguments I use when running JkDefrag are:
```
JkDefrag.exe -a 5 c:
```
This will group all the files on your C drive. Check the [JkDefrag site]("http://www.kessels.com/Jkdefrag/") for more info on this.

---

### Post by jamal6008 on 2008-10-15
Thanks Victormd

I downlaoded the defrag software. I am running it from windows now. So I should uninstall ubuntu through windows? Will it remove it from the boot menu at start of system?

---

### Post by Victormd on 2008-10-15
Yes, you should uninstall using "Add or Remove Programs" in the Control Panel. This will wipe out everything. This includes any data that you have saved in your ubuntu desktop for example. This will also remove it from the boot menu.

---

### Post by jamal6008 on 2008-10-15
Thanks

Is it possible that I can make a new partition through windows by using the free space I have in different drives of same hard disk. I have done the defrag bit. If its possible how?

So then I can install it the way you said.

---

### Post by jamal6008 on 2008-10-15
I just tried to uninstall ubuntu I am having weird problems. Whenever i try to remove it through add remove programs nothing happens after clicking on uninstall nothing comes up similarly if i go to ubuntu directory and click uninstall icon there nothing happens. Any suggestions?

---

### Post by Victormd on 2008-10-15
> **jamal6008 said:**
> Thanks

Is it possible that I can make a new partition through windows by using the free space I have in different drives of same hard disk. I have done the defrag bit. If its possible how?

So then I can install it the way you said.

What version of windows are you using, Vista or XP?
If Vista, then there is a disk manager where you can partition your HD. If XP, then you can do it using the disk editor off of the Live CD or download the Gparted Live CD which is a dedicated partition manager (vista partitions don't like Gparted).

---

### Post by Victormd on 2008-10-15
> **jamal6008 said:**
> I just tried to uninstall ubuntu I am having weird problems. Whenever i try to remove it through add remove programs nothing happens after clicking on uninstall nothing comes up similarly if i go to ubuntu directory and click uninstall icon there nothing happens. Any suggestions?

Hummm... not really sure what to tell you here. I've never used Wubi to install/uninstall ubuntu. Hopefully someone with Wubi experience will jump in and help...

---

### Post by jamal6008 on 2008-10-15
Thanks once again.

I have XP and I am just downloading Gparted live cd. Can anyone help me to uninstall ubuntu please?

---

