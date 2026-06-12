---
title: "Rollback to Windows XP - mess up Grub?"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by squashpup on 2010-01-30
I'm thinking of downgrading Windows Vista to Windows XP on my laptop.  I have four partitions:

Partition 1: HP Recovery
Partition 2: Windows Vista
Partition 3: Ubuntu 9.10
Partition 4: Storage
Partition 5: Swap

If I simply install Windows XP on sda2, won't that mess with Grub?  If so, how would I fix it afterward?

Thanks.

---

### Post by hemimaniac on 2010-01-30
to be safe, i would format numbers 1 & 2 right out and make it one ( as they are both unneeded if you remove vista, then go ahead with the xp installation to that partition that you created, go thru the entire install process (3x as long as a ubuntu install i know) then after word you can boot to the live cd and reinstall grub2 (ubuntu 9.10 uses this instead of the legacy grub).

If you have any problems, [here]("http://ubuntuforums.org/showthread.php?t=1195275") is an excellent guide. but ultimately yes, the windows install will break the grub2 but it is all easily fixed.

---

### Post by kansasnoob on 2010-01-30
> **squashpup said:**
> I'm thinking of downgrading Windows Vista to Windows XP on my laptop.  I have four partitions:

Partition 1: HP Recovery
Partition 2: Windows Vista
Partition 3: Ubuntu 9.10
Partition 4: Storage
Partition 5: Swap

If I simply install Windows XP on sda2, won't that mess with Grub?  If so, how would I fix it afterward?

Thanks.

First boot into Ubuntu and run:

```
grub-install -v
```

That will determine what version of grub you have so you'll know what instructions to follow for recovering grub to the mbr, 0.97 is legacy grub and 1.97+ is grub2.

Then I'd use Gparted to delete both sda1 and sda2, but I wouldn't create or format a new partition. I've found it better to leave the "free space" unpartitioned and unformatted like they show on page #4 here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4)

The same tutorial shows how to recover legacy grub, to recover grub2 look here:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by squashpup on 2010-01-30
I spoke incorrectly before.  The first partition is the Windows partition. 

And I got Windows installed and booted it, because Windows XP overwrote the MBR, but couldn't get into Ubuntu. 

So, restored Grub using the Live Install cd.

Now, Grub comes up, but the Grub menu still has Windows Vista entries (and choosing either causes an error), and won't load Windows XP, even though I changed those entries in menu.1st.  I can still boot into Ubuntu normally, though. 

From a HD installed Ubuntu 9.10, is there a way to make Grub reconfigure and find changes in the installed operating systems?  

Thanks again.

---

### Post by hemimaniac on 2010-01-30
please post the output of 
grub-install -v

---

### Post by drs305 on 2010-01-30
Posting the results of meierfra's boot info script would be even better:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
Please post the results inside "code tags" - i.e. Use the # symbol in the post's menu.

---

### Post by squashpup on 2010-01-30
nevermind.  Got it.

Once I could get back into my Ubuntu installation, it was a simple matter of running: 

sudo dpkg-reconfigure grub-pc

and accepting defaults.

It found XP and added it to the menu.1st automatically.  Now I can dual boot as I did with Vista. 

Thanks anyway.

---

