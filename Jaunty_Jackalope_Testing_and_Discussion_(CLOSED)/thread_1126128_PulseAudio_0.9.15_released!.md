---
title: "PulseAudio 0.9.15 released!"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cl333r on 2009-04-15
Phoronix:
[http://www.phoronix.com/scan.php?page=news_item&px=NzIwMg](http://www.phoronix.com/scan.php?page=news_item&px=NzIwMg)

Looks like a lot of improvements and bug fixes. I wonder if the Ubuntu devs consider it worth including into Jaunty since PulseAudio (0.9.14) in Jaunty seems problematic so far.

---

### Post by Kosimo on 2009-04-15
> **cl333r said:**
> Phoronix:
[http://www.phoronix.com/scan.php?page=news_item&px=NzIwMg](http://www.phoronix.com/scan.php?page=news_item&px=NzIwMg)

Looks like a lot of improvements and bug fixes. I wonder if the Ubuntu devs consider it worth including into Jaunty since PulseAudio (0.9.14) in Jaunty seems problematic so far.

I guess we'll have to wait 'till the first Karmic alphas to give it a try  (unless you want to use some PPA that includes 0.9.15)

---

### Post by plun on 2009-04-15
Jaunty can also be delayed....:cool:

alsa 1.0.19, PA 0.9.15 and HDA Intel fixes for the kernel...


Just to fix those IMHO  critical errors  (despite of where Debian is and freezes)

;)

---

### Post by lithorus on 2009-04-15
I have been using PA 0.9.15 for a while now (a few months perhaps) and had absotely no issues. I hope they make an exception with this one and include it in Jaunty.

---

### Post by KhaaL on 2009-04-15
is there a PPA where i can pull this baby?

---

### Post by gnomeuser on 2009-04-15
> **KhaaL said:**
> is there a PPA where i can pull this baby?

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

---

### Post by jfernyhough on 2009-04-15
[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

Have fun. ;)

--edit
:lolflag:

---

### Post by gnomeuser on 2009-04-15
I do get some nasty sort of feedback sound with .15 it only happens I think in situations where the soundcard has been put to sleep and then woken up the noise occures for a second or so then everything is find and dandy.

---

### Post by cl333r on 2009-04-15
Wow! I installed the PPA, rebooted, and my issue with the sound is solved!
Don't know if it's due to the new PPA or just cause of reinstallation, but anyway thanks!

ps: The issue was that the keys for volume up and down stop working after I browsed through the combo which lists the audio devices. After I realized that it was broken I picked each possible device but never got it working again.

pps: I confirm "the noise that occurs for a second" but it's a minor issue and I can live well with it.

---

### Post by MaX on 2009-04-15
That worked like crap... do I need to do anything more than just log out and in again?

---

### Post by gnomeuser on 2009-04-15
One can probably work around the noise issue by disabling glitz-free mode.

from the PA glitz-free featurepage in Fedora:
To limit the problems with Alsa drivers, there is now a switch "tsched=0" for the module-hal-detect module which will disabled glitch-free mode for all sound cards globally. To use this edit /etc/pulse/default.pa and append "tsched=0" to the line "load-module module-hal-detect" 

This is the default behaviour in Jaunty for Pulseaudio and is likely to work nicer. We should still enable glitz-free for the development series with the expressed statement and a written guide on how to gather information on problematic setups. This is because these are generally not Pulseaudio bugs as everyone likes to say, these are ALSA bugs and such be fixed. We need to do this work.

---

### Post by lithorus on 2009-04-15
> **MaX said:**
> That worked like crap... do I need to do anything more than just log out and in again?
I would suggest you restart...

---

### Post by gnomeuser on 2009-04-15
> **lithorus said:**
> I would suggest you restart...

running pulseaudio -k && pulseaudio -vvvv would suffice.

People with problems migh also want to experiment with the above to disable glitz-free. If that fixes the issue then capturing the output of pulseaudio -vvvv with glitz-free enabled would be great for discovering problematic drivers.

---

### Post by stefanwa on 2009-04-15
Did anyone manage to use an Airport Express? In the PA Preferences the "Make discoverable Apple Airtunes sound devices available locally" checkbox is greyed out.
Do I need some special settings or avahi package?

Thanks

---

### Post by MaX on 2009-04-15
> **gnomeuser said:**
> running pulseaudio -k && pulseaudio -vvvv would suffice.

People with problems migh also want to experiment with the above to disable glitz-free. If that fixes the issue then capturing the output of pulseaudio -vvvv with glitz-free enabled would be great for discovering problematic drivers.

I removed the PPA and the drivers instead. I just got a lot of connection lost stuff and I did "pulseaudio -k" and "pulseaudio -D" 

I might try it out later when I have more time to fiddle. Thanks for the help!

---

### Post by paradigm2 on 2009-04-16
I am interested in installing this new version.  Does anyone have any tips on how to do this on my production 9.04 system?  As well as tips on how to prevent conflicts from occuring as a result of this (I trust I need to lock certain packages in synaptic after doing this).

I'm fairly technical and can compile from source if I have to. I've used linux off and on for over 10 years.  My problem is mainly the interdependency issues as well as not being very familiar with package management and the consequences of upgrading manually like this on a component which is so integral to the system.

Thank you.

---

### Post by paradigm2 on 2009-04-16
> **paradigm2 said:**
> I am interested in installing this new version.  Does anyone have any tips on how to do this on my production 9.04 system?  As well as tips on how to prevent conflicts from occuring as a result of this (I trust I need to lock certain packages in synaptic after doing this).

I'm fairly technical and can compile from source if I have to. I've used linux off and on for over 10 years.  My problem is mainly the interdependency issues as well as not being very familiar with package management and the consequences of upgrading manually like this on a component which is so integral to the system.

Thank you.

I think I figured it out.  Simply put in the repository from the PPA, reload, apply the upgrade.  

But does anyone have any tips for making sure this does not result in later conflicts?  I like to use synaptic for everything.  I surmise that if minor bigfixes are released this PPA will probably update them?

---

### Post by KhaaL on 2009-04-16
I have the new version of PA installed and the output is of a terrible quality. very choppy and calls in skype are barely audible unless i kill PA. could this have something to do with me using 2.6.29-020629rc8-generic kernel?

EDIT:
> **paradigm2 said:**
> 
But does anyone have any tips for making sure this does not result in later conflicts?  I like to use synaptic for everything.  I surmise that if minor bigfixes are released this PPA will probably update them?

I think you're fairly safe for now, and doubt there will be a conflict later on since ubuntu does not update important packages too often. Oh, and you did install it in the right way :)

---

### Post by paradigm2 on 2009-04-16
report:

New PA is installed, rebooted, but the low volume issue remains for me although it seems as if it might be a bit better.  I guess I may just need to look into amplified speakers...

---

### Post by jfernyhough on 2009-04-16
> **KhaaL said:**
> could this have something to do with me using 2.6.29-020629rc8-generic kernel?That likely won't help. :wink: Try 2.6.29.1 or, if you're feeling adventurous, 2.6.30-rc2.

---

### Post by xens on 2009-04-16
can someone explain the easiest way to connect a bluetooth headset? I read that this new version'll support it out of the box.

---

### Post by nystire on 2009-04-16
After installing these updates on Jaunty 64bit, I cannot run Skype. The errors I get are:
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

/usr/bin/skype.real: relocation error: /usr/bin/skype.real: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference

Does anybody perhaps know how to fix these? :$

---

### Post by paradigm2 on 2009-04-16
> **nystire said:**
> After installing these updates on Jaunty 64bit, I cannot run Skype. The errors I get are:
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

/usr/bin/skype.real: relocation error: /usr/bin/skype.real: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference

Does anybody perhaps know how to fix these? :$

Did you install all the updates from the PPA (such as Alsa) or merely a few Pulse Audio ones?

---

### Post by KhaaL on 2009-04-16
> **jfernyhough said:**
> That likely won't help. :wink: Try 2.6.29.1 or, if you're feeling adventurous, 2.6.30-rc2.

As soon as I get to patch my nvidia drivers, I'll testdrive the .30 kernel :)

---

### Post by monstrosity on 2009-04-16
What gives? I added the PPA, and it won't update. I doubled checked it and the key and it seems fine. Restarting doesn't help. 

Do I need to uninstall something, or is the PPA down for the moment?

I'm on intrepid 64.

---

### Post by paradigm2 on 2009-04-16
> **monstrosity said:**
> What gives? I added the PPA, and it won't update. I doubled checked it and the key and it seems fine. Restarting doesn't help. 

Do I need to uninstall something, or is the PPA down for the moment?

I'm on intrepid 64.

Ah, I had not noticed that you both are using 64.  I had success with 32.  Also you are using intrepid.  I believe this is intended mainly for jaunty?

---

### Post by monstrosity on 2009-04-16
Perhaps it is mainly intended for jaunty. I was able to get a volume control update out of it, but this doesn't seem to be the whole kielbasa.

Ah well. I can wait a week or two until I'm up and running on jaunty.

---

### Post by nystire on 2009-04-16
Paradigm2, I ran a 'dist-upgrade', so I basically installed everything on the PPA.

---

### Post by vlovich on 2009-04-16
Does anyone have this working with skype or wine (I'm on 64-bit but would be interested to hear if it even works in 32-bit)?

Skype:
skype: relocation error: skype: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference

Wine:
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": /usr/bin/../lib32/wine/winealsa.drv.so: symbol snd_pcm_forward, version ALSA_0.9.0rc8 not defined in file libasound.so.2 with link time reference

I've tried building my own version of the libs using source, but I haven't had any luck resolving this issue.  Any hints?

Thanks

---

### Post by nystire on 2009-04-17
vlovich, do you perhaps also get an error mesage about libcanberra-gtk-module.so? Or did you manage to solve that? If so, could you perhaps say how?

---

### Post by vlovich on 2009-04-17
i'm guessing you don't have the 32-bit compatibility libraries (ia32-libs).

apt-file is your friend.

---

### Post by nystire on 2009-04-17
$sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

Guess again? :) That was the first thing I checked.

I tried running the statically linked OSS version of skype, but that doesn't even make static on my sound card :(

---

### Post by vlovich on 2009-04-17
sorry no clue.  maybe try

LD_LIBRARY_PATH=/usr/lib32 skype

but clearly it's loading the 64-bit library instead of the 32 for some reason.  try

env

if LD_LIBRARY_PATH is set, it probably shouldn't be (look in your bashrc)

---

### Post by nystire on 2009-04-17
$ LD_LIBRARY_PATH=/usr/lib32 skype
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/bin/skype.real: relocation error: /usr/bin/skype.real: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference

It isn't set in .bashrc

Almost as if the system is overriding the path by force. Or maybe the 64bit libraries were put into lib32.

However:
/usr/lib32$ file libcanberra-gtk.so
libcanberra-gtk.so: symbolic link to `libcanberra-gtk.so.0'
/usr/lib32$ file libcanberra-gtk.so.0
libcanberra-gtk.so.0: symbolic link to `libcanberra-gtk.so.0.0.4'
/usr/lib32$ file libcanberra-gtk.so.0.0.4 
libcanberra-gtk.so.0.0.4: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped

---

### Post by stefanwa on 2009-04-17
> **stefanwa said:**
> Did anyone manage to use an Airport Express? In the PA Preferences the "Make discoverable Apple Airtunes sound devices available locally" checkbox is greyed out.
Do I need some special settings or avahi package?

Thanks

Solved it by installing pulseaudio-module-raop! Airport is being recoginzed now!

---

### Post by perspectoff on 2009-04-17
> **stefanwa said:**
> Solved it by installing pulseaudio-module-raop! Airport is being recoginzed now!

How did you do that? Like this?

These capabilities require the newest version 0.9.15 of Pulse Audio and Pulse Audio Volume Control 0.98, as well as pulseaudio-module-raop (for Airport Express). Instead of (or, as in my case, after) installing the default (0.9.14) packages from the repositories for Jaunty, obtain them by adding the repositories:

 deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main

then install:
  sudo apt-get install pulseaudio pavucontrol pulseaudio-module-raop

Then configure Pulse Audio:

    Menu -> Settings -> PulseAudio Preferences Sound Audio preferences
    -> Network Access 

and check both:

 Make discoverable network sound devices available locally
 Make discoverable Apple Airtunes devices available locally

I found I also needed:
 sudo apt-get install paprefs padevchooser

I started the PulseAudio Device Chooser:
    Menu -> Multimedia -> PulseAudio Device Chooser

This allowed the installation of the PulseAudio Device Chooser icon to my task bar. I then looked for a list of my devices:
    PulseAudio Device Chooser icon -> Manager... -> Devices

Voila! Listed under sinks (which is the PulseAudio name for outputs) was:
    raop.Base-Station-e60157.local

This is my Airport Express Base Station. I clicked on it and was able to see the Properties and set the relative volume for the output to it.

the I went back to PulseAudio Device chooser to enter this as my sink:
    PulseAudio Device chooser icon -> Default Sink... -> Other

and entered the name of my Base station (i.e. raop.Base-Station-e60157.local). 

I use Audacious, so I set Audacious to use Pulse Audio output plugin from the Preferences menu. I played a song, and it played through the stereo connected to the Airport Express.

---

### Post by nkef on 2009-04-20
> **nystire said:**
> $ LD_LIBRARY_PATH=/usr/lib32 skype
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/bin/skype.real: relocation error: /usr/bin/skype.real: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference

It isn't set in .bashrc

Almost as if the system is overriding the path by force. Or maybe the 64bit libraries were put into lib32.

However:
/usr/lib32$ file libcanberra-gtk.so
libcanberra-gtk.so: symbolic link to `libcanberra-gtk.so.0'
/usr/lib32$ file libcanberra-gtk.so.0
libcanberra-gtk.so.0: symbolic link to `libcanberra-gtk.so.0.0.4'
/usr/lib32$ file libcanberra-gtk.so.0.0.4 
libcanberra-gtk.so.0.0.4: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped

I confirm the bug too in Jaunty 64-bit
Any workaround for that issue ?

---

### Post by vlovich on 2009-04-20
Yes found one.

```

qtconfig

```

Change the type to anything but GTK or default desktop (i.e. Oxygen).

I just posted a workaround to get skype started with sound working (but I couldn't figure out how to get sound out to go through pulse - it can only go through alsa).

---

### Post by Sophont on 2009-04-20
> **nystire said:**
> 
I tried running the statically linked OSS version of skype, but that doesn't even make static on my sound card :(

You're starting that (OSS version of Skype) with padsp in front?

I used the default Skype on an old Laptop with Jaunty (fresh install - almost everything at default) and PA used > 20% CPU. Together with Skype that maxed my CPU to 100% and led to an increasing delay between when I said something and people hearing it.

I installed the OSS static Skype version and start it with "padsp skype" - making Skype work without further problems (I don't use many features though - just a conference between 6 people during gaming).

---

### Post by nkef on 2009-04-20
> **Sophont said:**
> You're starting that (OSS version of Skype) with padsp in front?

I used the default Skype on an old Laptop with Jaunty (fresh install - almost everything at default) and PA used > 20% CPU. Together with Skype that maxed my CPU to 100% and led to an increasing delay between when I said something and people hearing it.

I installed the OSS static Skype version and start it with "padsp skype" - making Skype work without further problems (I don't use many features though - just a conference between 6 people during gaming).

I am experiencing exactly the same issue as i reported in :
[http://ubuntuforums.org/showthread.php?t=1127056](http://ubuntuforums.org/showthread.php?t=1127056)

I am also experiencing high cpu-usage with 64-bit flash and virtualbox, which also are configured to route sound through pulseaudio, i will investigate the issue further.

---

### Post by barisurum on 2009-04-20
My card is a usb-audio. Here are my results:

Pulseaudio didn't produce any sound whatever I did before the ppa upgrade. After the upgrade I had a well distorted noise instead of any sound. Playback was working but unusable. So I removed anything related to pulseaudio and switched to alsa everywhere. Strangely choosing ALSA in sound preferences didn't give any result but choosing my card's name (novation DMS x-station usb audio) gave me the test sound glitch free. I also choosed ALSA with usb-audio in multimedia systems selector (default ALSA didn't work). Now when I open any movie in totem I hear a background hiss with the sound playing. I had this problem back in 8.04 but using pulseaudio as frontend removed the hiss. So anyone having a solution or a link about this? Thanks.

---

### Post by barisurum on 2009-04-20
So now I removed the libasound2 provided with the ppa upgrade hoping this would solve the hiss problem and now I have no sound with alsa at all. I can't see the default alsa option in system/prefs/sound, only usb-audio. And in multimedia systems selector I can't select alsa at all.

aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 1: XStation [XStation], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but aplay alone gives:

ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:590: audio open error: No such file or directory

What should be the problem?

---

### Post by barisurum on 2009-04-20
Ok I have installed jack and qjackctl to give it a try. JACK server works and the sound output is clean, so the problem is not with alsa as JACK uses alsa to communicate with the hardware. But before that suspends pulseaudio. The problems are related to pulseaudio.

edit: I have created the audio group and added the lines to /etc/security/limits.conf following this thread [http://ubuntuforums.org/showthread.php?t=1130383](http://ubuntuforums.org/showthread.php?t=1130383). And voila! JACK works at 5.8ms latency fluently with my usb-audio device!

---

### Post by markbuntu on 2009-04-21
No sound in flash with 0.9.15. Anyone else seeing this?

---

### Post by gnomeuser on 2009-04-21
> **markbuntu said:**
> No sound in flash with 0.9.15. Anyone else seeing this?

I also saw updates to the 32bit multilib stuff, perhaps something broke the API. I just installed the flash 64 bit flash plugin manually.

---

### Post by gnomeuser on 2009-04-21
> **barisurum said:**
> Ok I have installed jack and qjackctl to give it a try. JACK server works and the sound output is clean, so the problem is not with alsa as JACK uses alsa to communicate with the hardware. But before that suspends pulseaudio. The problems are related to pulseaudio.


Pulseaudio uses ALSA in ways we have not done before and unlike other codebases does not willingly turn into a spaghetti mess of workarounds for driver bugs. 

Before you blame Pulseaudio run it in verbose mode and see if it actually pops up with nice error messages about ALSA bugs before you say that it is not ALSA.

---

### Post by markbuntu on 2009-04-21
> **gnomeuser said:**
> I also saw updates to the 32bit multilib stuff, perhaps something broke the API. I just installed the flash 64 bit flash plugin manually.

Well I guess I will be doing that since reinstalling from the repo did not work.

---

### Post by hanzomon4 on 2009-04-21
With distorted audio you may have delete some pulseaudio files in your home folder

---

### Post by barisurum on 2009-04-21
> Before you blame Pulseaudio run it in verbose mode and see if it actually pops up with nice error messages about ALSA bugs before you say that it is not ALSA.

I'm not blaming anything or anyone's work, I just post this because someone may have a clue about the solution. And as for 9.04 rc pulseaudio is just simply unstable.

When I kill it with:

```
pulseaudio -k
```

I get sound for a while and after that all goes silent. Once after killing pulse I started tremulous (a 3d game) and the sound was present until I quitted. What could be the cause of this?

---

### Post by markbuntu on 2009-04-22
If you killed pulse and sound worked and then stopped did you check to see if pulse started up again.

autospawn=yes is set in /etc/pulse/client.conf so it will do that.

There are also lots of buggy alsa driver regressions in Jaunty which can cause your sound to inexplicably go away, partucularly if you are using snd-hda-intel. The best way to discover that is to kill pulse and run it in verbose mode as gnomeuser has suggested.

pulseaudio -vvv

---

### Post by barisurum on 2009-04-22
> If you killed pulse and sound worked and then stopped did you check to see if pulse started up again.

autospawn=yes is set in /etc/pulse/client.conf so it will do that.

Thank you mark for your answer. So if I make autospawn=no will I get sound?

I did pulseaudio -vvv here it is:

```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
I: main.c: RLIMIT_RTPRIO is set to 99, allowing real-time scheduling.
I: main.c: RLIMIT_NICE is set to 39, allowing high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux x86_64 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 38037b4f706f0dd2a462600b49eba67a.
I: main.c: Using runtime directory /home/baris/.pulse/38037b4f706f0dd2a462600b49eba67a:runtime.
I: main.c: Using state directory /home/baris/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 0 "combined" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c: Created source 0 "combined.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module.c: Loaded "module-combine" (index: #0; argument: "").
I: module.c: Loaded "module-gconf" (index: #1; argument: "").
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #2; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/baris/.pulse/38037b4f706f0dd2a462600b49eba67a:device-volumes.x86_64-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #3; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/baris/.pulse/38037b4f706f0dd2a462600b49eba67a:stream-volumes.x86_64-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=1 sink_name=alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying front:1 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:front:1 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:front:1 without SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device plug:front:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL plug:front:1
I: alsa-util.c: Unable to attach to mixer plug:front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Master" or mixer control is no combination of switch/volume.
W: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
I: module-device-restore.c: Restoring volume for sink alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 1 "alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 1 "alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1764 bytes, buffer time is 80.00ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Plug PCM: Linear conversion PCM (S24_3LE)
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3528
D: alsa-util.c:   period_size  : 441
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 441
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 7944349742681554944
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 7944349742681554944
D: alsa-util.c: Slave: Hardware PCM card 1 'XStation' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S24_3LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 24
D: alsa-util.c:   buffer_size  : 3528
D: alsa-util.c:   period_size  : 441
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 441
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_thre
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0 becomes idle.
I: module-combine.c: Configuring new sink: alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0
D: memblockq.c: memblockq requested: maxlength=16777216, tlength=16777216, base=4, prebuf=1, minreq=0 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=16777216, tlength=16777216, base=4, prebuf=4, minreq=4 maxrewind=0
I: module-stream-restore.c: Not restore device for stream sink-input-by-media-role:filter, because already set.
I: module-stream-restore.c: Restoring volume for sink input sink-input-by-media-role:filter.
I: module-stream-restore.c: Restoring mute state for sink input sink-input-by-media-role:filter.
D: module-suspend-on-idle.c: Sink alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0 becomes busy.
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
D: memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: sink-input.c: Created input 0 "Simultaneous output on XStation - USB Audio" on alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module.c: Loaded "module-alsa-sink" (index: #5; argument: "device_id=1 sink_name=alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.usb_device_1235_6_noserial_if0_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying front:1 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:front:1 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Trying plug:front:1 without SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device plug:front:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL plug:front:1
I: alsa-util.c: Unable to attach to mixer plug:front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture" or mixer control is no combination of switch/volume.
I: alsa-util.c: Using mixer control "Mic".
I: module-device-restore.c: Restoring volume for source alsa_input.usb_device_1235_6_noserial_if0_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.usb_device_1235_6_noserial_if0_sound_card_0_alsa_capture_0.
I: source.c: Created source 2 "alsa_input.usb_device_1235_6_noserial_if0_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1764 bytes, buffer time is 80.00ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 15.
I: module-alsa-source.c: Volume ranges from 0.00 dB to 22.50 dB.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Plug PCM: Linear conversion PCM (S24_3LE)
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3528
D: alsa-util.c:   period_size  : 441
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 441
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 7944349742681554944
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 7944349742681554944
D: alsa-util.c: Slave: Hardware PCM card 1 'XStation' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S24_3LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 24
D: alsa-util.c:   buffer_size  : 3528
D: alsa-util.c:   period_size  : 441
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 441
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_thresh
D: module-alsa-source.c: Requested volume: 0: 100% 1: 100%
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
D: module-alsa-source.c: Got hardware volume: 0: 100% 1: 100%
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-suspend-on-idle.c: Source alsa_input.usb_device_1235_6_noserial_if0_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #6; argument: "device_id=1 source_name=alsa_input.usb_device_1235_6_noserial_if0_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/usb_device_1235_6_noserial_if0_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/usb_device_1235_6_noserial_if0_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #7; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #8; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #9; argument: "").
I: module-default-device-restore.c: Restored default sink 'combined'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.usb_device_1235_6_noserial_if0_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #10; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #11; argument: "").
I: module.c: Loaded "module-always-sink" (index: #12; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #13; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #14; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
D: module-suspend-on-idle.c: Sink alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing input 0 "Simultaneous output on XStation - USB Audio"
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.usb_device_1235_6_noserial_if0_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.usb_device_1235_6_noserial_if0_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
```

When I tried to play the test sound this appeared among other things:

```
E: module-alsa-sink.c: Failed to set hardware parameters: Operation not permitted
```

In multimedia systems selector when pulseaudio is selected I see "unknown" in device tab under default. When I select Novation DMS Xstation usb audio (ALSA) I see usb-audio under default. When I click the test sound with this option I hear it but there is a static hiss with the sound. And other apps are either silent or give me an error when I configure them to play using ALSA (for example mplayer). And finaly when I uninstall pulseaudio completely this option gives me sound in all ALSA configured apps (not system sounds) but the sound has the same hiss in it.


any ideas?

---

### Post by markbuntu on 2009-04-22
The alsa usb driver has issues and I have been having problems with the simultaneous output myself. The gnome-volume-control-pulse totally borked that even after I uninstalled it.

Try unchecking the simultaneous output and see if pulse works better with just one device.

---

### Post by barisurum on 2009-04-22
Nope no luck with that. ```
pulseaudio
``` in terminal gives the same error:

> E: module-alsa-sink.c: Failed to set hardware parameters: Operation not permitted

I had no issues with it in 8.04. Audio with pulse was clean. I have only JACK working right now with 9.04 and if the ALSA driver is buggy how does JACK manage to handle it? The output of JACK is robust with nearly N/A xruns?? :S

---

### Post by markbuntu on 2009-04-22
The usb driver is definitely buggy. I have difficulty adjusting the levels of my usb headset in the alsa mixer. Pulse 0.9.14 is also a little buggy and not reccomended by the pulse devs for distributions, they reccomend either 0.9.10 or 0.9.15. A lot of distros have already moved to pulse 0.9.15 but that also requires alsa 1.0.19. These or later will be in Koala.

You can get them from ppas at launchpad, there is a thread around here about that. I am trying them out on my "other"jaunty install which also has KDE4.2 and UbuntuStudio. At least the ppa for 0.9.15 includes pulseaudio-module-jack so I don't have to steal it from the debian repos.

---

### Post by barisurum on 2009-04-23
So I upgraded to 0.9.15 as you suggested. I did every update themuso ppa offers and I got strange results. When I play the test sound there is a constant ugly distortion and I can't hear the note its all distorted. But with the system sounds it gets better, there are cracks in the sound but it is still recognisable. Is there a fix for this?

I also installed the new pulseaudio-module-jack. How can I use this module as default playback sink and source? Do I have to change a conf file? Thank you.

---

