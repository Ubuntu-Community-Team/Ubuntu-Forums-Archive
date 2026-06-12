---
title: "Nvidia 180.37 install question."
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-03-14
Need some advice; running jaunty alpha 6-amd64. 
I'm using nvidia driver v173.14.16 because 180.35 crashes; big-time! I'd like to upgrade to v180.37 but all that was listed in Synaptic Package Manage yesterday was v180.35. So, I downloaded every deb from [http://www.avenard.org/files/ubuntu-repos/release/](http://www.avenard.org/files/ubuntu-repos/release/) that said 180.37 for amd64 that I could find. Not all would install. This morning there were some upgrades available in the Synaptic Package Manage that included some that did not install before.

So, I have the following loaded in the Synaptic Package Manage;
[I]nvidia-180-libvdpau, v180.37-0ubuntu1
nvidia-180-libvdpau-dev, v180.37-0ubuntu1
nvidia-setting, v180.25-0ubuntu1
nvidia-180-kernal-source, v180.37-0ubuntu1
nvidia-common, v0.2.9
nvidia-180-modaliases, v180.37-0ubuntu1
nvidia-glx-180, v180.37-0ubuntu1[/I]

I check System/Administration/Hardware Drivers but it's not specific which is being installed, 180.35 or 180.37 & I definitely don't want 180.35! Will these install via System/Administration/Hardware Drivers or with the terminal?

---

### Post by plun on 2009-03-14
if you are using a repo up-to-date this will install 180.37

```
sudo apt-get install nvidia-glx-180
```


Package info:
[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)

---

### Post by GARoss on 2009-03-14
> **plun said:**
> if you are using a repo up-to-date this will install 180.37

```
sudo apt-get install nvidia-glx-180
```


Package info:
[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)

Thanks. 
It said that it was already installed; & it was. 
Sometimes, I'm not sure what to expect. I had opened *System/Administration/Hardware Drivers*, selected *180 Recommended* to activate. It went into *Downloading* & did nothing for several minutes, causing me to think it was searching for the dreaded v180.35 to install! I force cancelled & posted this thread. 
When I did *sudo apt-get install nvidia-glx-180* as you suggested it said it was already updated. But, I never re-started the computer, so how could it be activated? I checked Hardware Drivers again & indeed it is activated. This is weird, but it doesn't matter, I guess. It's working! :D
Thanks again.

---

