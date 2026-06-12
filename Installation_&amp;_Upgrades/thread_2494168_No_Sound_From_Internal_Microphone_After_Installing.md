---
title: "No Sound From Internal Microphone After Installing Mantic Minotaur"
date: 2024-01-07
forum: Installation &amp; Upgrades
---

### Post by zashinoff on 2024-01-07
Hi All,

I would appreciate any help/assistance you can offer me.

I had a working internal microphone for the last several months when I was using Jammy Jellyfish, but then all of a sudden there was no sound coming from my internal mic (in settings it's digital microphone). Don't know what caused this. So I did a fresh install of Mantic Minotaur hoping it would resolve the issue. It didn't. My sound/speakers are working fine, my webcam is working fine, it's just the mic that's not working. The system is detecting the microphone, under settings, the input device is: "Digital Microphone - Tiger Lake-LP Smart Sound Technology Audio Controller". But there is no sound coming from it. When I try and speak, I can't hear anything. The volume is turned up (I checked in settings).

Can anyone please offer any help?

I am using the MSI Prestige 14 Evo laptop from 2020.

Thank you in advance :-)

---

### Post by #&amp;thj^% on 2024-01-07
Have you tried this yet?
```
sudo alsactl -F restore 

```
That command reloads the driver for your sound card. The -F option forces the restoration of the sound card state, and restore is used to load the driver.

---

### Post by zashinoff on 2024-01-07
Thanks for the advice, but unfortunately, it didn't resolve the issue :-/

Do you have any other ideas? Is there any line(s) I need to be adding to my alsa-base.conf file by any chance that could help?

---

### Post by #&amp;thj^% on 2024-01-07
The only other thing that comes to mind is "alsamixer" run it in the terminal and check if it was muted.
Sound has been a bit hit and miss form 22.04 to current.

---

### Post by zashinoff on 2024-01-07
In alsamixer my card and chip are both "Pipewire", and there's only one "Master" volume showing. There are no controls for anything else.

---

### Post by #&amp;thj^% on 2024-01-07
Press "F6" that should show you more.

EDIT: Please add this in your next post:
```
inxi -Axxz

```

---

### Post by zashinoff on 2024-01-07
Ok, so I tried pressing F6, and it turned out that my microphone was muted (it said "MM"), so I unmuted it, turned up the volume for the mic and mic boost, rebooted my system, and now no input devices are being detected in Ubuntu settings. There used to be "Digital microphone" but now there's nothing.

Here is the output you requested from inxi:

Audio:
  Device-1: Intel Tiger Lake-LP Smart Sound Audio vendor: Micro-Star MSI
    driver: sof-audio-pci-intel-tgl bus-ID: 00:1f.3 chip-ID: 8086:a0c8
  API: ALSA v: k6.6.10-060610-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin

Also, when I type: sudo alsactl -F restore, I get the following output now:
alsa-lib main.c:828:(execute_sequence) unable to execute cset 'name='Speaker Playback Volume' 60%'
alsa-lib main.c:2520:(set_boot_user) Unable to execute boot sequence
Found hardware: "sof-hda-dsp" "Realtek ALC298" "HDA:80862812,80860101,00100000 HDA:10ec0298,146212c5,00100103 cfg-dmics:2" "" ""
Hardware is initialized using a generic method
/usr/share/alsa/init/default:98: value write error: Input/output error
alsactl: set_control:1475: Cannot write control '2:0:0:Headphone Playback Volume:0' : Input/output error
alsactl: set_control:1475: Cannot write control '2:0:0:Speaker Playback Volume:0' : Input/output error



That wasn't happening before. Before, there was no output.

Where do I go from here?

---

### Post by #&amp;thj^% on 2024-01-07
There is nothing that pressing F6 would cause this, The un-mute seems to have revealed a bad driver.

Will you try this now, we will test by disabling the sof driver and falling back to Intel.
```
sudoedit /etc/default/grub
```
Now we add this to "GRUB_CMDLINE_LINUX_DEFAULT" like below
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash snd_hda_intel.dmic_detect=0"
```
update grub to reflect the new change:
```
sudo update-grub
```
Reboot, and now what shows or works?

---

### Post by zashinoff on 2024-01-07
I did everything you suggested, and rebooted, and in settings it's still not showing any input devices.

I don't know if this is relevant, but before I posted here, I was looking for solutions to this problem online and that's where I found the other driver I think. (the sof whatever)

So the mic is still not working, it was muted so I un-muted it, but like I said in settings there's no input device being detected.

Here is my current output from inxi:
Audio:
  Device-1: Intel Tiger Lake-LP Smart Sound Audio vendor: Micro-Star MSI
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:a0c8
  API: ALSA v: k6.6.10-060610-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin

And when I try sudo alsactl -F restore now I get the following:
No state is present for card PCH
Found hardware: "HDA-Intel" "Realtek ALC298" "HDA:10ec0298,146212c5,00100103 HDA:80862812,80860101,00100000" "0x1462" "0x12c5"
Hardware is initialized using a generic method
No state is present for card PCH

---

### Post by #&amp;thj^% on 2024-01-07
> **zashinoff said:**
> 
I don't know if this is relevant, but before I posted here, I was looking for solutions to this problem online and that's where I found the other driver I think. (the sof whatever)


yes that could be a or the problem, can you undo that? 
You card should have been installed with the proper driver at install time. Although sometimes a tweak here and there might be needed with Newer hardware.
But I don't see that as a problem for you Manufactured in 2020.

I've seen numerous reports on Windows and Linux with "Nahimic 3 / Hi-Res Audio "

---

### Post by zashinoff on 2024-01-07
I don't know how to undo it. Besides reinstalling the OS, is there another way to go about this? I'm thinking that maybe the microphone was muted in alsamixer after installing 23.10 and all I needed to do was unmute it.

---

### Post by #&amp;thj^% on 2024-01-07
> **zashinoff said:**
>  is there another way to go about this? I'm thinking that maybe the microphone was muted in alsamixer after installing 23.10 and all I needed to do was unmute it.
I would highly think so, but I would first need to know what you did. Dose that make sense. :)

---

### Post by zashinoff on 2024-01-07
First, I cloned this repository: [https://github.com/thesofproject/sof-bin#install-process-with-installsh](https://github.com/thesofproject/sof-bin#install-process-with-installsh)

Then, before I installed anything, I ran this command: [COLOR=#1F2328][FONT=ui-monospace]sudo mv /lib/firmware/intel/sof* some_backup_location/ (with my backup location)
Then, I ran: [/FONT][/COLOR]sudo rm -rf /lib/firmware/intel/sof*
Then, I installed v2.2 of the driver with ./install.sh (install.sh is located in the main dir of the repository)

I thought that by copying the files from the backup location to /lib/firmware/intel/ that would undo everything, but given that no input device is being detected now, maybe it didn't undo everything.

---

### Post by #&amp;thj^% on 2024-01-07
Some of that stuff is over 3yrs old.
I'm going to have to think on this, it's a bit more complex to what I had hoped for.
I'll return tomorrow.
BTW You may as well change back Grub  remove "snd_hda_intel.dmic_detect=0"

---

### Post by zashinoff on 2024-01-07
Maybe it would be simpler to just do a clean install of the OS. If you can't think of something before tomorrow afternoon, I think I might just do that, and I'll post back here if there's more to this than just un-muting the microphone after 23.10 is reinstalled.

---

### Post by zashinoff on 2024-01-08
So I managed to reinstall the OS, and the mic was still muted in alsamixer, so I unmuted it, and the mic is still being detected in Ubuntu settings, but there is still no sound coming from the mic input... any ideas about next steps? Thanks again for you help

---

### Post by #&amp;thj^% on 2024-01-08
This has kind of turned into testing things now, I'm just not up to snuff on your Hardware.
But first will you please again try with a modification to grub, but this time I would like to see if this will help:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash snd_hda_intel.dmic_detect=1"
```
update grub, and reboot.
Also what kernel are you using ATM?
```
dpkg --get-selections | grep -v deinstall | grep linux-image

```

---

### Post by zashinoff on 2024-01-08
I just tried it - same as before, there's still no sound coming from the mic when I talk.

I downloaded and installed the new kernel 6.7

linux-image-6.5.0-14-generic			install
linux-image-generic-hwe-22.04			install
linux-image-unsigned-6.7.0-060700-generic	install

---

### Post by #&amp;thj^% on 2024-01-08
This is starting to sound more of a Bug now on the newer kernels.
can you show me how this reads on your system:
```
[COLOR="#FF0000"]ls  /etc/modprobe.d[/COLOR]
amd64-microcode-blacklist.conf  libhackrf0.conf
blacklist-libnfc.conf           mdadm.conf
blacklist-nvidia-nouveau.conf   nvidia-blacklists-nouveau.conf
broadcom-sta-dkms.conf          nvidia.conf
dkms.conf                       nvidia-options.conf
intel-microcode-blacklist.conf

```

---

### Post by zashinoff on 2024-01-08
ls /etc/modprobe.d output:
alsa-base.conf                  blacklist-modem.conf
amd64-microcode-blacklist.conf  blacklist-oss.conf
blacklist-ath_pci.conf          blacklist-rare-network.conf
blacklist.conf                  intel-microcode-blacklist.conf
blacklist-firewire.conf         iwlwifi.conf
blacklist-framebuffer.conf

---

### Post by #&amp;thj^% on 2024-01-08
Ok Good you do have an "alsa-base.conf"
Keep track of what we do here so you can add or undo any settings we have changed thus far.
Now in the terminal:
```
sudoedit  /etc/modprobe.d/alsa-base.conf

```
Now add this to the bottom of that file:
```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

```
Save and exit, I "think" just a logout and login should be good enough but a reboot might still be needed to see any changes.

Also please run this before a new session is stsrted.
```
systemctl --user --now enable wireplumber.service
systemctl --user --now start wireplumber.service
```

---

### Post by zashinoff on 2024-01-08
Done.

After adding those two lines and rebooting, no input devices are being detected in Ubuntu settings.

I also ran:
systemctl --user --now enable wireplumber.service
systemctl --user --now start wireplumber.service

and nothing changed.

---

### Post by #&amp;thj^% on 2024-01-08
Just to be sure, I'm often assuming so have you removed "snd_hda_intel.dmic_detect=1" from grub yet?
If so I'm all out of anymore ideas for you my friend. :)

---

### Post by zashinoff on 2024-01-08
No I haven't. I'll try removing that now

---

### Post by zashinoff on 2024-01-08
So I removed that, updated grub again, and rebooted, and nothing changed.

Just to experiment, I removed the two lines you suggested I add at the end of alsa-base.conf and ran sudo alsa force-reload, and rebooted, and now my input device is being detected again in Ubuntu Settings.

But there is still no sound coming from the mic.

---

### Post by zashinoff on 2024-01-08
To experiment, I added those two lines back, ran sudo alsa force-reload, rebooted, and no input devices were detected.

So I removed the two lines again, ran sudo alsa force-reload again, rebooted, and still no input devices are being detected.

This is where I am currently.

---

### Post by #&amp;thj^% on 2024-01-08
This is very bug-worthy, i'd file a bug against it.
I wish i had a better outcome though.
Good Luck

---

### Post by zashinoff on 2024-01-08
You think it's a bug on Ubuntu's side? Or the linux kernel?
Thank you so much for your time; I really appreciate your help.

---

### Post by #&amp;thj^% on 2024-01-08
Your very welcome, i enjoy this kind of stuff. :)
Ubuntu handles their own kernels (kernel-team) by the time it reaches end users.

---

### Post by zashinoff on 2024-01-08
How do I file a bug report?

---

### Post by #&amp;thj^% on 2024-01-08
ubuntu-bug packagename. or for a more general report "ubuntu-bug alsa"
Try and gather the information from this thread and wait for them to contact or reply back from the generated report.

---

### Post by zashinoff on 2024-01-08
What package do I put? I tried alsa but my shell is saying it's not installed. And how do I gather info from this thread?

---

### Post by #&amp;thj^% on 2024-01-08
I'm on Debian today but if i remember right it should be "alsa-firmware-loaders"
Just copy and paste the information you have done here in your thread to help them out.

---

### Post by zashinoff on 2024-01-08
Just submitted the bug report. Instead of copying all 4 pages of this thread, I linked to it and let the bug team know to refer to it.

---

### Post by #&amp;thj^% on 2024-01-08
If they will, I bet they are far to busy to chase links.
It's considered proper courtesy to show them on the report page what and how you have done to help them.

They have thousands of bugs they chase at any one time, and it will increase your chance of getting to a solution.
And Thanks for helping to make Ubuntu Better.

---

### Post by zashinoff on 2024-01-08
How do I access the bug report? I'll go back and edit it

---

### Post by zashinoff on 2024-01-08
Done. All the details are in the bug report now.

---

