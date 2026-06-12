---
title: "Ubuntu and vista"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by SJHthomas on 2011-02-02
I just installed Ubuntu alongside windows vista and now cannot reboot windows

---

### Post by Quackers on 2011-02-02
Welcome to UF.
We'll need a bit more info than that to help you :-)
Which version of Ubuntu?
Have you run sudo update-grub in a terminal?
Alternatively, please tions > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by SJHthomas on 2011-02-03
I installed the most recent version of Ubuntu 10.10, but fear I have completely deleted my windows vista. I was installing Ubuntu to start learning about it, but now regret this move and think I should go back to windows. I can then install Ubuntu within windows and learn a bit more about it that way.
How should I go about this.
Tom

---

### Post by kansasnoob on 2011-02-03
Please at least post the output of this command from terminal:

```
sudo parted -l
```

I've worked very hard to get this bug fixed and it's now in the Release Notes:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

> In dual boot installs, side-by-side partitioning can be overridden by the user, resulting in data loss. After selecting the "Install alongside other operating systems" option, clicking on either the "Use entire partition" of "Use entire disc" buttons will override the side-by-side partitioning and result in a loss of data.

Before using Wubi to install Ubuntu also look here:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

You can create a true dual-boot just look here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

And here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

I'm sorry you had a bad experience.

---

