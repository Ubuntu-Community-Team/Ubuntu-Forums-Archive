---
title: "Nvidia and polkit. when is it going to be fixed????"
date: 2024-05-04
forum: Installation &amp; Upgrades
---

### Post by Mandle on 2024-05-04
for the past couple of years, EVERY SINGLE TIME, I install ubuntu, I MUST run 

sudo chmod u+x /usr/share/screen-resolution-extra/nvidia-polkit 

or nvidia-settings will not save.
This can't be a hard fix. I haven't posted till now, because I figured it would have been fixed by now, yet somehow, still nofix. Maybe I'm not understanding something between the devs and nvidia, ie open vs closed, but seriously, it's such a minor thing. I can think of a dozen ways that this could be implemented. Run a script. Put it on the nvidia how to page, tel nvidia to include it in their install drivers somehow, etc....

Most users do not have the technical know how to do this on their own necessarily. And since you're trying to make linux available to the masses, you'd think that in 3 or 4 years that can recall having to plug this command in, it would have been fixed by now.
Maybe I should be sending this to the nvidia forums. Let me know if I should. As I will, once someone can help me understand why this is even an issue.(just link a thread, I'll read)

Edit, to add the other issue with nvidia. Adding nvidia-drm modeset=1 to boot. there error shows up in the logs, also been having to do it for some time, mostly
[drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00002d00] Failed to grab modeset ownership

maybe an explanation in the wiki. Hell, I got time, I'd do if I could. I tried... we'll see what happens in the irc....

---

### Post by Mandle on 2024-05-04
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1822937](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1822937)

5 years to add one line of code? What am I missing here??? Like I feel like I must be missing something....
(and yes, I know, it looks like only one line to me, but seriously, you can't expect any of us to believe that it would take more than a few lines to add this in....)

---

### Post by zebra2 on 2024-05-04
Your dilemma is one of the reasons that I only buy systems with the Intel Chipset.  Intel is a leading member of the Linux Foundation and actually cares that their systems support Linux.  
I really don't know why there are problems with Nvida but consider this,  If you have to do something (run a code) to get Nvida to work on your system then you are hacking the Nvida drivers and not Ubuntu.  Just an idea. 
While you are at it you may want to do a search for "Members of the Linux Foundation" and see who isn't there. You may enlighten yourself. 
Nvida own's their products and I am certain that they work very well where ever they want them to work. 
I personally have been reading posts about these Nvida issues since I started with Karmic Koala.
Just fasten your seat belt and enjoy the ride.

---

### Post by Mandle on 2024-05-04
I don't like spending money on intel. I've always been happy with AMD. I get it though. 
Polkit is a linux package.... I'm thinking there's maybe an issue between the 2 security wise maybe? or just just some stupid politiking nonsense? I dunno. I don't think anyone really cares at this point. Nvidia has been at least trying to appear to be trying lately re: open source. But still not there yet either I know. Nvidia and AMD are both members btw... silver level, but there listed. what kind of irks me is microshaft being a gold member....sorry, platinum....wonder how much money they threw in there to get that.....(I joke now, but being a member of the linux foundation, seems to mean zilch nowadays..imho)
maybe the package maintainer hates nvidia.... dunno, don't care, the bug report is from 2019, but my research on this shows issues around polkit 2016?? why...it makes no sense....it's maddening to know you have to do something to make it work, and then I spent a few years googleing the whole error before realizing I could just google nvidia polkit and get the line...but geez....
I love the ride, but seeing something like this over and over and over again, from a community that says it cares about user experience, but doesn't fix an easily correctable but in over 5 years????

---

### Post by zebra2 on 2024-05-04
I actually agree with your OP. 
Re: Microsoft's platium membership. They support Linux for the same reason that they gave Apple ten million bucks back in the eightys to keep them from failing.  They need Linux and Apple both to exist so that they will have competition and not be a monopoly. MiIcrosoft owns the UEFI Secure Boot but provides the Linux kernel with a shim so it will work on Linux systems.  Same thing, they are avoiding the illegal monopoly status. 
I don't know much about the Nvida complications but back in the nineties a friend of mine spent 180 bucks for a Nvida video card which was pretty expensive in those days. I thought it was dumb but he really loved that video card. For as much as it cost and as much inroad as Steam has in the Linux gaming community you would think they (Nvida) would invest some effort to ensure that it all works. I'm not saying it's not a great product, I'm just saying I don't need it. Also, for the last few years intel has presented some very good graphics of their own. They are a legit competitor of Nvida.

PS. Incedentaly In exchange for the ten million MS requried Apple to allow Internet Explorer to run on the Apple system. Which they did!

---

### Post by Mandle on 2024-05-05
My next video card may be an intel. As I said, Nvidia has been trying to appear to be trying. They did hire the former maintainer of the nouveau driver, and he is apparently working on it now, from within nvidia... So I really do expect good things in the future. But I've got this nagging thought in the back of my mind, (I doubt it, but it's there) that nvidia hired him to sabotage the open source driver. But he posted 156 patches last month, so that's a pretty big something... And I don't really have any issues once I get the thing installed properly. Hell, there's are really just minor annoyances. But there is no reason for them to still exist after 5 years. Plus.... They're both minor, and i'm not sure about the drm issue, but def the settings issue is not going to stop anything from working. Minor annoyance...
I didn't know that about apple and IE. I really could care less about the worst pc company on the planet... I've dealt with enough pc issues, to know I never want to deal with mac issues. They'll make my brain explode. (i'm a pc/electronics repair tech) Go watch some Louis Rossmann videos if you haven't...(he's doing good work on right to repair now, and rarely posts vids on actual repairs now, but his earlier vid's are literally an encyclopedia of how to repair basically every mac available, and includes lots and lots of examples of how apple screws over the consumer.
Oh, and I really don't think the problem is nvidia. I've been doing some major distro hopping lately, and some distro's don't seem to have the issues. I've done so much that maybe I'm misremembering, but garuda and endeavour, both seem to just work after the installation guide. I would be using on or the other, if I could just get it to work raid0. arch doesn't like me and boot...and way too much conflicting info, and I love how all the arch peeps just point to the wiki, but it hasn't been updated, so the instructions don't work. Even with the level of knowledge I have, I've spent days trying to figure it out. but should be easy to setup one or the other now, and just use my xubuntu grub.

But if any dev's, or someone with knowledge of why these are still issues wanna chime in???? I guess it's the weekend, so I'll check back tomorrow night?(same for the wiki irc, no response there either...)

---

