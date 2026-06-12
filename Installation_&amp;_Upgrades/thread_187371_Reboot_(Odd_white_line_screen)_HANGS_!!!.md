---
title: "Reboot (Odd white line screen) HANGS !!!"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by zpro on 2006-06-02
Go to logout and reboot in 6.06, it goes to a white line off shade screen,
and just hangs.. NOTHING, no text, nothing.. have to do a hard reboot my Mac.

This is a virgin install from the .iso dvd disk.
so, what going on with this.. I fix the video display resolution issue,
now this problem got me stump.

](*,)

---

### Post by rumli on 2006-06-02
Do you have a FAT32 partition, by any chance?

My system was also hanging whenever I tried to reboot/shutdown.  The problem seemed to disappear once I commented out the line that mounted the FAT32 partition in my /etc/fstab file.

---

### Post by zpro on 2006-06-02
[QUOTE=rumli]Do you have a FAT32 partition, by any chance?

My system was also hanging whenever I tried to reboot/shutdown.  The problem seemed to disappear once I commented out the line that mounted the FAT32 partition in my /etc/fstab file.[/QUOTE]


The only FAT32 partition is the external usb drive
Why you ask?

---

### Post by zpro on 2006-06-03
[bump] again

---

### Post by rumli on 2006-06-03
The reason I asked was that I was having the same problem (hang on shutdown), and found that when I stopped automounting the FAT32 partitioin (by removing the appropriate line containing "vfat" from /etc/fstab), the problem seemed to go away.  I'm not sure whether this was the cause of the problem, or whether it was just coincidence.

Try the following:

sudo gedit /etc/fstab

Then comment out the line containing "vfat", by inserted a "#" character at the start of the line.
Then type:

sudo mount -a

Then reboot.  After rebooting, try shutting down.
If the shutdown problem still persists, then change things back to the way they were by editing /etc/fstab again and uncommenting the line.  That is, type "sudo gedit /etc/fstab" and remove the "#" that you added earlier.

---

### Post by zpro on 2006-06-03
[QUOTE=rumli]The reason I asked was that I was having the same problem (hang on shutdown), and found that when I stopped automounting the FAT32 partitioin (by removing the appropriate line containing "vfat" from /etc/fstab), the problem seemed to go away.  I'm not sure whether this was the cause of the problem, or whether it was just coincidence.

Try the following:

sudo gedit /etc/fstab

Then comment out the line containing "vfat", by inserted a "#" character at the start of the line.
Then type:

sudo mount -a

Then reboot.  After rebooting, try shutting down.
If the shutdown problem still persists, then change things back to the way they were by editing /etc/fstab again and uncommenting the line.  That is, type "sudo gedit /etc/fstab" and remove the "#" that you added earlier.[/QUOTE]


That would be great, but, I don't have any vfat in th fstab file,
the fat32 drive is a usb device (external hard drive ).

Sorry.
:-|

---

