---
title: "HELP!!! The last Huge Upgrade Hosed My Entire System 14.04"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-09-20
Help!!!

After the last upgrade I received the following message, when I tried to logged in from the greeter:

:unable to launch "gnome-session --session=gnome-flashback-compiz" X  session ---"gnome-session --session=gnome-flashback-compiz" not found;  falling back to default session.

When I tried to resolve this in Synaptic, I was instructed to fix the  broken packages first, which I could not do in Synaptic. When I rebooted  and tried to repair Broken Packages in Recovery Mode, I received the  following messages:

gnome-session depends on gnome-session-common(=3.16.0-1; however:version  of gnome-session-common on system is 3.9.90-0ubuntu12.1.

And

An error occured

The following details are provided

E:/var/cache/apt/archives/gnome-session-common_3.16.0-1_all.deb:trying  to overwrite 'etc/gnome/defaults.list', which is also in package  desktop-file-utils 0.22-1ubuntu1'

I am also getting dpkg errors and the Ubuntu option is missing from the greeter.

I have a backup drive, that is out-of-sync, which I am using to get online with.

This is important, because I'm running a business on this system; and I  have business files on this system that I need to access. I've even  tried to use a USB cable to access this drive, and it won't even mount.  The only way I can access this drive is through the Root Prompt in  Recovery Mode. I don't dare try to upgrade my remaining drive!

Any help appreciated.

Thanks, Hannibal

---

### Post by jean_rivire on 2015-09-21
Hi,
For the time being: access your file can be dne from usb live image, where what you need to do is to escape the install in order to access to a desktop; once there, you can install file manager and put your files in the cloud I believe. (If the usb key doesn't load , make sure your BIOS priority is the usb key.

For the rest: I see that something is problematic with compiz, but compiz is risky to even upgrade or reinstall, and I am not a crack, so I am not sure, personally if the files are saved, I would probably do a fresh install  but wait for somebody else to get a better idea.

Cheers,

---

### Post by coljohnhannibalsmith on 2015-09-21
> **jean_rivire said:**
> Hi,
For the time being: access your file can be dne from usb live image, where what you need to do is to escape the install in order to access to a desktop; once there, you can install file manager and put your files in the cloud I believe. (If the usb key doesn't load , make sure your BIOS priority is the usb key.

For the rest: I see that something is problematic with compiz, but compiz is risky to even upgrade or reinstall, and I am not a crack, so I am not sure, personally if the files are saved, I would probably do a fresh install  but wait for somebody else to get a better idea.

Cheers,

Thank you sir.

I will try those things. In the meantime I'll have to scramble to get my Enterprise System running again.

---

### Post by tgalati4 on 2015-09-21
What exactly did you try to update?  From 14.04 to 15.04?

Open a terminal:

```
uname -a
cat /etc/issue
lsb_release -a
```

There should be a list of packages that you attempted to upgrade in /var/log/apt

```
cat /var/log/apt/history.log
```

---

