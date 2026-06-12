---
title: "Repairing Windows (Dual Boot via Ubuntu)"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by Qwertyop on 2010-02-15
OK, maybe the wrong category but may be the right one depending on the solution.

I have a dual boot system Ubuntu 9 + Windows Vista. 
I have a windows Vista recovery CD - a CD drive
I have a 10GB CD with the files of the cd copied on it.

How can I repair windows considering the above? The issue is I do not have a CD drive and have not been able to work out how to make this USB bootable (I know how to boot a USB)? I think running CHKDSK.exe found on the recovery CD will fix the problem (which Ununtu caused). 

Thanks.

BTW: if you're wondering what the problem is I ran a check on the disk using my Dell (uh) utility in one of my partitions which gave me 5 or so addresses that were corrupted or what have you. 

Thanks.

Oh and is there any way to run chkdsk or similar through ubuntu!?

Thanks.

---

### Post by darkod on 2010-02-15
Sorry, I didn't understand, do you have the vista recovery cd files on the hdd or not?
Even if you don't, you should be able to get a vista rescue cd image from here:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Once you have that, you can use a usb stick in the following way:

1. From the ISO image extract just the boot folder.
2. From the boot folder, run the command:
bootsect /nt60 F:

In this command replace F: with the letter of the usb stick. That will write the boot sector to the usb stick.

3. After that extract the whole image onto the stick. Now you have the vista rescue cd but on bootable usb stick.

However, you would need to run all this on a windows computer. I have no idea how to do it from linux.

---

### Post by Qwertyop on 2010-02-15
> **darkod said:**
> Sorry, I didn't understand, do you have the vista recovery cd files on the hdd or not?
Even if you don't, you should be able to get a vista rescue cd image from here:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Once you have that, you can use a usb stick in the following way:

1. From the ISO image extract just the boot folder.
2. From the boot folder, run the command:
bootsect /nt60 F:

In this command replace F: with the letter of the usb stick. That will write the boot sector to the usb stick.

3. After that extract the whole image onto the stick. Now you have the vista rescue cd but on bootable usb stick.

However, you would need to run all this on a windows computer. I have no idea how to do it from linux.
Oh I forgot to mention I am aware of that method but my university blocks all bittorrent traffic via content-type header and I haven't been able to work out how to download it any other way.

---

### Post by darkod on 2010-02-15
> **Qwertyop said:**
> Oh I forgot to mention I am aware of that method but my university blocks all bittorrent traffic via content-type header and I haven't been able to work out how to download it any other way.

Well, can't you just find a computer to use for 5mins with cd drive, and create a usb stick from your vista recovery cd that you said you had? That same process will work from the cd of course, even better.

---

### Post by oldfred on 2010-02-15
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk".

---

### Post by Qwertyop on 2010-02-15
> **oldfred said:**
> sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk".

Tried that before, got this:

[HTML]Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.
[/HTML]And at a previous post one of the files on my CD is damaged in the optical disk and cannot be repaired/copied even with windows XCOPY /C. I don't think it is important, but it is called something along the lines of reinstall and is 2.3 GB.

EDIT: and just to point out I am using the right file in /dev/ for the ntfsp.

---

### Post by Mark Phelps on 2010-02-16
> **Qwertyop said:**
> And at a previous post one of the files on my CD is damaged in the optical disk and cannot be repaired/copied even with windows XCOPY /C. I don't think it is important, but it is called something along the lines of reinstall and is 2.3 GB.

Not good.  That looks like what you have in CD form is a Restore CD -- used only to restore your machine to its original setup -- which will most probably wipe all files from your drive and reformat it.

To repair Vista, you really need the repair CD that darkod linked to in his post.  That's an ISO image that must then be burned to CD, you boot from that CD, and you then run Startup Repair several times (usually 3 times) to repair Vista.

---

