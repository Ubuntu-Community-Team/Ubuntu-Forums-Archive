---
title: "Upgraded from 5.10 to 6.06 (via Synaptic): Having Issues and Not Sure What to Do"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by Wolfey on 2006-11-09
(Wow, it's been awhile since I last posted here :p)

I held off upgrading to 6.06 when it first came out after seeing that other people here had trouble with the upgrade process...and kept putting it off till now.  Unfortunately, when I tried to upgrade, it did not go as planned, and when booting into Ubuntu, I can only log in via the command line.

I apologize for not being able to give any more information about this issue right now, as I'm *really* not sure where to start looking first to fix this.

If anyone could help me out with this issue, I'd really appreciate it :)

---

### Post by jpeddicord on 2006-11-09
Log into recovery mode, and try running **aptitude dist-upgrade**. Do it multiple times if it complains about a dependency. Restart after all updates are completed, and then see if it works.

If you get any errors about X, it probably has to do with graphics drivers. Are you using a graphics card?

---

### Post by ciscosurfer on 2006-11-09
If you do an advanced search on the forums, you may find the answer you are looking for.

First, I would check to see that your sources.list is up to date with dapper being used instead of breezy.

Next, I would issue the following line```
sudo aptitude update && aptitude upgrade && aptitude dist-upgrade
```

You can also issue```
sudo dpkg-reconfigure xserver-xorg
```

And then try reinstalling any graphics drivers you may have been using as well.

Post back after you've done this.

---

### Post by Wolfey on 2006-11-10
> **jacobmp92 said:**
> Log into recovery mode, and try running **aptitude dist-upgrade**. Do it multiple times if it complains about a dependency. Restart after all updates are completed, and then see if it works.

Recovery mode?  I can't recall using that before :?:  If I read up on it correctly, though, it's accessed by having the word "single" at the end of the "kernel" line for the boot entry I want to use in menu.lst - am I understanding this correctly?

If so, I want to mention that I tried **aptitude dist-upgrade** in recovery mode, and it doesn't work, giving me the following error message:

```
bash: aptitude: command not found
```

I also tried **apt-get dist-upgrade**, but need the **-f** switch for it to continue.  Even when I do that, though, it gives a ***long*** list of errors, practically all of them alternating between "Failed to fetch http"//us.archive.ubuntu.com/**path/to/file**" (**path/to/file** varies) and "Temporary failure resolving "us.archive.ubuntu.com".

Could something have messed up my network settings during the upgrade?

> **jacobmp92 said:**
> If you get any errors about X, it probably has to do with graphics drivers. Are you using a graphics card?

Yes - according to the specifications for my laptop, it's an ATI Radeon 9700.

> **ciscosurfer said:**
> First, I would check to see that your sources.list is up to date with dapper being used instead of breezy.

It's listed as "dapper" everywhere except for two line, and both of those lines are commented out:

```
**# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted**

deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

**# deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted**
```

Would those two lines referring to "breezy", even though they're commented out, be an issue here?

> **ciscosurfer said:**
> Next, I would issue the following line```
sudo aptitude update && aptitude upgrade && aptitude dist-upgrade
```

I'll have to hold off on trying this for the moment, since as I earlier mentioned, the "aptitude" command isn't being found :(

> **ciscosurfer said:**
> You can also issue```
sudo dpkg-reconfigure xserver-xorg
```
I tried it, but it doesn't work, and gives me the error message:

```
xserver-xorg is broken or not fully installed
```
Does any of this information help narrow down what might be causing my problems here?

---

### Post by ciscosurfer on 2006-11-10
The two commented lines in your sources.list file are fine--they wouldn't affect the upgrade.

You can use apt-get instead of aptitude if aptitude is not installed.

Can you ping any sites?  Is your network connection hosed?  Try pinging [www.google.com]("http://www.google.com")```
ping www.google.com
```Do you get a response?

Once you get a connection up and running, you can download via a dist-upgrade, the new xserver for your system.

So, first try to ping.  If that's successful, then issue the following```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by Wolfey on 2006-11-10
> **ciscosurfer said:**
> The two commented lines in your sources.list file are fine--they wouldn't affect the upgrade.
That's good to hear :)

> **ciscosurfer said:**
> You can use apt-get instead of aptitude if aptitude is not installed.
Thanks for mentioning that - I'll keep it in mind :)

> **ciscosurfer said:**
> Can you ping any sites?  Is your network connection hosed?  Try pinging [www.google.com]("http://www.google.com")```
ping www.google.com
```Do you get a response?

The only response I got was "unknown host" :(

```
unknown host www.google.com
```

I also tried pinging "72.14.207.99", an IP address that also leads to Google (well, Google English), which also fails, stating:

```
Network is unreachable
```

Pinging 127.0.0.1 seems to work, though...

---

### Post by ciscosurfer on 2006-11-10
You can't upgrade because you don't have an internet (network) connection.

You can ping 127.0.0.1 because that is the loopback address, which effectively means your machine or localhost.  You can ping yourself.  That's good.  That means your LO interface is functioning just fine.

You need to try resetting your modem (cable, DSL, dial-up), your router (if you have one--and you should--firewall/router is the way to go).

Try unplugging all network cables, waiting 30 seconds, plug back in, reboot, see if you have an internet connection by pinging any site again.

---

### Post by Wolfey on 2006-11-11
> **ciscosurfer said:**
> You can ping 127.0.0.1 because that is the loopback address, which effectively means your machine or localhost.  You can ping yourself.  That's good.  That means your LO interface is functioning just fine.

You need to try resetting your modem (cable, DSL, dial-up), your router (if you have one--and you should--firewall/router is the way to go).
I just tried that (and I do have a router :)), and then I realized something - when I tested pinging 127.0.0.1 at that time, I was using a Live CD, rather than my copy of Ubuntu on the laptop #-o

Trying to ping 127.0.0.1, this time on my laptop's copy of Ubuntu, gives the error message:

```
Network is unreachable
```

I still can't believe I got that mixed up...

---

### Post by ciscosurfer on 2006-11-11
If you're able to, backup your important data, and then do a fresh install of 6.06 or 6.10 from disc.

I realize this is not ideal, but we made be troubleshooting this for a long time and a doing a quick backup and reinstall fresh will be a whole lot quicker.

Any other suggestions from other forum members is welcome at this point.  

Sorry I couldn't be of more help Wolfey :(

---

### Post by Wolfey on 2006-11-12
A reinstall?  I *really* don't want to have to do that...though given the previous upgrade I went through (from 5.04 to 5.10) had some issues, that might be just what I need to do...

There's a few questions I have to ask before I do this, though:

[list][*]This laptop was set up to dual-boot between Ubuntu and Windows (XP Professional) - are there any precautions I should take to ensure the reinstall doesn't cause problems with Windows?  I should note that, when using Ubuntu (or any other Linux distribution), the drives for it show up as "hda1" (partition for all Windows data) and "hda2" (partition used for sharing files between Windows and Linux).


[*]I have two CDs from when I got the laptop (Ubuntu 5.04), one an Install CD and the other a Live CD, but the only choice I see on their page that would correspond to either of those is the Desktop CD...would that be the disc I should use for reinstallation?  I admit that might sound like a dumb question, but as far as I'm concerned, better safe than sorry when it comes to a reinstall...[/list]
I'm not going to be able to do the reinstall right now, though - first I'm going to have to back up any important data (both for Ubuntu and Windows), and I might be busy the next few days with work.  After that, though (and assuming there isn't anything else I can try to fix this first), I'll do a reinstallation.

And it's OK, don't worry about it - if I have to reinstall Ubuntu to take care of this issue, then I'll reinstall.

---

