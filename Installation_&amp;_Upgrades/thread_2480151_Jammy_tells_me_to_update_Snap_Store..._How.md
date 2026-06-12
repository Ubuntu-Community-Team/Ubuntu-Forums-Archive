---
title: "Jammy tells me to update Snap Store... How??"
date: 2022-10-20
forum: Installation &amp; Upgrades
---

### Post by BlueAZ on 2022-10-20
Just fresh-installed Jammy 22.04 with general updates + upgrades on AMD 64-bit system.  Figured out quite a few issues, but not this one:  Every time I start it, there's an icon by the date/time display that drops down to tell me I should update Snap Store.  And I only have a few days left to do it.  It doesn't have a link or any indication of how to do this.  I've tried the Software Store, but I guess that would be too simple ;~]  Also tried in the Terminal and this is what I got:  [SIZE=3][SIZE=4][COLOR=#0000cd]

[/COLOR][/SIZE][/SIZE]blue@blue-buntu:~$ sudo snap-store update
[sudo] password for blue: 
mkdir: cannot create directory '/run/user/0': Permission denied
Warning: Schema “org.gnome.system.locale” has path “/system/locale/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy” has path “/system/proxy/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy.http” has path “/system/proxy/http/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy.https” has path “/system/proxy/https/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy.ftp” has path “/system/proxy/ftp/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy.socks” has path “/system/proxy/socks/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
18:30:59:0839 GLib-GIO g_app_info_get_name: assertion 'G_IS_APP_INFO (appinfo)' failed
Authorization required, but no authorization protocol specified
18:30:59:0858 Gtk cannot open display: :0

I'm at a loss.  It's confusing enough that we now have programs, applications, extensions and snaps.  I'm too old for this!
Thanks for any help!!

---

### Post by grahammechanical on 2022-10-20
> to tell me I should update Snap Store.  And I only have a few days left to do it.

That is not the situation at all. The notification is telling us that the application will update automatically when the count down ends. We are advised not to be using the relevant application at the time.

Up until now when we run Software Updater it will automatically check and update any snap applications that are installed and have updates available. But from now on the update/upgrade of certain applications that are snap packaged is done by the application developers without any user involvement. This applies not only to Ubuntu Software/snap store but also to Firefox and Thunderbird. This will happen from 22.04 onward. It does not happen on 20.04 unless we have choosen too install the snap versions of these applications.

Running commands to update these snap apps is pointless as the developers have not yet released to upgrade code and they won't until that count down has ended.

Regards

---

