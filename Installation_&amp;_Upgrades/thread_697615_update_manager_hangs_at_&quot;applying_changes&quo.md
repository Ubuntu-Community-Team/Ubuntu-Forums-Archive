---
title: "update manager hangs at &quot;applying changes&quot; window"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by rziegler72 on 2008-02-15
It doesn't always seem to happen when installing recommended updates for Ubuntu 7.10, but frequently the Update Manager hangs in the "Applying Changes" window and the progress bar stops. In the Details window, it's not prompting for any user input, in today's case, it just says "ldconfig deferred processing now taking place" and it's been like that for 30 mins or so.

Not really sure how to debug or recreate this, but if I run strace on the parent pid for the synaptic process, I see this over & over again:

time(NULL) = 1203086787
ioctl(3, FIONREAD, [0]) = 0
poll([{fd=3, events=POLLIN}, {fd=6, events=POLLIN}, {fd=8, events=POLLIN}], 3, 0) = 0
nanosleep({0, 5000000}, NULL) = 0
read(34, 0xbf873ebe, 1) = -1 EAGAIN (Resource temporarily unavailable)
time(NULL) = 1203086787

Not sure if that's relevant or not.

The only way to get out of the window seems to be to kill the pids, which probably isn't a good idea if it's in the middle of installing kernel updates...

Please let me know what additional info I can provide.

Thank you in advance for your support.
~Rick

---

### Post by taurus on 2008-02-15
What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rziegler72 on 2008-02-15
'sudo apt-get update' fetches the files, ok, but the 'upgrade' command throws an error, probably because the update manager window is still open and has those files in use?

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libpq5 linux-headers-2.6.22-14 linux-headers-2.6.22-14-386 linux-headers-2.6.22-14-generic linux-image-2.6.22-14-386
  linux-image-2.6.22-14-generic linux-libc-dev xserver-xorg-video-ati
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
65 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by xeth_delta on 2008-02-15
To me it would seem there is another package administration program already running in the background.
What is the output of:
```
ps -ef | grep -i dpkg
ps -ef | grep -i synapt
ps -ef | grep -i adept
ps -ef | grep -i apt
```

---

### Post by rziegler72 on 2008-02-15
Here's the ps output:

[FONT="Courier New"]$ ps -ef | grep -i dpkg
root     16231 16083  0 09:29 ?        00:00:00 [dpkg] <defunct>
rziegler 27688 15913  0 12:40 pts/0    00:00:00 grep -i dpkg

$ ps -ef | grep -i synapt
rziegler 15969 15893  0 09:27 ?        00:00:00 gksu --desktop /usr/share/applications/update-manager.desktop -- /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 33554435 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpMrNbmq
root     15970 15969  0 09:27 ?        00:00:30 /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 33554435 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpMrNbmq
root     16083 15970  0 09:28 pts/1    00:00:09 /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 33554435 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpMrNbmq
rziegler 27690 15913  0 12:40 pts/0    00:00:00 grep -i synapt

$ ps -ef | grep -i adept
rziegler 27692 15913  0 12:40 pts/0    00:00:00 grep -i adept

$ ps -ef | grep -i apt
rziegler 15969 15893  0 09:27 ?        00:00:00 gksu --desktop /usr/share/applications/update-manager.desktop -- /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 33554435 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpMrNbmq
root     15970 15969  0 09:27 ?        00:00:30 /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 33554435 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpMrNbmq
root     16083 15970  0 09:28 pts/1    00:00:09 /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 33554435 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpMrNbmq
rziegler 27694 15913  0 12:40 pts/0    00:00:00 grep -i apt[/FONT]

---

### Post by xeth_delta on 2008-02-15
Try the following:
```
sudo kill -9 16231
```
Then try again the upgrade.

[EDIT] Placed a sudo before the call to the command

---

### Post by rziegler72 on 2008-02-15
I tried the kill -9 several times on that pid, but it still shows up as defunct.

[FONT="Courier New"]$ sudo kill -9 16231

$ ps -ef | grep -i dpkg
root     16231 16083  0 09:29 ?        00:00:00 [dpkg] <defunct>
rziegler 28441 15913  0 12:54 pts/0    00:00:00 grep -i dpkg

$ sudo kill -9 16231

$ ps -ef | grep -i dpkg
root     16231 16083  0 09:29 ?        00:00:00 [dpkg] <defunct>
rziegler 28492 15913  0 12:55 pts/0    00:00:00 grep -i dpkg

$ sudo kill -9 16231

$ ps -ef | grep -i dpkg
root     16231 16083  0 09:29 ?        00:00:00 [dpkg] <defunct>
rziegler 28499 15913  0 12:55 pts/0    00:00:00 grep -i dpkg[/FONT]

---

### Post by xeth_delta on 2008-02-15
May I suggest trying to kill also the other package management processes: 15969, 15970, 16083.
Then:
```
sudo apt-get -f install
```

---

### Post by rziegler72 on 2008-02-15
OK, I killed the pids and 'sudo apt-get -f install' looks like it ran to completion.  The update applet still shows 7 updates available (mostly new kernel image & headers).

Should I try them via the update manager again, or via command line with 'sudo apt-get upgrade'?

My only concern with using the command line is I haven't found a way to skip the 'xserver-xorg-video-ati' package, since my video card has brightness issues with it and I always have to downgrade that package.  I can skip it in synaptic, but haven't figured out how to via the command line.

Any ideas why my original problem is happening?  The hanging happens from time to time, and I'm not running multiple instances of the update manager GUI or command line at the time that it happens.  In this case I was just trying to install the latest updates after a fresh reboot.

~Rick

---

### Post by xeth_delta on 2008-02-15
> **rziegler72 said:**
> OK, I killed the pids and 'sudo apt-get -f install' looks like it ran to completion.  The update applet still shows 7 updates available (mostly new kernel image & headers).

Should I try them via the update manager again, or via command line with 'sudo apt-get upgrade'?

My only concern with using the command line is I haven't found a way to skip the 'xserver-xorg-video-ati' package, since my video card has brightness issues with it and I always have to downgrade that package.  I can skip it in synaptic, but haven't figured out how to via the command line.

Any ideas why my original problem is happening?  The hanging happens from time to time, and I'm not running multiple instances of the update manager GUI or command line at the time that it happens.  In this case I was just trying to install the latest updates after a fresh reboot.

~Rick

For now I'd go for the safe way, with command line:
```
sudo apt-get update
sudo apt-get upgrade
```

There is a way to lock a certain package version. You can do it from synaptic, right click on the package and an option in the menu will be available.

---

### Post by rziegler72 on 2008-02-15
I have skipped over the xserver ati package via synaptic, but from the cmd line, apt-get still wants to upgrade it everytime.

The 'apt-get update' and 'apt-get upgrade' worked ok, and I rebooted since there were kernel updates.

My only concern is that the next time there are updates (unrelated to the ati package), I frequently run into my original problem of the update manager hanging.  I can try it all from the command line next time to see what happens, but then I have to deal with the ati downgrade again.  It would be nice if I can figure out why the update manager is having problems...

~Rick

---

### Post by xeth_delta on 2008-02-15
> **rziegler72 said:**
> I have skipped over the xserver ati package via synaptic, but from the cmd line, apt-get still wants to upgrade it everytime.

The 'apt-get update' and 'apt-get upgrade' worked ok, and I rebooted since there were kernel updates.

My only concern is that the next time there are updates (unrelated to the ati package), I frequently run into my original problem of the update manager hanging.  I can try it all from the command line next time to see what happens, but then I have to deal with the ati downgrade again.  It would be nice if I can figure out why the update manager is having problems...

~Rick

There is a way to lock a package version from the command line, too. Look at [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin). You can find more information in the forums, look it up, I'm sure you'll find it.

About the updater problem, it might have been a one-time problem, one process crashed and kept the database locked. Try again next time.

---

### Post by rziegler72 on 2008-02-15
Unfortunately, this isn't a 1 time problem, as the update manager has hung on me several times in the past like this.  I'll look into the command line options.

Thanks for the replies xeth_delta.

---

### Post by xeth_delta on 2008-02-15
> **rziegler72 said:**
> Unfortunately, this isn't a 1 time problem, as the update manager has hung on me several times in the past like this.  I'll look into the command line options.

Thanks for the replies xeth_delta.

You're most welcome! If you have further questions, just ask.
Good luck!

---

### Post by rosslaird on 2008-03-14
I have the same problem, and it's pretty consistent from within synaptic and the command line (which I use more often).

```
ldconfig deferred processing now taking place
```

just hangs.
It's not a permissions or lock file error, and on my system it's unrelated to rebooting, leftover processes, and specific packages. ldconfig works fine on its own. The problem seems to be apt itself. I have no leads on how to fix this.

Ross

---

### Post by xeth_delta on 2008-03-14
> **rosslaird said:**
> I have the same problem, and it's pretty consistent from within synaptic and the command line (which I use more often).

```
ldconfig deferred processing now taking place
```

just hangs.
It's not a permissions or lock file error, and on my system it's unrelated to rebooting, leftover processes, and specific packages. ldconfig works fine on its own. The problem seems to be apt itself. I have no leads on how to fix this.

Ross

What was the exact command you used when you got the error?

---

### Post by rosslaird on 2008-03-14
```
What was the exact command you used when you got the error?
```

It happens almost every time I upgrade or install a package, basically. But not every single time...
So, exact commands include anything to do with apt:

apt-get install
apt-get dist-upgrade

etc. Anything that calls ldconfig at the end (which, as I said, works fine on its own).
I just have to close the terminal window. Ctrl-C doesn't work -- but the job of deferred processing is done, so there's actually no process that is hanging. It's the failure to terminate the output that is the problem (I think).

Ross

---

### Post by xeth_delta on 2008-03-14
Might be related to this: [https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/156041](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/156041)
Someone seems to have found a solution in there.

---

### Post by rosslaird on 2008-03-14
Actually, the posted solution does *not* work (at least on my system, and that of others in that thread).

R.

---

### Post by xeth_delta on 2008-03-15
> **rosslaird said:**
> Actually, the posted solution does *not* work (at least on my system, and that of others in that thread).

R.

Hmm, different causes probably.

---

