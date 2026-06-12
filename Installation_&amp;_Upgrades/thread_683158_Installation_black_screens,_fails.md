---
title: "Installation black screens, fails"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by plethorex on 2008-01-30
First, I'm not very well versed in Linux at all, so most every "solution" I've found to my problem has gone right over my head.

Here is my issue.  When I run the Ubuntu installer when my computer boots, I get the BootSplash screen, but if I choose any option that includes the word "Install" my monitor goes into power saving mode, and never displays anything again.  Sometimes the computer will shut itself off after 2-3 minutes, sometimes it just sits there for (seemingly) forever, doing nothing.  This issue works with both the regular install option, the limited graphics install option, and several command line codes I've been advised to type in (pressing F6 at the install screen.)

I assume that the issue is my Nvidia 8800 GT video card, however, I do not know how to fix the issue.  I read a lot about installing drivers and such, but I can't even get past the introduction screen, let alone actually do anything productive.  Is there a fix, or am I waiting till April in hopes the next release supports the newer Nvidia cards?

Thanks for any help.

---

### Post by overdrank on 2008-01-30
> **plethorex said:**
> First, I'm not very well versed in Linux at all, so most every "solution" I've found to my problem has gone right over my head.

Here is my issue.  When I run the Ubuntu installer when my computer boots, I get the BootSplash screen, but if I choose any option that includes the word "Install" my monitor goes into power saving mode, and never displays anything again.  Sometimes the computer will shut itself off after 2-3 minutes, sometimes it just sits there for (seemingly) forever, doing nothing.  This issue works with both the regular install option, the limited graphics install option, and several command line codes I've been advised to type in (pressing F6 at the install screen.)

I assume that the issue is my Nvidia 8800 GT video card, however, I do not know how to fix the issue.  I read a lot about installing drivers and such, but I can't even get past the introduction screen, let alone actually do anything productive.  Is there a fix, or am I waiting till April in hopes the next release supports the newer Nvidia cards?

Thanks for any help.

HI and welcome, You can try and press F6 key at the start and install, this will allow you to edit  the kernel line and you can remove the quiet splash and add vga=771  or vga-775 and then hit enter. And if you just want to install without using the live cd you can use the alternate to install. It install on  a text based.  Hope this helps. Good luck!

---

### Post by plethorex on 2008-01-30
Well, I removed "quiet splash" and replaced it with both of the vga= commands you gave me.  771 causes it to show me a list of modes that I can't understand, 775 leads back to the power saving screen.  I also tried "noapic nolapic pci=noacpi acpi=off" which I found in another thread.  That got me some visual feedback, a bunch of command lines, then a brief GUI saying I was in low-res mode.  However, if I choose "continue" it goes back to the command line screen and dies.  And if I choose configure, no matter what options I set, it goes back to the command line and dies.

---

### Post by Rocket2DMn on 2008-01-30
I would say try the alternate install cd like overdrank suggested - it is just a text based installer without a live session, but it works very well.  It sounds like the LiveCD just doesn't like your video card at the moment, but once you get Ubuntu installed, the video card is easy to troubleshoot.
Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box for Alternate at the bottom.

---

### Post by plethorex on 2008-01-30
Well, Ubuntu is installed.  The new problem is, when I restart my computer, it automatically loads Windows.  I've tried using the command line to force GRUB into showing when I restart, but regardless of my attempts, it always reverts.  The only way I have to boot from Linux right now is to put in the Ubuntu CD and choose "Boot from first hard drive" option on the list.

---

### Post by Partyboi2 on 2008-01-30
try reinstalling grub with the live cd. see [here]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by plethorex on 2008-01-30
I have tried doing those steps, and when I restart my computer, it automatically loads Windows XP.  I never see a menu to choose from, I never see any "push suchandsuch button to load.."  BIOS startup messages, blinking cursor for ~2 seconds, Windows XP logo.

---

