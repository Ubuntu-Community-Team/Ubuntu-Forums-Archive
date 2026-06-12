---
title: "How do i get my logitech 530 (5.1 surround) speakers to work?"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by Xtract01 on 2012-06-08
[SIZE=2][FONT=System]Hello everyone, I have these :
[URL="http://ecx.images-amazon.com/images/I/41qa1aO9nOL._SL500_AA300_.jpg"]
[/URL] [/FONT][/SIZE][SPEAKERS]("http://ecx.images-amazon.com/images/I/41qa1aO9nOL._SL500_AA300_.jpg")

How do i configure them in Ubuntu? 

I've tried:
Sound Settings - Analogue Surround 5.1 Output = Only the front right and front left work.

Any help is much appreciated,
Thanks.

[FONT=Courier New]Xtract01[/FONT]

---

### Post by papibe on 2012-06-08
Hi Xtract01.

Sometimes some of the non standard outputs are muted. You can check their status and unmuted them using the command 'alsamixer'.

You can also test the outputs by running 'speaker-test'.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1629357&highlight=aplay") for examples.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Xtract01 on 2012-06-08
> **papibe said:**
> Hi Xtract01.

Sometimes some of the non standard outputs are muted. You can check their status and unmuted them using the command 'alsamixer'.

You can also test the outputs by running 'speaker-test'.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1629357&highlight=aplay") for examples.

I hope that helps, and tell us how it goes.
Regards.

Hello :)
I typed 'alsamixer' into the terminal, it looked fine to me :o. It looks like the results from the thread you posted. I tried to resolve my issue following your steps in that thread:

```
$ speaker-test -Dsurround51 -c6 -twav
```It always manages to get front right and front left.. I don't think it knows my speakers are there? In a way. I haven't installed drivers for them? If it was possible i wouldn't have a clue on how to do it . ](*,)

---

### Post by eric_son on 2012-09-01
@Xtract01

Were you able to fix your problem?  I'm also experiencing the same problem as you.
I have a 5.1 setup.  ALSAMIXER indicates that the volume settings of the rear, mid and lfe are okay.  But I only get sound from the front left&right speakers.

---

### Post by DaCast on 2012-09-02
I've read somewhere that Ubuntu, at present, use PulseAudio by default. It dictates the type of output you'll be getting from the sound card. Unfortunately, Pulseaudio also disables surround capability by default, which causes you to hear sound from only the two front speakers. I searched high and low until I came upon one website with the solution. It has worked for me so you might want to try it to see if it will work for you as well. I have copied the instructions from that website and pasted it here. Please see below.

"[I]Ubuntu now uses PulseAudio by default, so it dictates the kind of output you’ll be getting from your sound card. Luckily, PulseAudio makes it very easy to enable surround via a simple configuration file. I followed instructions here for editing via the command-line, but using a GUI should be just as easy.

    Press Alt-F2 to open a “Run” dialog, and type “gksudo nautilus“. This will give us a file-browser with administrator privileges.

    Warning: With this file browser we have access to do almost anything to our system. Follow these instructions carefully, or things could get bad!
    In the file browser, click on the “File System” icon on the right. Then navigate into the “etc” folder, and then “pulse”. This is the folder where our configuration file lives.
    Make a backup of “daemon.conf”. Do this by selecting the file, copy it, and then paste it in the same directory. Right click the new copy and rename it “daemon.conf.bak”. This is just in case things go wrong– it’ll be easy to revert back to the original settings.
    Now we’re going on edit the settings file. Double-click on “daemon.conf” to open it in a text editor. Remember that we have administrator privileges, so be very careful of the changes you make!
    Find the following line in the file, it should be towards the bottom:

        ; default-sample-channels = 2

    First, remove the “;” character to “uncomment” the line. Then change the value from 2 to either 6, for 5.1 surround sound, or 8 for 7.1 surround. For example:

        default-sample-channels = 6

    Save the file and exit the text editor and file browser. This is important so we don’t accidentally make more changes with administrator access.

That’s it for the hard part. For the changes to take effect, you will need to restart your computer. Afterwards, there is a simple command that you can use to test your surround sound. Press Alt-F2 to start the “Run” dialog, and enter the command:
speaker-test -Dplug:surround51 -c6 -l1 -twav
or to test 7.1 surround:
speaker-test -Dplug:surround71 -c8 -l1 -twav

This will play a sound from each speaker telling what channel it is set to. You should hear audio out of each one. If you don’t then you may have some of the channels disabled. Check them with the volume manager:

    Right click on the volume meter in the panel and press “Open Volume Control”.
    Make sure the “ALSA” mixer is selected. Go to File, Change Device, and select the one that contains “Alsa Mixer”.
    By default, many of the channels are hidden. Select Edit, Preferences. Make sure you have at least the following selected: Master, Front, Surround, Center, and LFE (and Side if using 7.1 sound)
    Now, make sure none of the channels are muted under the “Playback” tab. If they are, un-mute them.

    Then use the test command above to try again.

At this point you should have surround sound working via the test command. However, some applications may also need to be setup to use surround sound. Rhythmbox should play music using surround by default. However, Totem Movie Player needs to be configured for it. To do so:

    Open Totem Movie Player from the Applications menu under Sound and Video, Movie Player.
    Select Edit, Preferences, and click on the “Audio” tab
    Set the “Audio output type” to your surround-sound preference. For example. 5.1-channel.

Other applications or webpages that use Flash may not use surround sound correctly. You can test if an application is using surround sound using the PulseAudio volume meter. To do so, press Alt-F2 to open the “Run..” dialog, and enter the command “pavumeter“. You should see sound in each channel.

I’ve been very happy with my surround sound so far. What experiences have you had? Did these instructions work for you? Are there any other applications you’ve found that don’t work with surround sound? Post in the comments.[/I]"

Source: automaticabledotcom/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/

I hope this solution works for you. :)

---

### Post by eric_son on 2012-09-07
Thanks, but unfortunately, it still doesn't work for me.
I've already edited my daemon.conf file by uncommenting the default-sample-channels and setting it to 6.  
After rebooting and running the speakertest, I'm only getting sound from the FrontLeft and FrontRight speakers.

I've been using that trick on my older system and it worked beautifully.
But now, it doesn't.  Maybe it's a hardware issue. :(

I've attached screenshots of the alsamixer app.  Notice that I've already set my RearLeft/RearRight, Center and LFE channels to a high level.
I've also noticed a "Smart5.1" option on the far right end of Alsamixer.  But I can't change that. It's stuck at disabled.  So I'm not sure if that has something to do with my sound problem.

I'm using the onboard sounds from my  ASUS P8H61-M LX3Plus motherboard by the way. (Just in case anyone was able to get surround to work on this. :) )

---

### Post by eric_son on 2012-09-16
SUCCESS!!!!!
Out of desparation (or boredom...), I tried to install the gui version of the ALSAMIXER (Gnome Alsamixer).
Using the Gnome Alsamixer, I was able to enable the "Smart5.1" option which I couldn't do via the terminal ALSAMIXER.
Now I'm getting 5.1 sounds from the speaker test!

---

