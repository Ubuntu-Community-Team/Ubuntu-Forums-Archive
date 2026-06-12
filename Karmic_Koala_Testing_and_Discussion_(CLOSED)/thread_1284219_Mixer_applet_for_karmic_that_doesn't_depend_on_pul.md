---
title: "Mixer applet for karmic that doesn't depend on pulse"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by richie2.0 on 2009-10-06
The other day I upgraded to karmic from jaunty. I later ran zsnes (nintendo emulator), and it froze. After that it would freeze as soon as I loaded a rom. As I've had some trouble with pulse audio before, the first thing I tried as a remedy was to uninstall the pulseaudio package.

Now it worked again, but to my dismay the sound mixer is now gone. I filed a rather stupid bug I admit, that got closed in a matter of minutes. I hope this is a better place to resolve my issue.

I search for one of the following:
a: A sound mixer applet that lets me use my laptops volume keys, or
b: pulseaudio to not suck by stop breaking things, including stutterfree audio.

In return I offer 100 virgins in the afterlife. (not really true, but imagine...)

I looked in the repos, and tried a few mixers, but none dock to the panel. Except maybe kmix, that one I didn't try because I'm afraid it will load a ton of kde libs.

---

### Post by Taijitu on 2009-10-09
Hey there.

I'd like to add a +1 to your post, since I cannot even play video files without the sound stuttering, and the sound through VirtualBox seriously screws up...

Pulseaudio is an awesome piece of software (in principle), but so far it's just creating a lot of problems for people.

The problems could in 9.04 be solved by removing pulseaudio and using the standard alsa mixer applet for GNOME. But with 9.10 (in the beta, at least), this solution has been deprecated.

One way to avoid using pa is to install xfce4-mixer and run that to control your volume. But this solution still lacks an applet with volume key bindings.

Please just add the mixer-applet2 back into the gnome-applets-2.28.0 package as it is by standard... Or somebody please refer me to a place where I can download it... It would surely make my day :-)

---

### Post by forcecore on 2009-10-09
Current audio controller applet is best but someone should fix that pulseaudio (disabling these parts that is cause) or remove it forever. As far i have read these forums in years then looks like that lot of people suffer with audio because of that diseased pulseaudio.

I have not seen so many problems with Ubuntu audio system except sometimes rare like Wine with Windows games, Totem and flash but i forgot long time ago Totem and used only VLC or MPlayer, these will not suffer from audio problems.

Yes i can confirm that Virtualbox almost with every Ubuntu series (8.04 and up) had crackling sound so i guess that is too Pulseaudio fault or i am wrong???

---

### Post by Taijitu on 2009-10-09
I have removed pulseaudio and am using xcfe4-mixer to control my volume now, and sound in virtualbox works perfectly. And my sound problems with video persist in both Totem, MPlayer AND VLC when i use pulse... I agree that the new pulseaudio applet (technically, it's not an applet, but an icon in the status applet, but hell :-)) is fantastic and has a great settings dialog and window. A lot better than the old ones, but unfortunately, pulseaudio itself does not work for everyone yet... In karmic, problems with skype+pulseaudio have been solved, which is great. But other issues are still lagging behind.

PS: Besides this, I'm extremely happy with the Karmic beta :-)

---

### Post by tlacuache on 2009-10-09
Since I don't run pulse, I was dismayed to find out about this in Karmic as well. Here's what I did:

[LIST]
[*]installed gnome-alsamixer
[*]put a launcher for it in my panel
[/LIST]

Also, I noticed that my laptop hotkeys for volume up/down, mute, etc. didn't work. So to solve that problem I did the following:

1. Installed xbindkeys, xbindkeys-config, and xosd-bin packages
2. Created the following scripts and put them in my path:

showmute.sh
```

#!/bin/bash

mute=$(amixer -c 0 get Master|egrep  -e "Playback.*\[on|off\]"|sed -r 's/.*(on|off).*/\1/g')
echo $mute|osd_cat -o 1000 -s 2 -c darkgray -d 1 -f '-*-helvetica-*-r-*--100-*-*-*-*-*-*-*'

```

showvolume.sh
```

#!/bin/bash

volume=$(amixer -c 0 get Master|grep %|sed -r 's/.*\[(.*)%\].*/\1/'|head -n 1)
osd_cat -o 1000 -s 2 -c darkgray -d 1 -f '-adobe-helvetica-*-*-*--100-*-*-*-*-*-*-*' -b percentage -P $volume

```

3. Appended the following in my ~/.xbindkeysrc file (of course you'll have to replace my username with your username and also possibly change the names of your hotkeys, but you get the idea:
```

#alsa mute toggle
"amixer sset Master toggle; /home/tlacuache/bin/showmute.sh"
   XF86AudioMute

#alsa volume up
"amixer -c 0 set Master 2dB+ unmute; /home/tlacuache/bin/showvolume.sh"
   XF86AudioRaiseVolume

#alsa volume down
"amixer -c 0 set Master 2dB- unmute; /home/tlacuache/bin/showvolume.sh"
   XF86AudioLowerVolume

```

Now I've got a clickable launcher in my panel to bring up the graphical mixer, and I've got the ability to mute, raise, and lower alsa's volume with on-screen indicators of what I'm doing.

---

### Post by richie2.0 on 2009-10-09
Thanks tlacuache for your solution. I was thinking that it might be possible to just prevent pulse from loading in some way, do you think that's possible, or will it brake the mixer anyway? Thing is, I can use the mixer applet just fine after removal of pulse, until I log out.

-----------------

The issues with pulse is not likely to be solved, other than by using faster hardware. The thing is that pulse is quite cpu-intensive. And to reach low latencies pulse needs to have a tiny audio buffer. When audio stutter it is because that tiny buffer is not filled fast enough.

What I don't get is why alsa can do audio mixing with hardly and overhead at all, while pulse eats two-digit percentages for some streams.

Removing pulse made it possible for me to watch 720p video on my laptop, with processing power to spare.

I've noticed too, that when the buffer is empty for too long pulse craps out altogether, and makes no more sound until next reboot or suspend/resume cycle.

I've had more or less the exact same issues since pulseaudio was introduced to ubuntu, which is a very long time ago in tech years.

<rant>

It's very sad indeed that ubuntu defaults with pulse, and now makes it even harder to bypass. Combine this with the new default IM Empathy that has very poor msn support, and you get the impression that ubuntu is a playground for immature bleeding edge software. Fortunately Empathy seems to move along and looks to be a good IM pretty soon, unlike pulse will be for a sound platform.

It may sound like I'm conservative regarding new software, but I assure I'm not. I'm just reluctant to halfbaked solutions.

</rant>

---

### Post by chrisccoulson on 2009-10-09
> **richie2.0 said:**
> What I don't get is why alsa can do audio mixing with hardly and overhead at all, while pulse eats two-digit percentages for some streams.

How do you know alsa has hardly any overhead? How do you know that it doesn't have similar overhead to Pulseaudio? Remember - alsa is in kernel space, and running tools like "top" won't show you how much CPU it is using

---

### Post by Ric_NYC on 2009-10-09
What happened to pulseaudio?
Is it removed from Ubuntu?

---

### Post by richie2.0 on 2009-10-09
> **chrisccoulson said:**
> How do you know alsa has hardly any overhead? How do you know that it doesn't have similar overhead to Pulseaudio? Remember - alsa is in kernel space, and running tools like "top" won't show you how much CPU it is using

I really don't know. It's real life experience that make me assume this. It could be other issues at play of course. Still a fact that 720p video is pleasantly watchable with alsa, and a slideshow with pulse, on my hardware. Playing mp3's with pulse reports two-digit cpu usage, and cpu temp is several degrees celcius higher when using pulse. Again, cpu scaling is a factor, which perhaps could scale in a different way if load is in kernel.

As you notice, I have no hard numbers, just observations. If it looks like a duck etc..

> **Ric_NYC said:**
> What happened to pulseaudio?
Is it removed from Ubuntu?

It is NOT removed from ubuntu, and for me and others that is a problem.

---

### Post by tlacuache on 2009-10-09
This is the guide I followed for disabling pulse without uninstalling it:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

However, without pulse the default mixer applet does not work. gnome-alsamixer is the only one I've got to work so far.

> **richie2.0 said:**
> I was thinking that it might be possible to just prevent pulse from loading in some way

---

### Post by markbuntu on 2009-10-09
The problem with pulseaudio, as usual, it not so much pulseaudio itself as its implementation in ubuntu. Many necessary libs are still left out of the dependency lists so applications will work properly with pulse and some pulseaudio modules have been discarded, the udev rules are completely rewitten for reasons no one can fathom, the kernel scheduling is reduced (HZ=100, pa devs reccomend HZ=1000) resulting in higher latencies, greater cpu usage, and serious difficulties for pulse to use real time scheduling for glitch free operation.

This is a real shame as pulseaudio is becomeing so integrated into ubuntu/gnome. It is a far different experience with pulseaudio on other distros like Mandriva and Fedora. Kubuntu/KDE does not use pulseaudio at all. It has its own sound server, Phonon.

---

### Post by NRDNick on 2009-10-09
> **markbuntu said:**
>  the kernel scheduling is reduced (HZ=100, pa devs reccomend HZ=1000) resulting in higher latencies, greater cpu usage, and serious difficulties for pulse to use real time scheduling for glitch free operation.

Does this mean that we should install the -rt kernel in order to appease pulse audio's dependencies since we're using it as our main sound system? Sounds like something that would be use full information to have when first installing Ubuntu. Is it possible to install the rt kernel along side the generic one?

---

### Post by Taijitu on 2009-10-11
Okay... So i tested pulseaudio again after the 2.6.31-13 kernel got pushed out and that helped a HUGE lot on the stuttering :D. Sound through vbox is still kinda buggy, but now I can actually watch video (even 1080p x264) without the sound stuttering :).

A big thanks to the devs :D.

---

### Post by trulan on 2009-10-11
> **NRDNick said:**
> Does this mean that we should install the -rt kernel in order to appease pulse audio's dependencies since we're using it as our main sound system? Sounds like something that would be use full information to have when first installing Ubuntu. Is it possible to install the rt kernel along side the generic one?
Sure, you can install the RT kernel alongside the generic - it'll be just another entry in GRUB.  It does have the kernel hz set to 1000.  I have no idea if that will help your pulse audio issues though.  The RT kernel is getting pretty good, but it is still prone to having issues with proprietary video drivers and such.  But it shouldn't hurt to try.

---

### Post by NRDNick on 2009-10-11
Cool I might give that a shot, I've seen a few posts around about the video driver issues so it shouldn't be a problem. Thanks for the response! Are there any other benefits to running on the rt kernel other then Pulse-audio?

---

### Post by Taijitu on 2009-10-12
Disregard my last post about the .31-13 kernel... Only worked properly for a short time...

But now I've booted the rt kernel and it seems better. Will keep you posted

Update: Seems like even sound through virtualbox works now :D

---

### Post by Sandsound on 2009-10-12
> **tlacuache said:**
> This is the guide I followed for disabling pulse without uninstalling it:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

How did you get asoundconf ? it's no longer in synaptics :confused:

I tried downloading it from [bazaar.launchpad.net]("http://bazaar.launchpad.net/~motu/asoundconf-ui/asoundconf-trunk/annotate/head%3A/asoundconf") and place in in /usr/bin/ but I get errors whenever I try to set default-card.

btw. Been working on a small app I call UbuntuAudioTweaks, that uses asoundconf for different things, and I don't understand why they removed it from Karmic.
I know that the "to use Pulse or not"-debate is pointless, but at least it should be possible to choose NOT to use it

---

### Post by tlacuache on 2009-10-13
I got asoundconf from [http://bazaar.launchpad.net/~crimsun/asoundconf-ui/asoundconf-trunk/files](http://bazaar.launchpad.net/~crimsun/asoundconf-ui/asoundconf-trunk/files) and it seems to work for me:
```

tlacuache@tlacuache-laptop:E0:~$ asoundconf list
Names of available sound cards:
Intel
U0x46d0x9a1
tlacuache@tlacuache-laptop:E0:~$ asoundconf set-default-card Intel
tlacuache@tlacuache-laptop:E0:~$

```

---

### Post by Sandsound on 2009-10-13
> **tlacuache said:**
> I got asoundconf from [http://bazaar.launchpad.net/~crimsun/asoundconf-ui/asoundconf-trunk/files](http://bazaar.launchpad.net/~crimsun/asoundconf-ui/asoundconf-trunk/files) and it seems to work for me:


I can see you didn't run it with sudo, Where did you place it ?

---

### Post by AmyRose on 2009-10-14
> **chrisccoulson said:**
> How do you know alsa has hardly any overhead? How do you know that it doesn't have similar overhead to Pulseaudio? Remember - alsa is in kernel space, and running tools like "top" won't show you how much CPU it is usingALSA is the actual sound driver. Pulseaudio sits on top of it. Annoys me to no end when people talk about Pulse vs ALSA like they do the same thing.

Also... I'd really appreciate an option to have the old mixer panel applet back.

---

### Post by lazka on 2009-10-14
I use this ATM: [http://pastie.org/259660.txt](http://pastie.org/259660.txt)

Needs python-eggtray and python-alsa IIRC

---

### Post by tlacuache on 2009-10-14
I just have it in /usr/local/bin. Sorry for the confusing post, here, I'll run it as root:

```

$ sudo su -
[sudo] password for tlacuache: 
root@tlacuache-laptop:~# asoundconf set-default-card Intel
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

root@tlacuache-laptop:~# 

```

---

### Post by Sandsound on 2009-10-14
> **tlacuache said:**
> I just have it in /usr/local/bin. Sorry for the confusing post, here, I'll run it as root:

```

$ sudo su -
[sudo] password for tlacuache: 
root@tlacuache-laptop:~# asoundconf set-default-card Intel
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

root@tlacuache-laptop:~# 

```

Ok... now I understand, I just get a bit nervous when I get a warning about "unintended consequences" :-)

---

### Post by AmyRose on 2009-10-14
> **lazka said:**
> I use this ATM: [http://pastie.org/259660.txt](http://pastie.org/259660.txt)

Needs python-eggtray and python-alsa IIRCThank you so much! I second this.

The packages you need to install are python-alsaaudio and python-gnome2-extras.

More info: [http://xubuntu.wordpress.com/2007/08/15/gvtray-a-volume-control-for-your-system-tray/](http://xubuntu.wordpress.com/2007/08/15/gvtray-a-volume-control-for-your-system-tray/)

---

### Post by richie2.0 on 2009-10-19
:guitar:Thank you all for your comments. I have solved this issue in the following way:

For tray volume control I use a slightly modified version of the pastie.org script lazka provided. Speaker icon didn't show for me before, and I also extended the volume slider to the same size as the pulse volume control.

To control volume with dedicated hardware keys on my laptop I made a script myself. A simpler solution would be to call amixer directly, but I really want libnotify OSD.

I have put the files in the attachment into /usr/local/bin (need to sudo or become root)

Add volbar.py and alsavol.py in "system - settings - startup programs".
Open "system - settings - keyboard shortcuts" and add a custom shortcut key named "alsa mute" and command "/usr/local/bin/alsa_master_mute". Now assign the mute key to this command.
Repeat for "down" and "up".

Note: I have a swedish localized desktop. I'm not sure how the menu is labeled in english, but I think it's fairly accurate ;)

There may be prettier solutions, but this one works. This is an ugly hack, and it's my first pythonscript, which I didn't put more effort in than necessary for it to work.

Sidenote: Totem seems to be patched to not function with alsa. Audio is muted and grayed out. Other than that the pulse-free experience is pleasant.

---

