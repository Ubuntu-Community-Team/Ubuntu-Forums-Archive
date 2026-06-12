---
title: "How to get to a &quot;fresh&quot; system for install success?"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by mpietrek on 2011-07-12
I've been struggling with this for a few days now, and have searched extensively on the web for answers. So now I'm asking here.
 
I have a somewhat old box that I want to install 11.04 on for experimentation. Eventually I'll want to run server and LVM, but for now I'm just going for simple. The box is an AMD 4800+ with 3 SATA hard drives. It previously ran Windows, but I've made every effort to blow all HD contents away and start fresh.
 
The big picture problem is that I can't reliably get the system to boot from the SATA drives. After my first install of the 64-bit 11.04 from CD, it installed OK and booted fine. I then subsequently reinstalled the next day and the troubles began.
 
I've been booting into the "trial mode" from CD, then attempting to reinstall from there. After getting all the way through the setup, it gets to the grub install. It says that it can't install grub. It then offered to install it on the other /SD'x' devices (/SDA, /SDC, etc...) but failed to install grub there as well.
 
Thinking there may have been leftover state from a previous install, I've tried blowing away all the contents of the 3 hard drives. However, I can't do that either. Running the "disk editor" from within the "trial" mode, any attempt to erase a partition is met with a failure, with the error message "daemon is inhibited".
 
So the two big questions I have are:
 
1) Why is the grub install failing, and how can I deal with it?
 
2) Is there some expectation of what the drives look like prior to an install? And if so, how go I get them into that state? I'm lost on how to "uninhibit the daemon"
 
If it's helpful, I grabbed the relevant section of the log file that has what looks like more detailed errors from the grub install.
 
Thanks much,
 
Matt

---

### Post by Luke M on 2011-07-12
My code is in a tangle, I don't know what to do...er, sorry. :-)

I had a funky reinstall problem too - probably a different one - where the install crapped out if there was a linux partition in an unvalidated state (from a previous hard reset). Anyway....I would think that zeroing out the MBR should be sufficient to get a clean install. Something like this:

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

Verify success with:

sudo fdisk -l

---

### Post by oldfred on 2011-07-13
It looks like you are trying to install grub2's boot loader to partitions which it does not like and will not work without an install to the MBR of the drive you boot from in BIOS. I always suggest you boot from the same drive as the install. 
> 
Installing grub on '/dev/sdc1'

To see what is where (anyone with multiple drives and/or multiple installs should use this themselves to know what is where):
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

