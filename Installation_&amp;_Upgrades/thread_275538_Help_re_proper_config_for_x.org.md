---
title: "Help re: proper config for x.org"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by driggins on 2006-10-11
Greetings,

I am a Linux newbie, installing Ubuntu Server (Dapper Drake) as a replacement to Win 2K server. My goal is to have this machine operate as a file server to my Win XP clients. I'm interested in exploring the other possibilities once I establish a stable file share.

My command line Linux skills are very old, stemming from my college experience. You will need to provide explicit command line info if you can help me.

Since I plan to rely on a GUI for interacting with Ubuntu Server, installing one was at the top of my list. (This is something I wish Ubuntu would have included in their server distribution.) I did the following:
sudo apt-get update
sudo apt-get install ubuntu-desktop

This worked fine, although the install failed on a few files near the end. I attempted the install again and it appeared to "take".

When rebooting, I experienced the same video problem I encountered when trying to install Xandros server. The GUI attempts to load, fails, and dumps a lot of text to the screen. Some of the salient points appear to be:
"You passed an undefined mode number."
"Fatal server error:
no screens found"

I have been through dpkg-reconfigure xserver-xorg. During this process, I noted that the autodetection of my monitor yields some Elographics model. My monitor is a Dell Trinitron D1025HT. I also selected more video resolution modes during this process in an effort to give x.org more options. No dice.

I'm installing to an IBM NetVista 8311-XX7. All of the hardware is as installed by IBM (I am not using any add-on cards). Should be cake, right?

If I need to edit a configuration file, please tell me how. Since I do not have a GUI, I'm at a loss here.

Any thoughts?

---

### Post by whizbaby on 2006-10-11
You could post your /etc/xorg.conf (put on usbstick or so and post from where you currently are).

Why ubuntu server comes without GUI is simple: it's a very bad idea to run X on a server. You are adding security holes and the option of an X-crash as taking away processor time from more important services.

---

