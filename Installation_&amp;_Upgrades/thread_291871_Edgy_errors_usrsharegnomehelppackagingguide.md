---
title: "Edgy errors: /usr/share/gnome/help/packagingguide"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by jchau on 2006-11-03
After upgrading to Edgy, I get these errors.  They don't seem critical, but how do I fix them?

Here is the start of it.  The whole thing is gzipped and attached.  Thanks. 

> /etc/cron.monthly/scrollkeeper:
///usr/share/gnome/help/packagingguide/pt_BR/packagingguide.xml:9: I/O warning : failed to load external entity "/usr/share/gnome/help/packagingguide/pg-common.ent"
%pg-common;
           ^
 %pg-common; 
            ^
/usr/share/gnome/help/packagingguide/pt_BR/bookinfo.xml:9: I/O warning : failed to load external entity "/usr/share/gnome/help/packagingguide/pg-common.ent"
%pg-common;
           ^
 %pg-common; 
            ^
/usr/share/gnome/help/packagingguide/pt_BR/introduction.xml:9: I/O warning : failed to load external entity "/usr/share/gnome/help/packagingguide/pg-common.ent"
%pg-common;


---

### Post by racmar on 2006-11-17
I saw the same error this morning after anacron ran cron.monthly.  I tried this:

```

sudo apt-get install scrollkeeper --reinstall

```
After running /etc/cron.monthy/scrollkeeper I see this did not work.  I also tried:

```

sudo apt-get remove scrollkeeper --purge

```
However, it wants to remove too much stuff for me to bother:

> 
The following packages will be REMOVED:
  bug-buddy* capplets-data* doc-base* gedit* gnome-app-install* gnome-applets* gnome-applets-data* gnome-control-center* gnome-gv* gnome-panel* gnome-panel-data*
  gnome-session* gnome-system-monitor* gnome-terminal* gnome-utils* gnome2-user-guide* gthumb* gucharmap* language-selector* nautilus* nautilus-cd-burner* nautilus-data*
  scrollkeeper* synaptic* ubuntu-docs* update-manager* update-notifier* zenity*



So in the end, I'll wait for others smarter than me to fix it.  I don't think it's causing much trouble, because the system is working fine as far as I can tell.

-Rob

---

### Post by hirschler on 2006-12-10
i did a search, and the files which scrollkeeper responses with errors belong to ubuntu-docs. i uninstalled ubuntu-docs, then i checked it with:

sudo scrollkeeper-rebuilddb

no error output from scrollkeeper.

---

### Post by mattheweast on 2007-01-03
It's a bug in ubuntu-docs. We have fixed it in our repository but have not had any feedback from the developers about whether it is appropriate to upload it. For now, please ignore these errors.

---

