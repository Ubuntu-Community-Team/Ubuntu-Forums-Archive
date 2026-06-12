---
title: "libdns16 buffer_read problems"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by THEspacemonkey on 2005-06-12
Putting this thread in Installation, as I assume it has to do with either the distributed package, ISO, or my installation download. Moderators feel free to move to a more appropriate thread if needed.

Now I have both laptop and workstation ubuntuized, and cannot update either because libdns16 reports a buffer_read error.

From Synaptic's terminal, I get:

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /cdrom//pool/main/b/bind9/libdns16_9.2.4-1ubuntu1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libdns16': Invalid argument
```

From the command line using apt-get upgrade and such, I get:

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gedit_2.10.2-0ubuntu2_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libdns16': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/gedit_2.10.2-0ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I would gladly just remove libdns16, as I am not running BIND on either machine, but it is also required by ubuntu-base and ubuntu-desktop. Seems a little harsh to be removing ubuntu to get rid of a broken dns library:)

No matter what I try to install, this is the error that I get.](*,)

Looked everywhere for an apt-get version of --force, but it doesn't seem to be working for me either - and when I try to re-install, apt just demands the installation CD, which only repeats the installation of the offending package.

Checked the forums here, as well as the ubuntu bug tracker - with no mention. I worry that this is yet another personal problem:oops:

What are the ways of getting out of this circle?

---

