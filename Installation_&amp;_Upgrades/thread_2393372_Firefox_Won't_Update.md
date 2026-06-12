---
title: "Firefox Won't Update"
date: 2018-06-02
forum: Installation &amp; Upgrades
---

### Post by sdsurfer on 2018-06-02
Ubuntu 17.04
Firefox is currently 57.0.4 64 bit
Did do some searching, apologies in advance if I missed a resource. Been on and off this for a few weeks.

This is probably more of a confirmation than a problem requiring a solution. I keep getting those annoying "Your Firefox is critically out of date" messages, and have tried every update/upgrade, several times, always with the result

*"firefox is already the newest version (57.0.4+build1-0ubuntu0.17.04.1)"*

I suppose I could opt out of the update messages, just wondering, am I missing something? FF can't be upgraded past 57.0.4 on ubuntu 17.04? 

Thank you in advance.

---

### Post by monkeybrain20122 on 2018-06-02
Because Ubuntu 17.04 has reached end of life. All its repos have been removed. Now you should migrate to Ubuntu 18.04. And instead of doing "upgrade" which seems to be the source of > 50% of the problems here, back up your data and do a clean install.

---

### Post by Dennis N on 2018-06-02
For security reasons, I would say that the best suggestion for most users is to upgrade to a supported Ubuntu which would also have the latest available Firefox. Do you have a compelling reason not to? If so, you should know that the newest Firefox version is available for download from [www.mozilla.org](www.mozilla.org). The thing is, it is not automatically installed. Not difficult, but you have to know how to set it up yourself.

---

### Post by sdsurfer on 2018-06-02
Thank you, laziness/finding time/kinda like Unity over Gnome/other excuses mostly. :-) I can get through it, I have two disks for Windows and Linux/Ubuntu, I rarely go back into Windows any more (mostly for a video editor I use.) Was just wondering if 57.04 is the latest 17.04 can go.

---

### Post by Impavidus on 2018-06-02
Ubuntu 17.04 reached end of life back in January, so that's already a while ago. I find upgrades quite reliable, but 17.10 is close to end of life too, so you'd need a double upgrade to 18.04, which means that a fresh install is better. And Unity is still available on 18.04, it's just not the default any more.

---

### Post by monkeybrain20122 on 2018-06-02
> **sdsurfer said:**
> Thank you, laziness/finding time/kinda like Unity over Gnome/other excuses mostly. :-) I can get through it, I have two disks for Windows and Linux/Ubuntu, I rarely go back into Windows any more (mostly for a video editor I use.) Was just wondering if 57.04 is the latest 17.04 can go.

You can install unity easily in 18.04 thanks to the community [https://community.ubuntu.com/c/desktop/ubuntu-unity-dev](https://community.ubuntu.com/c/desktop/ubuntu-unity-dev)

```
sudo apt install ubuntu-unity-desktop
```

make lightdm default when prompted.

then reboot.

If you use touchpad

```
sudo apt install xserver-xorg-input-synaptics
```

I am using unity in 18.04. It is smooth and fast and much more responsive than gnome shell. If all works you can safely remove gnome-shell

---

