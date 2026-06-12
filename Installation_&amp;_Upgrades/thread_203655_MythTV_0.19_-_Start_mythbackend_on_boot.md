---
title: "MythTV 0.19 - Start mythbackend on boot?"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by fxer on 2006-06-25
I've been trying to get mythbackend to start on boot in Dapper, I can start the server manually by issuing "sudo /etc/init.d/mythtv-backend start" from the command line, using the script from [Hyams guide]("http://hyams.webhop.net/mythtv/myth_ubuntu.html"), but the script won't run on boot for some reason, the permissions are the same as every other file in the directory.

Is there something I am missing? Perhaps an error is logged about starting mythtv somewhere? Thanks in advance!

---

### Post by vigleik on 2006-06-25
You don't say how you tried to get mythbackend to start, did you do something like "sudo update-rc.d /etc/init.d/mythtv-backend defaults"? This is the default way to make programs that should be run by root start on boot. I didn't read the guide you're linking to though, so maybe Hyam told you to do exactly this. In that case, I don't know how to help you.

Vigleik

---

### Post by fxer on 2006-06-25
Thanks for the reply, it doesn't look like there is anything about updating the rc.d in the guide, so perhaps that is what I am missing. The actual script that I added to the init.d file is [here]("http://s91928265.onlinehome.us/hfamily/mythtv/mythtv-backend").

Do you think if I issued the update command you mentioned just as you typed it, that will solve my problem? Thanks again!

---

### Post by vigleik on 2006-06-25
[QUOTE=fxer]Do you think if I issued the update command you mentioned just as you typed it, that will solve my problem? Thanks again![/QUOTE]

I think so. It tells linux to run your script during bootup. It's possible that you'll have to submit an argument to tell it when in the bootup process it should be executed, for example if it depends on something else having happened first. But try this first.

Vigleik

---

