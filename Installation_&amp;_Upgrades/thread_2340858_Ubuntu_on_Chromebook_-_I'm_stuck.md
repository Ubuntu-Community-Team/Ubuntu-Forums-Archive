---
title: "Ubuntu on Chromebook - I'm stuck"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by stevlor on 2016-10-22
Hi Ubuntu/Linux absolute newbie here. I wanted to use Skype and OBS studio on my chromebook so I looked at installing linux. I followed the steps at [http://lifehacker.com/how-to-install-linux-on-a-chromebook-and-unlock-its-ful-509039343](http://lifehacker.com/how-to-install-linux-on-a-chromebook-and-unlock-its-ful-509039343) and got was running Ubuntu 12.04, I downloaded Skype and managed to use the crouton extension in chrome so that it opened up in a very accessible tab on my chromebook. However, OBS-studio is only available for 14.04 Ubuntu and later (so I read) so off I set this morning trying to update it from 12.04 to 14.04.

I'm now running Ubuntu 14.04 (at least this is what it says when I type the lsb_release -a command) - but now I have two problems:

1) from chrome, when I open a terminal and type sudo startxfce4, nothing happens - I just get:

Entering /mnt/stateful_partition/crouton/chroots/precise...
/usr/bin/startxfce4: Starting X server
/usr/local/bin/xinit: 34: exec: /usr/bin/xinit: not found
Unmounting /mnt/stateful_partition/crouton/chroots/precise...

I can only get into Ubuntu by typing "sudo startxfce4 -n trusty"

Is this normal? And I can't seem to use crouton any more at all - it just doesn't connect, I can only switch between Chrome OS and Ubuntu by the shortcut ctrl+alt+**** left/right - any way to fix this?

2) More importantly, whatever steps I follow to install OBS-studio, I fail. I follow their instuctions: [https://github.com/jp9000/obs-studio/wiki/Install-Instructions#ubuntu-installation](https://github.com/jp9000/obs-studio/wiki/Install-Instructions#ubuntu-installation)

I get to the final line: [COLOR=#333333][FONT=Consolas]sudo apt-get update && sudo apt-get install obs-studio

[/FONT][/COLOR]it seems to be installing fine, and then this is what I get:

"some packages could not be installed. This may mean you have requested an impossible situation..." 

Can anyone help?

---

### Post by TheFu on 2016-10-22
12,04 support ends in a few months.  14.04 is a better choice, but many of the GUI programs won't have support anymore, just the core programs that Canonical supports.  16.04 is the recommended stable version to be using today. Don't know if crouton supports it or not.

crouton isn't really running a complete Ubuntu. It runs the chromeOS kernel without the ability to load any kernel modules that google doesn't approve.  NFS for example, can't be easily loaded. That may or may not matter to you.  It did to me. Google sees this as a security issue, and they are correct.  I believe a stock, supported, chromeOS is the most secure OS today ... except for all the google spying. 

Anyway, doing an OS upgrade from inside the chroot/crouton doesn't modify the crouton settings, so crouton thinks you still have 12.04 though everything is really 14.04. Probably not good, though you'd have to look at the crouton code to be sure of how bad the issues are.  If you want to keep using the crouton environment, it would be best to wipe all crouton installs and start over with 16.04 or 14.04 (only if you must), IMHO.  

I haven't run crouton in about 8 months and only ran it for a few months total, so my knowledge is far from complete.  I am a long-time Linux user, developer and admin, however.  That doesn't mean I know everything and I'm often wrong, but I do have lots of experience.

For me, having control over the running kernel and the modules loaded is very important.  OBS works fairly well, if you have enough CPU and RAM to handle the workload.  With just a single hidef video input, a fast celeron should be fine. If there are multiple hidef video sources, then an i3 model is probably best.  Audio inputs don't matter too much - I usually have 3 or 4.

I hope you used the OBS PPA to deal with installation, not source.  The obs-project website has that PPA location and instructions. Ensure you are running to correct version for the crouton OS.  

I can't help at all with skype. Sorry.

---

