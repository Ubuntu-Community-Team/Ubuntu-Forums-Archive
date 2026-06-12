---
title: "Server - Which version???"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by jfm30204 on 2008-04-15
I know that options are a good thing, but they are confusing the heck out of me.

Here's what I have:
Old Dell Optiplex PIII 867
512mb memory
10g primary HD
130g slave HD

Here's what I want to do:
Serve up a photo gallery like Coppermine
Have Samba for network file sharing and shunting things back and forth w/o ftp

I am a Linux newbie now running everything under Wamp and would like to move to Ubuntu. Hopefully I will one day be able to run it by command line, but that is not today. I think, therefore, that a GUI will help me with installing pkgs and config options.

1. I want to install a LAMP server. Is this an install option with the desktop version?

2. Should I install the desktop and add the server pkgs or install the server and add the desktop? What would be the difference?

3. Can the desktop overhead be removed down the road?

4. Should I consider a LTS version? Is this important?

Sorry for all of the questions, but, like I said, I'm in a fog and can't see the lighthouse yet. Bite off as little or as much as you want. All suggestions and information appreciated.

Jere

---

### Post by blazercist on 2008-04-15
im not 100% sure but i dont think LAMP is an option on the dekstop install i would recommend installing the server version with LAMP and then just installing the desktop environment ontop of it it should be as simple as typing 

sudo apt-get install ubuntu-desktop

and then rebooting

the desktop environment can be added and removed to your heart's content in either case, its just that as i understand it, LAMP is more easily installed and preconfigured with the server version of the install.

LTS is only important if you are extremely worried about the LONG TERM stability of the system, releases that are not LTS are only really developed up until the next version comes out which is only about 6 months.... that is not to say that they are entirely unsupported but rather all the updates are just backports of things going on in the current version.

personally i dont think it matters because you can always dist-upgrade tot he newest version, and hardy will be comiing out on the 20th and will be an LTS.

---

### Post by jfm30204 on 2008-04-15
> **blazercist said:**
> personally i dont think it matters because you can always dist-upgrade tot he newest version, and hardy will be comiing out on the 20th and will be an LTS.

If Hardy is about to debut out of beta, should I then go ahead and install this version?

Jere

---

### Post by Pumalite on 2008-04-15
Beta might be Beta, but it's a great OS already. Besides, if you keep with the updates, you'll have Final Release by the 24th.

---

### Post by jfm30204 on 2008-04-15
Thought I'd use hardy, but on the initial screen, there is no "Install LAMP server" choice. It just says "Install Ubuntu server". Why is this?

Jere

[edit] I see now that the LAMP option comes later.

---

