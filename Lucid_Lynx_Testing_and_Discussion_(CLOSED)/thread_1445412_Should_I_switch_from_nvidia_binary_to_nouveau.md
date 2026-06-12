---
title: "Should I switch from nvidia binary to nouveau?"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gnudoc on 2010-04-02
So I learned today that the nasty 16-colour boot splash screen I get in lucid beta was because the proprietary nvidia driver won't play nice with [the new KMS stuff]("http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/")

Also, I realised that I'm not really using any compiz features any more, except maybe transparency in gnome-terminal. Which I would (I assume) get from mutter/gnome-shell as much as from compiz.

Furthermore, I don't care at all about 3D games, and I only vaguely care about video card accelerated movie playback.

So, two questions:

1. Does nouveau play nice with gnome shell?
2. Whether it does or not, how do I go about switching from freedom-hating nvidia to nouveau? Jockey (the hardware driver manager thing) doesn't offer nouveau at all.

Thanks,
gnudoc

---

### Post by wkulecz on 2010-04-02
Nouveau was installed by default on my 10.04Beta1 test system.

It didn't last long as there were many screen redraw issues when uncovering windows.  Installing the Nvidia proprietary drivers seems to have fixed all issues, but there have been some 300+ updates installed since my initial experience, perhaps the issues I observed have been fixed, but I haven't seen a lot Nouveau complaints here.

I'm not really in a position help debug video drivers so I didn't file a bug report on what I observed figuring it was so obvious that if it affected others the bug reports would flow in.

I'm using a pretty low end card, GeForce 5500 or 6200 I've several of each and can't remember which are in what systems and don't see a lick of difference that matters to me to worry about which is which.

But I've had to use the Nvidia proprietary drivers since 5.10 to get the 2D performance I need.

---

### Post by gnomeuser on 2010-04-02
Nouveau as present in the Lucid repos does not support the required features for gnome-shell. However if you install the xorg-edgers PPA (search this out yourself and read the disclaimer)  you should be able to get 3D acceleration that is capable of running not just gnome-shell and compiz but also 3d games such as Quake and TA:Spring.

This is experimental so results may vary and ppa-purge is definitely your good friend for recovery but I have been using it for a long time with stunning results (stable, smooth and with very acceptable performance).

---

### Post by gnudoc on 2010-04-02
gnomeuser, thanks a lot. I had not seen that ppa.

So, I've added ppa:xorg-edgers/ppa, and it very nicely pushed a bunch of upgrades and a few new packages to me, including the nouveau kernel module and xserver-xorg-video-nouveau. So jockey-text -l tells me I have both xorg:nvidia_current and kmod:lbm_nouveau enabled. A quick -e, -d and reboot later and the nouveau is up and running, and the splash screen suddenly looks very nice. Win!

Sadly, gnome-shell --replace (i'm using the ricotz ppa) gives me no joy. :( It was working with the binary driver.

Any suggestions? Should I try the current lucid gnome-shell instead? Maybe build it from source using jhbuild? Or should I just wait for a fix?

---

### Post by gnomeuser on 2010-04-02
it could be a bug in gnome-shell or a nouveau bug, can you e.g. run compiz (compiz --replace) ?

---

### Post by gnudoc on 2010-04-02
Heh, good question. Yes, compiz does work.

Are you running gnome-shell successfully? If so, which build?

Thanks for the quick reply.

---

### Post by sgage on 2010-04-02
Nouveau was mostly acceptable for me, except it would not allow resume from sleep. The nvidia drivers work fine, and with the glx tweak to the grub config, doesn't look too bad on boot.

---

### Post by gnomeuser on 2010-04-02
> **gnudoc said:**
> Heh, good question. Yes, compiz does work.

Are you running gnome-shell successfully? If so, which build?

Thanks for the quick reply.

No, I loath gnome-shell. I find it to be a misguided project. However just for you I attempted to run it and it is indeed broken using nouveau currently whereas compiz works fine.

It has worked before though. For now you will probably have to wait a bit and see if it works in a few days. Perhaps report a bug with the gnome-shell guys.

---

### Post by strobe on 2010-04-02
> **gnudoc said:**
> gnomeuser, thanks a lot. I had not seen that ppa.

So, I've added ppa:xorg-edgers/ppa, and it very nicely pushed a bunch of upgrades and a few new packages to me, including the nouveau kernel module and xserver-xorg-video-nouveau. So jockey-text -l tells me I have both xorg:nvidia_current and kmod:lbm_nouveau enabled. A quick -e, -d and reboot later and the nouveau is up and running, and the splash screen suddenly looks very nice. Win!

Sadly, gnome-shell --replace (i'm using the ricotz ppa) gives me no joy. :( It was working with the binary driver.

Any suggestions? Should I try the current lucid gnome-shell instead? Maybe build it from source using jhbuild? Or should I just wait for a fix?

I have added the same ppa's but still can't get any 3d functions.  Jockey shows no drivers at all aside from the nvidia 96 and 173 (gforce 5200 here).  How are you all getting compiz to work with nouveau?  I can't find out how to actually activate the 3d side of them.

BTW, the nvidia drivers actually work worse for video on my dell inspiron 8600 laptop than with the nouveau.  Together with Lucid, Nvidia drivers spike my cpu to max out and stutter the video to no end.  If I can't fix the nouveau 3d, Lucid may never be usable for me.  I guess I need to find the "how-to 3d Nouveau for Noobs" thread...

---

### Post by gnudoc on 2010-04-02
> **gnomeuser said:**
> No, I loath gnome-shell. I find it to be a misguided project. However just for you I attempted to run it and it is indeed broken using nouveau currently whereas compiz works fine.

Lol, thanks for that. :)

Now that I have confirmation of that, I'll put the bug report in asap.

I, too, have reservations about gnome-shell after a few hours of playing with it using the binary driver. I'm willing to give the benefit of some time to evolve and develop further. Maybe it'll grow on me eventually. Meantime, at least I don't have to use nasty binary drivers anymore. That's a definite win!

Cheers,
gnudoc

---

### Post by gnomeuser on 2010-04-02
> **strobe said:**
> I have added the same ppa's but still can't get any 3d functions.  Jockey shows no drivers at all aside from the nvidia 96 and 173 (gforce 5200 here).  How are you all getting compiz to work with nouveau?  I can't find out how to actually activate the 3d side of them.

BTW, the nvidia drivers actually work worse for video on my dell inspiron 8600 laptop than with the nouveau.  Together with Lucid, Nvidia drivers spike my cpu to max out and stutter the video to no end.  If I can't fix the nouveau 3d, Lucid may never be usable for me.  I guess I need to find the "how-to 3d Nouveau for Noobs" thread...

Well 3D for Nouveau is still highly unsupported, it just happens to work very well for at least some of us. 2D and XV acceleration should work but for 3D you simply might be unlucky and be on a card type that isn't well supported yet.

Looking over the official driver it seems that the card you have isn't supported beyond the 173 driver (Nvidia removes support as the driver progresses both to drive sales and to lessen their support burden). If this driver is giving you problems you can file bugs against it but since it is proprietary software there is little anyone not directly employed in the nvidia Linux driver department can do.

Your best bet for the future is Nouveau so hopefully we can get you up and running but it might take a while for support to be solid on your specific card.

I know that is not the answer you wanted to hear but there sadly isn't much to do in your situation than to double check that you are indeed using the correct Nouveau version and that it is activated correctly.

---

### Post by strobe on 2010-04-02
> **gnomeuser said:**
> Your best bet for the future is Nouveau so hopefully we can get you up and running but it might take a while for support to be solid on your specific card.

I know that is not the answer you wanted to hear but there sadly isn't much to do in your situation than to double check that you are indeed using the correct Nouveau version and that it is activated correctly.

I guess thats the problem... I don't know how to check first of all... and second, I have no idea how to activate it.  I have seen somewhere (once, don't remember how) that it showed it was using the nouveau as the display adapter driver.  I have never seen it in jockey or any referance to any driver other than the nvidia 96 and 173 drivers.  In Synaptic, I have installed nearly every instance of nouveau listed but still can't enable desktop effects or compiz.  How do you "Activate" the nouveau driver for any 3d functions if its never listed in jockey?

---

