---
title: "Starting Administrative Application problem"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Robin.Muilwijk on 2008-04-24
Hi,

I just upgraded from 7.10 to 8.04 without serious problems. Only minor issue is that Skype got removed so I wanted to install that again. For that it needs to start the package manager and of course this requires the "Starting Administrative Application" asking me for the admin password.

No luck though, in the taskbar I can see it starting up for a few seconds but then disappears again. I'm not asked for a password, and am unable to run the synaptic package manager.

I've seen the issue being reported between 1 and 2 weeks but in those topics it says it has disappeared.

Anyone with a hint how to resolve this?

Thanks Robin

---

### Post by Robin.Muilwijk on 2008-04-24
How funny, I might have solved it, will see.

What I did is run the Update Manager, check for any updates on 8.04. That triggered the admin password... no updates.

So running the package manager now worked.

Let's hope that did the trick, still remains odd though. Off to see if I can install Skype again.

---

### Post by Robin.Muilwijk on 2008-04-24
No luck,once the password is not in memory anymore I need to use that workaround again of running the update manager so I can get into the package manager. Hopefully fixed soon.

---

### Post by Peter09 on 2008-04-24
try doing sudo <any command>

if you get a sudo error then go to /etc/hostname and change your hostname to a single word.

You may have to go to recovery mode to do this.

Just a guess, on this, as its a common problem in Hardy.

PC

Edit re-reading your post again makes me doubt that this is the problem.

---

### Post by Robin.Muilwijk on 2008-04-24
Thanks I'll try that, I was just in gedit trying to sudo su which returns an unable to resolve host. My hostname is name-name, so I'll try to remove the "-" in the name.

---

### Post by Robin.Muilwijk on 2008-04-24
I went to recovery mode, got 3 options and chose shell command. What do I need to do from there, I tried gedit but no luck.

Edit; never mind, I used nano end got into the file, changed and it seems to work. First time it still did not respond, but second and after the package manager is now starting.

Thanks again for your help!

---

