---
title: "Alternate CD &quot;text-based&quot; installer opens a window!?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by dkarnows on 2007-10-25
Greetings,

I'm trying to upgrade from Feisty to Gutsy on a Xubuntu machine. My first attempt failed when the machine lost power during the upgrade leaving it in a funky state. A lot of GUI applications crash now and get into funky states. i.e. I can't rely on a GUI-based upgrade. So I'm trying the alternate CD which I read is "text-based". But when I run it ("sudo /media/cdrom0/cdromupgrade") it pops up the regular GUI Update Manager window, which I can't use because of the aforementioned funky GUI issues. OK, I thought, maybe it's because I've got "DISPLAY" set. So I unset it and try run it again and I get the following. Is this "text-based" installer not text-based? What do I need to do to ensure that my upgrade is entirely text-based?

$ sudo /media/cdrom0/cdromupgrade
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/tmp/tmp.DmhajQ6714/DistUpgradeViewGtk.py:347: GtkWarning: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  icons = gtk.icon_theme_get_default()
Traceback (most recent call last):
  File "/tmp/tmp.DmhajQ6714/gutsy", line 57, in <module>
    view = view_class(logdir=logdir)
  File "/tmp/tmp.DmhajQ6714/DistUpgradeViewGtk.py", line 349, in __init__
    gtk.window_set_default_icon(icons.load_icon("update-manager", 32, 0))
AttributeError: 'NoneType' object has no attribute 'load_icon'


many thanks,
David

---

### Post by thelocust on 2007-10-25
I think you have to boot from the cd for it to be text based.

---

### Post by Cryptog on 2007-10-26
Yes, you don't "run" it, you boot off of the CD and the installation screens are completely text based. Some options are only available from the alternate installer, like encrypted partitions.

---

### Post by dkarnows on 2007-10-26
> **Cryptog said:**
> Yes, you don't "run" it, you boot off of the CD and the installation screens are completely text based. Some options are only available from the alternate installer, like encrypted partitions.

When I boot straight from the CD I get these options:

Install Text Mode
OEM Install
Install Command line
Check CD
Rescue broken system
Memory test
Boot from first hard drive

i.e. No upgrade option. I did go into the "Install Text Mode" option but when it asked me to enter a (new) hostname I assumed it was not going to give me a chance to upgrade and would just overwrite everything. It shouldn't be asking for a hostname if upgrading was an option, so I aborted.

If you look at this thread: [http://ubuntuforums.org/showthread.php?p=3588743](http://ubuntuforums.org/showthread.php?p=3588743) forestpixie *thinks* you are supposed to launch the CD from the existing running (Feisty) (x)ubuntu installation for upgrades and boot from it for fresh installs.

So who is right? Am I supposed to boot from the alternate CD? And if so how do I start an upgrade rather than a fresh install? If I'm supposed to launch the alternate CD upgrade from within my existing running Feisty installation how do I launch it so that it runs in purely text mode?

---

### Post by Methomania on 2007-12-09
> **dkarnows said:**
> When I boot straight from the CD I get these options:

Install Text Mode
OEM Install
Install Command line
Check CD
Rescue broken system
Memory test
Boot from first hard drive

When I boot from my "text-based" CD it doesn't show.
It starts with a command prompt indicating that the mouse driver has been installed and "A:\>" shows.

?

---

