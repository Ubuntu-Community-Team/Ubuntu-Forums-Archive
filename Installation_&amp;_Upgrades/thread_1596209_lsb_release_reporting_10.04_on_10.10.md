---
title: "lsb_release reporting 10.04 on 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by agibby5 on 2010-10-14
I just did a fresh install of 10.10.  I was running 10.04 but formatted that partition when installing from a USB key.  Pre-install, I ran: 

```

sudo dpkg --get-selections > package.selections

```

Post-install, I moved some of my etc files back in.  I updated my sources.list.  Then I ran 
```

sudo dpkg --set-selections < package.selections
sudo apt-get dselect-upgrade
```

However, lsb_release is reporting 10.04.  When I boot the system it doesn't show the typical boot screen but rather "Ubuntu 10.10" and output of what's loading up.  On my laptop (upon which 10.10 installed fine), the splash screen shows the dots loading up with the new Ubuntu splash (10.10 style).

I go into Update Manager, and it thinks I need to upgrade to 10.10.  Thing is, I'm already on 10.10.  My kernel version is 2.6.35.22 and I'm running Gnome 2.32.00 according to the System Monitor.

I'm wondering if I'm getting 10.10 updates or 10.04 updates since my system incorrectly thinks I'm on 10.04.

Any ideas?

---

### Post by mikewhatever on 2010-10-14
Have you moved back the old /etc/lsb-release file?

---

### Post by bruno9779 on 2010-10-14
Your updates depend more on what is /etc/apt/sources.list than from /etc/lsb_releas.

You can edit the file if it says Lucid and change it to Maverik.

Also you could use something like this:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by agibby5 on 2010-10-14
> **mikewhatever said:**
> Have you moved back the old /etc/lsb-release file?

The only etc files I changed were fstab, grub stuff, and mdadm.  



> **bruno9779 said:**
> Your updates depend more on what is /etc/apt/sources.list than from /etc/lsb_releas.

You can edit the file if it says Lucid and change it to Maverik.

Also you could use something like this:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)


I manually changed the /etc/lsb_release and /etc/issues.  Things are showing up right, but there's a bunch of other buggy stuff going on.  I might try my luck at another install.  Maybe it was one of the packages that was installed from my package.selections that caused this bugginess.

---

### Post by agibby5 on 2010-10-14
I just reinstalled 10.10 again and this time the only thing I did differently was remove the old kernels from my package.selections file. Everything is good now.

---

