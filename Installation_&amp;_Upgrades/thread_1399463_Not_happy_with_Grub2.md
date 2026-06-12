---
title: "Not happy with Grub2"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2010-02-05
IMHO its a long way from ready for prime time.  I really hope it is not the default for 10.04, or if it is, the installer offers clear options to install Grub instead.

This about sums it up, from /usr/share/doc/grub-pc/README:
"For now, there is not much documentation yet. Please look at the GRUB
Wiki <http://grub.enbug.org> for testing procedures."


I've 9.10 installed multi-boot with 8.04 and 6.06.  Got a kernel update for 8.04 today and I've not a clue as to how to make Grub2 boot it.  The menu only offers the kernels that were there when 9.10 was installed.

9.10 is on a drive in a removable carrier, I can remove it, put back the Windows drive with grub on it and fix the /boot/grub/menu.lst in less time that it took me to figure out I've no idea how to do it in grub2 :(

Problem is at this point in time I'm more interested in using 9.10 than Windows on this box, but 8.04 and 6.06 are why I have the box and must be available when I need them.

Now I see there is kernel update for 9.10, perhaps in will automatically fix my multi-boot, but before I try, I need to see if there are 6.06 updates.

Nobody cares about the bootloader until it doesn't work.  I'm sure seeing a lot of cries for help on dual boot systems with Grub2 and not a lot of "solved" :(

---

### Post by kansasnoob on 2010-02-05
Just revert to legacy grub for now:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I'm already testing Lucid and I'm fairly sure it's grub2 will be working very well.

BTW I have tried to get the newer version of grub2 in Karmic:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/509438](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/509438)

---

### Post by presence1960 on 2010-02-05
> **wkulecz said:**
> IMHO its a long way from ready for prime time.  I really hope it is not the default for 10.04, or if it is, the installer offers clear options to install Grub instead.

This about sums it up, from /usr/share/doc/grub-pc/README:
"For now, there is not much documentation yet. Please look at the GRUB
Wiki <http://grub.enbug.org> for testing procedures."


I've 9.10 installed multi-boot with 8.04 and 6.06.  Got a kernel update for 8.04 today and I've not a clue as to how to make Grub2 boot it.  The menu only offers the kernels that were there when 9.10 was installed.

9.10 is on a drive in a removable carrier, I can remove it, put back the Windows drive with grub on it and fix the /boot/grub/menu.lst in less time that it took me to figure out I've no idea how to do it in grub2 :(

Problem is at this point in time I'm more interested in using 9.10 than Windows on this box, but 8.04 and 6.06 are why I have the box and must be available when I need them.

Now I see there is kernel update for 9.10, perhaps in will automatically fix my multi-boot, but before I try, I need to see if there are 6.06 updates.

Nobody cares about the bootloader until it doesn't work.  I'm sure seeing a lot of cries for help on dual boot systems with Grub2 and not a lot of "solved" :(

Just as it was when you first used GRUB Legacy 0.97 you are going to have to study and learn GRUB2. I am quite certain you knew little or nothing about GRUB Legacy when you first started using it. Such will be the case with GRUB2. IMHO GRUB2 is way better than GRUB legacy 0.97.

Check out this link so you can learn: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If you are looking for GRUB Legacy in Lucid you will be disappointed as GRUB Legacy is being phased out as of now.

---

### Post by wkulecz on 2010-02-05
Upgrades to 6.06 are booting because they have been 2.6.15-55.xx for a long time and the  2.6.15-55 image is over written,  so the name grub2 is looking for remains the same.  Of course this means I can't boot really boot the previous kernel if there is a problem, I'd have to go back to the last one in the 2.6.15-54.xx series which fortunately seemed to work OK, and actually I've had no kernel update issues with Ubuntu since 5.10 -- which was really an out of sync module version issue.

But the 8.04 upgrade changed the dash number so the name Grub2 will need to be looking for has also changed :(


I'm afraid "Just revert to legacy grub for now." is not a very good answer to the Windows user that wanted to "try Linux" and now has a broken system and no idea of how to revert even (especially) after reading the "instructions"

Is a choice of boot loaders at install time too much to ask for?  Asking me to throw away all my hard won grub knowledge for something "better" that is almost devoid of useful documentation with absolutely no evidence that "better" has any value to me whatsoever, is just ridiculous.

---

### Post by wkulecz on 2010-02-05
> Just as it was when you first used GRUB Legacy 0.97 you are going to have to study and learn GRUB2. I am quite certain you knew little or nothing about GRUB Legacy when you first started using it. Such will be the case with GRUB2. IMHO GRUB2 is way better than GRUB legacy 0.97.

Way better? Says you, in what way?  List a few. 

Unless it solves all issues with booting all varieties of RAID I can't imagine one thing that would make it worth the effort to learn since other than the RAID issues grub more than meets my needs and I already know how to fix it when something goes wrong.

Different is not better, better is better and I see zero better in Grub2 so far.

---

### Post by presence1960 on 2010-02-05
[http://news.softpedia.com/news/GRUB-2-The-New-Boot-Loader-in-Ubuntu-9-10-113671.shtml](http://news.softpedia.com/news/GRUB-2-The-New-Boot-Loader-in-Ubuntu-9-10-113671.shtml)

GRUB Legacy is so outdated. it hasn't been upgraded since 1996. Do you like using windows 3.1 or windows 95? I know that may be an exaggerated comparison, but truthfully GRUB Legacy is that old and hasn't been changed since 1996.

As far as GRUB2 issues not being solved on here I beg to differ because I have seen many helped on here by the likes of drs305, herman, kansasnoob, leppie, raymondh, meierfra and countless others as well as myself.

The bottom line is you can complain all you want. That is your right. but it will not help you. GRUB2 is here to stay and GRUB Legacy is out! You would be better served investing your time in learning GRUB2 rather than griping about what has already become the inevitable. If you don't eventually you will be left out in the cold I am afraid!

---

### Post by presence1960 on 2010-02-05
> **wkulecz said:**
> **_Way better? Says you, in what way? _** List a few. 

Unless it solves all issues with booting all varieties of RAID I can't imagine one thing that would make it worth the effort to learn since other than the RAID issues grub more than meets my needs and I already know how to fix it when something goes wrong.

Different is not better, better is better and I see zero better in Grub2 so far.

That discussion has already been waged and the results are final. The devs aren't going to change what is best for most in favor of a few who refuse to adjust.

_P.S. you know, you are entitled to your opinion, but that won't change anything. unfortunately both of us have wasted time here on a point that is not up to question- the fact that GRUB Legacy is now retired as bootloader of choice going from 9.10 forward. I think both you and I can find better things to do. I am moving on to try to help someone and hopefully learn some more myself._

---

### Post by falconindy on 2010-02-05
I'm using Grub .97 until it breaks, and there's no sign of that happening any time soon. Early userspace isn't something that sees major changes very often. Grub2 is needlessly complex for a process that happens about 3-4 times per month on my machine. Grub2 also wouldn't be able to boot my machine without unsupported patches (btrfs).

Fun facts: number of "TODO" and "FIXME" comments in grub source code:
```
         FIXME    TODO
grub1       49       6
grub2       67      30
```

Yes, I understand grub1 isn't in development any longer but grub2 is far from complete, and again, grub1 **still works**. From grub2's FAQ:
> It is usable, but we are still making incompatible changes from time to time.

---

### Post by kansasnoob on 2010-02-05
I love grub2. I think it's actually much simpler to deal with now that it's matured - in Lucid!

In Karmic it's been a nightmare. People just want a bootloader to work! - Consistently!

The devs believe it would cause more problems to update grub2 to - well at this point I don't know what's stable - but look here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457)

And here I gave an extra push:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/509438](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/509438)

The bottom line is that Ubuntu is always on the bleeding edge of development. Not every release can be expected to work perfectly for everyone.

Some people argue that they should change the 6 month cycle and I disagree. I think Canonical has it just right.

I'm nowhere near dev level but I think I've become a somewhat reliable "tester" and there are ongoing problems with grub2 in Karmic that simply turn people away from Ubuntu altogether.

---

### Post by meierfra. on 2010-02-06
>  I've no idea how to do it in grub2
Did you try 

```
sudo update-grub
```

This is one of the real advantages of Grub2, "update-grub" will automatically detect changes in other operating system. No need for manual editing.

---

### Post by Mark Phelps on 2010-02-08
I've been pleasantly surprised by how well GRUB2 has worked.

When I was running GRUB legacy, I did a test "upgrade" to GRUB2 -- and it was a disaster!  Nothing booted after that.

But, after I restored from backup (after all, that's what these are for!), I later installed 9.10 "clean", rebooted my machine, did an update-grub -- and every OS and kernel was found.  

And, they all boot now without any problems at all.

Eventually, we'll have a GUI version that will make customizing easier for those that don't want to read instructions.

But, as the others have already said, there's no value in complaining about something that has been "retired".

---

