---
title: "Some sort of loop after install"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2009-10-09
I have installed Karmic once on a VM and twice on a new partition using two different burned medias (1 CD and 1 DVD). I have experienced a strange issue on every install. After the installation completed, the installer requested to remove the LiveCD, then instead of rebooting, it kept switching between a black screen and the desktop wallpaper.

It looked like some sort of error looping. I gave it some time to see if something would change, but since the installation CD was already removed, I assumed it wouldn't hurt to just hard reset the machine. I worked and nothing seems to be damaged.

Anyone has experienced the same behavior or know if this has already been reported?

---

### Post by zika on 2009-10-09
> **lovinglinux said:**
> I have installed Karmic once on a VM and twice on a new partition using two different burned medias (1 CD and 1 DVD). I have experienced a strange issue on every install. After the installation completed, the installer requested to remove the LiveCD, then instead of rebooting, it kept switching between a black screen and the desktop wallpaper.

It looked like some sort of error looping. I gave it some time to see if something would change, but since the installation CD was already removed, I assumed it wouldn't hurt to just hard reset the machine. I worked and nothing seems to be damaged.

Anyone has experienced the same behavior or know if this has already been reported?+1, scared me out of my pants ... twice ...

---

### Post by lovinglinux on 2009-10-09
> **zika said:**
> +1, scared me out of my pants ... twice ...

:)

Do you have nVidia card? Could it be a graphic issue?

---

### Post by zika on 2009-10-09
> **lovinglinux said:**
> :)
do you have nvidia card? Could it be a graphic issue?No, it is ATI HD 3650.

---

### Post by kansasnoob on 2009-10-09
> **lovinglinux said:**
> I have installed Karmic once on a VM and twice on a new partition using two different burned medias (1 CD and 1 DVD). I have experienced a strange issue on every install. After the installation completed, the installer requested to remove the LiveCD, then instead of rebooting, it kept switching between a black screen and the desktop wallpaper.

It looked like some sort of error looping. I gave it some time to see if something would change, but since the installation CD was already removed, I assumed it wouldn't hurt to just hard reset the machine. I worked and nothing seems to be damaged.

Anyone has experienced the same behavior or know if this has already been reported?

Maybe. During iso testing I wrote this report:

> I'm giving this a "Fail" only because if "auto-login" is chosen during the installation procedure, after being prompted to restart and remove CD the display just flashes briefly and dies, then continues to repeat that behavior until rebooting by pressing Alt > Sys Req > B. Then the desktop starts up fine.

If you install with the default, require a password to login, all is fine.

There also seems to be a bug effecting Gparted post-install, but not related to the iso image.

I've not yet searched for bug reports. 	

[http://iso.qa.ubuntu.com/qatracker/result/3104/5](http://iso.qa.ubuntu.com/qatracker/result/3104/5)

And actually two more, considered filing a bug report and even asked for some guidance in doing so:

[http://ubuntuforums.org/showthread.php?t=1279375](http://ubuntuforums.org/showthread.php?t=1279375)

So, if "auto-login" was chosen during installation, then I guess we're all experiencing the same thing.

I gave up on filing a bug report because I'd been using an old 30GB drive that I always use for iso testing (I always begin with a full install, then auto-resize, and finally a manual partitioning install) and I was unable to duplicate the problem using two other hard drives (a WD 80GB and a WD 160 GB) so I decided it must be just the drive.

Now you have me wondering, and I see added to that iso testing report:

> At end of the install the screen keeps flashing instead of doing a reboot. I had to switch off the computer, but the system is ok on restart

So, if we all chose auto-login then I guess we should file a bug report so this doesn't happen with the RC and the Final.

---

### Post by kansasnoob on 2009-10-09
I'll be out to the hospital most of the day, but I'll check back in this evening.

If it all seems like the same bug then I'll try to file a bug report against ubiquity ............. eerrr, well, I'm thinking ubiquity.

That 30 GB testing drive hasn't been touched since then so I could pop it back in to possibly gather info if requested by the devs. I'd need detailed instructions of what to gather though!

---

### Post by lovinglinux on 2009-10-09
> **kansasnoob said:**
> So, if we all chose auto-login then I guess we should file a bug report so this doesn't happen with the RC and the Final.

Nope. I didn't use the auto-login option.

---

### Post by zika on 2009-10-09
> **lovinglinux said:**
> Nope. I didn't use the auto-login option.It happend to me in both cases, auto and non-auto ...

---

### Post by kansasnoob on 2009-10-09
It still sounds like we experienced the same "bug". I'm just wrong about the "common cause".

As I said I was not able to duplicate that result with every install and, as memory serves me, I believe I installed a total of seven times.

Must run now, but I'll be thinking about this.

Due to changes in gdm (assuming we're all using gdm and not kdm) I wonder if it might be worthwhile for some of us to try the daily build over the next few days and see if we can reproduce that result:confused:

Just a thought.

---

### Post by mc4man on 2009-10-09
Same thing on 2 similar desktops (with nvidia/agp)
Happened every time w/a5 and a6, only on one  with a beta (fresh installs

Seemed to have no lasting effect after a power off and reboot 

( don't think it always was set up with auto login, though that's my tendency

---

### Post by kansasnoob on 2009-10-09
mc4man,

I'm sure we're seeing the same thing. It's obviously not persistent.

I found that all subsequent reboots after a Alt > SysRq > B were fine.

So, I'm wondering should I try the newest daily build, not a huge problem to do so (and the weather here is too yucky to do outdoor things anyway), or should I try to file a bug report and see if they can suggest what info to gather?

Just not sure what step to take next. I'd assumed it was limited to only my testing hard drive, but that's clearly NOT the case.

BTW thanks for the link to this:

[http://ubuntuforums.org/showthread.php?p=7606998#post7606998](http://ubuntuforums.org/showthread.php?p=7606998#post7606998)

Handily shortened my reinstall and post-install time by about an hour:)

Oh, and if you think a bug report is the way to go, what package should I file it against?

---

### Post by kansasnoob on 2009-10-09
I'm downloading the daily ........ slowly! Wish I'd kept the beta iso on disc so I could use rsync.

I don't think you can do it if you copy the CD back to file. I'll have to study that.

The servers must be getting hammered again.

Anyway, I guess I'll try using my old testing drive again and see if I can reproduce this. Then I could try the 160 GB.

Damn I need more drives!

Dental and vet bills say no time soon!

---

### Post by mc4man on 2009-10-09
> thanks for the link to this

I find that extremely useful not only for re-installs or installs to other machines but also a way to manage some mods, and self-built packages (not checkinstall ones

My one on hardy is about 170 deep

I've left mt testing install alone but have found some use already on a 'real' karmic install 
> doug@doug-desktop:~/repo$ ls *.deb
amarok14_1.4.10-0ubuntu3~ppa4_i386.deb
amarok14-common_1.4.10-0ubuntu3~ppa4_all.deb
amarok14-engine-xine_1.4.10-0ubuntu3~ppa4_i386.deb
faac_1.28-0.3_i386.deb
ffmpeg_0.5+svn20090907-0.0_i386.deb
libavcodec52_0.5+svn20090907-0.0_i386.deb
libavcodec-dev_0.5+svn20090907-0.0_i386.deb
libavdevice52_0.5+svn20090907-0.0_i386.deb
libavdevice-dev_0.5+svn20090907-0.0_i386.deb
libavfilter0_0.5+svn20090907-0.0_i386.deb
libavfilter-dev_0.5+svn20090907-0.0_i386.deb
libavformat52_0.5+svn20090907-0.0_i386.deb
libavformat-dev_0.5+svn20090907-0.0_i386.deb
libavutil50_0.5+svn20090907-0.0_i386.deb
libavutil-dev_0.5+svn20090907-0.0_i386.deb
libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
libfaac0_1.28-0.3_i386.deb
libfaac-dev_1.28-0.3_i386.deb
libmediainfo0_0.7.20-1_i386.Ubuntu_9.04.deb
libmp4v2-1_1.9.1-0.1_i386.deb
libmp4v2-dev_1.9.1-0.1_i386.deb
libpostproc51_0.5+svn20090907-0.0_i386.deb
libpostproc-dev_0.5+svn20090907-0.0_i386.deb
libstdc++5_3.3.6-17ubuntu1_i386.deb
libswscale0_0.5+svn20090907-0.0_i386.deb
libswscale-dev_0.5+svn20090907-0.0_i386.deb
libvlc2_1.0.3-1ubuntu1_i386.deb
libvlccore2_1.0.3-1ubuntu1_i386.deb
libx264-68_0.svn20090730-0.0_i386.deb
libx264-75_0.svn20090921-0.0_i386.deb
libx264-76_0.svn20090928-0.0_i386.deb
libx264-dev_0.svn20090921-0.0_i386.deb
libzen0_0.4.3-1_i386.Ubuntu_9.04.deb
mediainfo-gui_0.7.20-1_i386.Debian_5.deb
mplayer_1.0~rc3+svn20090924-0-karmic1_i386.deb
rhythmbox_0.12.5-0ubuntu1-1_i386.deb
rubyripper_0.5.5-0.0_all.deb
totem-xine_2.28.1-0ubuntu1-1_i386.deb
vlc_1.0.3-1ubuntu1_i386.deb
vlc-data_1.0.3-1ubuntu1_all.deb
vlc-nox_1.0.3-1ubuntu1_i386.deb
vlc-plugin-pulse_1.0.3-1ubuntu1_i386.deb
vlc-plugin-sdl_1.0.3-1ubuntu1_i386.deb
w32codecs_20071007-0medibuntu4_i386.deb




---

