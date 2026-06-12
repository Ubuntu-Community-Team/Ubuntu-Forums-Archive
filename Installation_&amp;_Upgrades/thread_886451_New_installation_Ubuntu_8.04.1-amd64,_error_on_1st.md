---
title: "New installation Ubuntu 8.04.1-amd64, error on 1st. reboot."
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by Trimax on 2008-08-11
After I installed Ubuntu 8.04.1-amd64 I restarted the system for firt time, then I reached the GUI login of Gnome, but when I login a window alert on upper left corner advised this error: 

```
"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

```


file syslog:

```
Aug 10 14:08:29 jupiter2 anacron[5700]: Anacron 2.3 started on 2008-08-10
Aug 10 14:08:30 jupiter2 anacron[5700]: Normal exit (0 jobs run)
Aug 10 14:08:30 jupiter2 /usr/sbin/cron[5727]: (CRON) INFO (pidfile fd = 3)
Aug 10 14:08:30 jupiter2 /usr/sbin/cron[5728]: (CRON) STARTUP (fork ok)
Aug 10 14:08:30 jupiter2 /usr/sbin/cron[5728]: (CRON) INFO (Running @reboot jobs)
Aug 10 14:08:34 jupiter2 gdmgreeter[5816]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Aug 10 14:08:34 jupiter2 gdmgreeter[5816]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Aug 10 14:08:34 jupiter2 gdmgreeter[5816]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Aug 10 14:08:34 jupiter2 gdmgreeter[5816]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Aug 10 14:08:45 jupiter2 gdm[5668]: WARNING: No se pudo autenticar al usuario 
Aug 10 14:08:57 jupiter2 kernel: [   59.394958] NET: Registered protocol family 10
Aug 10 14:11:28 jupiter2 init: tty4 main process (4949) killed by TERM signal
Aug 10 14:11:28 jupiter2 init: tty5 main process (4950) killed by TERM signal
Aug 10 14:11:28 jupiter2 init: tty2 main process (4952) killed by TERM signal
Aug 10 14:11:28 jupiter2 init: tty3 main process (4955) killed by TERM signal
Aug 10 14:11:28 jupiter2 init: tty6 main process (4956) killed by TERM signal
Aug 10 14:11:28 jupiter2 init: tty1 main process (5808) killed by TERM signal
Aug 10 14:11:30 jupiter2 kernel: [  110.570858] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 10 14:11:31 jupiter2 exiting on signal 15


```

I dont have modified any setting of the default settings after I installed.

---

