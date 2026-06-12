---
title: "Installing Jaunty versus installing a pre-release of karmic"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scared0o0rabbit on 2009-09-19
So I read in a post earlier that Karmic is going to have some features not found in Jaunty including ext4 and GRUB2.

I also read that while you can upgrade from jaunty to karmic, a few things don't get changed over, including those two items above.

I guess my question is, if I were to do a fresh install with the current alpha of karmic, will it have those features already in it?  And if so, then when the actual release of karmic comes out, can I just upgrade then to that version through the updates or will I need to do an 'upgrade' or a 'clean install'?  Is there anything that doing this will mess up for me?  Are there any features I'd be missing out on from the karmic release if I install the alpha and can just update or upgrade?

I'd like to install ubuntu on another of my computers, and I figured while I was doing it I should go ahead and install a version with the newer features that won't come over when karmic comes out.

---

### Post by oboedad55 on 2009-09-19
> **scared0o0rabbit said:**
> So I read in a post earlier that Karmic is going to have some features not found in Jaunty including ext4 and GRUB2.

I also read that while you can upgrade from jaunty to karmic, a few things don't get changed over, including those two items above.

I guess my question is, if I were to do a fresh install with the current alpha of karmic, will it have those features already in it?  And if so, then when the actual release of karmic comes out, can I just upgrade then to that version through the updates or will I need to do an 'upgrade' or a 'clean install'?  Is there anything that doing this will mess up for me?  Are there any features I'd be missing out on from the karmic release if I install the alpha and can just update or upgrade?

I'd like to install ubuntu on another of my computers, and I figured while I was doing it I should go ahead and install a version with the newer features that won't come over when karmic comes out.

I just installed karmic and if you're looking for a bunch of cool, new features then I wouldn't bother. It's still buggy, automount doesn't work for example. You can use ext4 with jaunty, it's a format option. That's what I do, use jaunty with ext4. Best of both worlds.

---

### Post by Bucky Ball on 2009-09-19
Karmic is testing. If you want to test and report, go for it. If you want ultimate stablility and longest support, 8.04 LTS, if you want something that is still not quite cooked but approaching it, 9.04.

I repeat, Karmic is testing and NOT intended for production machines or any machine you rely on. Even after release it will probably be awhile. I tend to wait 6 months after release date for my 'workhorse' machine. That can't get broke (not in anyway that is going to take me two days to figure out a fix anyhow).

---

### Post by scared0o0rabbit on 2009-09-19
Well unfortunately for my work itself I have to rely on windows.  My main work application is rated as 'garbage' in the wine appdb heh.

So I mostly just use linux when I'm not working, so as long as it doesn't take my windows partition down, it doesn't matter too much.  So it sounds like karmic isn't worth bothering with for me so far.  If I wanted to use ext3 with jaunty, how do I go about doing it?  Is it something I do at the install time?  Or is it something I can do later?  Is it worth doing with jaunty?

---

### Post by oboedad55 on 2009-09-19
> **scared0o0rabbit said:**
> Well unfortunately for my work itself I have to rely on windows.  My main work application is rated as 'garbage' in the wine appdb heh.

So I mostly just use linux when I'm not working, so as long as it doesn't take my windows partition down, it doesn't matter too much.  So it sounds like karmic isn't worth bothering with for me so far.  If I wanted to use ext3 with jaunty, how do I go about doing it?  Is it something I do at the install time?  Or is it something I can do later?  Is it worth doing with jaunty?

Ext3 is default with jaunty. You can use ext4 when you install, you'll have to manually partition your drive at install time. Pretty simple really.

---

### Post by screaminj3sus on 2009-09-19
Yeah just manually partition with jaunty, all you need to do is make an ext4 partiton for / and a swap partition, and if you want a home partition also ext4.

I run karmic though because I love bleeding edge >:)

---

### Post by scared0o0rabbit on 2009-09-19
> **oboedad55 said:**
> Ext3 is default with jaunty. You can use ext4 when you install, you'll have to manually partition your drive at install time. Pretty simple really.

So would I need to set the partitions up with another piece of software before installing jaunty, or would I just manually change the partitions in the jaunty setup process?  I've only installed twice, so I don't have the whole process down 100% yet heh.

---

### Post by oboedad55 on 2009-09-20
> **scared0o0rabbit said:**
> So would I need to set the partitions up with another piece of software before installing jaunty, or would I just manually change the partitions in the jaunty setup process?  I've only installed twice, so I don't have the whole process down 100% yet heh.

When you run the install you'll see a section where it asks you how you want to install, side-by-side, use the whole drive, and at the bottom of that panel you'll see an option for "manual". That's what you want. Just pick the partition you want and click "change". There's you'll be able to set the mount point and format type. Just go slow and if you're not sure quit the install. Make sure you have everything you need backed up!

---

