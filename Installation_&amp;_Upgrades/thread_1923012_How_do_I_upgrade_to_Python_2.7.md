---
title: "How do I upgrade to Python 2.7?"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by Uxeh on 2012-02-09
I am using Ubuntu 10.10 which comes by default installed with Python 2.6, however some applications that I want to use require 2.7 and I want to update.

How would I go about doing this?

---

### Post by oldfred on 2012-02-09
Welcome to the forums.

I am running Maverick. If you look in Synaptic with a search on python2.7 it shows all the files. You can do the same with python3.

Whatever you do, do not uninstall 2.6 as Ubuntu uses that for many internal things. You just have to specify in each program or command line when using python to say python2.7 not just python as that will run the default.

---

### Post by Uxeh on 2012-02-09
> **oldfred said:**
> Welcome to the forums.

I am running Maverick. If you look in Synaptic with a search on python2.7 it shows all the files. You can do the same with python3.

Whatever you do, do not uninstall 2.6 as Ubuntu uses that for many internal things. You just have to specify in each program or command line when using python to say python2.7 not just python as that will run the default.

Hi, and thanks. I installed python2.7 however when I use the command python it uses the 2.6 installation, which isn't what I want. I could use python2.7 however when I would install a python module, it would set it up for the 2.6 installation. How would I "replace" 2.7 over 2.6?

---

### Post by oldfred on 2012-02-10
You cannot change the default without breaking the entire system.

If using command line
python2.7

If you are writing programs.

#!/usr/bin/env python2.7
#

You could install in another 10GB partition a newer version of Ubuntu that uses 2.7 as the default if you want.

---

