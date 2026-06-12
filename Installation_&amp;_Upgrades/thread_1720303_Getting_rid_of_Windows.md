---
title: "Getting rid of Windows"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by SirLenz0rlot on 2011-04-03
Hi all, 

After discovering Ubuntu using VirtualBox in Windows 7 (64bit),
I knew choosing Ubuntu over Windows 7 would be a good choice for me.

Because I'm on a new laptop and wanted to make sure all drivers are available and work properly, I choose the Windows Installer for Ubuntu 10.10.

Everything worked great, however, I expected Ubuntu to make a new partition for me.

So, what is the best way for me to get Ubuntu on a seperate partition AND eventually how to get rid of windows (without messing up my boot-menu etc).

---

### Post by beew on 2011-04-03
> **SirLenz0rlot said:**
> Hi all, 

After discovering Ubuntu using VirtualBox in Windows 7 (64bit),
I knew choosing Ubuntu over Windows 7 would be a good choice for me.

Because I'm on a new laptop and wanted to make sure all drivers are available and work properly, I choose the Windows Installer for Ubuntu 10.10.

Everything worked great, however, I expected Ubuntu to make a new partition for me.

So, what is the best way for me to get Ubuntu on a seperate partition AND eventually how to get rid of windows (without messing up my boot-menu etc).

There is no Windows installer for Ubuntu, that is WUBI. WUBI is not a real dual boot, it is a sort of castrated version of Ubuntu working in Windows and it works out of one folder. 

If you want to get rid of Windows then the easiest way is just to install Ubuntu on the whole drive. For that you want to get a Ubuntu iso image, make a live usb [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")/[INDENT][/INDENT] Boot into the liveusb and install.

You can also dual boot with Windows, but that would be a bit complicated if you want to get rid of Windows later because after Windows is removed you would have to expand the Linux partition to the right to use the space (I think it may be problematic to move the Ubuntu boot partition to the right,--to the left is ok,--but not sure, I had a Windows/Ubuntu dual boot, after removing Windows I installed another Linux in the vacated partition instead of expanding Ubuntu, partly because of this)

Also you should use manual install in any case, that way you can specify two partitions (/ and /home) the /home partition keeps all your data and settings, in case you need to reinstall Ubuntu, say in a distro upgrade, all you need is to install over the / partition (and use the same /home partition as the new /home during install) 

Some people say that 15G is enough for the / partition, but I would recommend about 20G if you have the space since all your programs will be installed in the / partition and not knowing what you may install, it is better to leave some room. The /home partition is for your data and settings, so it could be as big as you want.  Both should be formatted as ext4.


However, before you do all that, better check that your hardware is compatible, especially for things like video card and wireless.

---

### Post by SirLenz0rlot on 2011-04-03
So the best way to switch to ubuntu entirely is reinstall it the 'proper way'? 


[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
says wubi IS the windows installer for ubuntu. Too bad I'm going to pay now for choosing the easy way... :(

---

### Post by Dutch70 on 2011-04-03
> **SirLenz0rlot said:**
> So the best way to switch to ubuntu entirely is reinstall it the 'proper way'? 


[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
says wubi IS the windows installer for ubuntu. Too bad I'm going to pay now for choosing the easy way... :(

Well, you can't really say your paying for doing it the easy way, since you were able to use that to confirm that it works well with your hardware.

If you have a lot of customizations that you don't want to lose, you can migrate your wubi install to it's own partition. 
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1639198[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1639198")

If you decide to do that, you can delete windows afterward and "move" the ubuntu partition all the way to the left, so you can "grow" it to the right.

Although if your going to get rid of windows totally, a fresh install usually takes less than an hour and is quite easy. 
[[COLOR="Red"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by SirLenz0rlot on 2011-04-03
> **Dutch70 said:**
> Well, you can't really say your paying for doing it the easy way, since you were able to use that to confirm that it works well with your hardware.

Totally true, but to be honest I noticed Ubuntu was installed on my windows partition after I installed everything :p 
(Setting up my development environments took me almost half a day)

> **Dutch70 said:**
> If you have a lot of customizations that you don't want to lose, you can migrate your wubi install to it's own partition. 
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1639198[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1639198")

If you decide to do that, you can delete windows afterward and "move" the ubuntu partition all the way to the left, so you can "grow" it to the right.

Although if your going to get rid of windows totally, a fresh install usually takes less than an hour and is quite easy. 
[[COLOR="Red"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

Thanks a lot, the wubi-thread seems awesome. Im gonna wait for another week to see if i really miss anything and then choose whether i'm gonna need windows or not.

Just one more question: I'd like to keep my Dell-recovery partition intact and still be able to use it when necessary (after all, ive paid about €100,- for windows :p)
I think booting from it goes from the windows 'booting thingy'
But im not sure.
Anyone any experience with it?

---

### Post by Dutch70 on 2011-04-03
> Just one more question: I'd like to keep my Dell-recovery partition intact and still be able to use it when necessary (after all, ive paid about €100,- for windows )
**I think booting from it goes from the windows 'booting thingy'**
But im not sure.
Anyone any experience with it?

I agree, it's a really good idea to keep your windows recovery partition.

As for the part in **bold**... I don't even know how to explain how much that confuses me. :tongue:

---

### Post by beew on 2011-04-03
> **Dutch70 said:**
> 
Although if your going to get rid of windows totally, a fresh install usually takes less than an hour and is quite easy. 
[[COLOR=Red]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

It takes 20 minutes max.

---

### Post by AndyBoy_LV on 2011-04-03
I would use something like Partition Magic to divide your hard drive into 2 or more partitions and then would install Ubuntu on one of the newly created partitions. That way, you can keep Windows and also have Ubuntu. 

After that, when you will feel you are ready to get rid of Windows,  you can easily format its partition.

---

