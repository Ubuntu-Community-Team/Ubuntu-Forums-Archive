---
title: "Firefox and flash."
date: 2016-10-23
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-10-23
Just wondering, what flash player is firefox using.  I did not install any.

Henry

---

### Post by howefield on 2016-10-23
Flash isn't installed by default, so if you are actually using it you must have installed it.

Do you see any flash extension if you type

```
about:plugins
```

into the Firefox address bar.

---

### Post by Hewjr100 on 2016-10-23
Yea it's there, but during install of ubuntu 16.04.1 I checked download updates and third party software, so it must have been install from restricted extras or something.

Henry

PS how do I attach/insert screenshots, only choice is a url.

---

### Post by howefield on 2016-10-23
> **Hewjr100 said:**
> Yea it's there, but during install of ubuntu 16.04.1 I checked download updates and third party software, so it must have been install from restricted extras or something.

Yes, from memory I believe flash is explicitly mentioned in the 3rd party software before selecting the option, so that it where it would have been installed, it uses the ubuntu-restricted-addons package which is distinct from the ubuntu-restricted-extras package and includes the following...

> Recommends: gstreamer1.0-plugins-ugly, flashplugin-installer, gstreamer1.0-plugins-bad, gstreamer1.0-libav, gstreamer1.0-fluendo-mp3, chromium-codecs-ffmpeg-extra, oxideqt-codecs-extra

> PS how do I attach/insert screenshots, only choice is a url.

Best way would be to use the paperclip icon to attach the image to your post, available from the "*Reply to thread*" option but not the "*Quick Reply*" window.

---

### Post by Hewjr100 on 2016-10-23
Thank you.

Henry

---

