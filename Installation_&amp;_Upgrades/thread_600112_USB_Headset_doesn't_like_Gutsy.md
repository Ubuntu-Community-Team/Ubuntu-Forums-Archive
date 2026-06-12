---
title: "USB Headset doesn't like Gutsy"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Pender on 2007-11-01
I'm about to throw my laptop out the window.

I spent the morning looking for a way to get my USB headset to work.

I went to System, Preferences, Sound and changed under Audio Conferencing:  Sound Playback and Sound Capture to USB Audio. Default Mixer tracks is set to C-Media USB Headphone Set (Alsa Mixer). Under this option, Microphone and Speaker are selected.

Everything worked great. I was able to use Sound Recorder to record my voice.

I also wanted to get my iPod nano to work with linux, and I saw here in the forums that it was possible, but I had to upgrade to Gutsy.

After doing this, I ran Sound Recorder and got the following error:

Your audio capture settings are invalid. Please correct them in the Multimedia settings.



I went back into my sound setup and nothing had changed, so I tested the setup.

When I test the Sound Playback it works fine.

When I test the Sound Capture I can hear my voice in the headset, but then I get the following error:

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'




I really need help with this, as I feel like I just wasted $200.

---

### Post by kennedyjch on 2007-11-02
Yes, I have experienced this same problem - it's a microphone related matter and there are several posts on this problem already. 

I had everything working under 7.04; upgraded to 7.10 (Gutsy) and problems started. I reinstalled 7.04 and all worked fine; tried a fresh install of 7.10 (no upgrade) and sound recording problem occurs. 

Between this problem (can't use Skype) and another problem, I'm seriously considering going back to 7.04. BEWARE, if you upgrade your evolution mailbox under 7.10 it appears that it will be unusable under 7.04.

Of course, if there is a know fix for this problem, I'd like to find out sooner than later.

---

### Post by Pender on 2007-11-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/131711](https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/131711) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well...at least I'm not alone. Looks like the bug got reported already.

---

### Post by Zoil on 2007-11-04
My usb headset will not work with 7.10 either.  I never tried it with 7.04. Anyway,  I get the beep when I click on the test button, but nothing when I listen to streaming audio.  

On a related note, my volume is very low, even when maxed out, while listening to anything.  When I want to listen to streaming audio, I have to boot up in XP.  If I can get the audio fixed, I would be 99% Ubuntu at home.

---

### Post by PatrickMahoney on 2007-11-25
I have noticed also that my Logitech USB Headset gets the same results.

---

### Post by legend2440 on 2007-11-25
I had the exact same problem as pender with Gutsy.
What fixed it for me was uninstalling pulseaudio in Synaptic.
Sound Recorder now works and I can record .
Make sure you have microphone unmuted and volume up I had to mess with settings in Volume Control (right click on volume horn on top panel to get to the settings) but it finally works.

---

### Post by Ron F. on 2007-12-17
Oh, good grief. I cannot believe this. It is 2007, USB headsets ought to just work by now.

I bought one too - figuring, of course it will work. It doesn't work with Gutsy. The test buttons work in System->Preferences->Devices when USB audio is selected, but that's it. I cannot get a peep out of my headset in Skype, Amarok, or firefox. The hardware is properly recognized by Skype, and in Volume Control, but it doesn't matter - no sounds comes out of the headphones, except for the USB Audio Test buttons.

Audio capture fails of course: Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

Very Irritated,
Ron

---

### Post by Ron F. on 2007-12-17
Um, ok. Maybe I should sign up for anger management. I got it working.

Doing further reading, I learned about asoundconf, and after typing "asoundconf set-default-card Headset" at a command prompt - my USB headset began working, at least both in Amarok and Skype - the two places where it really matters to me.

I have to say though - for the typical convert from Windows XP, where when you plug in a USB headset and it just works, having to learn about something called "asoundconf" seems a bit odd. It should just work.

-Ron

---

### Post by Ron F. on 2008-01-08
After using my Logitech USB stereo headphones with Ubuntu Gutsy for a while, I have come to the conclusion there is a bug in hotplug subsystem related to this. My headphones will work if they are plugged in when I boot the system, but I cannot hotplug them. Unplugging them has actually crashed Gutsy the last time I did that. Everything froze, and I could not shut down.

-Ron

---

### Post by gobbluth on 2008-01-13
> **Ron F. said:**
> 
Um, ok. Maybe I should sign up for anger management. I got it working.
Doing further reading, I learned about asoundconf, and after typing "asoundconf set-default-card Headset" at a command prompt - my USB headset began working, at least both in Amarok and Skype - the two places where it really matters to me.
-Ron


Thank you, thank you, a thousand times thank you. This bug should not be this hard to find an answer for.

---

### Post by Baneblade on 2008-07-16
Having similar problems with my usb headset (Tritton AXPC) as the rest of you.
Setting it as the default audio device in System > Preferences > Sound
only seems to work for Rythmbox, Amarok etc.
Nothing else seems to recognize them.. Firefox, VLC... nada.
Any news on a fix for this? Or a workaround in the meantime?

*UPDATE*

Booting with the headset already connected seems to solve my issue. However, hot-swapping is still giving me trouble.

---

