---
title: "Persistant Upgrade annoyance"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by bdalzell on 2007-04-11
Every time a new kernel release comes out and I use the upgrade manager to install it - my nvidia drivers get trashed and I have to go through the whole process of reinstalling them in order to run google earth.

Why does the upgrade have to trash the nvidia driver setup. Why can't the beta testers for the upgrade test it on a machine with an nvidia graphics chip set before uploading it?

In the past all that happened was that google earth reported that the drivers were missing and it would not work properly but with the upgrade that presented itself today (April 11 2007) tryign to bring up google earth reboots the computer completely.

I have been using Ubuntu for over two years now and this is the first application error that I have found that actually crashes the computer back to a complete reboot (as opposed to freezing it up, etc). 

I am using Edgie

Frustrated

---

### Post by mhansen on 2007-04-11
I use the nvidia driver too, so I share your frustration, but this simply isn't an Ubuntu problem.  Like Forrest Gump's mama used to say, "Using proprietary drivers is like a box of chocolates.  You never know what you're gonna get."

To ask the kernel developers to build the kernel packages around nvidia's willingly (stubbornly?) closed-source, proprietary drivers is ***-backwards.  The bottom line is that it's an nvidia issue.  


Regards,
Mike

---

### Post by codejunkie on 2007-04-11
> **bdalzell said:**
> Every time a new kernel release comes out and I use the upgrade manager to install it - my nvidia drivers get trashed and I have to go through the whole process of reinstalling them in order to run google earth.

Why does the upgrade have to trash the nvidia driver setup. Why can't the beta testers for the upgrade test it on a machine with an nvidia graphics chip set before uploading it?

In the past all that happened was that google earth reported that the drivers were missing and it would not work properly but with the upgrade that presented itself today (April 11 2007) tryign to bring up google earth reboots the computer completely.

I have been using Ubuntu for over two years now and this is the first application error that I have found that actually crashes the computer back to a complete reboot (as opposed to freezing it up, etc). 

I am using Edgie

Frustrated
i have had this happen to me also, if you use the .run package from [www.nvidia.com](www.nvidia.com) this will happen every time a new kernel is installed, because when a new kernel is installed you need to build the module for that kernel, or this can happen when part of the xserver has been upgraded that overwrites libglx.so. the easiest way to avoid this problem is to use the nvidia drivers provided in synaptic this way it will reinstall the drivers for the new kernel automatically and you shouldn't notice any changes because synaptic should take care of things for you.

---

