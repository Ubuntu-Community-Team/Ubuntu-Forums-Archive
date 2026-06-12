---
title: "Multiple Display and Drive issues."
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by deniedproject on 2010-05-27
Ubuntu for whatever reason does not detect my monitors edid information nore does it support my 8800GTS G92 512MB card, ive tried the nosplash workaround several times and its a nogo. Ive tried using other monitors and they work but my main SCEPTRE X22WG-1080P Black 22" does not work at all. All I get is a black screen. 

Also for whatever reason when ubuntu's partition goes to detect my hard drives it fails to detect the partitions on two of my drives which is rather annoying as well. 

I'm using an EVGA nForce 780i SLI FTW motherboard. I am not using any sort of raid nore is raid enabled in the bios. Ive tried wubi, Ive tried the alternative disk, and ive tried USB all are nogos. Please can somone help me fix this issue so I can get Ubuntu installed. 

Ive previously used Ubuntu in the passed with this setup and it worked fine and I had none of these probelms however I don't remember which distro version I was using at the time. Ive tried all the modes on all methods of installation media and all of them do not work or if they do once installation is over I get a black screen.

---

### Post by dino99 on 2010-05-27
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

the actual kernel deal with video, so xorg.conf is not needed and old one often brake the process

sudo rm -f /etc/X11/xorg.conf (take note of your edid or rename to xorg.old)

your video card have no problem with nvidia synaptic package, need to install nvidia-current, nvidia-current-modaliases, nvidia-common and nvidia-settings

to built a new xorg for multi display: sudo x -configure

---

### Post by deniedproject on 2010-05-27
I'm going to try this method but it seems awfully the same as the methods I have already tried and I highly doubt its going to work.

---

### Post by darkod on 2010-05-27
You said you tried lot of parameters. Did you try using the nomodeset option? It should be available if you hit any key at the Ubuntu splash during boot, and then hit F6. After selecting nomodeset, try with Try Ubuntu option to load the live desktop.

If that works and you start the installer, don't forget that even if the disks are not used in raid right now, they would have metadata remains if they were ever used in raid. Trying to check that doesn't hurt, you can do it from live mode with:

sudo dmraid -r -E /dev/sda (and for /dev/sdb too if needed)

If it asks you to remove settings, you had metadata on it.

If that works and you install, you will need the nomodeset by editing the boot lines on first boot. After that it should detect and install a video driver and it should be fine.

But all of this is in theory. Lets see how far it gets you.

---

### Post by deniedproject on 2010-05-27
I'm trying the alternative disk this time around with the newly created partitions hopefully it works.

---

### Post by deniedproject on 2010-05-27
Just my luck the disk is bad i've seem to of scratched it since the last time I used it, I'm going to try the second theory with the live cd now. But it probably wont detect the partitions and then I'm going to have to reburn the alternative cd and try all over again. This really isn't my day lol.

---

### Post by deniedproject on 2010-05-27
Well that didn't work, it loads at the Ubuntu logo with the 5 red dots for a while and then it makes my caps lock and scroll lock key lights flash over and over and stops there. I'm really beginning to think I should just give up until I find a job and get new hardware whenever that may be.

---

### Post by darkod on 2010-05-27
> **deniedproject said:**
> Well that didn't work, it loads at the Ubuntu logo with the 5 red dots for a while and then it makes my caps lock and scroll lock key lights flash over and over and stops there. I'm really beginning to think I should just give up until I find a job and get new hardware whenever that may be.

Did you use nomodeset? Hit any key at the first logo to get a menu.

---

### Post by deniedproject on 2010-05-27
Yes I did and it allows me to see the ubuntu loading screen but it halts after a short period of loading.

---

### Post by WinRiddance on 2010-05-27
> **deniedproject said:**
> Well that didn't work, it loads at the Ubuntu logo with the 5 red dots for a while and then it makes my caps lock and scroll lock key lights flash over and over and stops there. I'm really beginning to think I should just give up until I find a job and get new hardware whenever that may be.

Sorry to hear about your difficulties. But where do you stand with your system at this very moment? You started out with primarily display issues which included boot issues. Post should always be kept down to one problem at a time in order to avoid confusing the order of relevance between the varying issues.

Having said that, I have no idea what you can or cannot do at this point ??? Can you boot up with Ubuntu at all? Which version of Ubuntu since you mentioned an earlier scratched version? What happens right now when you try to start your computer? Is there a menu that you can boot into? If your machine is several years old you may actually have to _wait several minutes_ for the boot process to complete. On some friends of ours and their 4 year old machine the boot process takes a whopping 3 minutes, but then everything is fine .... they only restart their Ubuntu once per month or so ...

---

### Post by deniedproject on 2010-05-27
My motherboard is listed in the first post i have 2x 320gb hd's and a 1x tb hd, 4gb of ram, cpu is a q6600, as stated before the video card is 8800GTS G92 512MB, i am unable to boot the live cd no matter what options i choose i always get a black screen and my monitor acts as if its getting no video signal, the alternative disk will install but after install i get the black screen again.

---

### Post by darkod on 2010-05-27
If the livecd doesn't work, most likely it won't work even after alternate install, because something is bothering it.

It's video driver issue, that's why alternate installer has no problem with it.

This thread is marked as solved for 10.04 and 8800GTS:
[http://ubuntuforums.org/showthread.php?p=9359803](http://ubuntuforums.org/showthread.php?p=9359803)

Also try searching around for that specific combination.

It's strange, other people have reported that nomodeset works, at least it would allow them to load the live mode, install, and boot once to update the driver.

But you claim nomodeset doesn't get you anywhere.

---

### Post by WinRiddance on 2010-05-27
> **deniedproject said:**
> My motherboard is listed in the first post i have 2x 320gb hd's and a 1x tb hd, 4gb of ram, cpu is a q6600, as stated before the video card is 8800GTS G92 512MB, i am unable to boot the live cd no matter what options i choose i always get a black screen and my monitor acts as if its getting no video signal, the alternative disk will install but after install i get the black screen again.
.
Well, perhaps this post might be able to help you out:
[http://forums.somethingawful.com/showthread.php?threadid=3298345&pagenumber=6](http://forums.somethingawful.com/showthread.php?threadid=3298345&pagenumber=6)

Primarily the top third of the page. If it worked before you could try using an older version of Ubuntu too of course, at least long enough until you can pinpoint the problem/solution if the above thread is no help to you ...

---

### Post by Vashtao on 2010-06-02
I have to admit that even in karmic Koala (Ubuntu version) I'm having trouble getting my quad monitor setup to work even beyond 2 monitors.  However, in regards to the issue of installing Lucid Lynx on my system I can't get it to do anymore than show the setup menu on the cd and then the loading screen.  After about 5 min or less my system simply goes into a dormant state doing little more than running fans.  The sad part is this still happens even after upgrading from Karmic.  In the end it makes little difference what I do to install 10.04 onto my system. It simply won't work at all.

Mean while in Karmic I always have trouble getting my system to actually enable all 4 monitors and i have to log in as root user to be able to actually do any configuring to get that far.  To top that off I have no sound.  So I can definitely understand your situation.  I wish there was a simple solution for these problems, but there just doesn't seem to be.  I wish they would come up with something like Xinerama and Twinview that actually supports 4 or more monitors.

my setup:

amd 965 Black edition 3.4Ghz
4Gb DDR3 Dominator memory
3 1Tb HDD 7200rpm
2 matched xfx 5770 1Gb video cards
Crosshair III Formula ASUS mobo
Soundblaster X-Fi Fatality Platinum Championship series
1000watt Ultra X3 PSU
Armor + full tower case
Coolermaster V8 CPU cooler
Plextor Blue ray burner
NEC DVD burner

Just a note the burners don't seem to fight with each other or interfere with installation of Karmic Koala and yes that is my home system.

---

