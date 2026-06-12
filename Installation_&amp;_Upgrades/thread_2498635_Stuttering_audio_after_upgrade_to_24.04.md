---
title: "Stuttering audio after upgrade to 24.04"
date: 2024-06-22
forum: Installation &amp; Upgrades
---

### Post by peyre on 2024-06-22
Canonical decided for some unfathomable reason to put the 24.04 upgrade back more than halfway to the next release, so on my laptops I forced the upgrade with **sudo do-release-upgrade -d**.  That's fine on my laptops because they'd be easy to reinstall from scratch if need be - but my desktop is another matter.  I wanted to hold off until the official release was available.

However, a project I'm involved with ([Raceintospace]("https://github.com/raceintospace/raceintospace")) now requires an updated version of CMake, which isn't available on 22.04 LTS, so I had to upgrade to 24.04.  It upgraded just fine and everything's working great, except certain things now have a sort of stuttery sound.  Audacious plays flawlessly, VLC plays movies just fine, etc.  However, the Raceintospace game now has stuttery sound.  I thought it was the game, until I opened LOTRO, and the music is kind of stuttery there too (less pronounced than in RIS, but definitely there).  

I've tried to record this stuttering in RIS, but as soon as I tell OBS Studio to record, the stuttering stops and the sound is just fine again.  I tell it to stop recording, and the stuttering resumes.  It's the strangest thing!  Anyone have any idea?  Is it maybe a problem with PulseAudio or something?

---

### Post by #&amp;thj^% on 2024-06-22
There was a workaround that jbicha had posted if you wan to give it try:
There was another workaround in the upstream bug:

```

systemctl edit --user wireplumber.service
```

Add this then save the file and exit:

```

[Service]
ExecStartPre=/bin/sleep 1
```

(And if one second isn't long enough, you could try a larger number.) I'm using "3" ATM
```
### Editing /home/me/.config/systemd/user/wireplumber.service.d/override.conf
### Anything between here and the comment below will become the contents of the drop-in file

ExecStartPre=/bin/sleep 3

### Edits below this comment will be discarded


### /usr/lib/systemd/user/wireplumber.service
# [Unit]
# Description=Multimedia Service Session Manager
# After=pipewire.service
# BindsTo=pipewire.service
# Conflicts=pipewire-media-session.service
#
# [Service]
# LockPersonality=yes
# MemoryDenyWriteExecute=yes
# NoNewPrivileges=yes
# SystemCallArchitectures=native
# SystemCallFilter=@system-service

```
I'm curious to see how this works or not for your use.  I still see a few race conditions though.

Sound and Video is at best in beta stage for Buntu flavors.....Sigh

---

### Post by peyre on 2024-06-22
Thanks for the suggestion!  It doesn't seem to have fixed it though, either at 1 or 3.

---

### Post by #&amp;thj^% on 2024-06-22
Your not alone: [https://askubuntu.com/questions/1515712/stuttering-audio-after-fresh-24-04-install](https://askubuntu.com/questions/1515712/stuttering-audio-after-fresh-24-04-install)
*Rumors* are is a fix is coming at some point soon.
One Bug report: [https://bugs.launchpad.net/ubuntu/+source/pipewire/+bug/2063150](https://bugs.launchpad.net/ubuntu/+source/pipewire/+bug/2063150)

---

### Post by peyre on 2024-06-22
Oh so it's not just me!  Thanks, good to know.  I was toying with the idea of wiping and reinstalling from scratch, and wasn't looking forward to that.

---

### Post by #&amp;thj^% on 2024-06-22
If your adventurous some had a fix with:
> Martin Vysny (vyzivus) wrote on 2024-05-09: 			#9

Blacklisting snd_soc_avs. (i.e. add this line: blacklist snd_soc_avs to /etc/modprobe.d/blacklist.conf) fixing the problem for me.


---

### Post by peyre on 2024-06-26
Thanks!  I added that and rebooted, but same problem.  Well, it was worth a try.

---

### Post by 909mjolnir on 2024-06-29
Maybe the new pulseaudio defaults are crazy.  Or maybe pipewire got installed.  
i'm not sure what to tell you.  I fuss with audio buffers all the time for my Digital Audio Workstation.  

Maybe post up a messages over at the Cockos Reaper forums in some section mentioning Linux.  They fuss with audio buffers there a lot, and would know which settings for you might be golden.  I only know my own system and some pro audio optimizations, but those aren't for everyday desktops.  

But I can tell you that the PulseAudio devs are kinda dorky because the default settings are the worst of both pro and consumer and prosumer.  They didn't set the buffers correctly to accommodate anybody, and yet they shoved in bluetooth audio support too (which I wouldn't wish on my worst enemies).  
I would try to do a more direct support for you, but I'm on Arch Linux instead of Ubuntu flavors.

---

### Post by peyre on 2024-07-04
My mistake, incidentally - it is affecting other sound and music, just to differing degrees.

---

### Post by him610 on 2024-07-06
> Maybe the new pulseaudio defaults are crazy. Or maybe pipewire got installed.

My audio works. It seems like pulseaudio has a substitute, look at Server-2
```
$ inxi -Axxz
Audio:
  Device-1: AMD driver: snd_hda_intel v: kernel bus-ID: 00:01.1
    chip-ID: 1002:15b3
  Device-2: AMD Family 15h Audio vendor: Conexant Systems
    driver: snd_hda_intel v: kernel bus-ID: 00:09.2 chip-ID: 1022:157a
  Device-3: Generalplus USB Audio Device
    driver: hid-generic,snd-usb-audio,usbhid type: USB rev: 1.1 speed: 12 Mb/s
    lanes: 1 bus-ID: 2-3:3 chip-ID: 1b3f:2008
  API: ALSA v: k6.8.0-36-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active
  Server-2: PulseAudio v: 16.1 status: off (using pipewire-pulse)

```

---

### Post by peyre on 2024-07-07
That's almost what I have.  In particular, my Server-2 looks just the same.
```
$ inxi -Axxz
Audio:
  Device-1: Intel NM10/ICH7 Family High Definition Audio
    vendor: Gigabyte GA-D525TUD driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
    chip-ID: 8086:27d8
  Device-2: AMD Baffin HDMI/DP Audio [Radeon RX 550 640SP / 560/560X]
    driver: snd_hda_intel v: kernel pcie: speed: 2.5 GT/s lanes: 8
    bus-ID: 01:00.1 chip-ID: 1002:aae0
  API: ALSA v: k6.8.0-36-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active
  Server-2: PulseAudio v: 16.1 status: off (using pipewire-pulse)

```

---

### Post by oiowise19 on 2024-11-13
Hello,


I had the same issue with my jbl earphones, everything was working great on ubuntu 22 / linux mint 21 but once i upgraded to mint 22 / ubuntu 24, the sound is stuttering and choppy. I tried a lot of suggestions on the forums but nothing changes.


The solution for me was to :


1) Disable my normal wifi (2.4 Ghz) and keep only the 5GHZ (SSID_5GHZ) through my router config interface.
2) Change the priority of pipewire, pipewire-pulse, wireplumber to high using the system monitor (right click, change priority ...).
3) Exit blueman-manager completely and reboot my laptop. (log out was not enough for my case).


Please let me know if this helps.


Kind regards

---

### Post by peyre on 2024-11-13
Thanks oiowise!  It seemed to resolve itself over time, likely with an update.  I've since wiped the drive and reinstalled from scratch as well, and am having no audio problems now either.

---

