---
title: "Ubuntu Studio 16.04 Sound Settings Not Available"
date: 2016-08-03
forum: Installation &amp; Upgrades
---

### Post by mdbratch on 2016-08-03
Recently installed Ubuntu Studio 16.04. I originally upgraded from 14.04, but weird things began to happen. Most of the systems settings icons disappeared (there were 4 left out of many). Nothing I did would rectify it. Googled potential solutions and tried them, and none worked.

I finally threw in the towel and installed 16.04 from scratch. I spent the last 2 days resetting up my stuff. I use the system not only for music, but Ruby/Rails development using MariaDB, and PostgreSQL. I finally got all that working agian, and now I am getting ready to try to do some sound and I have no sound. I have 2 or 3 different sound devices so I figured I'd check the settings. I go into system settings and.... there's no sound settings icon! There's just about everything else, but no sound settings. Anywhere. I recall I had a volume/settings icon on the task bar when I first installed it but at some point it disappeared. I have no idea when it did, as I wasn't looking for it. I went back to Googling and trying things and nothing has fixed it. For example, several suggestions on this link: [http://askubuntu.com/questions/483397/missing-sound-volume-icon-on-screen-top-14-04](http://askubuntu.com/questions/483397/missing-sound-volume-icon-on-screen-top-14-04) which are similar to others didn't work.

Just to get some real work done, I'm now contemplating dumping Ubuntu Studio and running Windows 7 or 10. I know it costs money and I never thought I'd want to consider this dark path. Ubuntu is a nice system, as is Ardour particularly. But, free (although I happily paid some money to the Ardour folks) and cool is no good if it's not working. I'm hoping someone has some ideas. Fighting with the basics is really getting old.

---

### Post by Bucky Ball on 2016-08-03
Welcome. Ubuntu Studio is specifically for multimedia production and there's a lot there that you will probably never want or use. It also uses Jack primarily for sound although Pulseaudio is in there somewhere.

I suggest you do a clean install of Ubuntu 16.04 LTS and if you have a repeat of your problems, start a new thread about each (one thread a question, please) and hopefully someone can help you. In-machine net upgrades can be problematic, as you've found. You need to update/upgrade your install first and switch off any PPAs you've installed manually, among other things, before commencing the upgrade to a new release.

You don't need UStudio to run Ardour, it will run on any Ubuntu flavour. This applies to most software in the repos. Rather than installing a full UStudio, to make it easy, if you look in your package manager for 'ubuntustudio-' you will find UStudio bundles specific to area, i.e. ubuntustudio-audio, ubuntustudio-photography, ubuntustudio-video, etc. Installing one of these will install the default UStudio packages/apps relevant to the area. It is a rare user that will have a need or desire for everything that comes default in UStudio.

(Final note: Ubuntu Studio uses the xfce4 desktop environment rather than Unity, as you would have noticed. If you prefer that, Xubuntu uses the same DE and you can install whatever you like in that. Lighter than Ubuntu and if you are into multimedia/AV, you want as light as you can get so the resources are used for multimedia production goodness :)).

Hope that helps a bit ... good luck.

(* Just a thought: UStudio may not install Pulseaudio Volume Control by default or it may not be visible by default. Right click on the task bar> add items and see if there is a selection for it or if you have it installed.)

---

### Post by mdbratch on 2016-08-03
I've studied up on Ubuntu Studio quite a bit and had a bit of experience tinkering with US 14.04 before I installed 16.04. I already did, indeed, do a fresh install of 16.04 (if you read through my note, I mention that). That's how I got here.

Ironically, I was able to at least get some sound to work by using ALSA. I had to open a terminal and run alsamixer to set levels. alsamixer recognizes all of my sound devices. Jack doesn't. It only sees the internal one on the motherboard.

I searched the right click menu for a way to add a sound icon. Nothing there. I logged in as root through the GUI and that desktop shows a sound icon. However, it is set to MUTE and is greyed out, so won't let me unmute. If I click the settings button, it hangs on "waiting for Pulseaudio".

---

### Post by Bucky Ball on 2016-08-03
You don't want to be logging into your machine and using it as root. Avoid. :|

---

### Post by mdbratch on 2016-08-03
> **Bucky Ball said:**
> You don't want to be logging into your machine and using it as root. Avoid. :|
Right. I have no intention to use root that way. It was the only other "user" I had handy to try a login for to see if it had a sound icon and it did, but with the issues I described. I'm a fairly savvy Linux user. I've used Linux since back when you had to rebuild the kernel to get certain features.

---

### Post by mdbratch on 2016-08-04
I was able to get my sound settings back on the task bar. With some experimentation, I found there's a setting in my `~/.config/xfce4` folder. I forced the reconstruction of that folder and, voila, the sound settings are back.

Now on to figuring out how to get Jack to see my sound devices again...

---

