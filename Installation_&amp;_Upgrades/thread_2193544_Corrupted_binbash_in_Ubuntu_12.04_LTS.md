---
title: "Corrupted /bin/bash in Ubuntu 12.04 LTS"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by Gregor D Seas on 2013-12-13
Hello everyone, 

I have a corrupted /bin/bash in my Ubuntu 12.04.

This is on a new server which I have spent three days configuring and have not yet got any system backups out of it to recover from backup.

Linux giri 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Any ideas how I can recover? Is there anywhere I can find the binary?

Thank you!

---

### Post by Y^2om&amp;#7sgP on 2013-12-13
not sure if this will help mate :)

[http://askubuntu.com/questions/135217/how-to-replace-fix-a-messed-up-bin-sh-and-bin-dash](http://askubuntu.com/questions/135217/how-to-replace-fix-a-messed-up-bin-sh-and-bin-dash)

---

### Post by steeldriver on 2013-12-13
Hello and welcome to the forum

In what way is /bin/bash corrupted? can you be more specific about your symptoms? I was once able to reinstall bash (after a brainfart in which I deleted the binary) - but I had a running shell process to do it from. IIRC I had to temporarily symlink /bin/bash to dash so that the install scripts had an interpreter to run (luckily they didn't seem to contain any bash-specific syntax). Otherwise you may need to chroot from a live disk or usb, I think.

---

### Post by Gregor D Seas on 2013-12-13
@steeldriver, mine was not a brainfart but a brain diarrhoea (lets not speak of what I did). I do have a running shell process. I have symlinked already /bin/bash to /bin/dash. 

What do I do now to get a fresh /bin/bash installed?

Thanks!

---

### Post by steeldriver on 2013-12-13
Have you tried just doing

```
sudo apt-get install --reinstall bash
```

*If* it works it should overwrite your symlink and hopefully everything will be back to normal... at least I *think* that's all I did

---

### Post by Gregor D Seas on 2013-12-13
> **steeldriver said:**
> Have you tried just doing

```
sudo apt-get install --reinstall bash
```

*If* it works it should overwrite your symlink and hopefully everything will be back to normal... at least I *think* that's all I did

I can try this. On a second thought, would copying the /bin/dash binary (if a kind soul can share and has the same kernel version with me -- if the precise version matters) work?
I now wonder which one is more ...dangerous (apt-get reinstall or the binary copy).

My version:

 Linux giri 3.2.0-57-generic ---  x86_64 x86_64 x86_64 GNU/Linux

---

### Post by steeldriver on 2013-12-13
I just tried it in a Kubuntu 12.04 VM

1. removed /bin/bash

2. attempted to open another terminal (Konsole) - fell back to sh with a big red warning

3. symlinked bash to dash from the working terminal

```
sudo ln -s dash /bin/bash
```

4. ran the apt get

```
sudo apt-get install --reinstall bash
```

5. all seemed to run OK, checked with

```

steeldriver@steeldriver-VirtualBox:~$ ls -l /bin/bash
-rwxr-xr-x 1 root root 959120 Mar 28  2013 /bin/bash
steeldriver@steeldriver-VirtualBox:~$ 

```

(symlink is gone) and new terminals now open without complaining

---

### Post by Gregor D Seas on 2013-12-13
Perfect, this is the answer, just did it. I am back in business. Thank you @steeldriver.

How can we mark this as SOLVED for the benefit of others?

---

### Post by steeldriver on 2013-12-13
Great - you should be able to mark as SOLVED using the 'Thread Tools' menu above the first post

---

