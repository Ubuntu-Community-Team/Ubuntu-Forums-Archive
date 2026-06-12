---
title: "Cant install anything"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by noenter1 on 2007-07-19
I was installing a deb package when my power went out. I rebooted everything seemed fine, then i noticed i couldn't install anything. It wouldn't even let me get into synaptic package manager. When ever i try to install a deb package it says either i don't have permission(i do have correct permissions) or that it is corrupt(tried the original one i downloaded and several others). No files on my comp seem to be corrupted(both old and newly downloaded text, audio, and video)

This is what it says when i try to open synaptic no matter how many times i restart my comp:
```
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

These are the errors i get when i do; sudo apt-get update:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

These are the errors when i do; sudo apt-get upgrade:
```
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
```

I have never had this problem before. Any help would be appreciated.

---

### Post by ddrichardson on 2007-07-19
The lock file wasn't removed because apt-get didn't terminate normally. Type:

sudo rm /var/lib/dpkg/lock

at the terminal.

---

### Post by noenter1 on 2007-07-19
Its still complaining that secondlife need to be reinstalled, however it still says that the .deb is corrupt or i don't have the correct permissions.
Edit: That did get rid of the apt-get update errors though.

---

### Post by ddrichardson on 2007-07-19
Did you install secondlife directly or through apt-get? It sounds like you don't have it in your sources repositories.

---

### Post by noenter1 on 2007-07-19
I got it through getdeb.net(wich i found out isnt even updated)

---

### Post by ddrichardson on 2007-07-19
I take it you clicked on a link and installed it directly? I notice the site has no repository, so apt-get wont work. Do a *sudo apt-get remove secondlife-install* then download it again.

---

### Post by noenter1 on 2007-07-19
```
 sudo apt-get remove secondlife-install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
```
No luck

---

### Post by noenter1 on 2007-07-19
Is there anyway to just make it forget about secondlife?

---

### Post by ddrichardson on 2007-07-19
Yes I've been in this position before when trying to get a sound driver installed. You're a bit stuck here because you wont be able to install the package either.

According to the [apt FAQ]("http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html#s-erros-comuns"):

Type *sudo apt-get -f install; sudo dpkg --configure -a* but do it twice if it doesn't work the first time.

---

### Post by DoruHush on 2007-07-19
Try that in the terminal:
```
sudo dpkg --remove --force-remove-reinstreq secondlife-install
```

---

### Post by noenter1 on 2007-07-19
Thank you DoruHush that worked ill make a note of it for future reference. And thank you ddrichardson for the help.

---

