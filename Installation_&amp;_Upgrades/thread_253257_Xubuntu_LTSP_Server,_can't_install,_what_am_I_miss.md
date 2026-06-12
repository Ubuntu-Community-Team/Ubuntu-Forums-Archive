---
title: "Xubuntu LTSP Server, can't install, what am I missing?"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by keltorsori on 2006-09-08
I have the alternate install CD for 6.06 and the latest 6.10 for Xubuntu. My understanding is that there is an LTSP server install option for the initial setup. Once I start the setup, I'm never prompted for optional install packages, it just installs the base and that's it (I'm not using the server install option). I've tried everything I can think of, no such luck. What the hell am I missing? All I want to do is install Xubuntu and LTSP straight from the CD on a freshly formatted drive, nothing fancy. Please help!

-eric

---

### Post by keltorsori on 2006-09-21
*bump*
anyone?

---

### Post by roberto22085 on 2006-09-22
hmmmm....i didn't even know that that was a possibility. when i wanted to run my ltsp server, i had to install ubuntu, and set up all of the services and change the config files manually. there was a program that would do it but it never set up the terminal server correctly. i will have to dive deeper into this topic!

---

### Post by roberto22085 on 2006-09-22
I just googled and I found this:

[https://launchpad.net/distros/ubuntu/dapper/+source/ltsp/+pots/pkgconf-ltsp](https://launchpad.net/distros/ubuntu/dapper/+source/ltsp/+pots/pkgconf-ltsp)

I am wondering if maybe this is a package that can be downloaded via synaptic?!?!

---

### Post by roberto22085 on 2006-09-22
oooooh, look what i found!

[http://developer.novell.com/wiki/index.php/HOWTO:_Install_MueKow_on_Ubuntu](http://developer.novell.com/wiki/index.php/HOWTO:_Install_MueKow_on_Ubuntu)

I hope that helps!!!

---

### Post by keltorsori on 2006-09-23
Found the answer. At the install prompt, instead of typing 'Install' to continue, type 'ltsp-server' it will install with the LTSP server options. Well, at least it looks like it should, my install kept failing at the chroot part, but at least we know how to do it now. I must be missing documentation somewhere or something, there's gotta be a reason why this isn't more straight-forward.

---

### Post by Juxi on 2006-10-02
my LTSP build client stops with at the chroot too, what am I doing wrong?

---

### Post by keltorsori on 2006-10-02
found a bug?

---

### Post by Juxi on 2006-10-27
yeah I just did an install like this:
sudo apt-get install ltsp-serve

then it worked, I guess there were just some packages missing...

---

