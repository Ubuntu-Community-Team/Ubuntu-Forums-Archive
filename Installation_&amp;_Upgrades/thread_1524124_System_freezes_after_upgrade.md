---
title: "System freezes after upgrade"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by batshwa on 2010-07-04
Hello, dear Ubuntu community,

A few days ago I updated my Xubuntu 9.10 to 10.4 using update-manager.  I had been using Xubuntu for about a year with no problems whatsoever.  When I started the upgrade process, after having downloaded all files needed, I got a read/write error from both autoconf-2.6.5 and libavahi_core6 (the first file's exact location was /var/cache/apt/archives/autoconf-2.6.5-3ubuntu1_all.deb, the second file's location I forgot to write down).

Now whenever I launch update-manager, autoconf and libavahi are still there, waiting to be updated.  When I start the update process the system freezes for about 10 minutes and then outputs the same error as before when upgrading the system to 10.04.

The most annoying problem though is the following:  once in a while (whenever one of the processes mandb or man-db is running) the system freezes almost completely -- this means I cannot run any command or launch any program (for instance xterm) until the processes man(-)db terminate, but I can move the mouse and I do see conky running in the background (switching to a tty using ctrl+f1-f6 does not work either -- at least at that particular moment).

The same thing happened when I last tried to install something using synaptic.  This is an excerpt from the terminal output:

```
Unpacking mozilla-plugin-gnash (from .../mozilla-plugin-gnash_0.8.7-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
/usr/bin/mandb: can't read from /var/cache/man/index.db: Input/output error
Processing triggers for desktop-file-utils ...
```

I have also attached an abridged output of the command dmesg.

Does anybody have any advice on how to solve this problem?

Thanks a lot in advance! (Also I am sorry if this or a similar problem has been reported somewhere elso before, but I have not been able to find anything useful.)

---

### Post by batshwa on 2010-08-02
The problem has now become even worse:  I cannot even open synaptic or run apt-get -- synaptic simply closes with no error message, apt-get gives a "Bus error" -- this happens after about 3 minutes during which nothing really works.

Does anyone have any advice?  (I have also tried fsck -f several times on that device, with no positive result so far.)

Thanks in advance.

---

