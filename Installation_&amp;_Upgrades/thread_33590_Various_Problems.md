---
title: "Various Problems"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by FyberOptic on 2005-05-11
Hiya folks, I was wondering if anyone could possibly help me out.  I started on the LiveCD, and despite knowing my network and sound didn't work, I thought I'd wipe out my old Fedora install on my laptop and try something new for a change.  But so far, I'm thinking it might have been a mistake, considering all the work I put into making my sound and wifi work on there originally!

I have a Thinkpad 600E, and as anyone who's used these with Linux knows, the sound sucks.  But I usually seemed to be able to get it working somewhat painlessly with enough fiddling, usually just with modules.conf, but so far, I just can't make it work, and can find no posts which give successful results.  ALSA seems to be taking over and messing up everything, loading the CS46xx driver back in constantly at boot, and I don't know enough about it to make it stop.  Not that that necessarily matters, because even when I unloaded all the sound drivers and modprobe cs4232 in manually with the correct parameters and everything, none of the sound-related applications would work anyway.

My other problem is with networking.  My DWL-G650 just will not work.  I mean it's there, it's detected, it's setup, there's signal strength and the lights flash like normal,  but the network doesn't work.  Even from the command line, I set it up just like I did in Fedora with iwconfig, using the correct essid and wep key and all that, set the ip and everything manually since it couldn't find a dhcp server, but no good.  I've found nothing online to help correct this.  It's acting almost as if it won't accept the wep key, but even when I completely disable wep on the router, it acts just the same.

I pretty much decided to give up on that and dropped back from my G card to a B one, a Microsoft MN-520.  Ubuntu won't even detect this card at all.  Again, I checked the forums, and it seems everyone else that had problems with this card never got a straight answer as to how to make it work.

I just really tire of all this effort to make Linux work no matter what machine I put it on.  At least usually I can find the help I need from the web, but it's just of no use this time.  I really don't want to have to go through all of this again for yet another distro, and will probably just wipe the partition for extra storage in Windows if all else fails.  I would just really appreciate any help, if there's any possible solutions.  Thanks in advance.

---

### Post by lt_kije on 2005-05-11
Sorry you're having problems...

RE: Sound; it seems like the problem you're having with the 600e and ALSA is common. There are two links I found in the Ubuntu forums and Wiki that seem to relate; have you read these? They seem to suggest that either your mixer settings or ALSA driver (cs46xx) should be adjusted. Try making sure the laptop's audio controls are turned on; also try modprobing cs4232 (not cs4236).

[1][http://ubuntuforums.org/archive/index.php/t-27421.html](http://ubuntuforums.org/archive/index.php/t-27421.html)
[2][http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsIBM](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptopsIBM)

RE: Network; I have a DWL-G650 running right now in a Thinkpad R51 (Hoary). No tricks at all -- it was autodetected just fine. Unless there's some weird difference between eg DWL-G650 v1/v2, I don't know why you're having trouble (see this[3] link for info on this). I'd check the other network devices you use (eg router) to make sure the settings are all correct.

[3][http://ubuntuforums.org/archive/index.php/t-4057.html](http://ubuntuforums.org/archive/index.php/t-4057.html)

HTH,
lt_kije

---

### Post by FyberOptic on 2005-05-11
Welp, I disabled ACPI, and suddenly the wifi card worked just like it should.  It's weird, because you'd think it would have been broken entirely, instead of acting like it's working and just not.  It's a revision B4, firmware 2.42, for the record.

Still no luck on the sound.  I put in that ALSA config file from the first link you gave (which I tried before btw), and then remove cs46xx from memory and modprobe cs4232, then log out/in, I get the sound icon and the media applications try to play.  But I get no sound output.  And everytime I reboot, I'm back to the constant amixer errors and it having loaded cs46xx again.  Is there some way to make ALSA stop doing this and use the proper driver?


Correction:  Adjusting the volume up and down for PCM and such in the Volume Control program fixed the sound.  I installed the mp3 decoder and it sounds good.  But the problem remains with ALSA trying to load the wrong driver on boot, though.

---

### Post by lt_kije on 2005-05-11
[QUOTE=FyberOptic]Welp, I disabled ACPI, and suddenly the wifi card worked just like it should.  It's weird, because you'd think it would have been broken entirely, instead of acting like it's working and just not.  It's a revision B4, firmware 2.42, for the record.

Still no luck on the sound.  I put in that ALSA config file from the first link you gave (which I tried before btw), and then remove cs46xx from memory and modprobe cs4232, then log out/in, I get the sound icon and the media applications try to play.  But I get no sound output.  And everytime I reboot, I'm back to the constant amixer errors and it having loaded cs46xx again.  Is there some way to make ALSA stop doing this and use the proper driver?


Correction:  Adjusting the volume up and down for PCM and such in the Volume Control program fixed the sound.  I installed the mp3 decoder and it sounds good.  But the problem remains with ALSA trying to load the wrong driver on boot, though.[/QUOTE]
 What does the output of the following look like on your system?
```
 $ rgrep cs46xx /etc 2>/dev/null
```

It'll search for instances of the driver you're using in the /etc directory, where Ubuntu stores configuration information (including files that control what gets started up and how).

---

### Post by FyberOptic on 2005-05-11
The only results from that are:

/etc/hotplug/blacklist.d/alsa-base
/etc/discover.d/alsa-base

They just seem to contain many different driver listings for whatever purpose.  I tried removing every cs-prefixed driver except cs4232 from them but it's the same'ol thing when I reboot.

Something else I noticed is that I'm getting no video when playing movie files, both mpg and avi.  Sound works on them, though.  But this is a lower priority; I just want sound to work correctly on boot for now.


Update:  It seems that if I disable hotplug, it stops loading the 46xx driver, but then of course my wifi and such stops working.  But without hotplug loading that, the cs4232 driver is able to load and work fine.  I also have ALSA disabled for the time being.  But I'm assuming then that it's a configuration issue with hotplug that I need to fix.

---

### Post by derrick1985 on 2005-05-11
[QUOTE=FyberOptic]The only results from that are:

/etc/hotplug/blacklist.d/alsa-base
/etc/discover.d/alsa-base

They just seem to contain many different driver listings for whatever purpose.  I tried removing every cs-prefixed driver except cs4232 from them but it's the same'ol thing when I reboot.

Something else I noticed is that I'm getting no video when playing movie files, both mpg and avi.  Sound works on them, though.  But this is a lower priority; I just want sound to work correctly on boot for now.


Update:  It seems that if I disable hotplug, it stops loading the 46xx driver, but then of course my wifi and such stops working.  But without hotplug loading that, the cs4232 driver is able to load and work fine.  I also have ALSA disabled for the time being.  But I'm assuming then that it's a configuration issue with hotplug that I need to fix.[/QUOTE]

There are no other sound devices in your laptop are there? EX: Microphone/Webcam with microphone? I know on a previous distro I used, if I had my webcam in during startup, it would think that the webcam was the sound and of course fail to boot right.

---

### Post by FyberOptic on 2005-05-11
[QUOTE=derrick1985]There are no other sound devices in your laptop are there? EX: Microphone/Webcam with microphone? I know on a previous distro I used, if I had my webcam in during startup, it would think that the webcam was the sound and of course fail to boot right.[/QUOTE]
 Na it's pretty much the bare laptop aside from the wifi card.

I did find I could prevent the cs46xx and snd-cs46xx from loading by blacklisting it from hotplug.

But having cs4232 in /etc/modules seems to freeze gnome at startup, when it plays its initial sound effect.  I can hear like this loop of noise playing over and over real quick if I listen close.  If I load no sound modules on boot, then "modprobe cs4232" after it's all started up, I can log into gnome just fine and have sound (after adjusting the volume).  So now I'm not sure why I can load it after boot but not before.

The snd-cs4232 module (for alsa I assume) still gives an error when I load it no matter what, but since sound seems to still work in gnome without it, I don't guess it's much of a concern.

---

