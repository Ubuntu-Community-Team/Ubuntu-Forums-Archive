---
title: "No WPA2 wireless option when using alternate expert mode installer"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by auh2o on 2010-03-24
I used the alternate Lucid beta CD to run the text-based expert-mode installer. Everything went smooth except I could not get network access during install since all I had on the laptop in question was a wireless PC-card and the only network available used WPA2 encryption (which I had the key to, but not the rights to turn off). The installer only supported entering a WEP-key. I guess my question is, what's up with that? Is there no way to access WPA-encrypted networks during install? WEP is pretty outdated today, I would think. Could it have been a driver-related problem? Though my wireless card was picked up automatically by the installer, and I know for a fact it supports WPA2.

---

### Post by mike984 on 2010-03-26
Might be connected to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545708](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545708)

---

### Post by iponeverything on 2010-03-26
> what's up with that?

Is it that big a deal? It is "text-based expert-mode installer" after all. After the install is finished, then work on getting your network up. If you, for some reason, need the network to finish the install, just run a cable into the router. Though I have done a number of installs like this and have never needed  the connection to finish the install. In fact I prefer not to have the connection during the install.

---

### Post by auh2o on 2010-03-26
> **iponeverything said:**
> Is it that big a deal? It is "text-based expert-mode installer" after all. After the install is finished, then work on getting your network up. If you, for some reason, need the network to finish the install, just run a cable into the router. Though I have done a number of installs like this and have never needed  the connection to finish the install. In fact I prefer not to have the connection during the install.

Excuse me, but that was a pretty useless post, which added nothing of value to the subject at hand. Hardly worth replying to, and yet I seem to have whipped something up below:

It's a deal alright. I never stated that it was big. In fact, the size of it I'll leave to others to decide. But by your rationale, why even offer a network connection during install at all? You are aware that in the case of the netboot mini CDs, a connection is  necessary, ain't you? As for the alternate CD, no it isn't *necessary*, but the option is there, and it speeds things up. THANK YOU for reminding me I can set up the network *after* installation! I would have *never* figured that out otherwise!

As I stated in my original post, I didn't have the option to run a cable. And WEP networks are far and few between these days. Naturally I would take the lack of WPA support to mean there was some sort of problem or something that was overlooked that needed to be fixed. It shouldn't be driver related, since my wireless card uses the Ralink RT61 chipset, which works out of the box with Ubuntu and has indeed worked on other Ubuntu laptops in my possession already. But I don't know what the problem might be, if others have experienced the same thing, or if it's worth filing a bug report over. Judging from the other reply, there might already be one that applies. In any case, that's why I was asking for input. If a problem arises, I prefer to deal with it instead of turning a blind-eye and working around it. Since that's obviously not in line with your way of thinking, you may refrain from replying any further. Thank you.

---

### Post by iponeverything on 2010-03-26
good luck then!

---

### Post by psyke83 on 2010-03-27
The bug mentioned earlier in this thread is not related.

[Bug #134795]("https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/134975") is what you're looking for.

---

