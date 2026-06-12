---
title: "No HDMI audio option in 12.04 LTS"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by beking3 on 2013-11-06
Hello:

I apologize, I have seen many, many posts regarding this topic, but I have not found a solution. 

System: Ubuntu 12.04.03 LTS AMD64; MOBO: Asus M5A78L-M/USB3; Chipset: AMD760G/AMDSB710; CPU: AMD FX6300; OCZ SSD; Built-in Graphics: Radeon 3000; Built-in Audio: VIA VT1708S.

I have connected the MOBO through HDMI to an AVR receiver that I know works-at least with Windows 7. Thus, cable does not go directly to monitor, but pass-through receiver. Video is perfect through HDMI.

Problem: Installed new OS and there is no HDMI sound or option. Only sound options are Analog Speakers and Digital Optical (SPDIF).

I read some posts and installed the Pulse Audio Volume Control. In that app, I see an option for HDMI as I read I should. However, when I then go back to the sound options, still no HDMI option. Other thing that is strange is that in the Pulse App, I do not see an option for the Optical output-just the HDMI and speakers.

I checked the drivers for the MOBO and their instructions for Linux said no drivers necessary, just make sure you have the most recent Kernal. I verified that updates were installed and OS is reporting up to date. 

I confirmed that HDAudio is enabled on MOBO, but I did not see any other option for HDMI-such as enable HDMI audio-or the like. 

I do get sound when I plug the optical into the receiver and choose that input. 

I have installed XBMC to use as media streamer from home server. Video works, but when I choose HDMI, it reports "Audio device failed to initialize."

I installed a Gigabyte HD5450 Card to see if that would force recognition. No luck-same result.

So my problem is that the OS is apparently not recognizing the HDMI and not even giving me the option to choose it. This is strange, because as stated, the Pulse Audio Volume Mixer seems to see the HDMI Audio. 

Any Ideas-and sorry again because I know there are a thousand posts on this subject-but each one seems a little bit different and I have yet to find a solution for my issue. 

Thanks in advance,

Brian

---

### Post by danny24 on 2014-02-10
Hello Brian,

>System: Ubuntu 12.04.03 LTS AMD64; MOBO: Asus M5A78L-M/USB3; Chipset:  AMD760G/AMDSB710; CPU: AMD FX6300; OCZ SSD; Built-in Graphics: Radeon  3000; Built-in Audio: VIA VT1708S.

I have the same mainboard and CPU. I have Ubuntu 13.10, though. I can see two HDMI audio outputs.

>I have connected the MOBO through HDMI to an AVR receiver that I know  works-at least with Windows 7. Thus, cable does not go directly to  monitor, but pass-through receiver. Video is perfect through HDMI.

>Problem: Installed new OS and there is no HDMI sound or option. Only  sound options are Analog Speakers and Digital Optical (SPDIF).

Did you enable radeon audio?

What happens when you do 

   systool -m radeon -v |grep audio

?

For me, the following is output:
    audio               = "1"


What does

  dmesg |grep radeon

say?

Try

   sudo apt-get install read-edid

Then what does

   sudo /usr/sbin/get-edid | parse-edid

say? Mention anything about audio?

>I read some posts and installed the Pulse Audio Volume Control. 

Yeah, that's the right one.

>In that  app, I see an option for HDMI as I read I should. 

In pavucontrol I have:

Under Configuration:

RS780 HDMI Audio [Radeon (HD) 3000 Series] Digital Stereo (HDMI) Output
Built-in Audio (about 20 entries including Digital Stereo (HDMI) Output)

I have multiple HDMI outputs in the Context menu of the Volume Control icon in the systray and then in the menu under Sound settings (so all in all under All Settings > Sound > Output > Play sound through):

HDMI / DisplayPort RS780 HDMI Audio [Radeon (HD) 3000 Series]
HDMI / DisplayPort Built-in Audio
Analog Output Builtin Audio

There's a Test Sound button right next to it. Click it and then click one of the speaker "Test" buttons that show up. What happens?

>However, when I then  go back to the sound options, still no HDMI option. Other thing that is  strange is that in the Pulse App, I do not see an option for the Optical  output-just the HDMI and speakers.

I don't see the optical either. I've been wondering whether it's just on of the many HDMI outputs I see.

>I checked the drivers for the MOBO and their instructions for Linux said  no drivers necessary, just make sure you have the most recent Kernal. I  verified that updates were installed and OS is reporting up to date. 

Where are these instructions?

>I confirmed that HDAudio is enabled on MOBO, but I did not see any other option for HDMI-such as enable HDMI audio-or the like. 

Me neither. As far as I can tell, HDAudio disables every audio device that's not on the graphics card. I only have one HDMI output left when I disable it (I tried).

>I do get sound when I plug the optical into the receiver and choose that input. 

I don't have anything that accepts the optical output, so I wouldn't know.

>So my problem is that the OS is apparently not recognizing the HDMI and  not even giving me the option to choose it. This is strange, because as  stated, the Pulse Audio Volume Mixer seems to see the HDMI Audio. 

It should detect MULTIPLE HDMI audios.

What does
  aplay -l 
say?

Mine says
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 3: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Try adding radeon.audio to the kernel command line or add a module configuration like this:

dannym@dayas:~$ cat /etc/modprobe.d/radeon.conf 
options radeon audio=1

---

### Post by David D. on 2014-02-11
I have the same video built into my HP laptop, and was able to get the sound for HDMI output working by adding a PPA for alsa sound.

[https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily]("https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily")

---

