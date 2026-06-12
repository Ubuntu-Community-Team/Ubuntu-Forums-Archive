---
title: "Grub error"
date: 2015-12-01
forum: Installation &amp; Upgrades
---

### Post by Buajor on 2015-12-01
I have been trying to fix my grub error but no luck.

After i installed boor-repair it still did not work.

Below is the url [http://paste.ubuntu.com/13594303/](http://paste.ubuntu.com/13594303/)

---

### Post by ajgreeny on 2015-12-01
So what exactly is the problem?  Just saying you have a grub error does not help us very much.

Can you boot to either of the two versions of Ubuntu 14.04 that you seem to have installed on the machine?

Do you see a grub menu?  You should see the menu appear as there are the two versions of Ubuntu to boot.

Has the computer ever managed to boot to Ubuntu or is this a completely new installation that has failed?

We need more info please.

---

### Post by oldfred on 2015-12-01
I see in Summary report mention of Dell Perc Matrix. I can move thread to server sub-forum if desired.

Do you get grub menu? Can you boot with recovery mode?
You also show a second install in sda4 that looks almost identical to first install in sda2.

I have seen one or two other threads with users having issues with the Matrix video. But I do not know servers nor details on that video.

> *******lspci -nnk | grep -iA3 vga
0c:00.0 VGA compatible controller [0300]: Matrox Electronics Systems Ltd. G200eR2 [102b:0534]
Subsystem: Dell Device [1028:048c]
3f:08.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link 0 [8086:3c80] (rev 07)
Subsystem: Intel Corporation Device [8086:0000]


---

### Post by sandyd on 2015-12-01
From personal experience, PERC H310 firmware is buggy, and doesn't work well in Ubuntu or Debian. I don't know if thats changed as that particular server doesn't use that card anymore, but if you are still using the original firmware, check for upgrades.
I've never been able to get it to be actually used as a boot device, had all sorts of boot issues. However, it sort of works if you install Ubuntu on another drive, and then just use the PERC H310 as storage. Funny enough, it is VMWare compatible and [works in all versions of ESXi to date]("http://www.vmware.com/resources/compatibility/detail.php?deviceCategory=io&productid=18957").

---

