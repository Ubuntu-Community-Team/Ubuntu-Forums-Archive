---
title: "Toshiba Satellite M645: No Sound from Headphone Jack and Low Laptop Speaker Sound"
date: 2018-05-28
forum: MINT
---

### Post by sn95 on 2018-05-28
Any help would be appreciated. 

Fresh Mint install on a laptop. I had not used it before it was given to me.

There is no sound from the headphone jack and the laptop speakers do not mute when headphones are plugged in. The sound on the laptop speakers have a low volume.

---

### Post by wildmanne39 on 2018-05-28
*Thread moved to **MINT for a more appropriate fit**.*

---

### Post by sn95 on 2018-05-28
> **wildmanne39 said:**
> *Thread moved to **MINT for a more appropriate fit**.*

Thanks. I realized that I posted in the wrong place about the same time I noticed the thread was moved.

---

### Post by sn95 on 2018-05-28
@wildmanne39 I just realized what happened. Threads here get no views. Help a brother out. Please don't leave me in a dark corner with no sound.

---

### Post by #&amp;thj^% on 2018-05-28
You get more views than you think here!
As a start go here first: [https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

---

### Post by wildmanne39 on 2018-05-28
Hello, first most of the users here that help answer questions use the activity page to watch for new threads so it does not make that much difference what sub-forum your thread is in, see the link for the activity page.

[https://ubuntuforums.org/activity.php](https://ubuntuforums.org/activity.php)

Second we are all volunteers from all over the world so the person that can help you may not be online right now, it is important to bump your thread once every twelve hours if you do not receive a reply within that time frame but only once every twelve hours.

Third since you are using Mint your thread is in the correct sub-forum and will stay here, if we make exceptions to this rule with as many members we have it would be chaos.

Fourth the view count is broken on the forum so it is not accurate, as of beginning this post to you there were six views that I can see as a moderator.

---

### Post by jeremy31 on 2018-05-28
cc0713?  Did you try my last suggestion on forums.linuxmint.com?  ```
alsamixer
```
In terminal might show the volumes at 100%....could you try the Live ISO and see if headphones work correctly, maybe create and switch to a new user on the laptop?

For posters other than sn95, I have a M645 Toshiba that has good sound in Linux Mint, even the headphones work, about the only difference in equipment are different HDD/wifi

---

### Post by sn95 on 2018-05-28
> **jeremy31 said:**
> cc0713?  Did you try my last suggestion on forums.linuxmint.com?  ```
alsamixer
```
In terminal might show the volumes at 100%....could you try the Live ISO and see if headphones work correctly, maybe create and switch to a new user on the laptop?

For posters other than sn95, I have a M645 Toshiba that has good sound in Linux Mint, even the headphones work, about the only difference in equipment are different HDD/wifi

I just did. It looks like the headphones volume is turned to 0. ?

> Simple mixer control 'Master',0  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 19 [61%] [12.00dB] [on]
  Front Right: Capture 19 [61%] [12.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Loopback Mixing',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'




---

### Post by sn95 on 2018-05-28
> **1fallen said:**
> You get more views than you think here!
As a start go here first: [https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

Thanks. Tried all 3 but none worked.

---

### Post by sn95 on 2018-05-28
> **wildmanne39 said:**
> Hello, first most of the users here that help answer questions use the activity page to watch for new threads so it does not make that much difference what sub-forum your thread is in, see the link for the activity page.

[https://ubuntuforums.org/activity.php](https://ubuntuforums.org/activity.php)

Second we are all volunteers from all over the world so the person that can help you may not be online right now, it is important to bump your thread once every twelve hours if you do not receive a reply within that time frame but only once every twelve hours.

Third since you are using Mint your thread is in the correct sub-forum and will stay here, if we make exceptions to this rule with as many members we have it would be chaos.

Fourth the view count is broken on the forum so it is not accurate, as of beginning this post to you there were six views that I can see as a moderator.

I did not realize the view count was not working. That is what caught my attention. My response was supposed to be taken partly as humor. Please don't take it as complaining or demanding.

---

### Post by jeremy31 on 2018-05-28
Did you press F6 and choose Intel PCH for the card?

---

### Post by sn95 on 2018-05-28
> **jeremy31 said:**
> Did you press F6 and choose Intel PCH for the card?

No. When would I do that? When booting up?

---

### Post by jeremy31 on 2018-05-28
In alsamixer as I never see the full settings until I press F6 and switch

---

### Post by sn95 on 2018-05-28
> **jeremy31 said:**
> In alsamixer as I never see the full settings until I press F6 and switch

This is my only choice: HDA Intel MID.

Under the Mint driver manager, I remember choosing an Intel proprietary driver. *I looked and this was intel-microcode. It looks like for the CPU and not onboard sound.

I can turn up the headphone volume when running alsamixer in the terminal but it does not help and then resets to 0 if I reboot.

---

### Post by #&amp;thj^% on 2018-05-28
What dose:
```
inxi -A
```
return?

---

### Post by jeremy31 on 2018-05-28
Hi 1fallen does [https://forums.linuxmint.com/viewtopic.php?f=49&t=270096#p1474070](https://forums.linuxmint.com/viewtopic.php?f=49&t=270096#p1474070) do enough?

---

### Post by #&amp;thj^% on 2018-05-28
> **jeremy31 said:**
> Hi 1fallen does [https://forums.linuxmint.com/viewtopic.php?f=49&t=270096#p1474070](https://forums.linuxmint.com/viewtopic.php?f=49&t=270096#p1474070) do enough?

:) It should.
I can't help but feel that the OP has just simply overlooked something though. :) Maybe even trying or borrowing another set of headphones to test the jack itself.
Thanks jeremy31 it's good to see you! ;) I don't hang out in your expertise in the forums as you guys just "get-er done"
Best Regards

---

### Post by sn95 on 2018-05-28
So OP is definitely missing a thing or two.

My headphones are definitely muted. 

I can unmute in alsamixer but how do I save the changes?

Also, auto mute mode is enabled. ?

---

### Post by #&amp;thj^% on 2018-05-28
Try:
```
 sudo alsamixer
```
make the needed changes and close>>>then try "alsamixer" again.

---

### Post by sn95 on 2018-05-28
> **1fallen said:**
> Try:
```
 sudo alsamixer
```
make the needed changes and close>>>then try "alsamixer" again.

I tried this. The change was made and stayed when I opened alsamixer back up.

However, there was still no sound on the headphones and when I rebooted (just to see if that would help) the headphones were muted again.

My problem seems to be that Mint is not detecting the headphones.

---

### Post by #&amp;thj^% on 2018-05-28
It is still possible that the jack itself is shorted or not working. (Don't kill the messenger.)
Sorry I'm just plain out of ideas now. :(

---

### Post by sn95 on 2018-05-28
> **1fallen said:**
> It is still possible that the jack itself is shorted or not working. (Don't kill the messenger.)
Sorry I'm just plain out of ideas now. :(

That's definitely possible.

However, they do make a little noise over the laptop speakers when plugging in so I have assumed they are not dead. I also had them in during a recent reboot and noticed a little noise during it. I assumed the noise was in response to being probed.

---

### Post by Yellow Pasque on 2018-05-29
Plug the headphones in and turn up the volume. Get more detailed info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by sn95 on 2018-05-29
> **1fallen said:**
> It is still possible that the jack itself is shorted or not working. (Don't kill the messenger.)
Sorry I'm just plain out of ideas now. :(

So don't kill the messenger and I appreciate everyone's help but the headphone jack is busted.

I looked carefully into it with a flashlight and some of the plastic is cracked. This machine has been through some hard use. Knowing this, I persistently wiggled the headphones with some music playing and I can find a sweet spot where they will make a connection. 

I am not good with anything laptop size or smaller so I doubt I will replace the jack, Does anyone know a decent, cheap USB device that I could use for sound to plug headphones or an external speaker in?

Thanks again for all the help and sorry to waste time.

---

### Post by #&amp;thj^% on 2018-05-29
Well at least you know now. It's never a waste of time helping someone out;) might feel that way to some when either no solution, or the solution is not a desired one.
Here is a link for some USB devices, make sure it includes Linux in the description, [https://www.amazon.com/Best-Sellers-Electronics-External-Sound-Cards/zgbs/electronics/3015427011](https://www.amazon.com/Best-Sellers-Electronics-External-Sound-Cards/zgbs/electronics/3015427011)

---

### Post by sn95 on 2018-06-01
> **1fallen said:**
> Well at least you know now. It's never a waste of time helping someone out;) might feel that way to some when either no solution, or the solution is not a desired one.
Here is a link for some USB devices, make sure it includes Linux in the description, [https://www.amazon.com/Best-Sellers-Electronics-External-Sound-Cards/zgbs/electronics/3015427011](https://www.amazon.com/Best-Sellers-Electronics-External-Sound-Cards/zgbs/electronics/3015427011)

Thanks again for the help and also big also thanks to @jeremy31. I do appreciate it and I am looking forward to tinkering with this laptop. My desktop runs Mint but I don't use it that much. My tablet and mobile device run Android. It will be nice to have something around besides those.

---

