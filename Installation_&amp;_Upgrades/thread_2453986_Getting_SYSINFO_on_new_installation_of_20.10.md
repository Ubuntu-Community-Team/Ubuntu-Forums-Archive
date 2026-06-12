---
title: "Getting SYSINFO on new installation of 20.10"
date: 2020-11-20
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2020-11-20
I have sysinfo (0.7-10.1) on my DELL laptop which is running 20.10 via an upgrade from 20.04 LTS.  I shows in synaptic.  However, on another laptop with a new installation of 20.10, sysinfo does not show in synaptic (repositories same on both laptops).  When I download the deb file from ubuntuupdates and try to install with gdebi, it says that libgconf2.0-cil is missing.  It is on my DELL laptop, but cannot be gotten with the new installation of 20.10.

John

---

### Post by TheFu on 2020-11-20
[https://packages.ubuntu.com/search?keywords=sysinfo](https://packages.ubuntu.com/search?keywords=sysinfo) looks like sysinfo isn't the package name anymore after 18.04.

**xsysinfo** could be the replacement.

```
$ sysinfo

Command 'sysinfo' not found, did you mean:

  command '**xsysinfo**' from deb xsysinfo (1.7-9build1)
  command 'rsysinfo' from deb rstat-client (4.0.1-9)

Try: sudo apt install <deb name>
```

---

### Post by cigtoxdoc on 2020-11-21
For those who say that SYSINFO will not run under Ubuntu 20.10, please see attachment.  This is from PC that had been upgraded from 20.04 LTS and before that earlier upgrades.

So, the questions is how to make SYSINFO run under fresh installs of 20.10

John

---

### Post by TheFu on 2020-11-21
> **cigtoxdoc said:**
> For those who say that SYSINFO will not run under Ubuntu 20.10, please see attachment.  This is from PC that had been upgraded from 20.04 LTS and before that earlier upgrades.

So, the questions is how to make SYSINFO run under fresh installs of 20.10

John

Who said that?  Not I.  I just said that the name of the package appears to have changed.  If one of the new package names doesn't include it, then look for a PPA or a flatpak or a snap to install. Did you install one of those other packages as the Canonical/Ubuntu link showed? Did that not include the command you seek?

An upgraded system can easily retain older versions of dead packages. There is a question during the upgrade process which asks that question.

I'm not in the habit of downloading random PDF files.  That's one of the highest risk things we can do on our computers.

---

### Post by SeijiSensei on 2020-11-21
Have you tried **lshw**? It will give you a very extensive audit of your machine's hardware. Run it with sudo.

---

### Post by ActionParsnip on 2020-11-21
You are wanting to run sysinfo. What do you want to know about the system, exactly? Maybe we can advise...

---

### Post by TheFu on 2020-11-21
There's also **inxi** with lots and lots of different options depending on what summary you seek. For an overview, **inxi -Fz**, but details about storage, video accel, RAM, including S/N is often possible.

But in an enterprise environment, where you want to have a daily snapshot of all systems available on a DR/Website for reference and custom scripts, having the same format and same information across all systems like sysinfo provides (not just linux) is extremely useful.

Something else to consider is using **Ansible** to "gather facts" - that's the "setup" module and it captures more data about a system than any other tool I've ever seen.  That data is provided in JSON, so languages like perl, python, ruby will parse it easily.

---

