---
title: "Can't uncheck proposed or usupported boxes in Kubuntu updates sorftware sources"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by megamasha on 2011-08-01
In KPackageKit I can't uncheck the 'Proposed updates' or the 'Unsupported  updates' boxes in the 'Kubuntu updates' section of the 'Updates' tab of  the 'Software Sources' window (brought up by clicking on the 'Edit  Origins' button in the 'Settings' tab of 'KPackageKit').

I've found a similar thread in the General help forum ([http://ubuntuforums.org/showthread.php?t=1788688](http://ubuntuforums.org/showthread.php?t=1788688)), but thought this would be a better place to post.

Can anyone shed some light on this?

64-bit Kubuntu 11.04 if that helps...

MM

---

### Post by ankspo71 on 2011-08-01
Hi,
It's not happening to me but it is likely to be a bug in software-properties-kde. An alternative to software-properties-kde is software-properties-gtk. software-properties-gtk is the same application but it is created with a GTK interface for use in other types of desktops.

If you don't already have software-properties-gtk installed you can install it with the following command:
```
sudo apt-get install software-properties-gtk
```

You can then run it with this command:
```
kdesudo software-properties-gtk
```

If you would like to report this as a bug to the Ubuntu developers, you can do so by pasting this into the terminal:
```
ubuntu-bug software-properties-kde
```

More info on Ubuntu bug reporting:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Kde specific bugs can be reported here:
[https://bugs.kde.org/](https://bugs.kde.org/)

---

### Post by megamasha on 2011-08-02
I installed the gtk version and was able to uncheck the boxes. I could subsequently remove the package. As I wasn't using any other gnome software, a lot of gnome packages were installed with it, which weren't automatically removed afterwards, so I removed them using ```
sudo apt-get autoremove
```

This is a workaround, not a solution, and bugs have been reported appropriately.

Thread marked as solved

MM

---

