---
title: "Repositories Gutsy 7.10"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by barqers on 2007-10-23
Okay so when I installed Gutsy, I am assuming the respositories were not transfered correctly, since I unplugged my internet in order to get past 82%.

Could someone post me the contents of their sources file? or tell me which repositories to add?

I am saying this because I could not find various applications, such as frostwire, wine, and gstreamer in synaptic package manager.

Thank you,

Francois

---

### Post by leexgx on 2007-10-23
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095)

goto System > Admin > software sources

1 Tick all box's apart form source code (do not think norm users need that)
2 Pick your Download From server location (as it picks main server by default click on search if you cant see one for you)
3 Goto updates and tick the first 2 options
4 [Optional] change the auto up date check to [Download all updates in background] (assuming you do not have an hard disk that is very small its an better option so your ready to install when you are ready just means you do not need to have to wait for them to download)
do not recommend auto install with out confirmation as it may not wait for all updates to be install when shutting down the pc, as it make brake your box

---

### Post by ester.galimany on 2007-10-31
What repositories are necessary to be able to update the system?
I try to lower the codecs for mp3...
On having tried to install GStreamer extra plugins, system says me that it cannot that is necessary to install gstreamer0.10-plugins-ugly from synaptic, but I cannot for conflicts and probably because I do not have well the repositories.
That I can do?

---

### Post by ryanshaw on 2007-11-06
Thank you leexgx
This fixed my issue with not being able to install syslinux.  It was a post a few days ago with no response.  I've had other install issues and maybe this will fix them also.

---

