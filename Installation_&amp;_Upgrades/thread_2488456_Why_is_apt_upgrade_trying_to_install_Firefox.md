---
title: "Why is apt upgrade trying to install Firefox?"
date: 2023-07-05
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2023-07-05
I have two machines with Ubuntu 22.04. On one machine, I don't use Firefox, so I've uninstalled it. On the other machine, I use the flatpak version, so again I don't want the snap version installed.

But today, [FONT=courier new]apt upgrade[/FONT] wants to install Firefox. Why? I don't want it.
```
$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  firefox
The following packages have been kept back:
  libidn12 libinput-bin libinput10 ubuntu-desktop ubuntu-desktop-minimal ubuntu-minimal ubuntu-standard
0 to upgrade, 1 to newly install, 0 to remove and 7 not to upgrade.
Need to get 72.3 kB of archives.
After this operation, 261 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```
In case it makes a difference, I have Ubuntu Pro enabled on both machines.

Unfortunately, removing Firefox as follows doesn't help…
```
sudo apt remove firefox
sudo snap remove --purge firefox
```
… because [FONT=courier new]apt upgrade[/FONT] just wants to install it again.

Why is it doing this? How do I prevent this?

---

### Post by TheFu on 2023-07-05
ubuntu-desktop ubuntu-desktop-minimal are meta packages.  I think ubuntu-desktop-minimal includes firefox ... and Canonical thinks you should have it.  So, you can either put a "hold" on the firefox package (use apt-mark) or remove ubuntu-desktop-minimal as a meta-package and it shouldn't attempt to install firefox's .deb file (which is really just a wrapper around the snap).

that's the theory.

When you get tired of fighting with Canonical's snap choice, there are other distros which won't try to force snaps onto you, but still feel mostly like Ubuntu.

---

### Post by Paddy Landau on 2023-07-05
> **TheFu said:**
> ubuntu-desktop ubuntu-desktop-minimal are meta packages.  I think ubuntu-desktop-minimal includes firefox ... and Canonical thinks you should have it.
Ah, so that's why. That could be related to the installation process.
> **TheFu said:**
> So, you can either put a "hold" on the firefox package (use apt-mark)…
Thanks, I've done as you suggest.
 > **TheFu said:**
> or remove ubuntu-desktop-minimal as a meta-package…
Not a good idea, unfortunately, because it also removes ubuntu-desktop, which helps to ensure that you get important updates.
> **TheFu said:**
> When you get tired of fighting with Canonical's snap choice, there are other distros which won't try to force snaps onto you, but still feel mostly like Ubuntu.
It's fine. I like Ubuntu, and I don't have the time to mess around with learning a new system. What I might do instead is raise a bug report. I'm surprised that I haven't seen others complaining about this.

---

### Post by TheFu on 2023-07-05
There are lots of non-snap distros that are based on Ubuntu. They even use Canonical repos, but they block snaps.  The "learning curve" is almost non-existent.

I got tired of fighting with Canonical's choices and mandates for desktops.  I use two different solutions.  Linux Mint and Ubuntu Server with a very light WM-only setup. Those don't have the metapackages for ubuntu-desktop on those systems.  I've been running this way for about 5 yrs, so "important updates" haven't been a problem. Guess it depends on what you consider important. That's a question each person needs to decide.

---

### Post by Paddy Landau on 2023-07-05
Linux Mint seems to be one of the most popular distributions around.

I don't actually have much of a problem with snap, although I'm not blind to its problems. As of today, there is only one that I know of: Its inflexible sandbox. For example, the snap version of [Gedit is unusable]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1897562") for me. Using apt or flatpak instead solves this problem.

---

### Post by TheFu on 2023-07-05
> **Paddy Landau said:**
> Linux Mint seems to be one of the most popular distributions around.

I don't actually have much of a problem with snap, although I'm not blind to its problems. As of today, there is only one that I know of: Its inflexible sandbox. For example, the snap version of [Gedit is unusable]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1897562") for me. Using apt or flatpak instead solves this problem.

Create a new userid.  Place the HOME directory for that user in /nfs/home/{username}.
Log into the system with the new user.  Try to use **any** snap program.

Try to load Ubuntu onto a Chromebook from 2015 that only has a 16GB SSD for storage and 2GB RAM. That year, it was common for chromebooks to have 16GB total storage.  How many GB do the snap packages (and flatpaks) use?

2GB RAM was common for 5+ yrs in Chromebooks too.  The amount of bloat that snap/flatpak packages force into RAM is extremely high. People trying to extend the life if their old chromebook hardware basically cannot because of the bloat that Canonical has mandated across all Ubuntu desktop variants.  I know that a tight, fast, Ubuntu is possible in much less storage:
```
$ dft
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01           ext4   35G  6.5G   26G  21% /
/dev/nvme0n1p3                    ext4  672M  281M  343M  45% /boot
/dev/nvme0n1p2                    vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-home01           ext4  9.8G  5.3G  4.0G  58% /home
/dev/mapper/vg01-tmp01            ext4  3.9G   15M  3.7G   1% /tmp
/dev/mapper/vg01-var01            ext4   20G  2.3G   17G  13% /var

```
The OS is using under 10GB and that's being generous.  My /var is a little big ... for convenience. Same for /tmp, which I mount with specific mount options for security reasons.
To be far, this system does have a 1TB SSD inside it. Today, even with my bloated sizes for logical volumes, looks like about 60GB is being used.  This is on a fairly powerful Ryzen system, but I'd like to be able to use my 2 chromebooks in a similar way.

There are lots of issues with snaps.  Storage and RAM bloat. Refusing to work for some userids with standard HOME directory locations, and the lack of local control for the constraints.  Those are the main issues.  **Snaps aren't a terrible idea, but they shouldn't be mandated either, ** at least not across all ubuntu desktop variants.

---

### Post by Paddy Landau on 2023-07-05
> **TheFu said:**
> Create a new userid.  Place the HOME directory for that user in /nfs/home/{username}.
Log into the system with the new user.  Try to use **any** snap program.
As I say, the sandbox function in snap leaves major room for improvement. It really should copy flatpak's method. It is the one big failing of snap.
> **TheFu said:**
> Try to load Ubuntu onto a Chromebook from 2015…
Ubuntu is specifically aimed at modern machines with higher specs, just as Windows 11 and MacOS are. If you have an older machine, you need to use a different distribution, such as Lubuntu, Debian, Bodhi, etc. Lubuntu has rescued quite a few old machines in my life, where not even Windows would run properly any more.
> **TheFu said:**
> **Snaps aren't a terrible idea, but they shouldn't be mandated either**.
Until this Firefox thing today, snaps haven't been mandated. It's a piece of cake to remove snap altogether — well, it was until today. However, if you want to use Ubuntu Pro (i.e. ESM) or Livepatch, you have to have snap.

Again, I don't have much of a problem with snap, because it's easy enough to use alternatives. That's what I've done with Gedit.

---

