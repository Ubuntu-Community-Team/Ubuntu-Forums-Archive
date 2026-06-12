---
title: "initramfs  what is that????"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by RamseyT on 2010-06-18
Hi Complete newbie to Ubuntu.

I downloaded the 
ubuntu-8.04-desktop-emc2-aj13-i386.ISO

Burned and Verfied a CD.

I put it in an older Toshiba laptop and set it to boot from the CD. I get the Ubuntu Install screen.

I select "Safe Video" (I also tried "Normal") in the F4 options and select "Install" and "Enter."

A little while later I get "Busy Box 1.1.3..."

and a bare prompt.

(initramfs) 

What do I do next? I typed "Help" as prompted but nothing there helps me.

{edit}
I have since found adding pci=nomsi to the F6 boot options but that did nothing.
The Toshiba does not have a floppy drive, nor does it have a SATA/RAID option in CMOS.
{/edit}
Thanks

Ramsey

---

### Post by RamseyT on 2010-06-18
Please see much more information in this other thread...

[http://ubuntuforums.org/showpost.php?p=9479690&postcount=409](http://ubuntuforums.org/showpost.php?p=9479690&postcount=409)

Ramsey

---

### Post by confused57 on 2010-06-18
Here's an older thread that may help:
[http://ubuntuforums.org/showthread.php?t=501353](http://ubuntuforums.org/showthread.php?t=501353)
see post #6

---

### Post by RamseyT on 2010-06-19
> **confused57 said:**
> Here's an older thread that may help:
[http://ubuntuforums.org/showthread.php?t=501353](http://ubuntuforums.org/showthread.php?t=501353)
see post #6

Hi,

Thanks for that. It has been rattling away for 15 minuts now, reading  from the CD. I will let it have it's way and see where it takes me. Much  more than I have had previous attempts. :)

In posting #7, part 2 where it says...

#sudo mount /dev/hda1 target  (or whatever slie you installed)

What is meant by "(or whatever slie you installed)" ?

I have a basic Toshiba laptop with 1.4G hard drive, CD, 32512K memory  and USB ports but no floppy. I have "installed" nothing.

Ramsey

---

### Post by confused57 on 2010-06-19
> **RamseyT said:**
> Hi,

Thanks for that. It has been rattling away for 15 minuts now, reading  from the CD. I will let it have it's way and see where it takes me. Much  more than I have had previous attempts. :)

In posting #7, part 2 where it says...

#sudo mount /dev/hda1 target  (or whatever slie you installed)

What is meant by "(or whatever slie you installed)" ?

I have a basic Toshiba laptop with 1.4G hard drive, CD, 32512K memory  and USB ports but no floppy. I have "installed" nothing.

Ramsey

I don't know of any linux distro that might run on your laptop, the Ubuntu live cd would require around 512 Mb memory to boot effectively, and you'd probably need at least a 5 Gb hard drive for installation.

---

### Post by RamseyT on 2010-06-19
> **confused57 said:**
> I don't know of any linux distro that might  run on your laptop, the Ubuntu live cd would require around 512 Mb  memory to boot effectively, and you'd probably need at least a 5 Gb hard  drive for installation.

Thanks,

That's probably the issue. It sat for an hour with a  blank screen and flashing cursor doing reads to the CD. I finally turned  it off.

Enough memory looks to be $188 and I will check on whether  I can get a bigger HDD for it. It is going into a workshop to drive a  CNC lathe. I didn't want to spend a lot getting it to work in case the  lathe didn't work as expected.

Using EMC2 seemed the best way to  test it all, I guess it is win98se and mach3 for me. Bummer.

Thanks  for the help. No Linux for me for this year. :(

Ramsey

---

