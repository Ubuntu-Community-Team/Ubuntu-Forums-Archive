---
title: "Remove Ubuntu Dual Boot"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by dec913 on 2012-11-19
Hi
I have tried 12.10 on my netbook dual booting to see if I liked it, but I would like to remove it and return the laptop to the windows 7 booting it was before as it seems to be causing more problems with my wife(!) than it's worth. Having to select what to boot everytime, and windows performing a disk check every boot is becoming an issue.
How (can?) do I do it?

---

### Post by darkod on 2012-11-19
There should be no disk checks on every windows boot. But you have to make sure you are not leaving windows in hibernate, because you can't leave any OS in hibernate and then try to boot another one.

Also, it's very easy to make windows be the default so she doesn't need to touch anything, only wait few seconds.

But in any case, if you do want to remove it to save your marriage :) , first restore the windows bootloader to the MBR of the disk. Do you have any win7 install media or rescue cd?

---

### Post by slickymaster on 2012-11-19
How did you installed Ubuntu in the first place? Did you did a Wubi install within windows or did you install it with a LiveCD?

If it was Wubi, all you have to do is go to Add/Remove programs in Windows 7, find Ubuntu, and uninstall it like you would with any other program.

If it was using the LiveCD, the fastest way is to use the Windows 7 CD/DVD. Boot from it and select "Repair your computer". Then go to the boot folder. Inside you can execute the following line:

```
bootsect /nt60 C:\
```

That will eliminate the bootable part of GRUB and reinstall Windows 7 Boot way. After that you will have to remove the Ubuntu partition or partitions created with it. You can later merge them with Windows or install Ubuntu because you feel you made a mistake :mad:

---

### Post by dec913 on 2012-11-19
> **darkod said:**
> There should be no disk checks on every windows boot. But you have to make sure you are not leaving windows in hibernate, because you can't leave any OS in hibernate and then try to boot another one.

Also, it's very easy to make windows be the default so she doesn't need to touch anything, only wait few seconds.

But in any case, if you do want to remove it to save your marriage :) , first restore the windows bootloader to the MBR of the disk. Do you have any win7 install media or rescue cd?

I think the hibernation things is where part of the problem lies?
I would be happy to try it with windows as the default, how do I do that?
If that doesn't keep her happy, what would I need for that ... I don't have an install or rescue disk as it was all preinstalled on my netbook.

---

### Post by darkod on 2012-11-19
To set windows as default I prefer command line procedure. If you are more of a GUI person, usually people use Grub Customizer which can help them set the default OS. I think it should be in Software Centre.
EDIT: Grub Customizer thread: [http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

If you don't want to install it, and don't mind doing it in terminal, here is what I'm doing on my computers:
```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/06_os-prober
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

Right now, the first OS in the list (ubuntu) is the default. The above commands move windows to the top so it becomes the default.
If you also have a recovery partition that is showing in the grub menu and it's above the windows entry, let me know and you will need to change one more parameter.

If none of this makes the Mrs happy, you can still install an equivalent of the windows bootloader using linux tools. So, you can still do it, remove ubuntu and keep only windows. If it comes to that, let us know and we'll give you the commands.

---

