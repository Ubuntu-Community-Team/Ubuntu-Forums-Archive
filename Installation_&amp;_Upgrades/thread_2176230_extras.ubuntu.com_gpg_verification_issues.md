---
title: "extras.ubuntu.com gpg verification issues"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by Christian Heinrichs on 2013-09-23
Hi Ubuntu forums, it's me again.

After a clean, fresh install of Lubuntu 13.04 32 bit on an offline machine, I am desperately trying to update and upgrade all the packages with the help of an online computer.
The program of choice was [apt-offline]("http://apt-offline.alioth.debian.org/") and when entering the last command to install the packages:
```
sudo apt-offline install --verbose apt-offline.zip
```
I get the error:
```
ERROR: I couldn't understand file type extras.ubuntu.com_ubuntu_dists_raring_Release.gpg
```

So I thought this would be a bug with apt-offline, but the developer found out that this is a bug with the extra repositories for Ubuntu. Read about it [here]("https://github.com/rickysarraf/apt-offline/issues/1#issuecomment-24880208").

Please help, as I am not able to solve this by myself.

---

### Post by gordintoronto on 2013-09-24
It's not clear what you tried to do: an upgrade from an older version, or a fresh install.

With a fresh install (on an older machine?) I would assume that you would download Lubuntu 13.04, burn the ISO to DVD, and install from there. I don't see how Apt-offline would be involved.

---

### Post by Christian Heinrichs on 2013-09-24
> **gordintoronto said:**
> It's not clear what you tried to do: an upgrade from an older version, or a fresh install.

I am sorry for not formulating the question properly.
Either check the edited post or read this:

Lubuntu 13.04 32 bit was successfully installed on the offline machine. The problem is not about upgrading or installing Lubuntu.
The problem is that I can't update and upgrade all the packages on the offline system, where Lubuntu 13.04 32 bit was freshly installed.

---

### Post by gordintoronto on 2013-09-24
Thanks, now I understand the question. Sorry, I have no relevant experience.

---

