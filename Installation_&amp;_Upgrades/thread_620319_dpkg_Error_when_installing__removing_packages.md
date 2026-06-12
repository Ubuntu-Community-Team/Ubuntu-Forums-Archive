---
title: "dpkg: Error when installing / removing packages"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by hunt.topher on 2007-11-22
After installing vorbis-tools and some related packages yesterday, I started getting errors when trying to install or remove any package: "Error while processing the following packages" and a list of the broken or problematic packages. Synaptic showed broken packages but fixing them didn't work, and I couldn't remove or reinstall the packages (Enlightenment, thunar, vorbis-tools, and a couple others) due to the same error messages.

Finally I found a way to stop this error message: remove those packages' entries from 
**/var/lib/dpkg/status**  . This worked, it now lets me install and remove packages fine, but I'm still getting an error message every time I try to install or remove from terminal using apt-get:

[B]/usr/sbin/dpkg-preconfigure: 6: BEGIN: not found
eval: 1: qq{: not found
/usr/sbin/dpkg-preconfigure: 8: use: not found
/usr/sbin/dpkg-preconfigure: 9: use: not found
/usr/sbin/dpkg-preconfigure: 10: Syntax error: "(" unexpected[/B]

While install / uninstall works now, I'd love to not have this error message pop up every time. Do you think that dpkg-preconfigure might have been corrupted somehow? Is there a single version of the file that someone could send me or direct me to? Let me know if you need more info. I have my dpkg-preconfigure file (renamed as TXT) below to compare.


[B]UPDATE:
[/B]
I just found out that the above "fix" to /var/lib/dpkg/status did not really fix anything, it just got rid of the error message; the Firefox Gnash plugin, for example, doesn't work at all now. **I want to remove it completely** and install Adobe's nonfree Flash plugin in its place, I'm not impressed with Gnash anyway... does anyone know if I can just edit or delete a specified list of files to effectively pick out the Gnash package from my system? Is it more complex than this? I hope not...

I don't know what is going on with my system but it sounds like a) this corrupted dpkg-preconfigure file might be causing problems, and b) I'll have to clean wipe my system to get my productivity back. And I was so impressed with the Deb package system until now... if this has happened to many users (which seems to be the case), shouldn't Ubuntu look into some thorough "system package repair" utility that goes through your packages and makes sure they're all intact?

I'd welcome any suggestions on what I can do to fix this. I've tried the dpkg --configure -a trick, no result. (Should that take some time to complete? it seemed to finish instantly.) Any ideas?
One thought: Might this be a problem with the packages involved in getting dpkg, apt, and synaptic to work properly? If so, is there a way to re-install those packages without formatting the system?

**2ND UPDATE:**

I reinstalled Ubuntu on the laptop resizing and keeping the original install partition, and while running standard updates on the new install, the same error happened again. I'm thinking it was something to do with my poor wireless connection. After some subsequent tweaking, I tried using the Add/Remove interface and it worked, no errors. I have no idea what fixed it but I'm afraid to play around now for the time being.

---

