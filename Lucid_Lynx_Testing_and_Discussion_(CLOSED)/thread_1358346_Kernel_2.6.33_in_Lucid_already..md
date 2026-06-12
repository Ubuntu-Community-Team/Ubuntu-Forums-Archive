---
title: "Kernel 2.6.33 in Lucid already."
date: 2009-12-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lnas90 on 2009-12-18
Staff would suggest that the 2.6.33 kernel included in ubuntu is lucid, fortunately it includes many improvements that I think is very useful for an LTS version.
We must remember that an lts version is not just for servers, are such that they are best placed to come pre-installed on PCs and laptops sold by Dell.
As I am Brazilian and I do not speak very well English, I would ask for a user who has knowledge of cause is to appeal to the devs.
If you need to think it would be worth delaying the launch by at least 1 month, as was done with the first version lts, known for its unusual stability.
Recalling that the first rc 2.6.33 was released today:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33-rc1/")
Well folks what do you think?

---

### Post by anders_c_ on 2009-12-18
I think they have already decided to stick with .32
Though i guess a lot of nvidia users would love to see that kernel in lucid.

---

### Post by lnas90 on 2009-12-18
[IMG]http://www.google.com.br/images/cleardot.gif[/IMG]Mostrar romanização
But if we put in the balance I think it would be worth, I think no one would bother to wait 1 month more to have a lucid with kernel 2.6.33.
It would be good for everyone, with the visibility of ubuntu would be much easier to fix the bugs until the final version of the kernel.
Not only for nvidia user, the ATI will also benefit greatly from the new kernel and the 'new' drives.

---

### Post by jpeddicord on 2009-12-18
You had me thinking .33 was in use in Lucid already. I'm indifferent on the situation; everything is working great here so I'd more likely prefer .32.

I don't think the developers would be convinced of a kernel change; read somewhere that they were pretty set on .32. But it has been done before...

---

### Post by Regenweald on 2009-12-18
If -33 proves itself to be *very* stable within the next month, I think a late inclusion will happen

---

### Post by xir_ on 2009-12-18
there is of course the option of features being back ported.

Do you have anything particular in mind?

---

### Post by gnomeuser on 2009-12-18
There has been talk of providing backported newer kernels for Lucid on supported hardware. Regardless .32 is going to be in the next Red Hat Enterprise product, and is generally going to be well supported as the foundation of a long term kernel. We can rely on pulling patches and backports from amongst others Red Hat for up to 10 years on this kernel.

.33 has some really nice things but so will .34. Most importantly probably is the removal of the need to backport Nouveau but Red Hat are likely to also add this feature to their kernel as it has been tested in Fedora for a while now.

I would really like to recommend going with .33 but .32 seems like the obvious choice here for stability, we can backport selected features for release and then move to .33 on selected platforms as they become regression "free".

---

### Post by ruik on 2009-12-18
Btw, anyone tried .33 with Lucid yet?

---

### Post by zika on 2009-12-18
> **ruik said:**
> Btw, anyone tried .33 with Lucid yet?Yes. It works by default with non-KMS. I had to force KMS (radeon.modeset=1) and I had to provide (ATI HD3650) R600_rlc.bin in /lib/firmware/radeon or in /lib/firmware/2.6.32-999-generic/firmware/radeon to get gdm working with KMS. It runs smoothly and, seemingly, more smooth than last 2.6.32-999...

---

### Post by plun on 2009-12-18
Yup, installed 386 version on a Dell Laptop, X300 ATI graphic.

Seems to work just fine, I have not checked my logs yet for trouble...:)

This RC1-kernel is "edge-stuff" so be careful out there...:lolflag:

PS 2.6.32-9 is also available for Lucid now.....DS

---

### Post by barisurum on 2009-12-18
I think its worth the risk. Considering windows 7 has many advanced features for gamers, going with the .33 should be a better approach as it has many improvements on the OSS video driver side.

---

### Post by plun on 2009-12-18
What is Windows 7 compared to a Lucid Lynx loaded with a new kernel  ?...:)

This kernel is the fastest I have tested.

Everything is "snappy and sharp" including sound !

---

### Post by sports fan Matt on 2009-12-18
ok, 2 quick questions: Has this new kernel been released yet?  Im not seeing it.
and 2: How can I check via terminal what kernel I have?

---

### Post by plun on 2009-12-18
> **sox fan Matt said:**
> ok, 2 quick questions: Has this new kernel been released yet?  Im not seeing it.
and 2: How can I check via terminal what kernel I have?

This kernel is released "upstream" at kernel.org and also within Ubuntu Mainline.

Its a RC version so be careful !

uname -a checks your kernel

```
plun@plun-laptop:~$ uname -a
Linux plun-laptop 2.6.33-020633rc1-generic #020633rc1 SMP Fri Dec 18 10:57:26 UTC 2009 i686 GNU/Linux
```

---

### Post by zika on 2009-12-18
> **plun said:**
> What is Windows 7 compared to a Lucid Lynx loaded with a new kernel  ?...:)
This kernel is the fastest I have tested.
Everything is "snappy and sharp" including sound !I'm glad that I'm not the only one with such impression. It is very promising ...

---

### Post by plun on 2009-12-18
Yup, but Lucid will be running on a 2.6.32 kernel according to mailing list.....


Phoronix about 2.6.33
[http://www.phoronix.com/scan.php?page=news_item&px=NzgyMQ](http://www.phoronix.com/scan.php?page=news_item&px=NzgyMQ)




--

---

### Post by zika on 2009-12-18
> **plun said:**
> Yup, but Lucid will be running on a 2.6.32 kernel according to mailing list.....
Phoronix about 2.6.33
[http://www.phoronix.com/scan.php?page=news_item&px=NzgyMQ](http://www.phoronix.com/scan.php?page=news_item&px=NzgyMQ)
--As long as we can "improve" it with using newer kernel it, really, doesn't matter for me. I understand that people developing Lucid have greater knowledge and wider scope than I do, so it's their decision, having in mind stability for the wast of future users of Lucid. I use the official kernel as a safety net for my "edgers" use of Lucid ...

---

### Post by plun on 2009-12-18
> **zika said:**
>  I understand that people developing Lucid have greater knowledge and wider scope than I do, so it's their decision, having in mind stability for the wast of future users of Lucid. I use the official kernel as a safety net for my "edgers" use of Lucid ...

Well, I dont understand.....:)

Ubuntu is often stubborn on totally wrong issues which just make Ubuntu buggy....  must be a UDS-lock...

---

### Post by plun on 2009-12-19
Alsa is also out with a new version...

[http://www.phoronix.com/scan.php?page=news_item&px=NzgxNA](http://www.phoronix.com/scan.php?page=news_item&px=NzgxNA)

I don't know if this kernel already have this code....:confused:

Running just fine after some more tests today...:)

---

### Post by ruik on 2009-12-19
Anyone got it working with nvidia drivers (195.22)?

---

### Post by paul_in_london on 2009-12-19
> **ruik said:**
> Anyone got it working with nvidia drivers (195.22)?

Having problems with that myself!

---

### Post by ronacc on 2009-12-19
same here, no nvidia driver in .33 right now .

---

### Post by sgosnell on 2009-12-19
It's not hard to upgrade to a newer kernel.  I'm running the 2.6.32 kernel in Jaunty with no problems.  I do keep at least a couple of older kernels that I know run without problems installed for a fallback.  It's easy enough to boot to another kernel with Esc.  It's not for everyone, of course, but I've been upgrading to the latest kernel regularly for some time, with mostly no ill effects.  I've had to remove a kernel here and there because it wouldn't boot or work correctly, but there were never any lasting effects.

---

### Post by dino99 on 2009-12-20
> **ruik said:**
> Anyone got it working with nvidia drivers (195.22)?

nvidia 195.22 failed here with this kernel 33

Is somebody have modified "dkms_autoinstaller" as "gnomeuser" have teach to do ? If so, where to include his code & is this code complete ?

gnomeuser code:

 Re: The latest gdm updates broke nvidia 195.22!
actually this is very likely a dkms problem.

The offending part of /usr/lib/dkms/dkms_installer is here:


if [ -L /vmlinuz -a -e /vmlinuz ]
then <--- missing
linktarget="$(basename "$(readlink /vmlinuz)")"

Insert that and it works

---

### Post by Globo on 2009-12-20
Strange expirience with 2.6.33.
On the other hand, it feels better than 2.6.32 (repsonses are faster, better network performance), but on the other the FS performance is still worse than in 2.6.30 and even in 2.6.31.

---

### Post by zika on 2009-12-20
I like it very much but I do not like ```
[    2.057845] wait-for-root[271]: segfault at 0 ip 00007f80f10da7c2 sp 00007fff87fd7958 error 4 in libc.so.6[7f80f105b000+166000]
```that I get ...

---

### Post by plun on 2009-12-20
About patching the nVidia driver...

[http://www.nvnews.net/vbulletin/showthread.php?t=142794](http://www.nvnews.net/vbulletin/showthread.php?t=142794)

Mandriva packager solution in message 5.


Principles for patching a driver:
[http://www.nvnews.net/vbulletin/showthread.php?t=110088](http://www.nvnews.net/vbulletin/showthread.php?t=110088)


ATI R600/700 GPUs is discussed within this thread:
[http://www.phoronix.com/forums/showthread.php?t=21034](http://www.phoronix.com/forums/showthread.php?t=21034)


(I am not running Lucid on my nvidia-box for the moment so I cannot verify this)

--

---

### Post by dino99 on 2009-12-20
Thanks Plun

hard time with nvidia & new kernel / new xorg

---

### Post by zika on 2009-12-20
> **Globo said:**
> Strange expirience with 2.6.33.
On the other hand, it feels better than 2.6.32 **(repsonses are faster, better network performance)**, but on the other the FS performance is still worse than in 2.6.30 and even in 2.6.31.I'm glad I'm not the only one having this feeling. I thought it was placebo, but after some measurement, it is not. The only time I had better graphic speed was at the very beginning of Lucid testing with xorg-edgers ... But I'm fine with the state now. The only thing is that segfault kind-of worries me ...

---

### Post by Merk42 on 2009-12-20
Why/where/when has it been decided Lucid would use .32 when the Kernel freeze isn't until March 11th?
...or do I totally not understand Kernels?

---

### Post by Gtklocker on 2009-12-20
> **plun said:**
> About patching the nVidia driver...

[http://www.nvnews.net/vbulletin/showthread.php?t=142794](http://www.nvnews.net/vbulletin/showthread.php?t=142794)

Mandriva packager solution in message 5.


Principles for patching a driver:
[http://www.nvnews.net/vbulletin/showthread.php?t=110088](http://www.nvnews.net/vbulletin/showthread.php?t=110088)


ATI R600/700 GPUs is discussed within this thread:
[http://www.phoronix.com/forums/showthread.php?t=21034](http://www.phoronix.com/forums/showthread.php?t=21034)


(I am not running Lucid on my nvidia-box for the moment so I cannot verify this)

--

> **dino99 said:**
> Thanks Plun

hard time with nvidia & new kernel / new xorg

Ok, but there must be some emphasis on nVidia drivers.

I'm not going to mess up with patches. If devs want sooooo new kernel, they should do something (prepatch nvidia drivers, take the newest nvidia drivers to the repository - whatever).

I'm complaining so much, because, nvidia drivers, have excellent performance in standard conditions.

Keep up the good work devs :)

---

### Post by plun on 2009-12-20
> **Merk42 said:**
> Why/where/when has it been decided Lucid would use .32 when the Kernel freeze isn't until March 11th?
...or do I totally not understand Kernels?

Phoronix article about this:

[http://www.phoronix.com/scan.php?page=news_item&px=Nzc3MA](http://www.phoronix.com/scan.php?page=news_item&px=Nzc3MA)

> The primary decision for the kernel team at UDS is to choose the
base kernel version for the release.  **For Lucid this will be 2.6.32**.
This version has just released providing the maximum stabalisation time,
it also is expected to be the kernel of choice for long term releases from other distributions.  We will also keep ext4 as our primary filesystem.

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-December/029653.html)




Maybe its more important to fix all trouble with "dirty drivers" and apps which the majority uses then to stick with a kernel.....:)

---

### Post by autocrosser on 2009-12-20
I just checked & that line is corrected as gnome-user talks about.....I'm not really savy about dkms, but I'll poke about & see what I can find...would be nice to have the auto-installer work on it......code is on line 72


> **dino99 said:**
> nvidia 195.22 failed here with this kernel 33

Is somebody have modified "dkms_autoinstaller" as "gnomeuser" have teach to do ? If so, where to include his code & is this code complete ?

gnomeuser code:

 Re: The latest gdm updates broke nvidia 195.22!
actually this is very likely a dkms problem.

The offending part of /usr/lib/dkms/dkms_installer is here:


if [ -L /vmlinuz -a -e /vmlinuz ]
then <--- missing
linktarget="$(basename "$(readlink /vmlinuz)")"

Insert that and it works

---

### Post by ruik on 2009-12-21
.33 seems to be faster here too. I'm not sure if it's related to the kernel itself or some other changes I did but after upgrading to .33rc1 I get almost 2x FPS in glxgears with nouveau (I know, glxgears is not a benchmark tool, but still..).

---

### Post by Zatara214 on 2009-12-21
So confirmed that the Nouveau drivers are faster than the nv drivers?  Thank the lord, I was getting so sick of them.

---

### Post by ruik on 2009-12-21
Oh nouveau worked just fine over here. Didn't try any 3D though. :)

---

### Post by plun on 2009-12-21
> **ruik said:**
> Oh nouveau worked just fine over here. Didn't try any 3D though. :)

Noway that I am going to test the Nouveau-crap....:tongue:

---

### Post by ruik on 2009-12-21
What makes it crap? KMS worked fine and 2D performance was good. It surely is still under heavy development but is making great progress. I guess how well it works just depends on your GPU..

---

### Post by plun on 2009-12-21
> **ruik said:**
> What makes it crap? KMS worked fine and 2D performance was good. It surely is still under heavy development but is making great progress. I guess how well it works just depends on your GPU..

Well for me Nouveau is religious software crap which doesn't work as I want !!! 

Nothing can change this  !

I don't want to play Duke Nukem now !

---

### Post by gnomeuser on 2009-12-21
> **ruik said:**
> What makes it crap? KMS worked fine and 2D performance was good. It surely is still under heavy development but is making great progress. I guess how well it works just depends on your GPU..

Nouveau is a magnificent piece of engineering, I have even heard positive reports of the gallium3D driver working well for a, limited, number of cards.

I have no doubt that Nouveau will be fully sufficient for most users soon. The progress is absolutely amazing.

---

### Post by gnomeuser on 2009-12-21
> **plun said:**
> Well for me Nouveau is religious software crap which doesn't work as I want !!! 


[Practicality not religion](http://davidnielsen.wordpress.com/2009/12/16/the-importance-of-open-drivers-and-openness-in-general/)

> 
Nothing can change this  !


You may want to look up the meaning of the term dogma. This is not a sentence that could be formulated by an informed open skeptical mind.

> 
I don't want to play Duke Nukem now !

Who is asking you to.. how did Duke even get into this?

---

### Post by Globo on 2009-12-21
> **plun said:**
> Well for me Nouveau is religious software crap which doesn't work as I want !!! 

Nothing can change this  !

I don't want to play Duke Nukem now !
Agree with you, nouveau is so slow compared to proprietary driver: no proper cairo and font rendering acceleration.

---

### Post by xir_ on 2009-12-21
> **Zatara214 said:**
> So confirmed that the Nouveau drivers are faster than the nv drivers?  Thank the lord, I was getting so sick of them.

the nv drivers are just designed to do the bare minimum whilst you install the binary blob in fact they are written by nvidia.

nouveau is the community deciding to backward engineer the brinary blob so that we get a real modern open source driver.

Nouveau drivers are already far more advanced than nv

---

### Post by PGHammer on 2009-12-21
> **Globo said:**
> Agree with you, nouveau is so slow compared to proprietary driver: no proper cairo and font rendering acceleration.

Which has generally been the case; poroprietary drivers will *always* wax FOSS drivers no matter how much the Richard Stallmans of the planet may hate that factoid (it's just as true outside of graphics, as the madwifi driver folks can tell you, as can those of us in the X-Fi FOSS userbase).

FOSS is catching up (and on the 2D side, just plain working miracles, as performance of the ATI 2D driver core for both 2.6.31 and 2.6.32 branches is proving; I actually dared to install 2.6.33rc1 in Lucid alpha 1 and have the fastest 2D performance I've ever seen); however, it likely will never catch up to proprietary drivers, as it will never be in the IHV's best interest to reveal *all* the tricks.

(To get an idea of how good the 2D driver performance actually is, consider that the 2D driver core is common across every AMD X.org server hardware branch from R300 (original Radeon) up; in fact, because of 3D performance issues with radeonhd unique to HD3450, I've used the radeon 2D driver, not the radeonhd driver, all the way back to Intrepid Ibex beta 2.  Despite the commonality, for some odd reason, the 2D side is more fleshed-out, and faster, in the radeon driver as opposed to the radeonhd driver, as far as HD34xx is concerned; I have no idea if this is unique to HD34xx or not, but if not, it is rather troubling.)

I'm normally no fan of beta kernels, especially ones that the distribution devs plan to skip; however, because of the performance gains over their *chosen* kernel (which is my backstop), why do I feel I was promised Harry Potter only to get Neville Longbottom?

---

### Post by RAOF on 2009-12-21
> **Globo said:**
> Agree with you, nouveau is so slow compared to proprietary driver: no proper cairo and font rendering acceleration.

You must be using either a different Nouveau or different proprietary driver (or, I guess, a really old nvidia card, or misconfigured nouveau).  Nouveau has (for a long time) had significantly better Cairo acceleration (than any other X driver).  In fact, GNOME Do and Docky have *work-arounds* for poor nVidia binary driver acceleration.

It's possible that you're thinking of the "nv" driver, which is the default nvidia driver?  Yes, that's slow, because nvidia don't invest a lot of effort into it.

---

### Post by xir_ on 2009-12-21
> **gnomeuser said:**
> Nouveau is a magnificent piece of engineering, I have even heard positive reports of the gallium3D driver working well for a, limited, number of cards.

I have no doubt that Nouveau will be fully sufficient for most users soon. The progress is absolutely amazing.


i seem to find myself agreeing you more often than not on these forums. 

people seem to think that the goal of nouveau is to beat the binary, its not. Instead it tries to offer a good open source driver with a decent feature set. 

In a couple years and the binary will not be able to keep up with nouveau in terms of the ever changing linux environment, but the things that the binary does it will be faster at. Remember guys this is the first pull of the driver into the mainline and its no got commercial support like the amd os driver.

---

### Post by xir_ on 2009-12-21
> **PGHammer said:**
> Which has generally been the case; poroprietary drivers will *always* wax FOSS drivers no matter how much the Richard Stallmans of the planet may hate that factoid (it's just as true outside of graphics, as the madwifi driver folks can tell you, as can those of us in the X-Fi FOSS userbase).

FOSS is catching up (and on the 2D side, just plain working miracles, as performance of the ATI 2D driver core for both 2.6.31 and 2.6.32 branches is proving; I actually dared to install 2.6.33rc1 in Lucid alpha 1 and have the fastest 2D performance I've ever seen); however, it likely will never catch up to proprietary drivers, as it will never be in the IHV's best interest to reveal *all* the tricks.

(To get an idea of how good the 2D driver performance actually is, consider that the 2D driver core is common across every AMD X.org server hardware branch from R300 (original Radeon) up; in fact, because of 3D performance issues with radeonhd unique to HD3450, I've used the radeon 2D driver, not the radeonhd driver, all the way back to Intrepid Ibex beta 2.  Despite the commonality, for some odd reason, the 2D side is more fleshed-out, and faster, in the radeon driver as opposed to the radeonhd driver, as far as HD34xx is concerned; I have no idea if this is unique to HD34xx or not, but if not, it is rather troubling.)

I'm normally no fan of beta kernels, especially ones that the distribution devs plan to skip; however, because of the performance gains over their *chosen* kernel (which is my backstop), why do I feel I was promised Harry Potter only to get Neville Longbottom?


theres and interesting phronix article showing how the new amd os driver is faster at 2d than the AMD binary at certain tasks.

[ http://www.phoronix.com/scan.php?page=article&item=amd_fglrx_radeon_2d&num=1]("http://www.phoronix.com/scan.php?page=article&item=amd_fglrx_radeon_2d&num=1")

---

### Post by Globo on 2009-12-22
> **RAOF said:**
> You must be using either a different Nouveau or different proprietary driver (or, I guess, a really old nvidia card, or misconfigured nouveau).  Nouveau has (for a long time) had significantly better Cairo acceleration (than any other X driver).  In fact, GNOME Do and Docky have *work-arounds* for poor nVidia binary driver acceleration.

It's possible that you're thinking of the "nv" driver, which is the default nvidia driver?  Yes, that's slow, because nvidia don't invest a lot of effort into it.
I'm using 8800gtx and 2.6.30 kernel + 185.18 proprietary driver. Tried 2.6.33 with thei nouveau, and inspite of the fact everything is faster exclude network through my l2tp/pptp (it has been slowed down since 2.6.31 and still broken), EXT4 performance (but this regression can be avoided) and 2D rendering performance which is horrible with nouveau. I don't care about wrongly done gnome-do and docky, especially after the fact gtkperf proves 2.6.30+gtk2.18.3+185.18 is much faster than 2.6.33 + gtk2.18.3+nouveau.
LOL. 2.6.33 feels faster, but it's slower actually: it responds faster, but poor PPP kernel support, slow EXT4 and slow nouveau performance did it slower than 2.6.30 and even 2.6.31. Although 33 is faster than 32.

BTW, you must be missed something, nouveau is only superior over poor NV driver. But there's no hope to catch up proprietary one, it's clear.

---

### Post by xir_ on 2009-12-22
> **Globo said:**
> I'm using 8800gtx and 2.6.30 kernel + 185.18 proprietary driver. Tried 2.6.33 with thei nouveau, and inspite of the fact everything is faster exclude network through my l2tp/pptp (it has been slowed down since 2.6.31 and still broken), EXT4 performance (but this regression can be avoided) and 2D rendering performance which is horrible with nouveau. I don't care about wrongly done gnome-do and docky, especially after the fact gtkperf proves 2.6.30+gtk2.18.3+185.18 is much faster than 2.6.33 + gtk2.18.3+nouveau.
LOL. 2.6.33 feels faster, but it's slower actually: it responds faster, but poor PPP kernel support, slow EXT4 and slow nouveau performance did it slower than 2.6.30 and even 2.6.31. Although 33 is faster than 32.

BTW, you must be missed something, nouveau is only superior over poor NV driver. But there's no hope to catch up proprietary one, it's clear.

Theirs no aim to do that, but the question will be about what is supported and seeing as the binary is mostly designed around windows there will be more thing that wont work in the long run.

---

### Post by ruik on 2009-12-22
Yeah, nouveau already supports features that the official drivers don't and probably never will support. Oh and, if someone's interested in trying nouveau, please make sure to try the very latest stuff. The xorg-edgers PPA is good for that.

> nouveau is the community deciding to backward engineer the brinary blob so that we get a real modern open source driver.

Actually they're not touching the binary blob at all.

---

### Post by xebian on 2009-12-22
The 33-rc1 from kernel-mainline won't compile the NV 190-53 driver.  Keeps complaining of not able to determine the kernel version?  Any idea/patch?

---

### Post by ruik on 2009-12-22
> **xebian said:**
> The 33-rc1 from kernel-mainline won't compile the NV 190-53 driver.  Keeps complaining of not able to determine the kernel version?  Any idea/patch?

[http://www.nvnews.net/vbulletin/showthread.php?t=142794](http://www.nvnews.net/vbulletin/showthread.php?t=142794)

---

### Post by xebian on 2009-12-22
Thanks ruik.  :popcorn:

---

### Post by RAOF on 2009-12-22
> **Globo said:**
> I'm using 8800gtx and 2.6.30 kernel + 185.18 proprietary driver. Tried 2.6.33 with thei nouveau, and inspite of the fact everything is faster exclude network through my l2tp/pptp (it has been slowed down since 2.6.31 and still broken), EXT4 performance (but this regression can be avoided) and 2D rendering performance which is horrible with nouveau. I don't care about wrongly done gnome-do and docky, especially after the fact gtkperf proves 2.6.30+gtk2.18.3+185.18 is much faster than 2.6.33 + gtk2.18.3+nouveau.
...

I think this comes under "mis-configured nouveau driver"; I'm fairly sure the branch merged to Linus' tree didn't include the ctxprog firmware-ish stuff.  Without that, you get *no* acceleration, so, yeah, it doesn't surprise me that the binary driver is faster than no acceleration.

Nouveau's acceleration does have more caveats than the binary driver; you need the firmware, and for nv5x+ you need to either be running a recent X server or have a compositing manager running.

gtkperf is also not a wonderful benchmark.  It's not as bad as glxgears, but it doesn't really replicate what applications actually *do*.

---

### Post by plun on 2009-12-23
Alsa 1.0.22 can now easily be testad for 2.6.33 from Thefirstm ppa

[https://launchpad.net/~thefirstm/+archive/lucid](https://launchpad.net/~thefirstm/+archive/lucid)

(he also got latest nVidia driver but its probably broken with this kernel, patch earlier posted)

---

### Post by zika on 2009-12-23
> **plun said:**
> Alsa 1.0.22 can now easily be testad for 2.6.33 from Thefirstm ppa

[https://launchpad.net/~thefirstm/+archive/lucid](https://launchpad.net/~thefirstm/+archive/lucid)

(he also got latest nVidia driver but its probably broken with this kernel, patch earlier posted)Seems that thefirstm ppa does not have amd_64 packages? I wanted to try alsa 1.0.22 but... No luck.

---

### Post by plun on 2009-12-23
> **zika said:**
> Seems that thefirstm ppa does not have amd_64 packages? I wanted to try alsa 1.0.22 but... No luck.

Yup...checked package details and there is only a 32 bit driver....

>  alsa-driver - 1.0.22-0ubuntu0~ppa0   	 (changesfile)   	2009-12-20  	Published  	Lucid  	Sound  	 All builds were built successfully.
Publishing details

    * Published on 2009-12-20
    * Copied from ubuntu lucid in Experimental

Changelog

alsa-driver (1.0.22-0ubuntu0~ppa0) lucid; urgency=low

  * New upstream release.
 -- Michael Marley <email address hidden>   Sun, 20 Dec 2009 09:37:58 -0500

Available diffs

    * 1.0.21+dfsg-3ubuntu1 (in Ubuntu) to 1.0.22-0ubuntu0~ppa0 (722.6 KiB)

[B]Builds

    * [FULLYBUILT] i386[/B]

Built packages

    * alsa-base ALSA driver configuration files

    * alsa-source ALSA driver sources

    * linux-sound-base base package for ALSA and OSS sound systems

Package files

    * alsa-base_1.0.22-0ubuntu0~ppa0_all.deb (265.3 KiB)
    * alsa-driver_1.0.22-0ubuntu0~ppa0.dsc (1.3 KiB)
    * alsa-driver_1.0.22-0ubuntu0~ppa0.tar.gz (4.2 MiB)
    * alsa-source_1.0.22-0ubuntu0~ppa0_all.deb (3.4 MiB)
    * linux-sound-base_1.0.22-0ubuntu0~ppa0_all.deb (32.6 KiB)



---

### Post by caryb on 2009-12-23
Not wanting to be a grumpy old man (am not old) but I feel sometimes the topic titles could be a bit more accurate, because a application is available in a PPA does not make it available in Ubuntu. I like to test the current version & adding PPA's negates testing in the current version.


Cary

---

### Post by Jordanwb on 2009-12-23
I got Lucid on my laptop. Can I install a .33 kernel alongside a .32 kernel? If so, what repo do I need to add?

---

### Post by caryb on 2009-12-23
If I search 2.6.33 in synaptic I get zippo!


Cary

BTW I have everything except the source files enabled.

---

### Post by darco on 2009-12-23
Here is a link to the mainline kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/)



darco

---

### Post by sgosnell on 2009-12-23
You don't need to add a repo, nor will Synaptic find it.  Use the link above for the Ubuntu mainline kernel repository.  You can download the image file, install it with gdebi, and reboot.  If it won't boot, reboot and press Esc when the boot menu comes up, you will have to be fairly fast at it, depending on how long your timeout is set to, I think the default is 5 seconds.  You should get a boot menu allowing you to select which kernel to boot, and you can select the previous kernel which booted and ran.  I have the .33rc1 installed, and so far it work fine on 9.04.  I've been running .32 for some time, and .30 before that.  .31 didn't boot on my EEE PC, so I never really ran it, although I did install it for awhile.  If you want to get rid of the .33 kernel, boot into another kernel and use Synaptic to remove it.

---

### Post by darco on 2009-12-23
Well, I had nothing better to do today since I finished my x-mas shopping yesterday....
I went ahead and installed this kernel along w/nvidia 195.22 and so far so good. 
Cant see much difference, tempted to try nouveau....


darco

---

### Post by vade on 2009-12-23
Radeon KMS doesn't seem to be working with this 2.6.33-rc1, at least for rv770. Mode isn't set during boot until X, and when X sets(?) the mode, booting hangs. Keyboard responds... I switch vconsole, the machine freezes to sysrq-reisub'able state.

And I had to radeon.modeset=1. Perhaps it's disabled by default for a reason. :P

---

### Post by Jordanwb on 2009-12-23
I tried to install the linux headers but the compiling of my broadcom chip's driver failed. A bug report has been filed.

---

### Post by BwackNinja on 2009-12-24
For me it seems to work well for a while, but soon just locks up the system.

---

### Post by plun on 2009-12-25
RC2 is out with a christmas message....:P

> Date	Thu, 24 Dec 2009 14:00:24 -0800 (PST)
From	Linus Torvalds <>
Subject	Linux 2.6.33-rc2 - Merry Christmas ...



.. or wahetever it is you'll be celebrating today/tomorrow.

And if you aren't celebrating anything at all, but instead sitting in your 
dark basement feeling lonely and bored, you can at least try out the 
latest -rc kernel. Because it's better than moping around doing nothing.

And if you _are_ celebrating, but are having a bit of an overload of ham 
(or are getting fed up with losing all your clothes in strip dreidel and 
having people point and snigger at you, if that's what gets you through 
the holidays), take a break, compile a kernel, and try it out for size. 

Because while your pants may not fit you for the next month, the new 
kernel might just fit your computer perfectly.

The dirstat says it all: mostly drivers (much of it staging updates, 
especially as nouveau also counts as staging even if it's not physically 
there). But a smattering of changes all over (scheduler, vfs, arch, kfifo 
etc):

<Snip>

I'd have been happier with a smaller -rc2, but I've seen worse too, so I'm 
not going to complain. 

And now I'm off to peel potatoes. And then to eat them.

Have fun,

		Linus

 

[http://lkml.org/lkml/2009/12/24/130](http://lkml.org/lkml/2009/12/24/130)


Not seen yet at Ubuntu Mainline.....

---

### Post by plun on 2009-12-25
Ubuntu Mainline:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc2/)

Testing...:twisted:

---

### Post by rafik24 on 2009-12-26
Hi All,

I looked at this thread, i did end up here looking for a solution to get lucid working with my old ati radeon mobility X600.

 I installed 2.6.33-RC2 from source and my problem is fixed, well I'm not expecting to get 3D out of my gfx.

 This kernel makes lucid fly, it's unbelievably fast while operating and also at bootup.

 It would just be a shame not to include it in lucid final rev.

 for those willing to try:

cd /usr/src/

wget [http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.33-rc2.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.33-rc2.tar.bz2)

tar -jxvf linux-2.6.33-rc2.tar.bz2

cd linux-2.6.33-rc2

cp /boot/config-2.6.32-9-generic .config

make old config

(keep pressing enter for a start)

make bzImage

make modules

make modules_install

cp arch/i386/boot/bzImage /boot/vmlinuz-2.6.3-rc2

mkinitramfs -o /boot/initrd.img-2.6.33-rc2

apt-get install plymouth

update-grub

then give this a reboot and get amazed...

---

### Post by plun on 2009-12-26
> **rafik24 said:**
> 
 This kernel makes lucid fly, it's unbelievably fast while operating and also at bootup.

 It would just be a shame not to include it in lucid final rev.

 

Yup, this kernel is excellent....:guitar:

I also upgraded my nVidia desktop to Lucid including this kernel and the patch earlier mentioned works just fine. The nvidia installer must just write a new xorg (question during install)

[http://ubuntu-pics.de/bild/35566/screenshot_mBsq7K.png](http://ubuntu-pics.de/bild/35566/screenshot_mBsq7K.png)  

:)

---

### Post by Milos_SD on 2009-12-26
I can't get my Intel HDA ALC888 sound card to work with 2.6.33-rc and Alsa 1.0.22. It doesn't reckognize it at all (no mixers). :S

---

### Post by plun on 2009-12-26
> **Milos_SD said:**
> I can't get my Intel HDA ALC888 sound card to work with 2.6.33-rc and Alsa 1.0.22. It doesn't reckognize it at all (no mixers). :S

What gives a:

```
aplay -l
```

and a

```
alsamixer -Dhw
```

Works just fine on my Laptop

```
plun@plun-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by phillw on 2009-12-26
> **rafik24 said:**
> Hi All,

This kernel makes lucid fly, it's unbelievably fast while operating and also at bootup.

 

I'll be very, very cross if it breaks my 10.04 ;-)   Heck, what's a test area for, if not to be broken - which 10.04 resolutely refuses to do :P

```
 sudo rsync -aS /home/. /media/oldhome/.
```

Be fun to see the new rc playing on a LAMP server 

Phill.

---

### Post by phillw on 2009-12-26
With regard to post #69 .. Do i need to 
```
  apt-get install plymouth 
``` 
for 2.6.33-rc2 to work ? As I'm not running plymouth yet.
Maybe I should try plymouth on my current kernel before I change over ?

Advice saught,

Regards,

Phill.
BTW - I hope you're all having a good Christmas. We're doing well - we 'off-loaded' (oops, i mean we attended the marriage of) my Sister on Christmas Eve ;-)

---

### Post by zika on 2009-12-26
From my experience You do not need plymouth installed in order to have 2.6.33-rc2 work in Lucid. But, once You get it installed there is no way You can clean all its parts from Your system. You can remove plymouth itself but libplymouth2 is un-removable... Even though I use ATI card installing plymouth also installs libdrm-noveau1... Work in progress...

---

### Post by phillw on 2009-12-26
> **zika said:**
> From my experience You do not need plymouth installed in order to have 2.6.33-rc2 work in Lucid.

well, I'll be able to confirm that shortly

:lolflag:

Thanks,

Phill.

---

### Post by plun on 2009-12-26
> **zika said:**
> From my experience You do not need plymouth installed in order to have 2.6.33-rc2 work in Lucid.

No... the boot to login is fast...:)

If someone have time this maybe is a clue for Plymouth.
vga=XXX is obsolete and this is maybe a clue:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=539239](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=539239)

gfxpayload  :confused:

---

### Post by autocrosser on 2009-12-26
Anyone got this working with the DKMS installer??  I've tried playing with it, but no go :(

The suggested mod from earlier in the posts has already been added into dkms_autoinstaller---so I need some fresh ideas......

---

### Post by phillw on 2009-12-26
>  cp /boot/config-2.6.32-9-generic .config

gives ...

```
cp: cannot stat `/boot/config-2.6.32-9-generic': No such file or directory

```

Hardly surprising  as it is not in /boot

Anyone got a set of instructions ? :confused:

Phill.

---

### Post by plun on 2009-12-26
> **autocrosser said:**
> Anyone got this working with the DKMS installer??  I've tried playing with it, but no go :(

The suggested mod from earlier in the posts has already been added into dkms_autoinstaller---so I need some fresh ideas......

No I removed DKMS and installed the patched version the old-fashioned way.

The old-fashioned way installing a nvidia driver can be seen in the Cafe.[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Patching the Debian/Ubuntu way:
(Below is the 32 bit way)

```
sudo sh NVIDIA-Linux-x86-195.30-pkg1.run --apply-patch nvidia-2.6.33.patch.txt
```

Install, easiest from recovery.
```
sudo sh NVIDIA-Linux-x86-195.30-pkg1-custom.run
```


Works just fine....:guitar:

---

### Post by paul_in_london on 2009-12-26
> **plun said:**
> 
Patching the Debian/Ubuntu way:
(Below is the 32 bit way)

```
sudo sh NVIDIA-Linux-x86-195.30-pkg1.run --apply-patch nvidia-2.6.33.patch.txt
```

Install, easiest from recovery.
```
sudo sh NVIDIA-Linux-x86-195.30-pkg1-custom.run
```

Yep, that's what I did and now nvidia 195.30 (32 bit) works for me with 2.6.33-020633rc2-generic

---

### Post by Milos_SD on 2009-12-26
> **plun said:**
> What gives a:

```
aplay -l
```

and a

```
alsamixer -Dhw
```

Works just fine on my Laptop

```
plun@plun-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


aplay -l reports just this:

```
**** List of PLAYBACK Hardware Devices ****
```
And the other command I didn't try. But in syslog it says something about hda_codec can't create mixers or something like that.

---

### Post by plun on 2009-12-26
> **Milos_SD said:**
> aplay -l reports just this:

```
**** List of PLAYBACK Hardware Devices ****
```
And the other command I didn't try. But in syslog it says something about hda_codec can't create mixers or something like that.

OK...checked Google and found this

[http://www.gitorious.org/opensuse/kernel-source/commit/63f02cf262f813b9fc10b0b3dcb27a8d017ce574.patch](http://www.gitorious.org/opensuse/kernel-source/commit/63f02cf262f813b9fc10b0b3dcb27a8d017ce574.patch)

Seems to have been trouble with this card.

Anyway, I am using this ppa for Alsa 1.0.22 (only 32 bit)
[https://launchpad.net/~thefirstm/+archive/lucid](https://launchpad.net/~thefirstm/+archive/lucid)

Alsa-lib and plugins are also upgraded to 1.0.22 within Lucid, but not the drivers yet.

---

### Post by phillw on 2009-12-26
> **phillw said:**
> gives ...

```
cp: cannot stat `/boot/config-2.6.32-9-generic': No such file or directory

```Hardly surprising  as it is not in /boot

Anyone got a set of instructions ? :confused:

Phill.

Oh, go on, I've the 64MB download in and unzipped....

PERRRLEEEEEEAAASE :-)

I'd love to try it out :lolflag:

Phill.

---

### Post by autocrosser on 2009-12-26
Yes--I've done it that way in the past---I'm just bloddy lazy right now & wanted a no-brainer way to do it---been too busy hacking my "new" phone--a [new-old-stock] HTC 411 (Star trek Cingular 3125) flip-smart phone--got a newish version of WM 6.1 on it & have been talking to the Wing mobile guys about installing Android on it :)  --- [http://sourceforge.net/apps/trac/wing-linux/wiki](http://sourceforge.net/apps/trac/wing-linux/wiki)  Lots of fun!!!!  Passing time until things get "fun" here--is interesting to get touch phone stuff to work on a button-only phone & it's linux instead of windoze Now if I could only "really" touch-dial a number instead of command-line it.........

> **plun said:**
> No I removed DKMS and installed the patched version the old-fashioned way.

The old-fashioned way installing a nvidia driver can be seen in the Cafe.[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Patching the Debian/Ubuntu way:
(Below is the 32 bit way)

```
sudo sh NVIDIA-Linux-x86-195.30-pkg1.run --apply-patch nvidia-2.6.33.patch.txt
```Install, easiest from recovery.
```
sudo sh NVIDIA-Linux-x86-195.30-pkg1-custom.run
```
Works just fine....:guitar:

---

### Post by plun on 2009-12-27
> **autocrosser said:**
> Yes--I've done it that way in the past---I'm just bloddy lazy right now & wanted a no-brainer way to do it---been too busy hacking my "new" phone--a [new-old-stock] HTC 411 (Star trek Cingular 3125) flip-smart phone--got a newish version of WM 6.1 on it & have been talking to the Wing mobile guys about installing Android on it :)  --- [http://sourceforge.net/apps/trac/wing-linux/wiki](http://sourceforge.net/apps/trac/wing-linux/wiki)  Lots of fun!!!!  Passing time until things get "fun" here--is interesting to get touch phone stuff to work on a button-only phone & it's linux instead of windoze Now if I could only "really" touch-dial a number instead of command-line it.........

OK... its boring...but I am  stubbard ):P

I bought myself a [HTC Hero]("http://ubuntu-pics.de/bild/35670/device_3jp7hU.png") and its FUN :lolflag:

And no software religious users in the Android community hacking the phone..just to do what you want without any preaching :wink:

---

### Post by descendent87 on 2009-12-27
Installing rc2 now, just noticed this message
```
  p, li { white-space: pre-wrap; }  [FONT=Monospace]Setting up linux-image-2.6.33-020633rc2-generic (2.6.33-020633rc2) ...[/FONT]
 [FONT=Monospace]Running depmod.[/FONT]
 [FONT=Monospace]update-initramfs: Generating /boot/initrd.img-2.6.33-020633rc2-generic[/FONT]
 [FONT=Monospace]W: Possible missing firmware /lib/firmware/radeon/R700_rlc.bin for module radeon[/FONT]
 [FONT=Monospace]W: Possible missing firmware /lib/firmware/radeon/R600_rlc.bin for module radeon
```[/FONT]

---

### Post by zika on 2009-12-27
> **descendent87 said:**
> Installing rc2 now, just noticed this message
```
  p, li { white-space: pre-wrap; }  [FONT=Monospace]Setting up linux-image-2.6.33-020633rc2-generic (2.6.33-020633rc2) ...[/FONT]
 [FONT=Monospace]Running depmod.[/FONT]
 [FONT=Monospace]update-initramfs: Generating /boot/initrd.img-2.6.33-020633rc2-generic[/FONT]
 [FONT=Monospace]W: Possible missing firmware /lib/firmware/radeon/R700_rlc.bin for module radeon[/FONT]
 [FONT=Monospace]W: Possible missing firmware /lib/firmware/radeon/R600_rlc.bin for module radeon
```[/FONT]Get files from [http://www.mail-archive.com/pld-cvs-commit@lists.pld-linux.org/msg204517.html](http://www.mail-archive.com/pld-cvs-commit@lists.pld-linux.org/msg204517.html). Create /lib/firmware/radeon ```
sudo mkdir /lib/firmware/radeon
```(if it doesn't exist) and put these files in it ```
sudo cp R600_rlc.bin /lib/firmware/radeon/.
sudo cp R700_rlc.bin /lib/firmware/radeon/.
```(as a root). Enjoy!

---

### Post by descendent87 on 2009-12-27
Thanks, that fixed it, can't see any difference but it's not complaining they're missing

---

### Post by zika on 2009-12-29
64-bit ALSA 1.0.22 is now available in [ppa](https://launchpad.net/~thefirstm/+archive/lucid) given above ...

---

### Post by Milos_SD on 2009-12-29
My problem with alsa 1.0.22 is fixed with new alsa release 1.0.22.1 :D

---

### Post by mickie.kext on 2009-12-29
> **gnomeuser said:**
> There has been talk of providing backported newer kernels for Lucid on supported hardware. Regardless .32 is going to be in the next Red Hat Enterprise product, and is generally going to be well supported as the foundation of a long term kernel. We can rely on pulling patches and backports from amongst others Red Hat for up to 10 years on this kernel.


How come you know that Red Hat will use .32 in RHEL6? Do you have a link to that news?

---

### Post by Eclipse. on 2009-12-29
> **mickie.kext said:**
> How come you know that Red Hat will use .32 in RHEL6? Do you have a link to that news?

[http://www.mail-archive.com/debian-kernel@lists.debian.org/msg51045.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg51045.html)

Steve Langasek is the ubuntu release manager btw.

Debian, Red Hat and Ubuntu all shipping the same kernel can only mean good things.

---

### Post by plun on 2009-12-30
> **Milos_SD said:**
> My problem with alsa 1.0.22 is fixed with new alsa release 1.0.22.1 :D

Great !  :)

About:
[http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.22.1](http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.22.1)


--

---

### Post by plun on 2009-12-30
> **Eclipse. said:**
> [url]
Debian, Red Hat and Ubuntu all shipping the same kernel can only mean good things.

Well, all three choosing the wrong kernel....:lolflag:

2.6.33 is just great !

---

### Post by Eclipse. on 2009-12-30
> **plun said:**
> Well, all three choosing the wrong kernel....:lolflag:

2.6.33 is just great !

Why is it the wrong kernel?

This idea that newer always is better seriously needs to stop, its the same every cycle.

---

### Post by zika on 2009-12-30
> **Eclipse. said:**
> Why is it the wrong kernel?

This idea that newer always is better seriously needs to stop, its the same every cycle.To the contrary. I love the fact that things (in Ubuntu and in *nix) are getting better with every new version. Very rarely I see regression. That is the point of (sic!) new version, isn't it. Newer should be better and, in almost all cases, it is. I repeat, in Ubuntu and in *nix... If You're OK with current version of stuff, OK, just do not upgrade. That choice is, always, on the menu and is Yours.

---

### Post by mickie.kext on 2009-12-30
> **Eclipse. said:**
> [http://www.mail-archive.com/debian-kernel@lists.debian.org/msg51045.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg51045.html)

Steve Langasek is the ubuntu release manager btw.

Debian, Red Hat and Ubuntu all shipping the same kernel can only mean good things.

That is indeed very good thing for Ubuntu and Linux generally. It means that less man-hour will be wasted and also means better stability. I also like that Novell is out of the picture, Linux community should completely avoid them and Ubuntu Server will eventually surpass SLES.

PS: I just did 'pacman -Su' on my Arch install and got 2.6.32-ARCH :KS

---

### Post by xebian on 2009-12-30
> **Eclipse. said:**
> Why is it the wrong kernel?

This idea that newer always is better seriously needs to stop, its the same every cycle.

We get newer version because the kernel devs are hard at work improving the previous version(s), plain and simple.

---

### Post by plun on 2009-12-31
Newest Alsa-driver with Lucid

[https://lists.ubuntu.com/archives/lucid-changes/2009-December/002472.html](https://lists.ubuntu.com/archives/lucid-changes/2009-December/002472.html)


:)

---

### Post by Souris on 2010-01-08
rc3 is out :


[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc3/)

;)

---

### Post by vishalrao on 2010-01-19
BTW see: [http://www.kroah.com/log/linux/stable-status-01-2010.html](http://www.kroah.com/log/linux/stable-status-01-2010.html)

If they (kernel and/or ubuntu devs) keep backporting stuff (including nouveau) .32 is looking to be super for a stable/robust/corporate-ready LTS :)

> I'd like to announce that the 2.6.32-stable tree is also going to be maintained as a "long-term" stable release, living for 2-3 years, like the 2.6.27 kernel is. This is because a number (i.e. more than 2) Linux distributions are basing their "enterprise" releases on this kernel version, and it will make their lives easier if I keep it alive.

Note, the viability of me keeping this tree alive for such a length of time relies on the developers working for those distros to keep me informed of patches that need to be backported and applied to it. Without their help, I will have no problem in stopping the maintenance of the tree.

---

### Post by bladerunner6 on 2010-01-19
iv installed the new rc4 from the mainline
how do i get nvidia 173 drivers to work using dkms
alternativley how do i enable noveau dtivers for my fx5200

---

### Post by stmiller on 2010-01-24
Bumping this thread with more info. (Is it just me or does it seems that Ubuntu always chooses the wrong release for a LTS?)

*****Support for the P55 i5/i7 processors was just added in the 2.6.33-rc5 kernel**.

The problem was a lack of 'turbo boost' not working on these CPUs.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036)

[http://bugzilla.kernel.org/show_bug.cgi?id=15064](http://bugzilla.kernel.org/show_bug.cgi?id=15064)

If anything, is it possible for the Ubuntu kernel team to backport this as a patch?

---

### Post by Slug71 on 2010-01-26
Has a bug/freeze exception been filed to include this Kernel? 
I know Lucid is an LTS release but that makes it even more sense to me to include the latest kernel version. After all, this kernel will be around for 2 years and supported for 3 AFAIR in Lucid. 
Thats plenty of time to sort out any kinks in this kernel down the road as long as its as stable as 2.6.32 at the moment.
It also makes sense to bring it in for the new features 2.6.33 has to offer since it will be the Kernel for the life of this LTS.

---

### Post by glasen on 2010-01-26
Kernel version 2.6.32 will be a LTS-version itself :

[http://thread.gmane.org/gmane.linux.kernel/939800](http://thread.gmane.org/gmane.linux.kernel/939800)

> I'd like to announce that the 2.6.32-stable tree is also going to be
maintained as a "long-term" stable release, living for 2-3 years, like
the 2.6.27 kernel is.  This is because a number (i.e. more than 2) Linux
distributions are basing their "enterprise" releases on this kernel
version, and it will make their lives easier if I keep it alive.

Note, the viability of me keeping this tree alive for such a length of
time relies on the developers working for those distros to keep me
informed of patches that need to be backported and applied to it.
Without their help, I will have no problem in stopping the maintenance
of the tree.


BTW, does anybody know where i can make a proposal for a kernel patch? I want to submit a patch which enables the XV-overlay-mode for all Intel 8xx-chipsets in KMS-mode. The patch is a backport from version 2.6.33 and works perfectly up to kernel version 2.6.32.6.

---

### Post by Slug71 on 2010-01-26
> **glasen said:**
> Kernel version 2.6.32 will be a LTS-version itself :

[http://thread.gmane.org/gmane.linux.kernel/939800](http://thread.gmane.org/gmane.linux.kernel/939800)



BTW, does anybody know where i can make a proposal for a kernel patch? I want to submit a patch which enables the XV-overlay-mode for all Intel 8xx-chipsets in KMS-mode. The patch is a backport from version 2.6.33 and works perfectly up to kernel version 2.6.32.6.

Thanks glasen,

The Kernel Team in launchpad might be able to help you.

---

### Post by DanaG on 2010-01-29
.config:1056:warning: symbol value 'm' invalid for FB_VESA
.config:4418:warning: override: reassigning to symbol STAGING
.config:4419:warning: override: reassigning to symbol STAGING_EXCLUDE_BUILD
.config:4420:warning: override: reassigning to symbol SND_HDA_HWDEP
.config:4421:warning: override: reassigning to symbol SND_HDA_RECONFIG


Looks like the Mainline builds don't have staging enabled; I need staging for the samsung-laptop driver.

---

### Post by Gourgi on 2010-01-30
> **DanaG said:**
> Looks like the Mainline builds don't have staging enabled; 
as far as i remember they never did

---

### Post by zaphod777 on 2010-01-30
Whats the current stability of this new kernel? I have a dell xps 1530 laptop with nvidia video card. I am wondering if I will need to do any patching or tweaking to get it working.

---

### Post by OlyPerson on 2010-01-30
> **stmiller said:**
> Bumping this thread with more info. (Is it just me or does it seems that Ubuntu always chooses the wrong release for a LTS?)

*****Support for the P55 i5/i7 processors was just added in the 2.6.33-rc5 kernel**.

The problem was a lack of 'turbo boost' not working on these CPUs.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036)

[http://bugzilla.kernel.org/show_bug.cgi?id=15064](http://bugzilla.kernel.org/show_bug.cgi?id=15064)

If anything, is it possible for the Ubuntu kernel team to backport this as a patch?

So unless the new kernel is used or i5/i7 turbo boost is enabled in the older one running a laptop with one of these with Ubuntu isn't going to be a good experience is it?

---

### Post by ranch hand on 2010-01-31
I suspect that the 2.6.33 kernel will be easy to get into 10.04 when 10.10-testing gets going.  The Ubuntu version should, I think show up very soon in that test cycle and be in the Mangy Moose (or what ever they call it) repo.

I have the Radeon HD 2400 PRO card and am hoping that it will have better support from the generic driver under 2.6.33.  I fully intend to put it on a 10.04 release install when it shows up in the repo and see.

If I do not get better support compositing will still be impossible and Gnome-Shell (supposed to be in 10.10) will not work, just as compiz does not now.

---

### Post by plun on 2010-01-31
RC6 is also out now

Linus message:
[http://lkml.org/lkml/2010/1/29/368](http://lkml.org/lkml/2010/1/29/368)

Ubuntu Mainline:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc6/)

Lucids latest kernel 2.6.32-12 (Vanilla 2.6.32.6) compared with RC6 is equal for me on my testbox, Dell Inspiron Laptop.

---

### Post by ranch hand on 2010-01-31
How the devil are you folks installing this?

I try to add the ppa to the sources list and update apt and get;
> 
W: Failed to fetch [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found


---

### Post by glasen on 2010-01-31
There is no real repo for the mainline kernels. The so-called "repo" is just a normal HTTP-Server.

So you must install them by hand. Just download the needed packages and install them with "dpkg" or "gdebi".

---

### Post by ranch hand on 2010-01-31
OK, I actually have tried this.  Got 2 packages the image and generic headers.

Image installs.  Headers return error "dependencies not met - headers not installed" or something to that effect.  I assume this is plain headers as opposed to generic headers.

The OS boots and uname -a returns 2.6.33-999 but I do not see that it is working the way it should without the rest of the "kit" installed.

This led to the attempt with the ppa, which does list the lucid repo.

---

### Post by zika on 2010-01-31
> **ranch hand said:**
> How the devil are you folks installing this?

I try to add the ppa to the sources list and update apt and get;For example, for yesterday's build, on 64-bit machine, just do```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-headers-2.6.33-999-generic_2.6.33-999.201001301150_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-headers-2.6.33-999_2.6.33-999.201001301150_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-image-2.6.33-999-generic_2.6.33-999.201001301150_amd64.deb
sudo dpkg -i linux-*.deb
```and that's it.

---

### Post by ranch hand on 2010-01-31
> **zika said:**
> For example, for yesterday's build, on 64-bit machine, just do```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-headers-2.6.33-999-generic_2.6.33-999.201001301150_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-headers-2.6.33-999_2.6.33-999.201001301150_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/linux-image-2.6.33-999-generic_2.6.33-999.201001301150_amd64.deb
sudo dpkg -i linux-*.deb
```and that's it.
Ah, well us noobs have to learn sometime.

That worked very well.  At least so it appears as I did it through chroot.

Seeing that it booted before with just the image I suspect it will be fine.  I will check on it later.

I was worried about going the dpkg route because of a warning at the bottom of the man page about debs extracted by dpkg being screwed some how.  Every thing looked great on the out put though.

Don't have firmware for a couple radeon chips but they are not mine.  Just hope mine works better.

Thanks a whole bunch.

---

### Post by darco on 2010-01-31
I've always used this simple guide in installing the mainline kernels:
[http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

The one thing that bugs me about the mainline kernels is the naming convention. It appends the 020633rc6 to the kernel name. Why does it bug me? I use conky and by adding that it lengthens my script a little more than I want. I guess compiling the kernel  would be my only choice to shorten the name? I know, I know I should just wait for Ubuntu's version but when you have free time on your hands this is what we do!

thxs

---

### Post by zika on 2010-01-31
> **ranch hand said:**
> Ah, well us noobs have to learn sometime.Ain't we all n00bs? ):P
Are these files that You need?

---

### Post by ranch hand on 2010-01-31
Those are the missing ones.  Do  I need them for my card?  Or do I need them for radeon support to work at all?

I have paid little attention to video related stuff as there is so much to learn and I am very happy with the desktop effects at "none" and the generic driver since 8.04.

The coming advent of Gnome-Shell has me worried as it requires compositing and I just can't do it the way things are.  I can't use compiz, which has never bothered me as it irritates me whenever I am around it.  I may not like GS but I will not know until I can see it.

As things are right now I can't even install the repo version because of lack of compositing support.

---

### Post by zika on 2010-01-31
> **ranch hand said:**
> Those are the missing ones.  Do  I need them for my card?  Or do I need them for radeon support to work at all?

I have paid little attention to video related stuff as there is so much to learn and I am very happy with the desktop effects at "none" and the generic driver since 8.04.

The coming advent of Gnome-Shell has me worried as it requires compositing and I just can't do it the way things are.  I can't use compiz, which has never bothered me as it irritates me whenever I am around it.  I may not like GS but I will not know until I can see it.

As things are right now I can't even install the repo version because of lack of compositing support.Just put them in /lib/firmware/radeon/ and forget about them... You should be able to use compiz with xorg-edgers, KMS and 2.6.3{2,3} as far as I know... I do not use it, I even disable KMS since there are some problems with freezing...

---

### Post by ranch hand on 2010-01-31
The OS I installed 33 on has "edgers" and will not run compiz.  The big change that I have seen is that compiz does not lock the box up tight.  Nothing about it works except the damned wobbly windows.

I will take the firmware and stick it.

Thanks.

---

### Post by _oOMOo_ on 2010-01-31
I've tried installing the 2.6.33 kernel as mentioned on page 12, but is there a best practice method of installing the most up-to-date nouveau driver on this kernel? I've tried apt-get -b xserver-xorg-video-nouveau, but the build fails; is there a ppa or do I need to build the driver completely myself from source?

Any help much appreciated,

thanks Jon

---

### Post by ranch hand on 2010-01-31
I did stick them in /lib/radeon/.  I had to create that directory though.

I also stuck them in the /lib directory for the kernel which did have a sub-directory for radeon.  The bugger boots is about all I can say now.  I am too tired to fool around with enabling effects and trying compiz.  They both irritate me to much too put up with right now.

---

### Post by ranch hand on 2010-02-01
I am not sure that compiz is working the way it is supposed to but that may be my ignorance.

It is working much more than it ever has.  It is obvious that the 2.6.33 kernel really does support my Radeon card MUCH better than it has ever been supported.

I will try the repo version of Gnome-Shell and if it is better than before may just get the ppa version and see what happens.

This is cool.

---

### Post by nanog on 2010-02-01
> This is cool.

Welcome to the other side, Ranch Hand. Soon your desktop switcher will be a dodecahedron and your wobbling windows will sprout flames.

---

### Post by ranch hand on 2010-02-01
My wobbly windows will do no such thing.  They are disabled and will stay that way.

I am trying to set up compiz and I do not know if I have it right.  Well I am sure I don't because I didn't have Emerald installed on that OS.  I believe that the "cube" is supposed to be on the desktop on top of the wallpaper.  Could be wrong.

I am tickled pink because it works this well but I want to see if it will work right.  The problem is that I do not know what right is.

If it does work right I will drop it like dirty underware and install Gnome-Shell.  Tried it from the repo and it wouldn't install do to lack of support.  I think that this kernel may well be giving that support.  I just figure to test that with compiz first.  I do not get on that OS very much so I do not want to waste time with something no one is sure what it is supposed to look like.

I figure that if it swill support compiz it will support GS.

---

### Post by sgosnell on 2010-02-02
Ranch Hand, you don't need the headers unless you plan to compile the kernel.  And it's already compiled.  Just download and install the image, and that's all you need.  I've been doing that for the past 4 kernel versions or so, on various Ubuntu versions.

---

### Post by ranch hand on 2010-02-02
> **sgosnell said:**
> Ranch Hand, you don't need the headers unless you plan to compile the kernel.  And it's already compiled.  Just download and install the image, and that's all you need.  I've been doing that for the past 4 kernel versions or so, on various Ubuntu versions.
I will keep that in mind but  I have all Of it anyway now.

I just want to see support get to the point where Gnome Shell will work.  This is not an old box (at least not in my opinion) and it should work on here.  It is improved some.  I get different errors than I did before.

I plan on upgrading the kernel about every week to watch the progress.  The install it is on is a "throw away" install that gets stuff thrown at it so that I know it is safe for the ones that count (I have 6 versions of 10.04 - 2 are throw aways).

I think this kernel is better and was hoping it was going in 10.04.  Doesn't  matter now as I know how to get it.

---

### Post by plun on 2010-02-07
Time for RC7

Linus Torvalds message, not so happy with a lot of regressions
[http://lkml.org/lkml/2010/2/6/106](http://lkml.org/lkml/2010/2/6/106)

Ubuntu Mainline
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc7/)

Testing...;)

---

### Post by IanW on 2010-02-07
> **ranch hand said:**
> I did stick them in /lib/radeon/.  I had to create that directory though.

I also stuck them in the /lib directory for the kernel which did have a sub-directory for radeon.  The bugger boots is about all I can say now.  I am too tired to fool around with enabling effects and trying compiz.  They both irritate me to much too put up with right now.

Those files need to be in /lib/**firmware**/radeon

---

### Post by zika on 2010-02-07
> **IanW said:**
> Those files need to be in /lib/**firmware**/radeon[http://ubuntuforums.org/showpost.php?p=8754541&postcount=122](http://ubuntuforums.org/showpost.php?p=8754541&postcount=122)

---

### Post by bladerunner6 on 2010-02-07
is nouveau in the daily builds yet? i see no reference to nouveau in the build.log

---

### Post by ranch hand on 2010-02-07
> **IanW said:**
> Those files need to be in /lib/**firmware**/radeon
They are in there too.  I am not sure why I used the other now.  If they do anything for my box I do not know.  I do know that the card likes the environment better over there.  At least to do things I am not interested in.

Still can't run Gnome Shell from the repo yet.  The errors are becoming less ominous.  When the bugger comes up and locks things up I am able to get out of it with tty2.  Much better than having to unplug the box because NOTHING worked.

Compiz is working a little better.  The settings seem to stay instead of reverting to default on every boot.  It still does not look the way it is supposed to but it does function some what.

I do not change the kernel daily.  About once a week is what I figure to do.  So I have 2 more before I am due to reinstall for A3 ISO testing.

I will put it back after that along with xorg.edgers.  Might work better on a clean install, maybe not.

---

### Post by MacUntu on 2010-02-07
> **bladerunner6 said:**
> is nouveau in the daily builds yet? i see no reference to nouveau in the build.log

ROFL. And I've wondered why I couldn't get Nouveau to work with that kernel.

```
CONFIG_STAGING_EXCLUDE_BUILD=y
```

I guess they do that to avoid tainting the kernel. Makes those builds useless to me. :(

---

### Post by ranch hand on 2010-02-07
> **MacUntu said:**
> ROFL. And I've wondered why I couldn't get Nouveau to work with that kernel.

```
CONFIG_STAGING_EXCLUDE_BUILD=y
```I guess they do that to avoid tainting the kernel. Makes those builds useless to me. :(
The edgers folks have Nouveau stuff to don't they.  I think so.  As an ATI user I am not sure but I think I get some stuff from them that refers to it.

---

### Post by MacUntu on 2010-02-07
They "only" have the linux-backports-modules package for 2.6.32.

---

### Post by bladerunner6 on 2010-02-08
I was able to install nouveau for 2.6.33 till sunday... from the ppa

if anyone can tell me howto compile my own kernel from the source debs and addin the nouveau stuff?

---

### Post by stmiller on 2010-02-15
> **bladerunner6 said:**
> I was able to install nouveau for 2.6.33 till sunday... from the ppa

if anyone can tell me howto compile my own kernel from the source debs and addin the nouveau stuff?

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

:)

---

### Post by soundcheck on 2010-02-19
Hi folks,

No idea if this has been posted before.This might be interesting for the Ubunutu Studio users,

There won't be a 2.6.32 rt patch available.

Due to several reasons the rt team around Thomas Gleixner just stepped up from 2.6.31 to 2.6.33 and left out 2.6.32. 

That'll be a serious problem for Ubuntu Studio I guess.

Cheers

---

### Post by zika on 2010-02-19
2.6.32-preempt is available, isn't that rt...?

---

### Post by crimsun on 2010-02-19
> **zika said:**
> 2.6.32-preempt is available, isn't that rt...?

No, -rt is a completely separate patchset (and thus, flavour). The difference between -generic and -preempt on amd64 is only a few config settings (hz set to 1000, preempt set, etc.).

---

### Post by zika on 2010-02-19
> **crimsun said:**
> No, -rt is a completely separate patchset (and thus, flavour). The difference between -generic and -preempt on amd64 is only a few config settings (hz set to 1000, preempt set, etc.).Thank You for clarification... Any chance there is a site where I could read a bit more?

---

### Post by aviramof on 2010-02-19
i'm not sure if it has something to do with one another but in 2.6.32.12/13 my tv screen looks pink and there for i can't use it is it possible that 2.6.33 would fix it?
 
of course if i manage to install ubuntu at all FEB 19 installer don't work very well for me right now.

---

### Post by chiisu on 2010-02-19
Is there any way to have the thread title edited?  Right now it's pretty misleading...

---

### Post by diebels on 2010-02-20
> **zika said:**
> Thank You for clarification... Any chance there is a site where I could read a bit more?

Here's the actual differences on a x86_64 machine, as crimsun said there's not much of a difference:
```

user@host:/boot$ diff config-2.6.32-13-generic config-2.6.32-13-preempt
3,4c3,4
< # Linux kernel version: 2.6.32-13-generic
< # Wed Feb 10 21:32:29 2010
---
> # Linux kernel version: 2.6.32-13-preempt
> # Wed Feb 10 23:42:31 2010
74c74
< CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.32-13.18-generic"
---
> CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.32-13.18-preempt"
307,308c307,308
< CONFIG_PREEMPT_VOLUNTARY=y
< # CONFIG_PREEMPT is not set
---
> # CONFIG_PREEMPT_VOLUNTARY is not set
> CONFIG_PREEMPT=y
375c375
< CONFIG_HZ_100=y
---
> # CONFIG_HZ_100 is not set
378,379c378,379
< # CONFIG_HZ_1000 is not set
< CONFIG_HZ=100
---
> CONFIG_HZ_1000=y
> CONFIG_HZ=1000
4645a4646
> CONFIG_DEBUG_PREEMPT=y
4702a4704
> # CONFIG_PREEMPT_TRACER is not set

```

I'm impressed by the ui-responsiveness improvement in Lucid with the .32-generic kernel, and as this kernel will get upstream driver updates for an extended time and ubuntu kernel devs are planning to backport drm parts, I think it's the best decision to stay with it for Lucid.

---

