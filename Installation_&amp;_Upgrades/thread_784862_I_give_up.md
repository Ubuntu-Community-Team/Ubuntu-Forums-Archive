---
title: "I give up"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by frankdn on 2008-05-06
OK, installed 8.04 using wubi, installation worked w/o a hitch.

Logged in, couldn't get wireless working.

Network-admin finds the device, "roaming" is set.  Unlocked and attempted to click the little 'enable' button: no result.  I won't bother relating all the rest of my frustration, although I will complain that the troubleshooting guide appears to belong to an earlier version (I suppose); for instance I'm advised to run 'ipconfig' and there's no such utility installed (not the only case of that either).

The wireless network around here is unsecured.  By way of contrast with ubuntu: here's what I had to do to get wirelessly connected under windows, first time out of the box:

1. boot windows
2. launch IE
3. browse

When you guys can do that, let me know.  Meanwhile I guess I'll stick with microsoft.

---

### Post by tamoneya on 2008-05-06
Im sorry you had a bad experience with Ubuntu and I hope that you give it a try in the future.  You should however consider that windows came installed on your box and was already preconfigured with drivers.  Linux this is not the case.  You had to install linux from scratch and if there are driver issues you have to resolve them just as you would in windows.

Also the command would be ifconfig or iwconfig.  ipconfig is the windows command for network stats.

---

### Post by Pumalite on 2008-05-06
Good luck.

---

### Post by frankdn on 2008-05-06
Just came back for an edit-- I obviously used IE the first time out of the box, not firefox.

But thanks for the concern.  It's not a driver issue, the correct driver is delivered with the default setup.  It's a configuration issue, and an incorrect/outdated troubleshooting guide was of no help.  I understand ifconfig and iwconfig; I had a lot of experience with commercial unixes a few years ago.  The troubleshooting guide definitely wanted me to run ipconfig.

---

### Post by frankdn on 2008-05-10
Turns out all I had to do was discover the networking icon at top right of screen and fiddle with that.  It would have been helpful for the docs to mention that status bar thingy.

---

### Post by tamoneya on 2008-05-10
instead of just complain about docs you could try and help the developers and community out by chaning them to be up to date.

---

### Post by mithritades on 2008-05-10
what did u do exactly with the network thingy,my laptop seems to be doing the samething but i'm not wireless....thnx

---

### Post by tamoneya on 2008-05-10
> **mithritades said:**
> what did u do exactly with the network thingy,my laptop seems to be doing the samething but i'm not wireless....thnx

Post the result of ```
sudo lshw -C network
```

Have you installed the drivers yet for your card?

---

### Post by mithritades on 2008-05-10
ok,since i read ur post about the networking thingy,i think i had to enable or disable my network...one or the other. it's working now,so i don't know what i did...thnx frankd

---

