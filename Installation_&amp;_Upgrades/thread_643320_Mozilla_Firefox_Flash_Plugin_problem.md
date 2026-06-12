---
title: "Mozilla Firefox Flash Plugin problem"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by qbox on 2007-12-17
Hi to all.
When I try to open some sites who have flash on it (cisco.netacad.net) all flash places are closed in the second. I start firefox in console and I have this report.

qbox@qbox:~$ firefox
*** NSPlugin Wrapper *** ERROR: NPP_NewStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_WriteReady() invoke: Connection closed


Someone to help?


qbox@qbox:~$ firefox
*** NSPlugin Wrapper *** ERROR: NPP_NewStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed
qbox@qbox:~$

---

### Post by Pumalite on 2007-12-17
Have you tried upgrading to latest version of Firefox?

---

### Post by qbox on 2007-12-17
i try sudo apt-get update 
but this problem didnt show in earlier versions

---

### Post by Pumalite on 2007-12-17
Go to the Firefox site and download the latest to your Desktop. Then, in Terminal:
cd ~/Desktop
tar xvzf firefox-2.0.0.11.tar.gz
cd firefox
./firefox
Make sure Firefox is closed when you do this.

---

### Post by Pumalite on 2007-12-17
Sorry. Already done.

---

### Post by mrwasabi on 2007-12-17
I'm having the same problem, I'm fully updated on Ubuntu 7.1 and firefox will not run flash, and I am running firefox 2.0.11 the latest version, any ideas?

---

### Post by qbox on 2007-12-17
with older versions i dont have this problem.

---

### Post by Pumalite on 2007-12-17
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by qbox on 2007-12-19
That isnt working. I already have installed flash plugin. He start to work but after a few seconds I receive upper error.

---

### Post by Pumalite on 2007-12-19
Start looking at other causes for your problem.

---

### Post by MangasColoradas on 2007-12-19
There is a bug with Flash and FF. [http://ubuntuforums.org/showthread.php?t=634756](http://ubuntuforums.org/showthread.php?t=634756)

---

### Post by qbox on 2007-12-19
Thanks to all
I do this
sudo apt-get remove flashplugin-nonfree
after that I install this 
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb)
Work fine for now :D

---

### Post by ThaRabbit on 2007-12-19
is it a specific website or is it happening on every website containing flash?

Also, 32 or 64 bit :) ?

Using FF 2.0.0.11 and this package:
[http://www.adobe.com/shockwave/download/index.cgi?Lang=Dutch&P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/index.cgi?Lang=Dutch&P1_Prod_Version=ShockwaveFlash)

---

### Post by Bablefish on 2007-12-19
So many people who still haven't noticed that Flash can be found in Add Remove

---

### Post by MangasColoradas on 2007-12-19
.

---

### Post by Pumalite on 2007-12-19
> **qbox said:**
> Thanks to all
I do this
sudo apt-get remove flashplugin-nonfree
after that I install this 
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb)
Work fine for now :D
Thanks for posting it. Good thing to keep in mind.

---

### Post by qbox on 2007-12-19
fmmm. that is happening again. I will try with older version. If I can find.

---

### Post by Pumalite on 2007-12-19
Spoke too soon.

---

### Post by daradib on 2008-01-03
In case someone sees this thread, the package was removed from the Ubuntu repository server. See [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

Also, [Bug #177856]("https://bugs.launchpad.net/nspluginwrapper/+bug/177856") seems similar.

---

### Post by zygut on 2008-01-09
> **qbox said:**
> Thanks to all
I do this
sudo apt-get remove flashplugin-nonfree
after that I install this 
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb)
Work fine for now :D

I am having this same problem... some flash works fine, but if I go to a myspace page with flash (for example: [http://www.myspace.com/josegonzalez](http://www.myspace.com/josegonzalez)), I get that error.

I tried to remove the flashplugin-nonfree and install that newer one, but same problem :(

This is an AMD64 firefox.

---

### Post by Chuq on 2008-01-11
I also had this problem - I changed my repositories to the internode ones ([http://mirror.internode.on.net](http://mirror.internode.on.net)) but that didn't help (it could find the packages, but still wouldn't display correctly on some sites) - it seems I had Flash 8 installed.

I followed this procedure to get Flash 9 installed - 
[http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu](http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu)

Not a problem for many of us but this kind of thing could really put off some first time users!

---

### Post by qbox on 2008-01-14
Can someone tell how to install flash 8?
I have 64bit version.

---

