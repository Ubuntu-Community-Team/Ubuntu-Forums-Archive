---
title: "Ubuntu Server + GUI = Ubuntu Desktop?"
date: 2021-03-30
forum: Installation &amp; Upgrades
---

### Post by james_n2 on 2021-03-30
Hello everyone, 
I am newbie here!
I have installed the headless Ubuntu Server version 18.04.
Recently, I come arcross an article that said, we can install the GUI for the Server by
apt-get install ubuntu-desktop
I did it, and in fact, after the completing the installation, the Server boot straight to the Desktop interface of the Ubuntu instead of showing the regular command line and prompt
I run "lsb_release -a" to check the version but unfortunately, the result does not tell if the version is Server or Desktop
Could someone please confirm if the Server + GUI install = Desktop? If it's what's the difference between Server and Desktop, apart from just the GUI?
Thank you very much

---

### Post by The Cog on 2021-03-31
I'm not sure, but possibly the server has slightly difference scheduling settings, prioritising overall throughput rather than a responsive GUI. 
Apart from that, I don't think there are any other differences.

---

### Post by CatKiller on 2021-03-31
The desktop installs get put on HWE by default where appropriate for the hardware, and I *think* the server installs don't?

But yeah, it's all the same software from the same repositories. You can add or remove whatever you want.

---

### Post by SeijiSensei on 2021-03-31
I believe the server version includes some packages by default that are not in the desktop version. Things like the Apache web server or the Postfix mail exchanger that are commonly run on servers.

---

### Post by TheFu on 2021-03-31
System management generally follows the server method, not the desktop.  That means wifi and LAN management is through netplan yaml files, not a GUI.  Lots of other little things like that wouldn't be integrated.

For most people, it is best to install the desktop version you want, then add server packages as needed.
For server people, some of us prefer config file management, not GUIs, for our networking, firewalls, package management and storage. Personal choice. My devOps tools are setup to work with servers, so not having network-manager-anything is a bonus to me. I never, ever, want network-manager or nm-* on my systems. NEVER.  Or nano.  Or gedit or leafpad or whatever other editor some DE team thinks we need. ;)

---

### Post by deadflowr on 2021-03-31
It's all just Ubuntu.
The difference being the server is a near blank slate that you can setup however you like.
and the desktop is packed with common apps most desktop users would use, like browsers and music players and email clients and so on.

As to whether it can be considered a server or a desktop, all depends on how you use it.
Services required for either can be disabled, so you can run it as a headless server or run it as a normal desktop.
Choice is yours.

My concern is who, outside of the Ubuntu developers themselves, would ever recommend the ubuntu-desktop as the gui?
Most users running servers would want a lighter desktop, if any.

---

### Post by ActionParsnip on 2021-03-31
Yes, its the same. There used to be a server kernel and a desktop kernel, now its just one kernel.

---

### Post by rsteinmetz70112 on 2021-04-01
One this I'd mention here based on the title is that the standard Ubuntu Desktop includes a bunch of default applications you would use on a workstation things like Libre Office, Firefox, Thunderbird and many others. If you install only a GUI like Gnome then those applications will not be installed but you can add those you want. You can also install the whole Ubuntu Desktop by installing the Ubuntu Desktop meta package. As a new user I'd recommend not getting too creative to start with.

I'm one of those people who generally installs the Ubuntu Desktop on my servers because I occasionally need to use the servers for other things.

---

