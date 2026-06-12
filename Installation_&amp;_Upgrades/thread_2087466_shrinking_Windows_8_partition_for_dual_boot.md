---
title: "shrinking Windows 8 partition for dual boot"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by parminides on 2012-11-23
I want to dual boot with Windows 8 and Ubuntu. When I run the Windows Disk Management utility, it will only allow me to shrink the Windows partition from about 700GB to about 340GB (I haven't done it yet). It says that "You cannot shrink a volume beyond the point where any unmovable files are located."

The Ubuntu installer (from LiveCD) has no such qualms. I'd like to leave only about 100GB for Windows 8 but am worried about these "unmovable files." Does the Ubuntu installer move them? Or is shrinking the Windows 8 partition asking for trouble?

---

### Post by darkod on 2012-11-23
Yes, the ubuntu installer will move them, it will not delete anything. But windows can be a real pain after detecting the move and until it sorts itself out.
On the other hand, Disk Management doesn't move those files.

You can try googling about shrinking with Disk Management when this problem exists, I think there was a way. For example, if those files are the pagefile of hibernation file, you can disable (delete) them temporarily, shrink the partition and create them again.

Another option is using Gparted from ubuntu live session and shrink the partition. DO NOT do it with the installer, use Gparted in live session and reboot into windows after that. That will allow it to try the chkdsk after the shrink.
If you do it with the installer and it continues with installing ubuntu, chkdsk can't start easily when booted from grub. That's why you need to do it and reboot few times BEFORE installing ubuntu.

---

### Post by ajgreeny on 2012-11-23
Is it possible in W8 to totally disable virtual memory, as you could in Vista?

That was the last windows I used before I moved to ubuntu and when I shrunk the Vista partition with windows disk management, I seem to remember that disabling virtual memory then defragging a couple of times allowed me to shrink it further.

Perhaps things have changed so much since those days that this is not possible any more.

---

### Post by parminides on 2012-11-23
Thanks for the replies. I'll try what darkod recommends (shrinking in gparted). If any problems persist, will reinstalling Windows 8 into the shrunken partition fix them? Is 100GB enough for Windows 8?

---

### Post by darkod on 2012-11-23
100GB is plenty, unless you install bunch of huge programs/games and loads of big data. Otherwise it can install on as much as 25GB and it will take about 12-13GB of that. Approx...

---

### Post by parminides on 2012-11-25
I changed my minded and ended up using Windows Disk Management to shrink the disk beyond the "unmovable" files.

Internet research led to the following steps. I'm not sure I did them in the order given, and I defragmented more times than is shown. Basically, I'd try something, do a defrag, and then try to shrink. Most of these steps didn't allow any extra shrinkage.

Using gparted would have been much, much easier, but I thought Windows might be more stable if I did it "the Windows way," which is given below.

1. disable pagefile: Control Panel -> System and Security -> System -> Advanced system settings -> Advanced tab -> [Performance] Settings... -> Advanced tab -> [Virtual memory] Change... -> uncheck Automatically manage paging file size for all drives -> select No paging file -> Set -> Yes -> OK...

2. disable hibernation file (hiberfil.sys): lower left corner rt click -> Command Prompt (Admin) -> powercfg /h off ["powercfg /h on" to turn it back on]

3. disable system restore: Control Panel -> System and Security -> System -> System protection -> select Local Disk (C:)(System) -> Configure... -> Disable system protection

4. disable writing debugging information: Control Panel -> System and Security -> System -> Advanced system settings -> Advanced tab -> [Startup and Recovery] Settings -> change Write debugging information from Automatic memory dump to none

5. disk cleanup: Control Panel -> System and Security -> Free up disk space [at bottom] -> check everything -> OK

6. reboot

7. defragment: Control Panel -> System and Security -> Defragment and optimize your drives [under Administrative Tools]

8. reboot

9. shrink Windows partition to ~100GB with Disk Management

10. reenable pagefile, hibernation file, system restore, and debugging info

I had some wifi problems during the first couple of bootups into Windows after reenabling everything, but after that Windows 8 seems to be working fine with 100GB.

Thanks, darkod, for your helpful suggestions.

---

