---
title: "Upgrading Gnome Commander"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by LeeU on 2008-08-19
I am using Gnome Commander v.1.2.4 and the current version is 1.2.7 but it is not in the Ubuntu repositories. I'm not familiar with installing/upgrading w/o using the Synaptic Package Manager. Can anyone give me some guidance? I'd appreciate. (I'm running Gutsy 7.10)

---

### Post by SabreWolfy on 2008-11-08
I'm having the same problem. The latest version in the Hardy repositories is 1.2.5, which is now quite old. Version 1.2.7 is available which includes many fixes. I've downloaded a .deb package of 1.2.7, but there are too many broken dependencies, so I could not install it. :-(

---

### Post by SabreWolfy on 2008-11-08
Edit: Instructions to compile from source [here]("http://ubuntuforums.org/showthread.php?t=971526"). Not sure how the posted in that thread had success installing 1.2.7...

I tried to install 1.2.7 from source, but (as is so often the case!) it didn't work. The line in the thread above that refers to "build-dep" required me to included "sources" in my software sources settings. I did this and tried the command again, but then I had to download and install 18MB of source files, which I decided I didn't really want to do just to install a file manager.

I then returned to trying to install 1.2.7 from the .deb file by manually finding and installing the dependencies. This "worked" for the first level of dependencies, but then one of them depended on a different version if libc6, so that's where I gave up. I've installed gcmd 1.2.5. *sigh* For this and various other reasons, I'm feeling somewhat anti-Ubuntu at the moment, so this waste of time and bandwidth only added to that! ](*,)

---

