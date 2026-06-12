---
title: "My Ubuntu/XBMC install is borked, how do I remove everything and start from scratch?"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by jensbodal on 2011-06-15
I have internet access and a semi-working Ubuntu install via command line / SSH.  XBMC has been running fine until I did an update, then the xorg.conf got ##$@ed and I've spent the last 4 hours googling and trying to fix it.  I'd love to just reinstall, but I don't have a blank CD or a USB Drive to use. 

Is there anyways I can just erase everything and start from scratch?  AFAIK it's not possible to run the Ubuntu Minimal install from anywhere but a CD-ROM or USB Stick.

This PC also has access to a Windows directory so I guess I could use WUBI, but would like to avoid that if possible.

Please let me know if you have any advise, thanks.

---

### Post by travlemon on 2011-06-15
> **jensbodal said:**
> I have internet access and a semi-working Ubuntu install via command line / SSH.  XBMC has been running fine until I did an update, then the xorg.conf got ##$@ed and I've spent the last 4 hours googling and trying to fix it.  I'd love to just reinstall, but I don't have a blank CD or a USB Drive to use. 

Is there anyways I can just erase everything and start from scratch?  AFAIK it's not possible to run the Ubuntu Minimal install from anywhere but a CD-ROM or USB Stick.

This PC also has access to a Windows directory so I guess I could use WUBI, but would like to avoid that if possible.

Please let me know if you have any advise, thanks.

If your xorg.conf is all messed up, there should be backup copies on the hard drive, automatically created by the system.

If I go into my /etc/X11 folder, I have at least 1 file called xorg.conf.backup (though I recall maybe even having more in the past)

You can try simply renaming your current xorg.conf to something like xorg.conf.old.  Or what I like to do, since .old might be too common, is xorg.conf.del.  Then rename xorg.conf.backup to xorg.conf. 

If you're unfamiliar how to do this, I can try to help.  I'm not super savvy, but maybe enough to help you fix it.  

**Try this:**
Try booting your system, when it's gone as far as it can go, press CTRL + ALT + F1 on your keyboard.  This should give you a basic command based login screen.

Login as root.  Then, type this command to get into the folder that contains xorg.conf:
```
cd /etc/X11
```
and press enter.

Just to check, run the dir command to see if the xorg.conf.backup file is in the X11 directory. If so (there should definitely be a backup file), do the following steps:

Then rename xorg.conf with this command:
```
mv xorg.conf xorg.conf.old
```
and press enter

Then rename the backup to your normal xorg.conf with this command:
```
mv xorg.conf.backup xorg.conf
```
and press enter

Hope this helps!

---

### Post by jensbodal on 2011-06-15
Thanks for the response.

I've tried that via SSH (Ubuntu login screen is frozen) and still won't work.  Pretty sure I've completely messed things up and need to start over

---

### Post by mörgæs on 2011-06-15
There are some ideas here
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
but vy far the easiest solution is to get a CD or a USB drive.

---

### Post by jensbodal on 2011-06-15
Great -- thank you for the link.

I'm sure it's easier with a USB stick or CD-ROM, but I love learning something new so this should be a pretty good challenge for me to figure out this weekend.  Worst comes to worse I'll just find a thumb drive.

---

### Post by jp_couch on 2011-08-17
Hey All,

I recently installed XBMC on my Linux Mint 10 gnome edition. After install my X server would error  on boot. I could drop to console and startx manually with success.

I stumbled around the forums and found the following link.
[http://askubuntu.com/questions/10664/how-do-i-fix-ubuntu-is-running-in-low-graphics-mode](http://askubuntu.com/questions/10664/how-do-i-fix-ubuntu-is-running-in-low-graphics-mode)

apparently the installing of xbmc removed the gdm somehow and simply typing

sudo apt-get install gdm

solved all my problems.

i hope this saves sombebody a headache.

---

