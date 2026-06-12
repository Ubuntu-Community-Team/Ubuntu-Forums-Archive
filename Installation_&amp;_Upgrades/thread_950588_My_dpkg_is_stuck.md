---
title: "My dpkg is stuck"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by I_love_Life on 2008-10-17
I wanted to download some files from a repository, but being behind a proxy the instalation wasn't succesful (it couldn't download)

Now every time I want to enter Synaptic Package manager I get the message something is broken (and to run the command dpkg --configure -a). If I do that it tries to continue the download (and the proxy blocks it).

Do you know how to cancel this package instalation ?
Thanks

---

### Post by lincoln32 on 2008-10-17
I just got the same on a spare pc doing updates I think a repository is messed up her looking for answer now

---

### Post by lincoln32 on 2008-10-21
just fixed mine, open terminal and type sudo then the dpkg config -a as in the error code "" and the repudated and all working fine mow

---

### Post by Partyboi2 on 2008-10-21
> **I_love_Life said:**
> I wanted to download some files from a repository, but being behind a proxy the instalation wasn't succesful (it couldn't download)

Now every time I want to enter Synaptic Package manager I get the message something is broken (and to run the command dpkg --configure -a). If I do that it tries to continue the download (and the proxy blocks it).

Do you know how to cancel this package instalation ?
Thanks
Have you set the proxy settings in Synaptic (System>Admin>Synaptic Package manager>Settings>Preferences>Network) Another place to check your proxy settings are correct is System >Preferences >Network Proxy.

---

### Post by I_love_Life on 2008-10-23
I did both of what you said (network proxy from preferences and network from Synaptic package manager). It still doesn't work. I have the same proxy for firefox and I can browse the web... maybe it's not the proxy then ?

I tryed to install something by apt-get and it worked now... although yesterday it didn't (I did no changes to the network settings).
Is it a problem with the proxy server ?

---

### Post by lincoln32 on 2008-10-23
sudo command dpkg --configure -a      this the exact code I used
to repair mine I think it told the dpkg to look at the -a configuration file shold worh for yours but I will keep looking for other concerns

---

