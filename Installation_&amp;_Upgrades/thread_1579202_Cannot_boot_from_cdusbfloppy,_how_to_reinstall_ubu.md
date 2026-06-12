---
title: "Cannot boot from cd/usb/floppy, how to reinstall ubuntu?"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by Baash on 2010-09-21
My computer doesn't support booting from a cd or a usb stick. I managed to install ubuntu (10.04) by using the utility program that came with the live cd. With it I was able to boot from cd and use the live cd. However, there still seems to be some leftover files of windows in the hard drive where I installed ubuntu. 

So my question is, how can I reinstall ubuntu so that it will format the whole drive. Is there perhaps a similar utility program for ubuntu that lets me boot from a live cd or can I do the reinstallation just using the already installed ubuntu?

Thanks in advance for any help.

-Baash

---

### Post by scandido on 2010-09-21
I think most computers can boot from CD or USB stick. Do you know for a fact that you have some special hardware that can't boot from anything other than the hard drive (very unlikely for a standard personal computer), or perhaps can booting from a CD be enabled. 

Certainly its very possible that the hard drive is above the CD drive in the boot order, so it would appear as though one could not boot off of a CD. This can be switched fairly easily.

---

### Post by Baash on 2010-09-21
Yeah, sorry forgot to mention that I have set the cd-rom to be first one to boot. I even tried to disable all the hard drives but it still didn't boot from cd. I can't say for sure that it is absolutely impossible to boot from a cd with my computer but it would certainly seem so.

---

### Post by scandido on 2010-09-21
Okay, just thought that might be a possibility. Sorry, but I don't know more regarding how to boot of the CD if your BIOS cannot do it.

---

### Post by Baash on 2010-09-21
Thanks for the effort anyway. :)

---

### Post by Chuck Ishman on 2010-09-21
I have been having the SAME problem for 2 weeks now. I somehow managed to get Ubuntu installed (after about 10 different attempts, and from several ISO burns) and I only discovered that it had installed when I turned on the machine to check the time and low and behold it opened to a dual boot menu, what a shocker! But from then on I have not been able to do the complete install, reformat the hard drive, and remove WinXp altogether. I cannot boot from the CDR, but I can boot from the 3.5 floppy boot disk that I made to verify that I could at least boot up from the floppy if I needed to, however, even after booting in DOS I can not get the machine to locate the HD and access a file list. It's like it's (HD) not even there. We have checked the hardware and the IDE cables and everything checks out. At worse I may need a new CDR. But what about Internet download options? I seem to have no problems at all accessing the Internet, but I can't seem to find an option to do a full Ubuntu install over the net. Is there an option to do this? If not, why not? Is there no way to download the ISO directly from the net to my HD and then open the ISO directly from my HD. You can imagine that after 2 weeks of banging my head against Ubuntu and getting nowhere fast this is getting very tiresome. So if anyone can help me get past this sticking point I would greatly appreciate it.

---

### Post by Chuck Ishman on 2010-09-21
This might also be of some help: I am working with a Dell Detention 3000, 40GB HD, CD-ROM, 3.5 Floppy, 256 RAM. Also, I am no longer able to access WinXp [which is not a big deal as I planned to get rid of that anyway] which allowed me the ability to play a music CD in the CDR using Windows Media Player, so as far as I can tell the problem is not with the CDR but I hope to be swapping that out soon to confirm the possibility that it may or may not be the problem.
 
In any regard, an Internet download option would be a benefit, don't you agree?

---

### Post by Skaperen on 2010-09-21
Virtually all desktop/server computers can boot from some media.  In older computers, that could be floppy-only.  Modern ones can boot at least one of ATA CD/DVD or USB CD/DVD or USB hard drive.

Now, if some hardware is broken in a particular computer instances, that's a different issue.  My brother's HP laptop has a broken internal CD/DVD interface, so the CD/DVD drive is completely non-functional.  The BIOS does not know how to read CD/DVD via USB.  But at least it can boot from USB hard drive.  So Ubuntu on a USB memory stick was a success (still haven't figured out how to get XP back on it).

There should be some way to boot something, even if it is a hard drive hanging out.  USB is likely to have some success with computers not more than 5 years old.

---

