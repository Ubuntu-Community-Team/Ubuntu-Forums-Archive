---
title: "Graphics upgrade killed X server"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by MattyRad on 2011-12-10
Hi,

I just upgraded my graphics card from nVidia 430 GT to a nVidia GTX 550 Ti, and after doing so, X won't start, and apparently can't start...

Since the upgrade I am only getting a text based login screen, no GUI. I manually tried "startx" and it gives me a good deal about the nVidia driver not being found or not being able to start.

I deleted xorg.conf and that managed to give me back the GUI. I tried reinstalling the additional drivers for nVidia, but when I do it brings me to the same problem: X can't start.

Any suggestions? I really don't want to have to reinstall Ubuntu clean and completely set my computer back up, especially for a seemingly trivial issue like this one.

---

### Post by MAFoElffen on 2011-12-10
> **MattyRad said:**
> Hi,

I just upgraded my graphics card from nVidia 430 GT to a nVidia GTX 550 Ti, and after doing so, X won't start, and apparently can't start...

Since the upgrade I am only getting a text based login screen, no GUI. I manually tried "startx" and it gives me a good deal about the nVidia driver not being found or not being able to start.

I deleted xorg.conf and that managed to give me back the GUI. I tried reinstalling the additional drivers for nVidia, but when I do it brings me to the same problem: X can't start.

Any suggestions? I really don't want to have to reinstall Ubuntu clean and completely set my computer back up, especially for a seemingly trivial issue like this one.
- What version o0f Ubuntu (or variant) are you running?
- Is it 32bit or 64bit OS?
- What NVidia Drver are you trying to use for your card.
- Did you use the nvidia-installer package to "uninstall" before you started deleting what you thought were driver files?

Can you post the /var/log/nvidia-installer.log file and the /var/Xorg.5.log file. When you do, please use the "#" button in the posting tool bar and paste your text within the code tags.

---

### Post by MattyRad on 2011-12-10
> **MAFoElffen said:**
> - What version o0f Ubuntu (or variant) are you running?
- Is it 32bit or 64bit OS?
- What NVidia Drver are you trying to use for your card.
- Did you use the nvidia-installer package to "uninstall" before you started deleting what you thought were driver files?

Can you post the /var/log/nvidia-installer.log file and the /var/Xorg.5.log file. When you do, please use the "#" button in the posting tool bar and paste your text within the code tags.

Nevermind, I fixed it. I just had to install the proper nvidia driver. I assumed Ubuntu would do that for me.

Thanks anyway.

---

### Post by MAFoElffen on 2011-12-10
> **MattyRad said:**
> Nevermind, I fixed it. I just had to install the proper nvidia driver. I assumed Ubuntu would do that for me.

Thanks anyway.
Your welcome, please mark this solved.

---

