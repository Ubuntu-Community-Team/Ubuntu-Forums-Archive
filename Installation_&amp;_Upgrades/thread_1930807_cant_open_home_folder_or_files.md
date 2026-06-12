---
title: "cant open home folder or files"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by cjay on 2012-02-24
I am unable to open my home folder or any related files
I am running Ubuntu 11.04 in Classic mode
All was OK until an Update Manager install
I have tried a Nautilus purge and reinstall but no joy 
I have typed Nautilus in a Terminal and this is the result

root@xxxxx-laptop:/home/xxxx# nautilus
Initializing nautilus-gdu extension

** (nautilus:16957): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '16957'

(nautilus:16957): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Please help if possible 
I would hate to have to do a re-install of my OS 

Thanks

If looking *your* mirror freaks you out, you wanna try looking in *mine*

---

### Post by sudodus on 2012-02-24
I have some questions to clarify what is the problem:

1. What happens if you try to open some other folder (not the home folder)? Can you browse it with Nautilus?

2. What happens if you open a terminal window and run the command
```
ls -l
``` Does it list the content of your home directory?

Maybe you can try to ***update and upgrade*** and watch the response, if there are error messages or suggestions what to do:
```
sudo apt-get update
sudo apt-get upgrade
```

---

