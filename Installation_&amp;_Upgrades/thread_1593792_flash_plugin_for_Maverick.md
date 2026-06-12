---
title: "flash plugin for Maverick"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2010-10-11
What is the name for the Adobe Flash plugin for Maverick ?

I don't seem to see it under the same name that it has been listed under previous versions of Ubuntu.

Thanks.

---

### Post by ratcheer on 2010-10-11
I had to reinstall it after installing Maverick, and I just found it by trying to open a YouTube video. It told me I needed to install Flash and gave me about three choices of plugins to install, just by clicking a link that showed up on the YouTube page. I chose the one from Adobe and it installed and worked with no further problems.

Tim

---

### Post by wpshooter on 2010-10-11
> **ratcheer said:**
> I had to reinstall it after installing Maverick, and I just found it by trying to open a YouTube video. It told me I needed to install Flash and gave me about three choices of plugins to install, just by clicking a link that showed up on the YouTube page. I chose the one from Adobe and it installed and worked with no further problems.

Tim

Is this the preferred way of doing this ?

Under the older versions of Ubuntu, there was what I thought was a Ubuntu supplied Flash Plugin under Synaptic.

Why is that not still there ?

Thanks.

---

### Post by shaggy999 on 2010-10-11
Have you enabled the universe/multiverse repositories in the new install?

I see it just fine:

$ apt-cache search flash | grep ^flash
flashplugin-installer - Adobe Flash Player plugin installer
flashplugin-nonfree - Adobe Flash Player plugin installer (transitional package)

---

### Post by efflandt on 2010-10-11
In a regular installation I would think universe and multiverse would be enabled by default (they were on a fresh 10.10 beta install weeks ago and previous Ubuntu versions).

But I noticed no flash (or restricted-extras) when I used Startup Disk Creator to put release iso with persistent data on bootable USB flash, until I checked the boxes in Synaptic settings to enable universe/multiverse.  So after installing ubuntu-restricted-extras and the thing for DVD's, I now have 64-bit 10.10 release iso on USB flash that can do flash and play DVD's.

I didn't put real 64-bit flash on that because that might not work on my early Athlon64 3200+ that lacks the lahf_lm instruction.  But I have 64-bit flash (10.2 r161) on USB hard drives (Lucid and Maverick) that run on newer desktop or laptop.

---

### Post by garvinrick4 on 2010-10-11
I prefer just to use ubuntu-restricted-extras to start an install.
Here is flash in Ubuntu software center if that is what you wanted.

---

### Post by wpshooter on 2010-10-12
> **shaggy999 said:**
> Have you enabled the universe/multiverse repositories in the new install?

I see it just fine:

$ apt-cache search flash | grep ^flash
flashplugin-installer - Adobe Flash Player plugin installer
flashplugin-nonfree - Adobe Flash Player plugin installer (transitional package)

I looked for Flash and several other plugins just after I did the initial installation and update manager of Marverick and I could NOT find a listing for the plugins.

The only thing that I know that I changed after that was the setting for getting backport updates.  I shutdown the computer after that for the night.

But this morning when I booted again, and after I polled for updates and there were some relating to a new version of the kernel, which I downloaded and applied, and when I went back into Synaptic and looked for the various plugins, Flash, etc. now they were there.

What made these show up all of a sudden when I could not find them initially ?

Thanks.

---

### Post by DougieFresh4U on 2010-10-12
When I did a fresh install yesterday, I recall it asking me if I wanted 3rd party repo w/flash and I checked the box and it continued with the Maverick install

---

### Post by wpshooter on 2010-10-12
> **DougieFresh4U said:**
> When I did a fresh install yesterday, I recall it asking me if I wanted 3rd party repo w/flash and I checked the box and it continued with the Maverick install

Doug:

Did you do the install from Live CD or from Alternate ?

I did mine (as I usually do) from the Alternate.  Did not see any such prompt.

Thanks.

---

### Post by ratcheer on 2010-10-12
> **wpshooter said:**
> Is this the preferred way of doing this ?

Under the older versions of Ubuntu, there was what I thought was a Ubuntu supplied Flash Plugin under Synaptic.

Why is that not still there ?

Thanks.

I am pretty sure it is NOT the preferred way of doing it, but it was quick, easy, and effective.

Tim

---

