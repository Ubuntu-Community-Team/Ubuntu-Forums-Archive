---
title: "/etc/init/ssh.conf - Respawn Question"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by artomason on 2013-01-25
[COLOR=black][FONT=Tahoma]Currently I'm using 12.04 LTS on an ancient hardware configuration for a home server. I have MaxStartups in /etc/ssh/sshd_config set to 2 however I'm unsure if the new upstart respawn setting in /etc/init/ssh.conf overrides these setting.[/FONT][/COLOR]

[COLOR=black][FONT=Tahoma]> /etc/init/ssh.conf[/FONT][/COLOR]
> 
[COLOR=black][FONT=Tahoma]respawn[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]respawn limit 10 5[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]umask 022[/FONT][/COLOR]


[COLOR=black][FONT=Tahoma]I would like to limit the instances of SSH to 2, and if the /etc/init/ssh.conf stuff doesn't effect ssh instances due to settings in sshd_config, can I remove the respawn & respawn limit. Basically letting sshd_config handle the max instances without risking the service being respawn 1000 times due to a hacker or glitch.[/FONT][/COLOR]

[COLOR=black][FONT=Tahoma]Thanks.[/FONT][/COLOR]

---

### Post by jrierab on 2013-02-15
[respawn]("http://upstart.ubuntu.com/wiki/Stanzas#respawn") is used to allow the daemon to re-start in case it is killed or dies somehow. The limit is to prevent it failing and starting again too quickly (which would indicate a failure somewhere anyway).

So, this has nothing to do with the number of ssh instances.

---

