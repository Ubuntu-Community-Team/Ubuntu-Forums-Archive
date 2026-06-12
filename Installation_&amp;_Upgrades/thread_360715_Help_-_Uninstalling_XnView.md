---
title: "Help - Uninstalling XnView"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by maloki on 2007-02-13
Hello, the other day i got the brilliant idea to text XnView. I installed the program by help from some forum using the following command's. What i would like to do is to Uninstall the program, all answer appreciated. Maybe not the best place to ask this question, but i didn't find a forum category fitting for my question
Best regards: Maloki

I downloaded the following file XnView-1.70-x86-unknown-linux2.x-static-fc4 extracted it and and the following things i did was:

```
#cd XnView-1.70-x86-unknown-linux2.x-static-fc4
#chmod +x install 
#sudo ./install
```

Then i was told to type in:

```
#xnview
```

And this is the code that i got when i followed the above steps:

```
root@loki-desktop:/home/loki/Tempo/XnView-1.70-x86-unknown-linux2.x-static-fc4# sudo ./install
  OS  : Linux, version 2.6.17-11-generic
This script will install nview/nconvert/xnview in the /usr/local/bin directory
cp: cannot create regular file `/usr/lib/X11/app-defaults/XnView': No such file or directory
chmod: cannot access `/usr/lib/X11/app-defaults/XnView': No such file or directory

Done!
root@loki-desktop:/home/loki/Tempo/XnView-1.70-x86-unknown-linux2.x-static-fc4# xnview
** XnView v1.70 Copyright 1991-2005 Pierre-E Gougelet (Sep  6 2005/15:28:24) **
        Version for Linux x86/Motif (All rights reserved)
** This is freeware software (for non commercial use)

     Type xnview -help, for more information
```

---

