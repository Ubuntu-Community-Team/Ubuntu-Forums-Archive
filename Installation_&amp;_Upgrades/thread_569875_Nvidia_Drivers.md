---
title: "Nvidia Drivers"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by brad1138 on 2007-10-07
I installed the latest Nvidia driver, and it _is_ activated. Is there a place to find all the nice settings you find in "Windows" version of Nvidia Driver. In windows there are dozens, if not 100's of settings. All  I can find on Ubuntu (7.04) are resolution and refresh.

Thanks,
Brad

---

### Post by oldos2er on 2007-10-07
Type nvidia-settings in a terminal.

---

### Post by forestpixie on 2007-10-07
if you want to make changes though you'll need to use

```
gksudo nvidia-settings
```

while there are not as many options as in the ms version - you should find more than resolution and refresh - if there's not then I would check that you actually do have the restricted drivers installed

---

### Post by brad1138 on 2007-10-07
Thank you, I created a launcher for it (I am a newb so thats a big deal :) ) actually that wasn't the big deal, when I created the launcher I tried to pick a custom icon but the Nvidia icon in "pixmaps" wouldn't work, It was labeled a gif but info on it said it was a png. I tried to rename it and it said I didn't have permission to make changes to the folder. I searched and found that if I type sudo nautilus, it would give me permission. So I did, created another copy of the file but renamed it .png and it worked great. 

Little things are cool to us newbs :)

Thanks,
Brad

---

