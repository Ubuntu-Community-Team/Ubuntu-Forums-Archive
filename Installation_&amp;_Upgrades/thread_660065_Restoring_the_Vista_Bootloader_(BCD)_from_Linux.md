---
title: "Restoring the Vista Bootloader (BCD) from Linux?"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by codesplice on 2008-01-06
Hey all,
Just picked up an hp dv6700 notebook (2.2ghz intel core 2 duo,  3gb ram, 256mb nvidia geforce 8400m gs), and I love it.  Came preinstalled with Vista Ultimate - which is a blessing and a curse, it seems.    Following the trend of all other computer manufacturers, HP neglected to include a recovery disc with the new computer.  Instead, I'm giving the HP_RECOVERY partition on the harddrive.  A nice gesture.... but when I went to burn some recovery discs, the utility gets halfway through the procedure and then exits, acting like I had canceled the process (even though the Cancel button is grayed out...).  I contacted HP and they are sending me a set of recovery discs.... in the meantime, I just HAD to play around.  

I deleted the (useless) recovery partition (13.5GB) and used that to install Linux Mint 3.1 (basically a prettier Feisty).  Had to do all the fun juggling to get Linux to play nice alongside Vista, and everything was good for a time.  Which makes me uneasy - I've got to be breaking and fixing things :p

So somewhere in my experimentations, I seem to have deleted the Vista bootloader.  Completely.  When launching the Windows Vista option from GRUB, I get an error about "NTLDR not found".  So it's looking for NTLDR (the previous Windows bootloader) rather than BCD.  

If I could boot into Vista, I could use EasyBCD to repair the bootloader.  If I had a Vista boot CD, I could use that to fix it.  (I even tried a legitimate Vista Business CD that I had lying around, and it told me that "this version of windows recovery is not compatible with the version of windows you're trying to recover", or something to that effect.  

I've tried using wine to run EasyBCD from the Vista partition, but had no luck :(  Tried installing it via wine, and also no luck (whines about not finding a few *.dlls).  I've tried pretty much everything I can think of - I'm even torrenting a copy of Vista Ultimate to see if that disc will let me repair my ****.

Any other ideas?  I'm getting kinda desperate (and too impatient to wait the few days before HP's discs will get here).

Thanks :)

---

### Post by digital_exhaust on 2008-01-06
Do you have an XP install cd? If so, boot from that disc, and when prompted, select the option to "save" the partition that Vista is installed on. I don't know why this works, but it does. 

Other than that, I'm not sure what to tell you.... borked Vista bootloaders are no fun, and can be a real pain to fix... 

Good luck!

---

### Post by codesplice on 2008-01-06
I've got an OEM Dell recovery CD... and I think I've tried it before.  IIRC, I got a message about not finding a recoverable OS or something to that effect.  I'll try that again in a minute to be sure though - thanks :)

---

### Post by Steve1961 on 2008-01-06
The makers of EasyBCD have produced a disk that you can download to repair the vista bootloader even if you don't have an installation disk.  looks useful, and hope it helps:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by codesplice on 2008-01-06
> **Steve1961 said:**
> The makers of EasyBCD have produced a disk that you can download to repair the vista bootloader even if you don't have an installation disk.  looks useful, and hope it helps:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

AWESOME.  looks quite promising - and it's exactly what I had been hoping to find.

Now, just to download it.  Whee!

Thanks!

---

### Post by Steve1961 on 2008-01-06
Let us know how you get on.

---

### Post by codesplice on 2008-01-06
Close, but no cigar.

Got the same message I received when using the Business Edition disc.  "This version of Windows Recovery is not compatible with the version of Windows you are trying to recover.  Try using a compatible version of Windows Recovery".

:-/

Of course, the first time it detected that the installation was damaged and asked if I'd like it to automatically try to repair the boot properties.... clicked yes, it rebooted, and still got the "NTLDR Missing" message when trying to boot Vista from GRUB.

Thanks anyway.

---

### Post by logos34 on 2008-01-06
codesplice,

Is vista on the second partition?  Maybe the grub windows entry is pointing to wrong one--should be (hd0,1).  On vista boot ption in grub hit 'e' and check the 'root' line

---

### Post by codesplice on 2008-01-06
> **logos34 said:**
> codesplice,

Is vista on the second partition?  Maybe the grub windows entry is pointing to wrong one--should be (hd0,1).  On vista boot ption in grub hit 'e' and check the 'root' line

Vista is on the first partition of the first (only) harddrive - (hd0,0).  GRUB's menu.lst entry concerning Vista:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Thanks though :)

---

### Post by logos34 on 2008-01-06
oh, I was thinking the recovery partition might have been first (usually is)

---

### Post by logos34 on 2008-01-06
why don't you try what digital_exhaust suggested, or do you have an XP disc?

There's also [Super Grub Disk]("http://supergrub.forjamari.linex.org/")--which is reportedly able to restore the windows bootloader (and no more) so you can boot vista. I have yet to try it so I don't know.

---

### Post by codesplice on 2008-01-06
Still haven't found that XP disc :-/  I'll definitely give that a shot once I do though.

And I've tried Super GRUB Disc - it wasn't able to restore BCD (or else I wasn't doing it right).

---

### Post by logos34 on 2008-01-06
The reason I suggested SGD was [this post]("http://ubuntuforums.org/showpost.php?p=4003118&postcount=10"). But either it's wrong or there's some special trick to using it.

---

### Post by codesplice on 2008-01-06
eh, I'm inclined to think that the Windows MBR is fine - as it IS trying to load a bootloader, just not the right one.  And if I repair the MBR using a tool for XP.... won't that also make it look for the XP bootloader rather than the Vista one?

or I could be way off track... I'll give it a shot :p

I can always restore GRUB via the Mint LiveCD, so I'm not gonna be worse off than I am now :p

---

### Post by logos34 on 2008-01-06
> **codesplice said:**
> eh, I'm inclined to think that the Windows MBR is fine - as it IS trying to load a bootloader, just not the right one.  And if I repair the MBR using a tool for XP.... won't that also make it look for the XP bootloader rather than the Vista one?

or I could be way off track... I'll give it a shot :p

I can always restore GRUB via the Mint LiveCD, so I'm not gonna be worse off than I am now :p

well, there's the MBR--the first 512 bytes of the disk--and then there's the bootsector of the windows partition, where vista has its boot manager and boot files.  They're two separate things.  As it is, Grub has overwritten the windows bootloader on the MBR.  Grub** chainloads **windows (vista or XP).  

[edit] [mint's on the 13 gb space of former recov. part.  got it.]

---

### Post by codesplice on 2008-01-06
Little juicy tidbit I forgot to mention (and didn't even think about until someone mentioned it on the EasyBCD boards): I've got Vista Ultimate 64-bit.  Both the EasyBCD Vista Recovery disc and the Vista Business edition I had tried were from the x86 version of Vista.  

Forgive my ignorance - I'm extremely new to the whole 64-bit ballgame :-D

Anyone know of a 64-bit Vista Recovery ISO anywhere? :-D

---

### Post by Computer Guru on 2008-01-07
Yeah, thanks for the heads-up on this issue; we hope to get an x64 recovery disc image up ASAP.

Also, as I posted in the thread in the NST forums, you can use this:
[quote=NeoSmart Forums]Get a bootable floppy or USB
Copy \bin\mbrfix.exe from the EasyBCD program file's directory to the bootable disk.
Boot from the disk and type this in at the prompt:

```
mbrfix.exe /drive 0 fixmbr /vista
```[/quote]

---

