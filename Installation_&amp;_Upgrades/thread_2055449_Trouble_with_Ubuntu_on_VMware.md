---
title: "Trouble with Ubuntu on VMware"
date: 2012-09-09
forum: Installation &amp; Upgrades
---

### Post by maygamer96 on 2012-09-09
Hello everyone, I am a total VMware and Ubuntu noob, and I am stuck in a rather interesting mess.
I downloaded the Ubuntu 12.04 iso for my VMware Player 3. Here's what I did:
[LIST]
[*]Made a virtual machine with no ISO file, selected Linux (Ubuntu) (to install VMware tools).
[/LIST]

[LIST]
[*]VM starts up, as usual prompts me to download tools for ubuntu.
[/LIST]

[LIST]
[*]VMware tools get downloaded and installed without hiccups. (NOTE;I was using IOBit's Game Booster 3 just to keep unnecessary services (vmware not affected) off while VMware was running)
[*]Once done, I delete the blank VM and make one with ubuntu iso.
[/LIST]

[LIST]
[*]Everything gets installed, ubuntu starts booting up.
[/LIST]
Now here's the mess:


Ubuntu 12.04 comes up in plain old Unicode font, and then:


VMware Easy Install


PLEASE WAIT! VMware tools is being installed on your PC. Depending on the version of Ubuntu you're installing, you may log in below and use the system during the installation. Otherwise, wait till the graphical interface comes up.


Now I'm perplexed. HELP ME!

---

### Post by Cheesemill on 2012-09-09
Ubuntu 12.04 isn't supported by VMware Player 3.0

Try using the latest version (VMware Player 5.0)

---

### Post by maygamer96 on 2012-09-09
Is that so?<sigh>VMware Player 4 and 5 are not even compatible with my PC, so it's dasvidaniya from Ubuntu for me.

---

### Post by Cheesemill on 2012-09-09
You can't really blame VMware for not wanting to certify a brand new OS on a product that's now 2 major versions old.

You could always use VirtualBox instead of VMware Player. The latest version of VirtualBox still works fine with 32-bit CPU's.

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

