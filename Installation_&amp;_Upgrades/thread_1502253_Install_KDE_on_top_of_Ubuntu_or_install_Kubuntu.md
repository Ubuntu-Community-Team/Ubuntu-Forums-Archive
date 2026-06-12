---
title: "Install KDE on top of Ubuntu or install Kubuntu?"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by fs_tigre on 2010-06-05
Hi,

I have been using Ubuntu with Gnome but last night I installed KDE and I really like it but I was wondering if there was an issue by having the two installed.

Would that be better to uninstall Ubuntu and just install Kubuntu? If yes, will I see any difference?

Whats better to have Kubuntu and Ubuntu separately installed or it doesn't make a difference?

Thanks a lot!

---

### Post by tommcd on 2010-06-05
> **fs_tigre said:**
> 
I have been using Ubuntu with Gnome but last night I installed KDE and I really like it but I was wondering if there was an issue by having the two installed.
There should not be any conflicts between the Gnome gtk libraries and the KDE Qt libraries.
> **fs_tigre said:**
> 
Would that be better to uninstall Ubuntu and just install Kubuntu? If yes, will I see any difference?
Whats better to have Kubuntu and Ubuntu separately installed or it doesn't make a difference?

When you have both Gnome and KDE installed you have a lot of bloat on your system imo. Since Ubuntu/Kubuntu is bloated to begin with, you end up with a LOT of extra bloat. 
This should not cause you any performance problems though. So, unless your root directory is short on space you should be fine.

---

### Post by fs_tigre on 2010-06-05
Thank you very much for your reply.

Will I be able to access the same files from either one (my personal files, home directory etc)?

How can I actually install Kubuntu without Ubuntu? When I downloaded Ubuntu it didn't have an option for Kubuntu.

Thanks

---

### Post by drpjkurian on 2010-06-05
Hi
You can download Kubuntu Lucid as torrent and install it.

You can access the files as well as operate all the programmes in either of the desktop environment.

I am having both KDE and Gnome.

---

### Post by fs_tigre on 2010-06-06
Thanks a lot!

---

### Post by sXeChris on 2010-06-06
You can get Kubuntu the same way you attained Ubuntu, ordering a disk, burning it, etc.

You won't find the option to download Kubuntu on an Ubuntu installation disk because it's something completely different.

---

### Post by wojox on 2010-06-06
> **sXeChris said:**
> You can get Kubuntu the same way you attained Ubuntu, ordering a disk, burning it, etc.

You won't find the option to download Kubuntu on an Ubuntu installation disk because it's something completely different.

Actually download the Minimal CD and you can install it through there.

---

### Post by tommcd on 2010-06-06
> **wojox said:**
> Actually download the Minimal CD and you can install it through there.
If you want a guide to using the minimal install CD, see this:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Note that a relatively fast internet connection is recommended for this, since you will need to apt-get all the software you will need.
Then to install KDE, just run:
```
sudo apt-get install kubuntu-desktop
```
Note that this will give you the same system that you would have ended up with if you just installed from the Kubuntu live CD.
The advantage of the minimal install CD is that you can pick and choose exactly what you want. So you can end up with a customized system to suit your needs if you want to exclude packages (like pulseaudio perhaps!!) that you may never need or want.

---

