---
title: "system restore on 9.10"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by kanolsen on 2009-12-22
I upgraded to 9.10, but since then I haven't been able to log in, I only get a logon box, but nothing happen when I log in.

I found someone mention on the net about system restore, and wonder how I restore the computer back to a working system.

Let me know If you need any more information to help out. I am new to this so can't find myself around much alone.

Thanks in advance
Kanolsen

---

### Post by lemming465 on 2009-12-24
Regretably, your video chip support probably regressed between 9.04 and 9.10.  If you have access to a live desktop CD, it would be interesting to know how well that works. (I like to try live desktop CD's before doing upgrades, just in case of regressions.)

If it does, write back for directions on how to use chroot to try and fix things further.  If you are comfortable at the command line, booting in "recovery mode" (single user) might help.  It might be possible to switch to the VESA video driver, but we'll need advice from someone else who knows more about X than I do.

Unfortunately, there is no downgrade method corresponding to upgrades; if you need to go back to 9.04 you'd have to reinstall.  If you have data you can't easily back up externally and restore later, write back for directions on doing an overlay reinstall. (The basic idea is to boot a live CD and remove system directories without removing data directories like your home directory.)

---

### Post by kanolsen on 2009-12-24
Thanks, I tried 9.10 live cd, and it worked perfectly. I have a Shuttle computer with onboard graphics. 

I have copied everything from the Home folder so no damage can be done there, but I really do not like the thought of configuring the computer again in all the different files to get it back to as it were - or else I could reinstall. But since I just have to follow manuals it will take days before I'm finished setting it up as I had it before 9.10. 
 
So if anybody can help out with how I get the computer back to working order I would be more than  thankful. I guess it might be something with X - hopefully an relatively easy solution. 

Thanks Lemming465 for getting back to me.

Kanolsen

---

### Post by lemming465 on 2009-12-28
One thing you can try from the live CD as a possible repair is to update packages and reconfigure X.  Boot the live CD, open a terminal window, and try something like:```
sudo -i
aptitude clean
aptitude update
aptitude full-upgrade -f
dpkg-reconfigure xserver-xorg
```
That may or may not fix things, but it shouldn't make them any worse, and won't damage your configured applications nor data.

---

### Post by kanolsen on 2009-12-28
thanks, tried the tip above, but the same thing happened when i finished it, and restarted it. 

Now, before it goes black with the swirvling wheel of wait, I got an error message with something that Gnome power management failed, but that shouldn't have anything to do with this should it?

So far, no luck.

Kanolsen

---

### Post by lemming465 on 2009-12-29
Oops, the boot the live CD direction were missing the chroot step.  Try again with:```
sudo -i
mkdir /media/root
mount /dev/sda3 /media/root # use whatever your root partition is if it's not sda3
cd /media/root
for f in sys dev proc ; do mount -o bind /$f $f; done
chroot .
aptitude clean
aptitude update
aptitude full-upgrade -f
dpkg-reconfigure xserver-xorg
```Without the chroot step it just patches the live memory desktop, not the hard disk.  My bad, sorry.

---

### Post by kanolsen on 2009-12-29
thanks for trying to help, I tried twice what you wrote, but got the same error message both times and on restart nothing had changed, it still goes black after the Ubuntu logo shows. 

This is the error message I got:
root@ubuntu:/# aptitude full-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "nb_NO.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

root@ubuntu:/# dpkg-reconfigure xserver-xorg
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "nb_NO.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
root@ubuntu:/# 


Thank you for your time.
kanolsen

---

### Post by lemming465 on 2009-12-31
I don't think the locale warnings are particularly serious.  It's a little odd that the live CD video works when the installed system video doesn't.  You'd have to compare the /var/log/Xorg.0.log files from booting both ways to see if they were trying to use the same drivers or not.

At this point, you have 3 likely directions you could go.  If older live CD's, say 9.04, work OK, you could reinstall with an older version (there are no easy downgrades corresponding to upgrades, alas).  If newer CD's, say 10.04 alpha 1 work OK, you could upgrade to next year's Lucid Lynx prematurely (via *sudo update-manager -d*).  That will be less premature around Alpha 3 or Alpha 4 or Beta 1, but those are months off yet.  Or maybe you could try forcing use of a different video driver by creating /etc/X11/Xorg.conf containing something like```

        Section "Device"
                Identifier      "Builtin Default vesa Device 0"
                Driver  "vesa"
        EndSection
```
I'm not an expert on X, so I'm not completely sure about the 3rd option.

---

### Post by t54 on 2010-01-04
Re updating kernel of unbootable karmic install from live CD

[http://ubuntuforums.org/showthread.php?p=8611984#post8611984](http://ubuntuforums.org/showthread.php?p=8611984#post8611984)

 Re: cannot boot into karmic after pkg update via synaptic
UPDATE:

   1. Have obtained a karmic live CD and run it.
   2. Also have mounted and backed up home folder located on unbootable karmic HD install.
   3. This appears to not be a GRUB problem per se. GRUB, which I have established is the legacy version, appears but after a selection of whichever version of karmic is made freezes up with the error msgs first reported at the URL above.
   4. Trying to update the karmic install within live CD has not been successful, even though I have used root to access root in HD install folder and run synaptic, aptitude, as upgrade, update, etc.

---

### Post by kanolsen on 2010-01-12
I tried looking at the /var/log/Xorg.0.log files but couldn't see anything wrong with them. 

I realised the best was to try to find all the files I have modified  and copy them and reinstall 9.10 (which worked fine), and now I copy the modified files back as it were. The only problem was with /etc/fstab which doesn't look at all as it did on my server now everything is written with UUID and not just the name. But that's another thread.

Thanks for all help.

Kanolsen

---

