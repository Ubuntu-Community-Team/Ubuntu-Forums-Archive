---
title: "windows host feisty guest install"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by yanqui on 2007-10-23
Man, I need help on this.  Every installation guide assumes you sort of know what you're doing, and I don't.

I have a Windows XP machine, and I"m GOING TO KEEP IT!  I had Dapper installed on a removable USB hard drive, tried to put Feisty on that drive, had problems, decided to try MS Virtual PC to host Feisty, just plain don't work!  So now I have VMWare, and I have a virtual machine created, but I don't know how to answer the questions so that I can keep my windows machine confidently.  I'm afraid that I'll answer a question wrong and overwrite my windows machine.  Is there a tutorial that addresses this step by step, rather than saying, "install it" and thinking that we really know what we're doing?

Please?

---

### Post by ddrichardson on 2007-10-23
VMWare will not overwrite Windows. It creates a disk file that when you install Ubuntu will recognise as /dev/sda1. Even if something goes wrong Windows will not be overwritten.

---

### Post by yanqui on 2007-10-23
Actually, I found a great video clip of what I needed:

[http://www.pcmech.com/article/running_ubuntu_linux_in_windows_xp_vmware/](http://www.pcmech.com/article/running_ubuntu_linux_in_windows_xp_vmware/)

YAY--I'm on the way.

---

