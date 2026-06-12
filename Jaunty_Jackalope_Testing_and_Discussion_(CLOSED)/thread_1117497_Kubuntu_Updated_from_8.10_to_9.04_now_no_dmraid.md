---
title: "Kubuntu Updated from 8.10 to 9.04 now no dmraid"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TheFuzz4 on 2009-04-06
Ok so tonight I upgraded to the 9.04 beta and after I got everything up and running my dmraid now no longer decides to play nice. When running dmraid -ay here is my output
RAID set "nvidia_iicejhch" already active
ERROR: dos: reading /dev/mapper/nvidia_iicejhch[No such file or directory]
although if you do a ls /dev/mapper you get
control  nvidia_iicejhch
so clearly the file does exist
The Raid 5 that I'm trying to get access to is a NTFS partition and I need it to stay that way since I use this partition for both windows and Kubuntu.  Thanks in advance for any and all help you can provide with this.

---

### Post by TheFuzz4 on 2009-04-06
Oh and here is the output of dmraid -r
/dev/sdd: nvidia, "nvidia_iicejhch", raid5_ls, ok, 312581806 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_iicejhch", raid5_ls, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_iicejhch", raid5_ls, ok, 312581806 sectors, data@ 0
/dev/sda: nvidia, "nvidia_iicejhch", raid5_ls, ok, 312581806 sectors, data@ 0

---

### Post by t.n. on 2009-04-06
I had the same problem with mdadm (which is not the same as dmraid, but the cause could be the same).

I did not really find out what the issue was, the RAID system should have worked but simply didn't. In the end I reconfigured the RAID using mdadm and everything worked fine.
I would guess some configuration file/format changed during kernel releases and the reconfiguration has updated the new format, but I don't know.

---

### Post by TheFuzz4 on 2009-04-06
Thanks for the suggestion I'll see what I can figure out with the configuration of it.

---

### Post by TheFuzz4 on 2009-04-06
Well I just don't think that dmraid is yet compatiable with the 2.6.28-11 kernel that was released with Juanty.  If I let my 2.6.27-11 kernel load it has no problems whatsoever but load up the other one and no go.

---

### Post by TheFuzz4 on 2009-04-06
Yep and this right here confirms it
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/315735]("https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/315735") so it's a known bug and doesn't like the new Kernel yet oh well that is why this is in beta and not in RC status yet :)

---

