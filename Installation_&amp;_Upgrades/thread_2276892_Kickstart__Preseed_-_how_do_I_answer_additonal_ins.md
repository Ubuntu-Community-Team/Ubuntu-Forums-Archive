---
title: "Kickstart / Preseed - how do I answer additonal installer questions?"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by Moptop650 on 2015-05-05
Hey all, I'm learning how to do automatic ubuntu installations via a kickstart / preseed custom ISO. I'm using a 14.04 ISO as the base, but I think this process is fairly agnostic regarding the ubuntu version.

All I've done so far is:
[LIST]
[*]Using *system-config-kickstart* create a ks.cfg file and put it in my ISO
[*]Add a menu option in isolinux/txt.cfg for installing using my kickstart file + the default ubuntu server preseed file.
[/LIST]

When I boot off the ISO, I choose the automated install options, and it proceeds and installs all beautifully.

Everything works fine, but there's one prompt during installation that I can't figure out how to automatically set an answer for. Since I'll be using my ubuntu installs as virtual machines, I do not create a swap partition. This  gets a warning/confirmation screen from the installer's partition editor:

[IMG]http://i.imgur.com/C8AVQQg.png[/IMG]

I know I just need to add a setting for this option in the preseed file, but I don't know what strings to use. Could someone guide me here? I understand that the preseed file can contain any and every installer option, but I don't know where these strings correlate to. Can I somehow disassemble the installer to see a "master list" of sorts of all the options I can specify?

Thanks!!

Edit: I found how to specify this option here: [https://lists.debian.org/debian-user/2012/08/msg01558.html](https://lists.debian.org/debian-user/2012/08/msg01558.html) - "d-i partman-basicfilesystems/no_swap boolean false". But if anyone can explain how this string could be tracked down manually, please do! The reply below mentions downloading a udeb and looking for where this option is set up. I did this, but how would I know what package to download for any other screen in the installer?

---

