---
title: "upstart config on upgrade to 6.10"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by shochatd on 2006-11-19
I am a new Ubuntu user (from SUSE 10.1) and am running 6.06. I was looking over the new features for 6.10 and considering upgrading. My main concern is "upstart". Suppose I upgrade as in the instructions:

gksu "update-manager -c"

Will my upstart configuration be generated automatically from my existing sys5 configuration? Or will it just start me off with a default configuration? How do I change the configuration? For example, I'm going to want NFS started during boot. I know how to do that in the Sys5 world, but have no clue how I'm supposed to do it with upstart. Does it have a GUI for saying which services I want started at boot time? How do I even start a daemon manually? Will I no longer have /etc/init.d scripts, or does upstart work with those? 

This seems to me to be mainly an upgrade question which is why I posted it here. If I should have posted in the "server" section, please advise. I'm running a desktop system which also has a few server-type responsibilities (firewall and NFS server).
-- David

---

