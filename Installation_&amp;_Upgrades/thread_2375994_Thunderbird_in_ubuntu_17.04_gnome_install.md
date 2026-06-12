---
title: "Thunderbird in ubuntu 17.04 gnome install"
date: 2017-10-29
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2017-10-29
Hi all. I just installed Ubuntu 17.04 gnome and refreshed the software center. There is no Thunderbird e-mail and calendar there to download.
I then installed Synaptic package manager and the list that shows after a search tor "Thunderbird" is large. I am not at all sure which ones to install here in the US.
If anyone could help I would greatly appreciate it.
Maybe a command line install?
Thanks in advance. Bob.

---

### Post by deadflowr on 2017-10-29
Thunderbird is simply thunderbird in terms of package names.
anything else is anything else.
so simply run
```
sudo apt install thunderbird
```
will install it.

---

### Post by bob brazie on 2017-10-30
Should I do a (i think it is) "sudo update" before or after that command?
Thanks in advance. Bob.

---

### Post by deadflowr on 2017-10-30
> **bob brazie said:**
> Should I do a (i think it is) "sudo update" before or after that command?
Thanks in advance. Bob.

Before. (and it's sudo apt update)
The update command syncs you and the Ubuntu servers package lists, so that when you try to download the package, what they have matches what you think they have.
Otherwise you run into a slight chance of mismatches and then a failure.
If that makes sense.

---

### Post by bob brazie on 2017-10-30
Thanks for you time.

I am having some trouble with the installation of gnome 17.04 as seen in this tread.

[https://ubuntuforums.org/showthread.php?t=2375681&p=13703542#post13703542](https://ubuntuforums.org/showthread.php?t=2375681&p=13703542#post13703542)

If I can ever get this worked out I can use you suggestions.

Thanks again.

---

