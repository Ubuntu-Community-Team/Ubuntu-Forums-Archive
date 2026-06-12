---
title: "Slow, especially Firefox"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by forficula on 2009-10-25
Hi, I am using Karmic and, as with Jaunty, some applications run very slowly - the worst of all is Firefox by a huge margin.  Opera, on the other hand, runs really well.  I also think that just having Firefox open appears to slow other applications, so I am assuming it is a memory thing.  I have 2GB RAM.  Many thanks for any ideas.  d

---

### Post by P4man on 2009-10-25
2GB ought to be more than enough. But have a look whats going on (or going wrong). Open a system monitor from system > administration > system monitor. Go to processes then enable all processes in the view menu, and see if anything is stealing memory or cpu cycles.

---

### Post by forficula on 2009-10-25
Many thanks for this - I note Firefox takes around 40MB, about twice as much as Opera.  Can anything be done about this?  Many thanks.  d

---

### Post by P4man on 2009-10-25
40Mb is completely normal, its even low. Thats not your problem (you have 2000Mb remember?). Anything else using excessive cpu% or is the xorg process using ridiculous amounts of ram or cpu?

---

### Post by forficula on 2009-10-25
Many thanks - xorg is currently the highest at 62.2 MB followed by three entries starting wcg and including the word rosetta in the title, each taking about 54MB.  The Gnome system monitor appears to be taking 90% plus (sometimes as high as 98% or 100%) of the CPU.  d

---

### Post by forficula on 2009-10-25
Of course system monitor was being used at the time!  Looking at the graphs, I note that RAM never gets above 50% usage, SWAP is never used and the CPU fluctuates, though most of the time it is below 50%.  It thinks I have two CPUs, which I don't - this is a fairly dated now 3 GHz P4.  Many thanks, d

---

### Post by P4man on 2009-10-25
eh. system monitor sucks :(
perhaps open a terminal and run 

```
top
```

instead. But Im wondering if you dont have a graphics card problem perhaps. Is it stuff like scrolling thats slow? What videocard do you have, and did you install any restricted drivers for it?

---

### Post by forficula on 2009-10-25
Many thanks for this - top didn't show any real hogs.  I am using nVidia GeForce 7600 GS card with 256MB memory and nVidia driver 185.18.36.  This is an ATX 8X card as the machine is a few years old.  Yes, it is often scrolling, though has improved slightly while holding this discussion!! d

---

### Post by ikisham on 2009-10-25
My machine is about as old as yours but weaker (Athlon XP - 1466 MHz -, 1 GB RAM - not an issue for both of us - and GeForce 6200 AGP).
I found that FF took some time loading but it's improved somewhat. It may have some thing to do with some learning settings that it may have, but that's just a guess.
What did definitely improve its performance was disabling cookies. You can enable cookies on a per-site basis and you'll find out that they're only needed in sites you must login to. Also I set FF to clear cookies when it's closed (allow for session) and since it remembers my passords, logging in to sites is a breeze.

---

### Post by lovinglinux on 2009-10-25
See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Also check if you have direct rendering enabled. It makes a lot of difference.

```
glxinfo | grep -i direct
```

---

### Post by forficula on 2009-10-25
Many thanks for your replies - direct rendering is active and I have just cleared cookies, cache, etc, which appears to help.  d

---

### Post by lovinglinux on 2009-10-25
> **forficula said:**
> Many thanks for your replies - direct rendering is active and I have just cleared cookies, cache, etc, which appears to help.  d

Also, disable "Block reported attack sites" and "Block reported web forgeries" and check other tips on my tutorial.

---

### Post by emshains on 2009-10-25
How about disabling some add-ons. I also have a P4 with h/t and with a 7300gt. And on that pc FF seems to be smooth, but chrome runs faster. Much faster. 
And I've got half the ram you've got. And I am running 9.04, upgraded from Hardy. And what about flash ? Are you using gnash or the proprietary adobe plugin.

And, for god's sake, don't disable anything. It ran fine on my box, with the exact P4 3,0 ghz processor.

---

### Post by ikisham on 2009-10-25
Cookies are trash, generically speaking. T R A S H (and generate a lot of _uneeded_ traffic, from what I experience).

*obs-* if cookies are disabled (allowed only for specific sites) you must never clear 'Site preferences' (leave that check box unticked) otherwise it will clear your site whitelist for cookies.

---

### Post by lovinglinux on 2009-10-25
> **emshains said:**
> And, for god's sake, don't disable anything. It ran fine on my box, with the exact P4 3,0 ghz processor.

Disabling cookies is recommended due to security issues. I recommend using [CS LIte](https://addons.mozilla.org/en-US/firefox/addon/5207) to easily control which sites can send you cookies.

Disabling the "Block reported attack sites" and "Block reported web forgeries" solves some issues with Firefox becoming unresponsive and also improves page loading.

Disabling scripts with [NoScripts](https://addons.mozilla.org/en-US/firefox/addon/722) is almost essential for security and also helps to avoid sites with bad scripts that easts CPU cycles.

Disabling flash with[NoScripts](https://addons.mozilla.org/en-US/firefox/addon/722) or [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433) improves performance a lot, since you can allow only the flash content you need or the sites you visit the most.

Blocking adds with AdBlock Plus improves performance and avoids the amazing visual pollution we encounter on several web sites and also protects against malicious scripts on third-party adds.

Disabling network.dns.disableIPv6 improves page loading and usually solves the problem when the user can't connect to any sites.

Disabling Color Management fixes the problem of images being rendered with weird colors.

Disabling network.http.sendRefererHeader prevents sites from tracking your activity.

Do you need more examples?

These and other tips can be found at [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by ikisham on 2009-10-25
I'll look at that thread.

I strongly second the NoScript recommend. With time we learn that a site must be unblocked only in relatively few occasions. Most of the time unblocking a site brings no useful feature and brings evident and maybe not evident unuseful ones. It speeds up browsing significantly for our not so powerful machines (my connection is 2 Mbit/s).

---

