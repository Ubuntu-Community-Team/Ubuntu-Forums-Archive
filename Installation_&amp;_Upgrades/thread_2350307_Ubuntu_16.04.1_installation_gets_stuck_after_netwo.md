---
title: "Ubuntu 16.04.1 installation gets stuck after network step"
date: 2017-01-23
forum: Installation &amp; Upgrades
---

### Post by samuel-santacatalina on 2017-01-23
I'm reposting this thread from AskUbuntu forum as I didn't got much feedback from that community.

When trying to install Ubuntu 16.04.1 Desktop amd64, through the USB instaler, [the installation gets stuck after network step]("https://i.stack.imgur.com/hGOol.jpg"), regardles of I select to connect to a specific network or not.

  The installer simply doesn't go to next step (I let the installer for   hours, and nothing happened), and doesn't seem to be processing   anything (no icon showing progression, processement or HD activity   perceived, nor any message shown), while it allows to cancel the  installation starting a live  Ubuntu instance (which starts pretty  well).

I had Ubuntu 14 installed until now on this laptop (ASUS A53S), along   with Windows 7 on dual boot with no problems, but would love to give a   try to this new version of Ubuntu.

Any ideas? maybe a hint on how/where to analyse the issue?

  
Thanks all!

---

### Post by 1vertex1 on 2017-01-23
Hello,

I recently installed Ubuntu (twice today infact!) - I found sometimes the installer does not register your choices. Stupid question, but have you tried going back and then forward again to the network selection screen?

I noticed also you've tagged it on the ASUS. My unit is also an ASUS... try using 'nomodeset' in the installer script (press e to edit the code before going to 'Install Ubuntu')... if you have an nvidia GFX card, this might cause problems down the line...

Cheers,

1vertex1

---

