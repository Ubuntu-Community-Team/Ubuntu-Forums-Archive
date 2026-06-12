---
title: "Got Me at Last"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by allupinya on 2005-11-30
I am running a new HP laptop ZE6130us 3200+ AMD 64
I have worked around the normal problems and have 5.10 installed..
One problem i have not been able to overcome is the xorg desktop..After loading the 64 ubuntu it give me the `ol " Xorg desktop disabled screen" thou all else works...I do have the new ATI M200 Radeon igp with 128 dedicated memory and the new wxga hd display. By adding the boot f7: linux noapic nolapic debian-installer/framebuffer=false  It would hang a couple times but would install after.
The xorg log is not telling me much.
I am wondering if there is a workaround to get the x desktop enabled on the lappy in 64 bit? from root or single user? "have not got it yet"
Any help would be great! 
Thanks in advance..
A user with 5 machines of all ages running Ubuntu 5.10

---

### Post by allupinya on 2005-11-30
A quick self reply to keep it up top:)

---

### Post by m3ck4rn on 2005-12-05
try to change in xorg.conf from Driver: "ati" to Driver: "vesa".
I've got ATI m200 and that worked foe me.

---

