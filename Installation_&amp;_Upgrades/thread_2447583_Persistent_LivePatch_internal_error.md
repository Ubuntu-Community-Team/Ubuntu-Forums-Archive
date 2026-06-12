---
title: "Persistent LivePatch internal error"
date: 2020-07-21
forum: Installation &amp; Upgrades
---

### Post by yehudahecht on 2020-07-21
[COLOR=#242729][FONT=Arial][FONT=inherit]I'm using Ubuntu 20.04. LivePatch informs me:

[/FONT][/FONT][/COLOR]> [COLOR=#242729][FONT=Arial]Canonical Livepatch has experienced an internal error. Please refer to [h]("https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues")[tt]("http://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues")[/FONT][/COLOR][ps://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues]("https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues")[COLOR=#242729][FONT=Arial] for further information.[/FONT][/COLOR][COLOR=#242729][FONT=Arial][FONT=inherit][FONT=inherit]

[/FONT][FONT=inherit]As per instructions I found [/FONT][here]("https://askubuntu.com/questions/1142602/canonical-livepatch-internal-error")[FONT=inherit], I've disabled and re-enabled LivePatch with a [/FONT][fresh auth]("https://auth.livepatch.canonical.com/?user_type=ubuntu-user")[FONT=inherit] from Canonical. Yet the issue persists, and the error message remains. Does anyone know what else might be causing this?[/FONT][/FONT]


[/FONT][/COLOR]

---

### Post by f1-tnolte on 2020-08-28
In my case I was able to resolve the issue by checking the error logs using:
```
journalctl -f -t canonical-livepatch
```
and i found an error message about a lock file:
```
To override this warning, remove /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_5_4_0_42_46_generic_70_70.3
```
I also ran the livepatch refresh manually from the console:
```
sudo canonical-livepatch refresh
```
Once I did all of that I was able to toggle off/on Livepatch from the Settings dialog and everything was working again.

---

