---
title: "Multisync and SynCE core dumps with WM5"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by falloutphil on 2007-09-19
Hi,

After a bit of mucking around I've got Synce/Raki working and can browse, install on, etc,  my WM5 mobile via USB on Kubuntu.  Which is great.

Spurred on by my success, I decided to try to Sync my WM5 calendar, contacts, etc with Evolution.

Now I've hit a brick wall :-(

I used the ubuntu repository version of Multisync (some other things were compiled separately to get SVN versions as required for WM5 - synce, rra, vdccm, odccm, synce-multisync-plugin and so on - they are all working as expected).  I'm pretty sure I haven't made some numpty error by mixing repository libraries with source I've compiled myself.  Installation went fairly smoothly - no errors.

I can find a few other people with the same issue on google - but no resolution or feedback.

Can anyone confirm that this is actually a known bug and I'm wasting my time trying to sync using this method (there are other suggestions on how to do this but they're a bit of saga!) OR that they have managed to sync their WM5 successfully by installing synce, raki, and then multisync and have some tips on how to do this?

The below output shows Multisync loading - the crash only occurs when click the "Sync" button to sync my WM5 device with Evolution.

Some quick info about my system - no surprises here:
$uname -a
Linux my-computer 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
$ more /etc/issue
Ubuntu 7.04 \n \l

Cheers,

Phil.

plugin_API_version
short_name
long_name
plugin_init
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/phil/.multisync/4/localsettings
[evo2-sync] DEBUG: end: load_palm_state

[evo2-sync] DEBUG: end: sync_connect

** (multisync:27670): WARNING **: Failed to get devices: The name org.synce.odccm was not provided by any .service files
[synce_subscribe:176] Synchronization of 'Appointment' events is not supported
[synce_subscribe:176] Synchronization of 'Contact' events is not supported
[synce_subscribe:176] Synchronization of 'Task' events is not supported
[rra_syncmgr_start_events:655] No valid subscriptions
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found

(multisync:27670): GLib-CRITICAL **: g_hash_table_size: assertion `hash_table != NULL' failed
Segmentation fault (core dumped)

---

