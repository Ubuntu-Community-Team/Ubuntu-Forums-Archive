---
title: "Upgraded, external hdd problem"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by motorcity909 on 2010-06-09
Hi all

Finally upgraded to 10.04 this morning.  

All seems fine except I have a 500gb external hard-drive which is mounted as /media/Music and Backups_.  

A while ago though I had tried to get it mounted as /media/external and that folder has remained (empty) within the /media folder and hasn't been an issue.

Now though when the computer starts up I get a screen advising me that "the disk drive for /media/external is not ready yet or not present".  See screengrab1 attached.

I can then press S to skip the mounting and the computer boots up fine.  

If I press M for recovery I get screengrab2 as attached but not knowing what (if anything) to do there I simply come out of it, press S and on we go.

I've removed the /media/external folder but the message is still there.  Any ideas on how to get rid of this?

Thanks
Dave

PS - apologies for quality of screengrabs, taken with my mobile phone.

---

### Post by darkod on 2010-06-09
You can check in /etc/fstab if there is an entry for /media/external that it looks for on each boot. Doesn't matter if the folder is empty or now deleted.

If there is such entry, delete that line, BUT BE VERY CAREFUL WHAT YOU DELETE!!!

In /etc/fstab there are also the entries for mounting /, swap, etc. Deleting the wrong thing can make ubuntu unbootable.

But if you pay attention it's not as bad as it sounds, I just had to warn you. :)

My favorite program for editing/looking at files is gedit, you can try:

gksudo gedit /etc/fstab

PS. If in doubt, make a screenshot with /etc/fstab opened in gedit and post it.

---

### Post by motorcity909 on 2010-06-09
Wow, thanks for the super-speed reply.

As suggested, I've attached a screengrab of the fstab file.

I'm guessing it's that last line, highlighted, that I should delete?

(I'll make a copy of the file first)

---

### Post by darkod on 2010-06-09
It sounds right. The lines starting with # are ignored, just for comments.

Then the first and second UUID lines are / and swap, and then cdrom and floppy.

It should be safe to delete the last line, save and close the file, and reboot.

I'm not sure if fstab is one of those files, sometimes in some files there needs to be empty line at bottom, at the end. If there is empty line existing now after the one you highlighted, then again leave empty line at the end, just in case. I hope that made sense. :)

PS. In fact you can comment out that /media/external line just by putting # at front. No need to delete anything. Might be better solution.

---

### Post by motorcity909 on 2010-06-09
Hey darkod, thank you so much for your help. 

As suggested I simply commented out that last line, saved fstab and rebooted.  No error screen, just a straight bootup to my desktop.

Thanks again, especially for the speed of your replies.

Dave :p

---

