---
title: "Updating feisty. Error after reboot"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by jollyr0ger on 2007-04-19
Hi to all.

I've got a serious problem. Yesterday (when feisty was still in beta) I've tried to update to feisty, and I use the method of modify the source.list of apt-get, 'cause the gksudo "update-manager -c" method did not work.

Then I've changed the term edgy with feisty. After I've prompt
sudo apt-get update
and 
sudo apt-get upgrade

then I've tried to shout down the pc 'cause was very late. But the shour down was broken and I've put off the power. Today I've tried to start ubu but there's a problem. 
In the startup the kernel fix the file system about the brutal shoutdown, after done it won't continue.
Doing the startup in Recovery Mode it break after the setting the font of console or system, something like that.

how can i finish the upgrading?

---

### Post by astronic on 2007-04-19
Quite frankly: You've broken your system really well.

First of all: apt-get / aptitude are explicitly not recommended to be used for upgrading edgy to feisty. Use update-manager instead.

Second of all: If you still decide to use apt-get / aptitude, you have to use "dist-upgrade" NOT just "upgrade". This is what probably broke things for you.

You could boot from a Live-CD, check your filesystem, chroot to your Ubuntu installation, look through the /var/log/dpkg* files and manually try to revert the changes. I my opinion, however, this is a waste of time. Either restore your last backup or safe your files and make a fresh installation of feisty.

HTH,
Stefan

---

### Post by jollyr0ger on 2007-04-20
when I've tryed to update i didn't know about the right way to do it... now I know

I've done the apt-get upgrade, after I've done apt-get dist-upgrade

but in the download fase I've killed it, and shoudown the pc. but the shutdown freeze. then i've turned off it.

now the system still don't start 

-can I upgrade the existing system with the livecd, or in different way?
-can i have the list of installed apps in apt of broken system?

---

### Post by venik212 on 2007-04-20
I have tried the network upgrade, but got an error, and now ADEPT seems to have trouble-- 
" There was an error committing changes.  Possibly there was a problem downloading some packages or the commit would break packages."

What do I do?

---

