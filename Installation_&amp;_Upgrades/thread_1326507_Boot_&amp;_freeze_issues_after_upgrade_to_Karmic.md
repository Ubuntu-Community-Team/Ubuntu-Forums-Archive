---
title: "Boot &amp; freeze issues after upgrade to Karmic"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by SuaSwe on 2009-11-14
Hi all!

Decided to upgrade to Karmic a few hours ago and have since been made to regret it.

Booting to the default kernel, it got to this point:


     Boot from (hd0,0) ext 3 <alphanumeric string>
     Starting up...


... then just sat there. I hard-rebooted and tried the second kernel, which flashed up the Jaunty Ubuntu splash then the Karmic one, then came to the login prompt. I tried to click on my username to log in but nothing happened, so - incorrectly assuming that it had frozen - I tried the third and last kernel, which behaved the same as the second.

Following this, I booted into my Intrepid LiveCD to get some tips, and have so far attempted the following in the recovery CLI environment, working with the second kernel:

- startx (screen just goes black)
- checked /etc/X11/xorg.conf (no vendor- or model-specific options)
- dpkg-reconfigure -phigh xserver-xorg (no changes to xorg.conf, but again, it already appears to contain only default settings as it is)
- aptitude install xserver-xorg-video-ati (comes back with "0 to install, 0 to upgrade" etc, so not useful)

After all this, I retried the second kernel and discovered that the keyboard actually works. Signed in and it loaded up with my regular graphical configs and files. I did not have time to do anything with it, however, as the screen went black before suddenly being covered with flickering multi-coloured stripes and pixels. Black into the LiveCD:

- disabled quiet splash in menu.lst (tried to do this to start with but discovered by chance that I'd done it improperly)

Upon reboot, I found that the first kernel, which had previously not booted at all, actually went all the way to the graphical environment, where I was able to sign in and even work with it for a moment. Unfortunately it froze up as soon as I attempted to do something with it (install additional language support, in this case); I had to hard-reboot again, and this time it halted during the reboot process. Tried the second and third kernels, and the mousepad still does not work on either. Rebooted into the first kernel once again, and it once again booted up fine (albeit very slowly), but as soon as I attempted to use Firefox the session froze.

I'm guessing that this problem is related to my graphics, and I am aware of the known and noted issues with ATI drivers and Karmic (I only wish I'd thought to read around a little *before* upgrading!). 'lspci | grep VGA' gives: 

```

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

```

Any ideas on what I might be able to do to regain functionality?

Thanks a bunch!

---

### Post by SuaSwe on 2009-11-14
Thanks to anyone considering helping me with this one - I'm afraid I have thrown in the towel after trying and failing to find a solution for the problem that didn't involve coding new ATI drivers myself. :D Maybe it's easiest to just stay with Jaunty for now (although the Ubuntu gods have already punished me for this indolence by eradicating my Firefox bookmarks during the downgrade - you live, you learn!).

---

### Post by wjgore on 2009-11-15
I had the exact same problem with Karmic, and I also assumed it was just an issue with the nvidia driver I was using.
I booted into the recovery mode and couldn't accomplish anything there. I opted to go to a command prompt. I put in *startx *and it started up the gui just fine. I haven't tried to reboot or change anything until I understand what the problem is.  What do you think?

---

