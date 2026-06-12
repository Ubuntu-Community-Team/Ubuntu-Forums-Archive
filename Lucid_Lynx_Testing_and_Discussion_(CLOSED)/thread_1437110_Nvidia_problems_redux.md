---
title: "Nvidia problems redux"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mhenriday on 2010-03-23
I note that **Alberto** states that the **Nvidia** driver problem has been [**_[COLOR="Blue"]resolved[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1423210"), but I'm still encountering problems after upgrading from **Karmic** to **Lucid** on my **HP Pavilion dv9000** laptop. Everytime I attempt to boot into the **2.6.32-17** kernel,I get an error message to the effect that **Ubuntu** will run in low-grafic mode as the **Nvidia** kernel module failed to load. If I click OK and select «Restart X», however, the boot proceeds without any problems. If instead, I boot into the **2.6.31-20** kernel, I don't encounter this message and the computer boots normally into **Lucid**.

This is by no means the most serious problem I've encountered in the process of upgrading to **Lucid beta 1** - see [**_[COLOR="Blue"]this thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1435093") and [**_[COLOR="Blue"]this one[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=9015377#post9015377") for a more detailed description of my trials and tribulations - but I'd be most grateful for any suggestions that could help me resolve it. Thanks in advance !...

Henri

---

### Post by dino99 on 2010-03-23
> **mhenriday said:**
> I note that **Alberto** states that the **Nvidia** driver problem has been [**_[COLOR="Blue"]resolved[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1423210"), but I'm still encountering problems after upgrading from **Karmic** to **Lucid** on my **HP Pavilion dv9000** laptop. Everytime I attempt to boot into the **2.6.32-17** kernel,I get an error message to the effect that **Ubuntu** will run in low-grafic mode as the **Nvidia** kernel module failed to load. If I click OK and select «Restart X», however, the boot proceeds without any problems. If instead, I boot into the **2.6.31-20** kernel, I don't encounter this message and the computer boots normally into **Lucid**.

This is by no means the most serious problem I've encountered in the process of upgrading to **Lucid beta 1** - see [**_[COLOR="Blue"]this thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1435093") and [**_[COLOR="Blue"]this one[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=9015377#post9015377") for a more detailed description of my trials and tribulations - but I'd be most grateful for any suggestions that could help me resolve it. Thanks in advance !...

Henri

Have you run: system - admin - hardware driver ?
Which video packages are installed ? Normally nvidia-current should be activated but jockey says "not in use" (jockey bug)

Be sure that your dist-upgrade is correct: watch your repo list ( no Karmic anymore and remove all ppa you can if you use some)

Often i can wipe problem by cleaning my system (clean, autoclean, autoremove, install -f). There are also some powerfull tools like bleachbit and/or gconf-cleaner ( be carefull before pressing Enter key)

---

### Post by pferraro on 2010-03-23
In my experience, installing nvidia-current is not enough.  You also need to explicitly create an /etc/X11/xorg.conf file specifying the nvidia driver.  If you install the nvidia driver via Jockey, this will be done for you automatically.

---

### Post by mhenriday on 2010-03-24
Thanks for your responses, **dino99** and **pferraro** ! When I check my hardware drivers, I find that the «current version» (which version that is is not stated !) of the **Nvidia** accelerated driver is enabled, but not in use (see the screendump - in Swedish - attached below). A **Broadcom B43** wireless driver is also enabled and this one is in use. Presumably I need to reinstall the **Nvidia** driver via **Jockey** (the jockey-gtk file is installed) as per **pferraro**'s suggestion, but alas, I don't know how to do so. Could someone enlighten me ?...

Henri

---

### Post by kyleabaker on 2010-03-24
Check this:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/545499](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/545499)

Add yourself to affected if this is your problem.

---

### Post by mhenriday on 2010-03-24
> **kyleabaker said:**
> Check this:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/545499](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/545499)

Add yourself to affected if this is your problem.
Thanks for your response, **Kyle** ! If I understand your bug aright, while similar it's not quite the same thing I'm observing. Your box crashes, which I presume to mean that you must reboot ; in my case, however, an error message is displayed and after clicking OK and selecting «Restart X», however, the boot proceeds without any problems. But perhaps I've misunderstood what you mean by «crashing» ?...

Henri

---

### Post by tad1073 on 2010-03-24
> **mhenriday said:**
> Thanks for your responses, **dino99** and **pferraro** ! When I check my hardware drivers, I find that the «current version» (which version that is is not stated !) of the **Nvidia** accelerated driver is enabled, but not in use (see the screendump - in Swedish - attached below). A **Broadcom B43** wireless driver is also enabled and this one is in use. Presumably I need to reinstall the **Nvidia** driver via **Jockey** (the jockey-gtk file is installed) as per **pferraro**'s suggestion, but alas, I don't know how to do so. Could someone enlighten me ?...

Henri

open a terminal an run:

```
sudo nvidia-xconfig
```

then reboot

---

### Post by mhenriday on 2010-03-25
> **tad1073 said:**
> open a terminal an run:

```
sudo nvidia-xconfig
```

then reboot

Thanks for your reply, **tad1073** ! But after installing the **Lucid** updates this morning, the problem seems to have disappeared of itself ! But should it return, I'll certainly try your suggestion....

Henri

---

### Post by dino99 on 2010-03-25
> **mhenriday said:**
> Thanks for your reply, **tad1073** ! But after installing the **Lucid** updates this morning, the problem seems to have disappeared of itself ! But should it return, I'll certainly try your suggestion....

Henri

nvidia-xconfig is an NVIDIA propriatary command, not an ubuntu one and such you might forget it, anyway Lucid now work without xorg.conf. you need it if you want a special config with several screens or tv for example.

---

### Post by mhenriday on 2010-03-25
Thanks for the clarification, **dino99** ! I don't think that **tad1073**'s suggestion will become unavailable to me, despite the ungoing degradation of my memory, as long as these **Ubuntu** fora continue to exist. In any event, I am grateful for the suggestions posted here - and hope they have been of aid to other users - and not least, for the fact that the problem seems to have been resolved....

Henri

---

