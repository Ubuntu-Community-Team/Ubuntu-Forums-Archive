---
title: "no sound"
date: 2008-11-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2008-11-11
Has anybody had sound problems ? I have no sound since Jaunty and every reboot the speaker icon is muted. I have intel 82801DB and tried all the ones in the list but not a peep !

---

### Post by philinux on 2008-11-11
You cannot be serious this is pre alpha.  :lolflag:

---

### Post by DougieFresh4U on 2008-11-11
> **cecilpierce said:**
> Has anybody had sound problems ? I have no sound since Jaunty and every reboot the speaker icon is muted. I have intel 82801DB and tried all the ones in the list but not a peep !
Same here
> **philinux said:**
> You cannot be serious this is pre alpha.  :lolflag:

Although pre-alpha, this is the 1rst time sound has not worked in all the times I have used a pre-alpha over the last 2 years.
And yes I know the ole this is testing and blah blah should expect blah blah blah :lolflag:

---

### Post by danf_1979 on 2008-11-12
I had problems too, but they were fixed with latest upgrades. Maybe you're sources aren't updated yet, or you're out of luck :(

---

### Post by ShirishAg75 on 2008-11-12
> **cecilpierce said:**
> Has anybody had sound problems ? I have no sound since Jaunty and every reboot the speaker icon is muted. I have intel 82801DB and tried all the ones in the list but not a peep !

same here, let's just keep track of the updates.

---

### Post by philinux on 2008-11-12
It's fixed here now. But check the sliders in your controller.

---

### Post by ShirishAg75 on 2008-11-12
> **philinux said:**
> It's fixed here now. But check the sliders in your controller.

what controller?

---

### Post by DougieFresh4U on 2008-11-12
> **philinux said:**
> It's fixed here now. But check the sliders in your controller.

Let me ask what do you have your sound set at in 'System>Preferences>Sound'?
Autodetect or Alsa?

---

### Post by philinux on 2008-11-12
Sound is set to the default of pulse audio. Alsa does not work. Autodetect does.

---

### Post by ShirishAg75 on 2008-11-12
> **DougieFresh4U said:**
> Let me ask what do you have your sound set at in 'System>Preferences>Sound'?
Autodetect or Alsa?

System > Preferences > Sound is same as gnome-sound-properties. 

I did try testing and while testing works, no sound coming out. 

Philinux again, what controller are you talking about?

---

### Post by cecilpierce on 2008-11-12
ShirishAG75,
Right click on the speaker icon in the panel and select "Open Volume Control"

---

### Post by ShirishAg75 on 2008-11-12
> **cecilpierce said:**
> ShirishAG75,
Right click on the speaker icon in the panel and select "Open Volume Control"

Ah, he calls the speaker volume as controller.

---

### Post by Kevbert on 2008-11-12
Sound is a bit unstable at present (please take a look at this [[COLOR="Red"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=978393")).

---

### Post by jerrylamos on 2008-11-12
Mine is still deader than a doorknob.  It worked before the updates.  I'm current on Jaunty updates now.

IBM Thinkpad R31, 
description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

At least the display still works.  

Jerry

---

### Post by ronacc on 2008-11-12
still dead here as of 23:00 nov 12 east coast US .

---

### Post by cecilpierce on 2008-11-13
Still not working here or in Intrepid, Mandriva's pulse sound works fine.

---

### Post by plun on 2008-11-13
Pulseaudio broke for me and also for others a week ago, 32 bit.

Also libasound as I recalls it.


What gives this:

```
pulseaudio -k; sleep 5; pulseaudio -vv
```

Also check settings:

```
alsamixer -Dhw
```


I switched to PAs GIT...

---

### Post by Kevbert on 2008-11-13
It looks like it's a kernel problem (rather than just Jaunty) as more and more people are reporting similar sound problems in Intrepid.

---

### Post by philinux on 2008-11-13
Maybe it's a card issue. Mines integrated.
 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

Sound still working although the slider for front refuses to stay set to full. On reboot is down ti min.

---

### Post by cykotiktek on 2008-11-13
Yah i am in the same boat no sound here either.

---

### Post by ronacc on 2008-11-13
it don't seem to me that it is card related , looking in this and another thread also the bug report , it affects both 32 and 64 bit and many cards from different mfg's .

---

### Post by jerrylamos on 2008-11-14
Jaunty is still "dumb" as in deaf, dumb, and blind.  I do updates every day and still nothing.

Why does the Gnome Desktop set mute, volume 0 on every boot, no matter what I set it to?  Why can't it remember settings?

Anyway, I put on updates every day, check to see it is still "dumb", do a couple other checks, then go right back to the Intrepid boot so I can hear the news videos.

Confused, Jerry

p.s. IBM Thinkpad, Intel 82801CA/CAM Audio Controller

---

### Post by philinux on 2008-11-14
I'm confused as to why sound is working for me. Are there any commands I can use to show why it's working for me. Maybe help solve the mystery.

---

### Post by Kevbert on 2008-11-14
Have a look at /var/log/user.log and user.log.0 
There should be a load of pulseaudio errors there.
I've added my log to the bug [[COLOR="SandyBrown"]report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/296738").

---

### Post by ronacc on 2008-11-14
this thing seems to be a multiheaded monster , my symptoms are different but the result is the same , no sound . my sliders are not set to zero , nothing is muted and there is no mention of any kind of audio in my user.log since nov 8 and I get a slightly different error message when I test sound with pulse-audio than with alsa or autodetect .pulse-audio says "...connection refused" 
while the others say "...unable to connect".

---

### Post by philinux on 2008-11-14
Here's a snip from my log. And sound [COLOR=Red]**is **[/COLOR]working. :confused:
```
Nov 13 11:47:17 philinux-desktop pulseaudio[5511]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 13 11:47:17 philinux-desktop pulseaudio[5513]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 13 11:47:17 philinux-desktop pulseaudio[5513]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 13 11:47:17 philinux-desktop pulseaudio[5513]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Nov 13 11:47:17 philinux-desktop pulseaudio[5513]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 13 11:47:31 philinux-desktop pulseaudio[5513]: module-x11-xsmp.c: X11 session manager not running.
Nov 13 11:47:31 philinux-desktop pulseaudio[5513]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 13 11:48:41 philinux-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov 13 11:48:42 philinux-desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov 13 11:58:48 philinux-desktop bonobo-activation-server (philinux-6721): could not associate with desktop session: Failed to connect to socket /tmp/dbus-u8m9jCC0ci: Connection refused
Nov 14 11:25:00 philinux-desktop pulseaudio[5525]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 14 11:25:00 philinux-desktop pulseaudio[5527]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 14 11:25:00 philinux-desktop pulseaudio[5527]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 14 11:25:00 philinux-desktop pulseaudio[5527]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Nov 14 11:25:00 philinux-desktop pulseaudio[5527]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Nov 14 11:25:15 philinux-desktop pulseaudio[5527]: module-x11-xsmp.c: X11 session manager not running.
Nov 14 11:25:15 philinux-desktop pulseaudio[5527]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 14 11:26:32 philinux-desktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov 14 11:26:34 philinux-desktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
```

---

### Post by xebian on 2008-11-14
Mine is working too.  However PA is not installed, only libpulse0.  I wasn't happy with Intrepid so upgraded to Jaunty, and it"s like Intrepid++ until perhaps the major update.

---

### Post by plun on 2008-11-14
> **philinux said:**
> Here's a snip from my log. And sound hp: 

Well.. I posted the magic commands earlier...

```
sudo apt-get install ubuntu-desktop
```

and

```
aplay -l
```

are also good ones....

---

### Post by ronacc on 2008-11-14
@ plun . following you're suggestions , my problem atleast seems to be a dependency problem with pulseaudio , pulseaudio won't install because it is looking for libpulsecore5 and libpulsecore7 is what is actualy installed . that dosen't explain why alsa don't work but atleast it shows why pulse won't .I didn't switch to the git version of pulse because atleast at the start I wanted to keep things "stock".

---

### Post by plun on 2008-11-14
> **ronacc said:**
> @ plun . following you're suggestions , my problem atleast seems to be a dependency problem with pulseaudio , pulseaudio won't install because it is looking for libpulsecore5 and libpulsecore7 is what is actualy installed . that dosen't explain why alsa don't work but atleast it shows why pulse won't .I didn't switch to the git version of pulse because atleast at the start I wanted to keep things "stock".

Ok...

We are probably in a situation where Intrepids patch totally broke.

PulseAudio 0.9.13 build broke a week ago and also Libasound as I recalls it.

I compiled both PA ver . 14  and Alsa.

Maybe its enough to compile new alsa-plugins  ????

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

It was "mission impossible" to build  ver .13 also for myself so something is totally broken.

Maybe also Luke is away for the moment  :confused:  the ppa is still Intrepid and nothing is changed.

---

### Post by DougieFresh4U on 2008-11-14
> **plun said:**
> Well.. I posted the magic commands earlier...

```
sudo apt-get install ubuntu-desktop
```

and

```
aplay -l
```

are also good ones....
```
dougie@DougiesLeanMachine:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: pulseaudio but it is not going to be installed
                  Recommends: firefox-gnome-support but it is not going to be installed
```
E: Broken packages

> **ronacc said:**
> @ plun . following you're suggestions , my problem atleast seems to be a dependency problem with pulseaudio , pulseaudio won't install because it is looking for libpulsecore5 and libpulsecore7 is what is actualy installed . that dosen't explain why alsa don't work but atleast it shows why pulse won't .I didn't switch to the git version of pulse because atleast at the start I wanted to keep things "stock".

I am getting the same messeges regarding pulseaudio as you are getting
I am glad you have been keeping an eye on it, as I was thinking I did some thing wrong in regards to my sound broken :)

---

### Post by plun on 2008-11-14
Well. I am not happy with this solution but "the gurus" also seems to be away

> **PulseAudio Removal**

If you decide you no longer like PulseAudio and would like to disable it: Remove the added lines to /etc/asound.conf If /etc/asound.conf did not exist when you installed PulseAudio, you may remove /etc/asound.conf entirely.

After this, you may remove all of the installed PulseAudio packages.

To disable pulseaudio in hardy you need to select alsa for for all options in **/system/preferences/sound** 

**[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)**



PA can be a "pig" to compile and I also needed a patch for GIT version.

---

### Post by DougieFresh4U on 2008-11-14
Does removing 'pulseaudio' bring back sound?
If not, I shall leave well enough alone.

---

### Post by cykotiktek on 2008-11-14
I have tried to remove pulsaudio and reinstall it but i still have no sound.

---

### Post by plun on 2008-11-14
> **cykotiktek said:**
> I have tried to remove pulsaudio and reinstall it but i still have no sound.

What gives this commmand ?

```
aplay -l
```


I cannot understand what blocks sound if PA is removed...:confused:


psyke83, where are you  !!! :)
.
.

---

### Post by cykotiktek on 2008-11-14
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by ronacc on 2008-11-14
here is the output from my aplay -l
```
ron@ron-desktop3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ron@ron-desktop3:~$ 

```

I am going to stick with the "stock" install so I can track this bug , I don't "need" sound on my test box right now so it poses no problem . The output from when I tried apt-get ubuntu-desktop is the same as DougieFresh4U

@DougieFresh4U nothing you did, it broke for everbody a few days ago  , now its back for some but not others .

---

### Post by DougieFresh4U on 2008-11-14
> **plun said:**
> 

```
aplay -l
```

 :)
.
.

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by pferraro on 2008-11-14
I dunno about you all, but with the snd-hda-intel driver, I was able to restore my sound by checking the "Headphone" and/or "Speaker" options in the Switches tab of the Volume Control applet (you may need to enable these in preferences to get them to show up).  Unfortunately, these switches (as well as the PCM volume) do not hold their values between reboots.

---

### Post by plun on 2008-11-14
> **ronacc said:**
> here is the output from my aplay -l
```
ron@ron-desktop3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ron@ron-desktop3:~$ 

```

I am going to stick with the "stock" install so I can track this bug , I don't "need" sound on my test box right now so it poses no problem . The output from when I tried apt-get ubuntu-desktop is the same as DougieFresh4U


Ok this is mine

```
plun@plun:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
<cut>
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
<cut>
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [Microsoft Digital Sound System ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```


This can take time.... the best howto for sound is this one.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Its still a mystery for me....(if PA is removed)

---

### Post by ronacc on 2008-11-14
completly off topic but here are 2 pics from my front yard of the spaceshuttle endevor lifting off a few minutes ago , I am about 80KM west of cape caneveral . the shuttle is the orange glow on the left, the white glow on the right is the full moon.enjoy :)

---

### Post by ShirishAg75 on 2008-11-15
> **pferraro said:**
> I dunno about you all, but with the snd-hda-intel driver, I was able to restore my sound by checking the "Headphone" and/or "Speaker" options in the Switches tab of the Volume Control applet (you may need to enable these in preferences to get them to show up).  Unfortunately, these switches (as well as the PCM volume) do not hold their values between reboots.

Wish I had read this one before filing this bug [lpbug]298301[/lpbug] . 

also filed a wishlist bug for having a status in /etc/init.d/pulseaudio [lpbug]298299[/lpbug]

---

### Post by Kevbert on 2008-11-15
> **ShirishAg75 said:**
> Wish I had read this one before filing this bug [lpbug]298301[/lpbug] . 

also filed a wishlist bug for having a status in /etc/init.d/pulseaudio [lpbug]298299[/lpbug]

Thanks for the links. Clicked on affects me too (I don't know if that helps).

---

### Post by BwackNinja on 2008-11-15
/etc/init.d/pulseaudio is pretty much not used at all, it is only used when you're running pulseaudio as a system-wide daemon which is not the default (which for some reason I can't get to work right now...but anyway) "pactl stat" tells you if pulseaudio is running plus some other info.

---

### Post by autocrosser on 2008-11-15
ronacc--I have "almost" same output & my sound is ok--

dean@linux:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dean@linux:~/Desktop$ 

I goto ALSA mixer & everything is muted on a reboot--I get sound if I unmute "Side" & "Centre" ????????

Cheers!!!!


> **ronacc said:**
> here is the output from my aplay -l
[code]ron@ron-desktop3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ron@ron-desktop3:~$ 
.

---

### Post by ronacc on 2008-11-15
@autocrosser I can't get to alsamixer it errors. I have everything set to alsa but still get this when I try to invoke alsamixer.
```
ron@ron-desktop3:~$ alsamixer
E: socket-client.c: socket(): Address family not supported by protocol
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
ron@ron-desktop3:~$ alsamixer
E: socket-client.c: socket(): Address family not supported by protocol
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
ron@ron-desktop3:~$ 

```

---

### Post by autocrosser on 2008-11-15
Hummmmm---I have everything set for <auto detect> & am using pulse--My alsamixer just shows pulse settings--I forgot to say that I have Gnome Alsa Mixer also installed & that is what I have been changing to get sound...

You might try it & see--install Gnome alsa mixer & change back to defaults.....

---

### Post by ronacc on 2008-11-15
ok tried that , gnome alsa mixer atleast comes up , nothing is muted , reset everything to autodetect , still no sound . I think the problem is a mixup somewhere in my dependencies , I do not have pulseaudio installed because it won't install , it bitches about wanting libpulsecore5 when libpulsecore7 is what is installed . if I try to install libpulsecore5 it wants to  remove everything else having to do with pulse . This is just my upgraded Ibex install since jaunty A1 isn't out yet ao I may have some stuff leftover from monkeying with pulse when it also crapped out early in Ibex . When A1 comes out I'll install that and see what happens .Thanks

---

### Post by DougieFresh4U on 2008-11-15
> **ronacc said:**
> @autocrosser I can't get to alsamixer it errors. I have everything set to alsa but still get this when I try to invoke alsamixer.
```
ron@ron-desktop3:~$ alsamixer
E: socket-client.c: socket(): Address family not supported by protocol
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
ron@ron-desktop3:~$ alsamixer
E: socket-client.c: socket(): Address family not supported by protocol
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused
ron@ron-desktop3:~$ 

```
I don't have pulse installed as it gives the same 'bitchin' you get about dependency drama.

---

### Post by autocrosser on 2008-11-15
Interesting---this is a "fresh" ibex install--with all the Jaunty updates--I remember getting the "bitchin" about libasound a while back (week & 1/2 ago) & then it installed--My users /home is the same one from Ibex---It's strange that my updated Ibex testing is working ok also--it was installed around Ibex Alpha 3~4 & I didn't play around very much with pulse on that one-----

The install I did play around with is the one I nuked to be fresh for Jaunty testing.....

I guess that I would suggest you try a fresh 8.10 install without mods & update it to see if the problem goes away....

I have a storage drive that I alias my /var/cache/apt/archives to--that way I can reinstall very quickly without having to re-d/l all the current testing stuff--it is the central /archive for both of my computers---the wonders of networked storage drives ;)

---

### Post by ronacc on 2008-11-15
I was right , I had "messed" with pulse audio back during intrepid then when I "upgraded to jaunty I pruned all of the ppa's out of my sources.list , I added this ppa back in .
```
deb http://ppa.launchpad.net/themuso/ubuntu intrepid main
deb-src http://ppa.launchpad.net/themuso/ubuntu intrepid main

```
that made a newer version of pulse available that would install . I still dont get sound with alsa but if I select pulseaudio and unmute everything I do have sound now . I didn't do a freshinstall of ibex before I moved to jaunty because I am intending to do a fresh install of A1 so basicly I shot myself in the foot by pruning the ppa's .

---

### Post by autocrosser on 2008-11-15
Good to hear you have sound again!!!

I'll be running this install until (if?) it "blows-up"--I have my second install as a backup (will be updating it tonight or tomorrow--I keep it a week back & bring it forward every Sat/Sun)--If my main stays good til Alpha 4, I'll think about reinstalling the backup with Alpha 4 or 5 & turning this one into the backup---I alternate the two testing installs so that neither one is more that 4 or 5 back (installed) from the current one......that way I don't get the "cruft" from a install that is updated from too long ago........

I hit upon the three install thought a while back--I have two "fall-back" installs in case of problems--one spare testing so I can figure out what went wrong--If both testing blow-up--I still have a Hardy in reserve--it sure looks old now ;)

---

### Post by ronacc on 2008-11-15
I do my testing on a seperate box , sometimes I do a fresh install of the previous release then upgrade sometimes I do the fresh install at A1 , I was figuring on going that route this time so I didn't bother with a fresh intrepid , I was afraid that might bite me because I had monkeyed so much with intrepid early on ( see my sig:lolflag: ) .I may take this opertunity to do some major "housecleaning" on the testbox it's a real kluged up mess .

---

### Post by DougieFresh4U on 2008-11-15
> **ronacc said:**
> I was right , I had "messed" with pulse audio back during intrepid then when I "upgraded to jaunty I pruned all of the ppa's out of my sources.list , I added this ppa back in .
```
deb http://ppa.launchpad.net/themuso/ubuntu intrepid main
deb-src http://ppa.launchpad.net/themuso/ubuntu intrepid main

```
that made a newer version of pulse available that would install . I still dont get sound with alsa but if I select pulseaudio and unmute everything I do have sound now . I didn't do a freshinstall of ibex before I moved to jaunty because I am intending to do a fresh install of A1 so basicly I shot myself in the foot by pruning the ppa's .
Thanks for your very helpful post. I did what you did and sound is back.
but hopefully what ever caused all this drama will get itself worked out

---

### Post by autocrosser on 2008-11-15
Understand--This is my main unit--so I evolved a way that under "almost" all conditions I still have a working install on it---I remember back during Gutsy testing I had a "stable" install of Feisty--My Gutsy blew-up & I went to Feisty that I had not updated for a couple of months & it blew-up right after updates--

I was royally f'***d & found it was easier to fix Gutsy ;)---in any case, I decided after that to do everything in threes--not had a problem (knock on wood) after that. And when I bought a separate networked storage for file backup--everything became MUCH easier--nice to have a central storage for docs. archives, etc---

I still mirror everything between my main unit & the storage drive--currently have over 2TB available between the various units in my system. Insurance policy.......

---

### Post by ronacc on 2008-11-15
I had so many disasters during testing that I just don't test on my main box at all . after one disaster where the installer went berzerk and formated evrey drive on the box ( thank god for offline backups) I said enough and built up a box I dedicate just to testing .ofcourse not long after that I had a harddrive fail on the main box :confused: oh well you can't win em all.

---

### Post by autocrosser on 2008-11-15
You'll like the backup I got!!!! Embedded linux--500GB storage--works very well. You can expand it with external USB2 drives.....

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3601883&CatId=2671](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3601883&CatId=2671)

---

### Post by ronacc on 2008-11-16
that looks interesting , a bit of overkill for my needs right now but I'll keep it in mind .

---

### Post by jerrylamos on 2008-11-18
Someone must have tweaked it.  This is a VIA motherboard, 1.2 gHz Celeron.  Jaunty via sources.list and updated as of a couple days ago, sound worked O.K.  

Got the usual fatal notification of updates on the top line of the screen, the downward pointing arrow with an !  in it. 

Sucked in, I did the Ubuntu recommended action.  

Sound died.

Alpha's coming, hang on to my hat.

Jerry

p.s. If it aint broke, don't fix it.  The fix broke it.

---

### Post by super.rad on 2008-11-19
I lost all sound recently when upgrading to jaunty but managed to solve the problem by opening volume control and in preferences making sure everything was ticked and then unmuting any that were muted

---

### Post by ShirishAg75 on 2008-11-20
with today's updates sound died at my end too :(

---

### Post by psyke83 on 2008-11-20
> **ShirishAg75 said:**
> with today's updates sound died at my end too :(

There's something strange going on with ALSA (no, not PulseAudio). It seems that upon every reboot, the mixer settings are all getting muted and set to 0% volume. I haven't had time to investigate properly yet.

---

### Post by cecilpierce on 2008-11-20
If you find anything out please let me know.
Sound is messed up in Intrepid and Jaunty.
No login, logout error, alert or anything in the
sound preferences work. I have Mandriva and its using pulse audio, every sound works ! I'm going to try alpha 1 and see if mabe I messed up something.

---

### Post by ShirishAg75 on 2008-11-24
I did updates and then sound came back from that session. The next session sound died again. I tried gnome-sound-properties and have been using ALSA for everything other than capture (I don't have a capturing device)

This is the error which comes. 

```

$ gnome-sound-properties

(gnome-sound-properties:8317): sound-properties-WARNING **: Bad setup, install the freedesktop sound theme
sound-properties-Message: Error running pipeline 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink': Could not get/set settings from/on resource. [gstalsasink.c(523): set_hwparams (): /GstPipeline:pipeline0/GstGConfAudioSink:gconfaudiosink0/GstBin:bin0/GstAlsaSink:alsasink0:
Unable to set hw params for playback: Invalid argument]

```

This is what lspci shows :-

```

$ lspci | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

```

I also have a TV-Card which isn't supported as eeprom therein is absent, although it also has the same chipset 

```

[   27.587403] saa7130[0]: board init: gpio is 38500
[   27.768940] saa7130[0]: Huh, no eeprom present (err=-5)?
[   27.772592] saa7130[0]: registered device video0 [v4l2]
[   27.773491] saa7130[0]: registered device vbi0
[   27.813955] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   27.814076] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   27.863866] saa7134 ALSA driver for DMA sound loaded

```

---

### Post by BwackNinja on 2008-11-25
Problem fixed. Was in alsa-utils. alsactl wasn't  in /sbin. Updates took care of it.

---

### Post by ShirishAg75 on 2008-11-25
That didn't fix for me (unfortunately) 

Although I filed another small design bug [lpbug]302259[/lpbug]

What I am more interested to know for now is let's say I delete the contents of /var/lib/alsa/asound.state would it recreate the contents of the same in next boot or no?

---

### Post by BwackNinja on 2008-11-25
Yup, recreates contents. Been there, done that.

---

### Post by ShirishAg75 on 2008-11-26
no idea when it gets fixed :(

---

### Post by Kevbert on 2008-11-26
Sound settings finally work for me and the sound settings don't get minimized on reboot...but now I get no sound whatsoever when I run test in the Sound - Devices Tab...so it's still not fixed.

---

### Post by ShirishAg75 on 2008-11-26
The only thing which I see got fixed is that audio is not muted, other than still no joy with audio. So its still not fixed at my end as well.

---

### Post by jerrylamos on 2008-11-26
Applications Sound & Video Pulse Audio Device Chooser puts an applet on the top line.

Selecting the applet, choose volume control

Shows volume up at max however the loudspeaker icon on output devices shows mute.  Click on hardware output device and it shows

No Output Device Available.

Strange, Hardy & Intrepid Release code plays fine.  Compaq Presario 3.3 gHz Celeron
Jerry

---

### Post by Gina on 2008-11-27
Well, I've tried all all available permutations of devices and settings both ALSA and PA and nothing gives me any sound out of Jaunty on my AMD64(64bit) or laptop(32bit).  Intrepid is fine.

---

### Post by philinux on 2008-11-27
Just installed 64 bit. Tried sound and no errors but no sound. Opened the volume control up and master and pcm where 100% but Front was very low. Slid the slider up and hey presto sound is fine.

---

### Post by Gina on 2008-11-27
Well...  I installed some updates and rebooted.  Set all the sound to Pulse Audio, found the Front volume on nil and moved it up - and - viola! - we have sound :)

Sound in Jaunty 64bit on AMD64 machine is now working fine :):)

---

