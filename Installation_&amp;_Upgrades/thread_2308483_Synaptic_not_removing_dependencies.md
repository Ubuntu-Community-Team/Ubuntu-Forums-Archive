---
title: "Synaptic not removing dependencies"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by PaulBx on 2016-01-03
I installed tiemu, a TI-89 calculator emulator. It had various dependencies like libticables2, libticonv7 and libtifiles2 that it also installed. All well and good.

I played with it a bit and decided to uninstall tiemu. I told Synaptic to "mark for complete removal" and it did that. Then I looked at the dependencies and found them still installed.

Somehow, I imagined Synaptic would be able to find dependencies that were used by nothing else and uninstall them as well. If that's not the way it works, I must have a huge load of libraries that none of my programs are using... Is that the way it is supposed to work? Do we have to chase down the dependencies manually, when doing removals?

I looked in the Synaptic help and found nothing about dependencies, where removal was concerned.

uname -a shows this:
Linux len780 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Synaptic is version 0.81.1

---

### Post by Dennis N on 2016-01-03
"Complete Removal" removes configuration files, but not these unneeded dependencies (orphans). You can remove them with:
```
sudo apt-get autoremove
``` 
or you can also remove them with Synaptic. Synatpic shows the orphans in its file display window if you click "Status" and then in the selection box "Installed (autoremovable)". You can then remove these.
 
Note: autoremove only works on files originally installed as dependencies by apt or Synaptic!

You can run a simulation first to see what will happen by using the -s option with apt-get. On my machine:

```
dmn@Zotac:~$ apt-get -s autoremove
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcmis-0.4-4 linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-3.13.0-71 linux-headers-3.13.0-71-generic
  linux-image-3.13.0-32-generic linux-image-3.13.0-71-generic
  linux-image-extra-3.13.0-32-generic linux-image-extra-3.13.0-71-generic
  linux-signed-image-3.13.0-71-generic

``` 

If you want to go ahead and do it, rerun with sudo and without the -s

---

### Post by PaulBx on 2016-01-03
Thanks, I did it in Synaptic this time. I'll have to remember that...

---

