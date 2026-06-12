---
title: "error no such device"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by psheldrake on 2010-02-06
Ubuntu newbie. Installed 9.1 overwriting a previous XP install. Rebooting with CD removed fails with "error no such device" followed by a long alpha numeric string I'm guessing indicates a drive.

Being a good forum user, I did find:
[http://ubuntuforums.org/showthread.php?t=1358061](http://ubuntuforums.org/showthread.php?t=1358061)

Talks about a bug with Grub 2. Now I've read about what Grub does, but that doesn't make me an expert. Is there any step by step instruction, that doesn't assume I can hack the Pentagon, to help me to get Ubuntu to work?

Thanks in advance.

---

### Post by presence1960 on 2010-02-06
> **psheldrake said:**
> Ubuntu newbie. Installed 9.1 overwriting a previous XP install. Rebooting with CD removed fails with "error no such device" followed by a long alpha numeric string I'm guessing indicates a drive.

Being a good forum user, I did find:
[http://ubuntuforums.org/showthread.php?t=1358061](http://ubuntuforums.org/showthread.php?t=1358061)

Talks about a bug with Grub 2. Now I've read about what Grub does, but that doesn't make me an expert. Is there any step by step instruction, that doesn't assume I can hack the Pentagon, to help me to get Ubuntu to work?

Thanks in advance.

Boot without the CD, at the GRUB menu highlight Ubuntu. DO NOT PRESS ENTER. press "e" instead. At the next screen use the arrow keys to navigate to --no-floppy. Delete --no-floppy only. Press control + x to boot ubuntu. Once the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
gksu gedit /usr/lib/grub/grub-mkconfig_lib
```

Scroll down a little to the same line you saw when you booted that contains the --no-floppy line. Again delete only the --no-floppy. Click Save on top toolbar & close file. 

In terminal run ```
sudo update-grub
``` This should remove the offending --no-floppy phrase from the GRUB menu and you should be able to boot normally now.

---

### Post by psheldrake on 2010-02-08
Wonderful. Works a treat, thank you.

For anyone wishing to follow the instructions, you should know that in the editing step following
```
gksu gedit /usr/lib/grub/grub-mkconfig_lib
```
You need to delete several lines, beginning "IF" before the mention of the floppy, and ending "FI".

Best regards.

---

### Post by presence1960 on 2010-02-08
> **psheldrake said:**
> Wonderful. Works a treat, thank you.

For anyone wishing to follow the instructions, you should know that in the editing step following
```
gksu gedit /usr/lib/grub/grub-mkconfig_lib
```
You need to delete several lines, beginning "IF" before the mention of the floppy, and ending "FI".

Best regards.

Thanks to meierfra's sourceforge page I found out that some people need to remove more than just the --no-floppy phrase. The web page recommends commenting out the last 3 lines of that file by placing # in front of each line. Here is the [link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search") to that page.

Glad you got it working, enjoy ubuntu

---

