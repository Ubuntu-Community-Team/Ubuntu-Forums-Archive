---
title: "Karmic Beta Borked my Kubuntu!"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cubdukat on 2009-10-18
About a week ago I upgraded my Jaunty install to the Karmic beta, so that I could get the jump on the official release and not have to wait so long to get the full version.

Unfortunately, now that I've done this, KDE is unusable. I get the login music, but the screen fades to black after the splash screen, and all that appears onscreen is a bash terminal, and an occasional error message about kinit crashing.

I've decided that maybe if I remove KDE and reinstall it, that would solve the problem. However, I am unsure about how to go about that. I used synaptic to uninstall kubuntu-desktop, but that seemed to make no difference. The only thing I can think of is to mark everything KDE and Kubuntu for reinstallation in synaptic, but I don't have much hope of that working, either.

If this continues, would I just be better off doing a clean install of Karmic RC? I would really hate to do that, seeing as I just did a clean install of Jaunty to resolve some issues I had with Intrepid, and I have it tweaked to my satisfaction.

---

### Post by Brandon Williams on 2009-10-19
The first thing I would do is attempt to determine whether the problem is related to your personal, user-level customizations/config. Create a new user for test purposes, and then log in as that user. Do you still have trouble?

Another thing to do is check your ~/.xsession-errors file. Are there any messages there that indicate what the problem might be?

PS: It might still be a good idea to post problems related to karmic over in the 'karmic testing' sub-forum under 'Development & programming'.

---

### Post by Abhishekc on 2009-10-19
Found similar problem though not exactly same on updating to karmic. 

I got it solved by running **ubuntu karmic 2.6.31-11-generic - Recover **on grub  screen(press esc on booting to see grub screen if grub do not show up for you) and then "repair broken packages".
It found 3 broken packages and repaired them.

Try it maybe will help you too.

---

### Post by cubdukat on 2009-10-24
I tried both approaches. There was nothing noticeable in ~/.xsession, and there were no broken packages to fix. I suspect it's probaby a theme that it was set up to use that's no longer there anymore. So my last resort before a clean install of everything is trying to get the theme manager up through a command prompt and choosing a different theme.

If that doesn't work, hang it. I'll just do a clean install of Karmic when it's available. Or maybe I'll try another distro to see if they're more laptop-friendly than they were before.

---

### Post by cubdukat on 2009-10-24
Yesp, it was looking for something that wasn't there.. It's back now that I reset it.

---

