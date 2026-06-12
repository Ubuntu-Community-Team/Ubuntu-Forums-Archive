---
title: "kernel based mode-setting for Ibex?"
date: 2008-05-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hexion on 2008-05-22
I know it's not yet in the kernel's mainline and the only driver that supports it is the Intel one, but it would be very interesting for a number of laptops.

Apparently Fedora 9 already ships this feature.

More info: [http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1](http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1)

---

### Post by smartboyathome on 2008-05-23
I already had this in the idea pool. Search there. :)

---

### Post by quickshade on 2008-05-24
and I already stated that it's not going to happen. Simple put, the kernel release date is far to close to feature freeze, if not over it.  Not only that, but X requires some work to get it to properly work with this feature, and all the drivers (including some work on intels) are going to need modification to work properly. It's a good 8 month project before it can even be considered for a new release, and thats if Nvidia or ATI fix the issues with their drivers.

---

### Post by chrisccoulson on 2008-05-24
Lets face it, knowing NVIDIA it will be another 3 - 5 years before they support the new functionality anyway

---

### Post by plun on 2008-05-24
> **chrisccoulson said:**
> Lets face it, knowing NVIDIA it will be another 3 - 5 years before they support the new functionality anyway

Well...

Qoute AaronP from Nvidia

> Unfortunately, we can't. Kernel modesetting was specifically designed to be incompatible with the NVIDIA driver.

There are no plans to use DRI, TTM, or Gallium3D since the driver already has its own code for what those components provide.

[http://www.nvnews.net/vbulletin/showthread.php?t=113645](http://www.nvnews.net/vbulletin/showthread.php?t=113645)

Use crappy Intel cards or old ATI GPUs ....:)

---

### Post by chrisccoulson on 2008-05-24
What is support for ATI cards like at the moment?

I'm sick of NVIDIA. I'm pretty sure all of my problems are related to their drivers. I can't suspend and I can't hibernate. If more than one user on my system logs in at any one time, then any windows which appear on the inactive desktops appear as white boxes etc etc

---

### Post by plun on 2008-05-24
> **chrisccoulson said:**
> What is support for ATI cards like at the moment?

I'm sick of NVIDIA. I'm pretty sure all of my problems are related to their drivers. I can't suspend and I can't hibernate. If more than one user on my system logs in at any one time, then any windows which appear on the inactive desktops appear as white boxes etc etc

Well, that can be a kernel, Jockey or nVidia-glx-new problem, Ubuntu mess...

I am running version 173.08 and the 2.6.25 kernel with perfect
graphics.  (slightly overclocked 7600GS card)

Phoronix is a good site for exploring news about ATI and nVidia

[http://www.phoronix.com](http://www.phoronix.com)

The AMD/ATI open source approach is maybe just be a commercial "theatre"... Specs are released for older GPUs and I havent seen any for latest GPU generations.....

nVidia earns more money and sells more cards then ever...

> For the first quarter of fiscal 2009, revenue was $1.15 billion, compared to $844.3 million for the first quarter of fiscal 2008, an increase of 37 percent. Net income computed in accordance with U.S. generally accepted accounting principles (GAAP) for the first quarter of fiscal 2009 increased by 34 percent year-over-year to $176.8 million, or $0.30 per diluted share.

[http://phx.corporate-ir.net/phoenix.zhtml?c=116466&p=irol-newsArticle&ID=1142512&highlight=](http://phx.corporate-ir.net/phoenix.zhtml?c=116466&p=irol-newsArticle&ID=1142512&highlight=)

:)

---

### Post by gnomeuser on 2008-05-24
> **plun said:**
> 
The AMD/ATI open source approach is maybe just be a commercial "theatre"... Specs are released for older GPUs and I havent seen any for latest GPU generations.....



Plun, I thought we had been over this once before. This is plain not true.

AMD/ATI have released specs for the RadeonHD cards[1][2], They also hired Alex Deucher to work on their open source driver and mesa[3] and they paid Novell to develop the radeonHD driver prior to that[4]

AMD/ATI are being very Free Software friendly, and as a result since they started this work the FLOSS drivers you have, for the newer cards as well for the older models have improved vastly. 

So please, stop saying that they are not doing anything, it's just plain not true. They have a solid long term plan for moving to FLOSS drivers and they continually release specifications for us without NDA requirements.

As for other vendors:

Intel are also being very FLOSS friendly, you might not like their GPUs but they are powered entirely by Free Software and their specifications are released under a CC license[5]. This naturally for Intel also extends to releasing specs and drivers under a suitable license for their wifi chips as well.

Even VIA are jumping onboard[6], abide so far only with a framebuffer driver but their recent +16000 line code contribution makes it by far the best supported framebuffer device we have.

I really wish I could add Nvidia to the list of players who are seriously doing something to support Linux and provide a good out of the box experience. They are though actively supporting the 2D nv driver in X[7] (giving credit where credit is due). Sadly they have a habit of obfuscating it[8][9]. The best news here is the community effort to bring a good 3D driver to nvidia users[10], which is making good progress, e.g. Dave Airlie demonstrated Open Arena running on this at LCA2007[11] (Video, the demonstration is near the end). This effort is done entirely without support or specifications from Nvidia, through time comsuming reverse engineering.

I'll leave it up to people to decide who to reward when buying video ards but I hope we can all rejoice that Free Software drivers are getting better by the day. More companies are supporting us actively and releasing specifications and/or source code. We lack only one big player in the field which given the situation two years ago is pretty damn good. The X stack is improving leaps and bounds as a result, and our users enjoy a better out of the box experience.

[1] [http://arstechnica.com/journals/linux.ars/2007/09/21/amdati-release-register-specifications-novell-follows-with-alpha-driver](http://arstechnica.com/journals/linux.ars/2007/09/21/amdati-release-register-specifications-novell-follows-with-alpha-driver)
[2] [http://www.x.org/docs/AMD/](http://www.x.org/docs/AMD/)
[3] [http://www.botchco.com/agd5f/?p=6](http://www.botchco.com/agd5f/?p=6)
[4] [http://www.phoronix.com/scan.php?page=article&item=842&num=1](http://www.phoronix.com/scan.php?page=article&item=842&num=1)
[5] [http://www.x.org/docs/intel/](http://www.x.org/docs/intel/)
[6] [http://www.phoronix.com/scan.php?page=news_item&px=NjQ2Nw](http://www.phoronix.com/scan.php?page=news_item&px=NjQ2Nw)
[7] [http://www.phoronix.com/scan.php?page=news_item&px=NjQ2OQ](http://www.phoronix.com/scan.php?page=news_item&px=NjQ2OQ)
[8] [http://airlied.livejournal.com/34017.html?thread=95201](http://airlied.livejournal.com/34017.html?thread=95201)
[9] [http://cvsweb.xfree86.org/cvsweb/xc/programs/Xserver/hw/xfree86/vga256/drivers/nv/Attic/README.RIVATNT.diff?r1=1.1.2.2&r2=1.1.2.3&hideattic=0&only_with_tag=xf-3_3_3](http://cvsweb.xfree86.org/cvsweb/xc/programs/Xserver/hw/xfree86/vga256/drivers/nv/Attic/README.RIVATNT.diff?r1=1.1.2.2&r2=1.1.2.3&hideattic=0&only_with_tag=xf-3_3_3)
[10] [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)
[11] [http://mirror.linux.org.au/pub/linux.conf.au/2008/Fri/mel8-081.ogg](http://mirror.linux.org.au/pub/linux.conf.au/2008/Fri/mel8-081.ogg)

---

### Post by chrisccoulson on 2008-05-24
gnomeuser, you seem very well informed. Although, I find the information available to be somewhat overwhelming. I suppose that the bottom line for someone like me is - what chipset should I go for when I buy my next card? (NVIDIA, Intel or ATI). I'm finding it very difficult to make that decision with the information available.

---

### Post by hexion on 2008-05-24
> **chrisccoulson said:**
> gnomeuser, you seem very well informed. Although, I find the information available to be somewhat overwhelming. I suppose that the bottom line for someone like me is - what chipset should I go for when I buy my next card? (NVIDIA, Intel or ATI). I'm finding it very difficult to make that decision with the information available.
IMHO, the best way is just what gnomeuser did. Just explain the facts so whoever can take the decision themselves ;)


And now staying on topic:

Ok, the feature freeze is not there yet. And that can and must delay the adoption by Ubuntu of that protocol. That makes sense..

But regarding the lack of support of others than Intel. What's the deal with it? Supposing adding mode-setting to the kernel won't affect negatively to other ways to approach the problem, it would be just a positive thing for Intel card owners, and nothing to the rest. Wouldn't it?

---

### Post by gnomeuser on 2008-05-24
> **chrisccoulson said:**
> gnomeuser, you seem very well informed. Although, I find the information available to be somewhat overwhelming. I suppose that the bottom line for someone like me is - what chipset should I go for when I buy my next card? (NVIDIA, Intel or ATI). I'm finding it very difficult to make that decision with the information available.

It depends on your needs, if you want to play 3D games then the Intel chips are generally out e.g. but if all you want is a desktop that runs silent and does Compiz as well then they are excellent chips. Another advantage with Intel' chips are that they are very well supported and used in prototyping new X functionality - In Fedora 9 we ship kernel modesetting as a technology preview for those cards. So if you like that kind of stuff it's a good choice.

If you want a fast 3D card and value active support for Free Software, releasing of specs, help make the world a better place then ATI are a good choice. Good performance, reasonable price and they are becoming very well supported (though features might be missing here and there, it's progressing very fast though).

Nvidia' cards are very good, their proprietary drivers work well for a number of people, their driver supports a lot of very fancy stuff (though as is stated they reinvent a lot of their own stuff to get there and it's literally impossible for us to fix when they break.. also a history of silent stack abuse which leads to applications crashing). Generally though of as "just works" provided they released a driver for the X server you are using and you are not using a card they consider discontinued.

But the buttomline is you weight out what matters to you, what your needs are and always be careful with the very latest revisions of any vendors cards. Even if the driver is there the day is ships, the code still needs to get into the X tree, a release of the driver needs to be made and an update pushed to you as a user. I don't know the Ubuntu policy for this but in Fedora we try to aggressively push out such driver updates to let people have support and still we have a little lag.

---

### Post by plun on 2008-05-24
> **gnomeuser said:**
> Plun, I thought we had been over this once before. This is plain not true.

AMD/ATI have released specs for the RadeonHD cards[1][2], They also hired Alex Deucher to work on their open source driver and mesa[3] and they paid Novell to develop the radeonHD driver prior to that[4]

AMD/ATI are being very Free Software friendly, and as a result since they started this work the FLOSS drivers you have, for the newer cards as well for the older models have improved vastly. 

So please, stop saying that they are not doing anything, it's just plain not true. They have a solid long term plan for moving to FLOSS drivers and they continually release specifications for us without NDA requirements.

As for other vendors:

Intel are also being very FLOSS friendly, you might not like their GPUs but they are powered entirely by Free Software and their specifications are released under a CC license[5]. This naturally for Intel also extends to releasing specs and drivers under a suitable license for their wifi chips as well.

Even VIA are jumping onboard[6], abide so far only with a framebuffer driver but their recent +16000 line code contribution makes it by far the best supported framebuffer device we have.

I really wish I could add Nvidia to the list of players who are seriously doing something to support Linux and provide a good out of the box experience. They are though actively supporting the 2D nv driver in X[7] (giving credit where credit is due). Sadly they have a habit of obfuscating it[8][9]. The best news here is the community effort to bring a good 3D driver to nvidia users[10], which is making good progress, e.g. Dave Airlie demonstrated Open Arena running on this at LCA2007[11] (Video, the demonstration is near the end). This effort is done entirely without support or specifications from Nvidia, through time comsuming reverse engineering.

I'll leave it up to people to decide who to reward when buying video ards but I hope we can all rejoice that Free Software drivers are getting better by the day. More companies are supporting us actively and releasing specifications and/or source code. We lack only one big player in the field which given the situation two years ago is pretty damn good. The X stack is improving leaps and bounds as a result, and our users enjoy a better out of the box experience.

[1] [http://arstechnica.com/journals/linux.ars/2007/09/21/amdati-release-register-specifications-novell-follows-with-alpha-driver](http://arstechnica.com/journals/linux.ars/2007/09/21/amdati-release-register-specifications-novell-follows-with-alpha-driver)
[2] [http://www.x.org/docs/AMD/](http://www.x.org/docs/AMD/)
[3] [http://www.botchco.com/agd5f/?p=6](http://www.botchco.com/agd5f/?p=6)
[4] [http://www.phoronix.com/scan.php?page=article&item=842&num=1](http://www.phoronix.com/scan.php?page=article&item=842&num=1)
[5] [http://www.x.org/docs/intel/](http://www.x.org/docs/intel/)
[6] [http://www.phoronix.com/scan.php?page=news_item&px=NjQ2Nw](http://www.phoronix.com/scan.php?page=news_item&px=NjQ2Nw)
[7] [http://www.phoronix.com/scan.php?page=news_item&px=NjQ2OQ](http://www.phoronix.com/scan.php?page=news_item&px=NjQ2OQ)
[8] [http://airlied.livejournal.com/34017.html?thread=95201](http://airlied.livejournal.com/34017.html?thread=95201)
[9] [http://cvsweb.xfree86.org/cvsweb/xc/programs/Xserver/hw/xfree86/vga256/drivers/nv/Attic/README.RIVATNT.diff?r1=1.1.2.2&r2=1.1.2.3&hideattic=0&only_with_tag=xf-3_3_3](http://cvsweb.xfree86.org/cvsweb/xc/programs/Xserver/hw/xfree86/vga256/drivers/nv/Attic/README.RIVATNT.diff?r1=1.1.2.2&r2=1.1.2.3&hideattic=0&only_with_tag=xf-3_3_3)
[10] [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)
[11] [http://mirror.linux.org.au/pub/linux.conf.au/2008/Fri/mel8-081.ogg](http://mirror.linux.org.au/pub/linux.conf.au/2008/Fri/mel8-081.ogg)

Well, they are probably friendly as long they have severe problems with business...

I don't think they publish specs for latest GPUs within a year or two.


I don't have any problems running a proprietary driver from nVidia, I have severe problems when I sees **_junk as Windows Vista_**....

I find Windows XP OK for a lot of users.

**I am NOT "software religious" and I think its time to fire RMS.**


This is just stupid that a small group of religious users stops development and every software projects are **hijacked** from religious users.

nVidia gives us a **first class driver** because they have a **_real market for pros_**, Quadro cards and the media industry.


So let users which are "religios" run Gobuntu or gnewsense, nVidia maybe opens their driver but thats not an important issue for me.

---

### Post by smbm on 2008-05-24
> **plun said:**
> This is just stupid that a small group of religious users stops development and every software projects are **hijacked** from religious users.

Do you have any examples?

---

### Post by ronacc on 2008-05-25
I guess "software religion" is in the eye of the beholder , I like Plun can find pleanty of evidence of it , ranging from posts in these forums to the choice of apps in the official repo's . look for your own examples I don't compile a list that I can refer to at need.

---

### Post by gnomeuser on 2008-05-25
> **plun said:**
> Well, they are probably friendly as long they have severe problems with business...

I don't think they publish specs for latest GPUs within a year or two.


Yes, because you always elect to slaugter the tactic that buys you marketshare as soon as you gain it.. 

The reason ATI changed their opinion on this area is two fold. 

A) they got bought by AMD who have always been very good at releasing specification and this leads them to this as a business decision.

B) AMD/ATI are integrating their GPU and CPU into one package in the near future, it makes business sense to release specifications to encourage this move. They already have a strong section of the laptop GPU market, this is a way to leverage that to also get their CPUs into more laptops. They get a boost in this effort by showing they are open.

Another reason would be:

C) Linux support being an increasing demand from business clients, you see every major company out there building a low cost Linux laptop e.g. AMD want a piece of this future market. They definitely also want a piece of the market for the low cost Linux desktops (like the Shuttle KPC).

AMD/ATI themselves have said this much when presenting this new move originally.

Now please just stop hurting AMD/ATI as well as the Free Software community by spreading such unfounded fear. It is not based in facts or sound argument.

---

### Post by ronacc on 2008-05-25
I build my own desktops so I have free choice of components, I have been keeping an eye on the AMD/ATI "opening" looking forward to good results since I have always used AMD cpu's . I have always used Nvidia graphics card because they just flat work best for linux (so far) . I am hardware agnostic so as soon as I see those good results ATI will be added to my list for graphics cards . note I say graphics cards as I am definately not a fan of combining the CPU with the GPU , atleast as far as desktops go since I believe that might render upgrading a box problematical . I certainly hope that AMD does not make the mistake of offering "combos" as an only choice .

---

### Post by Gina on 2008-05-25
I've always been wary of "combos" of any sort as they often seem to compromise with one or the other - and, yes, there is the problem if you want to upgrade one component.  I agree it would definitely be a mistake to offer combos only.  I think AMD probably have the sense to realise this, they certainly seem to understand customers wishes.

---

### Post by gnomeuser on 2008-05-25
> **ronacc said:**
> I build my own desktops so I have free choice of components, I have been keeping an eye on the AMD/ATI "opening" looking forward to good results since I have always used AMD cpu's . I have always used Nvidia graphics card because they just flat work best for linux (so far) . I am hardware agnostic so as soon as I see those good results ATI will be added to my list for graphics cards . note I say graphics cards as I am definately not a fan of combining the CPU with the GPU , atleast as far as desktops go since I believe that might render upgrading a box problematical . I certainly hope that AMD does not make the mistake of offering "combos" as an only choice .

There are ups and downs with suchs a setup, but clearly it is a good design for these low cost machines. There will always be a market for hobbists like yourself who want a seperate card for certain things, just like despite there being a decent audiocard on most motherboards today there is a market for extensions for this model. I have no fear that will go away anytime soon. Even if this becomes the norm, I am sure there will be a way to disable the builtin video card and extend it with your own (or add another in a kind of SLI like fashion). I don't think there is any reason to fear the demise for the seperate videocard just because AMD are investing in different areas.

If all my components were performing decently and had open specifications I wouldn't care either way really. I still use my trusty Radeon 9250 on the r200 driver because it runs beautifully and silently for my tasks.

---

### Post by smbm on 2008-05-25
> **ronacc said:**
> I guess "software religion" is in the eye of the beholder , I like Plun can find pleanty of evidence of it , ranging from posts in these forums to the choice of apps in the official repo's . look for your own examples I don't compile a list that I can refer to at need.

That's fair enough, I've not noticed it myself. 

I was just wondering if you knew of anything I could look into myself to find out what is going on.

---

### Post by ssam on 2008-05-25
ubuntu should not let proprietary slowness hold it back.

---

### Post by RAOF on 2008-05-27
> **gnomeuser said:**
> ...Even if this becomes the norm, I am sure there will be a way to disable the builtin video card and extend it with your own (or add another in a kind of SLI like fashion). I don't think there is any reason to fear the demise for the seperate videocard just because AMD are investing in different areas.
...

One of the [recent AMD chipsets]("http://arstechnica.com/reviews/hardware/amd-780g-chipset-review.ars") has precisely this sort of functionality; you can add a dedicated video card and gain SLI type functionality.

Also, it's my understanding that kernel modesetting doesn't really require *kernel* changes, per se.  Just new drm kernel modules, from a branch  (maybe?) of libdrm, which would normally be incorporated into the mainline kernel at some point.  An actual release of libdrm seems to be stalling on finalising a (or more than one) GPU memory manager.

---

### Post by Skerit on 2008-05-27
Well, I need to thank everyone in this thread because it's a very interesting read. 

For the record, I'm definitely going to consider AMD/Ati for my future setups.

I'm currently building an HTPC and, even with an nvidia 7600GS and Dual Core 2 Processor (E6600) with 2,4 ghz, watching an HD stream is painfully slow and requires CoreAVC to run.

It's very frustrating to know your computer HAS the power to do it with ease, knowing that you paid for it, but that it won't happen because of nvidia's restrictions. It's a big middle finger for a lot of customers (No matter how small the market share of Linux is, it would still translate to a large number of users)

I look forward to nouveau's progress, and the "Generic GPU-Accelerated Video Decoding" summer-of-code project.

---

### Post by gnomeuser on 2008-05-27
> **RAOF said:**
> One of the [recent AMD chipsets]("http://arstechnica.com/reviews/hardware/amd-780g-chipset-review.ars") has precisely this sort of functionality; you can add a dedicated video card and gain SLI type functionality.

Also, it's my understanding that kernel modesetting doesn't really require *kernel* changes, per se.  Just new drm kernel modules, from a branch  (maybe?) of libdrm, which would normally be incorporated into the mainline kernel at some point.  An actual release of libdrm seems to be stalling on finalising a (or more than one) GPU memory manager.

Wow, I did not expect that to be out already but that is good news indeed - hopefully such a solution would keep everyone happy.

As for the kernel stuff, it doesn't require changes outside the DRM tree so far as I know but this still only gets merged for new features once per kernel cycle. So some interesting choices will have to be made, stick with upstreams DRM tree or merge git to get the newest developments. I know Fedora will probably do the latter since we are upstream along with Intel for this work, if this is a suitable solution for Ubuntu one can speculate - it's optionally enabled for drivers AFAIK and upstream are very active fixing bugs in time for the next merge.. the pain level should be minimal for users and development time cost of doing this is likely minimal as well but it depends on how active one desires to be in shaping this feature and if it's right for the Ibex feature targets.. it might just be sensible to not bite off to much and focus on other things then start the kernel modesetting work in Ibex+1.

---

