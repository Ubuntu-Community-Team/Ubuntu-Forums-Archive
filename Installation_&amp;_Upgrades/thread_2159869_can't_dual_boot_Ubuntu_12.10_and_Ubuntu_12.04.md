---
title: "can't dual boot Ubuntu 12.10 and Ubuntu 12.04"
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by goodbye-windows(tm) on 2013-07-04
Hi all,

I have Xubuntu 12.10 installed on my SSD, it works fine/normal.

Now, I want to add 12.04 in a separate partition, and choose which one I want to boot into from the grub screen.

To do this, I booted using the 12.04 live cd, made another smaller partition using gparted (using default settings), then chose 'something else' from the live cd menu. I told it to install 12.04 onto the newly created partition. 

There was an error, which I had to correct from the partitioning menu, I corrected this by choosing a mount point for the 12.04 partition ('/'). 

My 12.04 install started running and concluded without errors. When it said to restart the computer, I did so.

It started in the 12.10 install, with no mention of the new 12.04 partition. I knew this was a grub issue, so I opened a terminal and did an update-grub command. 

```
sudo update-grub
```

The grub updated without errors, and the output mentioned the second (12.04) partition so I concluded grub knew about both installs.

I shut down and tried to restart the computer. When I select the first (12.10 partition) from the grub screen, it started normally and 12.10 ran great. But, when I tried to start from the second (12.04 partition), it hung and sat there forever. 

The error was text on the screen, so I couldn't capture it to display in the forum. So, I took notes by hand. 

Here is the error sequence:

```
Begin: Running /scripts/init bottom ... done
[3.317012] usb 3.1.2: new low speed usb device number using ohci-hcd
fsck from util-linux 2.20.1
12.04 was not cleanly unmounted, check forced.
checking disk for errors, this may take a few minutes.
Press C to cancel all checks in progress.
12.04: 138453/796544 files (.2% non-contiguous), 686594/3181824 Blocks
mountall: fsck / [408] terminated with status ?? (sorry for '??', can't read my own writing)

*starting cups printing/server
```

Then it hangs.

I've never dual booted from 2 'buntu's OS before, what did I do wrong???

TIA

Art

---

### Post by fantab on 2013-07-04
Since you installed 12.04 after 12.10, the GRUB in control now is that of 12.04, assuming that you've not changed the location of GRUB install when you installed 12.04. So, you have to run '***update-grub***' from 12.04.

---

### Post by goodbye-windows(tm) on 2013-07-05
Thanks fantab.

But, I can't get into 12.04!!!!! So, not sure how to update the grub from the 12.04 installation.

When it told me to restart 12.04 to complete the installation, should I have run update-grub before restarting??? Was that my problem??

When I did do the update-grub from 12.10, it succeeded without errors and there was a line recognizing the 12.04 installation. When the grub screen appears, there are entries to boot from either installation. 

Can you give me an idea how to start the 12.04 install without going through grub?? 

TIA

Art

---

### Post by fantab on 2013-07-05
We need Grub to load OS.

What you can do is, use grub from 12.10. Boot into 12.10 and run:

```
sudo dpkg-reconfigure grub-pc
```

Then install grub to /dev/sda, the process is guided with GUI so you shouldn't have any problems.

Or just reinstall GRUB in 12.10 with:
```
 sudo grub-install /dev/sda
```

If you can successfully boot into 12.04 then either Remove 12.04 Grub (Recommended) or install 12.04 Grub to its own partition. Because we only need ONE GRUB/Bootloader. 

Good Luck...

---

### Post by goodbye-windows(tm) on 2013-07-10
Sorry for the delayed response. I did try to fix the issue last night. And, installing grub to the 12.04 partition worked great.

Many thanks for the info. 

I'll mark the thread as solved.

Art

---

