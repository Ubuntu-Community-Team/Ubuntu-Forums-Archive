---
title: "Skype 2.2 + not working."
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by api984 on 2011-04-25
Hello,

[B]I Installed Ubuntu 10.10 x64. Skype 2.2 beta. Updatead regulary Ubuntu updates on the system. 
[/B]
**Skype 2.2 terminal output:**

andrej@atlantis:~/Downloads$ **skype** :)

(<unknown>:17651): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:17651): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:17651): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:17651): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:17651): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:17651): Gtk-WARNING **: Loading IM context type 'ibus' failed
**Segmentation fault** :popcorn:

**Info:**

GTK-Warning came before. Is there any way to debug why SEGFAULT came? Did anyone had the same problem with Skype. Not sure why it came like that.

**What did I try:**

1) V4L - Used for my WebCam
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit

2) Skype STATIC - Did not fix

3) Reinstall (Complete removal + install again)

4) Downgrade to lower version?? Searching for some older copy....

5) Pidgin - Skype Plugin (not tested, wondering if Audio/Video works there)

Will post same thing on skype until i try some things.

---

### Post by api984 on 2011-04-25
Seems to have been caused by:

SLEEP (S3).

Restart helped.

---

