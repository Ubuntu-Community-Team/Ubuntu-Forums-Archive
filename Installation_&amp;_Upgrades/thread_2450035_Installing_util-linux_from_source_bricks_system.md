---
title: "Installing util-linux from source bricks system"
date: 2020-09-06
forum: Installation &amp; Upgrades
---

### Post by stephanpham on 2020-09-06
Hello experts,

in an attempt to update a few shell utilities I frequently use (most notably *column*) I downloaded the source code of the most recent version of *util-linux*, built it and installed it like so:

```
cd $(mktemp -d)
curl -L -o - "https://mirrors.edge.kernel.org/pub/linux/utils/util-linux/v2.36/util-linux-2.36.tar.gz" | 
  tar -xvzf -
cd util-linux-2.36
./configure --prefix=/usr/
make
sudo make install
```

... after which Ubuntu wouldn't boot anymore. Some tinkering identified a broken */bin/mount* to be the culprit. More precisely, the above installation produces multiple, ostensibly essential binaries in a dysfunctional state. E.g. running a naked */bin/mount* in the terminal produces the error[B] 
/bin/mount: /lib/x86_64-linux-gnu/libmount.so.1: version `MOUNT_2_35' not found (required by /bin/mount)[/B] with similar results for other commands such as */bin/fdisk*, and */bin/umount*. However, only *some* binaries are broken (*column* did update just fine and works perfectly).

Now, my question is *why*? Why does the installation routine above break my system and what's special about *mount*, which breaks, compared to *column*, which gets installed properly? Did I make a mistake during configuration, or am I not supposed to install it like this?

My system is fine again, as a simple *sudo apt install mount* undid enough of the damage to allow me to properly boot again, so my question is purely out of curiosity as I'd like to understand and recognize any blunders I committed.

Thank you and kind regards,
Stephan

---

### Post by Impavidus on 2020-09-06
Much software is spread over multiple packages, with the executable in one package and the supporting libraries in another. They can be upgraded separately as long as you're only dealing with bugfixes that don't change the binary interface between them, which is very nice. Just upgrade the library and you've fixed a bug in every application using it. But if you want to go to a newer version, they can only be upgraded together. I guess you upgraded one package, but not the other.

To avoid these problems is exactly the reason why package management was invented. If you want to upgrade one particular tool by installing from source, I suggest you install the newer version in /usr/local/bin, where it won't interfere with the software from the official repositories.

---

