---
title: "Installing Automatix a prob"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by SuitWink on 2007-08-27
I got the Automatix pack and am trying to install it in Fiesty Fawn. But the install screen shows some error. Says "Error: Dependency is not suitable: Pythone 2.4". Does this mean I got no Python? I though Fiesty already have Python 2.5. So what's keeping me? Pleases someone out there, if you can help, it'll be a big help for me. I just don't wanna end up with Windows Vista yet again. With al it's DRM and things! 

P.S: I'm a newbie. Please make it simple if it can be  said that way too.

---

### Post by Zootropo on 2007-08-27
Automatix is not recommended.
Anyway, you can run the command
aptitude search ~i~npython
to see which packages are installed with python in the name

Or you can just use synaptics

---

### Post by liquidfunk on 2007-08-27
I believe in 7.04, if there is a file it cannot play, it will ask you if you want to download the codec to play it.

 Automatix isn't really that essential. Get out of the frame of mind that it is. 

 Try an MP3 or something.

 If not: Terminal > 

 sudo aptitude install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

 That is all.

---

### Post by aysiu on 2007-08-27
> **liquidfunk said:**
> 
 If not: Terminal > 

 sudo aptitude install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

 That is all. Actually, that isn't all.

First of all, *w32codecs* is not in the regular Ubuntu repositories. You'd have to add the Medibuntu repositories first. I also think the Multiverse repositories (where all those other packages live) are not enabled by default. You have to enable them by following the easy codec installation prompts or going to System > Administration > Software Sources.

Lastly, most new users do not know where the terminal is (Applications > Accessories > Terminal) or that you can copy and paste commands instead of retyping them. Might also be worth mentioning.

---

### Post by por100pre1 on 2007-08-27
The best thing you can do is to forget about Automatix. Read this [tutorial]("http://ubuntuforums.org/showthread.php?t=413624") instead.

---

### Post by SuitWink on 2007-08-30
Wow guys! I just never thought I would get a reply. Wow now I know what they were saying about Ubuntu forums.Okey I'm not installing Auomatix. Someone said installing it would allow my dial up modem to work. But when you all say it like this... Thank you anyways! And sorry for the late reply.

---

