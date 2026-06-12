---
title: "How to install Ubuntu running under Windows Server 2019"
date: 2019-06-15
forum: Installation &amp; Upgrades
---

### Post by lalevin on 2019-06-15
Sorry if this is terribly basic...

I started the Windows Server 2019 environment for Linux.
I then downloaded Ubuntu 18.04 LTS Desktop.
I mounted the iso file, and there are plenty of files there. But no .exe file to actually install Ubuntu.

Is something missing? I thought that I'd be able to set up Ubuntu to run as an application under Windows Server 2019.

Thanks!

---

### Post by Mark Phelps on 2019-06-15
Windows Subsystem for Linux (WSL) is a Microsoft app -- I believe you have to install it from the MS store.

---

### Post by QIII on 2019-06-15
As above, you do not install your Linux distro via a downloaded .iso (which is what you have downloaded, not an .exe), but rather through the Windows App Store.

Bear in mind that WSL does not allow you to run a GUI (desktop) session of your Linux distro.  It is *command line only* -- text based.

If you want to install Linux, I would recommend first using it in a virtualized environment such as VirtualBox.  That will give you some time to learn.  If you keep snapshots, you can revert to one if you mess up.  Just don't keep any important files there.

When you are confident, you can try dual-booting or another arrangement.

---

### Post by lalevin on 2019-06-15
Thanks to both of you for the advice to install it through the Windows App Store - that makes sense.

No problem with running it via command line - I only need Linux to run a specific program that only runs under Linux.

---

### Post by oldos2er on 2019-06-16
If your question has been answered to your satisfaction, please mark your thread 'Solved' under Thread Tools at the top of the page. This helps others with the same question to find an answer. Thanks.

---

