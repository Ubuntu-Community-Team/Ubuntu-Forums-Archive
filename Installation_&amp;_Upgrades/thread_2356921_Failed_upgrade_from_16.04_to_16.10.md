---
title: "Failed upgrade from 16.04 to 16.10"
date: 2017-03-28
forum: Installation &amp; Upgrades
---

### Post by gibbywilson on 2017-03-28
Hello

I am completely new to Ubuntu and just upgraded my laptop from 16.04 to 16.10 and I get a message saying installation is finished but with errors.

the box that pops up reads;

[B]Could not install 'systemd-shim'

The upgrade will continue but the 'systemd-shim' package may not be in a working state. Please consider submitting a bug report about it.

subprocess installed post-removal script returned error exit status 2[/B]

I hope someone knows how I can fix this error

Thanks

Gibby

---

### Post by Bucky Ball on 2017-03-28
Welcome. Have you rebooted, and if so, what happened? At this point, there is not a lot we can help you fix as you've received a message, but are not reporting an error booting or operating the machine. Reboot the machine, open a terminal (if you get that far) and post the output of this:

```
lsb_release -a 
```

It should say you are now running 16.10 if the upgrade worked. If you have any issues after booting the machine, try and be specific as to what is happening.

Just curious, was there a reason to upgrade to 16.10? That is an interim release, supported until the middle of this year. 16.04 LTS is a long-term support release supported until 2021. :)

---

### Post by gibbywilson on 2017-03-28
Thanks for the reply

The reason for the upgrade was simply I got Ubuntu yesterday and just wanted the latest version (I am new to this so not really sure how everything works)

I did as you asked and this is the message:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety

Thanks

Gibby

---

### Post by Bucky Ball on 2017-03-28
Well, you seem to be on 16.10. Is the machine working fine? No *error* messages?

As with Windows, the latest isn't always the greatest, and as mentioned, you will need to upgrade from 16.10 to 17.04 sometime mid-year. LTS releases are usually fine (five years support) unless you have very new hardware or are desperate for every new bell and whistle.

LTS releases also have the advantage of having longer to 'stabilise' while interim releases can sometimes have teething problems that never really get ironed out before they reach EOL and are no longer supported. On the other hand, some interim releases are rock solid from the start (occasionally), people love them, then they are gone. 

Either way, enjoy the learning curve and the ride and let us know if you are currently having a problem with the 16.10 upgrade. When you boot the machine from scratch and login, is there an issue or message along the way? :)

---

### Post by gibbywilson on 2017-03-28
Thanks Bucky Ball

When I am using the computer there seems to be no issues but when I use the Ubuntu Software to try and add a program it doesn't seem to work. I can click install and it asks so my password, then looks like it is installing but nothing happens. 

When I view my installed software I can see the program I tried to install in the list, but it still says "install" on the right.

When I click install again the process in repeated with the same result.

Can I revert back to 16.04 if you think that would fix the issue and if so how would i do that.

Thanks

Gibby

---

### Post by Bucky Ball on 2017-03-28
> **gibbywilson said:**
> Can I revert back to 16.04 if you think that would fix the issue and if so how would i do that.

The only way to do that is to reinstall 16.04 LTS from scratch (there is no 'downgrade' option in Ubuntu; I generally do a clean install on a different partition when a new LTS release comes out so I have both installs and can fallback on the old one if the new one falls over). 

Open a terminal and input these three commands, one at a time, and post any and all errors. You will be asked for your password and it will be invisible when you type. This is normal.

```

sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Tell us if there's any errors (use code tags for terminal output, instructions in my signature; green link, first line).

---

### Post by gibbywilson on 2017-03-28
Hello

After the first step i got

```

Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

after the second step

```

69 packages can be upgraded. Run 'apt list --upgradable' to see them.
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension


```

after the third step

```

dpkg: error processing package systemd-shim (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Thanks

Gibby

---

