---
title: "Update Notifier/Synaptic errors"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by Solon on 2006-08-22
All right, the Update Notifier would notify me of updates, I click on it, type in my password, it would come up. Then, when I click the "install" button, its as if I clicked the "Check" button instead, it would refresh the update window, not install the updates. So I figured I do it through synaptic, so I clicked on that, put in my password again, then nothing would happen, synaptic wouldn't come up, nothing.

So, I thought I would figure out what's wrong with synaptic, so I went to terminal and typed "sudo synaptic", and this is what came up:

> ******@******-linux:~$ sudo synaptic
Password:
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
******@******-linux:~$ 

After I had this problem, I used apt-get, it says that libvte-common is installed, latest version, I then went ahead and used apt-get dist-upgrade, it worked flawlessly. Don't know what's up, but so far I searched for the missing library, it doesn't exist on my system, the best I can tell, frankly I'm baffled.

---

### Post by randell6564 on 2006-08-22
Please post your /etc/apt/sources.list

---

### Post by dgoodwin on 2006-08-22
I have the exact same problem, have you found the solution to correct this problem. I guess it is a good thing synaptic is broken though because it apprears I missed the misery some people went through with the last round of updates that broke the xserver.

---

### Post by ScislaC on 2006-08-22
add one more to the list of people with this issue :confused:

---

### Post by mgpower0 on 2006-08-22
try the fix here [http://www.ubuntuforums.org/showthread.php?t=239095&highlight=libvte.so.4](http://www.ubuntuforums.org/showthread.php?t=239095&highlight=libvte.so.4)

from what i understand a recent compiz update used a Edgy lib not available for dapper. hope it works

---

