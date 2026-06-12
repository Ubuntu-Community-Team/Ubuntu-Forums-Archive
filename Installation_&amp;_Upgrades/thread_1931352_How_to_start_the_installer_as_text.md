---
title: "How to start the installer as text"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by jamapii on 2012-02-25
Hi,

I'm trying to install the 64bit 11.10 CD on Windows (virtual).

There seems to be an oops in booting, but it works, only without X11.

No installer is started.

So the boot messages pointed me to help.ubuntu.com, and this talked about debian-installer. There is no debian-installer. I found ubuntuone-installer, and continued with that doc anyway.

The ubuntuone-installer doesn't start, the error message talks about gtk any python.

The doc talks about boot parameters, but there is no way to supply them (except for modifying the iso file), as it boots directly without any menu.

So I tried the commands:

DEBIAN_FRONTEND=text sudo -E ubuntuone-installer DEBIAN_FRONTEND=text

and to be sure, retried without the "sudo -E".

Same error, the parameter is ignored.

So, how can I start the installer? Is there any uptodate documentation? Is there any way to search for this? I understand that any search will yield relevant results only behind lots of casino ads, Brazil news and cat videos, due to the generic nature of any relevant search terms ;)

---

### Post by jacob.david on 2012-02-25
Could you explain how you are trying to install it? From your mail it looks like you have Windows as host OS and trying to install ubuntu as a guest in a vm. Is this the case? Which vm are you using?
If you are using vmware then there is some option (not 100% sure as I'm away from my main pc) in which you have to choose the image from which you can start your installation. Choose that option and point to your CD.
You can also try Wubi ([https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi))

---

### Post by jamapii on 2012-02-25
That's right, I'm installing a guest in a Windows host.

By simply booting the CD. X11 doesn't start, so no installer.

It seems that the ubuntuone-installer is not the ubuntu installer. So back 1 square, forget that part --->

how can I start the installer in text mode, no X, no framebuffer?

---

### Post by jamapii on 2012-02-25
I can connect to a remote X server, so the forum title is obsolete.

Now the problem is, how to start it at all, what is the command line?

I start a new topic as the title is not editable.

---

