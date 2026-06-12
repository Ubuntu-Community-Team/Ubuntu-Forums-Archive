---
title: "Edgy livecd won't start"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by crazymonkey on 2006-10-23
I'm trying to install Edgy using Desktop or alternate CD and it block at the same place with both cds. I tryed to do a CD check from the cd menu and it block at the same place. I checked the md5 sum of both and everything is ok.

```
[17179573.540000] EIP: [<f8847652>] pdc_sata_scr_write+0x12/0x20 [sata_promise] SS:ESP 0068:dfdf9dc0
[17179573.540000] udevd-event[1498]: run_program: '/sbin/modprob' abnormal exit
<7>ieee1394: Host added: ID:BUS[0-00:1023] GUID[00508d0000ee328b]

```

I installed Edgy on my laptop successfully using the Desktop cd without any problem.

The system i'm trying to install to have been running Dapper since june and i never had any problem using dapper livecd on it.

---

### Post by ciscosurfer on 2006-10-23
Try downloading and burning a new disc.  Go to the [bottom of this thread]("http://ubuntuforums.org/showthread.php?t=280499") and choose a location to download.  Be sure when you burn to disc, you choose the ISO option.

---

### Post by crazymonkey on 2006-10-23
Thank you, but like I said i succesfully installed Edgy on my laptop without any problem using the same cd. I tryed it the other way around by reinstalling a fresh dapper desktop and then updating it and when it rebooted it hanged, i couldnt see the error message but i bet it was the same. Maybe the generic kernel doesnt like my PC...

---

### Post by crazymonkey on 2006-10-23
Well I found what the problem is, I use a SATAII150 TX2plus controler which is known to cause Kernel panic in edgy...[https://wiki.ubuntu.com/EdgyKnownIssues]("https://wiki.ubuntu.com/EdgyKnownIssues")

Lets hope it will be solved soon...

---

