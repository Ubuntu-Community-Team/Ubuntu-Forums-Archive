---
title: "Software Updater window - no file to update and 40kB to download"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by daniroma on 2013-08-28
Hello!

Could anyone explain what is wrong with Sofware Updater since shows no files to update and 40kB to download??
Thank you!

[ATTACH=CONFIG]245792[/ATTACH]

Xubuntu 13.04

---

### Post by ibjsb4 on 2013-08-29
I have seen a couple of other post on this, seems to be a bug.  Maybe just update in terminal or use synaptic for now.

---

### Post by kimble2 on 2013-08-29
I have the same thing with Lubuntu 13.04. apt-get update from the terminal shows nothing needs updating.

When I got one of these last week, and after much consideration clicked on "install now", something trashed my Master Boot Record. It would be quicker to go through that again than struggle to understand why it happens.

I've lost confidence in Ubuntu.

---

### Post by kimble2 on 2013-08-30
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1211511](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1211511)

correction to post #3 above: sudo apt-get upgrade shows libgksu2-0 needed upgrading with libgksu2-0 2.0.13~pre1-6ubuntu2 which installed OK.

---

### Post by daniroma on 2013-08-30
Kimble2 you are right.
libgksu2-0 needed upgrading. Installed via synaptic since Sofware Updater is no longer reliable.

Thank you all for answers.

This thread should be closed.

---

