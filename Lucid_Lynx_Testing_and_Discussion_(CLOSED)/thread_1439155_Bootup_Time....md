---
title: "Bootup Time..."
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by keljaden on 2010-03-25
Okay, I was all excited for this "10 seconds boot time". but i am extremely disappointed.  Instead ANY boot speed increase, it takes ~15 longer to boot that 9.10 (same hardware configuration).  Are beta's for ubuntu always this buggy???, maybe I am just used to more "complete" betas'.  Is there anything I can do beyond just hope the daily updates will fix this?

---

### Post by descendent87 on 2010-03-25
I've noticed a massive speed up in boot time. Probably boots in under 10 seconds on my machine (AMD Phenom II X3, 4GB RAM, ATI HD3200)

---

### Post by xebian on 2010-03-25
My boot time is so fast I hardly see that Ubuntu 10.04 thing.  And not even using ureadahead as it's always getting a status 5.  

I wish the shutdown would be as quick.

---

### Post by ankspo71 on 2010-03-25
Hi,
Betas are normally buggy. We really shouldn't expect great boot times until it's closer to the release date. Some updates have been making my boot times faster, and some have been making them slower. I can see from the number of daily updates that they are working hard to improve Ubuntu. So far Lucid has been faster for me than Karmic at total boot time, but it could be much better if the actual desktop (nautilus desktop) would load quicker. I'm sure that will be improved before the release date though.  The other day I was at 22.5 with a Pentium 4 3.0, 2gb memory (without tweaking)

---

### Post by ikt on 2010-03-26
> **keljaden said:**
> Is there anything I can do beyond just hope the daily updates will fix this?

Yes, I suggest a reinstall from scratch, not an upgrade.

---

### Post by night-wing on 2010-03-26
I also do not agree.

On my thinkpad t23 and thinkpad x60, the bootup time is a lot shorter than before - on the x60 I am now at 20 seconds from hitting the power-on button to complete loaded gnome desktop (not only from grub to gdm) !!!

---

### Post by Psumi on 2010-03-26
> **night-wing said:**
> I also do not agree.

On my thinkpad t23 and thinkpad x60, the bootup time is a lot shorter than before - on the x60 I am now at 20 seconds from hitting the power-on button to complete loaded gnome desktop (not only from grub to gdm) !!!

My IBM ThinkPad T41 seems to boot as fast as about 10 seconds, but according to bootchart, it takes up a whopping 40+ seconds.

---

### Post by keljaden on 2010-03-27
I updated for a couple of days and it seems now to be a lil bit quick than 9.10, but not by much.

My System specs:
ASUS P5N-D
XIGMATEK CPU cooler (idles at 28C, max load 43C)
Intel E8400
RAM 4gigs 800mghz DDR2
GPU 8800GT (oc'ed to 9800GT speeds)
HDD's are all 7200 RPM

Also, i start timing as soon as I select ubuntu from grub's menu. I end in when i see that the bar with the app menu is loaded.

---

### Post by tanari on 2010-03-27
47sec

Athlon II X3 420
HDD 7200rpm
4GB RAM
ASROCK A780GXE/128M

---

### Post by cariboo on 2010-03-27
For me boot times seem to be going up and down, currently on the system I'm using right now boot time is a little over 18 seconds, last week it was 15 sec. On my office system which is upgrade from Karmic it takes about 22 seconds. My netbook boots in a little over 14 seconds, which seems to be faster than starting up from hibernate.

---

### Post by ssam on 2010-03-27
take some boot charts (9.10 and 10.04) and file a bug

---

### Post by kansasnoob on 2010-03-27
> **cariboo907 said:**
> For me boot times seem to be going up and down, currently on the system I'm using right now boot time is a little over 18 seconds, last week it was 15 sec. On my office system which is upgrade from Karmic it takes about 22 seconds. My netbook boots in a little over 14 seconds, which seems to be faster than starting up from hibernate.

+1! This is what I see, boot times vary from just under 30 seconds to about 45 seconds, and the "splash" also varies now (in just the past 24 hours) from boot to boot.

One time I'll have a fairly pleasant font and on the next boot it will be ridiculously huge. Even gdm will vary in size from boot to boot, sometimes so large that it doesn't all fit on my 22" widescreen.

---

### Post by kansasnoob on 2010-03-27
> **ssam said:**
> take some boot charts (9.10 and 10.04) and file a bug

I think I'd wait a couple of days. These new changes were only implemented in the past 24 hours. Or comment on one of the many existing plymouth bug reports.

---

### Post by zengeos on 2010-03-27
I run Update Manager twice daily.  What I have experienced is that the first reboot after installing the recommended updates is always noticeably slower AND the login screen comes up simultaneously with the desktop.  After that the bootchart indicates about 15 second faster boot, but the login screen takes 5-10 seconds after the desktop displays to come up.

That is mostly the only real variation I get in boot times between updates.  This last update has slowed my bootchart boot times by about a second, 2 just over 27 seconds.

This is twice as fast as Karmic boots.

---

### Post by kansasnoob on 2010-03-27
> **kansasnoob said:**
> I think I'd wait a couple of days. These new changes were only implemented in the past 24 hours. Or comment on one of the many existing plymouth bug reports.

On second thought I was wrong. Go ahead and file your bug reports! When I'm wrong I'm dead wrong :P

I'm following a couple of these and I see Steve Langasek thinks it's fixed:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

---

### Post by Jordanwb on 2010-03-27
> **tanari said:**
> 47sec

Athlon II X3 420
HDD 7200rpm
4GB RAM
ASROCK A780GXE/128M

It's sad that my single core laptop can beat your machine's boot time with 45 seconds. My desktop machine boots in 20 seconds but I think it can be faster.

---

### Post by RJARRRPCGP on 2010-03-27
Boot times still reasonable with beta 1.

Karmic Koala seems to be the worst, recently. 

And Lucid Lynx beta 1 is possibly booting even faster than Jaunty Jackalope!

---

### Post by jaco223 on 2010-03-27
I'm averaging around 14-15 sec. boot times.

---

### Post by keljaden on 2010-03-28
SO are u guys starting as soon as u select ubuntu to the time the desktop fully loads?

---

### Post by Rob2687 on 2010-03-28
I think that's the interval that bootchart uses. It's best to follow a measurement tool like that anyways. I've seen on other forums where people brag about like 5 second boot times. They posted a youtube vid and it turned out the guy only counted the time he actually saw the boot logo on OSX. -_- It spent a lot longer loading during a blank screen and also loading to the desktop. If I only counted from the time it shows the Plymouth screen my boot time would be like 500 milliseconds. XD

---

### Post by jppr on 2010-03-28
both 10.04 and windows 7 boot about 15 sec.

---

### Post by keljaden on 2010-03-30
@jppr
what are you system specs?

Also, does anyone else get a ~5 sec wait time after u log in.  The default backround image will load and the ubuntu jingle plays, followed by a ~5 second wait time, my backround then loads along with the panels on the top and bottom of my screen.

---

### Post by 98cwitr on 2010-03-30
9.10 booted faster than my current (updated last night) version of 10.04 LTS...oh well, Ill update to 10.04 non-LTS when released, but for the time being the slash screens look like something from 1998 and gnome loads slower than usual.

---

### Post by julianb on 2010-03-30
Able to boot in about 25 seconds on Asus EEEpc 900A (1.6ghz intel atom, 1GB RAM).

I still can't figure out how to make Lucid do an auto-login.

---

### Post by cimh on 2010-03-30
> **julianb said:**
> Able to boot in about 25 seconds on Asus EEEpc 900A (1.6ghz intel atom, 1GB RAM).

I still can't figure out how to make Lucid do an auto-login.

On my 901 you get to autologin by - Menu>system>admin>Login screen
>unlock (enter pwd)> select login as 'username' automatically

Lucid on my 901 boots to desktop from switch on in 20s, this includes 6s to get to grub. 

on my hardware ubuntus boot time has steadily improved.

8.04  = 50s
9.04  = 32s
9.10  = 29s
10.04 = 20s

fastest I have ever had this netbook booting is 16s with an earlt version of puppee
but I have seen a video of arch booting in 12s on the 901 so there is still room for improvement!

cimh
eee 901, lubuntu, ubuntu, puppeee

---

### Post by julianb on 2010-03-30
I had tiny core linux booting in about 10 seconds on an eeepc but installing Chromium browser made the install tiime slower - it took something like 17 seconds instead.

---

### Post by cimh on 2010-03-31
> **julianb said:**
> I had tiny core linux booting in about 10 seconds on an eeepc but installing Chromium browser made the install tiime slower - it took something like 17 seconds instead.

Do you think that's one of the problems with the v small distros like tiny, moblin, and others? They are only fast when you keep them simple and adding more programs slows them down. As far as I can see this doesnt happen with ubuntu - although ubuntu one did slow things down quite a bit - I dont know if it still does as I dont use it now.

Boot times are no big deal on a desktop I'm happy to switch on in the morning and walk away but it is important on netbooks. I dont know what you think but with Lucid booting so efficiently and with the potential to get even faster. It decreases the usefulness of the small distros such as tiny as you pay a high price in terms of loss of utility to gain 3-4 secs at boot.

I keep a speadsheet of boot times on netbooks:
[http://spreadsheets.google.com/ccc?key=0Aib-MC2xtkLhcFRBaGJ1Q3o4WUJSSHNvUzdQNFM2T3c&hl=en_GB](http://spreadsheets.google.com/ccc?key=0Aib-MC2xtkLhcFRBaGJ1Q3o4WUJSSHNvUzdQNFM2T3c&hl=en_GB)

The sub 20s distros all tend to be small - Haiku, arch, xpud,chrome, moblin, jolicloud, slitaz.

but 3 larger distros are also there xandros (the original eee distro), cut down xp and ubuntu (using lxde rather than gnome), I guess it wont be long till ubuntu gnome is there too. (feel free to add tiny)

 
cimh
901

---

### Post by ankspo71 on 2010-03-31
> **keljaden said:**
> Also, does anyone else get a ~5 sec wait time after u log in.  The default backround image will load and the ubuntu jingle plays, followed by a ~5 second wait time, my backround then loads along with the panels on the top and bottom of my screen.

Yes I get that too, but after recent updates, the wait time has improved for me.

For anybody who is interested. I dug up some info about the test machine that Ubuntu is using to reach the targeted 10 second boot time. It is a Dell Mini 10 SSD & HDD. According to one of the links I have found, the targeted boot time is for the SSD, not the HDD (as seen in the first link below)

[http://people.canonical.com/~scott/daily-bootcharts/](http://people.canonical.com/~scott/daily-bootcharts/)
[https://wiki.ubuntu.com/FoundationsTeam/BootPerformance](https://wiki.ubuntu.com/FoundationsTeam/BootPerformance)
[https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Lucid](https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Lucid)

I wonder if my computer supports SSD drives. :P

---

### Post by cimh on 2010-03-31
> **ankspo71 said:**
> I dug up some info about the test machine that Ubuntu is using to reach the targeted 10 second boot time. It is a Dell Mini 10 SSD & HDD

Yes the target is 10s on the dell ssd. They are currently getting 17s. There is no target for a hdd because they are much more variable (but fyi their current test hdd machine boots in 26s).

The 17s that they are currently achieving is broken down to 1.6 kernel, plumbing 4.1, x 1.3 and desktop 10ish.

So I guess the big gain is to be made in the desktop. Their 17s on the dell presumably corresponds to the 20s I get on my eee which means I could look forward to boot times of about 13s, that's a challenging and impressive target.

My eee has 2 ssds, a fast 4g and a slower 16g. The speed of the ssd makes a difference too. The 4g is relatively fast and not so easy to change. The 16g is slower but is easily replaced by a faster or bigger card and many of us do that. This means that we can host the distro on either card with no loss of boot speed.

I am currently tribooting with Lucid, lubuntu lucid and puppeee. Of interest Lubuntu using lxde is only 1s faster to boot (19s).


cimh
eee 901 ssd.

---

### Post by keljaden on 2010-03-31
Has anyone else noticed that grub is pretty slow as well? After I select Ubuntu from the grub menu, I get a black screen with a flashing "_" at the top right corner for what takes up most of the boot time.  The other long delay is after I login, the default backround loads, then after liek 5~10seconds, gnome loads....the shutdown time before last night was horrific. (went from 10 seconds shutdown to 3 seconds shutdown).
I guess they just threw all the apps and skins to 9.10 and the updates must all be speed related because that is what I am seeing now. Also, I have heard that the removal of HAL is what has caused the supposed decreases in boot time, is this true?

---

### Post by Scott82 on 2010-03-31
lol, this is my sons pc stats:
celeron D, i think it's 2.5 Ghz (single core, 32-bit)
1.5 GB Ram (2 GB - 25% auto sent to integrated video even thoug i don't use it (can't be disabled in bios) )
nvidia geforce 5200 fx PCI (not PCI-E)
40 GB IDE HDD that reports as having more bad sectors than the total amount of sectors in SMART.

boot time:
after bios about 8 seconds..... the ubuntu and dots under it show for about 1.5 seconds.

crazy right?

it was however a total pain to even get ubuntu 10.04 installed on it, i'm pretty sure a lot of the hardware is failing lol.

edit was i put 80 GB instead of 40 lol.

---

### Post by keljaden on 2010-04-03
Are you saying it is not loading all the drivers increasing boot time?

This is still ridiculous, I ran some updates, and my boot time is still 46 seconds. It was 26 is Ubuntu 9.10.  out of the 46 seconds, it takes 26 seconds to load my desktop from the login screen which is INSANE, it only took 3 seconds in ubuntu 9.10.  How is a beta this much slower?  I expected crashes and bugs, but this confuses me.

---

