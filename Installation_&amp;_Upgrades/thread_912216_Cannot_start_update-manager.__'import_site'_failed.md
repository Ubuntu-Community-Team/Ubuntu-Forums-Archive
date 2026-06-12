---
title: "Cannot start update-manager.  'import site' failed; use -v for traceback"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by kstrike155 on 2008-09-06
Hello everyone,

Let me start by saying that I'm an Ubuntu/Linux n00b, so any help you might give me might need to be a little more detailed ;)  Although I am a software engineer, I'm coming from a Windows world.

Now, onto the problem.  This morning when I tried to launch the Update Manager from System->Administration, it wouldn't launch.  So I tried launching from a Terminal window using "sudo update-manager".  Here is my output:
```
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 25, in <module>
    import pygtk
ImportError: No module named pygtk

```
I went to Synaptic and looked at my Python packages, which are installed correctly.  I did a little searching and it seems that if I were to install python-gobject that this would fix the problem.  I already had it installed, but I reinstalled it.  No effect.

So now I'm here, asking for help, because I don't know what I'm dong. :)

I'm running Ubuntu 8.04, Kernal 2.6.24-19-generic, x86_64.

Thanks for your support!
Brian

---

### Post by Partyboi2 on 2008-09-06
Have you tried to reinstall python-gtk2 package?

---

### Post by kstrike155 on 2008-09-07
Yes, I've tried that.  It still has the same error.

Thanks,
Brian

---

