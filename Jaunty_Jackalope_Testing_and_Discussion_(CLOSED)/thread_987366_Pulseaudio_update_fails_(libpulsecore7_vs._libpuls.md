---
title: "Pulseaudio update fails (libpulsecore7 vs. libpulsecore8)"
date: 2008-11-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tawmas on 2008-11-19
Hi!

After the last updates, I was left with pulseaudio packages unconfigured because of unmet dependencies. The root cause of the problem is found in this line from dpkg:

```
dpkg: error processing /var/cache/apt/archives/libpulsecore8_0.9.13-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libpulsecore.so.8.0.0', which is also in package libpulsecore7

```

If what I recall about APT is not too rusty, libpulsecore8 should conflict with libpulsecore7, but it is not doing.

I don't see anything related to that here in the forums or on Launchpad, but I upgraded from an Interpid box where I had Pulseaudio 0.9.11 from Luke Yelavich's PPA (1), so I might be seeing something a "regular" user doesn't -- if there are any "regular" users around here, anyway! :-)

I was able to remove libpulsecore7 and complete the upgrade with the following commands, after which audio seems to be working as well as it did before:

```
sudo dpkg --remove --force-remove-reinstreq libpulsecore7
sudo apt-get -f install
```

The first line is derived from an incantation I found in (2) after some quick googling. It didn't eat my newborn, but I cannot guarantee for yours! :-)

I'm posting this in case it might be useful to someone else, but I also have a question for you: do you think it's worth reporting as a bug? And, if yes, is it (likely to be) a packaging bug as I suspected?

(1) [http://launchpad.net/%7Ethemuso/+archive](http://launchpad.net/%7Ethemuso/+archive)
(2) [http://ubuntuforums.org/archive/index.php/t-557546.html](http://ubuntuforums.org/archive/index.php/t-557546.html)

---

### Post by ronacc on 2008-11-19
I'm pretty sure that is what caused the problem I got the same thing and I had also installed the ppa pulse audio in intrepid , I used the --force-overwrite option to resolve it .I don't think there is a need to file a bug , it seems to be a self inflicted wound :)

---

### Post by jfernyhough on 2008-11-19
$ cd /var/cache/apt/archives/
$ sudo dpkg -i --force-overwrite libpulsecore8 [tab]

---

