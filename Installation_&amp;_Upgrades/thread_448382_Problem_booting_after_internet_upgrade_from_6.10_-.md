---
title: "Problem booting after internet upgrade from 6.10 -&gt; 7.04 - no /dev/disk (!)"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by Borzo on 2007-05-19
Hi All,

I have just upgraded my notebook ( Acer travelmate 2490 ) from 6.10 -> 7.04, but it's not booting the new kernel, it's not even booting the previous one :(

Starting up ...
Loading, please wait...
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/2c31a149-1608-4832-ac01-92331302111a does not exist. Dropping to a shell!

I snooped into /dev but found out **i have no /dev/disk at all**
then i tried to boot the kernels one by one going newest -> oldest on the list and:
2.6.20-15-386/recovery mode - not booting
2.6.20-15-generic - booting ok
2.6.17-11-386/recovery mode - not booting
2.6.17-11-generic - booting ok
2.6.17-10-386/recovery mode - **booting ok** :confused:
2.6.17-10-generic - booting ok

boot/grub/menu.lst looks fine... so i'm lost especially that 2.6.17-10-386 is working...

It seems to be the same case as in this thread:
[http://ubuntuforums.org/showthread.php?t=443759&highlight=Does+Dropping+to+shell](http://ubuntuforums.org/showthread.php?t=443759&highlight=Does+Dropping+to+shell)
[http://ubuntuforums.org/showthread.php?t=430880&highlight=missing+modules%2C+devices%3A+cat+%2Fproc%2Fmodules+ls+%2Fdev](http://ubuntuforums.org/showthread.php?t=430880&highlight=missing+modules%2C+devices%3A+cat+%2Fproc%2Fmodules+ls+%2Fdev)
and a mention in one of the replies in this one:
[http://ubuntuforums.org/showthread.php?t=416568](http://ubuntuforums.org/showthread.php?t=416568)

help? :) thaks in advance - borzo

---

### Post by W. James MacLean on 2007-05-19
I'm having a similar problem...

I upgraded from 6.06 -> 6.10 -> 7.04 several days ago, and all was working well until I tried to boot my laptop this morning. I tried to login, and it told me my home directory was missing. When I booted in recovery mode (kernel 2.6.20-15-386), /home and /tmp were missing, and I saw error messages about these not booting.

I checked the UUID numbers with "vol_id -u" and they are correct in fstab, but when I tried to compare them with the values in /dev/disk/by-uuid, I found /dev/disk didn't exist!

I can mount /home using "mount -t ext3 /dev/sda7 /home", bu I suspect I shouldn't just edit fstab and do this, right?

So how to get /dev/disk/by-uuid fixed so the boot sequence proceeds properly and I can login?

---

### Post by Borzo on 2007-05-19
In my case it doesn't go as far as the logging part, it drops out to busybox after pausing a while on the "Loading, please wait..." 

My understanding of what is happening in my case is that there are no disks detected by the booting kernel so no /dev/disk is created(?) thus no such disk mentioned in the menu.lst exist  -> no fs to boot from.

I don't know about you James, it could be realted ... or not...since you are able to go as far as logging in - remember i can't do that even in recovery.

mmm... smells bug

borzo

---

### Post by earl1940 on 2007-05-19
Yeah, pretty much the same story here.  Had 6.10 running just great for several months and loved it. Installed and ran flawlessly in a dual boot with my XP.  Did the internet upgrade to 7.04 and now it will not boot.  Last line from the recovery mode kernel 2.6 20-15 is:
14.979053] ACPI:PCI INTERRUPT  0000.00.4629[A]>GSI16(level, low)>IRQ16

So..... the internet upgrade didn't work for whatever the reason.  And yes, I followed the instructions exactly; all of them.  But now I cannot boot from XP anymore either, only from 6.10 or 7.04 and it hangs after partly loading with the above message in the recovery mode.  And it does NOT allow me the option of booting from CD (a second download which md55um said was good).  I'm stuck; can't boot from the good 7.04  CD.  Can't touch the 6.10 partition (24Gb)  from XP.

What now? 

And here I thought I was doing just great for an old fart (I'm 66) with my 6.10, which worked perfectly.  I want my Ubuntu back; am tired of Windows except I need it for some programs, especially my genealogy.  Now I'm stuck with XP only; no Unbuntu.  I don't know whether to cry or get drunk.:mad:

Can someone more gifted than I help me? :(

Please?

There's a few Amstels in it for you:)

Ok, ok, a whole crate, then.  But you'll have to pick them up from my place.

Greetz to all my fellow Ubuntu fans.

Earl
Amsterdam

---

### Post by W. James MacLean on 2007-05-19
I was only able to get a root console up after booting in recovery mode.

The strange thing is that it work fine for several days before doing this.

Cheers,

James

---

### Post by Borzo on 2007-05-19
Earl, Your inability to boot XP might be linked to grub's /boot/grub/menu.lst, i have noticed on my desktop, where i dual boot with XP,  that the installer/updater ignored my root values and  changed the root values to (hd0,0) on all entries, including that of XP, not only that but it also changed the UUID's for the Linux disks aswell.

when booting from live CD or the generic kernel, do a sudo fdisk -l to find out where your XP is, then see if the root value for XP in /boot/grub/menu.lst is the same.

Good luck,
Borzo

> **earl1940 said:**
> 
So..... the internet upgrade didn't work for whatever the reason.  And yes, I followed the instructions exactly; all of them.  But now I cannot boot from XP anymore either, only from 6.10 or 7.04 and it hangs after partly loading with the above message in the recovery mode.  And it does NOT allow me the option of booting from CD (a second download which md55um said was good).  I'm stuck; can't boot from the good 7.04  CD.  Can't touch the 6.10 partition (24Gb)  from XP.

---

### Post by W. James MacLean on 2007-05-19
Good news, bad news.

Good news: I just found my problem, and have my machine back to normal.
Bad news: It's because of something stooopid I did, so it may not help you.

But, I will describe what happened, in case it does help.

I was workin on trying to get my fax modem working yesterday, and going through somebody's "how-to", had created a file named /etc/udev/rules.d/ltmodem.rules. It had one line in it, "SYMLINK="modem".

While trying to diagnose my problems today, I discovered and read /var/log/udev, and after every /dev/sdaX entry (I have a SATA drive, hence /dev/sda as opposed to /dev/hda), I found the last line to be

SYMLINK+="modem"

instead of something like /dev/disk/by-uuid/<whatever>, as I might have expected. Once I removed ltmodem.rules and rebooted, everything was fine.

I'd rather it be something stupid I did, as at least I can trust my installation again. I don't know if looking at /var/log/udev would help, but if you can do it, it might be useful. I noticed that in Borzo's case he  (she?) had to boot from another kernel, but I wasn't sure if that meant they couldn't get to a root console in recovery mode with the 2.6.20-15 kernel or not. If they can, it would be worth looking at the udev log.

---

### Post by Borzo on 2007-05-19
Well, like I said in my first post i can't boot into the recovery kernels, just the generic ones and the old 2.6.17-10-386 ( normal , recovery and generic ), plus i didn't make any changes, so i don't suspect i have done something to screw the bootup process, i simply rebooted after the updater finished and ...viola! sudden death.

Good thing i made a backup of 6.10 with partimage :), i'll fall back if i don't get this resolved in a few days.

---

### Post by Borzo on 2007-05-19
Ok, issue resolved!

This must have been screwed by the updater!, I booted into the only working kernel and then reinstalled the rest ( the non working kernels ), and now everything runs fine :)

---

