---
title: "Failed to remove gparted after installation"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by metafile on 2007-04-24
This is about a clean installation.
First of all, "disk check" said "you`ve got two errors". I`ve reburned the disk, but the errors were still there, so I`ve decided to go ahead and try it anyway (the iso was downloaded from ubuntu website).

The intallation seemed to be successful, but right after all the files were copied, "couldn`t remove gparted" error occured. It said something like
"E: gparted: subprocess post-removal script returned error exit status 139".

I`ve restarted and now every action about synaptic is stopped by the same error.

"sudo apt-get -f install"

led to the following:

(update-desktop-database:13798 ): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gparted (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 gparted
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas how can I get out of this?

---

### Post by metafile on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/106939](https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/106939) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Looks like I`ve found a bug related to this issue.
[https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/106939](https://bugs.launchpad.net/ubuntu/+source/desktop-file-utils/+bug/106939)

---

### Post by zvacet on 2007-04-25
Maybe this can help you.Download version wich you are trying to install with torrent.Point torrent to download in the folder where your iso is.That way torrent will chek your iso and if it is any corrupted files torrent will replace with good one.No need to download all iso.After that burn iso on the slower possible speed.Boot up and chek Cd integrity.It should be O.K.

---

