---
title: "locked me out with a corrupt sudoers file"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by phibuntu on 2006-03-07
Hello

I have made a terrible mistake. I knew, that I had this problem before :( 
(And making the same error twice, that's what makes it terrible.)

I changed the sudoers file, but unfortunately I forgott to use the "visudo" command. (Under SuSE this was no problem, because I could always login as superuser and copy the original /etc/sudosers - File back on place.)

Now I am here with a sudoers File containing a syntax error.
All commands (like "sudo bahs", "sudo ...") fail, because sudo uses a clean sudoes file. 

:confused: 
For the Moment I am locked out: To fix the sudoers-File, I have to be root. To get root, I need (I think there is no other way) "sudo bash".  And finally to call "sudo bash", I need a proper sudoes file.

Any Idea?

---

### Post by colo on 2006-03-07
Reboot your machine, and press "Enter" to access GRUB's boot-menu. Select the Ubuntu-entry in question, and press "E". Select the line starting with "kernel", and press "E" once more. Navigate to the end of the line using the arrow keys, and append
```
 init=/bin/bash
```
to it. Press "Enter" to apply your changes (this does not modify any files at all, the changes you make are not permanent and discarded once you exit GRUB). Press "B" to boot.

You'll end up in a very limited environment with bash running under UID 0. Remount your root-partition read/writeable (mount -o remount,rw /), make the needed changes to your "/etc/sudoers", remount your root-partition read-only (mount -o remount,ro /), and cleanly reboot your box.

---

### Post by phibuntu on 2006-03-07
thanks colo for your prompt and helpful answer :-D
It worked perfectly as you mentioned.

---

### Post by awilki01 on 2008-06-07
This procedure did not work for me on Gutsy (7.10).  I simply chose the recovery option in the GRUB boot menu which gave me root access.  From there, I simply did the "visudo /etc/sudoers".  I then restarted and everything was fine.

I hope this helps someone else.  I was in panic mode....

---

