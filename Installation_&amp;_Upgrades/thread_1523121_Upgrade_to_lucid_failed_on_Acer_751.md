---
title: "Upgrade to lucid failed on Acer 751"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by kerze01 on 2010-07-03
Dear experts,

I upgraded (no: I tried to upgrade) my AO751 from 9.10 to 10.04. After the upgrade process the system rebootet automaticially, but stopped at a black screen and asked for an login.
After I typed in my login and password the system presents me a command line - nothing else.
I added the GMA 500 respiratory successfully based on the following instructions:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
But nothing changed.
I know, for an real linux freak the command line is a self-fulfilment, but I prefer the graphical interface.
Is there somone who is able to give me some tipps? Please note, that I am am a really novice - this means that i need the tipps in a very simple form.
I have to recover the system, because I was silly enough not to backup my data :-(

Thank you all for assistance

---

### Post by quixote on 2010-07-06
1) No worries about your data.  If you'd like to get a backup before doing anything else, 
boot with a livecd, 
attach a usb hard drive or whatever you'd like to back up to
open the file manager (eg by going to Places > Home)
select the drive in the left pane that's about the right size to be the one you want.
Go through till you find the folders you want and copy them to the external drive.

2) the boot problem is because it doesn't have the right driver for your graphics setup.  (Who knows why it couldn't carry it over from the earlier install.  Probably some random glitch.)

First try the easy "fix everything and hope it hits the target" method :D
Attach an ethernet cable to your computer.  Boot and when you're at the command line, notice whether the prompt looks like $ or #.  If $, you need to add "sudo" to commands.  If #, then you don't.  I'll assume it's $.  

I'm also assuming it's recognized your net connection.  If not, boot into "recovery mode" at the grub menu, and select "root shell with networking."  In that case, the prompt will be a # and you don't need sudo.
```
sudo dpkg --configure -a
```

If that doesn't just fix everything, we need to find out what your graphics card is.  Type ```
sudo lspci | grep 'VGA'
``` Copy the result over to your answer here.

---

