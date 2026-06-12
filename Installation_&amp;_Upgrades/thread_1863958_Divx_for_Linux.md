---
title: "Divx for Linux?"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by DrArroganto on 2011-10-18
Is it possible to have Divx on linux? I know there's no linux version of divx in their site... (Talking about the web player, not the video file)

---

### Post by khelben1979 on 2011-10-18
The newer versions of VLC have all the video codecs inbuilt, including the div X codec. And if you're thinking about looking at div X content on webpages, you can let the web browser take advantage of VLC by it's [VLC plugin system for the Firefox browser]("http://wiki.videolan.org/Useful_Firefox_Extensions").

```
apt-get install vlc
``` to install it to your system.

---

### Post by lovinglinux on 2011-10-18
Unfortunately, no. But you can play divx content with similar linux plugins.

> **khelben1979 said:**
> The newer versions of VLC have all the video codecs inbuilt, including the div X codec. And if you're thinking about looking at div X content on webpages, you can let the web browser take advantage of VLC by it's [VLC plugin system for the Firefox browser]("http://wiki.videolan.org/Useful_Firefox_Extensions").

```
apt-get install vlc
``` to install it to your system.

I use VLC as primary player, but the plugin is terrible in my opinion. Instead, install gecko-mediaplayer. Ubuntu comes with totem-mozilla by default. If you want to use gecko, you need to remove totem-mozilla.

---

### Post by DrArroganto on 2011-10-18
Thanks :)

@[khelben1979]("http://ubuntuforums.org/member.php?u=443262"), The VLC plugin doesn't work for me.. The divx player just goes black and doesn't start..

@[[COLOR=#d40000]**lovinglinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=649167"), Gecko worked **perfectly, **can't thank you enough :) That was the only thing, what kinda annoyed me about Linux, but I guess it's perfect for me now!

---

### Post by lovinglinux on 2011-10-18
> **DrArroganto said:**
> Thanks :)

@[khelben1979]("http://ubuntuforums.org/member.php?u=443262"), The VLC plugin doesn't work for me.. The divx player just goes black and doesn't start..

@[[COLOR=#d40000]**lovinglinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=649167"), Gecko worked **perfectly, **can't thank you enough :) That was the only thing, what kinda annoyed me about Linux, but I guess it's perfect for me now!

You are welcome. Please mark the thread as SOLVED using the Thread Tools menu.

---

### Post by DrArroganto on 2011-10-18
> **lovinglinux said:**
> You are welcome. Please mark the thread as SOLVED using the Thread Tools menu.

Yup.. Marked.

---

### Post by lovinglinux on 2011-10-18
> **DrArroganto said:**
> Yup.. Marked.

Thanks.

---

### Post by khelben1979 on 2011-10-18
I just wanted to add that the flash player can take care of DivX content as well. Works good over here.

---

### Post by lovinglinux on 2011-10-18
> **khelben1979 said:**
> I just wanted to add that the flash player can take care of DivX content as well. Works good over here.

However, it can't use xv output, so performance is terrible compared to gecko and totem.

---

