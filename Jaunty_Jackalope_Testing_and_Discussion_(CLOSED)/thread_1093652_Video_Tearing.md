---
title: "Video Tearing?"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Roasted on 2009-03-11
Is anybody getting any video tearing with Jaunty? I know Hardy was solid with that but Intrepid introduced video tearing which oddly hasn't been fixed throughout its current lifespan.

I was hoping Jaunty would have better luck...

---

### Post by TrueTom on 2009-03-11
I you have an Intel graphics card, you're out of luck. The developers of the driver have no idea how to fix it...

---

### Post by jmmL on 2009-03-11
I get video tearing with nVidia's drivers on jaunty. I have an 8600M GS. It doesn't bother me *too* much though, but it would be nice if it didn't do it in the first place.

---

### Post by Roasted on 2009-03-11
I have a Nvidia.

It's a total crapper keeping Vista around for games as it is... now to use it with movie watching as well just brings a sad face to me.

I can't use Ubuntu for everything if it doesn't do... everything. Not to be all picky but, it's frustrating when something that once-was suddenly can't-do anymore.

Let's pray for the final release to handle it without any issues...

---

### Post by LavianoTS386 on 2009-03-11
I only have this issue with compiz enabled, on both my Nvidia card and my EeePC w/ intel. Disable compiz while watching video.

---

### Post by crjackson on 2009-03-11
> **Roasted said:**
> Is anybody getting any video tearing with Jaunty? I know Hardy was solid with that but Intrepid introduced video tearing which oddly hasn't been fixed throughout its current lifespan.

I was hoping Jaunty would have better luck...

Well, let's keep our fingers crossed. I reverted to Hardy because of same. The upshot is that Hardy is an LTS and has lots of life in it.

---

### Post by crjackson on 2009-03-11
> **TrueTom said:**
> I you have an Intel graphics card, you're out of luck. The developers of the driver have no idea how to fix it...

Some people are having good luck with it, others not so much. We'll just have to wait until it's a release and see what happens.

It could be that 9.10 is the ticket for Intel Video - Who Knows?

---

### Post by Nullack on 2009-03-11
Its not NVIDIA's fault, turn off compiz. Its because Linux lacks proper GPU memory management. Compiz breaks other stuff too.

With compiz off and the NVIDIA drivers I do not get any artifacting on video playback.

---

### Post by Roasted on 2009-03-11
> **Nullack said:**
> Its not NVIDIA's fault, turn off compiz. Its because Linux lacks proper GPU memory management. Compiz breaks other stuff too.

With compiz off and the NVIDIA drivers I do not get any artifacting on video playback.

Yeah, that was the argument with Intrepid. Turn off compiz and all of your problems will be solved!

For the majority of us Intrepid users, that was not the case.

Again, Hardy - Yes, Intrepid - No. :( :( :( :(

---

### Post by Nullack on 2009-03-11
If your still having problems:

* Are you using totem?
* Gstreamer?
* What video driver version?
* What gpu do you have?

Have you got a sample of a problem video I can look at?

I dont have any video tearing and I havent seen any wide reports of it in jaunty.

---

### Post by Roasted on 2009-03-12
It does it using anything. I've tested totem, vlc, mplayer, movie player, etc. Even youtube sometimes does it.

This was taken with VLC.

[IMG]http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=SlashGuitarII.png[/IMG]

Nvidia 9600GT 256bit 512mb
Ubuntu Intrepid 8.10 64 bit
Nvidia 177 drivers

I tried installing 180 drivers and my system FUBAR'd.

---

### Post by Nullack on 2009-03-12
Well, Jaunty comes with X server version 1.6 that has numerous fixes. Also, the NVIDIA driver 180.37 is widely regarded as robust from reports on the nvidia nvnews forum.

I havent used Intrepid in a long time but I certainly can say that I have not had any video tearing on my NVIDIA card. The only issue is compiz and I disable it.

If you want to try out Jaunty before release or use the release version I would say you should be rid of the issue.

---

### Post by Roasted on 2009-03-12
I think it'd be in my best interest to try the latest 180 drivers...

Of course, this time I'll make an image of my system before I try that one...

---

### Post by bofphile on 2009-03-12
> **TrueTom said:**
> I you have an Intel graphics card, you're out of luck. The developers of the driver have no idea how to fix it...

It seems like this has been fixed by the developers: [http://bugs.freedesktop.org/show_bug.cgi?id=19635]("http://bugs.freedesktop.org/show_bug.cgi?id=19635")

At least with desktop effects disabled for now.

I just hope the fix will be incorporated into Jaunty.

---

### Post by TrueTom on 2009-03-12
> **bofphile said:**
> It seems like this has been fixed by the developers: [http://bugs.freedesktop.org/show_bug.cgi?id=19635]("http://bugs.freedesktop.org/show_bug.cgi?id=19635")

Ok, that actually works (atleast with compiz off), there is hope... :)

---

