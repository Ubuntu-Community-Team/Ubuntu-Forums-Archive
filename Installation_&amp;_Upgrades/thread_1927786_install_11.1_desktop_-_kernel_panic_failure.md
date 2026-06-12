---
title: "install 11.1 desktop - kernel panic failure"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by pfbroome on 2012-02-18
Greetings all,

I am trying to install V11.1 on a fairly simple machine (one that had 10.04 on it before). The machine has 1Ghz Celeron CPU, 750MB memory, 160GB drive, standard CD, video & NIC etc.

When I boot from the CD I (fairly quickly) get a 'purple-ish' background with two icons on the bottom, center of the screen. The left one looks like a display icon for a spreadsheet and the right hand one looks like a simple figure of a person contained inside a circle.

The install will sit there for a while (1-2 minutes) then it blanks the screen, putting a rapidly blinking cursor in the upper left hand corner where it will sit for another little while.  The next thing I see is a message that reads:

[  21.607610  Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(9,1)

This is a new one for me. Anyone with any ideas _LEASE let me know.  Thanks  in advance for any and all help.

Pete

---

### Post by MAFoElffen on 2012-02-18
> **pfbroome said:**
> Greetings all,

I am trying to install V11.1 on a fairly simple machine (one that had 10.04 on it before). The machine has 1Ghz Celeron CPU, 750MB memory, 160GB drive, standard CD, video & NIC etc.

When I boot from the CD I (fairly quickly) get a 'purple-ish' background with two icons on the bottom, center of the screen. The left one looks like a display icon for a spreadsheet and the right hand one looks like a simple figure of a person contained inside a circle.

The install will sit there for a while (1-2 minutes) then it blanks the screen, putting a rapidly blinking cursor in the upper left hand corner where it will sit for another little while.  The next thing I see is a message that reads:

[  21.607610  Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(9,1)
Since it already runs 10.04, you have to look at the changes....

This is a new one for me. Anyone with any ideas _LEASE let me know.  Thanks  in advance for any and all help.

Pete

First suspect is the ISO image and how it was burned to disk.  If the  checksum on the ISO is good, Burn to the CD disk at the lowest speed  possible. 

Next, at the first panel you described with the person/keyboard Icon (indicating "Input") > Press the <Esc> key. That will bring up a low res language panel, then the Advanced Installation screen. 

Move the menu selection to the option you want to select with the arrow keys to the option you want to do... One of those options is Test the Disk... which will test the integretty  of the files of the LiveCD...

Of the others options, you can install from Install or Try. I would move the menu to Try, but before selecting that option, Press <F6>. Then arrow down to "nomodeset". Press <Esc>. Back at the Advanced Menu, move the cursor to "quiet" and replace it with " --verbose " Press enter.

This "should" select the option you moved the menu to previously... I usually "try" / boot into the desktop (hopefully) where I can confirm that it's going to work and do the install from there.

See if any of that gets you around your problem.  If not, I know 3 other ways.

With deleting "quiet" and adding in " --verbose "... the suppressed boot messages will display and other messages will also display.

Initial boot is in tty1. The install in text mode displays in tty1. In graphics mode the install displays in tty7. All the background install/system messages display from tty4. You can jump from one to another via <Cntrl><Alt><F1 through F7> with the function key going to <F1> for tty1. <F2> for tty2 and so on.

Starting into TRY, booting the desktop and installing from there... On error, you can see the message in the virtual terminals, as well as check the system.log to see what happened. It also gives you the ability to get to a virtual terminal to correct an unmet need or condition.

---

### Post by pfbroome on 2012-03-03
Greetings all,

...and MANY thanks who made some suggestions. I don't know if it was a fresh download on yet a 'different' computer and/or the creation of the new cd on that same different computer but I actually made it through ONE complete (near as I can figure) install.

I removed the CD and rebooted and THIS time I got a blank deep-rust/purple screen (with nothing on it) and then, a few seconds later I got the dreaded "input not supported" floating box.

I was able to reboot and get to a recovery console and ultimately to a RW remount so I could go change the GRUB resolution (in /etc/default/grub) to force a 640X480 resolution.  This step corrected a similar problem I was having ("Input not supported") on a newly installed 11.10 (32 bit) server.

After I changed the grub file to default to 640X480 and ran update-grub I rebooted and boom! right back to "input not supported". I never saw ANYTHING getting loaded (as I suspect the first thing desktop does is set the screen resolution).

I must have made the change to the wrong file OR I needed to change something else as well...I just don't know.  Incidentally, my monitor is an Acer V173 (which seems to have its own issues judging from other posts).

So again, I throw myself on the mercy of the wonderful ubuntu community and ask FOR ANY IDEAS, directions, things to check...whatever.  I am going to try to install OpenSSH so I can see if I can access the machine via terminal (I don't know if it is actually loading the OS after it blows the screen up at the beginning).  So any kind soul ...***HELP***.

MANY thanks in advance,

Pete

---

