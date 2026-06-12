---
title: "Video Thumbnails in Nautilus"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rex4u on 2009-10-05
Hi everyone,  
I am having some trouble with my beloved Karmic. Nautilus does not create any thumbnails of videos. I have Medibuntu repo and ubuntu restricted extras installed.  

Additional piece of info here is that are no entries under (gconf-editor) Desktop>Gnome>Thumbnailer>xyz . It has no entries against any audio-video format. I consider this is the problem. But Why it is so and how to solve it ?  

Thanks for all the help !!!

---

### Post by Sashin on 2009-10-05
I also have this problem.

---

### Post by tjeremiah on 2009-10-05
a bit off topic. Is is possible to have moveable previews like you would when u hover over a audio file (u get a audio sample) ?

---

### Post by rex4u on 2009-10-05
> **tjeremiah said:**
> a bit off topic. Is is possible to have moveable previews like you would when u hover over a audio file (u get a audio sample) ?

Not yet :(

---

### Post by tjeremiah on 2009-10-05
> **rex4u said:**
> Not yet :(

:(

---

### Post by rex4u on 2009-10-05
> **tjeremiah said:**
> :(

Don't worry, someday...:guitar:
We already have come a long way :P

---

### Post by gali98 on 2009-10-05
I believe this is a regression in the new version of GNOME - not necessarily a bug. But I miss it already. I will try and file a bug about it. I'll report back here with the link.
Kory

---

### Post by gali98 on 2009-10-05
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/444103](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/444103)

Kory

---

### Post by rex4u on 2009-10-06
Will u believe how I solved it... I reinstalled Totem (yes I removed it alongwith Evolution and Rythembox right in the start itself) and now all the thumbnails are generating. Also the entries in gconf-editor has come up. This is annoying. Why gnome or Ubuntu won't let some other app create thumbnails (or I am in the dark here ???)  Thank u everyone for helping and Kory for filing bug report. Thanks...

---

### Post by gali98 on 2009-10-06
Running 
sudo apt-get install --reinstall totem totem-common
fixes the problem. You simply need to move the files to another folder and back for the thumbnails to be created.
(thanks rex4u!)
Kory

---

### Post by gali98 on 2009-10-06
Okay... This is new.
When I reboot, any videos on my desktop lose their thumbnails. Not good. Something is still going wrong.
Can someone confirm this?
Kory

---

### Post by rex4u on 2009-10-06
Hi Kory, What were the last few things you did before reboot ?

---

### Post by gali98 on 2009-10-07
Here is what I did. I closed out of every program then ran 
sudo apt-get install --reinstall totem totem-common
After that finished, I moved the video files on my desktop to my home folder and back and they created the thumbnails. Then I rebooted and the thumbnails were gone. I repeated this about two more times with the same results...
Kory

---

### Post by rex4u on 2009-10-07
Could u plz delete this folder ~/.thumbnails and then again try.
I hope your thumbnails would be back...

---

### Post by gali98 on 2009-10-07
That worked. Thanks! I'll post it on the bug report.
Kory

---

### Post by rex4u on 2009-10-08
Glad that it worked for you.:)

---

