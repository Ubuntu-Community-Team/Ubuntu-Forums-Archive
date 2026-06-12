---
title: "No Grub showing, just going into Windows"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by raj727 on 2007-08-04
I've just installed Ubuntu 7.04 as a dual boot option with my previous install of Windows XP.  

On my first boot after installing Ubuntu, I was taken directly to the Windows XP screen.  I did not have any options to go into Ubuntu.  I keep going into Windows after rebooting my computer.  The Grub option does not appear.

I have two hard drives.  A 200 GB and a 400 GB.  The 200 GB has separate partitions for Windows XP (25 GB in NTFS), Windows programs and files (55 GB in NTFS), Ubuntu (119 GB as Ext3) and Ubuntu (1 GB as swap).  The 400 GB is all in FATS32 and contains some AVI files.  

Some guesses that may or may not have an impact on my failure to have a boot option for Ubuntu:

First, the 400 GB hard drive shows up as drive "a" while the 200 GB shows up as drive "b".   Maybe the 400 GB hard drive starts first and points to Windows XP before loading Grub?

Second, I used all remaining space on the 200 GB for swap before installing Ubuntu.  I don't know if I needed to leave some space for Grub.

---

### Post by Pumalite on 2007-08-04
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You probably didn't install Grub to the MBR (hd0,0) and need to re-install it.

---

### Post by sfgeorge on 2007-08-04
Hi raj,

The simplest test for seeing what's going on here in my opinion (which requires opening the case) would be to disconnect that 400GB drive and see what boots first.

If Windows boots first, then your MBR is probably controlled by Windows... as Pumalite described

If Ubuntu boots, then your first hypothesis is probably correct.

Good luck!

Stephen

---

### Post by raj727 on 2007-08-04
Okay I'm getting closer.

I tried to restore Grub using the instructions on Pumalite's second link, but still ended up going to Windows XP on bootup.

I then tried disconnecting the 400 GB hard drive followed by carrying out the instructions on the second link.  This time I got the Grub menu.  However, when I chose to boot Ubuntu, I got the following error:

Error 21: Selected disk does not exist
Press any key to continue

I keep getting the same message.

---

### Post by Pumalite on 2007-08-04
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

---

### Post by raj727 on 2007-08-05
Okay, I followed the instructions in link.

Now I get:

Error 22

I'm about to re-instill Grub according to instructions under Error 22.  However,  in the instructions "Re-install GRUB with LiveCD" link in the Error 22 section, one step states:

grub> root (hd0)

My question, I found Stage1 on "hd1,5".  Should I enter "setup (hd0)" or "setup (hd1)"?

My guess is "setup  (hd0)" but I don't want to make a mistake and loose my Windows XP os.

---

### Post by merlinus on 2007-08-05
```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute your results for (hdx,x).

From what you wrote, root should be (hd1,5) and setup (hd1).

-merlin

---

### Post by raj727 on 2007-08-05
Okay I entered:

setup (hd1)

But I still get "Error 22".   Am I doing something wrong?

---

### Post by raj727 on 2007-08-05
I went back into the LiveCD to try to re-enter your suggested "sudo grub, find /boot/grub/stage1" commands.  However I now get an Error 15 after entering "find /boot/grup/stage1".

---

### Post by merlinus on 2007-08-05
At this point, I recommend downloading and burning SuperGrub, and following instructions:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

SuperGrub is a great tool to have around, and this will make it all easier.

-merlin

---

