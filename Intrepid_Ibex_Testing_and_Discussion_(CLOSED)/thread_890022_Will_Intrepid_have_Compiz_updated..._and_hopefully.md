---
title: "Will Intrepid have Compiz updated... and hopefully that flicker bug?"
date: 2008-08-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xeriouxi on 2008-08-14
Hi!

I'm not able at present to test out Intrepid and so I don't know too much about it, but I was wondering if it will feature an update to Compiz in it?

I have a really annoying bug in Hardy that makes my video's tear and flicker because of Compiz, and I know I can set an option 'Sync To VBlank' that fixes this but then Compiz runs real sluggish, especially when using the Cube.

I haven't seen any news on this issue being fixed in Hardy so I was wondering if there's a chance it might happen in Intrepid?

Thanks! =)

---

### Post by klange on 2008-08-15
Intrepid has Compiz from git as of 8/7/08:
compiz (1:0.7.7+git20080807-0ubuntu2)

---

### Post by Exsecrabilus on 2008-08-15
Isn't that the near-to-latest, if not latest, version of Compiz?

---

### Post by Nullack on 2008-08-16
Yes look at the git date

---

### Post by miltiad on 2008-09-28
> **xeriouxi said:**
> Hi!

I'm not able at present to test out Intrepid and so I don't know too much about it, but I was wondering if it will feature an update to Compiz in it?

I have a really annoying bug in Hardy that makes my video's tear and flicker because of Compiz, and I know I can set an option 'Sync To VBlank' that fixes this but then Compiz runs real sluggish, especially when using the Cube.

I haven't seen any news on this issue being fixed in Hardy so I was wondering if there's a chance it might happen in Intrepid?

Thanks! =)

I have the same problem. Wich one do you check ?

I got 2 in the "X Server XVideo Settings", one for "Video Texture Adaptor" and the other for "Video Blitter Adaptor Settings".

I also have one in "OpenGL Settings".

Screenshots:
[IMG]http://img527.imageshack.us/img527/6450/capturenvidiaxserversetcp7.png[/IMG]

[IMG]http://img264.imageshack.us/img264/9597/capturenvidiaxserversetsd5.png[/IMG]

Thanks

---

### Post by xeriouxi on 2008-09-28
> **miltiad said:**
> I have the same problem. Wich one do you check ?

I got 2 in the "X Server XVideo Settings", one for "Video Texture Adaptor" and the other for "Video Blitter Adaptor Settings".

I also have one in "OpenGL Settings".

Screenshots:
[IMG]http://img527.imageshack.us/img527/6450/capturenvidiaxserversetcp7.png[/IMG]

[IMG]http://img264.imageshack.us/img264/9597/capturenvidiaxserversetsd5.png[/IMG]

Thanks

Hi miltiad!

The option I used is actually in the Compiz settings manager. If you go General Options > Display Settings then you should see the 'Sync To VBlank' option there! Hope that helps! =)

---

