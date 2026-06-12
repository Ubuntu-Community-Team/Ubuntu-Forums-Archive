---
title: "Dedsktop or Server LTS upgrade?"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by davebaldwin on 2010-05-06
I have an 8.04LTS installation that started with the Desktop Live CD and I added Apache/MySQL/PHP with Synaptic.  I'm unsure of which upgrade I should do to go to 10.04LTS.  Suggestions?  Information?

---

### Post by koanhead on 2010-05-06
I'm not sure what you are asking, but my preference is usually to back everything up and do a fresh install. I have had so many bad experiences with dist-upgrade that I don't trust it any more.
With that said, as long as you have a good backup there's no reason why you shouldn't at least try to dist-upgrade to 10.04. It *should* work, and if it doesn't you can always finish up with a fresh install.
All you should have to do is:
1) Change all instances of "hardy" to "karmic" in /etc/apt/sources.list
2) do "sudo apt-get dist-upgrade" from a terminal
There are graphical ways to do it, but I prefer to use the terminal so that I can easily see if something goes wrong.

---

### Post by koanhead on 2010-05-06
Go with Desktop if you want to have a graphical desktop. The Server Edition does not install a GUI.

---

