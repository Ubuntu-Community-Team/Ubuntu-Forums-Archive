---
title: "can not get computer to start after upgrade"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by paulravin on 2012-11-07
Hi,

I have been using ubuntu 9ish for some time now and love it! But now trouble has struck...

I was getting trouble with ubuntu freezing up so I thought an upgrade may fix it..

I started the upgrade to 10.4, on the 3rd attempt it seemed to go through the motions up until the restart part. On restart it comes up with a message 

Filesystem check or mount failed
A mantanance shell will now be started.
Control D will termenate this shell and continue re booting after re-typing filesystems. Any further errors will be ignored.

So control D does nothing, windows (duel boot) will start on the same computer so it works but ubuntu will not.

Any ideas? Re format and re install or can it be salvaged.

Any help much!!!!! Appreciated.

                                  -PAUL-

---

### Post by UltimateCat on 2012-11-07
Hi:

I'm not the expert on computers that freeze or won't boot but I have a few ideas.

You said Windows will start but Ubuntu won't-
If when your computer starts at boot and you don't have the option to use the arrows keys to choose which OS you want to mount than Grub is gone.

You would have to re-install Grub2 
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

If you don't want to do that than yes; Re-install Ubuntu.

```
I started the upgrade to 10.4

```

Why? I don't think Ubuntu 10.04 is supported anymore-

Here's the ISO image of Ubuntu 12.10
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Hope this helps

---

### Post by black veils on 2012-11-07
before you do anything (especially a reinstall), backup your data! from both Windows and Ubuntu.

do this by booting a live cd/dvd/usb, open file manager, access the systems via the drives in the left pane, then copy-paste your files to another usb stick/upload to online storage like dropbox.

you will also probably want some application settings, like your web browser, messenger and email, get those by pressing Ctrl + H in the file manager, in the home/user directory. find the folders you want, they may not be immediately visible, but instead in the .config/.kde folder etc. copy-paste to the back-up location.

---

### Post by paulravin on 2012-11-07
Hi,

Thanks for such a quick reply! When I start the computer I can choose between Ubuntu or windows. Windows will start but ubuntu gets the error message so grub seems to be intact.

Great to know that files are accessible using the live CD, I did not know that. I don't use windows so all should be recoverable. 

Any idea how to fix the problem?

                                                    -PAUL-

---

