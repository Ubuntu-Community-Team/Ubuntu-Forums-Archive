---
title: "Error during grub-repair"
date: 2015-11-21
forum: Installation &amp; Upgrades
---

### Post by byc013 on 2015-11-21
Hello,

I had a DELL laptop with ubuntu 12.04 installed on it. Then I have installed Win7 on a separate partition in a hope to end up with a dual boot machine.
However, the win7 installer has overridden my MBR and thus boot was launching win7 unconditionally (no grub menu...)

So, I used ubuntu 12.04 DVD to try some recovery methods.
I tried 'boot-repair' app, but it has encountered an error during repair. Here is my boot info (pastebin):
[http://paste.ubuntu.com/13418176/](http://paste.ubuntu.com/13418176/)

Any ideas?

---

### Post by oldfred on 2015-11-21
You are showing 12.10 not 12.04.
       End of life:  (May 16, 2014), Ubuntu 12.10 is no longer supported.
    
So you cannot download fixes for 12.10 anymore.

Best just to install 14.04LTS as it is long term support.
Back up all your data. If you installed lots of apps backup a list to make it easy to reinstall them. If you made system wide changes you may want to backup /etc, but do not just copy those back as it may not be compatible. 

Best also to use Something Else so you can just choose your existing / (root) for new install.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

            Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

