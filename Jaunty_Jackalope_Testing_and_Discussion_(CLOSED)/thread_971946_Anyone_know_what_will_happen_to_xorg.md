---
title: "Anyone know what will happen to xorg?"
date: 2008-11-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-11-05
Auto detect doesn't always work. :-k

---

### Post by Slug71 on 2008-11-06
Wayland;)

---

### Post by danf_1979 on 2008-11-06
if automagic does not work, you can do it by hand.

---

### Post by gnomeuser on 2008-11-06
> **Slug71 said:**
> Wayland;)

whatever gave you that idea? It certainly was not any of the articles or the blog post by the author.

[http://hoegsberg.blogspot.com/2008/11/premature-publicity-is-better-than-no.html](http://hoegsberg.blogspot.com/2008/11/premature-publicity-is-better-than-no.html)

You may also enjoy reading this as well:
[http://cgit.freedesktop.org/~krh/wayland/tree/NOTES](http://cgit.freedesktop.org/~krh/wayland/tree/NOTES)

---

### Post by Slug71 on 2008-11-06
> **gnomeuser said:**
> whatever gave you that idea? It certainly was not any of the articles or the blog post by the author.

[http://hoegsberg.blogspot.com/2008/11/premature-publicity-is-better-than-no.html](http://hoegsberg.blogspot.com/2008/11/premature-publicity-is-better-than-no.html)

You may also enjoy reading this as well:
[http://cgit.freedesktop.org/~krh/wayland/tree/NOTES](http://cgit.freedesktop.org/~krh/wayland/tree/NOTES)

Thanks Gnomeuser, I read the Phoronix article which to me seemed like a xorg replacement or alternative.

---

### Post by philinux on 2008-11-06
> **danf_1979 said:**
> if automagic does not work, you can do it by hand.

Not good for newbies though.

---

### Post by philinux on 2008-11-12
Any update. The beginners are ranting over the loss of displayconfig when autodetect fails.

So whats the gossip re xorg.

---

### Post by gnomeuser on 2008-11-12
> **philinux said:**
> Auto detect doesn't always work. :-k

Did you file bugs?

---

### Post by dinxter on 2008-11-12
is this not the area bullet proof x was working on, does anyone know how well that is progressing? i thought the principle was to fallback to a decent and simple gui so when auto detect failed then there was a sensible way to configure things. it was a little raw in hardy(!) but i havent been paying attention to how its being developed, the idea is sound though

---

### Post by gnomeuser on 2008-11-12
> **dinxter said:**
> is this not the area bullet proof x was working on, does anyone know how well that is progressing? i thought the principle was to fallback to a decent and simple gui so when auto detect failed then there was a sensible way to configure things. it was a little raw in hardy(!) but i havent been paying attention to how its being developed, the idea is sound though

BulletProof was always a horrible idea, as proclaimed from experience by Adam Jackson and many other developers.

[https://www.redhat.com/archives/fedora-devel-list/2007-September/msg00051.html](https://www.redhat.com/archives/fedora-devel-list/2007-September/msg00051.html)

As such experience proved Adam right and it is now a dropped feature, it is entirely removed from Ubuntu as I recall during the Intrepid cycle. 

Good intentions but unwillingness to listen to criticism and experience doomed the approach before it got off the ground. It is an ex-parrot.

On the plus side, we have gotten increasingly better at handling things automatically. Failure to do so is a bug and should be filed. It typically doesn't take long for such problems to be worked out, spotting the trouble areas is the hard bit making increasing important to get them tracked somehow (I personally favour an automated approach like smolt to gather the data)

---

### Post by dinxter on 2008-11-12
surely it is only pining for the fjords!
as i say, i havent been keeping up with a lot of projects for a fair while, the principle is sound though, there should always be a solid fallback if X fails ubuntu users should always reach a desktop if nothing else. and auto detect will always fail in some cases. even just generating a vesa desktop is a lot better than dumping people to command line. there will always be bugs in auto detection, there has to be a decent fallback position. perhaps it was the way i've learned to design but in this sort of failure is inevitable in certain cases and this should be dealt with in some way 'gracefully'. if 'bullet proof x' wasnt the way then the idea was certainly the right one. excuse me if im missing something obvious but is smolt something that would work for this?

---

### Post by gnomeuser on 2008-11-12
> **dinxter said:**
> surely it is only pining for the fjords!
as i say, i havent been keeping up with a lot of projects for a fair while, the principle is sound though, there should always be a solid fallback if X fails ubuntu users should always reach a desktop if nothing else. and auto detect will always fail in some cases. even just generating a vesa desktop is a lot better than dumping people to command line. there will always be bugs in auto detection, there has to be a decent fallback position. perhaps it was the way i've learned to design but in this sort of failure is inevitable in certain cases and this should be dealt with in some way 'gracefully'. if 'bullet proof x' wasnt the way then the idea was certainly the right one. excuse me if im missing something obvious but is smolt something that would work for this?

Smolt would help here primarily in that it is a great way to get data on what hardware combinations cause issues. Often we simply don't know where the problem lies and getting data fixes that. 

Using such data gathering you can also track regressions, what changes cause what setups to stop working.

It does not fix the autodetection, it fixes the lack of data which makes the corner cases in autodetection light up.

As for a fallback, I would see any failure to autodetect as the worse problem. A fallback is merely a bandaid, you then ask the user to input all kinds of numbers and other advanced information. This is not really a suitable fallback, we could fallback to vesa and in fact I believe we do.

I think the parent post is quite symptomatic of the problem we face, if we provide a tool like bulletproof we pave over problems and they never get fixed. When the user has either managed to fix the problem or given up we never hear about the problem and thus we don't know what is broken.

---

### Post by dinxter on 2008-11-12
i obviously agree that solving the actual problems is always the best solution. but that is always easier said than done, there will always be bugs that prevent X from popping up. There should be a robust 'get me to x' daemon that should make sure that no matter what, there is no catastrophic failure.
bugs will always be there but i would hope that in a years time i will never see a post about people having to email from windows because they couldnt even get to a desktop. technically all the components are there to make sure that this should never happen, its merely an incredibly complicated matter of putting them all together :)

---

### Post by philinux on 2008-11-13
> **gnomeuser said:**
> Did you file bugs?

Autodetect workd for me so cant raise a bug for my hardware. I have encouraged people for whom it did not work to file bugs as thats the only way the devs can fix it. The most common rant in Absolute beginners forum is "stuck in low res no higher resolutions offered, no graphics driver offered".

---

### Post by ronacc on 2008-11-13
The major problem I had with "bulletproofX" was that it would without warning overwrite your xorg.conf if you accepted low graphics mode . There will always be cases where autodetect fails for some reason and some of these can not be fixed by any improvement in x because the fault may lie outside of x . Perhaps when a failure occurs we should be offered a simple set of choices , for example . 1 force vesa   2 enter data for your card and monitor  3 contine with command line .

---

### Post by meborc on 2008-11-13
> **ronacc said:**
> The major problem I had with "bulletproofX" was that it would without warning overwrite your xorg.conf if you accepted low graphics mode . There will always be cases where autodetect fails for some reason and some of these can not be fixed by any improvement in x because the fault may lie outside of x . Perhaps when a failure occurs we should be offered a simple set of choices , for example . 1 force vesa   2 enter data for your card and monitor  3 contine with command line .

as far as i remember, it always generated xorg.conf_DATE or something like that files to recover... so it was not overwriting... it was backup and new file

---

### Post by ronacc on 2008-11-13
> **meborc said:**
> as far as i remember, it always generated xorg.conf_DATE or something like that files to recover... so it was not overwriting... it was backup and new file

the problem was not no backup ,the problem was no warning ! also in the early versions it would do so no mater what choice you made. I don't know If this was ever changed because I never gave it a chance  I simpley killed the lowgraphics screen with ctrl>alt>bkspc and fixed things from the cmd line .

---

### Post by MacUntu on 2008-11-13
I just want to plug in my second monitor/a beamer and use it. Right now I have to use nvidia-settings for configuration, write the changes to xorg.conf, and restart X. I don't even know what SHOULD work so I can't file any bug reports.

---

### Post by RAOF on 2008-11-13
> **MacUntu said:**
> I just want to plug in my second monitor/a beamer and use it. Right now I have to use nvidia-settings for configuration, write the changes to xorg.conf, and restart X. I don't even know what SHOULD work so I can't file any bug reports.

You shouldn't need to touch xorg.conf to do that; nvidia-settings is perfectly capable of enabling/disabling/messing with additional monitors on the fly.

That said, it's a bit different to the rest of what's being discussed here; nvidia's driver requires these special tools to get anything interesting done; with a driver that supported XRandR 1.2 you'd just fire up System->Preferences->Screen Resolution and go on your merry way.

---

### Post by jocko on 2008-11-17
> **RAOF said:**
> You shouldn't need to touch xorg.conf to do that; nvidia-settings is perfectly capable of enabling/disabling/messing with additional monitors on the fly.

Not really... it's capable of detecting whatever you plug in, but to actually use it you need to restart the x server, which means you need to make sure to save the new monitor/tv/projector in xorg.conf...

---

### Post by RAOF on 2008-11-17
> **jocko said:**
> Not really... it's capable of detecting whatever you plug in, but to actually use it you need to restart the x server, which means you need to make sure to save the new monitor/tv/projector in xorg.conf...

News to me.  I happily plug and unplug monitors, change their positions, enable and disable them with nvidia-settings without restarting X.

Maybe you need to enable dynamic TwinView in your xorg.conf?  "nvidia-xconfig --twinview" should do that for you.

---

### Post by autocrosser on 2008-11-17
Just a note: From xorg-request-list--- 

On Fri, Nov 14, 2008 at 01:13:16PM -0800, Keith Packard wrote:[INDENT]> I volunteered to manage an X server 1.6 release, tentatively scheduled
> for the end of the year (yes, this year, 2008). This release will
> include DRI2 and RandR 1.3 support. I'd like to know how much of the 
> new Xinput stuff will be ready in time.
[/INDENT]

---

### Post by jocko on 2008-11-17
> **RAOF said:**
> News to me.  I happily plug and unplug monitors, change their positions, enable and disable them with nvidia-settings without restarting X.

Maybe you need to enable dynamic TwinView in your xorg.conf?  "nvidia-xconfig --twinview" should do that for you.
Ahh.. ok that's why. I have twinwiew disabled, as it causes my display to flicker (wrong refresh rate) and I like to run my tv as a separate screen to be able to see movies on the tv...

---

