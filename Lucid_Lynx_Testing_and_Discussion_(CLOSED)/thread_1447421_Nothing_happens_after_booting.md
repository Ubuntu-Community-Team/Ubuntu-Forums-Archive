---
title: "Nothing happens after booting"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by HMartinho on 2010-04-05
Hi fellas;

I was under the impression I'd already posted this, but can't seem to find my previous post.
I've updated from 9.10 to 10.04 beta and when i boot i get an odd desktop with no background and no icons on the taskbar, also I guess the all loading process freezes, i'm able to open a console by adding a launch button on the taskbar with that command, when I tried to launch update manager, it can't update cause it seems wireless is down also , I'm guessing network management has not loaded also. Can't really get anymore details since I'm quite noobish and the only way I have to be posting this here is by rebooting to Win7 (triple boot, vista 7 and ubuntu), wich reminds me, I've tried also to load some older kernel (?? not sure if correct) but even with previous to updating builds I have the same result.
Is this a known issue? Any ideas on how to fix it?
Thanks in advance.

---

### Post by cariboo on 2010-04-05
It looks like the upgrade didn't complete. If you can boot into recovery mode, select drop to root prompt with networking and type:

```
sudo apt-get -f install
```

After the above command has finished, type:

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

The above 3 commands should complete the upgrade for you.

---

### Post by HMartinho on 2010-04-05
Thank you cariboo907, but there's actually another problem with that, when I try to boot in recovery, I can't see a thing cause it seems the video driver is not configured, I get a sort of a 3 way blinking screen wich I can't even read.
But I'l try, one of the choices should be compatible mode or something like that.
My graphic card is an nvidia 8600G btw on an HP laptop.
Thank you once again, I'll tell you how it went.

edit:
it's actually a four way scrambled screen wich makes it unreadeable
so i can't even get it to root prompt

edit #2:
i figured the root prompt with networking was the longest line option (guessed it) but with no results either
maybe network manager is not loading
is there a way to force wireless networking to function? as i said earlier i'm able to start a console and can type commands in it, started firefox and update-manager, both with no results since network connection is down, I've even tried:
ifconfig wlan0 up
but it still did not make the update-manager able to fetch the updates.
getting close to downloading and re-installing I guess, but still wish i didn't

---

### Post by HMartinho on 2010-04-05
i was wondering if I could update/upgrade from cd, i mean, can I boot with live/install cd and do the apt-get thing?

Cheers

---

### Post by HMartinho on 2010-04-09
bump

---

