---
title: "No Multimedia sound (ie. only OS sound)"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by StevoDevo on 2009-11-17
Just upgraded to 9.10: the Karmic Koala Release. I have looked at the sound issues information but it seem to be so much deliberation on sound card problems assuming no sound is occurring. In my case the sound is working in the OS and the welcome (desktop startup) and close (desktop shut down) sounds both operate normally but no sound works in either my browser (i.e. for youtube videos) or any multimedia applications such as Codine or Minirok. Any ideas gratefully appreciated.

---

### Post by hellmet on 2009-11-18
See if sound is muted on "Sound Preferences">Applications tab for the applications you're using. Ex: Firefox

---

### Post by snuggs on 2009-11-18
> **StevoDevo said:**
> Just upgraded to 9.10: the Karmic Koala Release. I have looked at the sound issues information but it seem to be so much deliberation on sound card problems assuming no sound is occurring. In my case the sound is working in the OS and the welcome (desktop startup) and close (desktop shut down) sounds both operate normally but no sound works in either my browser (i.e. for youtube videos) or any multimedia applications such as Codine or Minirok. Any ideas gratefully appreciated.

I had the same problem.. here's what i found to work 
 	Code:
 	sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree 
i had to code each in individually... but it worked for me

found here [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

---

### Post by StevoDevo on 2009-11-19
> **hellmet said:**
> See if sound is muted on "Sound Preferences">Applications tab for the applications you're using. Ex: Firefox

Thanks Hellmet I can't find the "Sound Preferences" menu or dialogue anywhere. Are you talking about a specific menu item or dialogue? The closest thing I seem to have is the "Systems Settings" dialog...:

[CENTER][IMG]http://i48.tinypic.com/2dkziop.jpg[/IMG][/CENTER]

...which has the 'Multimedia' section on the bottom line there,... 

[CENTER][IMG]http://i48.tinypic.com/jiyg0k.jpg[/IMG][/CENTER]

but that doesn't have an 'Applications' tab. It's all about the hardware here.

Thanks for the reply though.

---

### Post by snuggs on 2009-11-19
btw stevodevo

this also happened to me after the upgrade to karmic.. sounds worked for me in 9.04, after update i had to uninstall the flash and reinstall

my sound worked on startup and exit, however no rhythmbox, or online hulu, youtube (could see vid but no sound), websites with music, anything. 

forgot to include that before.. but maybe it's a diff problem than yours.

---

### Post by StevoDevo on 2009-11-19
> **snuggs said:**
> I had the same problem.. here's what i found to work 
 	Code:
 	sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree 
i had to code each in individually... but it worked for me

found here [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

OK. I opened up synaptic to see what I have. Interesting.I dont have the swfdec-mozilla module installed nor the flashplugin-nonfree, nor the 'mozilla-plugin-gnash' one. I do have adobe-flashplugin, but I can't seem to get rid of it. Either by selecting to unistall from Synaptic, or using aptget with the --force- option. When I do it in Synaptic I get this message: 

```
E: adobe-flashplugin: subprocess installed pre-removal script returned error exit status 2 
```

While the command line returns:

```
(Reading database ... 407664 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
dpkg: warning: ignoring request to remove --force- which isn't installed.
Errors were encountered while processing:
 adobe-flashplugin 
```

Close and restart Synaptic and there it is; still marked as installed in the list. I also thought I might try uninstalling it through my browser, but that doesn't show uninstall options, only disable, so I am stuck it seems. The flash install makes some sense to me because the non-free alternative has an 'extra-sound' module. The trouble is these would not install, as they too aromatically selected the plain 'adobe-flashplugin' to be removed. and that wouldn't go.

Addendum:
~~~~~~~~~ 

I have since tried again, this time with the flash plugin disabled in F/fox and after a reboot. Now I just selected the plugins I wanted (without first trying to remove 'adobe-flashplugin') and hey presto, they all installed without complaint. :D Even removed the old 'adobe-flash plugin'. I am going to shut down my browser (after I turn the plugin on in the add-ons dialog), then I will reboot, to make sure all drivers are loaded as configured. Wish me luck. Thanks for the advice too. ;)

---

### Post by StevoDevo on 2009-11-19
> **snuggs said:**
> btw stevodevo

this also happened to me after the upgrade to karmic.. sounds worked for me in 9.04, after update i had to uninstall the flash and reinstall

my sound worked on startup and exit, however no rhythmbox, or online hulu, youtube (could see vid but no sound), websites with music, anything. 

forgot to include that before.. but maybe it's a diff problem than yours.

Sound's very similar snuggs. Time to reboot and try this baby out with a new flash install then. ;)

---

### Post by StevoDevo on 2009-11-19
> **StevoDevo said:**
> Sound's very similar snuggs. Time to reboot and try this baby out with a new flash install then. ;)

No deal still no joy. I noticed elsewhere, that the latest 'cantankerous koala' or whatever, uses Pulse Audio and in the flashplugin-nonfree-extrasound info it mentions: 

[CENTER]> This is an open Source extension library for the Adobe Flash Player that enables support for otherwise unsupported sound systems.  It provides the libflashsupport.so plugin. The sound system to use is automatically detected:

 * It first tries to detect Esound,
 * Next, it checks for OSS.

If all of the above failed, it falls back to the ALSA driver that's
built directly into FlashPlayer 9.

For PulseAudio support, see flashplugin-nonfree-pulse.
[/CENTER]

I'm looking at that last line and thinking A) Maybe the system only wants to use pulse now. B) Where in the hell is "flashplugin-nonfree-pulse"? Is that meant to refer to a package? It isn't in my list. (Oh! I had better check my repositories too, some of them were switched off in the install) perhaps the 'flashplugin-nonfree-pulse' refers to some settings mentioned in the docs, but I only have a README. Damn this is getting annoying. ](*,)

---

### Post by StevoDevo on 2009-11-19
And I guess that [:arrow:**[COLOR="Red"]THIS[/COLOR]**:arrow:]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=477266") means that my Pulse Audio hunch is just a dead end too, so I guess I'm back up s**t creek without a paddle. :icon_frown:

Some more info: When I installed the new OS, I had some problems as it finished as it complained about a dependency issue with installing or updating some software and got this message:

> E: : emacs22 subprocess installed post-installation script returned error exit status 255

I uninstalled emacs22 because there was a 23 and I thought it might be more up to date, but I got the same mesage when I tried other install modifications, only with the 23 complaining instead of 22:

> E: emacs23: subprocess installed post-installation script returned error exit status 255

I have since uninstalled emacs23 completely and I haven't gotten the massage since.

Also. Since disabling the old flash player, I have noticed one other thing which has changed. In the above mentioned dialog box i.e:

[IMG]http://i48.tinypic.com/jiyg0k.jpg[/IMG]

I failed to mention, that despite the fact that audio worked in the OS playing 'welcome' sound and in the some of the applications which had been installed with the upgrade such as KM Player Others (the legacy apps it seems) did not work. In the dialog above I noticed that in the video list, none of the listed devices played sound when I used the test button, but that changed after disabling the flash and I noticed (when going in to snap the above screen shot), that the analog entry is now working on test. It is the only one working though (in any of the lists) so I moved it up as the preffered device in each list, but still there is no youtube / flash playing in my browser, unless I restart and find it working.

Finally. This goes back well beyond the last upgrade. Some of my downloaded flash files (the temporary ones stored in /etc which I often move), are recorded with distortion which puts them beyond recognition (even if they have played normally in the web browser). It isn't all of them (even now), but at first I thought it had gotten worse, in fact It looked like all of them until this evening, but it does seem worse.

I do hope this helps. Isn't there a quick nasty way to 'fix' all this? Can I revert just the browser and sound system. While it wasn't perfect it worked well enough to get me by. This isn't going to do at all I need the sound to work for sure. [-o< Dear FSM I don't ask for much but... [COLOR="Purple"]LOL[/COLOR]

---

### Post by StevoDevo on 2009-11-19
I solved the sound problems by uninstalling the pulse audio drivers. :cool: Now everything seems to work again. With one tiny hiccup. The earlier upgrade/extention to the flash player seems to be producing a flicker / random blink in the player (the resulting downloaded file is fine and plays very well though). I think I'll call this a solved problem. I'll have a go at rolling back the changes to the flash player, and if I have any more trouble, I will post a new thread for the flash problem. Thanks for the advice snuggs & hellmet. Peace.

---

### Post by StevoDevo on 2009-11-19
Also solved the flashing flash video in youtube et. al. Was mostly by accident though. I did a search for flash roll back,  and came to a page (which to be quite fair does mention my symptoms). The instructions I followed meticulously however was [COLOR="DarkOrange"]NOT[/COLOR] intended to roll back the Shockwave Flash plugin, but the main video driver. I realized that I might not have followed the correct instructions, the exact split instant, AFTER I hit the return key, to commit to the changes.

As it happened I landed on my feet, because the older driver works even better and now I have no flash flashing in my browser. \\:D/ TALHEA.

---

### Post by snuggs on 2010-01-08
> **snuggs said:**
> I had the same problem.. here's what i found to work 
     Code:
     sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree 
i had to code each in individually... but it worked for me

found here [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

wanted to give this a bump.. in case anyone else needed it.
I just had a typical update and my youtube sound wasn't working again..so i repeated the process above.. didn't even need a restart.
thought maybe others would run into something similar... 

cheers


oh and stevodevo.. glad we could help!

---

