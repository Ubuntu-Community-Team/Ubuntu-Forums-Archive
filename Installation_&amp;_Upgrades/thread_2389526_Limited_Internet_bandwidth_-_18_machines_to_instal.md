---
title: "Limited Internet bandwidth - 18 machines to install"
date: 2018-04-18
forum: Installation &amp; Upgrades
---

### Post by 0cs935-bill on 2018-04-18
I'm new to Ubuntu, having been strictly on Fedora since FC2 through their latest which is F27.

I need to install Ubuntu 16 | 17 on my 18 boxes. I'd like to do what I've done on Fedora to limit downloads to "master" machines and seed the .deb files to secondary machines. I just don't know how to do it.

On a "master" machine, I would do normal package maintenance that, do to my location and expensive/limited bandwidth takes a very long time. I'd like to seed all the .deb files from that process to the secondary machines so that when it's time for them to get new packages, they already have the bulk of them local. Not every machine is identical to the master, so just scripting a forced .deb file install isn't the solution. I want to seed the masters .deb files and then allow the normal package maintenance on any given secondary machine to take over and NOT download what it already has.

Under the Fedora scheme, I wrote a script that would scp from master to secondary. I'd like to cook up a script under Ubuntu to do the same thing but experimentally I've not figured out the necessary steps.

Suggestions?
Reading list?
Internet sites to visit?
... ?

---

### Post by kerry_s on 2018-04-18
it should be pretty much the same as in fedora. just change your dnf options to apt/apt-get options in your script.

it's all linux underneath there's only slight changes from distro to distro.

sudo dnf update-> sudo apt update && sudo apt full-upgrade
(like fedora you can add "-y" to automate it, so you don't have to press "y" to continue)

i'm sure other options are common if you talking command line, there should be little to no difference.
also fedora being a rolling release & ubuntu being what it is, you will most likely be using older software than you were in fedora, unless you go for ubuntu 18, which is beta 2 right now, but will be the next long term version.

---

### Post by QIII on 2018-04-18
Hello.

On my way to slumberland, but I just thought I'd pop in to say that you can create a network share as a repo, maintain it as a mirror (maybe update it a couple of times a day) and direct all of the sources.list entries in the networked machines to that resource.

Not at my machine right now, but I think that researching the apt-mirror package may get you off in the right direction.

If you don't want to wrestle with scripts, you could use the command-line version of Ansible (free, but the GUI version, Ansible Tower isn't unless you use the free-but-hobbled version that is limited to ten machines) after a bit of a learning curve.  That way you could tell each machine to update only what it has installed -- or install something on all (or some) of your machines from a central location.

---

### Post by Irihapeti on 2018-04-18
[Apt-cacher-ng]("https://www.unix-ag.uni-kl.de/~bloch/acng/") may do what you're looking for. You install it on one machine and tell the others to use that machine as the proxy. If a package is already in the cache, it's not downloaded again.

The proxy is set as part of the install process; you don't have to complete the install first.

---

### Post by 0cs935-bill on 2018-04-20
Sorry for the late reply, but I never got notified anyone answered my request. I thought I hit the right button for that, but I'm new to the forum, so I probably messed up.

Irihapeti:
[Apt-cacher-ng]("https://www.unix-ag.uni-kl.de/~bloch/acng/")[COLOR=#000000] sound like it may do the trick. I'll check it out.

QIII:
Setting up a real mirror isn't realistic as just getting the download for the mirror would be a real issue for me. If there's a way of setting up a partial mirror of only the packages I normally use, then that might be an option with the real mirrors as fall back positions for anything my quasi mirror wouldn't have. I'll check that out.[/COLOR]

---

### Post by Irihapeti on 2018-04-22
To update my previous post, I've realised that the standard install ISOs don't allow one to set a proxy. (My excuse is that mostly I use non-standard install methods. :oops:)

Assuming the install is in English, you could do the initial installs with internet disconnected, and then add the proxy setting as described in the apt-cacher-ng docs before doing any updates over the internet.

---

