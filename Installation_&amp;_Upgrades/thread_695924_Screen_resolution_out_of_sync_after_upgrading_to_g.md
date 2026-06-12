---
title: "Screen resolution out of sync after upgrading to gutsy"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by ubuntosh on 2008-02-13
Hello there 

I can't access my desktop, the GUI is not displayed properly after an upgrade from feisty to gutsy. At the moment I'm using the live CD for feisty, I already accessed my xorg.conf script and found the display resolution is 1600 x 1400, but I'm not allowed to modify it, that I'm not the owner, and it is not possible to configure it using the kernel recovery mode with sudo gedit etc, tried nano but nothing is displayed for me to change.

Apart from the latter, I thought it was the new kernel giving me trouble, so I unistalled it, leaving the just the previous one.

fortunately, there is a partition where all my data is stored but I just need to move a single folder to this partition, which contains important job documents, 

So, how can I repair this? or, if there's no chance, how can I get the owner permissions using terminal from the live cd to move my important data to the other partition?
:confused:
Any help would be appreciated.

---

### Post by taurus on 2008-02-13
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

