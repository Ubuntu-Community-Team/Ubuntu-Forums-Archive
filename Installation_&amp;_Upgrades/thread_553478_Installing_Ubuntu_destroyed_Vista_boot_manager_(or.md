---
title: "Installing Ubuntu destroyed Vista boot manager (or mbr)"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by dkuhlman on 2007-09-17
I tried to install Ubuntu 7.04 on my Toshiba Satellite laptop.

I tried to follow the instructions here:  file://localhost/home/dkuhlman/a1/Debian_Ubuntu/Docs/windowsdualboot.html

Now, I cannot boot.

I believe that I've destroyed the MBR or the Boot Configuration Database (BCD) used by the Windows Boot Manager.

I have a recovery CD.  But when I run it, it asks me if I want to delete data on my first (Vista) partition.  I believe that the data there is OK.

Is there a way that I can restore my mbr/Boot Manager without deleting my Vista partition?

Dave

---

### Post by Pumalite on 2007-09-17
In your installation CD there must be something similar to XP's Recovery>FIXMBR>FIXBOOT.
Find it.

---

### Post by dkuhlman on 2007-09-18
> **Pumalite said:**
> In your installation CD there must be something similar to XP's Recovery>FIXMBR>FIXBOOT.
Find it.

Much thanks for the guidance here.

That tool (FIXBOOT ?) was on my recovery disk, I believe.  But, I did not know where to find it until you pushed me a bit to probe for it.

Here is what I did:

1. On the first screen after booting from the recovery CD, I selected "other options" (not too sure of the wording) and did **not** select the standard recovery wizard.

2. On the next screen, when it said something like "If you do not see your operating system in the list, then ...", I ignored that, this time.  The reason is that doing so leads you to the second CD.  What you do want to do is click "Next" to get the next screen.

3. On that screen there is an option to fix the MBR.

I believe that the option to fix the MBR is really running the program you told me to go looking for.

By the way, the recovery CD says Toshiba on it, so I do not know whether the above is specific to Toshiba or is just something that Toshiba licensed from Microsoft and re-branded.

And, for a few more notes, just in case it is of help to someone:

I had to install Kubuntu several times before I was able to successfully reboot into it.  I wanted separate partitions for "/" and "/home".  The way I finally got it to work was to make a new **primary** partition for "/" and a new logical partition for "/home" (and also a new logical partition for swap.  And, I still had to try several times before I was able to successfully install GRUB.  What's more, believe it or not, although I was very carefully trying not to install GRUB in the MBR, GRUB still took over the MBR, I believe. 

Sigh.  But, since I can boot both Vista and Linux, I'm not going to try to fix what's not broken.

Now, I'm looking at my Linux Ubuntu/Kubuntu desktop.  Great.

And, I can also boot into MS Vista.  Let's hope that I don't have to do that too often.

Thanks again for the help.

Dave

---

### Post by Pumalite on 2007-09-18
You are welcome. And thank you for posting the solution. Happy Ubuntuing!

---

### Post by bendystraw on 2007-09-18
the same exact thing happened to me, i know how much it sucks =[

---

### Post by Pumalite on 2007-09-18
Be happy! Now you know the solution.

---

### Post by rabidrabbit on 2007-09-18
to do it from the command line in the vista cd type bootrec /fixmbr. That will restore the vista bootloader if you want to get rid of grub.

---

### Post by PmDematagoda on 2007-09-18
But won't the Vista bootloader ignore Ubuntu?

---

### Post by dkuhlman on 2007-09-19
> **PmDematagoda said:**
> But won't the Vista bootloader ignore Ubuntu?

You can use bcdedit.exe or EasyBCD to add Linux to the Windows Vista bootloader.  See the following:

[LIST]
[*][https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[*][http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[*][http://technet.microsoft.com/en-us/windowsvista/aa905126.aspx](http://technet.microsoft.com/en-us/windowsvista/aa905126.aspx)
[/LIST]

Dave

---

### Post by PmDematagoda on 2007-09-21
> **dkuhlman said:**
> You can use bcdedit.exe or EasyBCD to add Linux to the Windows Vista bootloader.  See the following:

[LIST]
[*][https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[*][http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[*][http://technet.microsoft.com/en-us/windowsvista/aa905126.aspx](http://technet.microsoft.com/en-us/windowsvista/aa905126.aspx)
[/LIST]

Dave

Thanks Dave.:)

---

### Post by maybeway36 on 2007-09-21
The MBR reset can also be done with a DOS floppy:
```
fdisk /mbr
```

---

