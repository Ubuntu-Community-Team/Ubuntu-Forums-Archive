---
title: "No Ubuntu versions will install"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by junknstuff on 2008-11-14
hey fellas!

i've been running ubuntu 8.04 on my laptop for about a year now and have worked out many things that have got me enjoying my ubuntu experience! this is the first time i have gone 100% ubuntu on my laptop, previously it was just dual booting and not used much.

going forward, intrepid came out and i thought, what the heck. time to transition my desktop as well!

unfortunately i was receiving the black screen that everyone else was, even after removing compiz and compiz-core.

thinking it was my disk or the new kernel, i popped in a amd64 and x86 8.04 cd and i was thrown to the (initramfs) screen where it seems to be checking for some "atax.xx revalidation failed"

did some mild research on that but did not come up with a good fix.

i'm at the point where i'm thinkin my hardware is just not support by ubuntu and i need some confirmation of this. i did google searches for days on end now and have not been able to come up with a solid answer. here is my set up:

intel quad core q6600
4gb ram pc6400
abit ip-35 pro mother board
100gb maxtor sata drive (main os drive dual booting w/windows server 08 workstation)
500gb samsung spinpoint sata (media)
200gb seagate IDE (data)
**Nvidia GeForce 8400GS**

please shed some light as google has not been able to. rock on!:guitar:

---

### Post by oldos2er on 2008-11-14
Your hardware looks fine, but it would also help to know about your video.

 Did you upgrade, or is this a new install of 8.10?

---

### Post by junknstuff on 2008-11-18
sorry for the late reply.

i forgot to add that the video card i am using is a Nvidia 8400gs. Nothing fancy, just threw it in during the build because i didn't have any other PCI-E card laying around :)

---

### Post by littletinman on 2008-11-18
Alright, try this, install using the "Alternate install CD". Make sure to burn it on the slowest speed, one of my install disks didn't work because i put it at max speed. Let me know if that works.

---

### Post by junknstuff on 2008-11-20
> **littletinman said:**
> Alright, try this, install using the "Alternate install CD". Make sure to burn it on the slowest speed, one of my install disks didn't work because i put it at max speed. Let me know if that works.

i don't know why i haven't tried this little trick. maybe its because i've never had a problem with ubuntu iso's, my media, and my burner BUT. i will try it because its definitely worth the time :popcorn: stay tuned!

---

### Post by junknstuff on 2008-11-21
updates:
downloaded the alternated installer for amd64 and burned at 6x. popped it in and began going through the install process. i had to leave and left it hanging at the partitioning stage (haven't chosen any specific partion for it to instlal on). i come back about 2hrs later and ubuntu 8.10 is waiting for me to login. wtf?

i am ecstatic, but i dont know whats going on. i know intrepid installed before, but i wasn't able to get to the login screen. did loading the kernel into my memory help it some how?

besides that, it seems to be OK now except that after i followed this thread:
[http://ubuntuforums.org/showthread.php?t=549658](http://ubuntuforums.org/showthread.php?t=549658)
to get my airpace card working, i decided to run updates/upgrades to the packages and now my airpace card is recognized but wont connect to my wpa secured network :(

---

