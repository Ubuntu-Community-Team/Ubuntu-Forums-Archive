---
title: "Trapped in the Grub Terminal... SOS!"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by squeaky2 on 2015-01-26
Hey! I'm in something of a jam here, and was wondering if someone here can give me some advice.

I'm pretty new to Ubuntu. I've only had it running for about a month (14.10 with Distro-update), so I'm not a very advanced user. I like keeping a clean computer, with as few temporary files and junk as possible. To keep my pc as clean as I could, I ran BleachBit frequently and it worked wonderfully. But then I kept seeing a growing pile of 'error' messages; 1,800+ error messages to be exact. I thought that they might be orphaned directories, so I ran the GTKOrphan tool. That was a MASSIVE mistake.

Whoever designed that thing... you really got to work on what you define as 'optional' and 'important'. I deleted almost everything that came up without bothering to read the filenames... I reboot my computer and I'm trapped in the GRUB command-line. I can't get out. I don't know how what directories and libraries are destroyed. I don't know how to boot the LiveCD ISO on my USB key or my CD-Rom. I've tried several different places and asked a ton of people about how to fix my problem, and have come up dry for the past three days.

Help me, Obi-Wan Kenobi. You're my only hope.

---

### Post by sammiev on 2015-01-26
I would boot from a live USB/DVD and save all your data.

Then a fresh install and never use BleachBit again.

I use this to clean from Terminal.

> echo "Cleaning Up" && sudo apt-get -f install && sudo apt-get autoremove && sudo apt-get -y autoclean && sudo apt-get -y clean

You may want to wait for others to reply as there is more than one way to do things.

---

### Post by QIII on 2015-01-26
Hello!

This is a volunteer forum of users just like you.  So nobody here can answer for bleachbit.  Although you will see it recommended from time to time on the Forums, I, for one, don't recommend it.  Your situation is an example of why.

Anyway:

I agree with sammiev.  My recommendation, for the time being, is to back up all of your important files to removable media using a Live session. That will keep you from losing anything important while you sort this out.

Aside from that, don't do anything just yet.  Someone else may have a bright idea.  But I have only three circumstances for which I recommend re-installation out of hand:

1.  A compromised machine.
2.  Random recursive modification of file permissions.
3.  Random mass deletion of unspecified files.

I have to be honest:  Your system is likely so borked it will have to be nuked from orbit.

---

### Post by squeaky2 on 2015-01-27
> **QIII said:**
> Hello!

This is a volunteer forum of users just like you.  So nobody here can answer for bleachbit.  Although you will see it recommended from time to time on the Forums, I, for one, don't recommend it.  Your situation is an example of why.

Anyway:

I agree with sammiev.  My recommendation, for the time being, is to back up all of your important files to removable media using a Live session. That will keep you from losing anything important while you sort this out.

Aside from that, don't do anything just yet.  Someone else may have a bright idea.  But I have only three circumstances for which I recommend re-installation out of hand:

1.  A compromised machine.
2.  Random recursive modification of file permissions.
3.  Random mass deletion of unspecified files.

I have to be honest:  Your system is likely so borked it will have to be nuked from orbit.

LOL Thanks for lightening the mood. :) I had backed up my files before I started tinkering with the computer, so I guess that's a lucky break. Well, *cracks knuckles* Guess I get to learn how to reformat and reinstall an operating system.

---

