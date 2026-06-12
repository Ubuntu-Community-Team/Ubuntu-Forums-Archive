---
title: "gcc command not found..."
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by SangLad on 2007-04-14
I am installing vpnclient for cisco and when I am installing it (./vpnclient), I am getting error: gcc command not found.

When I do: ls -l /usr/bin/gcc

it is saying that I have gcc-4.1

I think I may have deleted the gcc file in the /usr/bin.

How can I reinstall this? or fix this problem?

I am a linux newbie and I have searched this forums and the web as well.

I have tried : apt-get install gcc, but it says I already have the latest version.

Should I completely uninstall gcc? if so, how?

Thanks for all your help!!

---

### Post by Legionox on 2007-04-14
Go to System -> Administration -> Synaptic Package Manager
Search gcc and find the package gcc
Click once on the green square to the left and select "Mark for Reinstallation"
Up the top click "Apply"

Hope this helps

---

### Post by TheWizzard on 2007-04-14
> **Legionox said:**
> Go to System -> Administration -> Synaptic Package Manager
Search gcc and find the package gcc
Click once on the green square to the left and select "Mark for Reinstallation"
Up the top click "Apply"

Hope this helps

it's better to install the **build-essential **meta-package!

---

