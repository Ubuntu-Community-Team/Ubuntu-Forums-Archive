---
title: "Having problems with gnome-keyring/seahorse..."
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by joobuntjoo on 2009-03-18
Hi all,

I have a normal ssh key setup to login to some systems remotely. I know the keys work fine, as I can get them working in previous Ubuntus and Fedora. I can also get the key working fine in Jaunty on this install, logging in via ssh-agent taking care of it, by adding a key with ssh-add.

In Jaunty with gnome-keyring (seahorse?), I can't really tell whats happening though. It asks for an unlock password (assuming a passphrase? Can't tell though for sure), I try any like login ones or none, which make no difference, it just reappears asking. During that time I can't do anything else (main gnome menus unaccessable). However, if I put in my passphrase, it lets me through (hence I assume its after a passphrase), but then this doesn't work and seems to ignore using the key totally. So I'm assuming its actually asking for the passphrase, but then ignoring it ?

Am I misunderstanding how this now works. Is there any way to troubleshoot this to see why its failing (when I know keys/ssh/ssh-agent all work fine if I test). Likely just simple error on my part, but its a bit confusing the way it is currently.

Also if I go to seahorse and change password, it lets me put any password in as the password to change "from", and doesn't seem to care what I put in there, nor have any effect after ?

---

