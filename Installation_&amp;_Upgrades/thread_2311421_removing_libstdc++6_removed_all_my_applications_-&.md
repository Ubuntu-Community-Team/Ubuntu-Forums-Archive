---
title: "removing libstdc++6 removed all my applications -&gt; can only see the desktop folders"
date: 2016-01-27
forum: Installation &amp; Upgrades
---

### Post by cbungau on 2016-01-27
Hello,

I removed libstdc++6 from my Ubuntu 14.04 32 bit machine. This has removed 15 GB of data and all my applications. I was not aware of the size when PackageManager warned my it will uninstall many programs and it will result in an unstable system.

So now I am left with my desktop folders and files, so it would be OK to assume my home directory content is intact. Trying to insert a memory disc for copying my files results in an unable to mount message.

I am afraid to reboot it as I am worried it might crash completely. 

I would be extremely grateful for any suggestions on how to recover my home directory files and re-install ubuntu.

Thank you,

Cristian

---

### Post by ajgreeny on 2016-01-27
Before you do shut down or reboot you should try to recover whatever you can of your OS and DE by running ```
sudo apt-get install ubuntu-desktop
```  Depending on what applications you can now open you may need to run that command from a command-line tty by using Ctrl+Alt+F1 and logging in to that.
That should at least get you to a situation where you have a GUI system that will run and allow you to reinstall anything else that you had but has now been removed, and it does look as if there will be a lot of those, depending on what extra applications you had added.

If that does not work it is always possible to recover all your /home files and folders by using a live DVD/USB, but let's hope that is not necessary

---

### Post by cbungau on 2016-02-01
Thank you for your reply. I could not open the terminal and Ctrl+Alt+F1 did not work, I must have screwed up everything quite a lot.... I had to use the Live DVD, and I installed Ubuntu 15.10 in a separate partition, and then loading the old partition I copied the content of home directory. Now, some games (TennisElbow2013, SuperTuxKart) do not work - I assume it is a RAM problem - I have 2 GB and a 32 bit system due to the old age of my PC (2010 HP Pavillion) and Intel HD video driver... Probably I should upgrade...

---

### Post by ubfan1 on 2016-02-01
Try xubuntu and lubuntu for older systems with less ram.

---

