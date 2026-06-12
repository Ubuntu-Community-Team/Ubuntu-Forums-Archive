---
title: "USB external drive mounting"
date: 2017-12-09
forum: Installation &amp; Upgrades
---

### Post by philpionus on 2017-12-09
Hello,

I recently built a new computer and I kept my RAID USB external enclosure with 4 drives.
To automount it, I have this line in fstab
/dev/md0 /media/user/More_space ext3 rw,auto,user,exec 0 0

On the previous computer (ubuntu gnome 14.04), I used to get a prompt during the boot that could allow me to skip the mounting if the drive was not present. That was great and acheived from the same line in fstab 
Now, with 16.04, I do not get that prompt and it seems that, sometimes, Ubuntu do not ping the drive, and therefore, it hangs on startup, because the friveis not found.
Do I need change any option in my fstab line.

I started suspected the drive, because when I installed minidlna, it was not possible to build the library. It came empty with no error. sudo minidlna -R retuned nothing. 
I tried to "stimulate" the drive by connecting to the minidlna server with a client (indicating no music). Then, if I issue a 
sudo minidlna -R
I get
minidlna.c:624: error: Media directory "A,/media/user/More_space/Music" not accessible [Input/output error]
and if I try now to access the drive in nautilus, I can't and get this error:
This location could not be displayed:
Sorry, could not display all the contents of “More_space”: Error when getting information for file '/media/user/More_space/Development': Input/output error

Any help will appreciated.

---

