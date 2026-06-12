---
title: "Trying to install Wubi but &quot;No Disk&quot; exception"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by The Brick on 2010-02-21
Appologies if this question has been asked a million times but I could not find the answer. I am trying to install Wubi in order to run Ubuntu/Kubuntu on Windows to check all is fine before transitioning 100% in order to get better speed from my v. slow PC. I have downloaded Wubi and Ubuntu 9.10 desktop to a folder but get a pop up saying "Windows -No Disk. Exception Processing Message c0000013 Parameters 75b6bf7c 4 -repeats". I have even tried to load it from my son's disk with Ubuntu on and get something similar which then won't go away.
 
Can anyone help me solve this? Thanks in advance.

---

### Post by phflupp on 2010-02-21
I'm pretty sure this version is broken. For me it complains if there is no Ubuntu CD in the tray (older versions would download) and if it is there then it wants to run Ubuntu with the standard install, without wubi (where installation is like a windows installation).

I tried an older version, but it wasn't 9.10 so no good for me.

I'm looking for another version that will install Intrepid Ibex, but no luck so far.

---

### Post by oldfred on 2010-02-21
This page has a lot of info on wubi issues and suggested solutions:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by The Brick on 2010-02-22
No luck yet.  Has anyone found a solution for this or experienced this problem?
 
Thanks!

---

### Post by Augustine325 on 2010-04-07
HAs this been resolved yet? I'm having the same issues.  thanks

---

### Post by lisati on 2010-04-07
Do you have a card reader (e.g. for SD cards) installed in your box? Try disabling it with "safely remove hardware" first.

This is a known issue: see [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

---

### Post by Augustine325 on 2010-04-07
i had similar problems and followed lisati's advice.  i disabled my card reader from the 'Device Manager' in windows and the error messages disappeared.  however wubi still won't load ubuntu properly.  having run wubi, ubuntu now appears in my programme list, but isn't given as an option when i start the computer.  hmmm.  does anyone know how to move on from here...

---

