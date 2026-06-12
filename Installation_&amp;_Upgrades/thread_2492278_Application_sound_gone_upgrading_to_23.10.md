---
title: "Application sound gone upgrading to 23.10"
date: 2023-11-06
forum: Installation &amp; Upgrades
---

### Post by boxrec on 2023-11-06
I have lost sound in all applications (Chrome, Rhythmbox etc) but system bell still works. 

My speakers are plugged into the headphone jack

pavucontrol shows headphone as being unplugged but adjusting the volume slider I can hear the pops get louder and quieter.

using system settings I can select headphones and front right front left test works fine

When booting I can hear a pop just after it starts and another pop when the desktop shows

pactl list sinks
Ports:
		analog-output-speaker: Speakers (type: Speaker, priority: 10000, availability group: Legacy 2, availability unknown)
		analog-output-headphones: Headphones (type: Headphones, priority: 9900, availability group: Legacy 3, not available)
	Active Port: analog-output-headphones


systemctl --user status pipewire-pulse.service
&#9679; pipewire-pulse.service - PipeWire PulseAudio
     Loaded: loaded (/usr/lib/systemd/user/pipewire-pulse.service; enabled; preset: enabled)
     Active: active (running) since Mon 2023-11-06 11:34:51 GMT; 6min ago
TriggeredBy: &#9679; pipewire-pulse.socket
   Main PID: 1886 (pipewire-pulse)
      Tasks: 3 (limit: 38192)
     Memory: 12.4M
        CPU: 201ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire-pulse.service
             &#9492;&#9472;1886 /usr/bin/pipewire-pulse

Nov 06 11:34:51 john-desktop systemd[1866]: Started pipewire-pulse.service - PipeWire PulseAudio.
Nov 06 11:35:26 john-desktop pipewire-pulse[1886]: mod.protocol-pulse: client 0x56470a348950 [Google Chrome]: ERROR command:-1 (invalid) tag:2 error:25 (Input/output error)
Nov 06 11:35:29 john-desktop pipewire-pulse[1886]: mod.protocol-pulse: client 0x56470a3d6b50 [Google Chrome]: ERROR command:-1 (invalid) tag:2 error:25 (Input/output error)




On third day of trying to fix it now, any clues appreciated.

---

### Post by boxrec on 2023-11-07
Issue solved, I disabled onboard sound in the bios and bought a cheap USB Sound Card.

---

