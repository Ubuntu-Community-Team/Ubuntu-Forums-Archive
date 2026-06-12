---
title: "'vesa' drivers not working - X server"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by phoenix96 on 2007-09-02
I'm still trying to dual install ubuntu with vista. 

Every time I try to boot the live CD it gives me the "failure to start x server" error.

I have an Inspiron 6400 with a x1400 ati graphics card. I changed the drivers to 'vesa' and then just pressed enter for the rest of the options - it then just spits me back out at the terminal.

What can I do?

---

### Post by Pumalite on 2007-09-02
[http://ubuntuforums.org/showthread.php?t=221320&highlight=ATI+x1400](http://ubuntuforums.org/showthread.php?t=221320&highlight=ATI+x1400)

---

### Post by phoenix96 on 2007-09-02
Doesn't help me since I can't even get it installed and therefore can't download or change any configuration files.

---

### Post by phoenix96 on 2007-09-02
Would I work if I tried Edgy?

Please guys - I'm gonna flip if I have to use thiis shitty *** OS (windows Vista) any longer :).

---

### Post by confused57 on 2007-09-02
Try the x86 version, if you're currently trying to install the 64-bit:

[http://doubleclix.wordpress.com/2006/11/29/ubuntu-on-dell-e1505-core-duo-2ati-x1400-part-i-of-many/](http://doubleclix.wordpress.com/2006/11/29/ubuntu-on-dell-e1505-core-duo-2ati-x1400-part-i-of-many/)

---

### Post by phoenix96 on 2007-09-02
> **confused57 said:**
> Try the x86 version, if you're currently trying to install the 64-bit:

[http://doubleclix.wordpress.com/2006/11/29/ubuntu-on-dell-e1505-core-duo-2ati-x1400-part-i-of-many/](http://doubleclix.wordpress.com/2006/11/29/ubuntu-on-dell-e1505-core-duo-2ati-x1400-part-i-of-many/)

Thank you very much, but is he talking about this version:

Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM

Because that's the one I'm using and the only option is Sun UltraSPARC or 64bit - both of which don't apply. I am not currently trying to install the 64 bit version.

---

### Post by phoenix96 on 2007-09-02
Okay, I'm going to try the alternate CD.

Hang in there guys - I really appreciate this :)

---

### Post by phoenix96 on 2007-09-02
Okay, I am now as far as getting the installation done.

Yet still, I set it to 'vesa' and it doesn't work.

---

### Post by Pumalite on 2007-09-02
Try another distro and see if you are incompatible with Linux or Ubuntu only.

---

### Post by confused57 on 2007-09-02
> **phoenix96 said:**
> Okay, I am now as far as getting the installation done.

Yet still, I set it to 'vesa' and it doesn't work.

Maybe something in this reply will help:
[http://ubuntuforums.org/showpost.php?p=2515869&postcount=7](http://ubuntuforums.org/showpost.php?p=2515869&postcount=7)

If you can boot into recovery mode, you might try color depth 16 in your xorg.conf:
```
cd /etc/X11
cp xorg.conf xorg.conf_backup
nano xorg.conf
```

Near the bottom of the xorg.conf file you'll see "Default Depth 24"...change it to "Default Depth 16".
To save the change: Ctrl+X, y, enter

You could then try pressing "Esc" or enter "reboot", without quotes, at the prompt.

My video cards are all Nvidia, so I can't really help you with your card; but I believe you need to search for installing the fglrx driver for your card.

Added:  You might want to check out this guide for installing the drivers:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

I believe you could do this from the recovery mode, but you'll need to use nano as your file editor...if you can't find anything useful from doing a fglrx forum search, someone else or I may be able to help you do it from recovery mode.

---

