---
title: "Just Upgraded and what is this?"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by 2uRcJQ34G1 on 2010-10-14
Hiya,

I just upgraded from 10.04 to 10.10 and while I was upgrading I was asked two or three question regarding GRUB config overwrite or something and something else. In my Ignorance I clicked forced to overwrite instead of leaving those files alone.

**Unfortunately, now whenever I start my computer, the Ubuntu splash screen shows up and then something quickly shows up on the screen and then the screen goes black and then nothing happens. The only way I can actually boot Ubuntu is if I quickly start to press the arrow keys and hope the Ubuntu loads. It loads after a few tries.**

Things I have tried: I reinstalled the GRUB.
Checked for broken packages(none found).
Googled my problem(nothing).

Thanks in advance for your help.

Cheers.

---

### Post by 2uRcJQ34G1 on 2010-10-14
I should also add that I have run the Dell Diagnostics to check my memory and HDD and everything else. All is well. Once I get Ubuntu booted everything runs well too. However, the trouble is actually getting it started.

---

### Post by 2uRcJQ34G1 on 2010-10-14
Is there any way to rebuild the nano and .conf files. I remeber being asked about this during the upgrade.

---

### Post by kansasnoob on 2010-10-14
This sounds more like either a kernel or xorg problem than a grub problem. First of all calm down!

Is Ubuntu the only OS on that machine?

If so try pushing a Shift key just after the System/BIOS screen passes. That should display the grub menu.

You should see you have both a Lucid and Maverick kernel to try and boot. Which works and which doesn't?

---

### Post by 2uRcJQ34G1 on 2010-10-14
Yes, Ubuntu is the only OS on the machine. I do see the GRUB menu but the Lucid is not there only maverick. There is also the memtest and the recovery mode. The recovery mode works fine, and so does the memtest. But the maverick does that splash-screen-and-then-black-screen-no-response thing as I described earlier.

---

### Post by 2uRcJQ34G1 on 2010-10-14
Sorry but my world is in the machine, and the only reason I use linux is because of its reliability. So when something goes wrong all hell breaks loose.

Cheers for helping :).

---

### Post by CharlesA on 2010-10-14
It sounds like xorg is having problems tbh.

Are you able to boot into recovery mode and run fix xorg?

---

### Post by 2uRcJQ34G1 on 2010-10-14
How do I fix xorg and what is tbh. Sorry I am not very fluent with commandline stuff, except the ones I use frequently.

---

### Post by CharlesA on 2010-10-14
tbh = to by honest.

As for fixing xorg, when you boot into recovery mode you should be prompted with what you want to do. There should be an option to fix xorg.

---

### Post by 2uRcJQ34G1 on 2010-10-14
No, I don;t see any fix org option in the menu. Sorry. I can however see the resume boot option which takes me to the command line. Is there any way I can do this manually?

Thanks.

---

### Post by CharlesA on 2010-10-14
Oh, sorry the option is "failsafeX"

---

### Post by 2uRcJQ34G1 on 2010-10-14
I just used the synaptic package manager to reinstall the xorg packages, all that I could find. I am going to try to reboot now.

---

### Post by 2uRcJQ34G1 on 2010-10-14
I can access failsafeX no problem.

---

### Post by CharlesA on 2010-10-14
Did you have any proprietary drivers installed before you did the upgrade?

---

### Post by 2uRcJQ34G1 on 2010-10-14
nope. Ubuntu supports ATI Radeon Cards natively now.

---

### Post by CharlesA on 2010-10-14
Did running failsafeX work?

If not, try booting off a livecd and see if it loads up on.

---

### Post by 2uRcJQ34G1 on 2010-10-14
Yes the failsafeX works, in fact if I do a normal boot and keep pressing the arrow keys or some sort of input, the normal boot works too. But if I don't keep inputting something during boot the splash screen shows up and then the screen goes blank and no response. Afterwhich, I have reboot again and try the arrow thing again.

---

### Post by CharlesA on 2010-10-14
Try editing the normal kernel option and removing "quiet splash" and see if it does the same thing.

Go to the grub menu, hit e to edit and then remove those two options. Then boot.

---

### Post by 2uRcJQ34G1 on 2010-10-14
Tried and no avail. Here is the original text I found in case this helps:
> record  fail
insmod part_msdos
insmod ext2
set root = '(hd0, msdos1)'
search --no-floppy-fs uuid--set 36fe079...(some hex) \58f
linux /boot/vmlinuz-2.6-35-22-generic root=UUID=(some hex)
ro splash vga=769 quiet splash
intrig /boot/intrid.img-2.6.35-22-generic

Just as a note: I have the filesystem as ext4 could the ext2 in the above text be a problem??

Greatly appreciate your help mate :)

---

### Post by CharlesA on 2010-10-14
That's fine. Try this:

Instead of having "vga=769 quiet splash"

Hit 'e' to edit and set "vga=ask" and see if it boots up.

---

### Post by Qvark on 2010-10-15
I kind of have the same problem. The screen dosen't gi black but it's stuck in the splash screen. xorg server log says: 
Fatal server error:
[14.341] no screens found

---

### Post by 2uRcJQ34G1 on 2010-10-15
Hi,
Tried to do the 'vga=ask' and it displays an error saying that this legacy feature is no longer supported.
New Development: I somehow tried to read one of the error messages and it said that-
> .../sd0...has been loaded 20 times and then something about it cannot boot something...(dots mean something there I do not remember)

STRANGE...

If no solutions work, and I do not have the excess time to HOPE that the dang thing works:- I am thinking of simply getting a live cd and reinstalling Ubuntu. Will my data be deleted if I do that?

---

### Post by 2uRcJQ34G1 on 2010-10-15
it also adds in the error that it is now going to force something.

---

### Post by CharlesA on 2010-10-15
You'd lose yer data if you reinstalled, but it would be worth it to wipe the slate clean.

---

### Post by 2uRcJQ34G1 on 2010-10-15
[B]THE VERDICT: I have no clue what the problem was but I am now backing up my data by accessing the FailsafeX session and then doing a clean reinstall.

LESSON LEARNED: When upgrading try not to change the .conf files for the GRUB when prompted for it during the upgrade.

Cheers and many thanks to CharlesA for all his help.[/B]

---

