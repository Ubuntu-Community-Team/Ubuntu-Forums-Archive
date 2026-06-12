---
title: "I really could use a little help...."
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by christopher19 on 2014-10-08
I want to be able to stop booting from the usb and install it (Dual) on my laptop. I refreshed my PC from windows 8.1 and, besides just uninstalling my applications, it also looks like it uninstalled Ubuntu as well. Before the refresh it would start my laptop each time into Grub (I think that's what it's called) and gave me options to start Ubuntu, Ubuntu Options, and Windows Boot Manager. Now it goes straight to Windows Log In. The only way I've been able to start Ubuntu is with my "bootable" USB Stick...Any ideas on how to pull up the window to install Ubuntu?

---

### Post by papibe on 2014-10-08
Hi christopher19. Welcome to the forum ):P

If you were careful while reinstalling Windows, Ubuntu may be still there.

Boot into Ubuntu using your USB stick, and then follow this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") on how to use Boot-Repair to reinstall grub and look for other OSes besides Windows.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by christopher19 on 2014-10-08
> **papibe said:**
> Hi christopher19. Welcome to the forum ):P

If you were careful while reinstalling Windows, Ubuntu may be still there.

Boot into Ubuntu using your USB stick, and then follow this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") on how to use Boot-Repair to reinstall grub and look for other OSes besides Windows.

Hope it helps. Let us know how it goes.
Regards.

Thanks for the reply. But I didn't choose the reinstall option from the "advanced startup" menu (That one is "reset" I believe), I chose the "refresh" option(the one that is supposed to keep all settings but uninstall applications installed from the web. I think it restored everything back to the original settings. Do you think I should still try to use Boot-Repair?

---

### Post by papibe on 2014-10-08
Unfortunately, I'm nor familiar with that Windows process.

This is how I see it:
[LIST]
[*]If Ubuntu is still there, you would recover it.
[*]If Ubuntu was wiped out, you would only be installing grub. The computer would boot into grub, and the only choice would be Windows. If you later install Ubuntu, the installer would offer you to install or upgrade grub anyway so there's no problem there.
[/LIST]

Regards.

---

### Post by grahammechanical on 2014-10-08
I think that the Windows Refresh has restored the Windows boot loader which, of course, does not allow the existence of any operating system except Microsoft operating systems.

Either way, load the Ubuntu live session and use the Disks utility to see if the Ubuntu partitions are still there. Boot repair will be able to restore the Ubuntu boot loader (Grub).

Regards.

---

### Post by christopher19 on 2014-10-08
what are the Ubuntu partitions called? Are they labeled Ubuntu?

---

### Post by papibe on 2014-10-08
> **christopher19 said:**
> what are the Ubuntu partitions called? Are they labeled Ubuntu?
No but, if you open gparted, they would be formated as ext3 or ext4.

Regards.

---

