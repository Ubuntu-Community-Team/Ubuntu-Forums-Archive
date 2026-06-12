---
title: "installing ubuntu to an ext4 partition?"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by soraxd on 2011-03-02
I cuerently have w7 and want to make ubuntu my main os, and install it on ext4, so I need to create a partition and format it to ext4 right?totally lost on how do it.. I want linux main os on ext4 and w7 on ntfs ( I think its called ntfs). how can I format a partition to ext4 tho, cause windows wont let me give up much memory, not the 160 gb I want to give ubuntu.. totally lost, any suggestions?

---

### Post by houseworkshy on 2011-03-02
If you are duel booting the operating system that is inactive won't use any memory at all, so you don't need to worry about that.
Next it is important that at the beginning of the process that windows is the operating system that is on first because whilst linux will see windows and make a boot entry for it the converse is not true.
So put windows on a partition first leaving the other blank. Then restart with the live Ubuntu cd in drive, it should boot up.  Have a live cd session "try without making changes" an make sure your hardware is detected correctly, can go online for example.  Then go System>Administration>Hardware Drivers, this will scan to see if a driver is available for your graphics card.  Don't try to put it in, you are still in a live cd session, just see that there is one available and back out.

For a first try I don't recommend doing the partioning by hand.  Instead when you do install just select the empty partition and let the automatic installer take care of creating what is needed.

If you want to do it by hand the disk manipulating program is called Gparted.  It's not so hard to do if you want the learning process and there are plenty of guides around.

This is where to get the best advice on installing

[https://help.ubuntu.com/10.04/installation-guide/index.html](https://help.ubuntu.com/10.04/installation-guide/index.html)

I'd recommend the Lts, third party software has had time to catch up.

---

### Post by grahammechanical on 2011-03-02
May I add, do not check the Use Entire Disc box or you will loose your Windows OS.

The Ubuntu installer will partition and format the partition for you.

Regards.

---

### Post by houseworkshy on 2011-03-02
Yes that is what I meant by "just select the empty partition", you are right though and the emphasis is welcome chooseing "use enire disk" instead of "use entire partition" would spoil the duel boot experiance somewhat.

Also be sure that your bios is set to look for a boot from the cd/dvd first, if you get to a live cd session then it already is, if it doesn't one taps a key during the boot to get to a bios screen ( this varies from pc to pc, on mine it is delete ) then go through the menus and change the boot prioritys so that the cd/dvd is at the top of the list above the hard drive  ( but change nothing else ), then save and exit to resume booting.

---

