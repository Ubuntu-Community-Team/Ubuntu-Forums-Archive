---
title: "Multiboot system: Proper way to remove an install?"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2007-06-23
I had a multiboot Windows system.
I squeezed some space and did an install of ububtu, using the NT Loader to handle the multibooting.

I realized that it would be better to add another disk drive.
So, I installed ubuntu on the new drive, still using NT LOader to boot all 6 systems.
When I boot to the 2nd upuntu, the 1st ubuntu is mounted as sdf10.

Now, I want to get rid of the 1st ubuntu install.

The brute force method might be to:

1. Boot from te LiveCD.
2. Edit the menu.lst from te 2nd ubuntu to remove references to the first ubuntu.
3. Reformat the partition in which the 1st ubuntu lived.

Is there a better way?
Can I achieve the same goal by booting to the 2nd ubuntu and using GRUBB To modify menu.lst, then unmounting sdf10, and reformatting what was sdf10?

---

### Post by reiki on 2007-06-23
boot to second Ubuntu and use partition editor to remove the partition containing the old ubuntu install you will no longer be using.

If you're using the NT bootloader then the options for booting multiple operating systems should be in the boot.ini file on the primary boot drive. You should be able to simply edit out the entry for the unused Ubuntu install.

I will issue this warning though since I haven't used the NT boot loader in a long time...

Warning: Boot.ini is used on Windows XP and earlier operating systems.

Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 

So if you have Vista installed as well.... you may need to use BCDEDIT.exe instead of just editing the boot.ini file.

---

### Post by Howard Kaikow on 2007-06-23
Grumble, mumble, fumble!
Ouch!

There has to be a better way.

I tried the following:

Booted to 2nd Ubuntu.
Figured out how to get rid of the 1st Ubuntu.

This was not easy as there was a swap partition following, so I could not just delete sdc10, I had to move it after the swap partition.

I cleaned up by booting to Windows and using Partition Magic, indeed, I created a new swap partition.

Now the fun begins!

When I tried to reboot to ubuntu, fscheck failed because it could not resolve a UUID.
CONTROL-D was supposed to continue the boot, it did not work. I had to use CTRL ALT DEL, then the boot continued with the filesystem and my USB drives mounted, but not the other partitions on hard drives.

So, I said I'll show you!
I removed the references to the 1st ubuntu in menu.lst.
Alas, my glee was short lived!
Again, fscheck failed to resolve a UUID.
Again, CTRL ALT DEL got me to boot.

So, I again said, I'll show you!!!
I edited fstab to remove sdf10 and assigned sdf10 to the swap partition, which had been sdf11.

I was concerned about th eUUID of the swap partition, ah, but one step at a time.

I rebooted, voila, no error!.
It seems that even tho I had reformatted and re-identified the swap partition, the UUID had not changed.

Obviously, there's gotta be a better way to achieve te goal in this thread

---

