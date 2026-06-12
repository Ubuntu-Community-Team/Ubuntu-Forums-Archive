---
title: "How to install Ubuntu server edition?"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by kwits on 2008-10-02
Good Day,

  I purchased an Ubuntu v8.04.1 DVD that supposedly has desktop and server editions.  I have a multiboot environment with Windows XP Professional on the primary partition while Ubuntu is part of a logical partition or extension.  I installed Ubuntu using all defaults but I am not sure what edition that I installed since I was not prompted.  How do I insure that I install server vs. desktop?

Regards,
KWITS

---

### Post by cariboo on 2008-10-02
A quick way to tell whether you installed the desktop or the server is if it boots to command prompt, you installed the server. If it boots to a desktop you installed the desktop version.

Another way is in a Applcations-->Accessories-->Terminal type:

```
uname -a
```

If you installed the desktop version, the output should look like this: 

```
uname -a
Linux intrepid 2.6.27-4-generic #1 SMP Wed Sep 24 01:29:06 UTC 2008 x86_64 GNU/Linux
```

For the server version it would look like this:

```
uname -a
Linux Willy 2.6.24-19-server #1 SMP Wed Aug 20 18:43:06 UTC 2008 x86_64 GNU/Linux
```

I beleive you have to specify which version you want to install at the menu screen. Press F1 for help.

Jim

---

### Post by Sef on 2008-10-02
The server just has a command line, not a GUI desktop.

---

