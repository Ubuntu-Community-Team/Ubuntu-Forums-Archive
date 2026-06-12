---
title: "Can't install anything"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by Happyman7 on 2010-06-08
Hey

I have Ubuntu 9.10 (Karmic Koala) and it is pretty good. But for some reason I can't install/uninstall _ANYTHING_, in terminal, synaptic, or the USC (Ubuntu Software Center). 
I think the problem is from some package called "pulseaudio-esound-compat." There isn't really much else I can explain, so I took some screenshots of installing & uninstalling things in terminal. 

[I]Trying to install "BzFlag" in terminal.
[/I][U][[IMG]http://img706.imageshack.us/img706/7329/regularb.th.jpg[/IMG]]("http://img706.imageshack.us/i/regularb.jpg/")

[/U][I]Trying to remove "pulseaudio-esound-compat."
[/I][[IMG]http://img35.imageshack.us/img35/9472/removeprob.th.jpg[/IMG]]("http://img35.imageshack.us/i/removeprob.jpg/")

They all lead to the pulseaudio package! 
It even stops me from upgrading Ubuntu! Ubuntu Update Manager doesn't work, because of this issue. 

Could someone tell me how to fix it?

*Other info:*
I am runing Ubuntu 9.10 on a dual boot machine with Windows XP on the other partition. I don't want to affect *_**anything**_* on Windows, as other people use it. 

I haven't used Ubuntu for a long time now, so if you have anything that involves terminal or something of the like, please explain it. I want to know what I am doing before I do something. :D

And before you ask: Yes, I did research this question.

Thanks in Advanced.

---

### Post by pytheas22 on 2010-06-08
From hints in [this thread]("https://answers.launchpad.net/ubuntu/+source/dpkg/+question/22587"), I suspect that the file list for the pulseaudio-esound-compat package is corrupt in some way.  To fix that problem, run:
```

sudo rm /var/lib/dpkg/info/pulseaudio-esound-compat.list
sudo apt-get -f install
```

The first command deletes the file list for the pulseaudio-esound-compat pacakge.  The second command tells the package manager to sort out its issues; along the way, it should realize that the file list in question is missing, download a fresh, uncorrupted copy, and then be able to proceed without issue.  Thereafter you should be able to install packages as normal.

---

### Post by Happyman7 on 2010-06-08
That worked :D 

Thank you soooo much.

---

