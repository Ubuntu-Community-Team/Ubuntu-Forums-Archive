---
title: "Can't install Kernel Updates"
date: 2023-06-28
forum: Installation &amp; Upgrades
---

### Post by dmueller87 on 2023-06-28
Hello there, 

this night unattended upgrade wasn't able to do the automated kernel upgrade. I'm receiving this:

```

[COLOR=#000000][FONT=Menlo]2023-06-28 04:03:32,559 WARNING package linux-generic upgradable but fails to be marked for upgrade (E:Unable to correct problems, you have held broken packages.)
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]2023-06-28 04:03:33,217 WARNING package linux-generic upgradable but fails to be marked for upgrade (E:Unable to correct problems, you have held broken packages.)[/FONT][/COLOR]

```

I tried to manually install via apt install but I'm getting this:
```

[COLOR=#000000][FONT=Menlo]linux-headers-generic : Depends: linux-headers-5.15.0-76-generic but it is not installable[/FONT][/COLOR][COLOR=#000000][FONT=Menlo] 
linux-image-generic : Depends: linux-image-5.15.0-76-generic but it is not going to be installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]                       Depends: linux-modules-extra-5.15.0-76-generic but it is not installable[/FONT][/COLOR]
```

How is this possible? Im already on [COLOR=#000000][FONT=Menlo]5.19.0-45-generic [/FONT][/COLOR]. Why is it requiring this old version?

---

### Post by MAFoElffen on 2023-06-28
Hmmm. Did you first try
```

sudo apt update
sudo apt install --fix-broken
sudo dpkg --configure -a
sudo apt autoremove
sudo apt clean

```
Then do this and post the output within code tags
```

find /boot -maxdepth 1 -mindepth 1 -type f -exec basename {} \;
sudo apt list linux-* --installed
sudo apt list linux-* --upgradable

```
To answer your question why it would upgrade an older version of a Kernel...

Look at the filtered output of my updates:
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo apt list linux-* --upgradable
Listing... Done
linux-generic-hwe-20.04/jammy-updates 5.15.0.76.74 amd64 [upgradable from: 5.15.0.75.73]
linux-generic-hwe-22.04/jammy-updates 5.19.0.46.47~22.04.21 amd64 [upgradable from: 5.19.0.45.46~22.04.20]
linux-generic/jammy-updates 5.15.0.76.74 amd64 [upgradable from: 5.15.0.75.73]
linux-headers-generic-hwe-22.04/jammy-updates 5.19.0.46.47~22.04.21 amd64 [upgradable from: 5.19.0.45.46~22.04.20]
linux-headers-generic/jammy-updates 5.15.0.76.74 amd64 [upgradable from: 5.15.0.75.73]
linux-image-generic-hwe-22.04/jammy-updates 5.19.0.46.47~22.04.21 amd64 [upgradable from: 5.19.0.45.46~22.04.20]
linux-image-generic/jammy-updates 5.15.0.76.74 amd64 [upgradable from: 5.15.0.75.73]
linux-libc-dev/jammy-updates 5.15.0-76.83 amd64 [upgradable from: 5.15.0-75.82]
linux-modules-nvidia-390-generic-hwe-22.04/jammy-updates 5.19.0-46.47~22.04.1 amd64 [upgradable from: 5.19.0-45.46~22.04.1]

```
The older versions are still there on mine because I have both linux-generic and linux-generic-hwe-22.04 stacks installed. Even though you can see that the 5.19.x series kernel are current, there are still 5.15.x kernels present...

If 'present' and if there are security updates, that back-port security patches for the older kernels, then you will get updates in your update stream to patch those kernels that are present... Does that make sense, or should I explain that differently? 

I'll do that anyways. LOL. Because the kernels are installed "on" your system, then they will continue to get security updates. In the off-chance that you 'might' use them, then you are safe and secure.

---

### Post by dmueller87 on 2023-07-01
Thx very much. 

In the meantime I could update like you did. However I still don't get why I should keep two stacks present. Is there a way to remove the old one? I think the 5.15.x is because I startet with Ubuntu Server 22.04.1 and we're on 22.04.2 now. 

But thx again for the explanation.

---

### Post by MAFoElffen on 2023-07-01
The official instructions are here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) But it is not really spelled out in clear language.

What is recommended, is that you have both stacks installed. But if using one, you don't need the other...

Look at this output:
```

mafoelffen@opti-ubuntu:~$ apt list linux-generic* installed
Listing... Done
linux-generic-hwe-20.04-edge/jammy-updates,jammy-security 5.15.0.76.74 amd64
linux-generic-hwe-20.04/jammy-updates,jammy-security 5.15.0.76.74 amd64
linux-generic-hwe-22.04-edge/jammy-updates,jammy-security 5.19.0.43.44~22.04.17 amd64
linux-generic-hwe-22.04/jammy-updates,jammy-security,now 5.19.0.46.47~22.04.21 amd64 [installed]
linux-generic/jammy-updates,jammy-security,now 5.15.0.76.74 amd64 [installed]

mafoelffen@opti-ubuntu:~$ apt list linux-image* --installed
Listing... Done
linux-image-5.15.0-76-generic/jammy-updates,jammy-security,now 5.15.0-76.83 amd64 [installed,automatic]
linux-image-5.19.0-43-generic/jammy-updates,jammy-security,now 5.19.0-43.44~22.04.1 amd64 [installed,automatic]
linux-image-5.19.0-46-generic/jammy-updates,jammy-security,now 5.19.0-46.47~22.04.1 amd64 [installed,automatic]
linux-image-generic-hwe-22.04/jammy-updates,jammy-security,now 5.19.0.46.47~22.04.21 amd64 [installed,automatic]
linux-image-generic/jammy-updates,jammy-security,now 5.15.0.76.74 amd64 [installed,automatic]

```
Above is with both stacks installed (looks like I need to uninstall the HWE stack for 20.04 on that...)

Now look at this server:
```

Listing... Done
linux-generic-hwe-22.04/jammy-updates,jammy-security,now 5.19.0.46.47~22.04.21 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

mafoelffen@Mikes-B460M:~$ apt list linux-image* --installed
Listing... Done
linux-image-5.19.0-45-generic/jammy-updates,jammy-security,now 5.19.0-45.46~22.04.1 amd64 [installed,automatic]
linux-image-5.19.0-46-generic/jammy-updates,jammy-security,now 5.19.0-46.47~22.04.1 amd64 [installed,automatic]
linux-image-generic-hwe-22.04/jammy-updates,jammy-security,now 5.19.0.46.47~22.04.21 amd64 [installed,automatic]

```
Notice with that machine I only have the HWE stack and it's kernels...

To get there uninstall the GA stack:
```

sudo apt remove linux-generic
sudo apt autoremove

```

---

### Post by dmueller87 on 2023-07-02
Thx, I tried that but still I got a huge list. Do you see another way of fixing this?

```

[COLOR=#2FB41D][FONT=Menlo]linux-generic-hwe-20.04-edge[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]/jammy-updates,jammy-security 5.15.0.76.74 amd64
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo][COLOR=#2fb41d]linux-generic-hwe-20.04[/COLOR]/jammy-updates,jammy-security 5.15.0.76.74 amd64[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#2fb41d]linux-generic-hwe-22.04-edge[/COLOR]/jammy-updates,jammy-security 5.19.0.43.44~22.04.17 amd64[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#2fb41d]linux-generic-hwe-22.04[/COLOR]/jammy-updates,jammy-security,now 5.19.0.46.47~22.04.21 amd64 [installed][/FONT][/COLOR]
[COLOR=#2FB41D][FONT=Menlo]linux-generic[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]/jammy-updates,jammy-security 5.15.0.76.74 amd64
[/FONT][/COLOR]
```

---

