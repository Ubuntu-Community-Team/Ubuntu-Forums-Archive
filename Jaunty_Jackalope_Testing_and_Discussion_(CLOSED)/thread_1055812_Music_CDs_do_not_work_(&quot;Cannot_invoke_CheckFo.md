---
title: "Music CDs do not work (&quot;Cannot invoke CheckForMedia on HAL&quot; error)"
date: 2009-01-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tawmas on 2009-01-31
Hi!

I just tried inserting a music CD I wanted to extract to flac. It didn't mount, and I instead got a popup with the following error message:

```
Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.32" (uid=1000 pid=6525 comm="/usr/lib/gvfs/gvfs-hal-volume-monitor ") interface="org.freedesktop.Hal.Device.Storage.Removable" member="CheckForMedia" error name="(unset)" requested_reply=0 destination="org.freedesktop.Hal" (uid=0 pid=5286 comm="/usr/sbin/hald "))
```

I tried launching sound-juicer all the same, but it just blocked (nothing happened on screen, but the process was running and apparently unkillable). As I was started writing this message (after a few minutes I spent googling for an already reported bug and scratching my head), I received a popup with "Unable to mount media". I checked ps again, and the sound-juicer process was gone...

My googling found no relevant bug, neither in Launchpad nor upstream. I'd like to report one, but I don't know if this is a gvfs or a hal thing.

What would you pick?

Also, is there any workaround that I can try?

---

### Post by Gina on 2009-01-31
I've just checked this in my 64 bit Jaunty.  Put music CD in drive, icon came up on desktop, dialog came up asking which app to use with Rhythmbox selected (which I use for ripping anyway) clicked OK and Rhythmbox came up and I was able to play the music.  I then tried ripping and that worked too.  Only thing was that it thought that there were 45 tracks rather than the 15 the CD had on it.  When it canme to copy track 16 it wanted to overwrite track 1 so I said no - and so on up to 45.  The ripping of the 15 tracks was successful.

---

### Post by tawmas on 2009-01-31
I investigated the problem a bit more. I have a second optical unit which seems to work correctly, and I see bunches of errors in dmesg about the other unit, so I guess it's either the kernel or the hardware failing.

I suspect the hardware. I don't know how to troubleshoot this, but I think I will open the PC and check for loose cables. From there on, all that's left is googling! :-)

If someone has suggestions, I'm ready to listen.

---

### Post by billyShears on 2009-01-31
same here but it happens when I try to mount an USB flash disk with a LUKS encrypted partition on it, gnome asks the password correctly but then it does not mount the partition, I get this error if I try to mount it by clicking on it with nautilus or inside the places menu:

Unable to scan USB Drive for media changes
Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.22" (uid=1000 pid=3939 comm="/usr/lib/gvfs/gvfs-hal-volume-monitor ") interface="org.freedesktop.Hal.Device.Storage.Removable" member="CheckForMedia" error name="(unset)" requested_reply=0 destination="org.freedesktop.Hal" (uid=0 pid=3241 comm="/usr/sbin/hald "))

---

### Post by tawmas on 2009-01-31
Uh... curious... USB drives (both flash-based pendrives and external hard disks) work flawlessly here, though I don't have any encrypted partitions around.

---

### Post by billyShears on 2009-01-31
I tried to connect the flash disk on another usb port and it mounts correctly...
I'm not affected by the audio cd bug.

---

### Post by Gina on 2009-01-31
Sounds like hardware that is on the edge.  May be something to do with the actual timing of commands to the device.  I've had this sort of problem in the past.  It's fiendishly difficult to track down.  Sometimes swapping the drive to another port cures the problem.  People used to find this a while back with PCI and ISA cards - work better in some slots than others.  OTOH your hardware may be about to fail.

---

### Post by billyShears on 2009-01-31
> **Gina said:**
> OTOH your hardware may be about to fail.

This is not unlikely actually :D

but I've got no problems at all with ubuntu 8.10

---

### Post by Eclipse. on 2009-01-31
Please file a bug and give as much information as you can to help get it fixed.;)

---

### Post by ayates on 2009-01-31
I have two drives, a cd-r/w and a dvd-r/w. I insert a blank cd in the cd-r/w and get the same error msg as above, but it works fine in the dvd-r/w. I insert a non-blank and it works in both. Weird.

---

### Post by tawmas on 2009-01-31
> **Gina said:**
> OTOH your hardware may be about to fail.

I also believe that these are from half-broken hardware, although our half-broken hardware might be exposing some half-bugged software path which is not otherwise hit during normal operation.

I don't know what it means, except that hardware's not working as it should, but my /var/log/messages is filled with logs like the fragment below coming from the failing CD-ROM:

```
Jan 31 12:17:08 tylke kernel: [11879.856016] ata1: link is slow to respond, please be patient (ready=0)
Jan 31 12:17:13 tylke kernel: [11884.840016] ata1: device not ready (errno=-16), forcing hardreset
Jan 31 12:17:13 tylke kernel: [11884.840026] ata1: soft resetting link
Jan 31 12:17:13 tylke kernel: [11885.092296] ata1.00: configured for UDMA/33
Jan 31 12:17:13 tylke kernel: [11885.124362] ata1.01: configured for PIO0
Jan 31 12:17:13 tylke kernel: [11885.125002] ata1: EH complete
```

It's bed time 'round here, I will investigate further tomorrow.

---

### Post by Ms_Angel_D on 2009-02-24
Did anyone ever figure this out? Or is there a lead on it maybe, I get this error no matter what Kind of CD's I insert. It's very strange as my drive works fine on Vista. And only recently did it begin to give me this error. Only Ubuntu 8.10 gives me this error. I have a fairly new system I doubt it has anything to do with failing hardware.

Angel

---

### Post by tawmas on 2009-02-24
> **MetalHellsAngel said:**
> Did anyone ever figure this out? Or is there a lead on it maybe, I get this error no matter what Kind of CD's I insert. It's very strange as my drive works fine on Vista. And only recently did it begin to give me this error. Only Ubuntu 8.10 gives me this error. I have a fairly new system I doubt it has anything to do with failing hardware.

Angel

Not yet. :-( Perhaps it's time I look into that again... I have a second unit, so apart from the slight inconvenience the pressure to have this fixed was low... :-)

---

### Post by Ms_Angel_D on 2009-02-24
Actually here's a bit of info on what I've done, maybe this too will help some. I'm not really a programmer or anything of that sort, but I did try a few things since I posted earlier, since I only have the one drive.

My system was due for wipe down anyway so I decided to back everything up to my external, and try a fresh install.

I installed from a disk using the problematic disk drive, once I finished with the actual install process, I proceeded to do my usual updates enabling 3rd party repositories before hand as well as backports, so far so good. But then after reboot I tried a disk again and again the system froze completely and I was forced to do a hard reboot. 

At this point I'm frustrated and after reading a bug or two on launchpad I almost decide to reinstall hardy and see if that will fix the issue, but then I thought what the  hell I already have a clean system and everything is backed up so I'll give it one more try.

Again I do an install from the disk using the same drive with no problems. This time I ran the updates only enabling 3rd party repositories without the backports. Everything runs smooth I do the reboot then I put in my Ubuntu disk and it loads right up asking what I want to do. So I click cancel then decide to try my Guild Wars disk again success. 

I decided to enable backports and have a look at what updates it would offer me. I noticed a few of the updates are for Brasero. Now I haven't installed backports updates, actually I disabled them again. But I have to wonder if that update isn't what caused the issue, but at this point I'm too tired to try it and find out.

Anyway maybe some of this info will give you some help on tracking down whatever it is that's causing a problem like this.

Angel

---

### Post by billyShears on 2009-02-24
an HAL update has solved the problem completely for me.

---

