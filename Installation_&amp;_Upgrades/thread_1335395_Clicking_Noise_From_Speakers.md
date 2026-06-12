---
title: "Clicking Noise From Speakers"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by nehalia on 2009-11-23
I know the clicking noise issue has been asked a lot, but my problem is different in a few ways.

 I have an old Dell Latitude laptop that I am going to give to my younger brother.  I was running Windows XP on it, but it's too to bulky for the computer and makes it unusably slow.  I figured some flavor of Linux would be the best solution for the machine, and decided on Ubuntu 9.10.  I installed Ubuntu, and when ever a sound is played, you hear the sound and you hear an obnoxious repeated "clicking" noise over the top for a few seconds.  The clicking only happens when a sound is playing.  The "clicking"  happens with the laptop built in speakers as well as head phones

I've already read through the other threads and the standard soultion does not work.  This is because I DO NOT have Intel HD audio controller.  When I type: ```
lspci | grep -i audio
``` I get back: ```
01:00.1 Multimedia audio controller: Neomagic Corporation MN2360 [MagicMedia 256 ZX Audio]
```Everything else with Ubuntu is great!  Any help with this problem would be appreciated.

---

### Post by nehalia on 2009-11-23
...also
 
Unlike many with a similar problem.  I can mute the volume and the clicking stops.

---

### Post by Friday7 on 2009-11-23
nehalia

I have the same problem with setting up a Dell Latitude CS with the same sound card.

```
01:00.1 Multimedia audio controller: Neomagic Corporation NM2360 [MagicMedia 256 ZX Audio]
```

From what I have read so far is we need to get the alsa driver installed.  But not sure how to do that yet.

---

### Post by Friday7 on 2009-11-23
This looks to be a common problem.  [**bug track 381201 link**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201")

But try this on your system it did not work on mine, but my system could be too old.

Editing the file /etc/modprobe.d/alsa-base.conf 
```
  options snd-hda-intel power_save=10 power_save_controller=N
to
  options snd-hda-intel power_save=0 power_save_controller=N
```

---

### Post by nehalia on 2009-11-23
Modifying alsa-base.conf only works if the souse of the problem is the power_save_controller in machines with Intel HD audio....our dell latitudes do not.

My guess is that instead of a power save issue, it's a driver issue.  I'm still unsure as to what course to take to fix it.

---

### Post by nehalia on 2009-11-24
I just connected the machine to the internet for the first time and did updates in hopes that the fix to this problem was there.

No such luck ;)

---

### Post by barthel on 2009-11-24
I've never owned this soundcard, but a quick Google showed other problems with the Neomagic 256 series chips. This is an old (2005) post, but it might point you in the direction of a solution. [http://www.linuxforums.org/forum/linux-laptops-netbooks-minibooks/28985-omnibook900-neomagic-nm2200-256av-alsa-problems.html](http://www.linuxforums.org/forum/linux-laptops-netbooks-minibooks/28985-omnibook900-neomagic-nm2200-256av-alsa-problems.html)

The author was able to successfully use the sound card by configuring it as a Crystal Audio CS4232.

Hope this helps you find a solution.

---

### Post by nehalia on 2009-11-26
Thanks for the link.

I ran the alsaconf script and I did not get Crystal audio as an option.  I tried the options that were presented and it probed. It changed files and adjusted the volume, but the sound was not fixed.  I was nervous the whole time it was running because I had to enter the superuser password, and  I had no idea what the script was doing.

I think this laptop is doomed to be a Mute for the rest of its remaining life.  My brother is using it just for word processing, and so he doesn't care about sound.  I asked him if he wanted me to try and put PCBSD on and see if it works, but he's happy with it the way it is.  So, I just disabled all sound on it to avoid the annoying clicking.

I think this problem is a little to big for a Linux newb like me ;)  Thanks for the help anyway guys.

---

### Post by key134 on 2009-11-28
> **nehalia said:**
> I think this problem is a little to big for a Linux newb like me ;)  Thanks for the help anyway guys.

Aw no, don't give up.  I was hoping you'd solve this problem for me.  I have the same issue with my nm2360 on my Dell Latitude.  I'll keep searching...

---

### Post by key134 on 2009-11-28
Actually, it looks like we are going in the wrong direction.  I am able to get proper sound by setting the output module to UNIX OSS in VLC.  ALSA and PulseAudio both have the horrible clicking sound.  It looks like the issue is probably in the sound server.

---

### Post by Shazaam on 2009-11-28
I know you don't have a Creative soundcard but try the edit in my sig. Might work. Make sure you test all apps/games that output sound after the change.

---

### Post by key134 on 2009-11-30
> **Shazaam said:**
> I know you don't have a Creative soundcard but try the edit in my sig. Might work. Make sure you test all apps/games that output sound after the change.

Unfortunately, it did not fix the problem.  I still have the helicopter noise when sound is playing (actually whenever pulseaudio wakes up).  Even after I stop the music in VLC it will continue to click for a while.  Heh, it is the worst in terminal when it would normally beep, I get a helicopter for about 10 seconds.

---

### Post by Kixtosh on 2010-01-25
Shameless bump of this thread from a newbie with his very first, all shiny new post!
 
I'm having the problem on a Dell Lattitude CPi R400GT (1999 model). The sound card is the same one:
 
NM2360 [MagicMedia 256 ZX Audio]
 
Like those mentioned above, this horrible clicking is only when a sound is being played, including the startup animation.
 
I'm hoping this bump will bring new inspiration or divine intervention of some description!

---

### Post by Kixtosh on 2010-01-25
Well, after some fishing around, I realized I had originally tried Linux on this same laptop about five years ago, and I didn't remember having sound issues ... so ... I poked around in my archives and found the Live CD for Knoppix 3.7 that I used at the time, and tried it again: sure enough, the sounds works perfectly with this O.S., but not with Ubuntu 9.10.
 
The sound module used by Knoppix 3.7 seems to be *nm256_audio*. I've done some searching, and I'm guessing this is an OSS module (if that's the appropriate term to use). I found a reference to it here:
 
[http://www.opensound.com/osshw.html](http://www.opensound.com/osshw.html)
 
I'm not nearly smart enough to know what to do at this point, but maybe it will help somebody else clarify things a little for the rest of us.
 
1) Does this mean the Alsa sound mixer will not work with this card? 
2) Is it even possible to use the OSS driver with Ubuntu 9.10?
3) Are their any issues with using the OSS driver, if it is possible?
4) How would one go about installing it, if this seems like a good idea?
5) Any other options, anyone (better ones, perhaps)?

---

### Post by Kixtosh on 2010-01-27
Well ... it seems as though everyone else having this problem has either given up, or gone back to Windows, or thrown out their computer and decided to become a hermit instead.

I've still been working with this. I've been trying the tips on the troubleshooting page:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

But, it isn't working out so far. I got as far as the stage where need to check:

[SIZE=3][COLOR=Sienna]Is ALSA using the correct model?[/COLOR][/SIZE]

But I tried every link provided from the result displayed in the Terminal window, and all I got was a load of gibberish. It did not have the information shown in the example page:

[http://www.alsa-project.org/db/?f=4e5ca464947959bdf373516314670645493e0dfa](http://www.alsa-project.org/db/?f=4e5ca464947959bdf373516314670645493e0dfa)

This is what I got, basically:

> ~$ wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
--2010-01-27 09:44:47--  [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh)
Resolving alsa-project.org... 212.20.107.51
Connecting to alsa-project.org|212.20.107.51|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2010-01-27 09:44:49--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [    <=>                                                                             ] 26,584      41.1K/s   in 0.6s    

2010-01-27 09:44:51 (41.1 KB/s) - `alsa-info.sh' saved [26584]
So ... I'm at a loss now. Maybe I need to figure out which Ubuntu release last used OSS, instead of ALSA, and try that (hoping it has support for my wireless card, which works flawlessly in Karmic Koala without any user intervention at all).

---

### Post by Kixtosh on 2010-02-04
I was able to solve this issue for my DELL CPi R400GT, as described in this thread, in the DELL area of the Forum:

[http://ubuntuforums.org/showthread.php?t=1391973](http://ubuntuforums.org/showthread.php?t=1391973)

Basically, my solution involved:

1) Updating ALSA to version 1.0.22.
2) Removing PulseAudio.
3) Adding PulseAudio back.

If this can help anyone, or anyone needs more details, please post in this thread and I'll add any clarifications necessary ... if I can!

---

### Post by Kixtosh on 2010-02-09
More information on this topic:

Well, I've actually switched my old DELL to Xubuntu 9.10, and my one remaining sound issue with the regular Ubuntu install (clicking noise during the startup splash screen) has been entirely solved. _I did not have to do anything with Xubuntu to get the sound working_, neither upgrading ALSA nor fiddling around with PulseAudio in the Terminal Console. It worked flawlessly (so far) out of the box.

---

### Post by keithspg on 2010-09-19
Same problem but with 10.04. This machine has run Ubuntu 9.10, windows XP, Ubuntu 8.04 all with no problems with sound. It is a Dell CSx with the Neomagic card. It sounds like a helicopter when trying to play sound. I have tried these suggestions and no improvement. The ALSA version with 10.04 is 1.0.23. I have tried the ALSA backports. Same result. Any help?

Keith

---

### Post by Kixtosh on 2010-09-19
> **keithspg said:**
> Same problem but with 10.04. This machine has run Ubuntu 9.10, windows XP, Ubuntu 8.04 all with no problems with sound. It is a Dell CSx with the Neomagic card. It sounds like a helicopter when trying to play sound. I have tried these suggestions and no improvement. The ALSA version with 10.04 is 1.0.23. I have tried the ALSA backports. Same result. Any help?

KeithKeith, if this were me, and it were convenient for you, this is what I would do in the same situation:

- Download and burn the ISO image of Lubuntu, Peppermint or Xubuntu
- Download and burn the ISO image of Puppy 501 (LuPu)
- Try both from a CD, and see if there are any sound problems

In the case of LuPu, starting from the CD is quite fast, and it works fast even without installing it to the hard drive (it's not really intended for a HDD installation anyway). If the LuPu CD is in the CD drive at the time of booting up, you get Puppy. If the LuPu CD is not in the drive at the time of booting up, you get whatever O.S. is currently installed on your HDD, the same as you do today.

As for the other choices, even when using Xubuntu, I much preferred to add the LXDE lightweight desktop environment, from the Ubuntu Software Center (you have to first download and install it, then log out and log in after selecting LXDE - shutting down and restarting does not work). Otherwise, both Lubuntu and Peppermint already use the LXDE desktop, they are lightweight, and just might solve your sound issue too in the same way Xubuntu solved mine. You can try any of these from a Live CD without removing your current Ubuntu installation. Heck! You might even decide you prefer one of them.

If any of these solve your sound issue, then you may be able to track down what is different from there, with some help from some more knowledgeable forum members than little ol' me.

Bear in mind also that Lubuntu 10.04 is a beta release. There will be no LTS release until 12.04, but it is quite polished already nonetheless in my opinion.

---

### Post by keithspg on 2010-09-25
Puppy works without the helicopter sound. lubuntu works like xubuntu with the annoying helicopter sound. One thing I did notice was that neither of the other 2 distros had a pulse process running at least when running off the CD. ps-e | grep pulse gave no result. Both seem to be running the same version of the NM256 driver. How to see what is the difference between the 2. I am considering removing pulse to see if that works. If I remove pulse, do I need to install OSS?

---

### Post by keithspg on 2010-09-25
I have compared the 3 systems. The comparison between the 3, lu and puppy do not use pulse. Only puppy has correct sound. 

On lsmod, this is what I see different and puppy and lu look very similar:
Xubuntu
snd                    62394  19 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device

lubuntu
snd                    54148  13 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Puppy
snd                    30859  10 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_timer

Both puppy and lubuntu use:
/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

xubuntu uses:
/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Sep 18 2010 for kernel 2.6.32-24-generic (SMP).

I am stumped. It is not pulse as the problem exists on lu or xu and only xu is using pulse, and the problem also exists with lu. IK am thinking of removing pulse just to see if it helps. An thoughts?

---

### Post by keithspg on 2010-09-25
Ok, So I removed pulse, rebooted and now no helicopter sound on xubuntu. I have no idea why lubuntu has the helicopter sound except that maybe the older version of alsa may be causing something. That really does not make sense b/c the puppy has the same version of alsa as lubuntu and no pulse and no helicopter sound. Regardless, I have a version of ubuntu and can use DAAP to play music on this antique. At least it has one good use.

In conclusion, 2 of us have had problems with this old card and neither knows exactly how we fixed it.

---

### Post by Kixtosh on 2010-09-25
> **keithspg said:**
> ... I am stumped. It is not pulse as the problem exists on lu or xu and only xu is using pulse, and the problem also exists with lu. IK am thinking of removing pulse just to see if it helps. An thoughts?Keith, I don't know enough about this stuff to figure out what information would be needed to figure out why the sound works on Puppy (which is based on Ubuntu, from version 501 - the current LuPu version), but not on Lubuntu. What you could try is a procedure that "accidentally" helped my situation on the old Dell with the same card, before I stopped using the regular flavored Ubuntu 9.10 Karmic Koala (switching to Xubuntu with LXDE). You may have noticed it in this post:

[http://ubuntuforums.org/showpost.php?p=8775740&postcount=16](http://ubuntuforums.org/showpost.php?p=8775740&postcount=16)

Basically:

```
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```which removed Pulse, but left me with no sound adjustments at all, so then:```
sudo apt-get install ubuntu-desktop
```which reinstalled Pulse, but it was mostly working after that.

Otherwise, you could open a bug report, possilby making reference to my but report also. Enter this code in a Terminal window:```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```This will give you a result like this (in the same Terminal window):```
--2010-09-24 21:26:49--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 212.20.107.51
Connecting to www.alsa-project.org|212.20.107.51|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2010-09-24 21:26:50--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,026      45.1K/s   in 0.6s    

2010-09-24 21:26:51 (45.1 KB/s) - `alsa-info.sh' saved [27026]

ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : **[COLOR="Red"]y[/COLOR]**
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=7a360844ca3de6116aa70b2b1ae9ef7571376244

Please inform the person helping you.

```You can type "y" where I highlighted it in red above, and then you will get a link to your report.

Here's a clickable link to my report:

[http://www.alsa-project.org/db/?f=7a360844ca3de6116aa70b2b1ae9ef7571376244](http://www.alsa-project.org/db/?f=7a360844ca3de6116aa70b2b1ae9ef7571376244)

And here's a link to my bug report:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/99706](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/99706)

Best of luck! The bug reporting was a bit frustrating, as you might notice from my report, since I mostly got links to my own responses in the forum here, and one somewhat cryptic suggestion, and then nothing further until I solved it myself as described earlier.

Perhaps you should indeed try the pulse procedure described above though. What's the worst that could happen? You might have to reinstall or something? That doesn't seem like a big deal at this point (unless you have already created a ton of documents in your home folder).

---

### Post by Kixtosh on 2010-09-25
> **keithspg said:**
> Ok, So I removed pulse, rebooted and now no helicopter sound on xubuntu. I have no idea why lubuntu has the helicopter sound except that maybe the older version of alsa may be causing something. That really does not make sense b/c the puppy has the same version of alsa as lubuntu and no pulse and no helicopter sound. Regardless, I have a version of ubuntu and can use DAAP to play music on this antique. At least it has one good use.

In conclusion, 2 of us have had problems with this old card and neither knows exactly how we fixed it.Sorry: we cross posted! Anyway, as described above, you may find that if you add Pulse back again, it might actually work without the helicopter sound.

It might be worth filing the bug report anyway, just to feed the topic. You will notice in my bug report that I stated that my alsa info did not change from before and after the Pulse removal procedure, so maybe it has nothing to do with alsa after all.

---

### Post by plumper on 2010-12-25
I also have a Latitude CS with the same problem.   Does this solution actually work - for everyone?  I am using a vanilla Ubuntu install with Fluxbox.

I tried it once on 10.10 vanilla and I got nothing.

************EDIT***************

I've gotten this to work.  My friend and I looked at it and determined that the reason for all of these problems is two audio drivers fighting with each other.  Just uninstall puse audio and all will be better.
[FONT=Courier New]> sudo apt-get remove pulseaudio[/FONT]

---

### Post by vafred69 on 2011-02-06
[B]Same resolution here:

[/B]```
[FONT=Courier New]sudo apt-get remove pulseaudio[/FONT]
```Works fine now!![FONT=Courier New]
[/FONT]

---

### Post by keithspg on 2013-03-15
Here we are 2 years and 4 versions hence and still the same problem. I re installed  totally forgot about this until it rebooted. Then the clicking. I read through this and other threads and the only way I have found to 'fix' it (make sound work) is to uninstall pulseaudio.

Before it is uninstalled, it looks to be fine, just no sound. All the modules are installed pulse is running, that pulse control panel shows everything, just does not work. Not a big problem, especially with a simple fix 'sudo apt-get remove pulseaudio', but odd that is does not work.

Keith

---

### Post by Kixtosh on 2013-03-16
You do have sound though, after removing Pulse, right? Otherwise, when I reinstalled Pulse after removing it, it then worked fine.

The old Dell has given up the ghost and gone to heaven since (not powering on ... I should sell the parts on e-bay or something). This is not likely to be a priority for fixing since Ubuntu has moved on from such lowly hardware many moons ago. I don't think it would be fun using Unity on the Dell if it were working today. These ancient machines should really use LXDE or OpenBox. Puppy 4.3.1. works well on older stuff too. Some of the newer Wary Pup versions also work, but sometimes not so much. It's trial and error. SliTaz can be super speedy on them as well, relatively speaking, but sometimes it's far too buggy to even attempt ... at least for me.

Related links:

[http://www.lxde.org/](http://www.lxde.org/)
[http://openbox.org/](http://openbox.org/)

---

