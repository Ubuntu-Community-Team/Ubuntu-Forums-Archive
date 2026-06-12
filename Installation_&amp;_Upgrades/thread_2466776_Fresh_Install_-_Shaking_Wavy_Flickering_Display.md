---
title: "Fresh Install - Shaking Wavy Flickering Display"
date: 2021-09-05
forum: Installation &amp; Upgrades
---

### Post by sjackling on 2021-09-05
I just installed Ubuntu 20.04 on my laptop. The screen is jiggling like jello constantly ([https://drive.google.com/file/d/12_ti0YLkELSaGQ3NRHI5fNW62RiOHHZM/view?usp=sharing](https://drive.google.com/file/d/12_ti0YLkELSaGQ3NRHI5fNW62RiOHHZM/view?usp=sharing)). I have the Nvidia 470 drivers installed. It has been a long time since I used Ubuntu and I am unsure what other information might be helpful to diagnose my problem so if I can add anything else please let me know.

---

### Post by MAFoElffen on 2021-09-08
Which desktop are you using and which kernel?
```

uname -r
echo $XDG_CURRENT_DESKTOP 
echo $DESKTOP_SESSION
echo $XDG_SESSION_TYPE
apt -cache show linux-generic-hwe-20.04

```

---

### Post by sjackling on 2021-09-09
Unfortunately I needed to have my laptop in working order for zoom and other things so I reverted to windows. I am 98% sure the kernel version was 5.11.0-34 and the desktop would have been whatever the default is in ubuntu 20.04. When I get some free time I will take another crack at it but I did read somewhere that it had something to do with the kernel version. I found two youtube videos showing the same problem (also on the same laptop) and according to those comments the issue appeared around kernel version 5.11.0-22 and persisted into 5.12.x-x. Ubuntu issue - [https://www.youtube.com/watch?v=xnI_zkabeCo](https://www.youtube.com/watch?v=xnI_zkabeCo) Fedora issue - [URL="https://www.youtube.com/watch?v=0u_CA6saNFc"]https://www.youtube.com/watch?v=0u_CA6saNFc
[/URL]

---

### Post by MAFoElffen on 2021-09-09
Unfortunately, yes... See my post on that here: [https://ubuntuforums.org/showthread.php?t=2466903]("https://ubuntuforums.org/showthread.php?t=2466903")

But even before that, some machines with NVidia had this shaking kind of thing going on. Most of the time, that was happening when users were using Wayland. The way to see if that is what is going on with yours, is at the Graphical Login Screen, press the gear icon and try different Desktops and see if they display better. Most were having better XServer or Metacity compositors.

---

