---
title: "Installing &amp; Using the New Kernel"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by SpecialEd.98 on 2009-12-10
Hello,

Thanks for taking the time to read my post. I've searched the forums (for "kernel", "upgrade", and "kernel upgrade"), but cannot seem to find the answer, so please excuse me if a similar post already exists.

I installed 9.10 about 3 wks. ago and I have to say I'm impressed with it, especially compared to my old OS...Windows XP Pro.

I have since installed updates a few times, which included the new kernels. I cannot remember the exact numbers, but it it went from something like 2.6.14 to 2.6.15, and is now at 2.6.16. 

So when I turn on my machine, grub shows me all these options (as well as Winblows) to boot in to and they all also have a "generic" version of the kernel (except Winblows of course).

So, my question is how to I get the latest kernel to use my previous settings?

I installed some drivers in 2.6.14 for my old Linksys Wireless B NIC and it worked. The drivers that came with 2.6.14 didn't work and it took a couple of hours for me to figure out how to get the newly downloaded ones to work, but I got it fixed.

Now I want the new kernel and any future kernels to "pick up" these settings so I don't have to go through this every time a new kernel version is released. Is this possible?

Thanks!

---

### Post by darkod on 2009-12-10
> **SpecialEd.98 said:**
> Hello,

Thanks for taking the time to read my post. I've searched the forums (for "kernel", "upgrade", and "kernel upgrade"), but cannot seem to find the answer, so please excuse me if a similar post already exists.

I installed 9.10 about 3 wks. ago and I have to say I'm impressed with it, especially compared to my old OS...Windows XP Pro.

I have since installed updates a few times, which included the new kernels. I cannot remember the exact numbers, but it it went from something like 2.6.14 to 2.6.15, and is now at 2.6.16. 

So when I turn on my machine, grub shows me all these options (as well as Winblows) to boot in to and they all also have a "generic" version of the kernel (except Winblows of course).

So, my question is how to I get the latest kernel to use my previous settings?

I installed some drivers in 2.6.14 for my old Linksys Wireless B NIC and it worked. The drivers that came with 2.6.14 didn't work and it took a couple of hours for me to figure out how to get the newly downloaded ones to work, but I got it fixed.

Now I want the new kernel and any future kernels to "pick up" these settings so I don't have to go through this every time a new kernel version is released. Is this possible?

Thanks!

The kernel is like the core of the OS but the drivers should be there for 31-15 and 31-16 too. I also installed some wi-fi drivers and the latest kernel works fine.
Did you try and your Linksys doesn't work in 31-16 or you just think it will not work?

A new kernel does not reset your settings.

---

### Post by SpecialEd.98 on 2009-12-10
darkrod,

thanks for replying. I booted into 31.15 last week (tried it about 4 times) and I couldn't get online. I then booted back into 31.14 and everything worked fine, so I assumed it was the new kernel.

I haven't yet tried 31.16, but will try it now.

On a side note, is there a way to get grub to list only the latest kernel to boot in to?

---

### Post by darkod on 2009-12-10
> **SpecialEd.98 said:**
> darkrod,

thanks for replying. I booted into 31.15 last week (tried it about 4 times) and I couldn't get online. I then booted back into 31.14 and everything worked fine, so I assumed it was the new kernel.

I haven't yet tried 31.16, but will try it now.

On a side note, is there a way to get grub to list only the latest kernel to boot in to?

That's strange. Depending what the settings were, you might need to redo them in newer kernels too. If it's only a driver that should work on newer kernels automatically.
Yes there is a way to remove them but it's always recommended to keep at least one older kernel that's working fine. This situation is exactly why. Something might not work in newer kernel, but work in older.
Solve your problem first, removing kernels comes after.

---

### Post by markbuntu on 2009-12-10
Of the driver did not come from the repo there is a good chance the module did not get built into the new kernels. You will need to do it manually. 

The kernel installer will try to build these modules when it is installing but sometimes that fails, especially if there is more than one module version to choose from. It happens all the time with nvidia and ati drivers and with the broadcom drivers if old modules are not removed before installing new ones. The installer  gets confused and skips installing them.

You will see messages to this effect if you are watching in the terminal as the new kernel is installing.

---

### Post by falconindy on 2009-12-10
Not strange at all. This is expected behavior. Extra drivers which are installed by a user will be associated with only the kernel they were built for. Wireless and graphics drivers are notorious for this. 

Essentially, if you had to install separate drivers to get a piece of hardware working, expect to do it every time you install a new kernel.

---

