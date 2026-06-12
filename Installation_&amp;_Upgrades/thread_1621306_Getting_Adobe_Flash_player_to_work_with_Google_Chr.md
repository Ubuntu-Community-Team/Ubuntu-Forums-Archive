---
title: "Getting Adobe Flash player to work with Google Chrome?"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by JesusSaves on 2010-11-14
I recently set up Ubuntu 10.10 on my computer to dual-boot with Windows Vista. I have no experience with Ubuntu or any other Linux-based operating system.

So I installed Google Chrome on Ubuntu and it works fine, however, I can't get the "integrated" Adobe Flash player to play anything. I followed the troubleshooting directions [here]("http://kb2.adobe.com/cps/839/cpsid_83950.html"), but Flash player wasn't on the list of plugins in Google Chrome. Then I tried downloading and installing an archived version of Flash, but Chrome won't let me do that either.

What can I do to get Flash working?

---

### Post by searchfgold6789 on 2010-11-14
Uninstall Google Chrome and get Chromium Browser from the software center.
They are *exactly the same thing*, except Chromium will probably work for you :P

---

### Post by efflandt on 2010-11-14
Are you running 32 or 64-bit Ubuntu?  Although, Chrome is supposed to include its own version of flash, it does not in 64-bit.

I don't know if Chromium includes its own flash or not, because I am using 64-bit, and it automatically used the real 64-bit flash I put in /usr/lib/mozilla/plugins.  Although, it should also work with flash if you install flashplugin-installer using Synaptic or apt-get.

---

