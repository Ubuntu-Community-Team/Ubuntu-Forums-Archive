---
title: "Gutsy upgrade failure"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Fraoch on 2007-10-18
Whoops, I could tell it wasn't going well when the following (sometimes very important!) packages "could not be configured and are in an unusable state":

libpam
login
base-files
bash
passwd
adduser
fuse-utils
ssl-cert
cupsys
dbus
libgnomevfs2-0
libgnome2-0
libbonoboui2-0
libgnomeui-0
libgnome-desktop-2
libgnome-menu2

Then I got a:

> The upgrade aborts now.  Your system could be in an unusable state.  A recovery will run now (dpkg --configure -a)

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade in the bugreport.
installArchives() failed

This was with "41 minutes remaining" a little over halfway on the progress bar.

The system then froze.  It no longer boots now due to a kernel panic, unable to mount root fs.

Good thing it's on a "development" machine.  I'll be keeping 7.04 on my regular desktop for some time...

I guess I'll have to wipe the HDD and install clean off a CD.

Is there any point filing a bug report and is there anything I can do?  Do you need more information?  Hardware:

ECS K7SOM+
AMD Duron 1.2 GHz CPU
512 MB RAM
Ubuntu 7.04, all updates installed

---

### Post by Fraoch on 2007-10-18
The system will get past the splash screen if I boot with the 2.6.20 kernel, but all I get is a blank X window.

---

### Post by MatthewPlanchard on 2007-10-18
Mine did that too the first time I restarted after a fresh install from the CD.

I had to press Esc at the Grub prompt and select the proper kernel for it to boot, then when I hit the black screen I pressed some combination of ctrl, alt, and f2/f1 (I am a total noob, I was just trying to see if any thing changed it).

It switched to the white text load progress screen and loaded fine. I have yet to restart again though, downloading updates is taking forever (usally I get 300+ kb/s and I'm down to 20, but that's what I get for waiting 'till today). I'll let you know if updating fixes the problem.

---

### Post by Fraoch on 2007-10-18
I can get a root prompt if I go into recovery mode with the 2.6.20-16 kernel, so if there was some CLI commands I could carry out I would.

I can't get into recovery mode with the 2.6.22 kernel, "unable to mount root fs".

---

### Post by hackmeister on 2007-10-18
I upgraded and the new kernel won't boot. I am able to boot into my old kernel without issue. I'll try re-installing the new kernel when I get home from work.

---

### Post by Spankypoo on 2007-10-18
Same exact thing here on an upgrade. Not cool.

---

### Post by asnd16 on 2007-10-18
well how about not even being able to get past the modifying sorces list step and it failing to connect to the sources list. . . then ending the install thus I am on the third try . . .

---

### Post by dlandis on 2007-10-18
Fraoch,

I am having the exact same problem with the same packages failing resulting in exact same kernel panic problem now.

Does anyone know why this "upgrade" just destroyed our drives??

---

### Post by kast on 2007-10-18
i would think these issues are having to do with the mass exoduses from 7.04 to 7.10 and the bandwidth issues that are happening.  

Repositories must be failing, or not responding causing packages to hang half downloaded, and or configured.

---

### Post by Fraoch on 2007-10-19
> **kast said:**
> i would think these issues are having to do with the mass exoduses from 7.04 to 7.10 and the bandwidth issues that are happening.  

Repositories must be failing, or not responding causing packages to hang half downloaded, and or configured.

I don't know - I would think there should be protection mechanisms in place to ensure half-downloaded packages aren't applied.

---

### Post by Fraoch on 2007-10-19
An install off a CD went perfectly but obviously wiped my drive.

Good thing there wasn't any critical data on that machine.

I'm very hesitant about doing this to my "production" machine now though.  There is critical data on that one - backed up, of course.  I believe I have my /home directory as a separate partition, but still, I'd lose all my installed programs and program settings, and they took a long time to get right.

---

### Post by VSpike on 2007-10-19
> **Fraoch said:**
> An install off a CD went perfectly but obviously wiped my drive.

I don't think the drive is wiped... it's just the new kernel can't access it.  The older kernel can still boot for me.

---

### Post by Fraoch on 2007-10-19
> **VSpike said:**
> I don't think the drive is wiped... it's just the new kernel can't access it.  The older kernel can still boot for me.

I installed off the CD and purposefully asked it to wipe the drive because my install was totally screwed.  I couldn't even boot with the old kernel anymore, not into the GUI anyway.

The new (clean) install is working fine using the new kernel.

---

### Post by MacDuff on 2007-10-19
There is definitely a problem with the update procedure and if my case it is in the download area.  The repositories apparently lack sufficient band width to deal with the load of everyone wanting to upgrade at the same time.  After 18 hours of downloading only about 45% of the files were in my box and sometime after I went to bed, the system quit downloading claiming that the connection had failed.   The download speed, by the way, was only 10% of what I would normally get from the repository.

The REALLY BAD thing is that apparently the files which had taken soooooo long to download were not saved and when I tried to re-start the process, everything apparently  had to be downloaded again.  Surely that can not be right.

I am not complaining about the speed.  I know that a company cannot buy enough bandwidth to deal with an occasional extreme but surely the developers can make a more robust download procedure that saves what has been downloaded and then picks up from where it last failed.

---

### Post by MacDuff on 2007-10-21
I have to retract my complaint about the download process not saving files to the point where the download connection is broken.

I tried another upgrade yesterday and although the download process seemed to completely re-start, it was only the first batch of files.  Once the process was into fetching files, it picked up where the previous download had failed and within minutes the download was complete and the installation went on without any hitches.

Now if I could just solve the problem with loosing all my video settings in the upgrade ......

---

### Post by dlandis on 2007-10-21
I don't think this failure was a result of download speed or repository traffic. The fact that all our problems began with the 'libpam' entry suggests there may have been something in our installations that the upgrade procedure didn't expect.

---

### Post by Fraoch on 2007-10-27
> **Fraoch said:**
> I'm very hesitant about doing this to my "production" machine now though.  There is critical data on that one - backed up, of course.  I believe I have my /home directory as a separate partition, but still, I'd lose all my installed programs and program settings, and they took a long time to get right.

I took a chance, backed up everything, and dove in - it worked flawlessly!

And this is a much more complicated machine - AMD64 architecture, using mdadm, lots of installed applications, all working fine after the upgrade!

The only confusion was the reset of my screen to 800 X 600, and I couldn't reset it in Screen Resolution, I had to set it in the new Screens and Graphics GUI.  Working fine now.

Umm, I'm going to be bored the rest of the weekend! :)

---

### Post by zveroboy on 2007-11-07
Here is something that worked for me.
Boot to the old kernel or live CD.

Take a look at your /boot/grub/menu.lst file.  See if there is 'initrd' entry missing for the new kernel(s) block or perhaps pointing to a wrong initrd.img-... file.  

That did it for me.  I hope this helps.

---

