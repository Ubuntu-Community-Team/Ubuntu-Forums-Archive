---
title: "Wubi using existing download"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by amanisdude on 2013-03-07
Hi all,

I searched the forums, and can't find if this has been asked for newer versions of Wubi. 

According to the [WubiGuide]("https://wiki.ubuntu.com/WubiGuide#How_do_I_install_Wubi_on_a_machine_with_no_Internet_connection.3F"), you can install Ubuntu by placing the downloaded image file in the same folder as [FONT=courier new]wubi.exe[/FONT] before executing it.

However, when I do this for Ubuntu 12.10, it doesn't work. Even when [FONT=courier new]wubi.exe[/FONT] and the content file are in the same folder, Wubi proceeds to re-download [FONT=courier new]ubuntu-12.10-wubi-amd64.tar.xz[/FONT] before installing it. Is there still a way to install without re-downloading? Or is it not working because I'm using the tarball instead of the ISO?

I got Wubi and the compressed tar file from [http://releases.ubuntu.com/12.10/](http://releases.ubuntu.com/12.10/).

Thanks guys!

-***amanisdude***
____________________

---

### Post by amanisdude on 2013-03-07
Nevermind. I got my answer. It was because I was using the tarball instead of the ISO. :oops:

Nevertheless, I feel that it should work with both the image and the tarball, since that's the one it tries to download.

Anyway, sorry about eating up your time. 

-***amanisdude***
___________________

---

### Post by bcbc on 2013-03-08
You can tell it to use your downloaded diskimage with the --diskimage= option (but it won't find it by default like it does for the ISO).\

See [http://askubuntu.com/a/143478/14916](http://askubuntu.com/a/143478/14916)

---

### Post by amanisdude on 2013-03-25
> **bcbc said:**
> You can tell it to use your downloaded diskimage with the --diskimage= option (but it won't find it by default like it does for the ISO).\

See [http://askubuntu.com/a/143478/14916](http://askubuntu.com/a/143478/14916)

Thanks **bcbc**! I somehow didn't find that post in my Google searches. Thanks for the info! Now this thread is really solved. :D


-***amanisdude***
_______________

---

