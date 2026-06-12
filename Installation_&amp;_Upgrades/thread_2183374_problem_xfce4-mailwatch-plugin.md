---
title: "problem xfce4-mailwatch-plugin"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by injaon on 2013-10-24
Hello community!
I've a little problem with my fresh installed xubuntu   13.10. It comes with the package "xfce4-mailwatch-plugin" installed  and i want to use it. The problem is that the only binary to execute is  located here:

/usr/lib/x86_64-linux-gnu/xfce4/panel-plugins/xfce4-mailwatch-plugin
and it doesn't work. This is its output

** (process:4166): CRITICAL **: Not enough arguments are passed to the plugin

btw, it is NOT in my $PATH variable.
So, how can I run it?
Thanks!
Gabriel Lopez

---

### Post by Toz on 2013-10-24
Hello and welcome to the forums.

You're not intended to run that executable. To use this panel plugin, right-click the panel and select Panel->Panel Preference, go to the Items Tab, click on the "Add new item to this panel" button and locate and add the "Mail Watcher" plugin. You can configure it by clicking on the "Edit the currently selected item" in the same window or by right-clicking the panel plugin directly.

---

