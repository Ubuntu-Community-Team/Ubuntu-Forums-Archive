---
title: "possible to reinstall &quot;/&quot; only?"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by HyperFlexed on 2010-09-01
Hi, my system is screwed.

Rather than sift through all the errors, I'd much rather reinstall ubuntu. However, I don't want to reinstall all my old programs.

I have my system partitioned with separate partitions for boot, home, var, usr, and tmp. The root directory also has its own partition. Because root is on its own partition, would there be a way of reinstalling only root while keeping already installed programs intact?

If not, I need to decrypt and back up my home folder. Any advice on how to go about this? I've never done it from the command line, and I notice in recovery mode my home folder contains many fewer files than I'm used to seeing. Some ecrypt file is there and I guess my home folder is hiding inside it.

additional notes:
My OS failed to boot properly after an upgrade. Before shutting down I was also experimenting with davical, and had used the command "sudo tasksel install lamp-server". When I couldn't get it to work I went "sudo tasksel remove lamp-server" but I noticed it was removing things like pulseaudio. My fear is that this tasksel thing removed more than it was supposed to. When I try failsafeX in recovery mode, it says something about not being able to detect screens, but the live CD detects the screen just fine. This leads me to believe some critical piece of software is missing.

Isn't there some kind of repair command or metapackage to verify/install what Ubuntu needs to boot and get me to the login screen?

---

### Post by zvacet on 2010-09-01
> Isn't there some kind of repair command or metapackage to verify/install what Ubuntu needs to boot and get me to the login screen?

You can try with 

```
sudo tasksel install ubuntu-desktop
```

If you want to reinstall you will keep setting (not programs) on your home partition.If you want to reinstall all programs you have now then 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
```

Send that text file to your e-mail.After reinstalling Ubuntu put that file in your home and 

```
sudo xargs aptitude --schedule-only install < my-packages
sudo aptitude install
```

EDIT:**If you are going to reinstall then do not format any other partition except root.**

---

### Post by HyperFlexed on 2010-09-02
so if I do reinstall, and I elect not to format HOME, ubuntu will be smart enough to leave it alone?

---

### Post by zvacet on 2010-09-02
Yes!

---

