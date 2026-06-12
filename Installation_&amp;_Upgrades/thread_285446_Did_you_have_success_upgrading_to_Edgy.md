---
title: "Did you have success upgrading to Edgy?"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by kwilliam on 2006-10-26
Because Edgy was supposed to be more, well, "edgy", I wondered how things were going.

I'll try to turn this into a poll if I can figure out what button to press.

---

### Post by nu2this on 2006-10-27
No vote by me yet haven't installed this is just a bump

---

### Post by cuplex on 2006-10-27
well using the livecd no chance installing it! everytime getting no screens error from X. when i used aptitude on my dapper no problem! well almost none i had to reconfigure my xserver! and i can not install the ati proprietary drivers as i did in dapper!

---

### Post by gabrieliscool on 2006-10-27
problems with my edgy install:
Nvidia Driver Wont Load Correctly (Hopefully i'll Get it Workin' soon)
Some Themes Look "Wrong"(The Loading bar doesn't show up and some gtk2.0 themes dont look like gtk2.0 themes, actually, more like gtk1.0 themes; although that might be a gnome problem)

that's it, my only problems.
they can probably be fixed in an update

---

### Post by supergrapeman on 2006-10-27
wireless card stopped working => no internet access.

had to switch to use ndiswrapper. Apart from that, all ok.

(there seem to be a lot of people with this issue. my card, a netgear wg311t uses the atheros chipset which has worked perfectly under dapper, breezy, hoary..)

---

### Post by mixmaster on 2006-10-27
I was running the last beta and upgrade from that was no problem.

Comes to that, upgrade from dapper to the final beta was problem free as well.

---

### Post by coastdweller on 2006-10-27
The upgrade caused an unstable system that forced me to reinstall.

---

### Post by boban on 2006-10-27
I tried updating using aptitude... I had serious problem with unmet dependencies... So I've download iso image and made clean install... Now I'm installing and configuring all the programs I need...

---

### Post by Soarer on 2006-10-27
No problems with the Aptitude upgrade from Dapper to Edgy. No wireless or advanced graphics in my system though.

---

### Post by tjansson on 2006-10-27
I made an apt-get upgrade and had problems with the samba package and with the xorg after install. Nothing that couldn't be fixed but it added 1 hour to the installation.

---

### Post by 5-HT on 2006-10-27
> **boban said:**
> I tried updating using aptitude... I had serious problem with unmet dependencies... So I've download iso image and made clean install... Now I'm installing and configuring all the programs I need...

Were the unmet dependencies related to python at all? 
I simulated a dist-upgrade using aptitude and encountered some issues with python packages and upstart. Simulating a simple upgrade seems to avoid the unmet dependencies, but I'm not sure if I should take the risk of doing that before the dist-upgrade and end up with a broken system.

I'd rather upgrade with aptitude instead of apt or update-manager in terms of package management down the road, but then again I'm not really looking forward to a clean install at this time.

Anyone managed to perform a successful dist-upgrade from Dapper using aptitude?

** EDIT: missed Soarer's post**

[quote=Soarer]No problems with the Aptitude upgrade from Dapper to Edgy. No wireless or advanced graphics in my system though. [/quote]

Were there no unmet dependencies or conflicts at all, or did you manage to update a few times and sort everything out in the end?

---

### Post by mr_fong on 2006-10-27
X broke. Since 1999 I've been using Debian and with every upgrade X broke. I thought I'd try (K)Ubuntu because of it being called the next best thing to sliced bread and.... X broke. Problem is that I haven't set up X since the days of XF86, so what happened to xf86cfg? Is there already a magical commandline tool to autodetect X and get it working within a minute?

Scim also gave a lot of errors, but that is minor of course, since without X I can't use scim anyway :-]

Otherwise no realy harm done. SAMBA and CUPS upgraded nicely, so I could access all my data from my wife's laptop.

Cheers,

Hans

---

### Post by yabbadabbadont on 2006-10-27
xorgcfg or xorgconfig do the same thing these days.  :)

---

### Post by mr_fong on 2006-10-27
So why can't I find xorgconfig and xorgcfg? Is there a specific deb-package I missed? I'm behind a Dapper Drake live-CD right now, so not my home system (I'm supposed to be working in a Windows only school ;-), but here I can't find them here either. --H

---

### Post by frodon on 2006-10-27
Did a dist-upgrade, no problem at all except with my generic kernel but it was before the official release.

---

### Post by yabbadabbadont on 2006-10-27
> **mr_fong said:**
> So why can't I find xorgconfig and xorgcfg? Is there a specific deb-package I missed? I'm behind a Dapper Drake live-CD right now, so not my home system (I'm supposed to be working in a Windows only school ;-), but here I can't find them here either. --H

Sorry, for some reason Ubuntu doesn't appear to have included these programs (which are a standard part of xorg...).  Looks like you will need to read the xorg.conf man page and try to work from that.

EDIT: a quick search turned up [this](http://www.ubuntuforums.org/showpost.php?p=501525&postcount=3).  I guess Debian has to do things differently than everyone else.  :D

---

### Post by 5-HT on 2006-10-27
[quote=mr_fong]So why can't I find xorgconfig and xorgcfg? Is there a specific deb-package I missed? [/quote]
 
You could  try:
```
 sudo dpkg-reconfigure xserver-xorg
```If you wanted to manually edit xorg.conf, you can find the file residing within /etc/X11/

Edit: too slow.

---

### Post by ASUmusicMAN on 2006-10-27
Upgrading with apt broke my X; I can't login and don't receive any prompt so it looks like i'm back to square one.  I also had busted python dependencies during my update.  I'll probably just reinstall from the iso now...damn.

---

### Post by cyriq on 2006-10-27
I tried to upgrade to edgy, normally I get no problems however the computer hangs under upgrade while trying to upgrade the nfs and my dapper installation is completly dead ](*,).

---

### Post by mr_fong on 2006-10-27
Thanks for the help. It is indeed wonderful that Debian does things differently ](*,) Keeps computing fun, right? --H

---

### Post by n00buntu on 2006-10-27
After rebooting, getting various messages (e.g., "can't find theme human"), then a login screen with all disabled fields. Can't login, given up, and will just reinstall.

Sincere thanks to the edgy guys, but must say a little disappointed after breezy->dapper went so smoothly.

---

### Post by litemotiv on 2006-10-27
after reading (all) these horror stories and having strangled a previous dapper install trying to upgrade to edgy beta i think i'll sit this one out for a while.

my aptitude simulation gives me back this:

```

Remove the following packages:
libvte4

Keep the following packages at their current version:
freeloader [0.3-3 (now)]
hpijs [2.1.7+0.9.7-4ubuntu1 (now)]
laptop-mode-tools [1.11-1ubuntu3 (now)]
libgda2-3 [1.2.2-1ubuntu2 (now)]
mdadm [1.12.0-1ubuntu5 (now)]
python-htmlgen [2.2.2-10ubuntu3 (now)]
python-libxml2 [2.6.24.dfsg-1ubuntu1 (now)]
python2.4-htmlgen [2.2.2-10ubuntu3 (now)]
python2.4-libxml2 [2.6.24.dfsg-1ubuntu1 (now)]
startup-tasks [Not Installed]
system-services [Not Installed]
ubuntu-desktop [0.120 (now)]
ubuntu-minimal [0.120 (now)]
upstart [Not Installed]
upstart-compat-sysv [Not Installed]
upstart-logd [Not Installed]

Downgrade the following packages:
libgl1-mesa-dri [6.5.1+cvs20060824 (now) -> 6.5.1~20060817-0ubuntu3 (edgy)]

Leave the following dependencies unresolved:
nautilus recommends fam
Score is -1411

```

and together with the kernel and X problems mentioned by others this looks like a disaster waiting to happen...

---

### Post by zba78 on 2006-10-27
Upgraded Kubuntu on my Acer laptop last night following instructions from [http://kubuntu.org/announcements/6.10-release.php](http://kubuntu.org/announcements/6.10-release.php) 

Downloaded about 850 MB, rebooted and all seems to be perfect. Glad the monitor brightness can now be set.

New splash screen seems nice (although the progress bar does look a little too much like WinXP for my liking).

The only problem I've encountered is why my various hot-key have stopped working (although this isn't a show-stopper).

Wireless, power features, fglrx etc. works fine. Absolutely love the fact that Hibernate/Suspend works out of the box

---

### Post by macogw on 2006-10-27
Nautilus, Inkscape, Blender, and XChat are all broken.  There's probably more that I haven't found yet :(  It seems to be halfway between Dapper and Edgy.  I'm using the update manager to try the distro-upgrade all over again.  I originally did it from a cd.  Attempts to apt-get those apps come up with all 0's for upgrade, install, remove, etc. and I did enable all of the (edgy) repositories.

---

### Post by boban on 2006-10-27
> **5-HT said:**
> Were the unmet dependencies related to python at all? 
I simulated a dist-upgrade using aptitude and encountered some issues with python packages and upstart. Simulating a simple upgrade seems to avoid the unmet dependencies, but I'm not sure if I should take the risk of doing that before the dist-upgrade and end up with a broken system.


Among other I had issues with some downgraded -dev packages... It was problem in dapper too (I had to downgrade some packages [ubuntu specific versions] to install other)

---

### Post by aos101 on 2006-10-27
> **frodon said:**
> Did a dist-upgrade, no problem at all except with my generic kernel but it was before the official release.
For my Kubuntu upgrade for some reason it installed a 386 kernel and used that as the default instead of the generic kernel, and when I try loading the generic kernel from grub it just gives a black screen with flashing cursor (kernel log shows no entries for the boot).  Its loads OK with the 386 kernel but slower than 6.06 (running a 686 kernel), so I'll grab the ISO and do a reinstall later.

Edit: Found [this](http://www.ubuntuforums.org/showthread.php?t=282956&highlight=generic+kernel) which looks like it might fix it.

---

### Post by kamstrup on 2006-10-27
I haven't even been able to install Edgy at all. I have a AMD64 and tried i386-desktop, amd64-desktop, and amd64-alternate cds. All crashed at some point during the installation.

i386-desktop: Hang during package installation. Hard reboot only solution. Also tried vesa driver - same result.

amd64-desktop: Black screen after a bugged out black-white usplash

amd64-alternate: hang during apckage installation

**Conclusion:** Disaster.

**Note:** Dapper i386 runs fine on this box.

---

### Post by g3k0 on 2006-10-27
I cant download the whole thing my proxy filter stops me because it parses words and misinterpreted something :(

---

### Post by mikeymikec on 2006-10-27
With a Dell C400 laptop and an almost out-of-the-box install of Dapper (I installed vlc, changed font sizes through UI, that was about it), I've ended up without a working GUI ("failed to start the X server").  It won't accept my password (keys seem to be randomly not working, and pressing return first time after putting in the password does nothing.  press it again and I get 'incorrect password').

- edit - I successfully sudo'd on the next reboot, for lack of a better idea (the X log showed nothing that I could discern to be useful), I did 'sudo apt-get dist-upgrade'.  That installed a few more things.  Rebooting atm, but the outcome is... even funkier than before.

I think I'll be asking in the newbie forum if I can save this installation somehow (unless anyone here wants to help me? :-) ).

---

### Post by Tux Aubrey on 2006-10-27
Have upgraded (or fresh installed) three machines now.

1. Upgrade did not work at all for me on a Compaq Presario 900 laptop - upgrade could not "calculate upgrade".  A fresh install worked fine - including getting the Netgear WG511 v2 PCMCIA wireless card working with ndiswrapper.

2. A fresh install of RC1 on a second hdd on my main P4 machine went smoothly.  I went as far as installing Beryl on this one and it rocks.

3. A fresh install on my son's brand new machine - ASROCK Mb/Athlon 3500+/SATAII - went well until trying to get wireless to work - A D-Link PCI card with an RT61 chipset - no progress at all despite compiling new native drivers - I gather this might be a genuine bug rather than lack of skill on my part.  This machine, while incredibly fast, takes 2 minutes to boot edgy because it timeouts trying to find SATA drives on the three empty plugs (or that's all I can put it down to). I'm still waiting for a response to posts on both the wireless and SATA issues.  This SATA thing may very well be one of those F00-L problems I've had before, but it would be good to get it sorted.

---

### Post by mikeymikec on 2006-10-27
I'm now doing a clean install of 6.06 on my laptop, and 6.1 on my test PC, then do an upgrade to 6.1 on my laptop (as admittedly it did hibernate during installation, and hibernate doesn't seem to work very well on my Dell C400).  See how it goes.

---

### Post by YorYor on 2006-10-27
Ok for me generally.

Upgraded a Server installation without any apparent problems (as yet, fingers crossed!).

My laptop upgrade was generally ok too, except for a few things:

1. ndiswrapper needed to be "upgraded" manually. For some reason, aptitude didn't uninstall the dapper version and install the edgy one; I had to do it manually in synaptic when ndiswrapper wouldn't load after upgrade.

2. the hicolor 48x48 mimetype icons got wiped. Seems like a bug that's already been filed, but given low priority. Bah. Shouldn't instances like this be more important than some obscure bug that happens only with a specific file with specific content which probably 90% of users won't experience?

Other than those 2 since my upgrade 6 hours ago, I think Edgy is indeed a better distro than Dapper.

---

### Post by morequarky on 2006-10-27
My install would have gone perfectly if I hadn't been so ignorant and read the WHOLE howto and not just step four.

I downloaded the alternative CD and was going to update that way.  SO I just skipped down to that step and started upgrading from the CD.

Rebooted...to a prompt, no Xwindows.

Now a few months ago I would have gone nuts, but I had read some place about what some others had dealt with in installing Brezy, anyway, I installed lynx and got back to the forum quick like and saw that I needed to follow steps 2 and 3.  So I did, rebooted.

...to a prompt AGAIN.  "lynx ubuntuforums.org" again.  This time seeing that I also needed to follow step one.  So I followed step one, two, three, four in order.  And rebooted.

Bingo.  Edgy works fine.  But I can imagine someone going nuts if their install ended up going to a prompt.

Good luck ya'll.

---

### Post by bean1975 on 2006-10-27
Needed to run apt-get dist-upgrade and apt-get  -f a few times and then a few settings got lost during the process but nothing serious. I am overly extremely satisfied by the smoothness of the upgrade.

---

### Post by GSMD on 2006-10-27
The upgrade has prought my server installation to knees. Even after the OS has been reinstalled, the 5 drives that had RAID5 on them aren't detected as they have any partition table at all and system startup lasts for ages. After it has booted, raid5 is functional though.

So far, not good at all. Anyways, I'll try a clean install with all of my hard drives repartitioned.

---

### Post by ZagiFlyer on 2006-10-27
Initially, when the system started I got no display at all after grub kicked off the kernel. As soon as it would have gone to the splash screen the display went blank and I was SOL.

I restarted in recovery mode and found that the upgrade botched the xserver upgrade and configuration. I re-installed the xserver and it still didn't work, so I editied xorg.conf to use the VESA driver, which worked.

When I restarted, the display still went blank, but when X started it came back on. I then installed the fglrx package to get a decent screen resolution. I tried to install the ATI binary drivers from the ATI website, but the installer said something like "bad substitution" and bailed out.

I still don't get the splash screen during startup and shutdown, but I can work on that.

---

### Post by theosib on 2006-10-27
Looks like anyone using software RAID is having trouble as well.  Although I had reported bugs in that while Dapper was in beta (!), they still haven't been addressed in Edgy stable.

---

### Post by jsully1 on 2006-10-27
I had a miserable time trying to get the ATI drivers to work - it seems that the glx library didn't match the kernel driver version - the kernel driver was older than the library.  Tons of trouble getting it to even boot initially as well.  Overall I'm extremmly unhappy with the upgrade process, and will be afraid to do it again in 6 months.  Also, Upstart doesn't seem to have done much... my dual core IBM T60 is actually taking a good 15 seconds longer to boot.  Sorry for the negativity - I do love the software, and the people behind it.
Now that it's up and running, I have to say it's working great, and I am once again thrilled to be running Ubuntu.

---

### Post by jem7v on 2006-10-27
I upgraded from 6.06 with the alternate install CD rather than over the web.
When it asked me whether to keep my old Gnome configurations or take the new ones it gave me the option to view the differences. I chose that option and it abruptly crashed the update process. Yikes.

So I started it over and it came up with some brutal errors by the end of it, warning me that my system may not be bootable. I took my chances and started it back up...

Long story short, I ran into this message: "API mismatch: the NVIDIA kernel module is version 1.0.8762, but this X module is version 1.0.7174. Please be sure that your kernel module and all NVIDIA driver files have the save driver version." i.e., this means I could only run in a terminal... It took me a long time to solve, but I used tseliot's Envy script to uninstall and subsequently reinstall my video drivers, which removed the kernel incompatibility and left me with a different problem: X couldn't properly locate my NVidia drivers or something. So then I just switched from the nvidia driver to nv in xorg.conf and it booted up fine. I still need to get the proper drivers working yet - just using the generic one right now.

I, uh, didn't realize it was going to uninstall so many programs, though.... had to reinstall Abiword, NoteEdit, Lilypond, and amarok, and all the games that came with 6.06 disappeared. (On the other hand, I didn't play half of those games anyway, so now that the package of all of them is gone I can just install things I want.)

All in all, the video driver issues were nothing I hadn't experienced before, but I'm a bit frustrated that it didn't install the latest x module kernely thingy at the same time as it installed the latest nvidia drivers. Also, I really had no idea it was going to remove so many programs. It doesn't Surprise me that it did - I just didn't know it was going to.


Ending on a positive note,  now that it's working, it's great (as many have said before me). Font smoothing is a lot prettier and more consistent than it used to be. The Gnome panels are a little different, but I think they're better. Firefox/Swiftfox 2 is a lot happier than 1.5 was. Everything's very pretty and smooth. I don't REGRET installing 6.10; I just wish it had been less frustrating.

---

### Post by steven43126 on 2006-10-27
I did an apt-get upgrade and everything seems to have gone fine. The system seems stable the one major problem i have encountered is i can not run mono apps anyone else having this problem ?

---

### Post by Midway on 2006-10-27
This was my first dist-upgrade I have ever done.  I usually start out "clean" when upgrading.

I did the 'gksu "update-manager -c"' which is dirt simple.  What I didn't account for was the weather.  Sometime during the night (I went to sleep during the upgrade) it had downloaded around 600MB or so and then I lost my satellite signal due to heavy rain.  This morning I had a bunch of "could not fetch..." messages and the installer had quit.  Alarmed and wondering if I had screwed my Dapper system, I rebooted (and breathed a sigh of relief when the desktop came back up again) and then ran the update manager thing again.  It reported I only needed to download 160MB more of updates so I didn't lose what I already had downloaded.  Some time later I was booting into Edgy.

Only problem I have noticed so far is that I also do not have usplash anymore as I have noticed other similar posts here.  I get a couple of messages about ata1 and ata2 being disabled, then what looks to be an fsck check and then the Nvidia splash screen.  On shutdown all I see is a quick line saying something about rebooting.  I have tried a couple of fixes such as the "VGA=xxx" but haven't had any luck so far.

Otherwise I am pleased with the increased performance of Edgy :)

---

### Post by beameup on 2006-10-27
Updated from the Alt CD first. Rebooted and update manager said 146 more updates and I need to do a distribution upgrade to complete some of them? So I did, took about an hour and all is OK. :KS

---

### Post by Epperly on 2006-10-27
before the official release I tested and it went fine, so I voted went perfectly. Although I am back to Dapper because of the FF crashes, that is irrelevant

[edit]ACTUALLY, I forgot I did have an error where X didn't work it took me to a black fullscreen terminal, luckily I have a working laptop with internet so I could post, I had to ```
sudo aptitude install xserver-xorg-video-i810
``` in that terminal then it worked perfect, lol.[/edit]

---

### Post by kleeman on 2006-10-27
64 bit upgrade wnt as smoothly as any upgrade I have done before. I had to recompile the nvidia driver but that was all really and that was needed because the graphics card is only supported by beta drivers. All in all surprisingly easy...

---

### Post by bananasareformonkeys on 2006-10-27
only 1 in 6 have a perfect upgrade... not too good.  

The only major problem i've had is that my scanner no longer works on this computer.  So the other one will remain dapper, probably until feisty.


btw, automatix 2 is available for edgy and it can install nvidia and ati drivers. (atleast for i386).

---

### Post by jss on 2006-10-27
Upgraded using gksu "update-manager -c". Everything worked perfectly. The upgrade took about 6 hours.I've had 2 Firefox crashes but no other problems. Edgy is awesome. I'm glad I upgraded.

---

### Post by Epperly on 2006-10-27
6 hours??? holy $#!T!

---

### Post by klato on 2006-10-27
I initially tried upgrade via Synaptic, but my brother rebooted the system when the upgrade was installing, so after that my internet connection was screwed.  So, I downloaded the iso at work and burned that puppy (loved the drag n drop iso burning =)

Anyway, I've got Edgy running right now on my Dell Inspiron 4150. Things are looking good (luckily my /home was on a seperate partition ;), booting definitely is faster for me (~18-20 sec.), and everything in gnome feels snappier too.

Unfortunately, I've no idea what happened to my Intel Pro wireless abg minipci card (didn't even work on a Dapper livecd,hmm..)...so I just popped in my old pcmcia wireless card. and boom I was online.

Direct rendering is also enabled, so I'm gonna have to screw around with Beryl once again (and hopefully break something :)

---

### Post by kingborel on 2006-10-28
Perfect Upgrade!

---

### Post by Shay Stephens on 2006-10-28
I tried upgrading and the system borked up really bad.  So I went to install in another partition with the live CD.  It wouldn't open up gparted so I couldn't get past that.

I downloaded the alternate CD for the text install, and that works, but it won't see my wireless card anymore.  So I am prepping my computer by stripping it down to the simplest configuration and going to try and build it from there.  If that doesn't work, then it will be back to dapper for me.  I am really bummed right now because the release candidate was doing so well on my test partition.  Something must have gone wrong from then to the final release.

---

### Post by davarino on 2006-10-28
I am bummed.

It took overnight to download the upgrade (I am not the type to sit staring at the screen for 6-10 hours, and for some reason the connection ran at only ~32Kbs). Well, I followed the instructions on the Edgy upgrade page here and...

I can't load X. I get the message:

[I]Error: API mismatch: the NVIDIA kernal module has the version 1.0-7667, but this X module has the version 1.0-8774. Please make sure that the kernal module and all NVIDIA driver components have the same version.
[INDENT]Failed to initialized the NVIDIA kernal module.[/INDENT][/I]

Now, I know some howler out there is going to give me grief about "buy a card with OS drivers only and throw away that piece of nvidia crap!" (It happened to me on Ubuntu IRC back when 6.06 came out... neither mature nor "ubuntu"-ish. Actually, it almost made me tear Ubuntu off my machine.) That's not why I'm here. I simply want to know how to make my system run.

If it's not going to be fixable, then I'd like to know how to revert to Dapper.

---

### Post by Brain_Recall on 2006-10-28
I had fun with the Dapper Flights, and enjoyed Dapper when it came out. Edgy tanked everything though.

So, I did the recomened "-c" method to upgrade. I noticed it added a few new kernels, which I figured would mess with my GRUB list. It did, however, not to the extent I expected.

All of the new entries give me this wonderful error:
> Booting 'ubuntu, kernel 2.5.17-10-386'
root(hd0,0)

Filesystem type unkown, partition type 0x7
kernel /boot/vmlinuz-2.6.17-10-386 root=/dev/evmu/sda3 ro quiet splash

Error 17: Cannot mount selected partition

Ehh... Well, all wasn't totally lost. I found my origional entries in the GRUB menu list to work, sort of. My 686 kernels gave me a blinking cursor, my 386 kernel failed to start X and died after telling me so. My 386 recovery kernel actually works. But this install is so badly mangled that I'm not even going to try to repair it. I think I'm just going to figure out how to get my home directory on a USB drive and try a fresh install.

---

### Post by paxmark1 on 2006-10-28
Kubuntu, My dsl hiccupped.  I turned it off so house mates could use Windoze.  So tty and cli and 30 plus packages, many python had to be re done via cycling through dist-upgrade.  qt and pthon kde3's didn't come easy.  dpkg-configure and apt-get clean helped getting the final two borked upgrades down (pythonhtml-gen and hpjis).  

But still no x.  ABI major version (0) does not match servers version (1)

Failed to load module sis and 

No driver available.  

failed IO 140 xserver 0.0

Any real easy way back to dapper?

---

### Post by Johnsie on 2006-10-28
All the stuff downloaded. It took hours and hours to download and install everything. When I rebooted I got an evil blue screen.

---

### Post by reyfer on 2006-10-28
Using Kubuntu here. Upgraded following the apt-get instructions here [http://www.ubuntuforums.org/showthread.php?t=285099](http://www.ubuntuforums.org/showthread.php?t=285099)  and it went just perfect!!! I have experienced no problems so far, my Nvidia card is working great, no network problems and no stability problems so far. I read some threads about people having problems with Firefox and flash, but I have no problems whatsoever (maybe because I installed Flash 9 a week ago). When I upgraded from Breezy to Dapper I found some problems, and I had to do some manual tinkering, but this time everything went perfect.
THANKS!!!!

*(By the way, loving the new Firefox 2)\\:D/ \\:D/ \\:D/ *

---

### Post by cborner on 2006-10-28
Edgy seemed to install fine.

There were, however, a couple of things missing/non-functional in the UI and OS that made me run back for Dapper though.

The Administration menu is missing the Disk manager.  That and Edgy simply WOULD NOT mount my NTFS partition, no matter what I did.  Unfortunately, I need to access my NTFS partition from Linux on occasion.  So this was sort of a deal-breaker for me.

I'll give it a try again in a couple weeks maybe.

---

### Post by Soarer on 2006-10-28
> **5-HT said:**
> 

** EDIT: missed Soarer's post**


Were there no unmet dependencies or conflicts at all, or did you manage to update a few times and sort everything out in the end?

None at all. Smooth as silk for me - I guess I was lucky. It is a 4 year old machine, P4 processor.

---

### Post by AlphaMack on 2006-10-28
Installed Edgy onto my PowerBook using the desktop CD (first time doing so as Breezy and Dapper were with the text-based installers).

X didn't like my decision to not use the kernel framebuffer device and screwed up my resolution along with leaving artifacts all over the screen.  Fortunately I had a backup of my xorg.conf that Ubuntu configured.  The same settings under Dapper work beautifully (for a semi-supported ATI Radeon Mobility 9600).

I reinstalled Dapper using the desktop CD.  Now after the mandatory kernel upgrade it won't boot using 2.6.15-27 but rather 26 from the 6.06-1 release.

Looks like I'll have to do one more re-installation - this time with the trusty alternate CD - just to be sure.

Oh yeah, it really helps to have /home on a separate partition for times like this. ;)

---

### Post by Daniel15 on 2006-10-28
> **Brain_Recall said:**
> 
All of the new entries give me this wonderful error:
> Booting 'ubuntu, kernel 2.5.17-10-386'
root(hd0,0)

Filesystem type unkown, partition type 0x7
kernel /boot/vmlinuz-2.6.17-10-386 root=/dev/evmu/sda3 ro quiet splash

Error 17: Cannot mount selected partition


To fix that, press 'e' to enter Edit mode, and then press 'e' on the first line (the (hd0,0) one) to edit that. Change the last 0 to a 2, so it reads: (hd0,2). Then, press 'b' to boot. This works for me :) It appears to be a bug with the kernel. It's assuming that Ubuntu is installed on the very first partition, and sets the root to that... (hd0,0) means the first partition of the first drive, and (hd0,2) means the third partition.

Anyways, the upgrade went (basically) perfectly for me. The only problem I had was this GRUB problem (which was easy to fix), and a problem with the properiatary ATI drivers (I needed to reinstall them using the ATI installer, due to the kernel upgrade).

---

### Post by Vuen on 2006-10-28
The upgrade went pretty much perfectly for me. I upgraded when the beta came out about a month ago, and I voted "The upgrade went perfectly!", even though I had two small issues (on NVidia/Asus/Intel P4):

1) My vfat partition wouldn't mount on boot with certain fstab uid/gid/umask and fsck settings. Simply typing "sudo mount -a" in a terminal would properly mount the drive. It suddenly started working again recently, so I think it's just a bug that they fixed before the release.

2) My computer no longer turns off after a shutdown. I don't know what the deal is, except that apparently they made some big ACPI changes in Edgy. Well it broke, but I don't care enough to even try to fix it.

So as far as stability, the upgrade was pretty much flawless. This machine must be their main testbed or something, because I didn't run into a single issue throughout the entire last month of beta. I didn't even get to file a single bug report :(

However I need to reinstall from scratch for unrelated reasons (I basically destroyed my installation using NVidia Beta + Xgl + Beryl SVN Trunk). Oh well. I'm still a happy Ubuntu user.

---

### Post by martinbriscoe on 2006-10-28
Well done a useful poll. 50% of 276 people have had serious upgrade problems.

OK I know it will be biased by people who have problems but surely that should be enough for the ubuntu team to call a temprary halt to this upgrade - Its far too risky especially when dapper is so good. It they dont call a halt soon they risk loosing lots dissappointed people to some other very good distros out there.

Martin

---

### Post by Loffe_ on 2006-10-28
I had problems with my upgrade. Beryl does not work anymore. Screen gets white when I login and the virtual terminals (Ctrl + Alt + Fn) aren't usable. There are only a crazy pattern of colors...

After some twisting with graphics drivers I get a desktop but no panels. Going for a blank install now...

---

### Post by tommcd on 2006-10-28
I did a clean install of Edgy off the alternate CD. This is the best way to avoid problems in my experience. I did this when upgrading from Breezy to Dapper also.
 The only problem I have is that I have not been able to get streaming video to work yet in firefox, but I think I'm just missing a plugin or something. I'll figure it out...eventually.

---

### Post by PaulJD on 2006-10-28
AMD 64 upgrade using official method.
Screen goes blank after "Mounting root filesystem: OK".
Ctl + Alt + F1 - last statement is: Booting Kernel
Oddly no 2.6.17* Kernels in GRUB menu?

---

### Post by alanpotpot on 2006-10-28
I did a clean install and had some problems with tty1-tty6. All I see right now is a multi-color screen. When I use MPlayer it says there is no XVideo.

---

### Post by ahh_Jebubs on 2006-10-28
I used the cd first but kept getting disk read errors so decided to use apt-get instead. It took a while and after rebooting, X wouldn't start at all. 
I'm using an old pc with an r200 chipset radeon for running linux (I'd guess that's causing the trouble, Gentoo never seemed to like the r200 chipset either). Tried different drivers and editing xorg.conf with nano changing ati to fglrx and radeon but it didn't help. I don't know enough to try anything else and I'm lost without some sort of gui.

---

### Post by divdude on 2006-10-28
I did a clean install on my Gateway laptop mainly because i didin
know how to upgrade. Anyway the install was good and it detected almost everything except sound. And my Intel 2200 Wifi card which wasnt working with dapper worked magically. So no complaints on that front.
  Now I decided to do upgrade in my desktop with official method using dist-upgrade. The upgrade was bit slow (2hrs) and everything went pretty well. I rebooted and everything worked. Even xgl/compiz worked pretty well. After that I decided to install nvidia-glx drivers because the upgrade had uninstalled them. I installed and rebooted and the xserver was gone.
  Looking at most of the posts the main problem seems to be with graphics cards. Ubuntu team should definitely not overlook this. Because graphics is probably most important thing for mere-mortals pc users.

---

### Post by pommattski on 2006-10-28
No major probs here upgrading with apt-get, despite seeing lots of these warnings during:
```
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_AU:en",
        LC_ALL = (unset),
        LANG = "en_AU.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```
Rebooted ok. 

Had to sort out ATI drivers, Audacity complained when I started it and Skype (latest beta) seems to have slowed down alot.

Everything else seems ok.

---

### Post by marvotron on 2006-10-28
im using xubuntu on a toshiba satellite and my upgrade was a bit of a nightmare. dpkg errors, packages held back.

I wrote a post on the xubuntu forums here for anyone interested :

[http://xubuntu.iphorum.com/topic/dapper-to-edgy-upgrade-problems-using-apt-get-27.html](http://xubuntu.iphorum.com/topic/dapper-to-edgy-upgrade-problems-using-apt-get-27.html)

I've only just moved to an *ubuntu distro, i was a happy debian user for years (which fortunately meant i had a good idea about recovering my system) but this doesnt instill me with confidence.

if i didnt have a second computer (xp) to use for ssh access then i think i would still be facing a black screen with a blinking cursor and no login prompt.

---

### Post by theplatypus on 2006-10-28
I'm beginning to think they should have held off on releasing this for a bit.

---

### Post by ajaym on 2006-10-28
I was utterly amazed how straightforward it was this time. Dapper wouldn't detect my SATA drive (Asus M2V mobo with AMD 3800 X 2) but I had already tried a previous release candidate of Edgy and found that gparted WOULD find the drive, so in preparation I had resized the existing Windows partition and left the 250G drive as 125G for Windows and 125G for Edgy when the final release came out.

The installation went absolutely glitch-free except that - and I expected this - the inbuilt Attansic L1 NIC was not detected. However, I have the luxury of several machines, so went over to the laptop and found without any trouble the Linux Attansic driver. I copied this to a USB key, plugged it into the Edgy machine - it was detected flawlessly - and then copied the driver files over, typed make install, and, wow! it worked. Configured the NIC under the desktop UI and off we went. I am truly deeply impressed. This is seriously quality work, Canonical!. Well done!.

---

### Post by dc. on 2006-10-28
My swap has not been recognized because of the new UUIDS in /etc/fstab instead of normal device names, so hibernating didn't work. But I was able to fix it by replacing the funny hex string with /dev/hda5. Now hibernate works.
Apart from that: When booting, I don't see what its doing, just the progress bar. In Dapper you could see the service and its Status, like 'OK' and so on.

However, the new boot process is faster and gnome is faster too!

So I'm happy. ;)

---

### Post by mistermax on 2006-10-28
The upgrade has been, fo me, an unmitigated disaster. I left it overnight, came back, accepted several of the non-free agreements and then it skipped along happily. Until it hit the flashplayer update. At that point it just hung for hours, I thought it would maybe time out or something, but no. In a fit of desperation, I returned to the terminal and broke the process. AAAAAAAAAAAAAAAAAAAAAAGgggggggggggggggggggghhhhhhhhhhhhhhhh! ](*,) 

Now it is goosed, I can use firefox, but I tried to relaunch the upgrade (not knowing any better) and my password isn't accepted. I'm still online, but I'm terrified to switch off as I suspect I'll loose my system. I have no idea what to do!

I've been searching to see if anyone else has had similar issues. I'm scared that I'm going to have to rebuild- set up my multimedia stuff again, setup all my dev environment again, setup my games and mame again. This is a nightmare.

---

### Post by 8oluf7 on 2006-10-28
Used the 'official' route via Update Manager to move from an up-to-date Dapper to Edgy.
[LIST=1]
[*]Flash non-free plugin took so long to download I thought it was broken
[*]I lost my GUI! "Module ABI major version (0) doesn't match the server's version (1). Failed to load module 'ati' (module requirement mismatch, (0). No drivers available"
[/LIST]
Eventually found a thread where some helpful soul pointed out that Xorg had changed the driver file names very recently. One needs to type in:

[INDENT]sudo aptitude install xserver-xorg-video-ati[/INDENT]

(I have an ATI video card - substitute the driver that failed to load.)

---

### Post by Leopard on 2006-10-28
> **theplatypus said:**
> I'm beginning to think they should have held off on releasing this for a bit.
From what I read when 6.06 was released:
Every third release will be a stable LTS release.
The next release after that will be bleeding edge
The next release unstable
The next is another LTS (ie: lots of testing).

So all those that are upgrading from 6.06 should realise that this version is going to be a bit temperamental.

There's no way I would upgrade to this version immediately after release, especially after using LTS!

My experience - I had an issue with the alternate CD upgrade, and ended up following the terminal upgrade details from a recovery console.
It's all back and working, now to figure out what happened to video card drivers since I last looked.
And what happened to XGL?

---

### Post by kperkins on 2006-10-28
Doing a smart upgrade using Synaptic completely hosed my xserver, everything I did made it worse (actually rebooting the computer when it told me to was a bad mistake.) I had to download an iso on a different computer), and install that way (which means I lost a lot of my programs I had installed.  Reinstalling now.  
I didn't lose any data, because I made backups, and I didn't have to touch my home partition.  Always put /home on a separate partition folks. 
But I think it was worth it--for me, anyways--since, now, NetworkManager works perfectly. :D 
Now to reinstall my fonts.

---

### Post by FatherDale on 2006-10-28
> **martinbriscoe said:**
> Well done a useful poll. 50% of 276 people have had serious upgrade problems.

OK I know it will be biased by people who have problems but surely that should be enough for the ubuntu team to call a temprary halt to this upgrade - Its far too risky especially when dapper is so good. It they dont call a halt soon they risk loosing lots dissappointed people to some other very good distros out there.

Martin

Agreed. Right now I'm working to save both machines, but I have FC6 downloading on this Windoze box....

Edit: OK, I just gave up on the laptop's upgrade. I did it both ways -- Fresh install on the big box, upgrade on the laptop. I used the official method to upgrade the laptop, but it quit -- powered down -- during the upgrade, and all the dpkgs and apt-gets haven't recovered it. So I copied my criticals to the windoze partition and sanded it down. Now I'm going to try the alt CD install.  
On the desktop, I did that first -- backed up, then did the alt-CD install. When I rebooted, I had no x server, and the error message was complaining about the lack of libasound2. No amount of cajoling could get it to reinstall libasound2, which dpkg insisted was just fine, thank you.
I just shoved the alt install cd into this laptop, and am about to reboot (one more look at the howto ;) ). Think I'll give FC6 a shot on the big box, cuz, what the hell. Wish me luck....

---

### Post by mistermax on 2006-10-28
> **Leopard said:**
> From what I read when 6.06 was released:

So all those that are upgrading from 6.06 should realise that this version is going to be a bit temperamental.


temperamental?

sheesh

---

### Post by exir on 2006-10-28
i did yesterday the upgrade (the official way). Yesterday everything seems working fine..but now..one minute browsing over the internet or starting an movie and ubuntu crashes at all!

it doesnt respond on anything more :(

im now doing an complete re-install....

---

### Post by phormion on 2006-10-28
I've used the update-manager way of upgrading:

> 
gksu "update-manager -c"


I did that yesterday evening. So far I've only noticed a breakage in amarok (more on this [here](http://ubuntuforums.org/showthread.php?p=1676281#post1676281)), and that's not supposed to be part of Ubuntu (it's in Kubuntu, being a KDE app). 

One thing I didn't like was the kernel list on boot having entries for all installed kernels - I had to uninstall all the old kernels to make them go away. But I guess the update-grub script is to blame for that. 

EDIT: so, for now, the vote goes to "had a few small problems". 

I'll have a look at movie playing later.

---

### Post by morequarky on 2006-10-28
If Dapper worked perfectly fine on your computer, then I would think that Edgy would too.

Did you have to install special drivers for Dapper?  You probably have to do that for Edgy, too.

Did you follow the wiki directions for upgrading to Edgy?

Did you have any trouble setting up RAID or multiple hard drives in Dapper?  You might have some issues with this with Edgy, but in the end it should work.

I am amazed at the number of people with trouble upgrading.  

Maybe you did all the above things and are still having issues, but it is hard for me to imagine.

---

### Post by eldaria on 2006-10-28
Upgraded my Dell Desktop, no problems at all so far, except thyat I'm now running a 386 kernel instead of 686, so no Hyperthread, and apt-get dsit-upgrade tells me some packages are being kept back:
```

The following packages have been kept back:
  hpijs python-adns python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-gadfly python-htmlgen
  python-htmltmpl python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-pam python-pexpect python-pgsql python-pylibacl
  python-pyopenssl python-pyorbit python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-syck python-xml python-xmpp
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.

```

Nothing that bothers me though...

-----------------------

My Sony Vaio Laptop did not upgrade well, Dapper worked perfectly on this one withouth a glitch.
A dist upgrade left me with no X, No network, and no errors.
A boot up of Live CD, crashed as soon as X loaded, before I got a chance to do anything.
Removed the Wireless NetGear card, and it will boot up into Live system, but with no network, (Including the wired one), tried to install. Crash during Format of Harddrive.

Downloaded the Alternative CD, and can run the install, it detects my wireless card, but after install is done, it no longer sees the wireless or internal network.
I have given up on laptop, and is now installing Dapper again.


-----------------

My Server, well went through an dist-upgrade, after a lot of Hassle, and some help from the forums I got a working system, with old version of SQL server:
[http://www.ubuntuforums.org/showthread.php?t=284950&page=4](http://www.ubuntuforums.org/showthread.php?t=284950&page=4)

We found that it is probably related to a bug:
[https://launchpad.net/distros/ubuntu/+source/mysql-dfsg-5.0/+bug/66702](https://launchpad.net/distros/ubuntu/+source/mysql-dfsg-5.0/+bug/66702)


So all in all,1 system working, 1 system, half working after some hassle, and 1 system not at all.
I think Edgy need som more work before beeing ready for the broader market. Unfortunatly the new bugs might put of some of the new commers who got tired of the Microsoft.

---

### Post by muxecoid on 2006-10-28
GLX not working properly. Also I needed to mark some dependencies for removal/upgrade "manually".

---

### Post by DJ Wings on 2006-10-28
No. DPKG conked out at the end (and still won't work), so now I can't install working copies of X.

---

### Post by ahh_Jebubs on 2006-10-28
> **morequarky said:**
> If Dapper worked perfectly fine on your computer, then I would think that Edgy would too.

Did you have to install special drivers for Dapper?  You probably have to do that for Edgy, too.

Did you follow the wiki directions for upgrading to Edgy?

Did you have any trouble setting up RAID or multiple hard drives in Dapper?  You might have some issues with this with Edgy, but in the end it should work.

I am amazed at the number of people with trouble upgrading.  

Maybe you did all the above things and are still having issues, but it is hard for me to imagine.
Did you read the previous 80 comments?

---

### Post by oneferna on 2006-10-28
I have had mostly success on 2 machines. On a dell Optiplex desktop I upgraded the "right" way, with gksudo..etc etc... However, I did have to run sudo apt-get dist-upgrade about 3 times and apt-get -f install because the first few tries upgraded about half and then quit. But I'm patient and just kept running dist-upgrade until it was done.

On my laptop, a Dell Inspiron (also with an nvidia card), I did it the "hacky" way, I changed my sources.list and then did a dist-upgrade. That only took 2 tries, but I have A lot less software on there. 

So far everything is working, except Firefox crashes over and over, but I've never had luck with browsers on my laptop, they always crash. So for now I'm using Opera and it seems a bit more stable. 

Thanks,
Ferna

---

### Post by Klaidas on 2006-10-28
Clean-installed -- perfectly worked for me :)

---

### Post by clebin on 2006-10-28
Unfortunately not a good story here. I used 'gksu "update-manager -c' (I su'ed to root for good measure, but I don't know if that was clever) After a few errors, the installation quit. Apt-get wouldn't work and the system wouldn't reboot. After a reinstall from the Dapper LiveCD, I'm now downloading the Edgy CD to try from there.

---

### Post by Snocrash on 2006-10-28
Well, it did not go smoothly for me.

I used the alternate-cdrom method. That should have been the same as the official method, just get packages from cd instead of repos.

First thing that went wrong was the nvidia-glx install failed, but I figured I could fix that later from console so I continued. about 5 minutes later the installer failed completely and said my system was probably unstable and may not boot! ](*,) 

Since it had already removed a bunch of stuff and was only about 20% into the install, I figured it probably would not reboot.

Just for kicks I tried to restart the installer and got a bzillion dependency problems and it shut down again.

So I killed X, logged into the console, fired up vi and verified all the official ubuntu stuff was changed to edgy and all the third party stuff was shut off in my source list.

After that it took a couple of hours and three runnings of "apt-get -f install", "apt-get update" and "apt-get dist-upgrade" for it to finish.

](*,) 

On the up side, edgy looks good, and most things "seem" to be working at the moment. My fluxbox is a little screwed, but I will get what I need from fluxbox.org to fix that. Other then that, it looks good. But I gotta give a C- on the upgrade. Most of the people I know would not have been to recover from the problems during upgrade.

Just my $.02.

Sno

---

### Post by angkor on 2006-10-28
Just finished the upgrade and I must say I'm pleasantly surprised at how smooth the upgrade was. No errors during the upgrade at all. I had a lot more problems with my upgrade to dapper but that was on a highly tweaked year-old install. This time my dapper was still fresh (new comp) and the upgrade went without a hitch using aptitude.

I had some post-install problems with sound but that was easily fixed. Edgy is happily humming along :).

---

### Post by skirkpatrick on 2006-10-28
Since I have less to lose on my Acer laptop if I have to do a re-install, I have only upgraded it so far.  I used Update Manager and only had a few problems.  I had to manually uninstall ndiswrapper, connect to my wired network, and install the latest ndiswrapper from repos.  Of course this is pretty much a stock Dapper install with no ATI or NVidia card and I'm still a little hesitant to update my desktop.  Certainly not without backing up a large amount of stuff.

---

### Post by PhilB on 2006-10-28
Had a few problems, none too serious.
I tried initially to upgrade using $ gksu "update-manager -c" as recommended, but it only got as far as downloading 49 of 51 packages then it stopped completely.
I downloaded and burnt a cd and tried to upgrade using the cd as my repository, but all I got was messages saying I was fully up to date. Presumably because of the prior attempt.
Finally I did a fresh install, which went smoothly and after running Automatix2 everything appears to be fine. 

Phil

---

### Post by neutro on 2006-10-28
At this time, it seems that 49.73% of the readers of this thread had serious problems or things got really bad for them. Maybe this is because people for which everything did go find didn't bother answering the poll (very probable), but then again, if you have only one computer and things got really bad, you probably can't answer, too.

My point is that the numbers are rather high in my opinion. I didn't have any problem upgrading from Breezy to Dapper, but I cannot boot in Edgy now after an update attempt (the boot process hangs; I'm downloading the ISO now, so I'll be with you guys in a few hours :) ). 

I don't know what has gone wrong: I started the update before going to bed and this morning the screen was showing an Xorg error. Reboot couldn't be completed. I should have tried an apt-get update && apt-get dist-upgrade at this moment just to make sure all packages were correctly installed :(

I just hope Ubuntu is not *loosing* users due to failed upgrades...

---

### Post by Jessehk on 2006-10-28
[list]
[*] There were about 20 packages that were held back that I had to upgrade manually.
[*] My ubuntu usplash was replaced with Kubuntu. In this case, it's a simple:

```

sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)

```

But should a new user really have to deal with that?
[*] The upgrade failed to remove my old kernel. I removed it in Synaptic, but a new user would be lost.
[/list]

---

### Post by mistermax on 2006-10-28
yes, that was a bit aloof was it not? You had a good time upgrading, others **clearly** did not.

---

### Post by kroenecker on 2006-10-28
My upgrade didn't go well.  After it completed and the system rebooted, it hung during the kernel load at hid-core.  Something to do with usb detection or another piece of hardware thereafter.  Anyway, I had to do a fresh install

---

### Post by davarino on 2006-10-28
This really is not a good situation. Of course there is some bias in this poll... probably a lot.;)  But that we have (at this moment) only 19% of respondents saying they had a slick experience is a real cause for alarm.

Window$ users have much better luck than 19%, and the non-techies among them (the "Human Beings" as in LFHB) certainly have no reason to change over to Edgy if this is the best we can do.

---

### Post by reyfer on 2006-10-28
And has it occurred to you that maybe, just maybe, a big percentage belongs to people for which the upgrade went smoothly, and just don't like to answer polls?

I say this because I contacted 35 people I know that run Ubuntu and Kubuntu, and for ALL of them the upgrade went without a gitch, but they are not really involved in this forum, so I think that should be taken into account here

---

### Post by exir on 2006-10-28
Just completed with the fresh install and setting up everything. so far so good. No problems :)

---

### Post by Zendarin on 2006-10-28
Nope.  I downloaded the alternate install cd and burned it for an upgrade from "Dapper".  During install, I got alot of "Locale not set" errors, but everything seemed fine.  Booted up fine, got in and have graphics. But, when I try to get into Synaptic or apt I get an error saying that Samba is a broken package, run "apt get install-f".  When I do that, this comes up-

"E: /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb: subprocess new pre-removal script returned error exit status 102"

Can't seem to get around it.  Any ideas? ](*,)

Check this out too. 

gksu "update-manager -c"
warning: could not initiate dbus

Not good.

---

### Post by skirkpatrick on 2006-10-28
> **Jessehk said:**
> [list]
[*] There were about 20 packages that were held back that I had to upgrade manually.
[*] My ubuntu usplash was replaced with Kubuntu. In this case, it's a simple:

```

sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)

```

But should a new user really have to deal with that?
[*] The upgrade failed to remove my old kernel. I removed it in Synaptic, but a new user would be lost.
[/list]

Jessehk, I always have to manually remove an older kernel using Synaptic.  I think it's because if something went wrong with installing the new kernel, you can always use the old one to fix the problem.

---

### Post by FatherDale on 2006-10-28
Well, I got no joy on the big box, and the fourth attempt (two upgrade, two clean install) on my laptop turned it into a lump of silicon and plastic. Won't even boot windoze now. I'll play with it later. In the meantime, FC6 seems to be running nicely on the big box. Sogh. Now I gotta find new toy stores... :-D

---

### Post by aaronw on 2006-10-28
The source of my troubles was that I began the upgrade while I was at school, and stopped it in the middle (including restarting because of a failed attempt to hibernate) when I went home.  I knew this was probably a bad idea, but I hadn't read anything to suggest the upgrade process was unable to pickup where it left off.  It is.  So I had to finish it using apt-get dist-upgrade, and then I had the video driver problems everyone else seems to have.  I eventually had to reinstall xserver-org, which got me up and running again.  Edgy is certainly faster, at least for now.

---

### Post by psycosmyth on 2006-10-28
Well I did not upgrade my primary box, my dell laptop, but the live cd ran well and everything was good, slow, but good. I installed it on my desktop's Linux drive and I think I fried it, it's had 12+ reformats and it's quite old,no tears. I did a first, I partitioned my xp's drive and put edgy there. I did not like the confusing dialog about the partition size I thought I was making the new partition but I wound up making the xp one smaller, no harm just got mixed up, the direction need to be more clear. 
I gotta find the post for good wifi cards cause mine is up and running great:p

---

### Post by Zendarin on 2006-10-28
Hey, fixed the problem with Samba, there was a locked Symlink that was erroneous.

Dbus still has issues, but it's getting there now.

---

### Post by Brendt2 on 2006-10-28
I had a few install problems... but honestly couldn't have been too bad... i mean x broke... but... I wizzed through the fix... and went on from there...

again... problems... probably would have stopped someone with no experience... 

I did experience an error with the update process initially ( RC ) but again... it couldn't have been too bad since I fixed it and still have all my nerves about me!

---

### Post by morequarky on 2006-10-28
> **ahh_Jebubs said:**
> Did you read the previous 80 comments?

Yes I did, everyone in fact, and people who upgraded successfully don't tend to go looking for polls online to cast their vote saying their upgrade when perfectly.

Also, I noticed that some people who upgraded had only minor issues and really should have voted for the first selection, but was too hard on Ubuntu.

I think the issues here are an aberration of reality.

---

### Post by andriansah on 2006-10-28
I have problems with x windows
I can't log to my Xwindows

---

### Post by aaronw on 2006-10-28
> **andriansah said:**
> I have problems with x windows
I can't log to my Xwindows

What error do you get?  Does it tell you that the x server is configured improperly?

Also, what kind of video card are you using?

---

### Post by andriansah on 2006-10-28
> **aaronw said:**
> What error do you get?  Does it tell you that the x server is configured improperly?

Also, what kind of video card are you using?

IT's dell gx260, I forgot the error, because it finished on the time i have to leave office

I haven't cek the log, but it give big blank screen and only ok button appear, after i enter it goes to login prompt

I check again on monday

---

### Post by rouben on 2006-10-28
I guess I'm one of the lucky ones that didn't have any issues with my Edgy install. Mind you, I've been using Edgy since beta2 (upgraded from Dapper) for months and I have a system with an ATI X300 (fglrx driver).

---

### Post by strawman on 2006-10-28
upgraded using the apt-get dist-upgrade.  only problem so far, and it's fairly serious, is my laptop does not wake after going into suspend.  i'm hoping a fresh install will fix this.

---

### Post by aaronw on 2006-10-28
> **andriansah said:**
> IT's dell gx260, I forgot the error, because it finished on the time i have to leave office

I haven't cek the log, but it give big blank screen and only ok button appear, after i enter it goes to login prompt

I check again on monday

It sounds like you are having the same problem I did, which is that your xserver configuration is broken.  Some people fixed this by reinstalling their video driver ("apt-get install xserver-xorg-driver-radeon" for me, but it sounds like you have some kind of on-board intel gfx card).  I had to "apt-get install xserver-xorg" and press "Enter" through all of the default settings, and then it worked.  Good luck!

---

### Post by majabl on 2006-10-28
I did a clean install of Edgy Eft, wiping off my previous Dapper Drake installation.  At first there were problems with the installation not recognising a root partition, even though there was one.  To get around this I tried someone else's trick of reformatting the root partition and this did the trick.  My system is now up and running and - fingers crossed - problem free.

Now all I need to do is find somewhere I can download the Dapper Drake wallpapers - their colour shades are nicer than the ones that come as standard with Edgy Eft!

---

### Post by ogryn on 2006-10-28
My Wireless card broke (was bcm43xx drivers). Fixed this by going to NDisWrapper

Still working on getting 3D accelerated ATI card back up and running though...

---

### Post by jordoex on 2006-10-28
Regarding the results of the poll, the answers are kinda skewed since most people who come to the forums want to fix something that screwed up, so most of the results of this poll are from people who need something fixed.  My problem is that the stupid Smart Boot Manager isn't working(pun intended).  Look for the thread, i'll be bumping it daily until I get a response.

---

### Post by khedron on 2006-10-28
My upgrade experience has been reasonable. Since a dodgy upgrade from Breezy a few years ago, I decided to take everything one step at a time.

So I manually changed my sources.list and ran aptitude dist-upgrade. :) I figured that anything a GUI could do, I could do better.

That decision definitely helped. I could see unmet dependancies etc and remove them manually, letting aptitude continue installing until it found the next problem. The python2.4 packages seemed to feature prominently in the problems. I also had to temporarily uninstall kubuntu-desktop and openoffice.org-kde in order to get some other packages working. Aptitude FTW.

Now my desktop is in a working state. Firefox 2.0 looks a bit weird with the default theme (the tabs are too small) but a switch to the Qute theme fixed that. Also, the KDE taskbar insisted on putting one icon per column in the system tray. Customising the taskbar's width (50px did it for me) changed that.

My one major problem is that fglrxinfo reports the Mesa driver. This is annoying, especially as I have installed the latest fglrx from a separate repository. Removing xorg-driver-fglrx and then rebooting to remove it from memory made X crash (the generic ati module can't be loaded because of a version mismatch or something) so I had to reinstall it from recovery mode. After two hours of fiddling I have not found a way to coax X into using the proprietary driver. :(

But everything else is working, and I'm sure that my driver annoyance will be sorted out soon. Thanks to the Ubuntu developers.

@ jordoex:
> the answers are kinda skewed since most people who come to the forums want to fix something that screwed up

Hmm, I would have thought that it was the other way round. Those who can't log in, boot or access the internet can't possibly vote here :D

---

### Post by Vuen on 2006-10-28
> **morequarky said:**
> Yes I did, everyone in fact, and people who upgraded successfully don't tend to go looking for polls online to cast their vote saying their upgrade when perfectly.

Most of the people in this thread probably did not find it looking for help on their broken upgrade. I was linked to it in #ubuntu on freenode, and this particular thread has been linked to on various blogs. Many people probably found this thread before they even upgraded, simply reading #ubuntu, blogs, and the internet in general for advice. Yes, there is probably some bias, but it's not nearly as radical as you claim. The fact is, a significant portion of Ubuntu users have had disastrous consequences from the Edgy upgrade.

> Also, I noticed that some people who upgraded had only minor issues and really should have voted for the first selection, but was too hard on Ubuntu.

Absolutely not. People with minor issues should have chosen the second option. If you have to fix things after upgrading, regardless of how minor, the upgrade did not go well. My computer no longer turns off after a shutdown, and I felt I was being generous by choosing the first option.

You seem to be forgetting that Ubuntu is meant to be a user-friendly distribution for your average PC user. Ubuntu is supposed to cater to the Windows crowd; these people do not know how to fix even the most minor of issues, and *they should not be required to fix them.* You will never solve [Bug #1](https://launchpad.net/distros/ubuntu/+bug/1) with your mentality.

---

### Post by Johnsie on 2006-10-28
I dont think this poll represents the whole Ubuntu community. This poll only targets  people who are on a problem forum that is mostly visited by people with problems. So obviously the percentage of people with problems is going to be higher. It's a good example of bad poll targetting.

Really a poll like this should be posted somewhere that is neutral like Ubuntu cafe, not somewhere people go to deal with their problems.

---

### Post by flowerbirdie on 2006-10-28
My husband helped me get the upgrade for my lappie, a Toshiba Libretto L5 (a tiny Japanese import), although we a slight problem with the upgrade we don't think our fix is unique to this machine.  

We did an upgrade from Dapper.  The download and upgrade took almost 24 hours from start to finish.  Under dapper we were using xorg ati driver.  We had the video corruption and hard lock problem, so we changed the color depth to 16 bit, which seemed to fix that problem. As a side effect, Ubuntu stopped updating the xorg.conf file because we tweaked it.  Again, all that was under Dapper.  When we did the upgrade to Edgy we had forgotten our tweak.  During the upgrade Edgy told us the ati driver was obsolete and deleted it.  Our fix was relatively simple, from text mode we re-installed the driver and re-booted.  Hope this helps.

Edit:  Having serious issues with FF.  Not happy about that at all.  Luckily I have Kubuntu on the same machine so I am simply booting into that desktop and using Konqueror until FF gets their issues fixed.

---

### Post by sg_57 on 2006-10-28
Overall was quite fine, but I am having issues with Firefox 2.0 randomly shutting down, and shutting down every single time I try and open GMail... 

So, on the plus side: No xserve problems, no blank screens, no major crashes, everything looks like it's running more or less, Thunderbird, OpenOffice, and more apps. (still checking).

It appears that there are a couple of different fixes for the Firefox crash issue, being that I have an NVidia card, I managed to make it work with the following tip:

> **me1on said:**
> 
Just type in a terminal (change gedit to kate if you're using kubuntu):
```
sudo gedit /etc/X11/xorg.conf
```

Then find the line that says (toward the bottom of the file):
Code:

```
DefaultDepth 24
```

Change the number 24 to 16, save, close gedit, and restart ubuntu for the changes to take effect.


SG

---

### Post by bgalan on 2006-10-29
I voted upgrade with a few problems, but they were minor problems. i'm no computer expert, but very enthusiastic about linux and ubuntu in particular (i love the philosophy of it all). but i'm not afraid to experiment, and ruin, my system. everything is properly backed-up (at least once a week) and i can always re-install things if i need to (i find that to be half the fun of using linux). 
i found solutions to even the minor problems, so they were quite momentary. i'm currently writing with a fully updated edgy eft system. i use a hp pavilion ze4145 with a belkin wireless pci card. to the moment, everything seems to function quite well.
thanks to all for your help in developing, releasing and helping along the way. peace to all. :) 
benjamin

---

### Post by morequarky on 2006-10-29
Maybe I am stubborn,....ok, I admit it, I am stubborn.  I had issues upgrading using the Edgy Alternative CD.  What was my problem?  PBKAC.  And I originally outlined that special setups of Dapper are going to need special upgrading.  My install refrused to load Xwindows like a WHOLE LOT OF THE FOLKS HERE, but my problem wasn't a config file. PBKAC.  I could be way off my rocker here, but I, honestly, wonder how many PBKAC issues this thread is refering to.

Maybe I am sticking my foot in my mouth, PBKAC.  I believe so strongly in Ubuntu that I, subbornly, beleive hardware and PBKAC issues before I jump on Mark's case.

I hope everyone here gets their problems solved by whatever means and has a blast using the best OS available.

---

### Post by jamvegan on 2006-10-29
I just upgraded using the officially preferred method with update-manager.  Files downloaded in about 20 minutes.  Installation and configuration said that it was going to take about an hour, and after 45 minutes that estimate seemed accurate.  Then I started getting "Could not install...The upgrade aborts now" windows.  First for 'debtags', then for 'adept-common' and various other adept packages.  Every window said "The upgrade aborts now", but it never did.  After a bit more than an hour past the one hour estimate I got a message that the upgrade had failed, and my system might be in an unusable state.

But it seems fine.  I rebooted, and got to hear the login music for the first time ever on this machine with Ubuntu (I've had sound problems with every previous version).  I've tried various applications, and they all work as they did before, or better.  The only exception is Firefox.  If I try to visit certain pages with Flash ([http://www.imdb.com/](http://www.imdb.com/) for instance) Firefox immediately crashes.  I'm not a big fan of Flash, anyway.  I may just uninstall it and see if that takes care of the crashes.

Overall experience: this upgrade gave me more scary messages than any previous Ubuntu upgrade, but appears to have actually gone more smoothly than any previous Ubuntu upgrade on this machine.  Weird.

---

### Post by Gipetto on 2006-10-29
I upgraded using the update manager.
Got a few dependency warning but they were mostly python so I agreed and it also seemed like it was after the installation had actually occured so I didn't think it was much harm.

Well, there must have been something in there because the XServer wouldn't recognize my screen. I could get a command line via rescue mode and tried to reconfigure the xorg.conf but still got a failure. 

I reverted to the backed up xorg.conf from before the upgrade and now get a GUI. I really have no idea what's going on that makes the old conf work and not the new one.

---

### Post by Sirkent on 2006-10-29
I had fairly serious issues using the Official update method:
gksu "update-manager -c"

I had everything backed up first, as I expected I might have to roll back, but I'm surprised at the problems I experienced.

Firstly, before the upgrade could complete in Dapper there was a problem removing /usr/X11R6/bin, as Opera had stuck a link in there. That caused serious problems with Synaptic and the upgrade process seems fairly confused after that. I restored the backup, removed Opera and then tried again. That was fine, so I rebooted.

Here's where I became surprised, because now I couldn't log in! I didn't expect that the changes to Gnome would be so severe that I wouldn't actually get a functional desktop! Firstly, there was a problem with keytouch, so I uninstalled it and removed the .keytouch directory from my profile. That enabled me to login with errors but now, once logged in, Metacity (the window manager) and the taskbars hadn't loaded. I created a new account (using the failsafe Gnome login) and compared the configurations and ended up deleting quite a few files from my configuration. I'm not sure which one(s) fixed me account.

So once I'm logged in, fglrx isn't working..! It turns out that because the new version supports aiglx, fglrx needs an extra section in the Xorg.conf file?
```
Section "Extensions"
	Option "Composite" "disable"
EndSection
```

Quite simply I expected those areas where I had difficulty to be pretty much automated. I haven't made any custom configuration changes to my Gnome account or any other part of Ubuntu, in fact most of my changes have been made through the GUI.

Still, at least I knew enough about Linux to fix the problem... I hope people with less technical knowledge have more luck or decide against upgrading for now!

---

### Post by Kazuhiro on 2006-10-29
I had some issues with the generic kernel, had to rebuild my initrd for the generic kernel to get it to boot with a intel core2 duo cpu and support smp.

The i586 kernel was fine.

Also X11 was a pain. xorg-server package did not get installed...

Overall I dont think this release was ready, maybe another week and a call for beta testers to upgrade and report their bugs. But overall im happy with edgy. Some of the beta software is less than rock solid stable but then it is the edgy release.

I did a dist-upgrade about 12 hours before the full release.

---

### Post by kooldeep on 2006-10-29
The new kernel in Edgy completely broke booting off my dmraid partion because of a new sanity check: [https://launchpad.net/distros/ubuntu/+source/dmraid/+bug/54246](https://launchpad.net/distros/ubuntu/+source/dmraid/+bug/54246)

It would have been helpful to put this in the known issues of the release notes. Even with the updated package on launchpad, it takes 4 minutes to boot because of some random read error that did not occur on dapper. I just gave up and moved my root partion on to a non-raided drive.

However, everything else upgraded nicely, only a few kernel modules to recompile (as expected). I think Edgy definitely needed a lot more testing before it was released. Bugs like the dmraid one should have been fixed before release.

---

### Post by kjaleel on 2006-10-29
i used the gksudo 'update-manager' method and the update went just fine, except my swap drive was disabled for some reason. I was going to do a clean install anyway because I wanted to wipe Windows off my drive and when I did that things were much better.

GNOME's desktop seems to be having some problems though, especially nautilus and gnome-panel. Yesterday I was just browsing around and occasionally opening up a disk folder or two, and nautilus locked up and started eating 99% CPU. So I had to do a 'killall nautilus' and it was back to normal.

Then, later on, I minimized a window, but it got stuck on the panel, and the whole top menu "Applications, ..." and the bottom panel got stuck. I had to do a 'killall gnome-panel' to bring those back. 

After the gnome-panel restarted, the 'gnome-power-manager' was no longer in the system tray for some reason. It became a regular window and I could not close it at all until I logged out and back in. 

So I think GNOME overall is a little bit unstable right now, it is Edgy after all.

Nautilus also seems to be having a few problems with mounting Samba shares, unmounting them when I hibernate the computer and remounting them when I wake up the computer

---

### Post by David Eikelenboom on 2006-10-29
The upgrade to Edgy went almost perfectly. X broke, but that problem was quickly solved.
Two minor details:
1) syslogd was running as root, and remote syslogging (my router supports that) also didn't work. Editing /etc/init.d/sysklogd did not solve the problem. Editing /etc/default/sysklogd did. I don't think that this is supposed to be done that way.
2) I don't see the OpenBSD Secure Shell Server in the System -> Administration -> Services dialog box. It is running though. This will probably be fixed in an update.

---

### Post by antoniocosta on 2006-10-29
Hi.
I have been using Ubuntu since Breezy (and Linux since 1993) in two laptops, an old Compaq Presario 1200 and an Asus A3. Upgrading from Breezy to Drapper was 100% successful, but from Drapper to Edgy was not straightforward:
[LIST]
[*]On both laptops, Xorg had to be reconfigured (a simple dpkg-reconfigure xserver-xorg solved it);
[*]On the Asus, ndiswrapper had to reinstalled from Synaptic (the ndiswrapper tools conflicted with the ndiswrapper kernel modules);
[*]Opera had to been removed because of the opera link in /usr/X11R6/bin, which stopped Xorg upgrade.
[/LIST]
I used two methods:
[LIST]
[*]On the old Compaq Presario, a network upgrade with apt-get update and two apt-get dist-upgrade's;
[*]On the Asus, I downloaded the alternate ISO image, mounted it as a loop device on /media/cdrom and proceeded like a cdromupgrade.
[/LIST]
I was slightly disappointed by the upgrade process, I was expecting a 100% smooth transition...

---

### Post by fisherdmin01 on 2006-10-29
Good point.  I voted that the upgrade went perfectly for me.  The ONLY reason I am here is because I read an article on Slashdot that indicated that there were major problems.  Maybe the lucky ones who had good installs will now find their way here and "fix" the curve??

I admit that I am VERY lucky as I did EVERYTHING wrong when I upgraded.  I am running a PowerBook G3 with 256 MB RAM and am trying to find every performance boost I can get.  I read in a post that Edgy's performance was superior to Dapper, so I upgraded just prior to the official release date to Edgy via apt-get.  I didn't read a single how to upgrade -- just rolled the dice (I'm actually looking for a good reason to install OS X back on the little beast and have a very vanilla installation - so far Ubuntu has been VERY solid for me).  Upgrade went well, installed Xubuntu desktop to streamline things further.

I WILL report that the system is not a big fan of my AirLink wireless adapter.  I occasionally get problems at boot pointing to what I presume is the wireless adapter, then the system does a fsck followed by a could not kill process xyz (forget exact number) and I have to pull the battery out (NOT FUN!).

All in all, a good experience, though my Linux-on-Mac overall experience is seriously dampened by lack of Flash/Shockwave, Quicktime, and other integral surfing enhancements support.  Still it's a 7 year old laptop with 256 MB of RAM.  I should consider this a freaking miracle.

> **reyfer said:**
> And has it occurred to you that maybe, just maybe, a big percentage belongs to people for which the upgrade went smoothly, and just don't like to answer polls?

I say this because I contacted 35 people I know that run Ubuntu and Kubuntu, and for ALL of them the upgrade went without a gitch, but they are not really involved in this forum, so I think that should be taken into account here

---

### Post by Sef on 2006-10-29
Only problem so far that I have had is that upon the initial reboot it got stuck.  Rebooted and all has been ok since. I update via update in Dapper.

---

### Post by infidel on 2006-10-29
Because my setup is a mishmash of large chunks of every *buntu but Edu, I suspected that my best upgrade path would be a fresh install.

Naturally, I ignored the better angels of my nature. :)

Forging ahead with apt-get, I had a few stutters over dependencies; otherwise, everything appears to have worked extremely well. Shockingly well, given the nightmares others are reporting. I'm still very much in "shakedown" mode, but so far everything appears to have gone smoothly.

Very sorry to hear about others' troubles...

---

### Post by Sencer on 2006-10-29
I voted perfect, because everything worked - even though I had my own kernel running (linux-phc for undervolting). As if by fate, I had just uninstalled opera a week ago - seems to have been my lucky week. ;)

I had one odd message regarding the "atop" package - due to a problem, update-messenger told me it would revert from the update. And once it was finished, it told me it had reverted - as a matter of fact though the update had went through just fine. Wireless & WPA was still working (ipw2200 & network-manager), graphics was working (Intel i915 & 915resolution), skype finally started working (had had audio-problems on dapper; ICH6).

---

### Post by igorzolnikov on 2006-10-29
gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
warnings.warn("apt API not stable yet", FutureWarning)

Software Updates have status: "Your system is up-to-date".

What next? I want upgrade to 6.10.

---

### Post by johann_p on 2006-10-29
Upgrade crashed and presented the message: The upgrade aborts now. Your system could be in an unusable state. A recovery was run (dpkg --configure -a)

Not a very user-friendly message. "could be in an unusable state" sounds scary and is not very helpful. 

I had no idea what I should do now, I had no idea if the system would be able to boot or not.

---

### Post by johnpenner on 2006-10-29
cant even get the iso install CD to fully boot (!)
it gets to the point where it starts to load the linux kernal, and then...

[55.018231] unable to locate RSDP (invalid compressed format (err=2)
[55.028758] Kernal panic - not syncing: VFS: Unable to mount roof fs on unknown-block(1,)

and it insists on making the 1024x768 LCD screen a 800x600 screen by default
unless i manually hack the xorg.conf file (ugh) -- a normal user would NEVER
know how to do that. oh, and thinkpad 770 sound never worked... :-\

guess its back to dapper for me.... :-^

---

### Post by professordes on 2006-10-29
I started upgrading a bunch of machines runner Dapper when Knot3 was released. The installer crashed in most cases at various points all the way through to the release candidate, for varying reasons. Tidying up by hand with some combination
of dpkg --configure -a and apt-get -f install or aptitude  gave a bootable system in all cases. I had to resort to a forced
install of a package or two with dpkg for a couple of the machines.

In all cases as far as I could see something slightly "non-standard" was causing the problems, i.e. Ubuntu + Kubuntu, Opera, Xgl, additional repositories.

The only machine I have installed onto with the real thing - an IBM ThinkPad X31 - was a clean install, so I don't know if some problems still persist, looks like they might from the reports here :)

Rough head count so far:

2 Shuttle SN41 desktops, Ubuntu+Kubuntu  Athlon XP. 1Gb RAM. PATA hard drivesx2: This gave an installer crash when it tried to install KDE stuff. I had to remove kubuntu-desktop and run several apt-get -f install, dpkg --reconfigure -a's. It didn't like Opera either. There was a lot of python drek as well left over on upgrade which aptitude cleaned up.

2 generic beige boxes: also Athlon XP and Ubuntu+Kubuntu. KDE install crash, again had to remove kubuntu-desktop and Opera
and clean up python afterwards by hand. The Xgl stuff (compiz) was broken on upgrade, I added the Beryl project repo. and Beryl works nicely from 0.1.1 onwards.

Mac-mini and eMac: The installer crashed quite early in the install, I can't quite remember at what point. 
Ploughing on by hand with aptitude eventually got to a bootable state. The kernel links didn't get updated though, so it booted but the wireless connection no longer worked on the old kernel.
Once I realized what had happened and rebooted we had internet connectivity, but no X. Reconfiguring X sorted that out.


2 via Mini-ITX boxes: Kubuntu-desktop stalled things again.

Various IBM Thinkpads: not happy with Kubuntu-desktop, Opera.


With everything finally upgraded Edgy is nice and stable on all the hardware, and the default theme is now actually bearable :)
A nice piece of work, all in all. Can I have my SD reader on the 
X40 laptop working please :) ?

---

### Post by deadwing on 2006-10-29
Upgrade went perfectly well... almost TOO perfect...

---

### Post by TRAVISL on 2006-10-29
Upgraded my old Gateway tower and things went perfectly.  Install took forever though because I didn't see the box to accept the flash agreement so it could continue. ](*,) Once I clicked OK it took about 4 hours to upgrade from the alternate CD.

---

### Post by tmahmood on 2006-10-29
I edited my source.list and upgraded using Smart Upgrade. It took over 24+ hours on my 56kb (eh ](*,) ) but upgrade went smoothly... but the trouble start after the installations..,

1. found some packages were not upgraded (mainly python based) 
2. It was not using upstart for booting 
3. No Splash while booting

but the system was running fine..

Then I manually updated/removed packages and Now all the problems above are fixed But the thing is GAIM is locked in Synaptic and I can't neither upgrade nor remove it... I've tried to unlock it didn't work, anyone have any Idea how to remove the lock?

Its probably better to install ubuntu-desktop, ubuntu-minimal packages before upgrading.

---

### Post by Buffalo Soldier on 2006-10-29
I tried both; dist-upgrading and clean install.

Dist-upgrading went smooth except for 1 minor problem. System -> Administration -> System Log icon is missing from the menu.

Clean install was a lot better than my Dapper experience. Dapper installation always blanks out at the last step. Edgy clean install *feels* faster and it went without a hitch.

---

### Post by Rob_Frohne on 2006-10-29
Hi,

Fortunately I had a spare hard drive to experiement with.  I cloned the hard drive with dd before starting the upgrade via synaptic.  There were some problems with the upgrade (a couple of packages wouldn't install), but I wasn't too surprised because I had added a lot of packages to Dapper before the upgrade.  

When I finished the upgrade, I found that there was a funny little line of pixels under the mouse cursor that follow it around.  I found fglrx wasn't working, as it complained about not being able to load DRI.  So OpenGL is using Mesa.  Octave complained about not being able to write to /tmp/....

I went back to my Dapper CD and it is so nice to have everything working again.  I would like Gnome 2.18, but not if it doesn't work.

My advice to everyone is to upgrade with caution.  Make sure you have a backup that is easy to go back to.  I plan to continue working with the Edgy image I have, but my main woring install is still Dapper and I suppose it will be that way for a while.  

Rob

---

### Post by JohnLloydJones on 2006-10-29
Eventually, but only after much struggle

1st) the KDE desktop would not start. Thankfully I got a log in prompt and poke around in the logs: ' module ABI major version doesn't match server's major version' -- ouch. Googled up a page that asked if 'xserver-xorg-video-ati' was installed. Did the apt-get and interestingly, it installed and removed 'xserver-xorg-driver-ati'. Hmm, something renamed? That opened the magic door to X and KDE came up. 

2nd) No wireless -- expected as I use ndiswrapper. Did the make, make install etc. and there we are copnnected. It would be nice if someone could make this a bit more automatic updating, but blass those ndiswrapper folks; life would be hard without it.

3rd) Fired up Bluefish editor, did some work, hit Save As -- oops, segmentation fault. Still clueless on why, but Bluefish isn't much use if I can't save my work, so that's a pain. 
Oh and kicker still crashes after some time (seems to be when I wake the PC up after it has powered off the monitor; could be wrong there). That's a hoary old but that isn't specific to Edgy/Ubuntu.

---

### Post by JohnLloydJones on 2006-10-29
Eventually, but only after much struggle

1st) the KDE desktop would not start. Thankfully I got a log in prompt and poke around in the logs: ' module ABI major version doesn't match server's major version' -- ouch. Googled up a page that asked if 'xserver-xorg-video-ati' was installed. Did the apt-get and interestingly, it installed and removed 'xserver-xorg-driver-ati'. Hmm, something renamed? That opened the magic door to X and KDE came up. 

2nd) No wireless -- expected as I use ndiswrapper. Did the make, make install etc. and there we are copnnected. It would be nice if someone could make this a bit more automatic updating, but bless those ndiswrapper folks; life would be hard without it.

3rd) Fired up Bluefish editor, did some work, hit Save As -- oops, segmentation fault. Still clueless on why, but Bluefish isn't much use if I can't save my work, so that's a pain. 
Oh and kicker still crashes after some time (seems to be when I wake the PC up after it has powered off the monitor; could be wrong there). That's a hoary old but that isn't specific to Edgy/Ubuntu.

---

### Post by gmc on 2006-10-29
Too bad I can't vote twice. I've upgraded a webserver, which was originally just a simple server install of hoary and been apt-get dist-upgraded all the way to edgy, with no problems.

The other system (Acer 5672) was a dapper to edgy apt-get dist-upgrade and considering it's a laptop I consider myself fortunate. Everything except the built-in webcam is now supported. Hopefully the SPCA driver will take care of that in time for feisty.

G.

---

### Post by Drezliok on 2006-10-29
I tried upgrading my Xubuntu with the update program. I fought with that till I installed the Ubuntu-desktop package. Then it fired right up. Half way through it bummed out on me.

Tried Apt-get to finish at it told me to use a command. I forgot it now, but it smoothed everything out. Everything works.

I had to reset a setting in wine but that wasn't a big deal.

---

### Post by Iandefor on 2006-10-29
I tried using the official upgrade tool, it hung on some uim packages, and I was left with a totally borked system. I'dve done a fresh install, but I had used my last CD-R on a bad install disk.

I wound up just upgrading from my sandbox partition where I had Edgy (but in a development state) and adding my /home partition to fstab.

Things could have gone better.

---

### Post by hotani on 2006-10-29
Machine 1 (Dell desktop): Tried the update, it bombed somewhere during the process and on reboot I had no X. After that I did a clean install which went well with no problems at all.

Machine 2 (Dell laptop): Updater wouldn't even start because of some package problems. After a couple of hours of googling and digging thru the forums I found a command line fix for it which involved removing some packages. After that, the update ran without a hitch. Only problem on that machine with Edgy is that it has lost wifi. It sees the card but no networks - this worked fine in Dapper.

Machine 3 (home built AMD X2 3800+): Ran the update, which actually went off with no problems. Booted after that and realized I was using a kernel that did not support both cores of my chip. Tried booting to the 'generic' kernel which had the dual core support and was not able to. After a good deal of digging, once again there was a CLI fix that allowed booting with the new kernel and both cores were functional. More minor non-boot-related problems on that machine: the azureus-from-repos-doesn't-work bug got me, while in 386 single processor mode rhythmbox went ape-shyte and at some point when deleting files via the application it somehow sent my entire music library to the trash. On opening, rhythmbox would utilize 100% CPU for about 20 minutes as it read the library (before it deleted it). After fixing the kernel, it still uses a good bit of CPU when opened but otherwise is running fine. 

Machine 4, webserver (another Dell desktop): Staying with Dapper. :)

So for me it was a mixed bag. None of the system upgrades were without problems, but some were more severe than others (not being able to boot comes to mind).

---

### Post by RaiSuli on 2006-10-29
I upgraded with apt-get and ran into some problems:
1) very slow download speed on some packages
2) the xorg problem a lot of people experienced
3) mysteriously disappearing icons - the "restart" and "shutdown" icons only showed up after the 3rd for 4th time I booted Edgy

This is all solved, only problem that remains is the slow booting process. It takes considerably longer than on Dapper. I'm thinking of trying a clean install.

---

### Post by wilberfan64 on 2006-10-29
My Edgy 32 install went almost flawlessly!   Right out of the box I didn't have most of the problems I had in Dapper.

My Edgy 64 install was a teensy bit more complicated--mostly involving having to download and tweak the nvidia driver to get proper screen res, etc...

I'm having the usual Firefox32 issues on the 64:  Mplayer plugin doesn't work, Java crashes the browser, etc...    Thunderbird didn't start properly this morning...

Edgy 32 feels faster on the 32bit box--I'm not sure if Edgy 64 is faster...

---

### Post by Furesta on 2006-10-29
Hi folks, i just upgraded to from dapper to edgy using the official method (gksu "updtate... etc. etc.) and everything went fine, exept it took 7 hours between download and update (640 mbit DSL) on my PIII box.
Everything runs fine, X works, network works, and no strange stuff until now.
After hearing about upgrade armaggedons I made a complete backup yesterday of  my partitions using PartImage (great tool!) and today I made the big step. Just lucky? :-k 
Cheers

---

### Post by megamaced on 2006-10-29
I successfully upgraded Xubuntu using Aptitude. I decided to use aptitude over apt-get because it handles dependencies better.

Anyway, I followed [this tutorial]("https://help.ubuntu.com/community/EdgyUpgrades#head-0ee455b2d02f220b043c084f09dffb86c1c6bd79") when I upgraded

One thing not mentioned in that guide is that it's probably a good idea to quit GNOME/KDE/XFCE and go into a console before you perform the upgrade. This can be achieved by pressing CTRL+ALT+F1

Also note that there will be a lot of unresolved dependencies and upstart will not be installed at the first dist-upgrade. To resolve this, you MUST run dist-upgrade twice

---

### Post by yelloguy on 2006-10-29
My problems are over.  Complete reinstall took care of them :-)

I wasted 4-5 hours trying to update and then some trying to make it work.  Then Saturday morning I downloaded an image, burned it to a CD and booted from it.

My wireless card was the only problem I had after that and that was the same from Dapper.  Edgy gave me nothing new or better or shiny except the splash screen.  They could have at least improved the support for my (and presumably others') wireless card.  Netgear WG511 problems have been widely reported and fixes have been posted for Dapper.

---

### Post by Zdravko on 2006-10-29
I had a few problems, but nothing seriosly! I use dual-boot with WinXP and was afraid of loosing the NTFS partitions. But it seems Edgy eft is cool and knows how to upgrade correctly. Now I have a good running Edgy Eft machine (without any big problems). Well, good work!

---

### Post by siepo on 2006-10-29
I moved my Macbook to Edgy at the first beta, using aptitude dist-upgrade. There were some problems, but nothing very bad.

One nuisance was that I had to redo my .Xmodmap file.
Another was that for wpa-encrypted wifi I had to manually load additional kernel modules.
There were initially some problems with upstart, but that, too, seems to be ok now.

---

### Post by proxess on 2006-10-29
had problems with the locales

---

### Post by cbbyers on 2006-10-29
The upgrade from Dapper to Edgy was successful on my laptop, but I did have the problem with the missing swap partition and hibernation.  The solution on the forums fixed it, though.

---

### Post by jabudia on 2006-10-29
lots of problems with non solved dependencies, basically, I think, because post-installtion scripts during configuration of python related packages went wrong.... and still searching... :-(

I used the method chaging dapper into edgy on the spurces list, then apt get update and then dist-upgrade.

---

### Post by Thumbo on 2006-10-29
Complete failure, sadly.

The upgrade from Dapper to Edgy left the system only bootable with the 386 kernel - the generic kernel stopped, complaining about being unable to find etc/mdadm/mdadm.conf (though the file did exist).

I then tried a complete reinstall from CD. This time the kernel booted ok, but I could find no way to mount my second and third drives, where I keep user data - disk manager was not available. X performance was noticably degraded. 

I have now reverted back to Dapper.

---

### Post by joshua neff on 2006-10-29
I've been using Ubuntu since Breezy, and this was by far the easiest, best upgrade I've been through. I have [encountered a few quirks]("http://ubuntuforums.org/showthread.php?t=288119"), but nothing so serious that I can't use my computer.

---

### Post by Scheater5 on 2006-10-29
Had major problems (X was mangled!) but I ultimately got it to work, and it was worth the trouble!
I voted "serious problems" instead of "Really badly" because that was the one and only problem - and despite having to do some major searching, the actual solution was quite simple.  
[http://ubuntuforums.org/showthread.php?t=288037](http://ubuntuforums.org/showthread.php?t=288037)

---

### Post by obriente on 2006-10-29
I had several serious problems that probably would have driven a less stubborn person to simply start with a fresh install.

After the the update manager finished downloading and installing all the packages and removing the obsolete ones it was time for a reboot!
...
unfortunately non of my kernels would load... my updated 2.15 686, my original 2.15 386 that is the default dapper kernel or the brand new 2.17 generic...

it seems as if the update rewrote my grub menu.lst file and put the wrong partition info

booted a dapper live disk to repair.

rebooted.

launched the new generic 2.17 kernel...
SUCCESS!!!
got the fancy new Ubuntu splash screen...
30 seconds later...

Busy Box console!

can't access tty; job control turned off

GREAT!
this one took a lot more time to solve... and apparently it was my own stupidity.
corrected the partition info in Grub, but didn't correct the mounting location.

reboot...

load 2.17 again...

Splash...

AND NOW WE'RE getting somewhere... progress bar moves...
almost to the end... then

Feed garbage to the screen!
X crashed!
unable to load module i810

I go back and compare my xorg.conf files and find that the following line had been removed from the device section:
Option  "XAANoOffscreenPixmaps"

reboot...
load 2.17 again...

Splash...
progress bar almost to the end...
CRASH!
X gave a different error this time... that I can't remember off the top of my head..
more forum crawling...
eventually had to delete my xorg.conf-custom file

now edgy would boot...
but I lost my wireless conection!
network manager wouldn't launch.

had to re-install the Ubuntu desktop system to repair...

******* nightmare...

---

### Post by nardis_Miles1 on 2006-10-29
I have done three edgy upgrades at my house. The first went without issue (AMD XP3000+, nvidia GeForce FX 52000 graphics card, SATA and IDE disks).

The next two were installed through an apt-cacher archive on a firewall Debian (sarge) box. On these two machines, I had some installation issues. One KDE component wanted to overwrite a file. I had to force this with dpkg. After that, things worked well until I got to the xorg installation. The machine has an ATI Radeon card. Edgy had installed the 

xserver-xorg-input-all

X wouldn't come up because of a versioning problem. The server and the ABI class had different major numbers, i. e. 0.8 vs. 1.2, in their versions. I solved this by installing 

xserver-xorg-video-ati

I'm still having some small font problems. Gnome fonts look fine, but KDE looks like I installed ttf-preschool fonts.

The third machine also had small difficulties, again around some dependency issues. I did all of this very late Friday night and very early Saturday morning, so things are a little fuzzy. Doing an aptitude update and aptitude dist-upgrade was helpful. The third machine also has ttf-preschool on the KDE side.

---

### Post by obrient on 2006-10-29
Upgrade went well other than wireless card not showing up at all. Still trying to figure out what happened and what I need to fix it. Oh well thank goodness for 20+ feet of network cable :)

---

### Post by khedron on 2006-10-29
Hmm... I have just realised I cannot access my virtual consoles (Ctrl-Alt-F1 etc). Anyone else have this problem?

I'm using the fglrx drivers straight from ATI, but fglrxinfo is reporting that the Mesa drivers are being used. I reckon that this is at the heart of all of my problems with Edgy so far.

---

### Post by Fran on 2006-10-29
I went for a 'gksu update-manager -c' GUI upgrade over the net and to my complete surprise it moreorless worked.  It wanted to download about 0.8GB so I let it run overnight.  A couple of configuration questions to answer in the morning and 2 hours after that it rebooted into the new system.  Much cleaner than breezy->dapper via apt-get dist-upgrade.

Only downside was that my wireless card was non-functioning in edgy.  That required recourse to this [forum]("http://www.ubuntuforums.org/showthread.php?t=285733") but got fixed (thanks again Tasuki!) pretty quick.

---Fran

---

### Post by OneSeventeen on 2006-10-29
The upgrade worked for me, but the resulting system really didn't do it for me.  I'm assuming that's because I had tons of custom config files here and there, a few commercial apps I bought, and things like that.

In the end, I had a workable system, but applications would just stop working after a while.  (formatting and reinstalling now, but that's another post for another thread)

---

### Post by ajft on 2006-10-29
> **bean1975 said:**
> Needed to run apt-get dist-upgrade and apt-get  -f a few times and then a few settings got lost during the process but nothing serious. I am overly extremely satisfied by the smoothness of the upgrade.

Seems to be the summary of how my upgrade went.  Ran
gksu "update-manager -c" then went away for a day while it downloaded 1800 packages over the next 24hours, then came back and started answering assorted keep/replace queries from the installer.

After an hour or so of this I got a fatal error in trying to replace postgresql8.1 and the installer quit, telling me I had probably got a completely unstable system that would not boot!

Crossed my fingers, ran apt-get -f and apt-get remove postgresql (which I didn't even realise was installed, it certainly wasn't being used), then restarted.

Everything seems to work, a couple of minor problems with settings files etc.

---

### Post by FatherDale on 2006-10-29
Persistence pays. Not only did Ubuntu fail to load on either of my computers yesterday, it hosed the laptop. I put FC6 on the desktop. After I got the laptop revived last night, I installed FC5 on it. Bluntly, it worked, but was boring. So this afternoon I downloaded Kubuntu, on the off chance that it would be different enough to run on the laptop without exploding. It worked! I'm up and running in K6.10 on this box. Life is good. 

fd

---

### Post by zek725 on 2006-10-29
Firefox did not upgrade to 2.0 :( But synaptic shows it's already installed! :(](*,) :-k

---

### Post by joshua neff on 2006-10-29
> **zek725 said:**
> Firefox did not upgrade to 2.0 :( But synaptic shows it's already installed! :(](*,) :-k

Same here. I don't know why that is, but it's weird.

---

### Post by ChadMMc on 2006-10-29
Have an old Etower 500idx with a 12 gig hard drive and a usb 80 gig HDD for backup purposes.
Following the official upgrade instructions, the ONLY problem I had was 2 icons were no longer valid and I changed those. No problems yet. :)

---

### Post by frühstück on 2006-10-29
i did the gksu "update-manager -c" it downloaded all the stuff, then installed some of it, and then crashed...  GREAT!

now i am downloading the .iso, i hope my system can still burn CDs :rolleyes:

---

### Post by atari130xe on 2006-10-29
I did it successfully but... (always a but):
My modem US Robotics 56k PnP are not recognized by Edgy so.. No internet access.
I´m having problems to shut down my computer (it freezes at the end of the process)
anyone has some help?:(

---

### Post by NewDisciple on 2006-10-29
I updated using gksu update-manager -c. I can login but that's about it.  The gtk-engines-eazel will not install.  I know that it is a Debian pkg so I'm kind of thinking that it might be missing some dependencies.  Hopefully it can be fixed otherwise I'll have to fire up my Dapper cd.  I anticipated a few problems but, nothing like we are seeing with this release.  Prior to this release I did not see anything in the forums that would indicate serious problems.  Right now I'm using a live cd from another distro.  I imagine that there are many who don't have a second computer, or live cd's or any other way to report on or research their upgrade problems.

---

### Post by h2gofast on 2006-10-29
slice of cake here.

---

### Post by grkravi on 2006-10-29
I first tried to install Edgy in a new partition from the live CD but didnt get the GDM after the boot process. It was hanging.

I then tried to upgrade from Dapper using aptitude and it went on well. But after rebooting, i again didnt get gdm working. I rebooted into recovery mode and found xorg installed. 
Is edgy using 915resolution ? i am having problems with it on my Dell Inspiron 5160 laptop - "unable to determine bios type".

I reverted back to Dapper now.

---

### Post by felosi on 2006-10-30
wow what a screwed up dist-upgrade for my xubuntu, had to completely reinstall. X wouldnt install right, never could get it to install all packages even with -f.
I think Ill stay with dapper for a while longer

---

### Post by ChrisVio on 2006-10-30
Upgrading from Dapper to Edgy was a total mess. I ended up doing a clean install. "It should just work." Yeah, right. What happened to that? This experience takes me back to the days of Windows 95. I feel I shouldn't be complaining because all is free but, if you're going to do something, do it right! And screw the release schedule. Test test TEST! I switched to Linux to get away from this nonsense.

---

### Post by bobpaul on 2006-10-30
gksu 'upgrade-manager -c' complained that it couldn't do the upgrade, so I editted my sources.list and did an apt-get update; upgrade; and dist-upgrade...

Lots of packages were held back, or dpkg-configure error'd out, or everything else. Played around with aptitude etc and couldn't resolve it. Eventually I had to reboot and now X won't launch. So I have a mess of my dependencies and text only. Currently on the live CD separating home to a separate partition so I can re-install.

---

### Post by mtpadilla on 2006-10-30
Had a very standard 6.06 on my IBM Thinkpad and everything was beautiful. Did an upgrade using the method recommended by Ubuntu, over the net, and things went to crap really fast. Couldn't even log in as once it started to boot it complained of some sort of xorg problem which I couldn't understand. I just did a fresh install and now things are great. The fresh install was fast to get up to speed since I had a separate /home partition, keeping all my main application config files, etc.

So in a nutshell...upgrade: crappy, fresh install: superb.

Ciao!

---

### Post by itchanddino on 2006-10-30
The 2.6.17 kernel won't boot on my laptop.  Neither the livecd nor the upgrade method works.  I did a successful upgrade, but it stalls the same exact way the livecd does.

---

### Post by angrykeyboarder on 2006-10-30
> **kwilliam said:**
> Because Edgy was supposed to be more, well, "edgy", I wondered how things were going.

I'll try to turn this into a poll if I can figure out what button to press.

I never have problems upgrading an operating system. That's because I don't.

I only do clean installs.

---

### Post by cowbean on 2006-10-30
I upgraded by %s/\sdapper/ edgy/g in my sources.list, then running aptitude update && aptitude dist-upgrade && aptitude dist-upgrade.  Only problem was no 3d acceleration (on an acer laptop with ati x1600 graphics), which was fixed by disabling composite in xorg.conf.

I was honestly pleasantly surprised that things went smoothly.  HOWEVER, I was fully expecting that it would trash the install... so I made a systemrescuecd cd and backed up my partitions so I could go back to dapper.  I highly recommend doing this whenever your system gets to some kind of steady state, or before attempting a drastic upgrade.

Amazingly, I got Xgl / Beryl working too.

---

### Post by msandersen on 2006-10-30
Looks like my upgrade has crashed.
I had someone download the Alternate CD (8 min on ADSL2), since my connection is slow. I used the official method with the upgrade script on the CD. Even with the CD, it needed over 300MB downloaded. Over 14hrs later at modem speed, with an estimated 13min to go at the config stage, it has crashed on asking about whether to keep the gconf config (I asked to see a diff). Pretty pathetic all-round. Linux is a product of the Internet, and needs fast broadband, and hence ironically not even ideal for poorer countries. I may force-quit the update manager and try the apt-get method, as I'm pretty sure it won't resatart properly. Failing that, a re-install seems the only way out, and another marathon installing extra software and codecs etc with Automatix or EasyUbuntu.
This is just a test machine, as problems like these is why I cannot depend on it and why I cannot recommend it to non-techies who aren't prepared for getting stuck on a commandline. 14+hrs just to bomb out is less than impressive. Microsoft isn't exactly threatened by the current state of Linux for the Desktop.

---

### Post by Sariel Amraphel on 2006-10-30
Well, I didn't have that much trouble with upgrading.
Only thing was that X didn't want to start up (probably because of GDM being faulty because of my aiglx configuration of X, beryl)
What I did was:
- edit /etc/apt/sources.list, change everything from dapper to edgy
- apt-get update
- apt-get upgrade
- apt-get dist-upgrade
- apt-get upgrade
- reboot
- oops.....X has problems.
- restore backed up version of xorg.conf and gdm.conf and gdm.conf-custom
- restart gdm
- up and running......AND FAST!!! :)

Edgy is much more responsive than the previous versions, with aiglx and without :)



edit: oh, btw, updating was nice and quick: 3 hours and done, including downloading from a site that was kindof full (which only took 15-30 minutes or so)

---

### Post by uid0 on 2006-10-30
Things went pretty well, but the upgrade broke my cd recording capability and some of the system admin applets disappeared. I'm going to muck with it a day or two longer and if I can't get it working is Nuke & Pave time...

---

### Post by MeneK on 2006-10-30
I've got it!

2 hours downloading the new packages, plus 30min of installation. 

I only got two minor problems and one was my own fault (I was using XGL/Beryl from non official repos)

a) The system restarted ok, but XGL/Beryl wasn't working and the system was really slow. I went back to Xorg/Metacity, updated sources.list with the new repos for Edgy and reinstalled all the packages from Beryl. I also get rid of the default "compiz_core" (it seems it was interfering with Beryl). And then, everything went back to normal state, even a bit faster than with Dapper.

b) The new usplash was horrible and i couldn't access the terminals (CTRL+ALT+F[1..6]). I had to add the vga=xxx option to the boot options. 

Now my system is working perfect. The start/close times are a lot faster and the system seems quite stable, so this is my advice:

- REMOVE ANY NON-OFFICIAL PACKAGE BEFORE UPGRADING !!!

- CROSS YOUR FINGERS. ;)

(sorry for my crappy English)

---

### Post by rrwo on 2006-10-30
My problems in the upgrade:

Ones which I think are fixed:
* Apparently the en-GB language pack was not available initially, which
  caused many warnings (and errors?) in the process.
* The i810 video driver was not upgraded, so I could not start X.
* tetex would not upgrade, I think due to a conflicting style file
  I installed. I had to remove (backup) my old texmf folder
  and reinstall tex-common, which seems to have worked, though now I have
  to manually re-install various styles and classes. :( 

Outstanding issues:
* Hibernate and suspend are broken.
* The upgrade removed various packages for unknown reasons. I copied the
  list into a file for diagnosis and reinstallation later.
* I'm using XUbuntu.  The labels in the settings manager are mangled
  (they begin with "Button Label").  Icons are also garbled.
* I need a working version of vte4 so that I can use xfterm4. I'm really
  annoyed about this not being fixed.  libvte exists as a dead package,
  it seems.

---

### Post by merwizard on 2006-10-30
I performed the update using apt-get dist-upgrade. No showstopper, just the following problems after upgrade:

The sound doesn't work at it should. No dmixed alsa anymore. I had to write my own .asoundrc where I employed dmix/dsnoop/asym. This is weird, as there was no /etc/asound.conf or .asoundrc in Dapper, and sound was working on multiple channels (Nforce2 chipset)

No more splash image at boot. The screen is going dark and the monitor produces a warning messagebox on the screen about setting the correct resolution. I can't see anything until gdm loads and X fires up. The splash screen used to work in Dapper.

The HP Deskjet 3940 printer again stopped working in KDE due to the same bug present also in Dapper (empty printer filter or so).

Some dependency problems preventing upgrading of some python packages

Broken Romanian language translation of the Update Manager, preventing it to work properly. The Software Properties applet crashes when launched, due  to this bug.

Cannot use the open source drivers for my ATI 9200SE video card anymore. On startup, X complains about the wrong version of the drivers (?). Fortunately, the proprietary fglrx driver works fine, with both overlay and  3D acceleration functional. For GL to work, I had to remove the Composite extension from xorg.conf. 

Overall Edgy works fine. Good job team! It is as usable as Dapper was for me. The most annoying problem for me is the sound problem, but this is (almost) fixed.

---

### Post by merwizard on 2006-10-30
> **zek725 said:**
> Firefox did not upgrade to 2.0 :( But synaptic shows it's already installed! :(](*,) :-k

Check if you have another version of firefox installed, besides 2.0. See where /usr/bin/firefox symlink points. If this symlink exist already and points to a nonstandard location, a "firefox-ubuntu" symlink will be adittionaly created.

---

### Post by cosborn72 on 2006-10-30
Mmmmm...... I retrospect, I voted incorrectly.  Assuming I could only vote once,I chose "minor problems".

I reality, my vote should have been.

Edgy on a X86- all smooth
Edgy on a PPC- total failure. can't start X and no ethernet.

---

### Post by JediSpam on 2006-10-30
worked flawlessly for me with a fresh install. i have a p4 3.0 ghz socket 478 with nvidia 6800 gt. i managed to get steam working flawlessly as well too :mrgreen:

---

### Post by ssam on 2006-10-30
perfect on 3 machines.

i dont use any of the dodgy scripts. had officia lbackports installed. and use the instructions from the wiki for restricted formats [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29)

---

### Post by Allan Eising on 2006-10-30
Well, I didn't have any blank cds so I installed 6.06 and then upgraded that one. It went quite well, but I had to manually reinstall xorg. Besides that, I have no real problem. The new init system wasn't installed, but I have just installed it and it has no problems running.

---

### Post by Mr Green on 2006-10-30
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Followed the instructions above.

Major crash. Starts to boot but crashes after a while, my guess it's when the login screen is supposed to come up.

Haven't tried "sudo apt-get install xserver-xorg" which I think has been added to the wiki tonight.

[UPDATE] Installing xserver-xorg fixed everything so now I'm up and running with Edgy! :KS [/UPDATE]

---

### Post by msandersen on 2006-10-30
I managed to recover from the installer crash after some fiddling in the terminal. What worked in the end was sudo xkill to kill the stalled installer, dpkg --connfigure -a to finish configuration, and reran the upgrade script gksu "sh /cdrom/cdromupgrade". The system restarted and seems to work fine. A few quirks, like using the Xubuntu GDM theme (I'd tried and uninstalled Xubuntu-desktop previously) and Firefox being 1.5, which I attribute to Automatix (installed in /opt). Haven't tried everything, but notice a few cosmetic defferences. 
It's a bit annoying that you get a fresh installer CD and it still requires a massive update via the internet. Same happened with the update to Dapper, which otherwise went fine. Apart from Gconf config crashing and taking the installer with it, this update seems to have gone fine. I doubt it made the changes to gconf once I finished the update, so I don't know if anything's misconfigured.

Since FirwFox 2 seems to be installed according to Synaptic, can I simply delete the version in /opt that Automatix installed? Or do I need to use Automatix? I think it may have put some symplinks somewhere.
EDIT: Will change symlink /usr/bin/firefox to match /usr/bin/firefox.ubuntu as per previous post.

I'll go ahead and upgrade my main machine. I have XGL/Compix as a separate session, so it should be OK. Some people with XGL/Compiz/Beryl enabled have had X problems on upgrading. Until it's stable and supported I wouldn't have it on by default. Guess I'll have to research Beryl and so on for Edgy.

---

### Post by bobpaul on 2006-10-30
> **MeneK said:**
> 
- REMOVE ANY NON-OFFICIAL PACKAGE BEFORE UPGRADING !!!

- CROSS YOUR FINGERS. ;)

I did the second one, but I didn't do the first. For future reference, is there an easy way to do that? I tried simply removing the non-official repos but that's not enough, obviously. I've used tools like automatix, so I don't always know the package names that are unofficial.

---

### Post by archis on 2006-10-30
I'd be filing this one under 'almost carefree'. I performed a second-generation upgrade (Breezy-Dapper-Edgy) on this machine using gksu "update-manager -c" and everything went well, although I encountered the same locale settings warning messages as [pommattski]("http://www.ubuntuforums.org/showpost.php?p=1676453&postcount=68") through the first two thirds of the upgrade process -

[FONT=Courier New][COLOR=DarkSlateGray][INDENT]
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_AU:en",
        LC_ALL = (unset),
        LANG = "en_AU.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").[/INDENT][/COLOR][/FONT]

I think it stopped as soon as the new locale files were being set up and configured (duh). There was also a spurious update-manager crash message sort of 70-80% into the package configuration process that was caught by the bug reporter -

[FONT=Courier New][COLOR=DarkSlateGray][INDENT]Memory status: size: 50708480 vsize: 0 resident: 50708480 share: 0 rss: 12423168 rss_rlim: 0
CPU usage: start_time: 1162163414 rtime: 0 utime: 1526 stime: 0 cutime:786 cstime: 0 timeout: 740 it_real_value: 0 frequency: 529

Backtrace was generated from '/usr/bin/update-notifier'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7481463 in ?? ()
#2  0xb7f4bf58 in ?? ()
#3  0xb7f198e6 in ?? ()
#4  0x00000d33 in ?? ()
#5  0xbfa78058 in ?? ()
#6  0x00000000 in ?? ()

[/INDENT][/COLOR][/FONT] apparently with no immediate consequences but I had some problems with update manager after reboot, see below.

Everything went smooth at first login - no problems with X, new usplash shows just fine although I have the impression that the new logo is slightly bigger than it ought to be, perhaps due to some inherited vga=x setting in grub's # kopt. I'll check into that.

The performance boost is very noticeable on my machine - boot was pretty fast with Dapper already but the actual desktop performance has really increased. Everything's a whole lot snappier.

Ran into two post-install problems: Update Manager and, unfortunately, Firefox. Using Update Manager for the first time after login, it tells me 'cannot install all upgrades, use Distribution upgrade' and then fails with 'cannot calculate upgrade'. I thought perhaps something broke during the upgrade but Synaptic reports everything's fine, no broken packages or anything. So I switched on and adjusted my third-party repos; then I decided to re-install update-notifier and upgrade-manager from Synaptic and the problem just went away. Looks like it had something to do with the spurious crash message I had received previously.

The only real issue seems to be Firefox, unfortunately. It crashes or doesn't open at all, so I'll need to check into possible fixes for that. The solution offered earlier on this thread - reducing DefaultDepth from 24 to 16 in xorg.conf - is not a route I want to take just to get FF going.

So yes, an upgrade not without issues but doing great once I get FF sorted.

**Update:** Sorted. The cause of the Firefox segfaults turned out to be an incompatible pair of extensions that were not caught by the extension compabitbility test at first run. I ran [FONT="Courier New"][COLOR="DarkSlateGray"]firefox -safe-mode[/COLOR][/FONT] with extensions switched off and located the troublemakers. That's a *very* common problem with Firefox upgrades I might add - some third-party FF extensions will not be caught by the compatibility test and occasionally cause trouble; not all that surprising given the scale and scope of the weird and wonderful third-party extension universe that has sprung up around Firefox. So the issue here was really Firefox's extension manager and had nothing to do with the edgy upgrade per se.

---

### Post by Richard Sevenich on 2006-10-30
I encountered ATI X700 problems which yielded blank screen from the liveCD. Going to console mode yielded an unusable screen also. Using info from the forums, I worked round the problem and now have a working 'radeon' driver and a usable Edgy install.

Looking at the forum, it appears that the beta testers did a decent job, but whoever interprets their work and makes release decisions did not do as well.

Regards,
Richard

---

### Post by stuart.crouch on 2006-10-30
I have a desktop and a laptop - the desktop couldnt load the live cd (it did work with the dapper version though ?!?), so I ran the update.

gksu "update-manager -c"

Reboot, got no X.  Downloaded and installed the text version, got an X desktop.  Installed my ATI drivers, and a reboot later, no X again.  Also it didnt fix the mouse jumping problem I was having, so I've switched the desktop PC back to suse.

I did the web update on my laptop, but that hung about half way through.  Im dreading what state it will be in when I boot it up next time :(  The laptop doesnt handle suse very well, but ubuntu everything just worked, so I will be getting ubuntu back on the laptop :)

---

### Post by fabioleitao on 2006-10-30
](*,) 

Total disaster... My Compaq M700 wont start anymore, no matter what I try. 

No problem downloading, or setting up the upgrades via "gksu update-manager -d -c" but after that, nothing else works.

Initially, after the first boot, I assumed it might be a Xorg incompatibility or wrong configuration to its ATI video card, but I've realized I can't even get the bash prompt.

I'll try a fresh install as soon as I finish downloading the CD image, but I it still sucks, I'll run back to 6.06 Dapper and wait for the 7.04

---

### Post by yalding on 2006-10-30
> **fabioleitao said:**
> ](*,) 

Total disaster... My Compaq M700 wont start anymore, no matter what I try. 

No problem downloading, or setting up the upgrades via "gksu update-manager -d -c" but after that, nothing else works.

Initially, after the first boot, I assumed it might be a Xorg incompatibility or wrong configuration to its ATI video card, but I've realized I can't even get the bash prompt.

I'll try a fresh install as soon as I finish downloading the CD image, but I it still sucks, I'll run back to 6.06 Dapper and wait for the 7.04
I did the samething for my two machines. It seems no one in the ubuntu testing team has ATI video cards. Strange.

---

### Post by jgcamp99 on 2006-10-30
Mine was hopelessly hosed after a couple of attempts to fix it, no fglrx for the ATi dispaly, nothing (none of the selections in grub that is) would boot into a gui, just a terminal style look like the old days of DOS. Fortunately, I made backups of what I needed and did a clean install. All I have to do now is reinstall applications and transfer the data back over from the usb drive. I tried with the desktop cdrom iso download, that failed me, then I did it on-line, it worked, but with the fglrx issues. I figure it'l take me a week or so to get the Edgy back to Dapper installation functionality. Oh well, that's the price for a new OS. I feel better knowing it's a clean install vs the upgrade anyway. I just didn't want to do it with a clean install. Edgy will be around for a long time coming on this box, I can't upgrade every 4 months like this, it's not worth the turmoil. Interkernel updates go smoother, but this was traumatic. I don't know so much I gained anything out of it, other than to say it's Edgy and not Dapper. Unfortunately for Linux, the kernel changes every 6 months (well that's good and bad, good that we get new and improved, bad the hell you have to go thru to get it there.). I don't know that OS X changes, they stick with the same kernel throughout an Os, it last a year or two. Windows, they're getting ready for Vista, I figure they'll make that another 5 year OS.

---

### Post by tombott on 2006-10-30
things went really wrong.
When trying to boot I get an unreadable message loading X.
X then fails to load 6 times in 90 seconds so halts.
If I CTRL-ALT-F2 login as my user then force x to load by typing exit i can get X to load, but after a few minutes the screeen screws up and I have to reboot.
Am using Acer Aspire 9500 with ATI x700.
I have tried using the ATI, RAEDON, VESA and FGLRX drivers and only FGLRX give me a display, the rest just give the black screen.

sorry i forgot to add it does this in recovery mode as well, but only recovery mode eventually lets me log in.

---

### Post by tombott on 2006-10-30
> **Richard Sevenich said:**
> I encountered ATI X700 problems which yielded blank screen from the liveCD. Going to console mode yielded an unusable screen also. Using info from the forums, I worked round the problem and now have a working 'radeon' driver and a usable Edgy install.

Looking at the forum, it appears that the beta testers did a decent job, but whoever interprets their work and makes release decisions did not do as well.

Regards,
Richard

can you point me in the direction of the info?

---

### Post by bruce89 on 2006-10-30
My upgrade was absoultely fine, but it was around the knot-3 milestone.
[B]
Before attempting an upgrade, remove all 3rd party stuff, and do not use scripts to install stuff, as they mess everything up.[/B]

---

### Post by blunden on 2006-10-30
I upgraded when I was in school. For some reason though the wlan was very slow, probably because a lot of people were using it. However this made the download a long process, and it took more about 2,5 hours. :( When booting it I was greated with a black screen, and some checking showed that my xserver for some reason was broken. :( This wouldn't really be a problem if the school's wlan didn't require you to login before getting internet access. ](*,) My friend and I solved it by spoofing the mac-address of another friends logged in computer and setting the same ip as him and adding the gateway. It gave some strange results at first but after a few tries we were able to download a working xserver. Phew... Now, though the system works very well. I noticed though that the 686-smp kernel function was now included in the generic kernel. Is that really smart?

---

### Post by bagatonovic on 2006-10-30
No problems at all.

I updated sources.list to the ones listed at UbuntuGuide
Ran the dist-upgrade
There were a few packages held back, but it was easy to resolve those with apt-get install <held back package name> and resolve it that way.  My system has been running for 4 days without trouble.

:-k   I feel bad for all the people who had to reinstall.  That really sucks.  At least you get a working Destkop while you're installing :D

---

### Post by NemesisUK on 2006-10-30
I too had no problems at all. Over the weekend I upgraded 5 machines and not a problem.

---

### Post by KraftyUA on 2006-10-30
My upgrade to Edgy was probably the most difficult upgrade I have ever done. 

First I ran into problems with Ubuntu-desktop, fixed that, then had the problem many others are having with X.
I also got a whole slew of error messages, don't remember exactly what they were now. Ran through the upgrade again to try to fix them, restarted, and got a kernel error message. 
Couldn't login, couldn't get to a terminal. 

Rebooted with Knoppix, mounted the hard drive, and ran through the steps of upgrading again. 
This time I got error messages with the install of Firefox 2.0. 


After about 6-7 hours my machine is working again.

---

### Post by Niber on 2006-10-30
Made the upgrade using update-manager and all went perfectly on dell latitude 505.

---

### Post by Richard Sevenich on 2006-10-30
Hello Tombott.

As best I recall:

1. boot via live CD gives black screen in X and unusable console via ctrl-alt-F1

2. reboot but first choose a resolution (via F4 or F5 key?) that should work; I chose 1024x768

3. then reboot of live CD again gives black screen in X, but now a usable console via ctrl-alt-F1

4. replaced /etc/X11/xorg.conf with one from another partition and used 'vesa' driver (I always have working Linux versions lurking in other partitions)

5. restarted kdm (not reboot) and got a usable X display

6. Chose to install into an available partition

7. Installation evidently kept my xorg.conf

8. After reboot tweaked xorg.conf adding line from forums
        Option "MonitorLayout" "LVDS,AUTO"
(no idea if necessary)

and changed driver to 'radeon'

9. this worked, but I changed to different resolution to fit my tastes

Clearly some steps were duplicative, but I though it best to give the whole scenario in case magic was involved.

Regards,
Richard


Regards,
Richard

---

### Post by dreamer_uk on 2006-10-31
My experience? Frustrating.
I love Ubuntu. Sinse 5.10. I keep love it. But the upgrade, think, affects distro reputation.

1. Package installation stuck somewhere in the middle completely. Well I killed it.
Sinaptic asked me for some password, that it never did before. I failed here.
dpkg wisely suggested options to continue broken installation. But again got stuck on some gstreamer package completely.

2. System reload came to its inability to load itself. Full stop - useless system. (Init got removed?)

3. Loading Windows, burning Ubuntu 6.10 live CD to rescue. Not at this time! It simply can not recognize my logical volumes!!! lvm2 is not on live CD.

4. Burning INSERT rescue CD, insured it can do LVM. Mounting my partitions, chroot, dpkg. Seems upgrade finished.

5. Loading 6.10. More or less fine. Mono stuff does not work (F-Spot, Beagle). Reinstalling mono* packages helped.

= Experience not for novice user!!

---

### Post by tazzz on 2006-10-31
Had no more X after bootup, had to apt-get install RADEON packages and then it was ok. Dont know why it didnt take those packages during dist-upgrade ..
Also the 386 kernel wasnt working at bootup(Kernel panic), so I put the "generic" which was more tuned towards my cpu anyway as default after choosing it at bootup and that was most of the trouble. A couple of icons I had to reset, and gaim had to open port 1863 in firewall wheras before it went ok through http proxy. Evolution seemed slow and freezed a couple of times at first, but now it seems fine again ..
pppconfig still works but I get ARP errors which I didnt get b4 the dist-upgrade.. Havent figured that one out yet ..
Other than that its great to have an uptodate distro again, like every ~6months ..   :D
keep up the good work !

---

### Post by zek725 on 2006-11-01
Xubuntu Dapper to Xubuntu Edgy upgrade successful with problem with courier-authdaemon  which was resolved with a dirty fix [http://www.ubuntuforums.org/showthre...hlight=courier](http://www.ubuntuforums.org/showthre...hlight=courier). However, Firefox failed to upgrade to 2.0. For some reason it was even downgraded to 1.5.0.2!

I tried a clean install of Xubuntu Edgy Eft but halt no longer powers down the pc [http://www.ubuntuforums.org/showthre...43#post1090643](http://www.ubuntuforums.org/showthre...43#post1090643) but was solved by adding acpi=force lapic to the kernel entry in /boot/grub/menu.lst.

---

### Post by dotdot on 2006-11-01
hey folks,
I run ubuntu on several laptops ...
all now different.. oops
I tried upgrading on one from 606 to 610.
Upgrade went off fine.
Ndiswarpper :) problems caused ..well unhappiness.
Luckily i had cable on said lappie.
Download ndiswrapper... etc reconfigged.
..Alas .. still not working.
I've postponed all upgrades till i get that simple task working - if only it was eh folks ?

Alas edgy mas actually made me - like a few others edgy about edgy...

Can't say i'm too impressed - you find people who've used something for a while... think like me - "i dont have the time , man , it's not working... is it rubbish ?  " ...We know it's not - but alas - well I don't see too many - "ok people here's why it's not working as it did before.." emails - do we ?

..have fun..

---

### Post by Footer on 2006-11-01
> **dotdot said:**
> well I don't see too many - "ok people here's why it's not working as it did before.." emails - do we ?

**AMEN!**  What I'd like to know is **WHY** as well.  My upgrade went OK.  Just a few problems (which is the way I voted).  But my current gripe is FONTS.  Just do a search in this forum and you'll see what I mean.  Two big problems for me currently:  OO fonts and not being able to get vncviewer working because of apparent font issues.

---

### Post by ephemeros on 2006-11-01
i made 2 clean edgy installs of xubuntu (me) and kubuntu (my gf), i didn't upgrade.
  the biggest problem i encountered is i broke some CDs trying to burn an iso image. i tried graveman, k3b and cdrecord. i don't know if this is an ubuntu issue, as long as i found a post, a dude using peanut and the same versions of the programs having the same problems.
  another thing is the x display (on both desktops) looks weird (some apps box selection not visible, different colors, messed fonts), usually motif.
  sometimes the apps slow down, like overloading something (thunar+gaim+some others open on xfce, gimp+maya on kde).
  i consider edgy a failure for now, but i trust the guys, i am sorry i don't have the time to test it further, i'll need to reinstall dapper :-\ .
\m/

edit: i use edgy now, it was my mistake i hasted to reply here. the hour i installed edgy was a "cursed hour" :D :
 -my CD writer failed (i don't know when, but i don't use it anymore), this is not an edgy failure;
 -the composite feature (ENABLED BY DEFAULT IN EDGY) cause my display problems in maya, i consider it caused thunar and other apps to freeze, as long i didn't experience any more problems after i disabled it(tested on xubuntu only);
 -graveman was known not complete at the time i tried it.
 -i used also re-writable worn CDs;
 -everytime i checked the booting CD didn't pay attention to the number of failed checksums (this is a stupid anger reaction, i appologise).

---

### Post by nerval on 2006-11-01
no

---

### Post by reyfer on 2006-11-01
I hope I'm wrong, but after reading this thread from the beginning, and consulting other threads and forums, seems that GNOME is a big part in these problems, since almost 89% of the people that report problems use GNOME, against 9% that use Kubuntu and 2% Xubuntu. :-k

---

### Post by mgmiller on 2006-11-01
If a noob had done my upgrade, he/she would have thought it went perfectly.  I used the gksu "update-manager -c" method.  It asked only 3-4 minor configuration questions, gave no error messages and booted into x without comments running the fglrx driver.  This was using an ATI 9600 with s-video out driving a TV as the only display.  fglrxinfo, however showed that I was still using MESA instead of ATI.  I knew this was due to needing to disable composite rendering in xorg.conf, so I did have to edit that file by adding the following as the last few lines:
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
and issue one command:  ```
sudo aticonfig &#8211;overlay-type=Xv
```

I also needed to remove a vga=786 command from /boot/grub/menu.lst that I needed in dapper to get the graphical boot screen to render at the correct size.  Good to see the upgrade correctly read the "automagic" lines and applied them to the new kernel, although, with Edgy, this one item was no longer needed.  

After that, 1 reboot, and I was back on my normal accelerated desktop with NFS and network printer support and everything else I have tried working fine.

Next, I may try a little beryl magic.

My total time was about 12 mins. to download the approx 600 MB of files (gotta love cable, better than 1100 KBPS for the whole download) and another 35 mins to configure/install them and then a few mins. to make the changes I needed.

All in all a smooth upgrade, but not "perfect".  I have to knock it down 1 notch because of the video xorg.conf issue.  Since this is a known item in the starter guide, I think it could have been rolled into the upgrade somehow.  The menu.lst item, I don't see as a problem, rather I think the installer did the right thing by carrying my settings through to the new kernel.  

As a non-noob Ubuntista I give it 4.75/5 beans.  For a noob, I would give it 4/5 beans. 

System specs:  AMD xp2600+ with 512 meg ram, ASUS A7N8X mobo, ATI 9600, IDE HDD, ASUS DVD-rom, Floppy.

---

### Post by krypto_wizard on 2006-11-01
I was happily using Dapper until Edgy came and destroyed my partition.

I did the following thing to move from dapper to edgy.

1. Changed all occurrences of dapper to edgy in the /etc/apt/source.list

2. sudo apt-get update
2. sudo apt-get dist-upgrade


Then I could never boot.

When the computer restarts it says " count not mount the partition /vmlimz.... sometthing like that.

I can't even login in the recovery mode....its halts after some tiem and says "file checking .."


Can you please help me and help me restore my Linux partition.

I don't want the hassle of going through the pain all over again.

Thanks

---

### Post by dreamer_uk on 2006-11-02
> **krypto_wizard said:**
> 
2. sudo apt-get update
2. sudo apt-get dist-upgrade


Then I could never boot.

When the computer restarts it says " count not mount the partition /vmlimz.... sometthing like that.


I found that the upgrade in my case changed path in grub menu list, adding /boot prefix to the location of images. That is wrong, since "/boot" partition, I got separate, is mounted as root initially. 

From start grub menu try to check boot string. If it contain /boot prefix to linux image and initrd, try to remove it. Then load the system.

If succeded, edit /boot/grub/menu.list with the fix.

--
Do not panic. Nothing happened to your data.

---

### Post by davro on 2006-11-02
Before i was having problems with lock ups (breezy, dapper), i posted quite a bit about my problems, but i gave up bad me.
 
Installed edgy and everything is fine, no lock ups yet(temps fate)  ;)
Really am pleased to back using ubuntu on my sony vaio pcg-z1rmp :D 
Everything is running nice and fast, generic kernel 8)

---

### Post by merlyn on 2006-11-02
No hassles whatsoever!

I simply made sure that the metapackages ubuntu-desktop and ubuntu-minimal were installed prior to upgrading.

Cheers.

---

### Post by archis on 2006-11-03
> **reyfer said:**
> I hope I'm wrong, but after reading this thread from the beginning, and consulting other threads and forums, seems that GNOME is a big part in these problems, since almost 89% of the people that report problems use GNOME, against 9% that use Kubuntu and 2% Xubuntu. :-k

Nice number-crunching there, however... have you factored in the percentage of people who are actually using gnome over kde / xfce on this distro? Once you do that, the number of people reporting problems *and* using gnome might not say much any more.. just a thought.

My earlier [reporting of two issues]("http://www.ubuntuforums.org/showpost.php?p=1687768&postcount=201") for example is about two very minor issues with trivial solutions: ironically, [FONT="Courier New"][COLOR="DarkSlateGray"]update-manager[/COLOR][/FONT] was one of them (sorted by re-install) and a very common problem with Firefox upgrades (third-party extension incompatibilities). Neither of those two issues fits particularly well into a "problems with gnome" or "problems specific to gnome" category even though I am a gnome user.

---

### Post by gu014 on 2006-11-03
corrected problems:
was not able to log in with GNOME session(default)
  - all other sessions worked(KDE+fluxbox)
  -when attempting to log into GNOME the screen flashed and looped     me back to the sign in screen.
  *solution - booted ito recovery mode and changed the permission on some file(advised in #ubuntu)
- my bottom launcher panels launchers have been removed.  the launcher panel still remains with all settings preserved but, the launchers themselves have been emptied out. icons,name,command.  i had about 15 launchers and now they all show the default gnome icon with no settings.
  - i corrected this issue by adding all the launchers back manually.(a wine issue now remains)

outstanding problems:
- libdvdcss has been removed and is not found in apt-get
- my bottom launcher panel is not working correctly(only the wine apps)
  - when i click on a wine app from my bottom launcher panel nothing happens. however, when i load the app from the command line there is no issue(i.e. wine /home/xx/.wine/drive_c/Program_files/dvd_shrink/dvd_shrink   loads without issue.

-overall the system just feels slugish. before the upgrade my system was runing very smooth(intel 2.8ghz,3g ram,sata HD,avi x300 video)

guess i will just have to search for some solutions.

---

### Post by Max_Might on 2006-11-03
Yesterday finally got Dapper Upgraded to Edgy with 2 minor problems:
1) After the upgrade, I restarted the system and when it tryed to boot it failed to scan one of the partitons so i just removed t from fstab :) I dont really need this 8MB partiton :)

2)The X server failed to start, so I rebooted in started Ubuntu in recovery mode and reconfigured it.

When I first started Firefox 2 it crashed, but after that crash it is working perfect :)

So I am happy with Edgy ... great work guys :)

---

### Post by gu014 on 2006-11-03
> **Max_Might said:**
> 
2)The X server failed to start, so I rebooted in started Ubuntu in recovery mode and reconfigured it.
)

Can you elaborate a little as to the problem as i was having the same issue and was wondering how you corrected it.

---

### Post by zeca_pedra on 2006-11-03
> **coastdweller said:**
> The upgrade caused an unstable system that forced me to reinstall.

Same here! Had to burn alternate cd iso and make a clean install.
Now I'm having problems with something I'd never thought to have problems with: customization!!!
Yep. I can't change a theme without things look ugly as hell (I was trying to set mac-osx icons, mac-osx controls and mac-osx windows from [Ultimate OSX Theme]("http://ubuntuforums.org/showthread.php?t=200892&page=6"))
Hope to fix this soon - if I only understand why is this happening!

---

### Post by tomdkat on 2006-11-03
I upgraded a couple of days ago and X wouldn't start (due to the fglrx module not being found).  That was the biggest obstacle I hit. I'm getting an [error message](http://ubuntuforums.org/showthread.php?t=291388) when I login to X but it doesn't affect anything.

Peace...

---

### Post by RealGene on 2006-11-03
I've spent 8 hours trying a CLEAN install.
This is one of my basement servers, and it has a small VGA-only monitor attached, that only supports 60Hz refresh.  The Live CD, unfortunately, tries to use a higher refresh rate (despite my specifying vsync=60 on the option line), resulting in overscan, so that the system is unusable.  I downloaded Dapper 6.06.1, and found no such problem.
Apparently, someone decided that splash screens have to be high-res and ergonomically refreshed.

So, the answer is no...

--Gene

---

### Post by zek725 on 2006-11-03
> **RealGene said:**
> Apparently, someone decided that splash screens have to be high-res and ergonomically refreshed.


yeah! it should have been at low-res and adapter-default refresh rate. 640x480, 800x600, @ 60Hz.

---

### Post by xodus1 on 2006-11-03
i had only one small problem with the upgrade via update manager, that was with booting with the generic kernel, which was fixed easily with a post about it in this forum,

no loss of setting (exclude Grub & Login Settings), Nvidia drivers worked fine and all the codecs aswell (1 hour give or take to upgrade and i was back in the mix with the default kernel)

---

### Post by setdosa on 2006-11-04
Yes. I have a dell 700m and everything is working perfectly as of now.

---

### Post by Quirky on 2006-11-04
I upgraded to the Eft yesterday and it has been the upgrade that has given me least problems. I've upgraded Hoary->Breezy->Dapper->Edgy over the last 18 months on the same machine (clean installs are a cop out! :)).

Hoary to Breezy was not too bad, but Breezy was pretty rough around the edges to start off with (wifi problems, X freezes). Breezy to Dapper had the upgrade applet crash near the end and a warning about my system being unusable - turned out to be minor, but it was scary at the time and required a bit of cleaning up after reboot.

I upgraded to Edgy using an image of the alternate CD mounted via the loop device. Downloading the lot from the repositories would have taken days (the speed varied from 70kb/s to 14kb/s, often stalling) but the CD downloaded in a few hours using the torrent. 

During the actual upgrade I only had a couple of really minor problems - the http downloader seemed to stall towards the end with just 2 minutes of download left, so I killed the upgrade tool (after waiting ~1 hour with no progress, perhaps being patient would have resulted in it restarting but it looked pretty stuck). Restarting the program, it reconnected and downloaded the remaining 20 or so packages. A relief as I didn't fancy downloading the extra universe stuff again. The upgrade had just one incident - the Debian program that checks for upgraded scripts went wonky when installing new autofs configuration files. The "wizard" shows differences in a console, but if you aren't viewing the console it looks like the program has frozen.

After upgrade, the boot/shutdown splash screen wasn't shown. Adding "vga=791" to grub's menu.lst fixed this, but the resolution was wrong. Editting /etc/usplash.conf to the right resolution (1024x768 ) and rerunning update-initramfs sorted it out.

All in all I was pleasantly surprised - after expecting things to go horribly wrong the upgrade was 99% painless. It's worth noting that I had no 3rd party debs installed, used the open source Xorg drivers and had only official repositories in apt's sources.list. It seems that most of the problems reported are by users of binary blob drivers and those that have all sorts of extra repositories and unofficial debs on their system.

---

### Post by sadalmelik57 on 2006-11-04
The Edgy upgrade killed my Ubuntu.  I think the original problems were due to ATI Radeon video card, but now it is so hopeless I am ready to re-format my hard drive and re-install Dapper.  I hate to lose the data I have saved, programs installed, upgrades completed.  Maybe a fresh copy of Dapper followed by an immediate upgrade to Edgy might work for me.

---

### Post by mikeymikec on 2006-11-04
It worked for me fine on the third attempt, using the officially-suggested method that came out a little while after my first two attempts.

---

### Post by psycho78 on 2006-11-04
i upgraded 3 machines now and I had to reinstall gnome-desktop on 2 of them. But all in all it went without problems... had to reconfigure vmware because of the modules and different kernel versions but this is not a problem of ubuntu ....  that's just "normal" :) All in all i love edgy. But I have to say that the 4th machine that I installed completely new with the 6.10 cd works more smoothly somehow....

---

### Post by notnuforlong on 2006-11-04
I loose my monitor after the boot screen. It just goes completely black. Don't  know what I'm going to do so I posted about it. Maybe somebody can help.

---

### Post by JohanL on 2006-11-04
Worked well for me. In spite of the fact that a fuse in our apartment blew (or whatever it is fuses do, my english doesnt go this far)in the middle of the upgrade; the power went down and the computer died. I said a number of really foul words, apologized to my wife, fixed the fuse, restarted the computer which promptly continued where it had been interupted, spouting a number of locale errors messages which didnt seem to matter, and finished the upgrade. Works like a charm. Still amazes me...

---

### Post by jerrylamos on 2006-11-04
Edgy runs fine on my IBM Thinkpad 2656 laptop.  X cannot initialize on my IBM NetVista 8303-SB2, 2Ghz Pentium, Intel 82845G graphics controller Sony 15sf monitor.  Depending on what I enter on CDLive sudo dpkg-reconfigure xserver-xorg there are different errors reported such as "screen(s) found but none have a usable configuration".  BTW, I'm sending this message using Windows XP Professional on that same configuration.  I'm still looking thru forums for ideas.

---

### Post by rthompson0926 on 2006-11-04
Edgy appears to be running fine on my Dell Dimension XPS T600r (256 MB, NVIDIA RIVA TNT2 Model 64 video card). I didn't upgrade though - I did a fresh install today from the alternate install CD and it has worked perfectly so far.

---

### Post by kahping on 2006-11-05
Upgrade from Dapper to Edgy went perfectly using the official method. 

Only "problem" was my own fault for forgetting to change xorg.conf to use ati driver for my video card instead of the fglrx module that was removed during the upgrade

---

### Post by zugu on 2006-11-06
As you can all see, only 24.3% of the voters had a clean upgrade. Do the math and you have ~75.7% frustrated users.

I hope someone at Canonical sees this thread.

---

### Post by patty522 on 2006-11-06
The install was perfect, even better than upgrading from 5.10 to dapper. the only problem was i didnt change all of the source code from dapper to edgy. but once it complained i was able to change it. once that was done i was inpressed how much better it ran than dapper.

---

### Post by Freddy on 2006-11-06
When I first joined the Ubuntu family by installing it's cousin Kubuntu back when it was first released, a weird bug appeared due to a dependency problems which was never solved but easily fixed with some help from the friendly community here at ubuntu forums. I too remeber that the newly installed Kubuntu first upgrade screwed up the panel. No worries I said to myself this is the first realese of this awesome Kubuntu distro and used it until the second realese went gold.

When upgrading my system to the new version, I knew I was right. The problems with the first Kubuntu was gone and everything went smoothly and it kept on working smoothly until the day that Canonical decided to change things. They realesed something that should still be in beta for quite some time. I tried to make a dist upgrade the way they wanted me to do and what happend? I can only say badly and I had to make a clean install...okey no worries, **** happens.

I installed this realese, updated everything and went into apt-get to install my k7 kernel. Ohh what now everythings changed here to okey no worries I will try to install nvidia-glx and it will take all the stuff I need for my GF 6800GT, but whopps it wants to install a i386 compiled kernel, I don't want that. So I installed the meta package for the restricted modules for my generic kernel myself, ahh everythings smoothly again. I installed nvidia-glx, yay it's alright, it doesn't want to install a i386 kernel anymore, nice. Now I just need to enable it :), ehh btw not that nice.> error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.  Well I just need to go to my friends over at ubuntu forums and ask the question, they will help me and everythings will be just fine, ehh wait since the merge of of the sections, threads comes so so fast that just 20 minutes after you asked your question, your thread are down to page 2 where nobody seems to look :-(.

Ahh now I feel much better I needed to vent myself some and Dapper, here I come, sorry for the times I yelled at you, everything is forgiven.

PS: If Canonical is honest when they say that their target is making windows users to convert they really need to fix things before they release a new version, for me this is not a problem I will only change distro if this kind of stuff keeps happening but for a new linux users this kind of thing could be a deal breaker, just look at the number of the people having serious problem with a simple upgrade. 

Ohh well, sorry for my rant but I really love this distro and the community that surrounds it, at least I did before. Now a days when I'm having some problems I mostly relay on linuxquestions.org, here I need to bump the question for a few days before I might get a answer :-(.   /// Freddan

---

### Post by Quirky on 2006-11-06
> **notnuforlong said:**
> I loose my monitor after the boot screen. It just goes completely black. Don't  know what I'm going to do so I posted about it. Maybe somebody can help.

This is what happened to my upgrade too. You probably need to add "vga=791" to your /boot/grub/menu.lst file, then run update-grub.

Next time you reboot type "e" on the grub OS selection screen and add vga=791 and see if it works out for you. If it does you can make it permanent. Look for this section in menu.lst:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=791

```

---

### Post by GettinBetter on 2006-11-06
yes, without any problem :D

---

### Post by Footer on 2006-11-06
You are definitely in the minority ... Consider yourself lucky ... or very fortunate!!!

:)

---

### Post by tommcd on 2006-11-07
As a way of keeping things in perspective, just remember that upgrading from windows98 or windows ME/2K to windows-XP did not always go very well for a lot of people either. For that matter, installing service packs or even updates for windows-XP has been known to cause problems.
Plus, with Microsoft, you never know when they are going to sneek in some crap like the "windows genuine advantage" tool that phones home to microsoft on a regular basis (and somehow bypasses software firewalls) to report who knows what!

---

### Post by mc2k4 on 2006-11-08
Well as i far as i know my upgrade went OK.

I used the update manager using gksu "update-manager -c"

It downloaded the 500+MB in 20 minutes and installed the files in another 20 minutes. 2 minutes after spending 40 minutes on installation i was using 6.10. :mrgreen:  

Only at installation it said it will remove 78 packages or so and i said ok and so i no longer had VLC and Firestarter on Edgy but thats about it. Is this a success? As far as i can see it was fine. Oh and my Java programs started working correctly so thats another plus.:-D

---

### Post by newmo on 2006-11-08
It seemed to be ok but I only had it for ten minutes - it was a dist-upgrade that took six plus hours to download.  Looked at it and it looked good - something went weird and it got grubbed out of existence.  Since that install no cdrom reinstall of Dapper has worked either.  A complete linux-killer after six months of using it.  It wasn't the only problem I had with Ubuntu/Mepis/GNU-Linux over that time of course but it was the worst.

---

### Post by lucnoc on 2006-11-08
- IBM T41p clean install from live cd worked fine; no problems so far; did not try to use ATI drivers yet.

- AMD desktop with ATI won't boot the live cd... tried the non live cd and after the install it won't boot either...

---

### Post by Monkus on 2006-11-10
It took me a couple of tries to get the wireless working on my laptop, but I got it and everything has been great ever since.

---

### Post by ExMachina on 2006-11-11
Dapper was great wifi , lan everything..
updated and my wifi died on my vaio << it shows the card but can seem to ever find any networks <<

---

### Post by MrMacHead on 2006-11-13
Hibernation is broken. Worked fine in 6.06.

First install was from the 6.10 CD. I ended up with limited screen resolutions and refresh rates. However, after I experimentally installed 6.06 first, then upgraded to 6.10, all is "normal" regarding screen resolutions and refresh rates.

---

### Post by ulph on 2006-11-14
i had to do apt-get (-f) dist-update and apt-get (-f) install a lot of times to get all packages and their dependecies installed. then, i had to delete ~/.asoundrc to get back alsa.

what i didn't solve yet, blender doesn't work anymore with 16 bit colour depth - i really need that, because my very old ati rage hardware only is well acceleratded at 16 bit.

---

### Post by bradh on 2006-11-20
I had a few problems with the X server, which almost caused me to find another distribution; however, the advice on the Ubuntu forums allowed me (after some struggles) to complete the install successfully.  

No problems since, and the WPA wireless support for my fairly new laptop is much more successful/stable than Dapper (a big reason for me to attempt the upgrade in the first place).

---

### Post by bjourne on 2006-11-28
I used the 'gksu "update-manager -c"' and things went pretty smooth. The upgrade process failed twice, first because /usr/X11R6/bin wasn't empty and then a second time because some python-* module couldn't be upgraded. The second problem was solved by simply removing the offending python module.

Post-install, I've had no problems whatsoever so far. But on the other hand the differences between Dapper and Edgy aren't earth-shattering.

---

### Post by civilian on 2006-11-28
#1 I didnt have any problems, nothing at all, everything that worked before did now, the only problem I have with Edgy is that easyubuntu does not work for it yet.

---

### Post by xjlx on 2006-11-28
I had not booted in to Ubuntu for quite sometime, have to blame myself for that, so I upgraded to dapper, and then to edgy, dapper had a few problems with nessus, edgy went fine though.

---

### Post by frankophile on 2006-11-28
> **bjourne said:**
> I used the 'gksu "update-manager -c"' and things went pretty smooth. The upgrade process failed twice, first because /usr/X11R6/bin wasn't empty and then a second time because some python-* module couldn't be upgraded. 

I had this same problem only when I tried to empty said directory, I got an access denied error.  I was in su mode.  I don't know what to do now.  Can somebody help a rank newbie?

---

### Post by dtfinch on 2006-11-28
My upgrade went pretty well. It was a bit tricky getting it to upgrade without wanting to remove or hold back dozens of vital packages (as is normal with all ubuntu upgrades :) ), but once I got it to not want to trash it all, the upgrade went pretty smooth.

Afterwards, there were some problems, but nothing serious:
I had to set an environment variable to get Firefox w/Flash to not crash.
Firefox occasionally freezes, unresponsive but idle. It's not Ubuntu's Firefox build though.
Nautilus often consumes 100% cpu when I browse to a folder with files that are being actively updated. It's still responsive, but consumes 100% cpu until I do a "killall nautilus".
Gnome-btdownload's min/max port settings were set to a bad default that prevented multiple downloads.
3d acceleration was disabled until I removed 1600x1200 from my xorg.conf, even though I was only using 1280x1024.
I lost my usplash. The screen is black until it reaches the GDM login screen. And the screen is black while it shuts down.

---

### Post by vnevoa on 2006-11-30
For the first time, it went almost perfectly!!!
My previous dist-upgrade (to dapper) was a disaster and I ended up reinstalling from scratch, this time I was surprised to see everything finish without (much of) a hitch! :)  Nice work, ubuntu!!!

The only things I noticed were:

1 - a few packages were held back and would not upgrade no matter what I did. I found [this]("http://www.ubuntuforums.org/showthread.php?t=286464") thread and everything solved quickly. Consult the Debian "dist-upgrade howto" link over there.

2 - The system froze completely and hopelessly on random occasions, when I was using rythmbox music player... really weird. But this I can't decide if it was SW or HW related, because I had just upgraded the mobo, while keeping the same HDDs and CPU and DDR.. After a while it stopped happening, and I don't know if it was my 17th try at reseating the CPU cooler with just the right amount of thermal paste (those Athlon XP bridges don't like it very much!) that solved the problem, or a subsequent apt-get upgrade that replaced some quirky library... anyways, it's all gone and pumping happily now.
:)

---

### Post by Kalif on 2006-11-30
I have done upgrade on 3 systems, the first a few weeks before the actual release: apt-get... ; everything went fine.
The only issue was LTSP that had gone through a major revision (which I had anticipated and been waiting for); it needed some tweaking before that worked.
The second system was upgraded a few days after the actual release:
apt-get... ; also fine and dandy :-)
The third system I installed yesterday, plonked in a dapper CD in a  fresh system, installed and then aptitude to upgrade. All went smoth except that X did not work after the install. Then I clicked the orange update button in the notification area on the first system and after ugrading a few packages I was recomended to reboot my system and was greeted with a non working X11.
I think I will wait a few days before clicking any orange buttons again 8-)

/k

---

### Post by Ares139 on 2006-11-30
I didn't realize it at first, but I have had several bugs pop up after upgrading to Edgy.  I had a few known bugs like the File Roller 7-zip bug and the missing swap bug.  I managed to partially correct the swap bug, but I can no longer hibernate or standby.  Standby didn't work in Dapper either, but Hibernate did at least.  If I hibernate, it overwrites my swap and doesn't restore my session on the next boot.  I then have to go through the steps of fixing my swap.  Also, many settings aren't "sticking" - like ANY of the settings in Power Management, or the Remote Desktop settings.  The Power Management settings don't work, period.  The Remote Desktop password will stick for that session, but if I reboot and log in, I'll have to reset the password before I can remote in again.

I'm planning on backing up my home directory and starting from scratch, soon.

---

### Post by YoungCthulhu on 2006-12-02
[FONT="Garamond"][/FONT]
This is my third attempt to install Edgy and I have just got on to the internet using judgekaster's excellent thread "RaLink RT61 Wireless Solved (Updated)".
After upgrading from Dapper I found my D-Link DL-510 no longer worked.  It had previously worked out of the box under edgy.  I downloaded the drivers from [www.ralinktech.com](www.ralinktech.com) as instructed and followed judgekaster's directions, augmented by the "readme" file that comes when you extract the driver files.
A lot of work but being an absolute beginner I learned something and got a good start in Linux command line usage. :D 
Now I just have to sort out my sound card, hopefully using LoardRaiden's thread "Comprehensive Sound Problems Solutions Guide v0.5e"  :-k 
Cheers all!

---

### Post by Josh Kurtz on 2006-12-06
I had to run apt-get install kubuntu-desktop ubuntu-desktop and apt-get dist-upgrade a few times before all my packages were up to date.  Something was wrong with my xorg.conf file that made me have no video but it was just a one line fix in vi and I was done (can't remember which line though).  Also, I can't play mp3's in Amarok](*,)  which is a bummer.

Other than that everything is good.

---

### Post by kleeman on 2006-12-08
Update. I have gone wild (Ubuntu users gone wild- get the video!!!) and installed/upgraded Edgy on four boxes, all without issue:

1) Dual Xeon emt64 box with AMD64 bit version. 7950 GX2 graphics card
2) New 3.4GHz P4 i386 box with new nvidia graphics card
3) Old 2.8GHz P4 box with old Audigy and old nvidia card. This box is on the internet with port 22 open for ssh so a firewall install was needed and tcp-wrapper. All straightforward.
4) Pentium Centrino 2.0GHz laptop with intel graphics and madwifi wireless.

The only real problem I had was that the laptop overheated during a Dapper upgrade to Edgy and shutdown in the middle which locked me out of the box. A fresh install from the livecd was however uncomplicated. Networkmanager is more reliable on the laptop with edgy than dapper which is a pleasant bonus.

Much kudos to the developers

---

### Post by Azriphale on 2006-12-12
All of my hardware (except my ATI x700) works natively with Linux (well, bluetooth needs a little fiddling, first tested in Edgy), even wireless (intel card, great open source drivers). The only issue is there is occaisionally a garbled X session (random colours displayed, or no display at all) on startup, which is fixed with a simple ctrl+alt+backspace. I had to turn off "splash" in the /boot/grub/menu.lst so that I am able to access the virtual consoles (ctrl+alt+Fx). Otherwise it seems to be ok.

Need to use the fglrx drivers to get any X video at all, but that was no surprise, its been like that from the start with this machine. The open ATI drivers do not have good support for some of the newer ATI chips. Just need to use the vesa driver in the livecd install.

This is a Toshiba Satellite Pro M70-235, for those that are interested. One of the models with a Phoenix BIOS. Everything is now working, for the first time in Ubuntu (only tried Dapper and Edgy on this machine, and i didn't bother with bluetooth before-- the only thing not working in dapper)
Pentium-M 1.86
1GB RAM
ATI x700
Intel WiFi
Toshiba Bluetooth

---

### Post by golem3 on 2006-12-13
> **coastdweller said:**
> The upgrade caused an unstable system that forced me to reinstall.

SO are people having trouble only with an upgrade or with fresh installs as well?

---

### Post by EdThaSlayer on 2007-01-06
My nice(or used to be nice) ATI Radeon 9600(with 128mb of vram) is pretty useless now. I mean, 250 fps is the max it can give?It used to be above 2000 before I upgraded to Edgy Eft!

---

### Post by dolphinsonar on 2007-01-15
Still cant get my Epson CX5400 Printer Scanner to scan, printing works.  Both were fine in Dapper.

---

### Post by adam_pretty on 2007-01-31
Only just upgraded ...  the "official" method failed before it finished installing eveything... I attempted to finish it by running "aptitude update" and "aptitude dist-upgrade" .. then restarted, and seems to be fine!

---

### Post by housam on 2007-01-31
Although I've read many threads about System crashes after Edgy upgrading, I did it but through a fresh install. All went fine and it works like a charm on my laptop.

---

### Post by twygly on 2007-04-23
> **adam_pretty said:**
> Only just upgraded ...  the "official" method failed before it finished installing eveything... I attempted to finish it by running "aptitude update" and "aptitude dist-upgrade" .. then restarted, and seems to be fine!

You're lucky - I'm still trying to figure out what to do after my failure. update and dist-upgrade both didn't do anything.

Trying to find a solution without having to clean install but so far nothing...

---

