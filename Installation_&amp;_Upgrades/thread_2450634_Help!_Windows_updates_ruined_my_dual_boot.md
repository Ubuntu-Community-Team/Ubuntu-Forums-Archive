---
title: "Help! Windows updates ruined my dual boot"
date: 2020-09-18
forum: Installation &amp; Upgrades
---

### Post by LotsOfStuff on 2020-09-18
I have a Dell XPS-15 7590, and some updates just killed my dual boot.  I've been able to repair these sorts of Windows update boot issues before, but I would appreciate some help on this one.

I ran boot-repair from a live USB and got this:
[http://paste.ubuntu.com/p/dZHrH5hBPY/](http://paste.ubuntu.com/p/dZHrH5hBPY/)

When I boot, I get a familiar looking set of boot options, but when it tries to boot up Ubuntu, it tells me:

"Gave up waiting for root file system device.  Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=173a8cbe-<redacted> does not exist.  Dropping to shell!"


Any suggestions?

---

### Post by CelticWarrior on 2020-09-18
Boot Windows and check whether Fast Startup has been re-enabled as it usually happens with major updates. Disable it if that's the case. Shutdown.
Then open your UEFI settings > Boot menu and put "Ubuntu" back as the first boot.
That should be all.

---

### Post by LotsOfStuff on 2020-09-18
Thanks for the suggestion.  Fast Startup was enabled, so I disabled it.  I had already moved Ubuntu to the top of the boot order, and I ensured it's still there.   However, I still get the BusyBox message and (initramfs) prompt when Ubuntu boots, which is the same thing that was happening before.

Details on the Windows updates that occured yesterday are here:
[https://www.catalog.update.microsoft.com/ScopedViewInline.aspx?updateid=12d4f3e2-1a12-4563-978b-96b1b621df36](https://www.catalog.update.microsoft.com/ScopedViewInline.aspx?updateid=12d4f3e2-1a12-4563-978b-96b1b621df36)
[https://www.catalog.update.microsoft.com/ScopedViewInline.aspx?updateid=3d6be63f-cc33-4071-a510-8810e902560d](https://www.catalog.update.microsoft.com/ScopedViewInline.aspx?updateid=3d6be63f-cc33-4071-a510-8810e902560d)

Searching around, I found these links:
[https://askubuntu.com/questions/741109/ubuntu-15-10-busybox-built-in-shell-initramfs-on-every-boot](https://askubuntu.com/questions/741109/ubuntu-15-10-busybox-built-in-shell-initramfs-on-every-boot)
[https://proposedsolution.com/solutions/ubuntu-booting-to-initramfs-prompt/](https://proposedsolution.com/solutions/ubuntu-booting-to-initramfs-prompt/)

It suggests running:
[FONT=&quot]fsck /dev/sda1[/FONT]

Does that make sense in my case?

I also see an option in Windows to uninstall updates.

Any advice?

---

### Post by Impavidus on 2020-09-18
Whatever damage the Windows update did, uninstalling the update won't reverse the damage. The output you get when you try to boot Ubuntu suggests that grub can find the initramfs (maybe in a separate /boot partition?), but that fails to mount the root filesystem because it isn't there, at least not with that UUID. There are some known cases of Windows deleting Ubuntu's filesystem (in particular, Windows 8 or 10 on an mbr drive can delete logical Linux partitions). Your boot-repair output on the other hand doesn't show your internal hard drive at all. A bit more information on the partitioning of your hard drive may help.

---

### Post by oldfred on 2020-09-18
Boot-Repair only saw your flash drive and as sda.
Is your drive an SSD or HDD? And NVMe drive?

Does Windows boot ok from UEFI boot menu?
So drive is ok and working?

Have you updated UEFI (or did a Windows update do that in background)?
It may have reset UEFI settings to defaults like turn AHCI off again. Review UEFI settings.

---

### Post by LotsOfStuff on 2020-09-18
It was the AHCI setting.  Thank you!  All is normal now.

I think my lesson for next time is: find the instructions I followed for setting up the dual boot originally and check all of the settings that were required to make it work.

Thanks everyone!

---

### Post by oldfred on 2020-09-18
Glad you got it working.

I do not have Windows, but every UEFI update has changed settings. 
My old BIOS system, I had to take photos, newer system gives me list of changes I made, so I make a copy.
And Asus lets me do screenshots of UEFI pages, so I have saved those.

---

### Post by dragonfly41 on 2020-09-19
I now keep my two Ubuntu installations on two colocated SSD's in a Startech dual docking hub (USB 3.0 connection gives acceptable performance).
When I do have to go into Windows 10 (the internal drive) I can switch off power to the Ubuntu docking hub.
This should guard against the "cuckoo in the nest" effects of Windows updates.
I have an old Ubuntu installation in the internal drive "alongside" Windows but that is not important to me.

---

