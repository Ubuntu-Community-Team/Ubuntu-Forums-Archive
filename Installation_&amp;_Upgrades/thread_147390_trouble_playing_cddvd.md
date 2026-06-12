---
title: "trouble playing cd/dvd"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by parsival on 2006-03-20
Hi Forum,

I am having as lot of trouble getting a cd or dvd to play.
I dont know if this is one problem or a series of unrelated problems.

gnome-cd wont play cd's
"** (gnome-cd:12109): WARNING **: Could not open resource for writing."
but nothing happens
I used gstreamer-properties
to change the "default sink" to ALSA
now the track indicator moves but still no sound.

kscd --  the track indicator moves but no sound.

Konqueror -- the cd icon starts Konqueror which gives the error message
"klauncher said: Unknown protocol 'audiocd'."

alsaplayer -- crshes as soon as I selected "cd player (CDDA)"

sound-juicer (cd ripper) can play the cd!!

sound is clearly working (as sound-juicer shows) and if I 
rip the cd then alsaplayer or xmms can play it.

I am having similar troubles with dvd's

mplayer says  "failed to open dvd://1"
totem movieplayer  says "Failed to find mountpoint for 
         device /dev/hda in /etc/fstab"
but there is a mountpoint in  /etc/fstab
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto  0  0

---

### Post by IYY on 2006-03-20
> /dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

This doesn't look right to me. Why would the device /dev/hda (a hard disk) be mounted as a CD-ROM? Try replacing hda with hdc.

---

### Post by parsival on 2006-03-20
Hi IYY,

yes it does look a bit odd. However it matchs the boot-up messages ie.

hda: PHILIPS DVD+/-RW DVD8701, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20

could this just be because the hard disk is a SCSI device?
ie /etc/fstab
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda9       /data           ext3    defaults        0       2
/dev/sda6       /local/home     ext3    defaults        0       2
/dev/sda8       /tmp            ext3    defaults        0       2
/dev/sda3       /usr            ext3    defaults        0       2
/dev/sda7       /var            ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto  0   0

Bye
Rob

---

### Post by parsival on 2006-03-25
Hi Forum,

here is an update on my cd problem

1) beep media player -- works!
2) gnome-cd          -- works!
3) kscd   -- no sound
4) alsaplayer -- crashes whenI try to play a cd
5) vlc media player   -- works!

so this problem is solved. How I solved it I am not sure. I have changed
so many options that I have completely lost track. I think that selcting
ALSA output and rebooting got beep to work -- I have no idea what caused 
vlc and  gnome-cd to start working. Not very helpful I know.

As far as DVD do -- I have found that the problem is relatd to 
dvdread. I will start another thread on that.

Bye
Rob

---

