---
title: "Screenlets Manager crashes on Ubuntu Karmic Koala"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nazty on 2009-10-11
Hi there!


 I am getting the following error when I try starting the Screenlets Manager. I have tried reinstalling it but it still keeps crashing on my Ubuntu Karmic Koala.


> nexus@versus:~$ screenlets-manager 
/home/nexus/.themes/Oversword Dark V4.5/gtk-2.0/panel.rc:66: Unable to locate image file in pixmap_path: "/arrows/arrow-up-panel.png"
/home/nexus/.themes/Oversword Dark V4.5/gtk-2.0/panel.rc:70: Overlay image options specified without filename

** (screenlets-manager.py:11640): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (screenlets-manager.py:11640): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (screenlets-manager.py:11640): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'
/usr/share/screenlets-manager/screenlets-manager.py:93: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips = gtk.Tooltips()
/usr/share/screenlets-manager/screenlets-manager.py:414: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but1, _('Launch/add a new instance of the selected Screenlet ...'))
/usr/share/screenlets-manager/screenlets-manager.py:415: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but2, _('Install a new Screenlet, SuperKaramba or Web Widget or Web Application  ...'))
/usr/share/screenlets-manager/screenlets-manager.py:416: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but3, _('Permanently uninstall/delete the currently selected Screenlet ...'))
/usr/share/screenlets-manager/screenlets-manager.py:417: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but4, _('Reset this Screenlet configuration (will only work if screenlet isnt running)'))
/usr/share/screenlets-manager/screenlets-manager.py:418: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but5, _('Install new theme for this screenlet'))
/usr/share/screenlets-manager/screenlets-manager.py:419: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but6, _('Restart all screenlets that have auto start at login'))
/usr/share/screenlets-manager/screenlets-manager.py:420: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but7, _('Close all Screenlets running'))
/usr/share/screenlets-manager/screenlets-manager.py:421: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but8, _('New Screenlets Options/Properties'))
/usr/share/screenlets-manager/screenlets-manager.py:422: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but9, _('Create a Desktop shortcut for this Screenlet'))
/usr/share/screenlets-manager/screenlets-manager.py:477: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_about, _('Show info about this dialog ...'))
/usr/share/screenlets-manager/screenlets-manager.py:478: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_download, _('Download more screenlets ...'))
/usr/share/screenlets-manager/screenlets-manager.py:479: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_close, _('Close this dialog ...'))
True
Starter already exists.
DAEMON FOUND!

GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
Aborted
nexus@versus:~$ 



Any help is much appreciated...

---

