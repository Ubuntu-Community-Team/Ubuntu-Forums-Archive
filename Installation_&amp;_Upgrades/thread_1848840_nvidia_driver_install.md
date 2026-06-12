---
title: "nvidia driver install"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by knarfoe1 on 2011-09-23
Hello,

After installing ubuntu I need to install the nvidia driver 280.13
During install it disables the nouveau driver. And I need to restart.
After that the machine reboots and it hangs at the ubuntu stratup screen with the 5 red dots.
What need I do now?
tnx
frank

---

### Post by vinterkind on 2011-09-23
if the boot process is at its end, you can switch to another console with [<ctrl>]<alt><f2>.

then you could invoke

```

apt-cache search nvidia

sudo apt-get install <whateveryouwant>
```

have fun!

---

### Post by realzippy on 2011-09-23
@vinterkind

Why should this help OP ?


@OP

hello,we need a few more infos,eg:

```
lspci | grep VGA
```

---

### Post by knarfoe1 on 2011-09-23
Hi,
ok, it does not boot at all.Because the nvidia driver disables the nouveau driver this happens.
Is it possible to disable the nouveau driver after installing ubunt but before installing the nvidia driver ? 
tnx
frank

---

### Post by MAFoElffen on 2011-09-23
> **knarfoe1 said:**
> Hi,
ok, it does not boot at all.Because the nvidia driver disables the nouveau driver this happens.
Is it possible to disable the nouveau driver after installing ubunt but before installing the nvidia driver ? 
tnx
frank
Frank, at your reference to a numbering scheme (280.13)... sounds like you are installing the Binary driver downloaded from NVidia, instead of the Ubuntu packaged NVidia Driver packages from the Additional Drivers applet... Correct?

Yes = NVidia drivers and Nouveau drivers cannot run at the same time!!! So during the install of either the Ubuntu NVidia driver packages or the Nvidia binary install runfiles "blacklist" the nouveau files so that doesn't happen.  You would have to boot using a "nomodeset" kernel boot switch to bring up the X-session and your GPU in a VESA mode.

If you are using the NVidia run file to install the binaries from NVidia... be aware that the runfile needs to be started from a TTY Text Console without a GUI running.  Translation- once you get your GUI up > Bring up a terminal session > 
```

sudo service gdm stop

```That will close the GUI and drop you down to a TTY Text console without the GUI.

--OR--> Use the instructions in Post 1 of:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")
To boot directly into a TTY Text console...

If you are leaning towards installing the binaries, refer to post             #[**280**]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280") of my sticky for installation instructions.

If you are undecided on what "style" of installer to use, refer to posts #[**541**]("http://ubuntuforums.org/showpost.php?p=11277239&postcount=541") and              #[**543.  **]("http://ubuntuforums.org/showpost.php?p=11278627&postcount=543")

The easiest and safest way to install drivers for you, if you just want the extra features, but not actually using any additional NVidia ports to their tools, is to boot up in Rescue Mood (or use the "nomodeset" boot option) > Go to Admin > Additional Drivers > Install your driver.

---

### Post by knarfoe1 on 2011-09-24
great thanks.
Ill focus on the "nomodeset" kernel boot switch first.
tnx
frank

---

