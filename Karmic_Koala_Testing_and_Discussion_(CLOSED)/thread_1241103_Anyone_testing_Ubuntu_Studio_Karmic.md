---
title: "Anyone testing Ubuntu Studio Karmic?"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by trulan on 2009-08-15
Just curious.  There are two new real time kernels now available in Karmic - one based on 2.6.29 (latest stable), and one based on 2.6.31. 

Problems:  Other than having to do some wrangling to get Karmic to stop fighting with the NVidia drivers (It now says the drivers load properly on bootup and also says they are not installed once booted up, not exactly sure how I got there), I have seen no real problems.  Oh, and I've been fighting with GRUB2 but that's another story.

Improvements:  The firewire setup is much improved, permissions are much easier to set now.  Although adding myself to the 'video' group was a bit harder.  The desktop is slightly rearranged and already I like it better that anyting else I have ever used.  Also the login screen is very nice, a little less typing.

I'd like to hear anyone else's experiences with this.  (maybe this thread should be in the Karmic discussion forum but no one there has been talking about real time, so I posted here.)

---

### Post by falkTX on 2009-08-15
I don't specificelly use UbuntuStudio (my desktop is a mix between Gnome-KDE); but in my little HP notebook, with Intel graphics (KMS...), karmic just rocks!

The kernel 2.6.29 is working fine for me, haven't tested the .31 yet

And I heard UbuntuStudio 9.10 will have "LIVES" for video app - which sounds very cool to me

---

### Post by fedexnman on 2009-08-15
does ardour still crash on export using a firewire device ??

---

### Post by falkTX on 2009-08-15
> **fedexnman said:**
> does ardour still crash on export using a firewire device ??

I don't have a FW device, but I know that a new version is out - 2.8.2 (at least GetDeb.net has it).

2.8.3 should be out soon too, as they say on the ardour website

---

### Post by trulan on 2009-08-15
Ardour still is a little goofy when exporting (Presonus Firepod here).  It exports successfully, but cannot re-connect with Jack properly afterwards.  Jack then dies.  Ardour is still somewhat functional after this, but you can't re-connect to Jack without closing and re-starting Ardour.  So it's not perfect but it's a little better than in Jaunty.  If you remember to save your session before exporting, it's not much trouble.

I haven't seen LIVES yet but I'll look for it.

---

### Post by bluesscream on 2009-08-16
Today I sat on my terrace not motivated to move by temperatures >30&#8242;C and installed daily build 20090816 ubuntustudio 9.10 amd64 manually into two free partitions. I used all defaults - ext4 for both /filesytem and /home, flawless install ~ 1/2 hour on my nexoc notebook with an intel core duo T5750@2GHz CPU. Here I am:

Wlan could not be configurated out of the box,  I did not find a network-manager in the DVD-repo.So I had to connect wired and install a network-manager, in my case preferred wicd, which is in the repos in a little obsolete but stable working version.

jackd 0.116.1 runs fine on alsa with internal Intel HDA Chip, settings 44,1 kHz, 64 frames, 2 periods-->2,9 msec 
ardour opens and connects: DSP 12,4%, 1,5 ms,
hydrogen demo-set and extern microfone recorded in ardour without xruns.

Panel-applet CPU Frequency Monitor Preference works fine, recommends password once a session.

edirol fa101 control-leds indicate connection but ffado mixer doesn't find the device,
No progress with gksu ubuntustudio-controls.
manage groups with users-admin-gui failed, seems to be a bug, it doesn't show existing groups except root and username.

Had to edit /lib/udev/rules.d/50-udev-default.rules, looked for the line with raw1394  (was at the end of the file) and changed the "GROUP" entry from "video" to "audio".
Changed group of /dev/raw1394 from "video" to "audio" too.

Now ffado-mixer  let me register the edirol fa101 on ffado site and opened the slider-gui.
jackd connects to firewire, but for me it has higher dsp-use and needs higher latencies then a configuration with jack v.1.9.3. ffado support seems to be better performant with jack v.1.9.3, for alsa with onboard audio-chip performance of jack seems to be better in version 0.116.1.
So my first impression is: Awesome realtime-kernel 2.6.31-1-rt in a stable running environment but  at least for firewire poor/obsolete jackd0.116.1.

---

### Post by Stochastic on 2009-08-17
> **falkTX said:**
> I don't have a FW device, but I know that a new version is out - 2.8.2 (at least GetDeb.net has it).

2.8.3 should be out soon too, as they say on the ardour website

No need to run to GetDeb.net for your 2.8.2 package, it's in Karmic's official repositories.


LiVES does not look to be in REVU yet, so it's unlikely that it will make it into the repositories before the feature freeze (August 27).  There was some talk on the mailing list about it being one that should get packaged soon though.


As for Karmic in general, look for 2.6.31-RT to be very stable as it is a release patch from the upstream RT guys rather than a snapshot of their development work (as some of the other RT kernels have been).

I've yet to get much testing in on 2.6.31-RT because it's not happy with my graphics card (ATI Radeon XPRESS 200M).  But overall Karmic looks good.

---

### Post by trulan on 2009-08-19
What I though were new features on the desktop are standard gnome, I have learned.  Just shows how much of a newbie I am.

I couldn't find the users and groups gui in the menu.  There is a gui that allows you to set permissions for specific tasks though (maybe this is a replacement).  I checked the box to allow me to use video stuff, and viola, I was a member of the 'video' group.  (I'll have to boot into Karmic to get the specifics as to where it is and what it is called.)

Edit: Okay, it is in users and groups. It's just set up differently.  Here's how to make yourself a member of the video group:

1. Open the 'Users and Groups' gui and unlock it.
2. Click on your username.
3. Click 'properties'.
4. Click the 'User Privileges' tab.
5. Check the boxes to allow certain tasks.  I think 'Capture video from TV or webcams...' is the line you need.  'Use audio devices' seems like it should be enabled as well.
6. Click 'OK'.  You are now a member of the 'video' group.

---

### Post by eric71 on 2009-08-29
I've just installed karmic alpha 4, installed the rt kernel, jack, qjackctl, added myself to the audio group and edited limits.conf.

Usually when setting up Ubuntu for recording, I start by removing pulseaudio as well. This worked fine, and jack started from Qjackctl as normal. I then noticed I had no volume control applet in my panel anymore. Some trial and error showed that new applet uses pulse, and so does the "sound" configuration in System-Preferences-Sound.

So I re-installed pulseaudio, only to find that jack will no loner start in RT (it does without RT checked in Qjackctl). 

It seems that I either need to remove pulse again and find an alternative gnome volume control (the one listed when adding new applets is depreciated, and nothing gets added to the panel) orI need to get jack and pulse to work right together.

Any hints from those of you trying out karmic would be much appreciated. Maybe I removed something along with pulse that is needed for it to cooperate with jack, and haven't added it back?

---

### Post by Stochastic on 2009-08-29
Moved to Karmic Koala Testing & Discussion.

---

### Post by eric71 on 2009-08-29
I've done a bit of research on my original problem. Pulseaudio (at this time anyway) does not seem to include module-pulse-jack which is necessary for jack and pulse to work together. So until/if this gets fixed there will be no pulse and jack at the same time.

Since I installed from the regular ubuntu cd (not ubuntustudio), I'm not sure what it provides for basic volume control (i.e. system tray volume applet). I can install and use something like Gnome Alsa Mixer, but that doesn't provide an applet. Can someone using Ubuntustudio karmic let me know how this is handled?

---

### Post by trulan on 2009-08-29
Karmic Studio does indeed use Pulse for the volume control applet.  I'm not sure how it is handled but Jack works just fine here.

I've tried to get a list of all installed Pulse Audio packages.
```
dpkg -l |grep pulse
```yields:
```
ii  gstreamer0.10-pulseaudio              0.10.15-2ubuntu1                           GStreamer plugin for PulseAudio
ii  libcanberra-pulse                     0.15-0ubuntu3                              a simple abstract interface for playing event sounds
ii  libpulse-browse0                      1:0.9.16~test6-3-g57e1-0ubuntu2            PulseAudio client libraries (zeroconf support)
ii  libpulse-mainloop-glib0               1:0.9.16~test6-3-g57e1-0ubuntu2            PulseAudio client libraries (glib support)
ii  libpulse0                             1:0.9.16~test6-3-g57e1-0ubuntu2            PulseAudio client libraries
ii  pulseaudio                            1:0.9.16~test6-3-g57e1-0ubuntu2            PulseAudio sound server
ii  pulseaudio-esound-compat              1:0.9.16~test6-3-g57e1-0ubuntu2            PulseAudio ESD compatibility layer
ii  pulseaudio-module-bluetooth           1:0.9.16~test6-3-g57e1-0ubuntu2            Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-gconf               1:0.9.16~test6-3-g57e1-0ubuntu2            GConf module for PulseAudio sound server
ii  pulseaudio-module-udev                1:0.9.16~test6-3-g57e1-0ubuntu2            udev device detection module for PulseAudio sound server
ii  pulseaudio-module-x11                 1:0.9.16~test6-3-g57e1-0ubuntu2            X11 module for PulseAudio sound server
ii  pulseaudio-module-zeroconf            1:0.9.16~test6-3-g57e1-0ubuntu2            Zeroconf module for PulseAudio sound server
ii  pulseaudio-utils                      1:0.9.16~test6-3-g57e1-0ubuntu2            Command line tools for the PulseAudio sound server

```I've also attached a screenshot of synaptic listing all installed Pulse packages.

---

### Post by ram130 on 2009-08-29
I have no problems with Jack and Pulse. Just that i cant have both runing, also the volume control worked once but had glitches and havent worked after.

---

### Post by trulan on 2009-08-29
ram130 - Yeah the volume control has been in and out.  Pulse Audio gets at least one update a day lately, so every day is a new adventure!  But I guess qjackctl kills pulse temporarily or something, because it has never conflicted for me.

---

### Post by eric71 on 2009-08-30
I've reinstalled and not removed anything from pulse. I still can't get jackd to start in RT, so I suspect there must be something new in limits.conf regarding pulse. COuld someone using the actual ubuntustudio install post the contents of limits.conf? I read somewhere that the changes come with the ubuntustudio-audio metapackage, but that is quite a bit to download on my slow connection.  Thanks.

---

### Post by trulan on 2009-08-30
```
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4







@audio          -       rtprio          99

@audio - memlock 995740

# End of file
```Obviously your memlock will depend on you system's memory.  But there's mine.  Those last two lines were put there by Ubuntu Studio controls.

---

### Post by eric71 on 2009-08-31
Thanks. That's similar to mine, so there must be some other trick to it that Ubuntustudio has right and I have wrong trying to get it working on Ubuntu alpha 4. Taking a break for a bit with this to test out Debian Squeeze with the RT kernel from AVLinux. I'll be back for the beta release, I think. I'll be following the forum here regarding Ubuntustudio, pulse, jack, etc. progress toward the karmic release.

---

### Post by ram130 on 2009-08-31
Lets just hope the dev figure something out. Would really like to see Ubuntu Studio put up some competition against the other OS  in Music Production. All these years and they finally have  a good Desktop system, just needs to be more user friendly towards installing software and it will be good. To me i can say Ubuntu Studio really came along way,its just the dev to step up there game and put out a full staff for it so the next release can  be really competitive item. For the problem, i have not gotten any further, so i too will take a break from this until the official version is out.

---

### Post by barisurum on 2009-09-09
I have installed the ubuntu karmic 9.10 (generic kernel) alpha 5 and installed the rt patched kernel on top of it. The generic version works fine but the rt didn't boot at all (2.6.31-4). When I switched to generic after that during the boot I had a file system check fail message so I had to run fsck manually as linux suggested and the problem was solved pfeuww! So I won't touch the rt stack any more until it gets updated.

But surprising thing is jack with generic kernel works at 192khz 10.7 ms latency (better than the 9.04 generic kernel). Maybe its a result of the latest alsa updates dunno but before (9.04) my esi juli@ didn't even work at 192khz.

Specs:

AMD ATHLON X2 64
esi juli@ sound card
Radeon X1950XT using OSS drivers (of course!)

---

### Post by trulan on 2009-09-09
Some of the RT patches have made their way into the generic kernel, so that may explain your performance increase.

Also, regarding the RT kernels, I have yet to successfully boot on either 2.6.31-4-rt or 2.6.31.3-rt.  The generic kernels work fine for me, and 2.6.31-2-rt and earlier work great as well.  I'm on a single core AMD64.

---

### Post by barisurum on 2009-09-10
My flash sound is problematic is there anyone with the same problem?

I have no sound with flash and I can't open alsamixer, gnome-alsamixer to see if PCM volume level is 0 or not. Alsamixer says:
alsamixer: function snd_ctl_open failed for default: No such file or directory

Flash videos play but I can't change the volume. In pulseaudio volume control I can't see the flash video's stream in playback section as if it doeasn't exist at all. Other sounds fill my ears with joy.

---

### Post by trulan on 2009-09-10
There is indeed a bug in the current RT kernel, affecting at least x86 systems:
[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/423152](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/423152)

Until this gets fixed, us 64 bit folks are stuck with 2.6.31-2-rt.

---

### Post by ram130 on 2009-09-10
That's why i decide to wait on the official. Its not a big deal really.

---

### Post by barisurum on 2009-09-11
After the latest horde of updates including a pulse update sound in flash videos work. Pulseaudio version is 0.9.16-0ubuntu1. Only the rt kernel remains covered with black clouds.

Edit: Flash sound doesn't work anymore. Dunno why!

---

### Post by falkTX on 2009-09-11
Also , LiVES 1.0.0 is the repos.

Version 1.0.1 is out, but not sure if is going to be updated.
You can always use GetDeb for this - [http://www.getdeb.net/app/LiVES](http://www.getdeb.net/app/LiVES)

---

### Post by trulan on 2009-09-11
When I try to run LiVES (from the repos), it fails for me with this message:
```
Inconsistency detected by ld.so: dl-tls.c: 79: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx + 1' failed!
```On another note, I was surprised at the performance I am able to get from 2.6.31-10-generic with my firepod.  I can't wait to see how the release version of the real time kernel performs!

---

### Post by ram130 on 2009-09-11
LIVES working perfectly on ma Ubuntu 9.04

Starting...
Succesfully loaded 124 Weed filters
Loading default keymap from /home/digit/.lives-dir/default.keymap...done.
Started jack audio subsystem.

Checking optional dependencies:mplayer...detected...convert...detected...composite...detected...sox...detected
xmms...NOT DETECTED...cdda2wav...detected...jackd...detected...python...detected...dvgrab...detected...xwininfo...detected...

Window manager reports as "compiz"; number of monitors detected: 1
Temp directory is /tmp/livestmp/
Compiled with jack support, good !
Welcome to LiVES version 1.0.1.

---

### Post by barisurum on 2009-09-12
Hmm yessss... very juicy... :) I recently downloaded the 2.6.31-2 rt kernel from launchpad and installed it along with headers. So far so good! The kernel seems to be stable after 2 hours of testing. Latency is very low 2.6 ms and I can use standalone windows VST plugins via wineasio and record from them to ardour without a single problem. Compiz and 3D work along with that solid latency too! No lockups, glitches in sound so far. I think we are very close to a rock solid ubuntu studio experience with 9.10!

The only drawback is that during the first boot of 2.6.31-2 rt I saw a fsck failure again... It said %1.3 of filesystem uncontigous. What does that mean? Something serious?

By the way my system is as follows again:

AMD 64bit X2
4gb ram
ATI X1950XT (R580) working lovely with open source radeon drivers
ESI juli@ 24bit sound card

---

### Post by falkTX on 2009-09-12
I figured out why the RT 2.6.31-4 kernel is not booting: because it's based on 2.6.31-9 (which is a bad "build").

Once the generic kernel gets *.31-11, another RT kernel will be out, based on 11

---

### Post by falkTX on 2009-09-12
> **trulan said:**
> When I try to run LiVES (from the repos), it fails for me with this message:
```
Inconsistency detected by ld.so: dl-tls.c: 79: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx + 1' failed!
```On another note, I was surprised at the performance I am able to get from 2.6.31-10-generic with my firepod.  I can't wait to see how the release version of the real time kernel performs!

LiVES has been updated - [http://www.getdeb.net/app/LiVES](http://www.getdeb.net/app/LiVES)

Changelog:
```
* Fix startup crash when loading frei0r plugins.
* Fix hang/crash in rfx builder rebuild.
* Fix strange error message when cancelling "load device map".
```

Neverthless, it still crashes for me

---

### Post by hanzomon4 on 2009-09-12
> **falkTX said:**
> I figured out why the RT 2.6.31-4 kernel is not booting: because it's based on 2.6.31-9 (which is a bad "build").

Once the generic kernel gets *.31-11, another RT kernel will be out, based on 11

Will the nvidia drivers build? The RT kernel is great but it's given me nothing but problems going all the way back to the dapper days. I just want one that works minus the headache

---

### Post by trulan on 2009-09-12
The nvidia drivers build but they need to be patched first.  It's a one-line change - there's a thread on here and a bug on launchpad about it, both of which have the patch.

I am unable to boot 2.6.31-4-rt on my 32 bit laptop, but was able to install 2.6.31-2-rt successfully.  I eagerly await the next rt kernel!

---

### Post by ram130 on 2009-09-12
> **barisurum said:**
> Hmm yessss... very juicy... :) I recently downloaded the 2.6.31-2 rt kernel from launchpad and installed it along with headers. So far so good! The kernel seems to be stable after 2 hours of testing. Latency is very low 2.6 ms and I can use standalone windows VST plugins via wineasio and record from them to ardour without a single problem. Compiz and 3D work along with that solid latency too! No lockups, glitches in sound so far. I think we are very close to a rock solid ubuntu studio experience with 9.10!

The only drawback is that during the first boot of 2.6.31-2 rt I saw a fsck failure again... It said %1.3 of filesystem uncontigous. What does that mean? Something serious?

By the way my system is as follows again:

AMD 64bit X2
4gb ram
ATI X1950XT (R580) working lovely with open source radeon drivers
ESI juli@ 24bit sound card

Can you tell me how to install the standalone windows vst drivers?? :confused:

---

### Post by barisurum on 2009-09-12
ram130 here is a link to grab wineasio:

[http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187)

the guy explained how to configure it too

to install a standalone VST plugin just double click on its installer as you would do in windows. Run it after running qjackctl. Your jack setup must be stable at this point. If you encounter xruns (cracks in sound) increase the buffers/periods. You will see the output ports of the VST plugin in JACK connections. Plug them to any program you want and have fun.

edit: Hey its you FalkTX! our hero is here with us :) thank you for this 64Studio's stolen 64 bit alienated wineasio deb package man :)

---

### Post by ram130 on 2009-09-12
> **barisurum said:**
> ram130 here is a link to grab wineasio:

[http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187)

the guy explained how to configure it too

to install a standalone VST plugin just double click on its installer as you would do in windows. Run it after running qjackctl. Your jack setup must be stable at this point. If you encounter xruns (cracks in sound) increase the buffers/periods. You will see the output ports of the VST plugin in JACK connections. Plug them to any program you want and have fun.

edit: Hey its you FalkTX! our hero is here with us :) thank you for this 64Studio's stolen 64 bit alienated wineasio deb package man :)

Thank you so much, I'm gonna try it as soon a stable rt is out. Hopefully it will be has easy as doing it in pro tools.

---

### Post by trulan on 2009-09-12
...and I have LiVES running on my i386 laptop - now I just have to figure out how to use it ;)  Still no joy on the AMD64 desktop...

---

### Post by ram130 on 2009-09-12
> **trulan said:**
> ...and I have LiVES running on my i386 laptop - now I just have to figure out how to use it ;)  Still no joy on the AMD64 desktop...

takes  a  little getting use to..they need to improve on the user interface and make the space bar a control for playing. Its good so far tho, just some weird exporting and space problems.

---

### Post by barisurum on 2009-09-13
> Still no joy on the AMD64 desktop...

The stock LiVES from the repos works on my 64bit desktop. Version is: 1.0.0-5

---

### Post by haemphyst on 2009-09-13
I'd *LOVE* to test Karmic.  I can't get it to install to my Compaq Laptop from the alternate Alpha CD.  It SHOULD work, my 9.04 install dropped in FLAWLESSLY.  The links to download from Ubuntu.com are ALL error 404's.  Where are people getting their iso's?

---

### Post by trulan on 2009-09-13
> **haemphyst said:**
> I'd *LOVE* to test Karmic. I can't get it to install to my Compaq Laptop from the alternate Alpha CD. It SHOULD work, my 9.04 install dropped in FLAWLESSLY. The links to download from Ubuntu.com are ALL error 404's. Where are people getting their iso's?
I must say I haven't had much luck installing from a Karmic Studio Alpha DVD.  Alpha 3 installed the base system but no desktop or software...Alpha 5 installed everything but was un-bootable.  My latest excursion was to install Xubuntu Jaunty, upgrade that to Karmic, then install the Studio audio, audio-plugins, video, and graphics packages.  (Performance on my 3 year old laptop is noticeably improved over the Hardy Studio install I have been using - Maybe it's Karmic that's faster, maybe it's Xubuntu.  Whatever it is, I like it.)

Given the current state of the RT kernel I would not recommend installing a Ubuntu Studio alpha ISO, as you will very likely end up with an un-bootable system.  If you want a fresh Karmic install, use a regular Karmic ISO, then install the Studio packages via synaptic or apt-get.  If you need the RT kernel, get the 2.6.31-2-rt debs from launchpad.

---

### Post by hanzomon4 on 2009-09-13
Can you provide a link? It seems like that kernel has been deleted from launchpad

EDIT: Found it [[LINK amd64]]("https://launchpad.net/ubuntu/+source/linux-rt/2.6.31-2.2/+build/1169145")

Oh wow, the patched nvidia drivers fail to build on this one and the one in the repos fails to boot.

---

### Post by barisurum on 2009-09-13
They try to make the kernel compatible with nvidia binary blobs then? Well... Good luck to them :)

---

### Post by ram130 on 2009-09-13
> **hanzomon4 said:**
> Can you provide a link? It seems like that kernel has been deleted from launchpad

EDIT: Found it [[LINK amd64]]("https://launchpad.net/ubuntu/+source/linux-rt/2.6.31-2.2/+build/1169145")

Oh wow, the patched nvidia drivers fail to build on this one and the one in the repos fails to boot.

Here are the Karmic Alpha 5 isos, will update if you need it when 6 comes out.

 [http://cdimage.ubuntu.com/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/releases/karmic/alpha-5/) (Ubuntu)
 [http://uec-images.ubuntu.com/releases/karmic/alpha-5/](http://uec-images.ubuntu.com/releases/karmic/alpha-5/) (Ubuntu Server for UEC and EC2)
 [http://cdimage.ubuntu.com/ports/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/ports/releases/karmic/alpha-5/) (Ubuntu ARM)
 [http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/kubuntu/releases/karmic/alpha-5/) (Kubuntu)
 [http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/xubuntu/releases/karmic/alpha-5/) (Xubuntu)
 [http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/mythbuntu/releases/karmic/alpha-5/) (Mythbuntu)


For Ubuntu Studio I'm not sure what Alpha it is, but i guess its updated daily since Alpha 4

[http://cdimage.ubuntu.com/ubuntustudio/daily/current/](http://cdimage.ubuntu.com/ubuntustudio/daily/current/)

---

### Post by hanzomon4 on 2009-09-13
I fixed it I had to hunt down the linux-rt-headers-2.6.31-3 in addition to the linux-headers-2.6.31-3.3-rt. Crazy if you ask me, it was in the i386 section but the deb was for all arch

---

### Post by barisurum on 2009-09-15
Is the puredata in karmic (0.41.4-1) broken or am I doing something wrong? In every way I try the test sound in media menu I hear cracks in the sine wave and there are IO errors reported (ADDA sync errors). I tried every possible jack frequency in qjackctl and latency setting from 50 to 100 in puredata's sound settings window to no avail. 

While there are cracks in the sound qjackctl reports no xruns and this makes me even more confused. 

Meanwhile reaktor 5 with wine and wineasio works with no xruns or cracks-pops in sound. And this makes me think there is something wrong with the puredata package. Anyone confirms this or is there anything I can do to make it work? Thanks.

PS: I start puredata with -rt startup flag

---

### Post by trulan on 2009-09-16
The world is a better place today!

The new version of the RT kernel is out, and it actually works!!
Welcome to 2.6.31-5-rt.

---and welcome to alpha reality - one successful boot and then the whole thing went down on the next boot - now nothing boots - oh well...now to figure out how to fix it...

---

### Post by falkTX on 2009-09-16
> **trulan said:**
> The world is a better place today!

The new version of the RT kernel is out, and it actually works!!
Welcome to 2.6.31-5-rt.

---and welcome to alpha reality - one successful boot and then the whole thing went down on the next boot - now nothing boots - oh well...now to figure out how to fix it...

I'm currently using the RT kernel, it seems fine.

I haven't rebooted yet though. Better use generic kernel until Karmic is officially released

---

### Post by barisurum on 2009-09-16
trulan: can your problem be related to the latest upgrade mess that stormed the forum? because you said "now nothing boots"? If so there is a cure here:

[http://ubuntuforums.org/showthread.php?t=1267183&page=3](http://ubuntuforums.org/showthread.php?t=1267183&page=3)

if not I won't do that upgrade too...

---

### Post by trulan on 2009-09-16
I'm pretty sure it's update related rather than kernel related.  For some reason nothing would boot - not even the generic kernel - this morning.  Now it boots just fine.  The real time kernel is still hit or miss on the boot-up but I am running it at the moment.  I'm off to see what I can sort out...

---

### Post by hanzomon4 on 2009-09-16
RT 5 won't boot for me... argh!!! Regardless the system timer resolution is still to freakin low for an rt kernel ```
/boot/config-2.6.31-5-rt:# CONFIG_HZ_1000 is not set
/boot/config-2.6.31-5-rt:CONFIG_HZ=250

```

---

### Post by barisurum on 2009-09-16
Just tested the 2.6.31-5-rt kernel, I couldn't defeat my curiosity :))

The kernel boots me to the test partition after some udev errors and various messages that I can't read during the boot and after usplash doesn't come up and then everything seems to be working :) I booted it two times and tested it's realtime scheduling performance a bit and that seems normal too, (perhaps a bit better?). No lockups were detected after one hour of testing. Here is what works:

Video: ATI X1950XT (R580):

2d desktop
3d graphics opengl etc.
compositing (works much faster after the update)
textured video


Audio: Esi juli@ (envy24 HTS)

Audio playback pulse
Jack realtime (perhaps a bit better, need to test more)

Network: problems fixed with latest upgrade, now starts on boot

Mounted devices: problems fixed with latest upgrade, all mounts auto


I suggest people with an open source driver ATI GPU to upgrade to this new kernel. I dunno about nvidia matterz sorry but hope there won't be any problems and you will feel this relief too. :guitar:

---

### Post by trulan on 2009-09-16
> **hanzomon4 said:**
> RT 5 won't boot for me... argh!!!
**Edit: forget this.  NVidia troubles.  See end of post.**
It seems like I need to boot into the generic kernel, then restart, then RT 5 will boot.  Restarting straight back into RT 5 repeatedly fails.  The last few times it has been freezing at xsplash for me (before the login screen).  But sometimes it will boot right up and run great.

For some reason the recovery console is gone no matter which way I boot.  That makes me think that something else is still wrong.

The Ubuntu devs are making some significant changes to the booting process (first xsplash, now upstart and mountall) which is why things have been in such a mess the last few days.  And I expect that the fixes for properly booting the RT kernels will be coming along shortly, after they get done cleaning up after themselves for the generic kernel.

All in the name of progress.

Edit: The udev errors on boot are no big deal.  There's a bug referencing them - something to do with a package being tested that will hit upstream next week, then they'll be gone.

Another edit:  I had said the NVidia drivers work?  Well, I did the good old 'sudo gedit /etc/X11/xorg.conf', 'change driver to vesa' routine and my RT boot problems disappeared.  (None of the RT kernels had been booting anymore) So it's back to fighting with those for me.  (This has been an off-and-on issue for me, even in Jaunty, so I'm quite used to it.  Maybe I should learn how to actually fix it.)

---

### Post by trulan on 2009-09-17
Something in the latest round of updates seems to have broken raw1394 access by the 'video' group.  When I run
```
ls -l /dev/raw1394
```
as directed by qjackctl's messages, I get
```
crw-rw---- 1 root root 171, 0 2009-9-17 07:12 /dev/raw1394
```
whereas before (with permissions properly set) it would say 'root video' instead of 'root root'.

I wonder if the problem is related to the udev error messages (that I have been telling people not to worry about:).)  raw1394 permissions are set in /lib/udev/rules.d/50-udev-default.rules.  It now reads "dv1394/%n" and "video1394/%n".  Those '/%n' things look an awful lot like some of the udev error messages.

But, KERNEL=="raw1394", GROUP="video" is still where it belongs.  So I'm not sure exactly what is wrong, but I know I'm not supposed to have to run all my audio software as root.

---

### Post by ram130 on 2009-09-17
Glad to see everything  getting better. Will test this RT when beta version of Ubuntu studio is is out.

---

### Post by trulan on 2009-09-17
Hmm...  I had to boot one time with my firepod turned on and plugged in, then the raw1394 permissions righted themselves, now they 'stick' - they stay the way they belong even if I reboot without plugging th firepod in.

And alas, the nvidia 185 drivers cause the RT kernel to hard-freeze as soon as it attempts to load xsplash.  And I was just getting to like Compiz...:(

---

### Post by barisurum on 2009-09-18
> And alas, the nvidia 185 drivers cause the RT kernel to hard-freeze as soon as it attempts to load xsplash.

Does it work with reverse engineered noveau or 2d nv drivers, if not the vesa driver?

---

### Post by trulan on 2009-09-18
> **barisurum said:**
> Does it work with reverse engineered noveau or 2d nv drivers, if not the vesa driver?
It works with the vesa drivers.  I haven't tried the nv drivers in a while, but if I remember correctly they only give me 640x480 resolution.  The vesa drivers give me 1280x1024 and work fine, so it's quite usable - just no 3D, no Compiz.

---

### Post by ram130 on 2009-09-18
Tried the Karmic Alpha 5 built on ma PC this morning. Couldn't get pass the log in screen, it just kept flashing over and over. Gonna try Ubuntu studio next in a VM and see if it works.

---

### Post by trulan on 2009-09-19
More good news!  The latest ffado and jackd updates fix the 'Ardour export issue' when using a firewire device!

It is now possible to export directly from Ardour, on the RT kernel, with real time enabled and low latency settings.  The light on my firepod turns red, the export process runs, and when it finishes the firepod light turns blue and Ardour is immediately fully functional again.  Now that is an improvement worth getting excited about!

---

### Post by trulan on 2009-09-19
I was doing some recording today on Karmic and got a little sidetracked. ;) Here is a table of latency test results (using jdelay).

AMD Athlon 3800+, 2gb ram, Presonus Firepod.
Ubuntu Studio Karmic, XFCE session (not Gnome)
All measurements are at 44100hz sampling
```
Frames    Periods    latency    Jack L.    Round-trip latency
256         3        1011.48    17.4ms    22.9ms
256         2        754.980    11.6ms    17.1ms
128         3        626.946    8.71ms    14.7ms
128         2        511.955    1.45ms    11.6ms
64          3        448.595    4.35ms    10.2ms
64          2        371.138    2.9ms     8.4ms
32          3        352.593    2.18ms    8.0ms
32          2        307.571    1.45ms    7.0ms
16          3        328.144    1.09ms    7.4ms
16          2        299.410    .726ms    6.8ms
```Note that as the Jack latency gets smaller, the difference between it and the actual latency (or, the latency of the firepod) increases slightly.  This difference is also greater when using 3 periods than when using 2.

The lowest buffering settings I was ever able to get to work before (Hardy or Jaunty) was 32 frames 3 periods, and that wasn't very stable. Using XFCE significantly lowers my onboard video card's load on the processor. That, combined with the new Karmic RT kernel, yields some pretty impressive numbers.
:guitar:

Edit: Just for kicks I pushed the sample rate all the way up for the firepod.  I was actually able to sync up enough to get the following mesurement:
32 frames 2 periods 96000 sample rate
478.688 samples latency, or 4.9ms round trip!
Not that it was stable enough to record at those settings, but that is a number that no previous Ubuntu setup would have ever dreamed of getting.  And that was using gnome!

---

### Post by barisurum on 2009-09-19
Thanks trulan for the enlightenment. Jdelay gives me:

2 periods, 16 frames @44100 : 16.000 +- 0.001 (15.999, 16.001 rarely)
Jack latency : 0.726 
dunno how to calculate the round-trip latency guy.

Can you tell me if it's good or not? RT jumps to %70 when I do that. My system is:

AMD 5600+ X2 64
4gb ram
ESI juli@ 24/192
I use gnome (I'd love to use xfce but gnome is just a damn pretty little bastrd)

PS: I connect the output of jdelay to input of jdelay, is it the proper usage?

---

### Post by trulan on 2009-09-19
Connect the output of jdelay to one of your system outputs.  (ie, output 1).  Plug a patch cable from output 1 to input 2.  Connect input 2 to jdelay's input.  Then, divide the number jdelay gives by your sampling rate.  The result is your actual round-trip latency.

I agree gnome is much prettier.  But given the age of both my computers, xfce increases my performance and stability significantly.  You would probably not be able to tell a difference on your system.

---

### Post by barisurum on 2009-09-19
I looked at the man page and it says plug the output of jdelay to input of jdelay and it gives me 16.000. I guess it is 16 thousand not 16 dot 000 and the result is: 0.362811791 but how come it is smaller than the jack latency?

---

### Post by trulan on 2009-09-19
I think you need to actually loop it through your soundcard, out one channel and into another, as I described above.  This measures the time it takes for a signal to complete the circuit - from the input of your soundcard, through Jack, to the output of the soundcard.

Something big has changed over the past 24 hours.  I can now run much lower latencies, yet have  greater stability.  I can push my CPU usage much higher with no x-runs - as in, two days ago if my CPU usage was hitting 40% I could expect glitches.  Now I can run at 70% with no problems.  And exporting from Ardour works as it should.  So like I said, something big has changed.:popcorn:

---

### Post by barisurum on 2009-09-19
and puredata now completely refuses to cooperate! Everything else works (including gigantic reaktor 5 in wineasio!) and the most important thing doesn't. I correctly set the samplerate and try with every possible latency setting but it keeps telling me:

audio I/O stuck... closing audio

Either there is a nasty bug in puredata or I do something wrong here

edit: OK I sorted the "audio I/O stuck..." issue, input channels were set to 0 somehow, but pops and cracks continue in the test audio, the I/O errors and cracks seem to be related to gui functions of puredata because I can reproduce them with pressing a button or menu item, it smells like a bug.

---

### Post by trulan on 2009-09-20
> **hanzomon4 said:**
> RT 5 won't boot for me... argh!!! Regardless the system timer resolution is still to freakin low for an rt kernel ```
/boot/config-2.6.31-5-rt:# CONFIG_HZ_1000 is not set
/boot/config-2.6.31-5-rt:CONFIG_HZ=250

```
They fixed it for you!
> linux-rt (2.6.31-5.6) karmic; urgency=low

  * Set CONFIG_HZ to 1000
  * New upstream RT patchset release, -rt11

 -- Luke Yelavich  Sun, 20 Sep 2009 10:19:56 +1000I guess there's no guarantee it will boot for you but they did change the system timer.

Edit:  Ran it through a few test with the firepod.  I haven't noticed any performance changes with this update (which means it still knocks the socks off anything I've used previously).  The big improvement for me seemed to come when Ffado and jackd were updated a few days ago.

---

### Post by barisurum on 2009-09-20
> linux-rt (2.6.31-5.6) karmic; urgency=low

* Set CONFIG_HZ to 1000
* New upstream RT patchset release, -rt11

-- Luke Yelavich Sun, 20 Sep 2009 10:19:56 +1000 


I was thinking about that too. Can anyone explain me how this will affect the performance of my system? Linux people say it results in higher processor overhead...

[http://www.linuxforums.org/forum/linux-kernel/52155-need-higher-timer-resolution-kernel-than-10ms.html](http://www.linuxforums.org/forum/linux-kernel/52155-need-higher-timer-resolution-kernel-than-10ms.html)

---

### Post by hanzomon4 on 2009-09-20
Yeah! I've been on a bug reporting spree

---

### Post by hanzomon4 on 2009-09-20
Yes!! It works perfectly!! Boots fine, nvidia drivers work(make sure you have the headers), and no hard lockup. It kicks ***!!

---

### Post by barisurum on 2009-09-20
> Yes!! It works perfectly!! Boots fine, nvidia drivers work(make sure you have the headers), and no hard lockup. It kicks ***!!

glad to hear that! :D So the rt kernel works with nvidia binary blobs then? Did you test it well? (I will post a wall message to facebook groups if it really kicks *ss)

---

### Post by hanzomon4 on 2009-09-20
Well I did normal computing stuff.. and used vkeybd to record into rosegarden which triggered qsynth and hydrogen. I then used ardour to record the output from the rosegarden controlled synths. All of this was synced through jack-transport. I only got xruns when I opened monsters like Ardour and rosegarden. At 5.3 ms latency I only got like 3 xruns, none of which occurred during performing/recording/playback. Add to that compiz was kicking, evolution was doing it's thing, and I had firefox open to help me figure out all of the jack routing + facebook.

---

### Post by trulan on 2009-09-20
Still fails to boot for me with the NVidia blobs.  (love that term!)

---

### Post by hanzomon4 on 2009-09-20
make sure you got the headers for that kernel, I had to install them manually from synaptic

---

### Post by trulan on 2009-09-21
Oh, the NVidia driver will install (if I do the init_MUTEX to init_semaphore change - then again, the results were the same without that change.)  And it kind of boots, but instead of seeing xsplash, I get a flashing text login.  Only slightly usable.  It will boot fine like this on the generic kernel, and it boots fine if I change xorg.conf to use vesa.

I have the headers installed (At least I think I do...)

---

### Post by barisurum on 2009-09-21
omg :S and what will I write to the wall posts then? there are people desperately waiting for this rejoice and I told them (nvidia users) not to download karmic studio alpha 6...

---

### Post by hanzomon4 on 2009-09-21
Just  sudo apt-get install linux-headers-2.6.31-5-rt to be sure. I had the same flickering problem before I installed this package.

---

### Post by trulan on 2009-09-21
Did you patch the NVidia driver or did you install it as it comes from the repository?  Which version are you using?

---

### Post by hanzomon4 on 2009-09-21
Yeah the little init_semaphore thing

---

### Post by ram130 on 2009-09-22
Well i finally got Ubuntu 9.10 to work...still lacking in features I see,  i hope by beta it looks good. I like the new login screen tho. Waiting on Ubuntu studio beta before i burn it.

---

### Post by trulan on 2009-09-22
Still no joy with the NVidia driver here.  It may be the result of the many upgrades in the alpha process. might be the result of my tinkering, or it might be because my hardware (onboard graphics card) is a bit sticky to initiate.  On boot-up, it always throws this error:
```
[    6.280271] ACPI: I/O resource nForce2_smbus [0x4c00-0x4c3f] conflicts with ACPI region SM00 [0x4c00-0x4c05]
[    6.280323] ACPI: Device needs an ACPI driver
[    6.280326] nForce2_smbus 0000:00:0a.1: Error probing SMB1.
[    6.280546] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c40
```Now the NVidia drivers do work for me on the generic kernel, and the vesa drivers work on the RT kernel.  This error shows up booting on any kernel, with any driver.

Also, when I was running Jaunty it would frequently hang on bootup with the NVidia drivers.  Sometimes it would take three or four tries before it would successfully boot.  So my experience with this may not be typical.  Nevertheless, there it is.  I think I'm going to let it rest for now as I can function just fine with the vesa drivers.

---

### Post by ram130 on 2009-09-22
> **trulan said:**
> Still no joy with the NVidia driver here.  It may be the result of the many upgrades in the alpha process. might be the result of my tinkering, or it might be because my hardware (onboard graphics card) is a bit sticky to initiate.  On boot-up, it always throws this error:
```
[    6.280271] ACPI: I/O resource nForce2_smbus [0x4c00-0x4c3f] conflicts with ACPI region SM00 [0x4c00-0x4c05]
[    6.280323] ACPI: Device needs an ACPI driver
[    6.280326] nForce2_smbus 0000:00:0a.1: Error probing SMB1.
[    6.280546] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c40
```Now the NVidia drivers do work for me on the generic kernel, and the vesa drivers work on the RT kernel.  This error shows up booting on any kernel, with any driver.

Also, when I was running Jaunty it would frequently hang on bootup with the NVidia drivers.  Sometimes it would take three or four tries before it would successfully boot.  So my experience with this may not be typical.  Nevertheless, there it is.  I think I'm going to let it rest for now as I can function just fine with the vesa drivers.

Just wait til beta! lol:guitar:

---

### Post by ranch hand on 2009-09-22
I think that the driver issues for nvidia will be straight before the beta release, at least for the generic kernal.

---

### Post by prismatic7 on 2009-09-22
I can't make 2.6.31-5-rt boot at all - as soon as X starts, my laptop locks so hard I have to remove the battery to restart! Anyone notice a problem like this? I want to be sure it's not a mistake I've made before I go bug reporting...

---

### Post by hanzomon4 on 2009-09-22
Do file bugs folks.. The rt kernel is the linchpin of audio on linux

---

### Post by ranch hand on 2009-09-24
AMD Phemom 8650 triple core processor (2.1GHz I think) is what my son has on his box.

None of the rt kernals from Hardy to Jaunty will install on the box, the generics all do.  He really wants to use Studio.  Any chance of the new kernals working on his box?

---

### Post by cornflake000 on 2009-09-24
I hope this isn't a stupid comment as I haven't read back through the posts but are you going to /etc/security/limits.conf and adding:

@audio   -  rtprio     99
@audio   -  memlock    unlimited

...to the file?  That will give you permissions to run the rt.  Without it, no way.  You can change @audio to any specific user instead e.g. @[user].  Anyway, I hope this is not old hat...

---

### Post by ranch hand on 2009-09-24
> **cornflake000 said:**
> I hope this isn't a stupid comment as I haven't read back through the posts but are you going to /etc/security/limits.conf and adding:

@audio   -  rtprio     99
@audio   -  memlock    unlimited

...to the file?  That will give you permissions to run the rt.  Without it, no way.  You can change @audio to any specific user instead e.g. @[user].  Anyway, I hope this is not old hat...
I am only lurking on this forum out of interest to see if I learn anything.

I do wonder if your post is aimed at me.

He can't install the rt kernal, as I understand it.  I will pass this on to him though.

---

### Post by cornflake000 on 2009-09-24
I see.  So many are not able to get the rt running due to the permission issue I just took a stab at it.  90% of the time it seems this is the fix, in jaunty or karmic.

---

### Post by ranch hand on 2009-09-24
Well, he may have had trouble getting it to reboot after installing, I don't really remember.  I do know that there is a bug report about it;

[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/407660](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/407660)

He is a musician and wants to record using Studio but can't get it to work.  He is headed this way tomorrow and I will show this to him.  Who knows, it may help.

I had no idea that the rt kernal existed until recently and have found this thread real interesting.  I may have to try it myself when 9.10 is released.  Right now I have all my extra HDD space tied up in testing.  I may have to see if I have a space for it while he is heree and see how it goes on this box.

We may learn something.

I have run linux, now, for a year.  He has been using it for several.  I am catching up fast but now here comes this rt stuff.  Geeze, and people have time to play games on their boxes.

Thanks for that pointer.

I would really like to know if anyone has used that processor with an rt kernal.  He has no trouble with the generic kernal.  I have tried to get hime to try a newer rt kernal in Jaunty but have no idea if they will support his tri core or not.

---

### Post by barisurum on 2009-09-25
ranch hand: 

I've a box with AMD athlon 64 X2 in which I can use the rt kernel. The important thing is which type of graphics adapter your son has. If it is  an older ATI (X series), then rt kernel will most probably work, because the drivers for them are open source. If it is nvidia then there are problems with the binary only (non-opensource) drivers that the vendor provides, it is very hard to adjust those drivers to an rt kernel since you can't have a look at the source code and don't know exactly how it works. If it is a new ATI (hd series) since they are generally used with the fglrx (closed source) drivers (you can use the open source drivers with them too but not mature yet), I don't have any info about them. 

In jaunty rt kernel didn't work for me too (ATI X1950XT here) but karmic 2.6.31-5 rt works here wonderfully.

---

### Post by ram130 on 2009-09-25
Well there is this new disk utility in Karmic and the studio verison that is telling me my hard drive is failing. Can I trust it? there are times where when accessing my drive or certain sections on it causes it to just freeze for  a few min(never usually does).....anyone?

---

### Post by barisurum on 2009-09-25
"Well there is this new disk utility in Karmic and the studio verison that is telling me my hard drive is failing. Can I trust it? there are times where when accessing my drive or certain sections on it causes it to just freeze for a few min(never usually does).....anyone?"

This problem must have been fixed with the latest updates. At least has been fixed for me...

---

### Post by cgroza on 2009-09-25
I never test beta versions...I use stable ones...I dont like to spent time fixing stuffs

---

### Post by bluesscream on 2009-09-25
An other place on the chance getting your question about this triple core processor answered might be [https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-users](https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-users)

---

### Post by ranch hand on 2009-09-25
> **barisurum said:**
> ranch hand: 

I've a box with AMD athlon 64 X2 in which I can use the rt kernel. The important thing is which type of graphics adapter your son has. If it is  an older ATI (X series), then rt kernel will most probably work, because the drivers for them are open source. If it is nvidia then there are problems with the binary only (non-opensource) drivers that the vendor provides, it is very hard to adjust those drivers to an rt kernel since you can't have a look at the source code and don't know exactly how it works. If it is a new ATI (hd series) since they are generally used with the fglrx (closed source) drivers (you can use the open source drivers with them too but not mature yet), I don't have any info about them. 

In jaunty rt kernel didn't work for me too (ATI X1950XT here) but karmic 2.6.31-5 rt works here wonderfully.
Hey that is great.  I do know that he is using the on board video so it has to be ATI.  He also just had some shop fix his box and they put the MB in but I don't know how old the chip is.

Thanks.

---

### Post by ranch hand on 2009-09-25
> **bluesscream said:**
> An other place on the chance getting your question about this triple core processor answered might be [https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-users](https://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-users)
Wow, I didn't have a clue that you guys were so well infiltrated into the fabric of our world.

He mentioned some forum but this list looks good to me.  Thanks a bunch.  I'll get him on there tomorrow (he is coming to help with some construction) and he can change his address later when he heads home.

---

### Post by ram130 on 2009-09-25
> **ranch hand said:**
> Hey that is great.  I do know that he is using the on board video so it has to be ATI.  He also just had some shop fix his box and they put the MB in but I don't know how old the chip is.

Thanks.

Hmm try the drivers  from ati main site. They might just help you out.

> **barisurum said:**
> "Well there is this new disk utility in Karmic and the studio verison that is telling me my hard drive is failing. Can I trust it? there are times where when accessing my drive or certain sections on it causes it to just freeze for a few min(never usually does).....anyone?"

This problem must have been fixed with the latest updates. At least has been fixed for me...

It alerted you that your hard drive was failing too?? Just wondering cause my system is behaving like does when my hard drive is failing(constant freezes when accessing the drive to point where linux crashes).

---

### Post by barisurum on 2009-09-26
ram130: Disk utility and fsck alerted me that the filesystem check failed (fsck) and it was uncontigious (disk utility). then your problem must be a "real one". I referred to the "file system %1.5 uncontigious" fsck failures which happened through alpha4 to alpha5. But if you experience lock-ups related to file read-write operations, then I fear the problem is really there.

---

### Post by ram130 on 2009-09-26
> **barisurum said:**
> ram130: Disk utility and fsck alerted me that the filesystem check failed (fsck) and it was uncontigious (disk utility). then your problem must be a "real one". I referred to the "file system %1.5 uncontigious" fsck failures which happened through alpha4 to alpha5. But if you experience lock-ups related to file read-write operations, then I fear the problem is really there.

hmm, well i boot back into 9.04 and the problem has gotten worst. Its strange though, no warning from xp(just crashes), 9.04 or my own bios(smart). The problem has gotten so bad that my system get unresponsive to  a blank screen and hard restart is needed. I guess 9.10 has some tricks up its sleeve..

---

### Post by bluesscream on 2009-09-26
@ram130: karmic shows me a bad drive on my stationary pc and that's true. It's a drive from an old windows pc and it doesn't boot at all, only blue screens or freezes after some minutes. But I succeeded backing up all important files to healthy drives. There are 4 in this machine, 3 are ok. Think it's high time for your new drive.

@barisurum: -rt-5 works fine, even 3d, on my notebook with intel graphics. On my stationary pc with legacy nvidia graphics if I use -rt I have to edit xorg.conf driver from "nvidia" to "nv". A boot-script for switching between different xorg.conf would be fine, but my coding abilities are too poor.

---

### Post by ranch hand on 2009-09-27
Seeing how my son is here, and I am nuts, I installed Studio9.04.

How do I go about getting the newer kernals?

It really is kind of an interesting OS.  Smaller than I figured it to be.

Haven't really fooled with it except to get medibuntu and configure the bugger to my liking.

What audio file editor do most folks use?

The sucker installed easily and runs all right on my box.  He may have trouble with his weird board and triple core but I have yet to meet an Ubuntu variation that does not just love my box.  Upstart youngsters.

---

### Post by barisurum on 2009-09-27
> bluesscream: -rt-5 works fine, even 3d, on my notebook with intel graphics

Its good to hear that intel graphics stack works with rt! This means a lot of people will be using ubuntu studio 9.10 and our community will get much bigger and a bigger community means a louder voice. Thank you Ingo Molnar and other upstream rt guys!

And because the intel graphics stack is also opensource this also means that open source drivers are a key to stability. I hope nvidia drivers will also be opensource someday.

---

### Post by ram130 on 2009-09-27
> **bluesscream said:**
> @ram130: karmic shows me a bad drive on my stationary pc and that's true. It's a drive from an old windows pc and it doesn't boot at all, only blue screens or freezes after some minutes. But I succeeded backing up all important files to healthy drives. There are 4 in this machine, 3 are ok. Think it's high time for your new drive.


yep! Its pretty smart utility, all OS should have one like it. I got my xp to boot finally and had to goto Event Viewer to see that my disk was failing "had a block" frm step. 3. I should be getting a new hard drive by next week hopefully. Thanks goes to the new Karmic early warning disk utility.Hmm, alot of people gonna be surprise when they see a pop up about a failing drive though, they gonna be like "that cant be true".

---

### Post by trulan on 2009-09-27
Wow, I was away for the weekend and you guys have been having fun!

I was visiting my brother (a long-time linux user) and I was actually able to teach him something about linux! (I've been using Linux only for a few months).

Thought I'd put in a word here about the difference between real time permissions and a real time kernel.

Real Time Permissions (as in, checking the 'real time' box in Jack control) allows a process to get higher scheduling priority.  This is managed by the security limits.  In my brother's case, he is using the generic kernel but we were still able to get pretty good audio performance on his onboard intel sound card by enabling 'real time'.  (He thought he had to be using the real time kernel for that to work.)

The Real Time kernel (RT), on the other hand, is just that - a kernel optimized for such things.  You still need to have the security limits set properly for your processes to get good scheduling priority.  In actual practice, the real time kernel will allow me to basically cut my audio latency in half, and run with improved stability (fewer x-runs).

Unfortunately, the community using the RT kernel is a lot smaller than the community using the generic kernel, and there have been frequent instances of it having problems where the generic kernel works just fine.  (Not booting, freezing, not liking the NVidia binaries, etc.).

@Ranch Hand:  Most people use Audacity for a basic audio editor (and the generic kernel is fine for that type of work).  For multi-track recording, Ardour would be the program of choice.

I pretty much am focused on recording acoustic instruments and vocals, so I use Ardour on the RT kernel for that (when I'm recording in a live concert setting and some of the signal to the speakers is actually being routed through the computer, I need the latency to be as low as I can get it.  And x-runs or glitches are simply out of the question.)

---

### Post by barisurum on 2009-09-28
New upstream nvidia patch arrived! [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/413296](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/413296) (see end of posts)

Has any nvidia user tried this?

---

### Post by bluesscream on 2009-09-28
@barisurum: Nvidia drivers opensource, that would be great. But I think there is only little chance. Hope I'm wrong, but nvidia seems to be in the obsolete, but still powerful mainstream of propriarities, copyrights... I tried to hack kernel 173.14.20 whith the contents of the patch you gave the link -thanks -, but did not succeed. There is a  thread around here to this special theme. In last gerneric kernel driver 173.14.20 runs fine.  But as long as I do audio production I don't need 3d, compiz or opengl, so old opensource driver "nv" does it's job, may be even better then 3d-driver because this eats system performance. As I wrote before, it would be fine to have a tool for easier switching graphic modes  synchronous with kernel-changes.
@ ranch hand: I also use audacity. It's in the repos. On wine/wineasio most windows-audio stuff works too. 
@trulan: welcome back, thanks for yor explanation about difference between rt-permissions and rt-kernel. I figured out, that sometimes activating -rt in jack configuration worked too in generic kernels, but didn't understand why. 
I use midi controlled synthesizers and  sound input modifying effects in real-time performance, so I need an optimized balance between system performance and low latencies. Karmic (i. E. it's developers) do a good job!
Have a good day and keep some energy for really making music.:guitar:

---

### Post by trulan on 2009-09-28
> **barisurum said:**
> New upstream nvidia patch arrived! [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/413296](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/413296) (see end of posts)

Has any nvidia user tried this?
This fixes the init_MUTEX bug.  The dkms module now builds without manually patching anything.  Unfortunately, X still fails to start for me on the RT kernel when the NVidia driver is selected.  It hard freezes before the login screen.  Works fine on the generic kernel.

---

### Post by trulan on 2009-10-03
**Edit: The fix has made it into the main repository, as of 10-27-2009.  No need to patch anything.**

The rest of this post is obsolete, just for reference:
 
A patch has been submitted on Launchpad that now allows the NVidia 185 drivers to work properly on the RT kernels.  If you want to try it out before the driver package is updated, here's how I got things working:

1. Boot into the generic kernel.  Through Jockey (hardware drivers), activate the NVidia 185 drivers.

2. Download and unzip the patch.  In a terminal, navigate to the directory where it is saved.

3. Put the patch in the right place:
```
sudo mv rt_preempt_31.patch /usr/src/nvidia-185.18.36/patches/
```4. Delete the un-needed patch (the new patch includes a replacement for this one)
```
sudo rm /usr/src/nvidia-185.18.36/patches/nvidia-rt-compat.patch
```5. Build the dkms module for your kernel:
```
sudo dkms build -m nvidia -v 185.18.36 -k 2.6.31-9-rt
```[I].
[/I]
7. Reboot into the RT kernel, and all should be well.

On my first reboot I had a flashing screen for maybe half a minute.  Then xsplash came up and everything was fine.

I modified the patch from Launchpad just slightly so it can find the files to patch - apparently the author of the patch wasn't using Jockey to install the drivers and the files were in a slightly different place.

---

### Post by bluesscream on 2009-10-03
congratulations trulan for making your nvidia card work with -rt :P
I was not lucky with 173.14... in my stationary machine, but your success restores hope.

---

### Post by hanzomon4 on 2009-10-03
> **trulan said:**
> A patch has been submitted on Launchpad that now allows the NVidia 185 drivers to work properly on the RT kernels.  If you want to try it out before the driver package is updated, here's how I got things working:

1. Boot into the generic kernel.  Through Jockey (hardware drivers), activate the NVidia 185 drivers.
2. Download and unzip the patch.  In a terminal, navigate to the directory where it is saved.
3. Put the patch in the right place:
```
sudo mv rt_preempt_31.patch /usr/src/nvidia-185.18.36/patches/
```4. Delete the un-needed patch (the new patch includes a replacement for this one)
```
sudo rm /usr/src/nvidia-185.18.36/patches/nvidia-rt-compat.patch
```5. Build the dkms module for your kernel:
```
sudo dkms build -m nvidia -v 185.18.36 -k 2.6.31-5-rt
sudo dkms build -m nvidia -v 185.18.36 -k 2.6.31-6-rt
```6. Reboot into the RT kernel, and all should be well.

On my first reboot I had a flashing screen for maybe half a minute.  Then xsplash came up and everything was fine.

Edit:  I modified the patch from Launchpad just slightly so it can find the files to patch - apparently the author of the patch wasn't using Jockey to install the drivers and the files were in a slightly different place.

Yay!!!

---

### Post by cornflake000 on 2009-10-05
I've been lurking this thread having had the same Nvidia issues.  With this patch I don't have the X crashes.  That's great.  But now nothing related to sound production, manipulation or encoding will work without either crashing, exiting or causing the system, memory or whatever, to go into these timeouts things eg. stop... wait... start for a moment... stop... you can move the cursor then you can't... then you can... It's weird.  At least before, I could get jack to work till X crashed but now jack crashes instead as well as other things related.

Anyone have any enlightening thoughts or ideas?

I'm running Karmic Beta 64 Studio....

Thanks!!

---

### Post by trulan on 2009-10-05
There's a new patch out.  I'll test it and post it here if it works for me.

---

### Post by bluesscream on 2009-10-05
@cornflake 000: I urgently need enlightenment too. But maybe this can help you a little on your way to ubustu:
Really it's a little tricky. 'Think you've properly set the limits in /etc/security. Another really important thing ist to set your processor('s) fixed on full performance:
Right click your panel, add Cpu Frequency Panel Monitor for each cpu-kernel, configure them per rightclick one for each kernel.

Now, by left-clicking on the CPU Frequency Monitor applet, you can choose the frequency for your processors after verifying with your password.

In former versions I had to do:  
$ sudo dpkg-reconfigure gnome-applets
and answer “yes” to the question regarding setting the suid of the cpufreq-selector executable. 
But I don't know wether you need this anymore.

And please figure out jack's priority setting. In earlier versions best setting was top 89. Now if I set it too high I get such crashes too. Start with default (think it's 10). For me it works until 50 - 60.

For me proprietary nvidia and rt-kernel is voodoo. I try to get my card running with actual rt-kernels too, but from former experiences with neccessity of editing graphic-card latencies, IRQ-priorities etc. I think on -rt we should use "nv" as driver in xorg.conf instead of "nvidia"  and if we want to play 3d/opengl we should edit xorg.conf to driver "nvidia" and reboot into -generic kernel. 
And  again: for this switching I'd like to have a working script, maybe on grub level ;) Any lurking coders/scripters around?

Good luck

---

### Post by trulan on 2009-10-05
OK, I deleted the old patch and uploaded the new one to my how-to post.  It seems to work well.
[http://ubuntuforums.org/showpost.php?p=8046770&postcount=109](http://ubuntuforums.org/showpost.php?p=8046770&postcount=109)

@bluesscream - I think you've got a great idea there.  Let us choose which video driver to use when booting up.  I definitely notice a decrease in RT performance when running the NVidia drivers.  I guess it might work too if we could lower the priority of the drivers, like we raise the priority of Jack and such.  But that might cause other issues, I don't know.  A convenient way to switch which drivers are used would be very nice.

Also, thanks for the tip on CPU scaling!  That's great!

I never messed with Jack's priority settings much.  I set it at 70 like I saw on a guide somewhere and there it sits - including right now.

---

### Post by trulan on 2009-10-09
There is an update to the NVidia drivers today.  It does not include the latest RT patch.  I patched it using the same method as the previous version of the driver.  I did not test it without patching it.  So far it is working well.

---

### Post by bluesscream on 2009-10-10
> Let us choose which video driver to use when booting up. I definitely notice a decrease in RT performance when running the NVidia drivers. I guess it might work too if we could lower the priority of the drivers, like we raise the priority of Jack and such. But that might cause other issues, I don't know. A convenient way to switch which drivers are used would be very nice.
It's a great community, so even a noob like me may be able to figure out something that comes near to a solution:
[http://ubuntuforums.org/showthread.php?p=8084937#post8084937](http://ubuntuforums.org/showthread.php?p=8084937#post8084937)

---

### Post by eric71 on 2009-10-14
After initial problems with jack not starting and not being able to remove pulseaudio without screwing everything up (very early in this thread), I came back to the Beta release of Karmic. I started with the basic Ubuntu install and added the rt-kernel, updated limits.conf, and have been running Reaper with Wine and wineasio as well as it has ever worked for me. This has been with no modifications to pulse either. 

I was extremely happy until I updated yesterday. It pulled in a new version of the RT kernel and a new version of Wine 1.2. I didn't have time to investigate last night and I am stuck at work now, so I am not sure if Wine or the new kernel is to blame. Has anybody using Ubuntustudio had any issues with the new kernel? I've had xruns and almost immediate audio stuttering in the same project that was running beautifully (even with full desktop effects enabled) a few days ago.

I'll follow up when I get home and can try the old kernel and play with Wine a little, but if anyone else has seen something change since recent upgrades, it could point me in the right direction.

---

### Post by hanzomon4 on 2009-10-14
yeah I've had problems with the new *.8 rt kernel. I think has something to do with dynamic ticks being off by default ([link to changlog]("https://launchpad.net/ubuntu/+source/linux-rt/2.6.31-8.12/+changelog"))

---

### Post by hanzomon4 on 2009-10-14
I filed a bug... [https://bugs.launchpad.net/ubuntu/+source/linux-meta-rt/+bug/451169]("https://bugs.launchpad.net/ubuntu/+source/linux-meta-rt/+bug/451169")... Get in on it as "affecting you too" if it affects you too.

---

### Post by trulan on 2009-10-14
For those who are using the NVidia drivers and the patch I posted, Iain Buc&#322;aw, who wrote it, recommends rolling back to the older patch due to a screensaver issue, so I re-posted it  (on page 11).

---

### Post by hanzomon4 on 2009-10-14
> **eric71 said:**
> After initial problems with jack not starting and not being able to remove pulseaudio without screwing everything up (very early in this thread), I came back to the Beta release of Karmic. I started with the basic Ubuntu install and added the rt-kernel, updated limits.conf, and have been running Reaper with Wine and wineasio as well as it has ever worked for me. This has been with no modifications to pulse either. 

I was extremely happy until I updated yesterday. It pulled in a new version of the RT kernel and a new version of Wine 1.2. I didn't have time to investigate last night and I am stuck at work now, so I am not sure if Wine or the new kernel is to blame. Has anybody using Ubuntustudio had any issues with the new kernel? I've had xruns and almost immediate audio stuttering in the same project that was running beautifully (even with full desktop effects enabled) a few days ago.

I'll follow up when I get home and can try the old kernel and play with Wine a little, but if anyone else has seen something change since recent upgrades, it could point me in the right direction.

Hey try this... 

1.reboot and highlight the rt kernel in grub menu

2. Press "e" and add nohz=on to the end of the kernel command line. Thats the one that looks like this "linux	/boot/vmlinuz-2.6.31-8-rt root=UUID=b5f26eeb-b511-4d06-8989-486e8a53a84b ro quiet splash **[COLOR="Red"]nohz=on[/COLOR]**".  

3.Then press ctrl+x

4.Play around with it, see if performance is better.

5.After you tested it a bit run this command in a terminal ```
cp /var/log/dmesg dmesg.txt

```

6. Attach that file dmesg.txt to my bug report and leave a comment [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/451169")

---

### Post by eric71 on 2009-10-14
I've just now seen your post and will do what you suggest. I have tested with the previous two RT kernels -6 and -7. They still work fine, so it is definitely not related to the Wine upgrade. So something has definitely changed in the update of the RT kernel to -8. I'll add to your bug report as soon as I try the nohz option.

---

### Post by eric71 on 2009-10-14
The nohz option fixed the problems. I've posted this to the bug report, which unfortunately seems to have been marked invalid already. Hopefully it gets re-opened so this can be fixed. It seems to make a huge difference. I'd never been happier with RT performance in Ubuntu, until this change. I guess it's easy enough to append the grub line if they choose not change it back.

Thans for the help.

---

### Post by hanzomon4 on 2009-10-14
I actually removed it from the kernel command line and it worked even better. just reboot to try it out.

---

### Post by eric71 on 2009-10-14
I've rebooted without adding nohz=on and the major problems have returned. So, at least in my case, it made a big difference.

---

### Post by eric71 on 2009-10-14
I've run some tests for Alessio over in the bug report thread. If I'm interpreting cyclictest results right (and I might not be) realtime performance looks better without adding nohz=on. So it may be that Wine or wineasio were working better with dynamic ticks on and now don't fare so well with them off by default, whereas native apps like ardour and hydrogen might be happier now. i'll see what Alessio says, but it may be that us Reaperites on Ubuntu may need to to add nohz=on to our boot lines in grub, or maybe it is just something specific to my setup (a thinkpad with admittedly finicky onboard intel sound.

---

### Post by hanzomon4 on 2009-10-14
File a bug against wine if that's the case

---

### Post by trulan on 2009-10-14
> **eric71 said:**
> So it may be that Wine or wineasio were working better with dynamic ticks on and now don't fare so well with them off by default, whereas native apps like ardour and hydrogen might be happier now.
I haven't had time to test the new kernel very thoroughly with Ardour, Jack, and Ffado yet, but from what I've seen it's at least as good as the previous kernels.  Just for kicks I ran Ultimate Stunts (a 3d driving game) on the RT kernel.  I was getting 30 fps on the generic kernel and 20 on the rt kernels.  The new -8-rt kernel gives me 30 fps, so it's a definite improvement in that area.  Whatever that's worth...

Edit:  A little further testing shows that I was off - 3d graphics are better under the generic kernel.  I wonder if there was any change at all in this area.

And, as NVidia updates keep rolling out, we'll see how well the driver continues to play with the RT kernel.

Another edit:  I noticed one small but possibly significant improvement with the recent updates:  I can now maximize and minimize Ardour, or switch workspaces, while running DSP usage in excess of 50% and using the NVidia drivers, without causing x-runs.  This has been possible for a while for me on the vesa drivers, but it's a first for NVidia.  Good stuff!

---

### Post by eric71 on 2009-10-16
I'm not even sure at this point if wine or wineasio were the problem. I only noticed a downgrade in performance because I had been playing back an old project for a friend who sang on it. It played without a hitch. A few days later, after the kernel upgrade, I tried again and got xruns, and the audio basically ground to a halt after 30 seconds. 

It turns out that this project was using a very cpu heavy mastering chain with vsts I have long since replaced with less cpu intensive ones. I suspect one of these plugins running in Reaper under wine might have worked better for some reason with dynamic ticks. Swapping that mastering effects chain for other plugins lets the project play fine with the current kernel. In hardy or Jaunty I can't recall even being able to play this old project with all the plugins enabled.

And this is playback, not recording. My results running cyclictest definitely show improvement with the current realtime kernel with dynamic ticks off by default. 

So, in summary, the problems I ran into were probably a fluke related to certain free vsts in one project, and even for others running Reaper with wineasio, the new kernel should be just fine. And if for some reason it isn't, try adding nohz=on to the grub boot line.

---

### Post by cornflake000 on 2009-10-17
Everything works like a dream using Karmic Studio rt 64 bit.  Smooth as silk... as long as I don't do anything relatime.  Is anyone using jack.d or anything else relatime in Karmic?  Sorry, I'm not really trying to be cute but I have been using the rt kernel for the last 3 distributions on the same box without to many problems but I have yet to get it working in Karmic without crashing into the Nvidia card.  I have kept up with, and have on occasion been involved in all the Nvidia chaos from Jaunty A2 on but haven't had a break with Karmic rt yet. 

I think my question is too broad to attempt but what am I missing?  Maybe nobody can actually use it reasonably with Nvidia and no one has admitted it or maybe I'm the only one on the planet that can't get it to run for more than 2 minutes. If I flip over to my Jaunty64 partition, there's no problem.  I'm just curious.  I have no real need for it; I just test distros for the fun of it, but I am getting nowhere fast and I think my ego is tarnished.

---

### Post by hanzomon4 on 2009-10-17
Anybody else getting hard lock ups after prolonged use of the rt kernels?

---

### Post by barisurum on 2009-10-17
> Anybody else getting hard lock ups after prolonged use of the rt kernels?

No lock-up here: AMD64, ATI X1950XT card

---

### Post by hanzomon4 on 2009-10-17
I wonder if it's my nvidia card

---

### Post by trulan on 2009-10-17
Mine has started occasionally locking on boot (when using the NVidia driver), just like Jaunty does - Once it is up and running all is well.  I have not had it running for more than a few hours at a time though in the last week.

I do use jackd, sometimes with the nvidia drivers and sometimes with the vesa driver, but always in real time.  With Hardy or Jaunty, if I pushed my CPU above 30% jack would become very unstable.  With Karmic I can run it up to 60% with no issues.  That's why I keep saying it is a big improvement over previous versions.

The lockups on boot though are a bit disturbing.  I was hoping I was past that...

Edit:  (some of this is in response to the post below.)
I have an onboard NVidia GeForce 6150 LE.  I have had no success in editing xorg.conf to manually set my screen resolution, and I really don't see the point in learning as this is fast becoming obsolete.  Only the NVidia drivers will see 'past' my video card and identify my monitor, so using them is the only way I can adjust the settings.  Driver "nv" will give me nothing but 640x480, driver "vesa" gives me 1280x1024 which is what I want anyway, so I can use that.  As far as performance goes, the gap has been steadily closing between the NVidia and vesa drivers for me (as long as I remember to turn Compiz off when I am trying to record ;).)
I guess the main thing is, if Ubuntu Studio is going to be widely used (and I hope it is) proprietary video drivers such as NVidia and ATI are going to have to work out of the box, consistently.

---

### Post by bluesscream on 2009-10-17
Did you try -9-rt with driver "nv"? for me this is the best audio-configuration I ever had on my stationary machine, most stable and lowest latencies. Firewire is as tricky as before. I don't try to do other things then sound-audio-production/live-performance with this kernel boot-up. For anything else I boot into generic kernel which supports the last proprietary driver for my old Geforce 5200FX.

---

### Post by trulan on 2009-10-17
> **bluesscream said:**
>  Firewire is as tricky as before.
I'm curious, what troubles have you had with firewire?

---

### Post by bluesscream on 2009-10-18
I see, nv driver isn't really useful as long as it's limited to poor resolution.
I had a similar problem too, but not so low resolution, only black stripes at both sides. 
Now the Screen Resolution GUI from System/Preferences works fine for me on "nv"-driver, but as I remember I first had to sychronize it's settings with nvidia-settings in running prorietary driver on a -generic kernel.
My etc/X11/xorg.conf is untouched from proprietary driver install except  driver "nvidia" replaced by "nv".
Here is a link which may be helpful 
[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)
and I remember sometimes before I had to use xrandr to solve resolution issues.

---

### Post by bluesscream on 2009-10-18
> **trulan said:**
> I'm curious, what troubles have you had with firewire?
Had to make /dev/raw1394 member of group audio with rw enabled (on default owner and group were root)
and open as root lib/udev/rules.d/50-udev-default.rules: 
search/edit/insert following line:
KERNEL=="raw1394",		GROUP="audio"
(Maybe it works too if /dev/raw1394 is member of group video
and lib/udev/rules.d/50-udev-default.rules contains line 
KERNEL=="raw1394",		GROUP="video")
when I did this, after reboot qjackctl started jackd, jackbridge for wine/wineasio and connected the edirol fa101.
I had to reinstall ffado-mixer to make it work.
My firewire-pci-card with via chip is known for issues, so may be other fw-chips work ootb.
No real troubles, but I think for a bloody newbie that's really hard.

---

### Post by cornflake000 on 2009-10-18
I decided to give up on the Nvidia drivers for a while and I'm using vesa since last evening.  Interesting enough, I can now run jack.d etc. for about 20 minutes... but it still crashes in the end and will only run if I use default priority.  

Another interesting item is that I noticed the cpu freq changes from performance to ondemand even though I have it set to performance.  I'm wondering if that is throwing it off.  I posted this dilemma to a different thread a few moments ago.

---

### Post by markbuntu on 2009-10-18
I tried. I had fglrx working with the -8rt kernel with update to fglrx with the new rt patch. Got the ubuntusudio-audio metapackage and the system locked up while installing it. Had to run dpkg blah blah because synaptic was borked. got me the -9rt kernel and a bunch of other stuff. -9rt will not build fglrx kernel modules. can boot into -8rt but no menus etc. gnome is trashed....

bahhhh.......

At least the rt kernel will boot on my hardware. It would not do that on Intrepid or Jaunty.

I will wait for the rc in a few days and try again.

---

### Post by trulan on 2009-10-18
@bluesscream - yeah Ubuntu Studio controls assigns raw1394 permissions to the video group.  That works, as long as your username has permission to use video devices (this is turned off by default.)  The users and groups gui is a bit different in Karmic than it was in Jaunty or previous versions - IMO it's an improvement.  And my onboard agere 1394 chip worked OOTB.  So did my laptop's Ricoh chip, and they're supposed to be one of the worse.

Of course, I've never tried to use wineasio so that may add to the complexity a bit.

---

### Post by motin on 2009-10-19
Using the latest rt and 185 nvidia drivers from karmic repos and still no-go with stable graphics... Tracking my progress and have collected some valuable information in [http://ubuntuforums.org/showthread.php?p=8127639](http://ubuntuforums.org/showthread.php?p=8127639) on the subject.

---

### Post by barisurum on 2009-10-19
@Markbuntu 
> At least the rt kernel will boot on my hardware. It would not do that on Intrepid or Jaunty.

So can we say that fglrx drivers have some little solvable problems? Did you try the 4, 5, 6, 7rt kernels with fglrx? What ATI hd card are you using (R600 - R700?)? And did you try any rt kernel with open source radeon drivers? I may consider upgrading my card to a hd one if it works and many people must be watching us... Yes I know they do... :)

---

### Post by trulan on 2009-10-19
For the record:

I don't usually use RT stuff and Compiz at the same time (sure-fire way to cause x-runs ;) )
But it works.  -9-rt kernel, latest nvidia-glx-185 from the repo, onboard GeForce 6150 LE.  I've never had a kernel lock-up once I was up and running - only X occasionally failing to start.

Why someone would want to use the Compiz cube and Ardour at the same time, I don't know.  But here you have it:

---

### Post by barisurum on 2009-10-19
> Why someone would want to use the Compiz cube and Ardour at the same time, I don't know.

It's very useful when you record the output of another application to ardour. For example rosegarden to ardour. You can watch the playheads move together and make sure that everything is in order. And it doesn't cause extra xruns, at least on my system (open source ATI), all the xruns happen on graphics rendering threads and have nothing to do with the sound, and yes its a little bit annoying but I got used to it :). Desktop zoom function is veerry useful when I work with small-gui vst plugins. I manage my studio much more efficiently with compositing.

---

### Post by motin on 2009-10-19
> **trulan said:**
> Why someone would want to use the Compiz cube and Ardour at the same time, I don't know.  But here you have it:

For me it's about using Mixxx (which requires graphic acceleration for the waveform displays) and RT at the same time as well as not having to reboot the computer to use RT.

---

### Post by hanzomon4 on 2009-10-19
I'm not sure what happened but I'm now starting to get xruns out the *** and disconnects from jack by ardour, qsynth, aeolus.. just about everything that makes sound. It's quite bad, things like qsynth won't even reconnect. The only audio thing I noticed was the removal of rtkit but that's a pulse thing.

---

### Post by bluesscream on 2009-10-19
> **cornflake000 said:**
>  I can now run jack.d etc. for about 20 minutes... but it still crashes in the end and will only run if I use default priority.  


> Another interesting item is that I noticed the cpu freq changes from performance to ondemand even though I have it set to performance.  I'm wondering if that is throwing it off. 

Yes, it does.

Same for me if cpufreq is set to "performance" it falls back when all processes are idle. Can you select numeric userspace frequencies? This does the job for me.

---

### Post by bluesscream on 2009-10-19
deleted

---

### Post by trulan on 2009-10-19
> **trulan said:**
> Why someone would want to use the Compiz cube and Ardour at the same time, I don't know.
> **barisurum said:**
> It's very useful when you record the output of another application to ardour. For example rosegarden to ardour. You can watch the playheads move together and make sure that everything is in order. And it doesn't cause extra xruns, at least on my system (open source ATI), all the xruns happen on graphics rendering threads and have nothing to do with the sound, and yes its a little bit annoying but I got used to it :). Desktop zoom function is veerry useful when I work with small-gui vst plugins. I manage my studio much more efficiently with compositing.
I see.  I was just trying to be funny when I made the above statement.  I hadn't really viewed the Compiz stuff as useful, just as very cool effects.

Rotating the cube does cause audible glitches for me, so I try to always turn visual effects off when doing stuff where it matters, like recording.  But then I have an onboard video card, and three year old hardware.

---

### Post by bluesscream on 2009-10-19
> **hanzomon4 said:**
> I'm not sure what happened but I'm now starting to get xruns out the *** and disconnects from jack by ardour, qsynth, aeolus.. just about everything that makes sound. It's quite bad, things like qsynth won't even reconnect. The only audio thing I noticed was the removal of rtkit but that's a pulse thing.

Same for me after today's (20091019) update :confused:. Be careful,  keep a  partition for production untouched - it's beta :-k

---

### Post by trulan on 2009-10-21
More NVidia adventures:

Two days ago, a patch was added to the nvidia-glx-185 set that broke it, at least for me.  More info on it on my how-to NVidia post on page 11:
[http://ubuntuforums.org/showpost.php?p=8046770&postcount=109](http://ubuntuforums.org/showpost.php?p=8046770&postcount=109)

Edit: I have been told on Launchpad that this should not affect anything to do with the RT kernel.  Hopefully that is the case, and the problem was a result of my own blunder.  But, I may have inadvertently sped up the process of getting the RT fix released, so manually patching the NVidia driver will no longer be necessary.  Hopefully the update will hit the servers soon.

---

### Post by trulan on 2009-10-22
It seems it was not so much the patch that broke things.  It seems to be the removing and rebuilding of the dkms module that allows things to work for me.

At any rate, there is now a ppa you can use to install RT compatible NVidia 185 drivers, already patched:
_[https://launchpad.net/~tinivole/+archive/ppa](https://launchpad.net/~tinivole/+archive/ppa)_

---

### Post by hanzomon4 on 2009-10-23
nvidia drivers have been smooth for me after the building of the module got worked out some time ago

---

### Post by barisurum on 2009-10-23
An update removed the rtkit package recently. is it needed to be installed for rt kernel to work properly? What does it do actually by the way? Because my system seems more unstable without it.

---

### Post by bluesscream on 2009-10-23
> rtkit... do we need it?
I don't think so. 2.6.31-9-rt as well as 2.6.31-14-generic after a reinstall are running smooth for me on an old amd64x2 with nvidia legacy agp graphic card and on an up to date notebook with intel chips. For me as a former ms-junkie rights management is the most difficult issue.

---

### Post by bluesscream on 2009-10-23
Damned file /etc/security/limits.conf, it stole me 3 days. Typed erroneously a line @audio - priorities 99 instead of @audio - rtprio 99 whith the consequence of total firewire dysfunction. Please developers, if anyone of you reads this, please make this entry default in /etc/security/limits.conf. As far as I see this doesn't touch any other progs or performance.

---

### Post by barisurum on 2009-10-24
Thanks bluesscream, forgot about rtkit already. increasing the realtime priorities of threads like sirq-timer, sirq-hrtimer and the thread of my soundcard's alsa driver gave me a much more stable jack environment. Priorities are as follows now:

hrtimer, timer: 95 (midi timing is the most important)
soundcard: 90 (sound card must work glitch free)
jack: 70 (Jack must be below the soundcard and above the overall system)

Now a question comes to my mind: If the rtprio 99 in limits.conf effects all processes that are @audio members, then will it break my above setup?

PS: You can set the thread priorities by "chrt -f -p my_priority my_thread" command (as root). First get the thread numbers with a "ps -e" command (ie. "ps -e | grep ICE1724" my sound card). And then "sudo chrt -f -p 80 2312 (or whatever)"

---

### Post by barisurum on 2009-10-24
:D I recently realized it isn't that easy...

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

chrt -f -p 95 5
chrt -f -p 95 11
chrt -f -p 95 19
chrt -f -p 95 25
chrt -f -p 95 772

chrt -f -p 90 1552 [COLOR="Red"]-> changes with boot[/COLOR]

exit 0
```

I can succesfully increase the priorities of the first five processes (timers) as their process ids don't change with boot, but the last id changes with every boot (soundcard driver). How can I change the last line of the script to find out the process id of the alsa driver? (module name is ICE1724). Thanks.

---

### Post by trulan on 2009-10-25
> **bluesscream said:**
> Damned file /etc/security/limits.conf, it stole me 3 days. Typed erroneously a line @audio - priorities 99 instead of @audio - rtprio 99 whith the consequence of total firewire dysfunction. Please developers, if anyone of you reads this, please make this entry default in /etc/security/limits.conf. As far as I see this doesn't touch any other progs or performance.
I think that entry is made by default when Ubuntu Studio Controls is installed or run - whichever, that line gets put there automatically if you use Ubuntu Studio Controls.

---

### Post by g-raf on 2009-10-26
Does anyone know if the proprietary fglrx video driver is working on karmic rt?

---

### Post by markbuntu on 2009-10-26
I had fglrx working with the -8rt kernel after some updates from Beta but it looked like the -9rt kernel had some issues trying to build the kernel modules. Then disaster struck and the whole install is kludged right now. I will be trying again soon, maybe with rc but I will probably wait for the release in a few days.

---

### Post by bluesscream on 2009-10-26
> **trulan said:**
> I think that entry is made by default when Ubuntu Studio Controls is installed or run - whichever, that line gets put there automatically if you use Ubuntu Studio Controls.
tx trulan, I figured it out: developers made genuine ubuntustudio  write this '@audio - rtprio 99' into etc/security/limits.conf by default at install :oops: Kudos!
In my defence: I was on my other machine with ubuntustudio audio compilation installed on a normal ubuntu.  There this entry is not standard and must be added by hand. Python-script ubuntustudio-controls manipulates among other things this file too but doesn't make this rtprio entry.
Now I'm really happy with ubuntustudio and my edirol fw101 and I get much better performance, less xruns, lower latencies both for synths, effects, wine-vst as well as for clean multichannel-recording then in a parallel installed widespread unappetizing os with similar environment.

---

### Post by trulan on 2009-10-27
OK, as of today the NVidia patch has made it into the main repos.  NVidia drivers 185, 173, and 96 should all work 'out-of-the-box' now on the RT kernel.

---

### Post by bluesscream on 2009-10-28
Tx trulan, prop-driver 173.14.20 form repos now works for me too on 2.6.31-9-rt :)
No issues as far. Later I'll test it's influence on audio-performance.

---

### Post by hanzomon4 on 2009-10-28
> **bluesscream said:**
> tx trulan, I figured it out: developers made genuine ubuntustudio  write this '@audio - rtprio 99' into etc/security/limits.conf by default at install :oops: Kudos!
In my defence: I was on my other machine with ubuntustudio audio compilation installed on a normal ubuntu.  There this entry is not standard and must be added by hand. Python-script ubuntustudio-controls manipulates among other things this file too but doesn't make this rtprio entry.
Now I'm really happy with ubuntustudio and my edirol fw101 and I get much better performance, less xruns, lower latencies both for synths, effects, wine-vst as well as for clean multichannel-recording then in a parallel installed widespread unappetizing os with similar environment.

What kind of latencies do you get with the edirol fa-101

---

### Post by bluesscream on 2009-10-28
> **bluesscream said:**
>  Later I'll test it's influence on audio-performance.

This repo-prop-driver patched for realtime-kernel makes me happy. I see no need to fall back to driver "nv" or "vesa" anymore. All jackd, hydrogen, zynadd.., rakarrack, ardour..., wine/wineasio/reaper/vst are running smart with best performance I ever had on this machine in ubuntustudio, my impression is even better then with the basic standard drivers.

---

### Post by bluesscream on 2009-10-28
> **hanzomon4 said:**
> What kind of latencies do you get with the edirol fa-101
I'll try to give you the numbers, but first I must sleep and do my daily work :) Hope this thread will still exist after karmic full release

---

### Post by flipper9 on 2009-10-28
> **bluesscream said:**
> I'll try to give you the numbers, but first I must sleep and do my daily work :) Hope this thread will still exist after karmic full release
This thread will be closed soon as the forum is shutting down soon.  Maybe recreate it in the general forums or some other long-term forum?

---

### Post by trulan on 2009-10-29
The Multimedia Production section (which is where this thread got moved from) would be the long-term forum of choice.  This will be preserved in the archives, so you can link to it if you need to in posting over there.

Thanks for all the discussion!

---

### Post by hanzomon4 on 2009-10-29
> **bluesscream said:**
> I'll try to give you the numbers, but first I must sleep and do my daily work :) Hope this thread will still exist after karmic full release

Deal

---

