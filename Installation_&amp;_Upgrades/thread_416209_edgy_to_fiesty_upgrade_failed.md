---
title: "edgy to fiesty upgrade failed"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by andysdp on 2007-04-20
I have followed the recommended network update using adept manager, after checking that my system was up to date first. Upgrade wizard was then offered and I followed the instructions. All the files seemed to download OK (1234 packages - took half an hour or so). The wizard then started installing / upgrading the downloaded packages - got to about 8% complete and has fallen over - with an error could not commit changes.

Have retried running Adept, using full upgrade button, apply changes and it falls over with following error:

"Could not commit changes - adept manager
There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break packages."

Edgy seems to be a little unstable since. Open office has been upgraded to 2.2.

Could anyone give me any advice what to do next?

I have had problems in the past with nvidia drivers which has been sorted using the envy script, and I notice in the adept list of packages that nvidia-kernel-common has been installed.

I would be grateful of any help.

Cheers

Andy

---

### Post by k7k0 on 2007-04-21
In my case, a package didn't update correctly, I reconfigured it manually and restarted the process.

Try running in a command-line (System -> Konsole)
```
sudo dpkg -a -reconfigure
```

---

### Post by jdong on 2007-04-21
The correct command is

```

sudo dpkg --configure -a

```

After that, run:

```

sudo apt-get -f install

```

Then, run
```

sudo apt-get dist-upgrade
sudo apt-get install kubuntu-desktop

```


At this point, you should be fully upgraded. Report any errors that pop up along the way...

---

### Post by andysdp on 2007-04-21
Thanks guys, will give this a try.

After reading further on the forums, I'm wondering whether I would be better doing a clean install from CD rather than network upgrade. Is there any benefit?

I'm also looking at moving my /home to a separate partition on my second hard drive, before doing this. Which is the best HOWTo to follow - there's a few out there!

Thanks

Andy

---

### Post by andysdp on 2007-04-21
Jdong -  I decided to move my /home to a separate partition which seemed to work OK - followed the howto on [www.psychocats.net](www.psychocats.net).

I then followed your instructions which also seemed to work - in as far as the packages got installed and configured.

I got an error message at the end - which I have seen before after routine updates in edgy - and ignored (rightly or wrongly) and edgy continued to work. Error as follows:

"Errors were encountered will processing exim.
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Rebooted and I have a problem!

"Failed to start the X-server. It is likely that it is not set up correctly"

next screen

X window system version 7.2.0
Release date: 22 January 2007
x protocol version 11, revision 0, release 7.2
build operating system: linux ubuntu

next screen

The x server is now disabled. Restart GDM when it is configured properly.


This as far as it goes!

I have a command line login.

Any ideas?  Is there an envy type script to fix this in fiesty?  I suspect this linked to nvidia drivers - but I don't know what to do.

Is it time to do a clean install with the CD.

Any help would be appreciated.

Cheers

Andy

edit: just tried the envy script - doesn't seem to work with fiesty....

---

### Post by andysdp on 2007-04-21
Have succeeded with the upgrade I think....

Solved the x server problem by editing the xorg.conf file - changed driver "nvidia" to "nv" and it booted first time.

All seems to be working.

Silly question:  How can I find out if I'm actually running Fiesty now?  Is there anywhere that reports which version of Kubuntu is running?  I can see that KDE is now running 3.5.6.

Anyway, thanks for you help people.

Andy

---

### Post by sauyeeluo on 2007-04-21
use either:

1. sudo lsb_release -a

output should be something along the lines of;

distributor:
description:
release:
codename:

so if feisty upgrade was implemented correctly i guess you would see '7.04' in the release field and 'feisty' in the codename field.

or

2. cat /etc/issue

both should give you an indication as to what you distro version you are running, if i remember correctly.

---

### Post by andysdp on 2007-04-21
You are correct with both:

feisty, and / or 7.04 reported in results as you suggested

Nice to know upgrade was successful....

Thanks for your help.

Andy

---

