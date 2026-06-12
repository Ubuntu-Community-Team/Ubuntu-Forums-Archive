---
title: "Installed Ubuntu but will not load"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Neon612 on 2008-02-24
I just installed Ubuntu 7.10 to make a dual boot system. Windose XP was on first.

Heres my setup:
160GB Sata drive
     C: OS
     D: Data
160GB IDE Drive
     G: Data
500GB Sata Drive
     F: Empty but formated for Windose
     (Also on this drive is around 10GB with Ubuntu installed)

After I installed Unbuntu it tells you to restart, so I do. And Windose starts without even showing the GRUB Boot screen, Windows runs ChkDsk and I figure "Ok its checking for the new partition. great."

I shut down and restart hoping the GRUB screen will show up, but it doesn't and I'm into Windows again. Ubuntu is installed, but not recognized.

Then I put the LiveCD in to check the GRUB configurations.
Enter in the SUDO command to open /boot/grub/menu.lst
gedit opens up with a blank document, nothing in it.

What can I do to get the GRUB boot screen to show up?

---

### Post by mwray on 2008-02-24
Umm...
Which drive did you tell grub to install to? Generally speaking your C: drive is where grub should be loaded to. It sounds to me like grub is not installed properly, and needs reloading..in which case since you haven't booted to ubuntu yet, you should just reload.

Also, what OS is on drive C: (Obviously an windows variant...), secondly, it appears that your ubuntu is installed on a secondary sata drive. Does your motherboard support booting off of the sata directly?  If so, does it support booting off of any sata drive, or just the primary.

Also, recommended is making a separate home partition, so if you have to upgrade your distro, or change it, your data in your home directory remains.

---

### Post by Neon612 on 2008-02-24
When I installed it there was no mention of GRUB in the process.

Drive C is Windows XP Pro

IS it a good idea to have C (The Windows Boot sector) and the unbuntu boot sector on the same drive?

And what do you mean by this statement:
> **mwray said:**
> Also, recommended is making a separate home partition, so if you have to upgrade your distro, or change it, your data in your home directory remains.

---

### Post by confused57 on 2008-02-24
> **Neon612 said:**
> When I installed it there was no mention of GRUB in the process.

Drive C is Windows XP Pro

IS it a good idea to have C (The Windows Boot sector) and the unbuntu boot sector on the same drive?

And what do you mean by this statement:
Sometimes when there is a mix of IDE & SATA drives, grub's IPL(Initial Program Loader) is automatically installed to the IDE drive's mbr...you could try setting your bios to boot first to your IDE drive to see if this is the case.

---

### Post by Neon612 on 2008-02-26
I'll try booting from the IDE drive tonite, an dhopefully it will work. Thanks

---

### Post by Chappy7777 on 2008-02-26
> **Neon612 said:**
> I'll try booting from the IDE drive tonite, an dhopefully it will work. Thanks

If it works please post the fact here so that if others have the same problem, they'll see the fix.

---

### Post by Neon612 on 2008-02-26
Thank you everyone that posted. I set the IDE drive as the first to boot and everything worked great.

Now if I could just fix the OS boot order.

---

