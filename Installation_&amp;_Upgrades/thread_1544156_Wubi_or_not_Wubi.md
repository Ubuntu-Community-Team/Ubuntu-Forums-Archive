---
title: "Wubi or not Wubi?"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by fleamour on 2010-08-02
I downloaded Ubuntu Lynx image, hash checks out.  Then burned it & tried installing within Win7 itself.  I get a Ubuntu option in boot menu but it returns this error:
> Try (hd0,0): NTFS5 No wubildr
Try (hd0,1): NTFS5
I have tried installing, uninstalling, reinstalling & re burning image.

What gives?  I have two soft NTFS partitions on C:, XP & 7, and a data drive D:.

---

### Post by lechien73 on 2010-08-02
If you leave this message on the screen, does it boot after a minute or so? If it does, then you could have the same problem as described in this post: [http://uri.tl/o](http://uri.tl/o)

and solved in post #33

---

### Post by fleamour on 2010-08-02
It seems to hang indefinitely, but will give it five minutes or so, worth a shot.

---

### Post by fleamour on 2010-08-02
Maybe Ubuntu does not like Bitlocker?

---

### Post by lechien73 on 2010-08-02
Ah - that would explain it :)

There are several posts on these forums relating to Wubi and Bitlocker. One workaround posted from January this year is here: [http://uri.tl/p](http://uri.tl/p)

---

### Post by fleamour on 2010-08-02
U cant have it all aye?  MS should have better interoperability.  Dream on.

If I hard partition & install Ubuntu on a dedicated third disk (storage is cheap) where will grub reside/would that work?

---

### Post by lechien73 on 2010-08-02
I would install Grub to the MBR of the third disk. Then, using the techniques and principles we were discussing at [this post here]("http://uri.tl/q"), I would create a copy of the boot sector from the third disk, and use bcdedit to add the option for Linux to the Windows boot menu.

Alternatively, if your BIOS gives you the option to press, for example, F12 at boot to select your boot device, then you don't have to do anything - just select your Windows or Linux disk.

If you want to go with the first suggestion of adding Grub to Vista's Boot Manager, then let me know if you need more details :)

---

### Post by fleamour on 2010-08-02
F11 in my BIOS, how cool is that!  So install grub to MBR of third disk?  Lovin' it, now if only I had some money...

---

### Post by lechien73 on 2010-08-02
Yes - that should do it. Grub on the MBR of the third disk and choose your preferred boot medium from the BIOS menu :)

---

### Post by fleamour on 2010-08-02
Interesting blog by the way, though you really need a favicon for your site for when it gets bookmarked.

Sort it!

;)

---

### Post by lechien73 on 2010-08-02
Thanks for the compliment and that's a very good point about the favicon :) I've added one now. Just didn't expect anyone to actually bookmark it, I guess ;)

---

### Post by fleamour on 2010-08-06
I've seen your blog entry for hacking a grub entry into NTLDR, may try it, but will follow your earlier suggestion of installing Ubuntu to 2ndry HDD along with GRUB on 2ndry HDDs MBR & then using F11 as device boot selector.

One question, I cannot recall an option in Ubuntu setup for choosing which disk's MBR to install GRUB to.  

So how do I go about it exactly?

Thanks.

---

### Post by fleamour on 2010-08-09
Right!

Had a nose round Ubuntu installer & the very last advanced option before committing to install asks *where* you want to install Linux bootloader.

Super nice!!!

---

### Post by oldfred on 2010-08-09
Picture from a Karmic install but it is the same in Lucid. I missed it on my first install of lucid and it just installed to sda, even though my BIOS default is sdc.

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

---

### Post by fleamour on 2010-08-09
If you do install GRUB over 7's bootloader, like I did, 7 will not boot.

To fix, boot with your recovery disc you created earlier (you did didn't you? ;) ) or original 7 install disc, & navigate to command prompt.

Since I had XP & 7 in a dual booting setup, I typed in these commands below, and press enter after each one:

```
bootrec /FixMbr
bootrec /FixBoot
bootrec /RebuildBcd
```
Exit the command prompt and restart the computer.  At this point, Windows 7 should boot up as before.

---

