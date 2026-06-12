---
title: "Where is Folder for Firefox &amp; Thunderbird?"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2014-09-01
Recently installed UbuntuStudio v14.04 onto an old Dell Precision 390, and wanted to copy over my Mozilla Firefox and Thunderbird folders. 

In my older system, I had Xubuntu installed and those folders were under My Name as .Mozilla and .Thuderbird .... however, that doesn't seem to work under Studio!

Any idea where they are supposed to go?  

Thanks
Rick
1

---

### Post by kansasnoob on 2014-09-01
In standard Ubuntu Trusty they're where expected:

```
lance@lance-desktop:~$ ls -a
.                    .config           .gnome2_private  Music
..                   .dbus             .gphoto          Pictures
.adobe               deja-dup          .gstreamer-0.10  .profile
.apport-ignore.xml   Desktop           .hardinfo        Public
Backups              .dmrc             .hplip           Templates
.bash_history        Documents         .ICEauthority    **[COLOR="#FF0000"].thunderbird[/COLOR]**
.bash_logout         Downloads         .local           Videos
.bashrc              examples.desktop  .macromedia      .Xauthority
brasero-session.log  .gconf            **[COLOR="#FF0000"].mozilla[/COLOR]**         .xsession-errors
.cache               .gksu.lock        .mozilla_BK      .xsession-errors.old
.compiz              .gnome2           .mozilla_OLD

```

Remember they're hidden files. Or maybe Ubuntu Studio is doing something different :???:

---

### Post by Rick St. George on 2014-09-01
OH ... OK, Show Hidden Files ... Now that I see them, the differrence is small M vs Large M for mozzila and T for thunderbird. Deleted new and renamed old. Worked like a charm. Thanks!

---

