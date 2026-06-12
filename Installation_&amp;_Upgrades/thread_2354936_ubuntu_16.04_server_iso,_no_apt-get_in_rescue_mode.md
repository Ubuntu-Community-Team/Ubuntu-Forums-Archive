---
title: "ubuntu 16.04 server iso, no apt-get in rescue mode"
date: 2017-03-07
forum: Installation &amp; Upgrades
---

### Post by imraven52 on 2017-03-07
Sorry for my ignorance.

When I boot up a desktop iso I get the full environment and have apt-get to install secondary packages in the temporary environment to allow me to do custom installs.  Is there a way to do that with the server ISO?

When I boot into rescue mode and finally execute a shell it seems pretty limited.  I see the packages inside of the pool dir but I'm not sure how to install them w/o the dpkg command.

Thanks in advance.

raVen

---

### Post by papibe on 2017-03-07
Hi imraven52.

I haven't heard of live 'server' ISOs. Most of the concerns for a live media is to resolve problems, so it is easier to work on GUI with multiple terminals, and applications like gparted, boot-repair, etc.

As far as I know, the 'shell' in the server installer is not a live version. It is more like busybox or alike. 

As an alternative, you could boot into the desktop, and then jump into a console (Crtl+F1) and then kill the GUI, thus having a text-only environment.

You could also create your own live 'server' media by installing the proper server (or [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD")) into an USB, DVD or external hard drive. When you boot into it,instead of an installer, you boot into a running server.

Just my thoughts. Hope it helps.
Regards.

---

