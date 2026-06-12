---
title: "All I Can Say Is, &quot;OMG&quot;"
date: 2008-06-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by GuitarRocker2562 on 2008-06-18
Okay, so I just updated Intrepid and my sound stopped working, no suprise. I got some weird error message from Songbird saying my media didn't exist or something, or whatever, so I checked to make sure gstreamer was working, so I opened up "When My Heart Stops Beating" and the song is playing, no audio obviously, but you can tell gstreamer is working, and my computer started making a funny noise. After listening for a minute I realized me computer's internal speaker (the one that only makes error beeps) is playing the song, lol. How the **** did that happen? :lolflag:

I love development!

---

### Post by | MM | on 2008-06-19
dude that is hilarious!

---

### Post by lithorus on 2008-06-19
The thing is that the pc speaker now has an output sink in pulse audio and gets selected as default. That you can do is start "padevchooser" if it's already not started. Find the sink name of your desired default output (you find it in the pulse audio manager under devices). In my case it's "alsa_output.pci_8086_27d8_alsa_playback_0". Through the applet you choose Default Sink -> Other... and paste in the sink name you found earlier.

---

### Post by Henrik on 2008-06-19
> **GuitarRocker2562 said:**
> Okay, so I just updated Intrepid and my sound stopped working, no suprise.

Hi!

Could you please also test your sound with Hardy and hardy-proposed updates? We are planning to upgrade pulseaudio to a new upstream version for the point release and would appreciate more testing.

Sound breaking in the dev release pre-alpha 1 is amusing, but in a stable release update it would be very bad ;)

Thanks!

---

### Post by autocrosser on 2008-06-19
I'm getting the same thing--my pizo pc speaker & normal sound out are working at the same time--tried above fix to stop pc speaker out--no go--also tried to mute pc speaker only--just mutes whole system.

I'm heading to work , so I can check into this more in about 8/9 hours from now.....

---

### Post by psyke83 on 2008-06-19
> **Henrik said:**
> Hi!

Could you please also test your sound with Hardy and hardy-proposed updates? We are planning to upgrade pulseaudio to a new upstream version for the point release and would appreciate more testing.

Sound breaking in the dev release pre-alpha 1 is amusing, but in a stable release update it would be very bad ;)

Thanks!

Intrepid's first kernel landed in the repositories recently, so you may also want to consider that as potential a source of the problem...

(By the way, I'm having no problems; I have one system using Intrepid and another using Hardy with the proposed/backport repositories active).

---

### Post by Henrik on 2008-06-19
> **psyke83 said:**
> Intrepid's first kernel landed in the repositories recently, so you may also want to consider that as potential a source of the problem...

Right. TBH I'm not too concerned about figuring out the source of the problem in Intrepid, as it could be many things and breakage is expected at this stage. It was more a general appeal for testing of Hardy as well.

> (By the way, I'm having no problems; I have one system using Intrepid and another using Hardy with the proposed/backport repositories active).

Excellent, thank you! :) Have you registered your testing [here]("https://bugs.edge.launchpad.net/proposed-tracking/")?

---

### Post by Luffield on 2008-06-19
No problems on Hardy-proposed here.
And yes, I have registered :)

---

### Post by philinux on 2008-06-19
No sound problems in Hardy. I'm registered as having proposed repos active.

---

### Post by GuitarRocker2562 on 2008-06-19
While I do not use proposed updates on Hardy (It is my only stable system unless you count windows, lol), with the regular updates sound works just fine.

---

### Post by autocrosser on 2008-06-20
Hi Henrik---

Interesting--I tried to change the default in the PulseAudio Applet (PulseAudio Device Chooser)--no change---but when I used pavucontrol & changed the default thru the non-intutive arrow (for defaults menu) & selected my ALC883--everything worked as expected...no more pc speaker--do you want me to file a bug & if so, on both the applet for non-change & VUcontrol for better explaining the non-labled arrow?


> **Henrik said:**
> Hi!

Could you please also test your sound with Hardy and hardy-proposed updates? We are planning to upgrade pulseaudio to a new upstream version for the point release and would appreciate more testing.

Sound breaking in the dev release pre-alpha 1 is amusing, but in a stable release update it would be very bad ;)

Thanks!

---

### Post by lithorus on 2008-06-20
Another option is also to blacklist the snd_pcsp module in /etc/modprobe.d/blacklist

---

### Post by GuitarRocker2562 on 2008-06-20
lithorus, thanks, it's all better now.

---

### Post by autocrosser on 2008-06-21
Pulse returned to the pcsp every boot after--so the blacklist is where it went--thanks!


> **lithorus said:**
> Another option is also to blacklist the snd_pcsp module in /etc/modprobe.d/blacklist

---

### Post by ShirishAg75 on 2008-06-21
Hi all, 
 With the new kernel I'm finally able to use padevchooser . This is the menu I get 

```

Default Server
Default Sink 
Default Source 

----------------

Manager
Volume Control 
Volume Meter (Playback)
Volume Meter (Recording)
Configure Local Sound Server 

--------------------------------

Preferences 

---------------------------------

Quit

```

Now nothing is selected either in the Default Server, Sink or Source. 

Also if I use pavucontrol from the CLI (not using any sound applications) I get a Connection refused dialog box and it closes. I tried also using sudo but of no avail. 

I'm newbie to the sound applets and stuff so please be patient with me. 

Thanx in advance. :)

---

### Post by exploder on 2008-06-22
No problems with Hardy Proposed here. Sound is working just fine on Hardy.

---

### Post by ronacc on 2008-06-22
here is what I have found with intrepid so far , changing to alsa sound is normal with some apps ,bmpx,totem ,exalie ,songbird. Mplayer sound is ok after configing it to use alsa xine ok after configing it to use alsa,vlc no sound yet .

---

### Post by ShirishAg75 on 2008-06-22
> **lithorus said:**
> The thing is that the pc speaker now has an output sink in pulse audio and gets selected as default. That you can do is start "padevchooser" if it's already not started. Find the sink name of your desired default output (you find it in the pulse audio manager under devices). In my case it's "alsa_output.pci_8086_27d8_alsa_playback_0". Through the applet you choose Default Sink -> Other... and paste in the sink name you found earlier.

How do I find the Pulse Audio Manager? I can't see the same either under System > Preferences or System > Administration 

I can't see it as well under Applications > Sound & Video menu as well :(

Any help would be appreciable.

---

### Post by autocrosser on 2008-06-23
It is not installed by default--Use Synaptic & search for "pulse"--Install padevchooser (that will get you what you need) & optionally--paman, papref, pavucontrol & pavumeter for all the GUI's for Pulse.

---

### Post by lithorus on 2008-06-23
> **ShirishAg75 said:**
> How do I find the Pulse Audio Manager? I can't see the same either under System > Preferences or System > Administration 

I can't see it as well under Applications > Sound & Video menu as well :(

Any help would be appreciable.

I think the blacklisting is a better solution which will also stick after reboots.

---

### Post by Gina on 2008-06-23
IMV this is definitely something that wants sorting out with some urgency - if people find their sound doesn't work in their favourite apps they'll dump Ubuntu!

After much fiddling about I eventually got Audacity to record sound on one machine but I'm still struggling, without any success, on the machine I'd really like to use :(  It won't even work in WINE in that machine (And I only have Ubuntu on that - no other OS).

---

### Post by dinxter on 2008-06-23
For me, the sound coming out through the speaker sounded like a lovely crackle of electricity, coinciding with the start up of X, comedy followed as i leapt across to the off switch in blind panic and sniffing around the graphics card for charred silicon. wakes you up quicker than a cup of black coffee :) i've blacklisted the speaker module to protect my weak heart from any more early morning surprises...

---

### Post by Gina on 2008-06-23
For me the sound playback is fine on all 3 machines running Hardy proposed - the problem is with recording sound with either Audacity or Sound Recorder on my AMD64.  Strangely, the recording on my 4yr old P4 is now working from the Line input. My laptop only has front microphine and that's mono.

Coming back to the AMD64, whatever I do in the pulseaudio setup, volume control or Audacity prefs the capture always seems to use the front mic input (if any at all) even with recording set to Line rather than Mic or Front Mic.  Problem is my Front Mic input is mono on left channel only or I might have been able to use that.  The Line input does work - I can playback from that input fine - it just won't connect for recording.  I've tried every suggestion in this forum and the Multimedia one.

---

### Post by soccerboy on 2008-06-23
I believe that pc speakers have had the ability to do things besides beep codes for a while.  I know in my pc days, one of my old computers would default sound to pcspeaker if no external speakers were connected.  Even without an audio card (I am talking old school 1998 Gateway).

---

### Post by dinxter on 2008-06-23
anyone who played manic miner on a zx spectrum must know the strange magic of the speaker in the right(?) hands :)

---

### Post by soccerboy on 2008-06-23
And there has always been the beeps with diff. frequencies.

---

### Post by ShirishAg75 on 2008-06-23
> **autocrosser said:**
> It is not installed by default--Use Synaptic & search for "pulse"--Install padevchooser (that will get you what you need) & optionally--paman, papref, pavucontrol & pavumeter for all the GUI's for Pulse.

I have installed padevchooser and while I have the pulseaudio applet but no  Pulse Audio Manager .  Now I find I have paman which is Pulse Audio Manager. 

However when I try to run paman I get this :-

```

shirish@Mugglewille:~$ paman
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
^C

```

When I run the same as sudo paman 

The Manager runs and shows that the manager is disconnected to the server.  It takes time and stays disconnected. There is no output on the CLI on whatever is happening. 

All any clues or what I need to do are appreciated.

---

### Post by psyke83 on 2008-06-23
> **ShirishAg75 said:**
> I have installed padevchooser and while I have the pulseaudio applet but no  Pulse Audio Manager .  Now I find I have paman which is Pulse Audio Manager. 

However when I try to run paman I get this :-

```

shirish@Mugglewille:~$ paman
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
^C

```

When I run the same as sudo paman 

The Manager runs and shows that the manager is disconnected to the server.  It takes time and stays disconnected. There is no output on the CLI on whatever is happening. 

All any clues or what I need to do are appreciated.

It's possible that you performed a Partial Upgrade that has uninstalled vital packages from your system. Try updating your repositories and installing the metapackage "ubuntu-desktop" to install missing packages, but there's no guarantee it will work. I recommend you perform a clean reinstall, and in the future, *never* allow Partial Upgrades (or a "dist-upgrade" that elects to remove packages).

If you insist on fixing your system without a reinstall (or perhaps you're using Kubuntu and the package didn't get installed), this will get you started: the shared library libatk-bridge.so is part of the package "at-spi".

Also, your problem (as I saw in your posts in the PulseAudio fixes thread) is that PulseAudio is segfaulting - if the PulseAudio server isn't running, then none of the PulseAudio applications (Manager/Volume Control/Volume Meter) will work. Follow the uninstall instructions of Appendix C, and you may also need to follow the instructions in this thread about blacklisting the pc speaker module. Then see if PulseAudio works properly.

---

### Post by durand on 2008-06-26
Does adding snd-pcsp to the blacklist disable the pc speaker? I find it really useful for system beeps.

---

### Post by nbubis on 2008-10-04
The workaround only works for gnome based players - for some reason amarok thinks "the device is busy" even if nothing is playing..

anyone know of a permanent fix?

---

### Post by psyke83 on 2008-10-04
> **nbubis said:**
> The workaround only works for gnome based players - for some reason amarok thinks "the device is busy" even if nothing is playing..

anyone know of a permanent fix?

This thread should be locked, as the issue has been resolved *a long time ago*.

You're suffering from something else.

---

