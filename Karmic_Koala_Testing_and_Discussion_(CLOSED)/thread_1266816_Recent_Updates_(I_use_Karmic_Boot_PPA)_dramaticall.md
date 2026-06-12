---
title: "Recent Updates (I use Karmic Boot PPA) dramatically decrease boot time"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2009-09-15
Wow, I'm very impressed with these latest updates. Whenever I start up my laptop now, it skips the usplash and goes straight to the xsplash, I've never seen a PC boot so fast! 

The boot developers deserve a huge pat on the back!

Lee

---

### Post by slymi2005 on 2009-09-15
Could you share the link to ppa?

---

### Post by Bucky Ball on 2009-09-15
Don't get too excited, that could change in the next update! It is Karmic, but yea, could you share the link?

---

### Post by Trevice on 2009-09-15
what ppa is that??

---

### Post by go7Ul1ai on 2009-09-15
The work done on Ubuntu boot time won't be available until Karmic Beta, but you can check out the changes using the Ubuntu-Boot PPA here:

[https://launchpad.net/~ubuntu-boot/+archive/ppa](https://launchpad.net/~ubuntu-boot/+archive/ppa)

Lee

---

### Post by yelo3 on 2009-09-15
The ppa is empty

---

### Post by go7Ul1ai on 2009-09-15
> **yelo3 said:**
> The ppa is empty

Oops, I gave you the link to the staging PPA instead of the regular one..

Here you go 'pal':

[https://launchpad.net/~ubuntu-boot/+archive/ppa](https://launchpad.net/~ubuntu-boot/+archive/ppa)

Lee

---

### Post by zika on 2009-09-15
> **lee.jarratt said:**
> Oops, I gave you the link to the staging PPA instead of the regular one..

Here you go 'pal':

[https://launchpad.net/~ubuntu-boot/+archive/ppa]("https://launchpad.net/%7Eubuntu-boot/+archive/ppa")

LeeWhat is the relation of this PPA to the "official" development of Karmic. I do not want to end up in a blind alley ... Even though I'm very interested in faster boot since the current state is ...

---

### Post by hugmenot on 2009-09-15
> **zika said:**
> What is the relation of this PPA to the "official" development of Karmic. I do not want to end up in a blind alley ... Even though I'm very interested in faster boot since the current state is ...

The uploader in this PPA is Keybuk, the main developer of boot plumbing in Ubuntu and the creator of upstart. The PPA is meant for testing things that will go into main at one point.

You can imagine that toying with and restructuring the init system can lead to wide-spread breakage when done in the main archives. This is what the PPA is for, to invite more courageous testers.

My bootchart got down to seven seconds with this PPA. But I have an SSD and disabled quite some unnecessary services.

---

### Post by zika on 2009-09-15
> **hugmenot said:**
> The uploader in this PPA is Keybuk, the main developer of boot plumbing in Ubuntu and the creator of upstart. The PPA is meant for testing things that will go into main at one point.

You can imagine that toying with and restructuring the init system can lead to wide-spread breakage when done in the main archives. This is what the PPA is for, to invite more courageous testers.

My bootchart got down to seven seconds with this PPA. But I have an SSD and disabled quite some unnecessary services.I have an itch in my fingers but not enough courage in my heart ...

---

### Post by lucazade on 2009-09-15
only the braves! :)

---

### Post by Yes_It's_Me on 2009-09-15
Yep, that was my stupid decision of the day!

The ppa broke my system :( Well at least gdm/X are grumpy and don't want to start. Hopefully it will be fixed soon and i can pull the updates down.

Dammit, I told myself that if i was ever going to do anything risky I would do it on my less-critical laptop. This happens every time! Oh when will I learn!

Thankfully I can at least boot and connect to the internet and access my data so as long as my laptop is fine it's bearable.

---

### Post by woodbj on 2009-09-15
My system broke too it's saying something about not being able to find my external hdd where i keep my /home

---

### Post by hugmenot on 2009-09-15
I think just now the PPA is inconsistent because the newest Upstart wants a mountall package that didn&#8217;t build last night.

---

### Post by Funnnny on 2009-09-15
I can't find the mountall package needed by upstart...how can i find its source :(
Edit: nvm, i found it, it's from the repo

---

### Post by slakkie on 2009-09-15
Well, revert the changes:

```

apt-cache policy upstart
upstart:
  Installed: 0.6.3-1
  Candidate: 0.6.3-2~boot11
  Version table:
     0.6.3-2~boot11 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 0.6.3-1 0
        500 http://archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```

Just wipe the packages and the ppa from your sources.list and install the packages again. This should lead you into a propper working system.

PS. BACKUP YOUR DATA FIRST WHEN EXPERIMENTING!!
Yes, that was intentional shouting.

---

### Post by orlox on 2009-09-15
The launchpad keyserver is not responding so I can't get the GPG key for now...It's like it's warning me to avoid it :P

---

### Post by Yes_It's_Me on 2009-09-15
It's a sign!

---

### Post by orlox on 2009-09-15
> **Yes_It's_Me said:**
> It's a sign!

aleluya my brother! the lord is telling us to stop using this pagan PPA

---

### Post by cyberkilla on 2009-09-15
SEVEN seconds to boot!?

Wow, anything under <30 seconds would be a dramatic improvement for me. It usually takes just over a minute.

I have an Intel Core2 Duo (1.80GHz) and 2048MB RAM.

I might try bootchart again - the last time I tried, the laptop failed to boot at all.:P

---

### Post by MacUntu on 2009-09-15
**[COLOR="Red"]Stay away from that PPA if you're not completely fine with a broken system. It may boot fast as hell but also may eat ALL your kittens![/COLOR]**

---

### Post by b3n87 on 2009-09-15
> **cyberkilla said:**
> SEVEN seconds to boot!?

Wow, anything under <30 seconds would be a dramatic improvement for me. It usually takes just over a minute.

I have an Intel Core2 Duo (1.80GHz) and 2048MB RAM.

I might try bootchart again - the last time I tried, the laptop failed to boot at all.:P

No way, are you using a SSD or a SATA Hard Drive? What graphics card you got?

---

### Post by cyberkilla on 2009-09-15
> **b3n87 said:**
> No way, are you using a SSD or a SATA Hard Drive? What graphics card you got?

Sony Vaio VGN-AR41E
- NVidia 8400M GT (256MiB, I think)
- Intel Core2 Duo @ 1.80GHz
- Seagate HDD, 5400 RPM
- 2048 MiB Kingston RAM

---

### Post by MacUntu on 2009-09-15
> **Funnnny said:**
> I can't find the mountall package needed by upstart...how can i find its source :(
Edit: nvm, i found it, it's from the repo

How did you install it? Just did the upgrade and realized upstart didn't get upgraded because of mountall missing.

---

### Post by b3n87 on 2009-09-15
> **cyberkilla said:**
> Sony Vaio VGN-AR41E
- NVidia 8400M GT (256MiB, I think)
- Intel Core2 Duo @ 1.80GHz
- Seagate HDD, 5400 RPM
- 2048 MiB Kingston RAM

7 Seconds on spinning media is insane.

Kudos FOSS devs

---

### Post by cyberkilla on 2009-09-15
> **b3n87 said:**
> 7 Seconds on spinning media is insane.

Kudos FOSS devs

Ah, you misunderstand me. Sorry about the wording of my previous post.

I was trying to say that 7 seconds was amazing, and that I'd be happy with anything under 30 seconds on my own computer:P

The other guy, a few posts before mine, claims to be getting his booted in 7 seconds. Sounds hard to believe. He must have removed half of his system to achieve that:)

---

### Post by gnomeuser on 2009-09-15
> **MacUntu said:**
> **[COLOR="Red"]Stay away from that PPA if you're not completely fine with a broken system. It may boot fast as hell but also may eat ALL your kittens![/COLOR]**

That's okay I have no kittens

---

### Post by MacUntu on 2009-09-15
Lost them already? :lolflag:

Edit: according to [https://launchpad.net/~ubuntu-boot/+archive/ppa](https://launchpad.net/~ubuntu-boot/+archive/ppa) the packages mountall and sysvinit failed to build. Guess I'll just have to wait.

---

### Post by Starks on 2009-09-15
> **orlox said:**
> The launchpad keyserver is not responding so I can't get the GPG key for now...It's like it's warning me to avoid it :P
why aren't you using the ppa:*name of ppa here* method for adding sources? it grabs the key automatically.

---

### Post by Starks on 2009-09-15
btw, booting in recovery mode will let you reach the desktop if the updates broke your system.

---

### Post by Vanishing on 2009-09-15
> **Starks said:**
> btw, booting in recovery mode will let you reach the desktop if the updates broke your system.

lol..good to hear that..:lolflag:

---

### Post by Yes_It's_Me on 2009-09-15
hmm really? when i try it seems to get stuck at "loading sambadaemons or something" and doesn't appear to do much. I can use the ttys but as far as gdm or do a startx, no go.

---

### Post by Schendje on 2009-09-15
> **Starks said:**
> btw, booting in recovery mode will let you reach the desktop if the updates broke your system.

That didn't work for me... It tries to boot but the last thing it says is:

```
init: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```
...And then it shows the login prompt. After logging in it can't connect to do an apt-get update or anything.

Ah well, this is my testing machine. :P

Before I added the PPA though, everything was fantastic! Nvidia driver installations have an actual loading bar now, and switching between normal/extra effects is very smooth!

---

### Post by Funnnny on 2009-09-15
> How did you install it? Just did the upgrade and realized upstart didn't get upgraded because of mountall missing.
Can't build a deb from it :(, maybe I have to wait

---

### Post by Vanishing on 2009-09-15
any updates?
using backtrack atm...
obviously that means if you do restart, you won't get into the system again(not even with recovery mode), and by not getting into the system i meant can't startx..lol
=.=update update update..

---

### Post by hugmenot on 2009-09-15
> **cyberkilla said:**
> SEVEN seconds to boot!?

> **cyberkilla said:**
> The other guy, a few posts before mine, claims to be getting his booted in 7 seconds. Sounds hard to believe. He must have removed half of his system to achieve that:)

Seven seconds /in the bootchart/. I have no idea when it stops counting. To get to the desktop it takes a bit longer. But even there I trimmed it down.

Things I removed from startup (still installed): eth0, fingerprinter, cdrom, bluetooth, cups, samba, winbind, cryptdisks, couple of modules (modprobe takes up a lot of the time booting), gdm user list, usplash.

Things uninstalled: modemmanager (takes too long), ubuntu-one, all accessibility stuff (braille, text2speech, etc), unnecessary panel applet gimmicks (fusa, indicator, etc).

But I still use: tomboy, gnome-do, globalmenu, gajim. quite alot of stuff actually.

---

### Post by VMC on 2009-09-15
> **Starks said:**
> btw, booting in recovery mode will let you reach the desktop if the updates broke your system.

How is that possible if this ppa borked the system?

---

### Post by hugmenot on 2009-09-15
> **VMC said:**
> How is that possible if this ppa borked the system?

As far as I know recovery mode (the "single" kernel option) also uses the init system.  So, some "more advanced" recovery methods have to be used. Like booting from live CD and chrooting the local disk to fix breakage. Nothing for weak nerves, I guess.

---

### Post by Funnnny on 2009-09-15
Any workaround to solve that problem ?
Tries to compile mountall myself, but I can't make deb package

---

### Post by zika on 2009-09-15
I did not use aforementioned PPA. This mess is a result od "official" upgrades" today ...

---

### Post by abstractor on 2009-09-15
That's right, it seems that Karmic Boot PPA is getting at least something merged to Karmic. I'm also having some problems related to this, particularly not being able to update to latest upstart because of missing mountall. It seems that just 7 minutes ago, though, mountall was built. I'll see if the mess cleans up by itself now.

---

### Post by Vanishing on 2009-09-15
> **abstractor said:**
> That's right, it seems that Karmic Boot PPA is getting at least something merged to Karmic. I'm also having some problems related to this, particularly not being able to update to latest upstart because of missing mountall. It seems that just 7 minutes ago, though, mountall was built. I'll see if the mess cleans up by itself now.

i dont see it built in the PPA...o.o:(
where did you see that? the mountall built.

---

### Post by portis on 2009-09-15
> **Vanishing said:**
> i dont see it built in the PPA...o.o:(
where did you see that? the mountall built.

[https://launchpad.net/ubuntu/+source/mountall/0.1.3](https://launchpad.net/ubuntu/+source/mountall/0.1.3)

---

### Post by Vanishing on 2009-09-15
> **portis said:**
> [https://launchpad.net/ubuntu/+source/mountall/0.1.3](https://launchpad.net/ubuntu/+source/mountall/0.1.3)

Got it..ty!

now my box is back!
but the boot speed is the same i think...o.o

---

### Post by abstractor on 2009-09-15
Well, after manually adding mountall deb I managed to update upstart, but now my system won't boot X-(

Luckily I have a live system on a USB drive, so I'm using that at the moment. It seems there are still missing dependencies to upgrade all packages, namely latest initscripts depends on unavailable versions of rsyslog and udev.

---

### Post by Vanishing on 2009-09-15
> **abstractor said:**
> Well, after manually adding mountall deb I managed to update upstart, but now my system won't boot X-(

Luckily I have a live system on a USB drive, so I'm using that at the moment. It seems there are still missing dependencies to upgrade all packages, namely latest initscripts depends on unavailable versions of rsyslog and udev.

lol..i fixed the problems and are able to get my normal box back.

---

### Post by MacUntu on 2009-09-15
Boot time increased for me:

* Full boot to desktop
- before: 26s
- after: 28s

Maybe GRUB->GDM got faster but I'm not interested in that timespan.

---

### Post by garba on 2009-09-15
is all this fast boot goodness expected to be included in the upcoming alpha6 release or it's just a proof-of-concept?

---

### Post by Vanishing on 2009-09-15
> **MacUntu said:**
> Boot time increased for me:

* Full boot to desktop
- before: 26s
- after: 28s

Maybe GRUB->GDM got faster but I'm not interested in that timespan.

same, it seems to be a increase...

---

### Post by Funnnny on 2009-09-15
So the mountall package live in main repo.
But the performance is not really great, though..

---

### Post by Vanishing on 2009-09-15
this is really getting on my nerves:
i kept getting this fsck message everytime i reboot......:confused:

---

### Post by Kamilion on 2009-09-15
Ahoy there! 

Just a little note, not all of the necessary packages have shown up in the main repositories yet.

Hold off on upgrades today (09-15-09) until they're all built and released.

Check here for more details of the merge from the ubuntu-boot PPA to karmic repos:

[https://bugs.launchpad.net/bugs/427356](https://bugs.launchpad.net/bugs/427356)

As of my typing this, we're still missing the following packages for upstart to work properly:

apport
at
avahi
cron
cryptsetup
cups
gdm
hal
network-manager
procps
sreadahead
usplash
util-linux

Here is the complete list of packages affected by this merge AFAIK:

acpid
anacron
apport
at
avahi
cron
cryptsetup
cups
dbus (dbus, dbus-x11 & libdbus-1-3)
debhelper
gdm
hal
hostname
ifupdown
initscripts
initramfs-tools
module-init-tools
netbase
network-manager (libnm-util1)
procps
rsyslog
sreadahead
sysvinit (sysvinit-utils)
udev (udev & libudev0)
upstart
usplash
util-linux



Good luck, and DO NOT UPDATE until you see gdm, dbus, and hal packages with changelogs indicating upstart jobs. Missing these are what is preventing X from coming up on startup.

---

### Post by Kamilion on 2009-09-16
Seems to be all cleared up now.

---

### Post by tretle on 2009-09-16
Can anyone confirm that the packages are now working?
Looks like the repo is empty?

---

### Post by xens on 2009-09-16
yop! did the updates 10 minutes ago and it works now :]

gr888888888888 :guitar::guitar::guitar::guitar:

---

### Post by tretle on 2009-09-16
The updates to the repo which was given at the start of the thread? the boot repo? It looks empty to me on both launchpad and through update manager.

---

### Post by Schrotthaufen on 2009-09-16
On my Laptop (Lenovo W500 NRA4MGE) boot time decreased from alpha4 to today from 5,60(a4) to 4,4(yesterday) to 3,44 seconds(today).
With an Intel X25-M 80GB SSD of course...

Bootcharts can be found here:
[http://forum.ubuntuusers.de/topic/bootchart-wer-hat-den-schnellsten/16/#post-2147688](http://forum.ubuntuusers.de/topic/bootchart-wer-hat-den-schnellsten/16/#post-2147688)

---

### Post by Yes_It's_Me on 2009-09-16
Yeah, it's working fine now with the latest updates that came out a few hours ago. All good now. My bootspeed is around the same as before, maybe a touch faster but that might just be a placebo.

---

### Post by MacUntu on 2009-09-16
> **Schrotthaufen said:**
> Bootcharts can be found here:
[http://forum.ubuntuusers.de/topic/bootchart-wer-hat-den-schnellsten/16/#post-2147688](http://forum.ubuntuusers.de/topic/bootchart-wer-hat-den-schnellsten/16/#post-2147688)

You need to be loggind in to see the post. Inyoka sucks! :P

---

### Post by abstractor on 2009-09-16
After upgrading my system to latest versions of packages a couple of hours ago made my system boot again, glad to be back :)

I noticed that there is a new .legacy-bootordering file in /etc/init.d, can anyone explain what it does, or point me to where this and perhaps more on the subject is already explained?

> Hold off on upgrades today (09-15-09) until they're all built and released.

Thanks for the heads up :D

---

### Post by MacUntu on 2009-09-16
> **MacUntu said:**
> Boot time increased for me:

* Full boot to desktop
- before: 26s
- after: 28s

Maybe GRUB->GDM got faster but I'm not interested in that timespan.

Too complete the data:

* before: 26s
* half-merged: 28s
* after: 31s
* after, running sreadahead with the --no-fork option (I'm using a HDD): 27s

That's the first time I see sreadahead running in the foreground being faster than running in the background (default). Good job! :)

---

### Post by tekstr1der on 2009-09-16
I waited with much eagerness while the dependencies resolved yesterday before performing any updates. Per the topic of this thread, I was excited to finally witness some decreased boot time. If anything about Karmic has regressed for me from previous releases this is it. On at least three separate occasions, changes have come down that have dramatically INCREASED boot time, both from GRUB to GDM and even more so, from GDM to desktop.

Intrepid:
Grub -> GDM: 28s
GDM -> Desktop: 16s
Total Boot: 44 seconds

Karmic (2009.09.16):
Grub -> GDM:58s
GDM -> Desktop:41s
Total Boot: 99 seconds

This is just horrendous. I have only one panel with only the clock applet and notification area. Not much else I can trim there. Thinking that this could have something to do with upgrading from previous releases, I have periodically clean-installed alphas and daily CD images in a virtual machine to verify things slowing down from Intrepid release clean install. I am very confused as to how people are really obtaining faster boot here? My total boot has more than doubled. I really would not care if this was a desktop that rebooted every blue moon, but unfortunately it's my laptop, so I suspend often to avoid the reboot.

As an OT aside, the whole partial distribution upgrade thing should really be a sticky here, as many seem to just dive right in and break stuff.

---

### Post by Kamilion on 2009-09-16
> **Starks said:**
> why aren't you using the ppa:*name of ppa here* method for adding sources? it grabs the key automatically.

How exactly does one do this?

> **tretle said:**
> Can anyone confirm that the packages are now working?
Looks like the repo is empty?

> **tretle said:**
> The updates to the repo which was given at the start of the thread? the boot repo? It looks empty to me on both launchpad and through update manager.

The boot-ppa repo is now empty as it's been merged into the main karmic package stream, causing some havok.



Everything seems a bit better today.

Some notes:
It didn't automatically pick up my br0 definition in /etc/network/interfaces.

Was triggerable by "start networking" which does an ifup -a

Starting a specific network device is now
"start network-interface INTERFACE=eth0"

To list upstart jobs:
initctl list

Other upstart commands:
"start <job>", "stop <job>" "status <job>"
These can be used at a prompt or through initctl:
"initctl status gdm" is the same as "status gdm"

The rest of the old init scripts are ran from upstart.
/etc/init/rc.conf seems to trigger this.

Packages with upstart jobs make a link in /etc/init.d/ to /lib/init/upstart-job for sysv coexistance.

Attempting to interact with upstart jobs with "service <job> status" or similar will throw information on stdout about using 'status <job>' but it will still work.

Attempting to interact with sysv tasks with "status <task>" throws an error, such as "status: Unknown job: ssh".

Currently 'service' will work with both sysv initscripts and upstart jobs, but 'status' will only work with upstart jobs.

---

### Post by Podex on 2009-09-16
> **Kamilion said:**
> How exactly does one do this?


```
sudo add-apt-repository ppa:'name-of-ppa'
```

Example:

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily
```

---

### Post by Taoye on 2009-09-17
I got a SSD recently and here's my bootchart with Karmic Alpha 5 (upgrade current as of this morning)... I'm lovin' it! 

:guitar:

(I disabled sreadahead because it was actually adding a second to my boot time...)

---

### Post by artir on 2009-09-17
> **Taoye said:**
> I got a SSD recently and here's my bootchart with Karmic Alpha 5 (upgrade current as of this morning)... I'm lovin' it! 

:guitar:

OMG 4 friggin seconds, that's crazy, you did any tweak to the base installation?

---

### Post by MacUntu on 2009-09-17
Would be more interesting how long your total boot time is. You can add "bootchart=nostop" to the kernel line of your GRUB entry to make bootchart run until you stop it manually ('sudo /etc/init.d/stop-bootchart start' or 'sudo start stop-bootchart' - don't know how it works after the upstart merge).

Do want SSD now! :D

---

### Post by bear24rw on 2009-09-17
> **Taoye said:**
> I got a SSD recently and here's my bootchart with Karmic Alpha 5 (upgrade current as of this morning)... I'm lovin' it! 

:guitar:

(I disabled sreadahead because it was actually adding a second to my boot time...)

Are you using the PPA? What did you tweak?

---

### Post by zika on 2009-09-17
> **Taoye said:**
> (I disabled sreadahead because it was actually adding a second to my boot time...)How did You manage to disable it ... ?

---

### Post by MacUntu on 2009-09-17
> **zika said:**
> How did You manage to disable it ... ?

It should be sufficient to rename the file /etc/init/sreadahead.conf to something that doesn't end with '.conf'.

---

### Post by bear24rw on 2009-09-17
> **MacUntu said:**
> It should be sufficient to rename the file /etc/init/sreadahead.conf to something that doesn't end with '.conf'.

do you replace sreadahead with regular readahead, or do you just not have a readahead at all?

---

### Post by Taoye on 2009-09-17
> **MacUntu said:**
> Would be more interesting how long your total boot time is. You can add "bootchart=nostop" to the kernel line of your GRUB entry to make bootchart run until you stop it manually ('sudo /etc/init.d/stop-bootchart start' or 'sudo start stop-bootchart' - don't know how it works after the upstart merge).

Do want SSD now! :D

I added this to grub.cfg, booted, and then stopped bootchart using the first command you listed. No .png was generated. When I run the bootchart command to generate one, I get an error:

```
root@ckahn-X61s:/home/ckahn# bootchart
Parsing /var/log/bootchart
Sep 17, 2009 3:48:41 PM org.bootchart.Main render
WARNING: Unknown log file: ckahn-X61s-karmic-20090917-6.tgz
Sep 17, 2009 3:48:41 PM org.bootchart.Main render
WARNING: No process samples
Wrote image: ./bootchart.png
root@ckahn-X61s:/home/ckahn# 

```

Dunno what the fail is about, as when I boot up without the nostop thing it makes the image file normally...

To disable sreadahead I commented out the "exec /sbin/sreadahead -t 0" line in /etc/init/sreadahead.conf.

I installed via the alpha 5 live CD and did an apt-get upgrade this morning... I also uninstalled xsplash because for some reason it's waiting until it automatically connects to my wireless network before showing me a usable desktop (which was causing an extra 10 seconds delay). The only other thing I've changed was the boot concurrency option in /etc/init.d/rc. In total from power on to a usable desktop it's ~16 seconds... most of which is BIOS stuff, etc.

I can attach my bootchart .tgz file if somebody else wants to generate the .png...

---

### Post by MacUntu on 2009-09-17
Would be nice and maybe that's a bug in bootchart?

---

### Post by zika on 2009-09-17
> **MacUntu said:**
> It should be sufficient to rename the file /etc/init/sreadahead.conf to something that doesn't end with '.conf'.

> **Taoye said:**
> To disable sreadahead I commented out the "exec /sbin/sreadahead -t 0" line in /etc/init/sreadahead.conf.

I also uninstalled xsplash because for some reason it's waiting until I connect to my wireless network before showing me a usable desktop (which was causing an extra 10 seconds delay).
Thank You, I will try these suggestions.

---

### Post by Taoye on 2009-09-17
The nostop .tgz file is 2.3 MB... I think it's too big for forum attachments... Gotta go for now, will report back later.

---

### Post by Taoye on 2009-09-18
I think it might be a problem with java, not bootchart itself... I'm getting similar errors about class main with other programs, too. Also getting the same errors when I try to run it off a Jaunty live CD session. Oh well... if someone wants to check out my bootchart .tgz I can e-mail it to them.

I'm sooo looking forward to the final Karmic release.

---

### Post by MacUntu on 2009-09-18
If it's Java, you could try the package pybootchartgui instead (will replace the Java part of bootchart).

> I'm sooo looking forward to the final Karmic release.

I'm sooo looking forward to the final Karmic+1 release - IMO the release after Karmic will be a real blast. :)

---

### Post by Sashin on 2009-09-18
Karmic+2 will own, that's when the software store will be finished.

---

### Post by go7Ul1ai on 2009-09-18
I reckon Karmic+3 will be the ultimate release though

---

### Post by Sashin on 2009-09-18
Yeah, you're right I can feel it. 

2012: The year of the linux desktop.

---

### Post by wilbur.harvey on 2009-09-18
Too bad it is still much slower than the same laptop booted with Jaunty before the upgrade yesterday.

---

### Post by Funnnny on 2009-09-19
Lol, Linux will not get much attention in the near future, even if it's good, it's secure or whatever it is. Just because there's Microsoft :(.
But I'm glad that when Linux getting better, Windows is getting worse, hope at least 10% computers will install Linux in next 5 years :P

---

### Post by Sashin on 2009-09-19
That's a big ask. 10%

---

### Post by Funnnny on 2009-09-19
That's our hope :P, 10% in 5 years :P

---

