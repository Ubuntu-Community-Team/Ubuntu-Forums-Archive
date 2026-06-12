---
title: "GRUB can't find menu.lst, and can't boot kernel"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by hbquikcomjamesl on 2010-02-10
I seem to have determined a few other things about my "only gets as far as a GRUB command line" problem:

To recap, sda3 (GRUB hd0,2) is the main Linux partition; sda9 (GRUB hd0,8) is the boot partition.

GRUB is 0.92.
Installation was from an 8.04LTS live CD (at least, that's what the envelope says it is)/

"/boot/grub" (i.e., "/grub" on sd9/hd0,8) contains a "menu.lst" file. I modified it (had to do a "sudo gedit" from a command line!) to (1) comment out the line that hides the boot menu, (2) change the timeout from 3 seconds to 90, and (3) add a menu line based on my succesful manual IPL of DOS.

It still boots to a GRUB command line. If I do a "configfile /grub/menu.lst," a boot menu comes up. DOS will successfully IPL, but Linux still gets a "no setup signature found," (ditto for "recovery mode"), which suggests either a bad kernel, or a kernel that's too big for the GRUB to handle.

Why would it be finding its way to grub, but not finding the boot menu file?

Why would the live CD come up just fine, yet the GRUB and kernel it installs fail?

---

### Post by northrup on 2010-02-10
Which GRUB is giving you problems, the one on the boot partition or the one on your main Linux partition?  Or is the one on the boot partition the only one?

---

### Post by hbquikcomjamesl on 2010-02-10
So far as I'm aware, the one on the boot partition is the only one.

And certainly that's the partition I'm in when it comes up to a GRUB command line.

---

### Post by northrup on 2010-02-10
Okay then.  Here goes a nice long list of questions.

First, did you install Ubuntu before or after you set up GRUB on the separate partition?  8.04 defaults to installing GRUB on the same partition as Ubuntu itself, although it might default to using an existing GRUB installation if it's present; I've never installed Ubuntu alongside another Linux distro, so I don't know.  Check if Ubuntu set up an additional copy of GRUB on sda3, and if so, you could try chainloading into that instance of GRUB instead of attempting to boot the kernel directly.

Also, make sure that the entry in menu.lst is pointing to the vmlinuz-x.x.xx-generic file.  It should be working fine if it is.  I presume the binary is on the Linux partition in the /boot directory.

---

### Post by lidex on 2010-02-10
Firstly, follow this procedure:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

More info here:
[http://www.troubleshooters.com/linux/grub/grub.htm]("http://www.troubleshooters.com/linux/grub/grub.htm")

---

### Post by hbquikcomjamesl on 2010-02-10
Driving home, (I'll be able to pursue this further tomorrow), a thought struck me:

The GRUB that comes up in a command line self-identifies as 0.92

But there's a file in /boot/grub that says 0.97 (which is what I thought Ubuntu 8.04LTS came with).

What if there's another GRUB lurking somewhere, that I don't know about?

Also, if I open up a terminal window, "sudo fdisk -l" gets me a report that looks completely unremarkable, except for one thing: in the "boot" column, there is exactly one asterisk, and it's on my primary DOS partition:

```
 Device     Boot Start    End     Blocks    ID   System

/dev/sda1   *       1      7      56196     6   FAT16
/dev/sda2           8    250    1951897+    5   Extended
/dev/sda3         251  19000  150609375     83  Linux
/dev/sda4       19001  19457    3670852+    82  Linux swap/Solaris
/dev/sda5           8     20     104391     6   FAT16
/dev/sda6          21     97     618471     6   FAT16
/dev/sda7          98    174     618471     6   FAT16
/dev/sda8         175    225     409626     6   FAT16
/dev/sda9         226    250     200791     83  Linux
```Could it be that I'm booting to an old GRUB that lives someplace else?
If it's a GRUB configured for Red Hat, then it would be looking for a "grub.conf" instead of a "menu.lst."

Hmm. If the new Stage 1 never made it to the MBR, that would explain a LOT!

---

### Post by lidex on 2010-02-10
If you run grub from the LiveCD you may be using a different version than what is on the HDD, which may have been upgraded at some point.

---

### Post by hbquikcomjamesl on 2010-02-10
> **lidex said:**
> If you run grub from the LiveCD you may be using a different version than what is on the HDD, which may have been upgraded at some point.Or, as I just said, what came with Ubuntu never made it into the MBR.

---

### Post by presence1960 on 2010-02-10
Instead of getting asked a ton of questions to which you may or may not be so sure of the answers, we need a way to see what you have on your machine. Do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by hbquikcomjamesl on 2010-02-11
Make that DEFINITE! The new GRUB never made it into the MBR; it thinks it's still Red Hat 8!

I simply copied menu.lst to grub.conf, and the GRUB boot menu came up just fine.

Now following Catlett's procedure, as per Lidex's link. Might even have time to put in a background screen.

---

