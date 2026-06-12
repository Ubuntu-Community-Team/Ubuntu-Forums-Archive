---
title: "Tough Install situation."
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by SpiffyRiffy on 2007-06-05
I have a friend's old laptop here that was in need of totally being wiped and we decided to give it a fresh new install of Ubuntu.

Here is the problem, though. The previous owners (we got the thing for free) decided to remove the CDROM and floppy drives for some reason. We don't have them. And the bios is too old to allow it to boot from USB devices.

There is hope, however. I have another spare laptop lying around I am going to sell soon, and I took the hard drive out and swapped it with the computer we are working on. The idea was to install ubuntu there, and then put it back in it's original laptop.

But the problem with that is, when we did it, it worked fine on the laptop we installed it on, but then when we put it back in it's original, nothing worked. Loaded in text based mode (couldn't find the screen.) and no networking either, not even for the built in ethernet plug. I'm assuming this is because it has all of it's modules installed/configured for the other computer. And to be honest, I am not really sure what kind of hardware it has, so getting the right drivers would be...difficult.

I was thinking about trying to create a new, small partition on the hard drive, and copying the install disc to that. Then booting from it and using it to install ubuntu on the rest of the system. Afterwords I could use something like gparted to remove the install partition and all would (theoretically) be good. The problem is I have no idea how to do that and it doesn't look like many other people have faced this problem...my extensive googling has come up dry so far.

I'm also still somewhat new to linux, by the way; so explaining any obscure commands would be helpful ;)
Anyway, any ideas would really be appreciated. Thanks in advance.

---

### Post by dabl on 2007-06-05
It sounds like a rather unnatural act that you're trying there, Spif.  *nix systems are built more or less from the ground up at the time of their installation, and are very unlike the MS DOS-based world where you can just throw the OS on a hard drive and then stick that hard drive in any other PC and expect success.  When you install *nix, including Ubuntu Linux, it "builds" itself on the BIOS information, the CPU that it sees, RAM, the hard drive controller, the combination of drives and partitions, the video display system, etc. etc., and then that is "the system" that you have on the hard drive.  You can't take that system and pop it in some other PC with different BIOS, CPU, RAM, etc., and expect it to run successfully, I'm afraid. :(

I guess if you could find two identical computers, you could pull it off, or if the only difference is video, then you could edit that one after moving the hard drive, and end up OK.

---

### Post by bapoumba on 2007-06-05
> **SpiffyRiffy said:**
> 
Here is the problem, though. The previous owners (we got the thing for free) decided to remove the CDROM and floppy drives for some reason. We don't have them. And the bios is too old to allow it to boot from USB devices.
Are there some spare parts stores around ? If the laptop is old, you may find a cdrom drive for almost nothing. Just an idea.

---

