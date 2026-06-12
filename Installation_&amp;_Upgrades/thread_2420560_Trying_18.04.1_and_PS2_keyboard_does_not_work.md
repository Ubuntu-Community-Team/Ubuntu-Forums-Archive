---
title: "Trying 18.04.1 and PS/2 keyboard does not work"
date: 2019-06-06
forum: Installation &amp; Upgrades
---

### Post by Newbunto on 2019-06-06
I have 16.04 LTS running fine but want to upgrade to 18.04 LTS and hence decided to try (LiveBoot) 18.04.1

It boots fine but the PS/2 keyboard does not apparently work at all once booted. I know the keyboard itself works because in order to try 18.04.1 I have to use the keyboard to get into the boot menu on powerup and thereafter also to select the correct boot option. The USB mouse works fine and the LiveBoot environment otherwise appears to be normal.

If I go ahead and upgrade (i.e. shutdown, boot normally and let 16.04 upgrade) will I have the same problem? If so, is there anything I can do about it?
(Obviously not having a working keyboard is going to make fixing a problem after the upgrade more painful but I can SSH in from another computer after the upgrade and/or I think I can temporarily plug in a spare USB keyboard. Using a USB keyboard is not a viable permanent option.)

Has someone intentionally dropped support for PS/2 or is this a bug?

Edit for summary of all LiveBoot versions available to me.

16.04 Live - YES, works
16.10 Live - YES, works
17.04 Live - NO
18.04.1 Live - NO
18.04.2 Live - NO
19.04 Live - NO

---

### Post by Newbunto on 2019-06-06
PS Can't shutdown of course. Have to press and hold power button to 'crash' the computer. Because otherwise it wants me to press ENTER to remove installation medium.

The new lock screen behaviour also doesn't work unless there is a working keyboard.

---

### Post by Bashing-om on 2019-06-06
Newbunto; Hello -

I also run a PS/2 - mechanical - keyboard. I have no issues on all installs up to and including 19.04. However, make sure in bios that USB settings are set to "legacy" ( in my use case !).

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Newbunto on 2019-06-06
> make sure in bios that USB settings are set to "legacy"

I don't know what that does but the setting that I think you are referring to is and already was[INDENT][FONT=courier new]Legacy USB Support [Enabled][/FONT]
[/INDENT]

Here's a strange additional piece of information ... if during the LiveBoot boot I stop in the keyboard? language? configuration (sorry, I don't know what it is called, and the icon is hard to describe but it looks like the USS Enterprise :-) but this is a link to the screen [http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png](http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png) ), and I just keep English and don't change anything then the keyboard works !

---

### Post by Bashing-om on 2019-06-06
Newbunto; Hummm ...

With no keyboard - I can not at this time wrap my mind around how one can troubleshoot :(
will give it some thought on a means to proceed.

[INDENT][INDENT]stuck in the middle
[/INDENT][/INDENT]

---

### Post by Newbunto on 2019-06-07
> **Bashing-om said:**
> Newbunto; Hello -
I also run a PS/2 keyboard.


What colour and number of PS/2 ports do you have and what is the PS/2 keyboard plugged into?

A fairly old computer will probably have a purple port and a green port (I think purple is keyboard, green is mouse) i.e. 2 PS/2 ports. Maybe a more recent computer has a single PS/2 port that is half purple and half green (which may mean that you can plug in either a keyboard or a mouse but not both?).

---

### Post by Bashing-om on 2019-06-07
Newbunto; Yup
> **Newbunto said:**
> What colour and number of PS/2 ports do you have and what is the PS/2 keyboard plugged into?

A fairly old computer will probably have a purple port and a green port (I think purple is keyboard, green is mouse) i.e. 2 PS/2 ports. Maybe a more recent computer has a single PS/2 port that is half purple and half green (which may mean that you can plug in either a keyboard or a mouse but not both?).

I do run old hardware - circa 2007. I can confirm that purple is the keyboard and green is for the mouse.

Further for diagnosis purposes, if you boot a liveDVD, in this environment is the keyboard functional ? From here maybe we can do some poking about with mounting the installed file system from the live world.

[INDENT][INDENT]sometimes, just a hard way to go
[/INDENT][/INDENT]

---

### Post by Newbunto on 2019-06-08
> if you boot a liveDVD, in this environment is the keyboard functional ?

I am unclear whether you are making a particular distinction here but ...

I am currently running 16.04. I would like to upgrade to 18.04. Rather than just blindly upgrading and finding that it doesn't work, I decided to do a LiveBoot of 18.04 and found that it doesn't work. Hence I am in a position to delay the upgrade until hopefully I can sort this problem out.

The only difference between what I have tried and what I think you are suggesting is that I always do LiveBoot from a USB drive, rather than a DVD. Typically it is more hassle to find a blank DVD and burn it, and takes longer to write it and takes longer to boot from it.

---

### Post by Bashing-om on 2019-06-10
Newbunto; Thoughts -

Maybe this is a xorg thing ?

What results if you boot to a terminal interface from grub's boot menu ?
At the grub boot menu the 'e' key for edit => boot parameters screen
in the linux line similar: "linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff"
replace the quiet splash terms with the term " systemd.unit=multi-user.target ",
key combo ctl + x to continue the boot process to a terminal.

Does the keyboard work in this environment ?

[INDENT]maybe
[/INDENT]

---

### Post by Newbunto on 2019-06-11
> **Bashing-om said:**
> Newbunto; Thoughts -
Does the keyboard work in this environment ?


(in the meantime I have installed 18.04.2 from scratch on an external drive, for testing purposes)

1. Yes it does.

2. Those instructions are inherently contradictory though. So much typing on an ostensibly non-working keyboard. :-) For some reason though the keyboard does work i.e. works in BIOS, works at the boot menu, works at the GRUB menu, then works *or not *once finally booted.

3. The problem seems a bit heisenbug. After booting to the terminal and then shutting down and then booting normally, the keyboard works. Shutting down and switching off at the power point and then starting normally, the keyboard does not work.

---

### Post by Newbunto on 2019-06-11
I may have found the solution on the internet though. Recent versions may require the following additional boot options in order to work with my computer.

[FONT=courier new]i8042.nomux=1 i8042.reset[/FONT]

I don't know exactly what they do and I don't have time to test by a process of elimination whether they are both required or if not which one is required.

I have made the changes permanently (i.e. edit [FONT=courier new]/etc/default/grub[/FONT] and [FONT=courier new]update-grub[/FONT]) and the keyboard seems to work reliably from a cold boot. However the changes are only on the external drive at this stage. So I now need to do the upgrade that I originally wanted to do, make those changes (using any temporary workaround technique to get a working keyboard) and then try a cold boot.

---

### Post by Bashing-om on 2019-06-11
Newbunto; Hey hey !

Making progress ! It is an Xorg thingy -
Maybe time to submit a bug report ? Once you know the more.

[INDENT][INDENT]making things the better
[/INDENT][/INDENT]

---

### Post by &amp;wP*!) on 2019-06-11
Boot it with the problematic ISO again. Mark the location of /var/log/syslog of that session (which harddrive etc)
Boot it now with a working ISO. Copy the /var/log/syslog from the problematic ISO and paste it here.
Then we can take a look in a more detail.

---

### Post by Newbunto on 2019-06-13
> **pencuse said:**
> Boot it with the problematic ISO again.

I wish I could. The problem has gone away now. :-( In my original post, you can see that I tried 4 different recent LiveBoot Ubuntu versions that did not work. Now they are working. All I can say is that if the problem comes back, I will be sure to grab a copy of syslog and post relevant parts of it here.

In the meantime I had already gone ahead with the upgrade. So the internal disk is now running 18.04.2 and, with no workaround applied, the PS/2 keyboard is working.

I am as confused as ever but unless and until the problem comes back I think we will have to leave it.

---

### Post by Newbunto on 2019-07-04
Recognising that PS/2 is fairly obsolete these days, I've gone out and bought Plan B - a 2 x PS/2 to USB adapter. Works out of the box at all levels (BIOS, boot menu, GRUB, ...) without drivers etc. With that, the PS/2 keyboard should be able to be used for as long as it lasts.

---

