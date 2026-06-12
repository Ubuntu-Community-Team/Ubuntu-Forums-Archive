---
title: "Dapper to Edgy upgrade - Xserver Failing to load (i810)"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-10-27
I upgraded my box today from Dapper to Edgy and now it won't load the Xserver. The upgrade process itself seemed to go ok. At the end of the upgrade process I restarted and got the splash screen showing the progress bar. Then there was a 20 second delay with a black screen and blinking cursor. Then it told me that the Xserver failed to load and when I viewed the output the following lines looked conspicuous to me:

```
(EE) Module ABI major version (1) doesn't match the server's version
(0)
(EE) Failed to load module "i810" (module requirement mismatch,0)
(EE) No drivers available

Fatal Server Error:
no servers found
```


I tried "dpkg-reconfigure xserver-xorg" and set it up for my i810. This didn't help. Got the same error.

I then tried reconfiguring using the "vesa" driver and it didn't work either.

I compared my old (pre-upgrade) xorg.conf file and in the devices section it appeared to be the same.

Any ideas how I can get X working again?

My machine has an 82915G Chipset display adapter. I was running AIGLX prior to the upgrade and thought this might be the problem, but I thought re-configuring Xserver-xorg would have fixed any potential problem in that regard.

As an aside, it also came up with the "Kubuntu" splash screen even though my pre-upgrade machine was Ubuntu and not Kubuntu (although I had previously installed the kubuntu-desktop package a month or so ago to try it out). I would think this is unrelated to my xorg problem but I thought I'd mention it just in case.

Any clues as to what I should do to fix the problem? I can't bear to boot up into my XP partition for much longer (Gawd I forgot how long it takes for my machine to boot up XP..there must be at least 16 little flashing icons down there in the system tray!).

---

### Post by 8oluf7 on 2006-10-28
Try:

[INDENT]sudo aptitude install xserver-xorg-video-i810[/INDENT]

There are now several threads where helpful souls have pointed out that Xorg changed the driver file names very recently (replacing 'driver' with 'video' in the file name, I think).

---

### Post by Pablasso on 2006-10-29
> **8oluf7 said:**
> Try:

[INDENT]sudo aptitude install xserver-xorg-video-i810[/INDENT]

There are now several threads where helpful souls have pointed out that Xorg changed the driver file names very recently (replacing 'driver' with 'video' in the file name, I think).

im having the exact same problem (maybe i should have uninstalled aiglx and beryl before doing a distro upgrade grrr) and the driver is already updated, it doesnt help reinstalling it neither

---

### Post by Pablasso on 2006-10-29
i uninstalled xserver-xorg-air-core linux-dri-modules-common and reinstalled xserver-xorg and its working now

---

### Post by richardq on 2006-10-29
Thanks for the all the responses. I finally managed to get it back up and running properly. I too wish I had uninstalled compiz/Aiglx prior to upgrading, I'm sure it would have gone smoother.

Anyways, I solved most of my problems by editing my /etc/gdm/gdm.conf-custom file replacing the line:

command=/usr/bin/Xorg-air :0

with 

command=/usr/bin/Xorg :0

Through all my searching (I was trying *everything*) I found this in one discussion thread. I'm not sure why it wasn't updated automatically. But this then allowed me to boot properly into X. Getting rid of Compiz was the next major step. I found that following instructions on installing Beryl did the trick. (Now I have to somehow find that cgwd theme I loved before).

---

### Post by beercz on 2006-12-07
> **richardq said:**
> Thanks for the all the responses. I finally managed to get it back up and running properly. I too wish I had uninstalled compiz/Aiglx prior to upgrading, I'm sure it would have gone smoother.

Anyways, I solved most of my problems by editing my /etc/gdm/gdm.conf-custom file replacing the line:

command=/usr/bin/Xorg-air :0

with 

command=/usr/bin/Xorg :0

Through all my searching (I was trying *everything*) I found this in one discussion thread. I'm not sure why it wasn't updated automatically. But this then allowed me to boot properly into X. Getting rid of Compiz was the next major step. I found that following instructions on installing Beryl did the trick. (Now I have to somehow find that cgwd theme I loved before).

Thanks richardq

I am running edgy and after this mornings' updates I found X server would not start when I restarted my laptop.

I tried
> dpkg-reconfigure xserver-xorg and > apt-get install xserver-xorg-video-i810 as suggested by several people, all to no avial.

Having further searched the forums, it was your post that provided the answer.

Thanks again.

---

