---
title: "Problem with graphics card after linux upgrade"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by ali999 on 2008-06-15
Hi
I am having some issues with my Nvidia 9600gt graphics card here. Everything was working fine until today when I logged into Ubuntu and it told me there were some updates available. I usually just install these trusting that they are fully working and everything. However, after insalling these updates and rebooting my comp, the 3d effects on my nvidia 9600gt card stopped working. I am not really sure qhy this is. While installting the update i did notice there was one for compiz, so i'm concerned weather this is a problem with the update itself. HOwever, at the same time the driver I had installed and working was still beta so I dunno if that is the problem. Does anyone else have this issue? or does someone have any suggestions? Please help. 

Thanks in advance

---

### Post by PmDematagoda on 2008-06-15
Do:-
```
sudo modprobe nvidia_new
```
and restart the X-Server by pressing Ctrl+Alt+BackSpace.

But before that, how did you install the Nvidia driver in the first place?

EDIT:- Oh wait, you installed the driver manually, in that case you would need to reinstall the driver, download the driver from [here]("http://www.nvidia.com/object/linux_display_ia32_173.14.05.html"), I trust you know how to install it?

---

### Post by mrhelpman on 2008-06-15
I too have just had to re-install the nvidia driver following an update to the X server. I install the nvidia drivers manually because I use multiple kernels; I use a real time kernel for audio recording and find manual installation easier when using multiple kernels.  Can you just confirm that this re-installation was only needed because of the update to X? I am a little out of date in that I am still using Dapper.

Thanks in advance.

John T.

---

### Post by ali999 on 2008-06-20
sorry for the delay in replying back. I installed the latest version of the driver today (173.14.09) and it seems to be working perfectly so far. Installation method is same as the 171.06.

---

