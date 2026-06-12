---
title: "Embedded Linux with no package manager"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by Mike_Winter on 2014-04-16
Hi
I am a newbie on Linux \ ARM, etc so excuse me and my ignorance!
I have a project where I am using an ARM embedded device running Linux Ubuntu. Part of this project is to use VoIP, and I have been looking at PJSip. I have been able to cross compile PJSip, and run the sample program (PJSUA), however I do not get any audio. I believe this is due to certain packages are not installed. The target device does not have a package manager installed, so I am wondering how to install the packages that are needed?
A list of the needed packages are:
[FONT=Courier New]alsa-base
alsa-utils
alsa-tools
libasound2-plugins
libasound2
libasound2-dev
libasound-dev

How do I go about getting the packages? I can think of 2 methods - 1 is to download the packages on another device and somehow install from there, and the other would be to install a package manager (how?) and then use the normal method.
I have also tried cross compiling PJSip for the Raspberry Pi, and I managed to get this to work, so I know I am on the right route!

Any help or advice will be greatly appreciated!
Mike

I have been able to [/FONT]

---

### Post by ian-weisser on 2014-04-16
It's probably easier to manually install what you need rather than install a package manager.

If you install a package manager, it will promptly complain that lots of critical dependencies are not installed...because it cares about packages, and those packages are not installed.

To install manually, download the software_name.tar.gz (tarball) file (you can even get those from packages.ubuntu.com)
Download it, decompress it, look for the INSTALL file, read it, and follow the instructions.

It's usually pretty easy.

Without a package manager, *you* handle updates and dependencies and uninstalling. I find it handy to keep a diary or log of exactly what you do, and where to find the isntructions or software to do it.

---

### Post by Mike_Winter on 2014-04-17
Hi ian-weisser
Thanks for your help. I will hopefully get the chance to give this a try this afternoon. I will let you know how I get on

Regards

Mike

---

### Post by Mike_Winter on 2014-04-17
I was just having a quick look around on packages.ubuntu.com and hopefully have a question. I notice that some of the required packages have AMD or i386 options. My target device is an ARM processor, so which package would I need? I have had a google, but not found an answer...
Thanks
Mike

---

