---
title: "[SOLVED] Virtualbox 2.0.4 (PUEL)"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by shane19174 on 2008-10-24
Sun released virtualbox 2.0.4 today, but on their website there is still no Intrepid repo. I am still running 2.0.2 from my Hardy installation, which I upgraded to Intrepid beta a few weeks ago. In the process of the upgrade, Sun's repo was disabled along with all the other 3rd party sources, and I didn't re-enable to avoid any possible conflicts.

My question: can I safely re-enable the repo and upgrade vbox, or should I sit tight until they open an Intrepid repo? Has anyone else installed 2.0.4 in Intrepid yet?

Thanks,
Shane

---

### Post by dinxter on 2008-10-24
works fine with the hardy repo so you should be able to just go with that for the moment. using 2.04 myself from the same

---

### Post by niccholaspage on 2008-10-24
I installed VirtualBox with the SH Script on Intrepid.

---

### Post by FuturePilot on 2008-10-24
I'm using the deb for Hardy right now and it works fine. You just have to recompile the kernel module which it will ask you if you want to during installation, say yes and allow it to recompile it.

---

### Post by ThrobbingBrain66 on 2008-10-24
> **shane19174 said:**
> Sun released virtualbox 2.0.4 today, but on their website there is still no Intrepid repo. I am still running 2.0.2 from my Hardy installation, which I upgraded to Intrepid beta a few weeks ago. In the process of the upgrade, Sun's repo was disabled along with all the other 3rd party sources, and I didn't re-enable to avoid any possible conflicts.

My question: can I safely re-enable the repo and upgrade vbox, or should I sit tight until they open an Intrepid repo? Has anyone else installed 2.0.4 in Intrepid yet?

Thanks,
Shane

The Intrepid repo is available, it's not listed on the website though.  Just change the repo reference from hardy to intrepid.

---

### Post by shane19174 on 2008-10-24
> **ThrobbingBrain66 said:**
> The Intrepid repo is available, it's not listed on the website though.  Just change the repo reference from hardy to intrepid.

Hey, thanks! I changed it and it's downloading now.

EDIT: But the download is verrry slow...

---

### Post by Fracman on 2008-10-24
Could someone please explain how I download and install from the Virtualbox site? I've already edited the sources list, but when I try to  sudo apt-get install virtualbox-2.0 2.0.4-38406_Ubuntu_intrepid it says it can't find the package.

---

### Post by FuturePilot on 2008-10-24
> **Fracman said:**
> Could someone please explain how I download and install from the Virtualbox site? I've already edited the sources list, but when I try to  sudo apt-get install virtualbox-2.0 2.0.4-38406_Ubuntu_intrepid it says it can't find the package.

Just try "virtualbox-2.0".

---

### Post by Fracman on 2008-10-24
> **FuturePilot said:**
> Just try "virtualbox-2.0".

Thanks man, that did it!

---

### Post by pferraro on 2008-10-24
Yes - I've installed it on intrepid x64.  Installed a Vista x64 host successfully.  An intrepid repo actually does exist:
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

It is mentioned in the release notes:
[http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)
"Linux additions: support Ubuntu 8.10"

Though they have not yet made the appropriate updates to their download page.

---

### Post by shane19174 on 2008-10-24
> It is mentioned in the release notes:
[http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)
"Linux additions: support Ubuntu 8.10"


Actually, I thought that meant that the "additions" (USB support, etc.) were now available for Intrepid *guests*.

Whatever, though, the good thing is that the repo exists and everything works fine.

---

