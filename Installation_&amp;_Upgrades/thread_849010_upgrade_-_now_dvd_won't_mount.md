---
title: "upgrade - now dvd won't mount"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by pikaia on 2008-07-04
Hello.

Just upgraded from Gutsy over the weekend, and for the most part I'm pleased.  However I've noticed some problems.  The most pressing is that no disc media (CD, DVD, data, music, nothing) will mount at all.  For whatever reason after the upgrade it wouldn't at all, then I changed my fstab from udf to auto and then it would right after the reboot, but has since stopped.  I haven't installed or removed any packages.

Another issue is that Kaffeine (my preferred DVD player) throws up an error whenever I try to watch a DVD (it never did this in Gutsy).
"This DVD Video is encrypted. To be able to watch it you will need to install libdvdcss by running from a console: sudo /usr/share/doc/kaffeine/install-css.sh. In some countries it is illegal to install the decryption software without permission from the video copyright holder."  

I ran the shell, but I still get the error. Is this because the DVD isn't mounted?

I also have found it impossible to make Kaffeine the default player and autoplay my DVDs.  I followed the walk through in this thread: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

But no luck.  Just to clarify all worked well in Gutsy, and still works well on the XP side of my dual boot.  So its Not the hardware.

I appreciate any help.

---

### Post by LinuxRocks713 on 2008-07-05
Mount it yourself (assuming your DVD drive is /dev/scd0):

```

sudo mkdir /media/dvdplayer
sudo mount -t auto /dev/scd0 /media/dvdplayer -o uid=`id -u`

```

---

### Post by pikaia on 2008-07-05
Thanks for the feedback, but this doesn't work.  I changed your code to fit what is in my fstab: /dev/cdrom0, but I get "special device /dev/cdrom0 does not exist" Any thoughts?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=db4a997f-0e0e-453b-adff-6517e30ea5c7 /               ext3    defaults,erro$
# /dev/sda5
UUID=bb1f9ae6-a236-4906-a25f-04cc96f2fdd0 none            swap    sw           $
/dev/cdrom0        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by LinuxRocks713 on 2008-07-06
[QUOTE=pikaia;5325161]but I get "special device /dev/cdrom0 does not exist"QUOTE]


Well, what device is your dvd? It certainly is not /dev/cdrom0 then.

---

### Post by pikaia on 2008-07-09
Wouldn't it have to be considering that is directly from the fstab?  I have ONE optical drive.  I don't know whats going on but it is very frustrating.  Its a huge pain to reboot just to be able to access a disk.  It makes no sense to only be able to do it sometimes, and a reboot be required if its not.

Again, any help would greatly be appreciated.

---

### Post by christianvaldes on 2008-10-15
I am having the same problem.
Is there a solution?

---

### Post by christianvaldes on 2008-11-03
The upgrade to Intrepid fixed my issue with my DVD Drive.
DVR-108

I wish that someone would have communicated that the fix was coming in Intrepid.

---

