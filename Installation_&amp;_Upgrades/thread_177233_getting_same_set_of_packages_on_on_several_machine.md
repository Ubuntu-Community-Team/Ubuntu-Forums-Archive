---
title: "getting same set of packages on on several machines?"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by LazyBoy on 2006-05-16
I  want to get similar set-ups on multiple machines (which have different hardware).  

Once I get one set-up, is there a way to capture the list of packages I've loaded (beyond the installation) so I can load them on the others?

What about other install/config choices?  I imagine there's a way to put a particular distro+basic-config on a DVD  -- it seems like something real IT guys would do.

Thanks,
LB

---

### Post by aysiu on 2006-05-16
It's too bad the systems have different hardware; otherwise, you could have used PartImage to replicate the partition of one once you got it set up the way you want it.

If you go into it knowing that you want to replicate the work you do in one installation on two others, you can make it fairly easy on yourself.

First of all, make sure all the changes you make you make through terminal commands. For example, don't use Synaptic to install AbiWord, BUM, Adobe Acrobat, and Thunderbird. Do ```
sudo apt-get install abiword bum acroread mozilla-thunderbird
``` As you're making changes through the terminal, copy and paste them into a text file. Then make sure the first line of the file says ```
#!/bin/bash
``` and save it as *idealinstall.sh*.

Once you're satisfied with how one installation went, copy that file to the new installation's desktop and then paste this into the terminal: ```
cd ~/Desktop
chmod +x idealinstall.sh
./idealinstall.sh
```

---

