---
title: "Pretty sure I need help with this."
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Baphijmm on 2007-04-23
I was attempting to upgrade to 7.04 from 6.10 using the method recommended, via the update manager.  After the second step in the update process, the operation seemed to freeze consistently, warranting a reboot (as in, the window would stop everything and blank out if anything else were opened over it, including menus).  After letting it sit in this state for an hour, the update manager popped up with something on the order of 968 new updates available, while this other window was doing jack-squat.  I decided to try my luck with those.

After several hours of waiting, the program updates finished and I was prompted to restart my computer; I did so, because the other window trying to update the OS itself was still frozen.  Upon return to the login page, all text was replaced by those boxes that basically mean "I don't have this character, so here's a box instead".  Not too worried about it, I tried logging in, only to be presented with what is likely an error message (it flashes by too quickly for me to really read it) and a return to the very same login screen.  I can no longer use Ubuntu, the main OS on my computer (I'm posting this from a Windows boot).

Any idea wtf I can do to rectify the situation?  I'd like to return to using Ubuntu.

---

### Post by Spr0k3t on 2007-04-23
I don't think I can help with this one, but I had a similar experience to yours and I did manage to capture the error as it flashed by.  The error I had was "failed to initialize HAL".  See if that might be the same error message.  I believe I had to edit my xorg.conf for some reason.  Also, it sounds like there might be a font or two missing... see if you can get to the terminal through the grub menu and perform another sudo apt-get update/upgrade.

---

### Post by GeDaMo on 2007-04-23
If you can get to a terminal via safe mode, try
```

sudo apt-get update
sudo apt-get upgrade

```
That should upgrade any packages which require upgrading.

---

### Post by Baphijmm on 2007-04-23
New issue, related to attempting to do this: I am able to access the terminal in recovery mode just fine; however, I am on a college campus where the ISP has instituted a form of login that requires access to a browser before access to the internet can be established.  In other words, I cannot perform any upgrades from the terminal mode that I know of.

If someone knows how such a system works and how I might be able to get around it just for this, or would know of another way to solve this problem, I'd greatly appreciate it; at this point, I'm kind of desperate, as most of my files are on a partition only Ubuntu could access.

---

### Post by GeDaMo on 2007-04-23
There are command line utilities that can retrieve web pages such as wget or there's the text mode web browser lynx. I don't know if you have any of these installed.

---

### Post by Baphijmm on 2007-04-23
If they were not standard release, then no, I don't think I have them.

---

### Post by Paul41 on 2007-04-23
I was thinking about Lynx also, but I don't know if you can get it without a connection.

```
sudo apt-get install lynx
```

You could also use the live cd to mount your drive and get the files you need in the worst case.

---

### Post by GeDaMo on 2007-04-23
It looks like wget is a dependency of ubuntu-standard so it should be installed - try something like 
```
wget http://google.com
```
at the command line

---

### Post by Baphijmm on 2007-04-23
```
--12:02:04--  http://www.google.com
           => index.html
Resolving www.google.com... (random IP numbers)
Connecting to www.google.com|(random single IP)|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,134 (1.1K) [text/html]
100%[==================>]1.134  --.-- K/s

12:02:04 (29.23 MB/s) - 'index.html' saved [1134/1134]
```
This is exactly what I got when I tried wget; I don't know if that's supposed to be the case or not.

---

### Post by Paul41 on 2007-04-23
I think, although I may be wrong, that wget will only do a HTTP get and not a post. If that is the case you would not be able to use it for what you are trying to do. Lynx would work if you can install it.

---

### Post by GeDaMo on 2007-04-23
wget downloads a file - it looks like your internet connection is working.

---

### Post by Baphijmm on 2007-04-23
Actually, shortly after posting the last thing I did, I checked and lynx is indeed on here; I used it, then sudo apt-get update and upgrade; I'm still having the exact same problem.  Also, apparently what's happening at the login page is that, once I log in, it flashes the terminal, then just returns to the login screen again, without an error message like I thought there was last time.

If it helps, the update seemed to go a lot faster than I would have expected, as did the upgrade; I'm not sure either actually did anything.

---

### Post by GeDaMo on 2007-04-23
The upgrade should have told you how many packages it was going to upgrade and asked for confirmation.

As to the login problem, do you have space on your hard disk?

---

### Post by Paul41 on 2007-04-23
See if running this helps.

```
sudo apt-get -f install
```

---

### Post by Baphijmm on 2007-04-23
> **GeDaMo said:**
> The upgrade should have told you how many packages it was going to upgrade and asked for confirmation.

As to the login problem, do you have space on your hard disk?
It did neither.  How does one check hard drive space?  I should, easily, but I do recall a window popping up saying I didn't when it was updating, but it continued with the update anyway as though it wasn't a problem, and I was still able to download things to the hard drive with no issue.

Paul41: I did that, and it appears to have done nothing.

---

### Post by Paul41 on 2007-04-23
This should give you the amount of free space you have.

```
df -h
```

---

### Post by Baphijmm on 2007-04-23
According to that utility, I have 9.2G available, 8.8G of which is being used; however, it still also reads that 100% of the disk space is being used.  I seem to have seen this in other threads about this new upgrade; is this just a problem with the OS now?  Seriously, if that's the case, I don't mind waiting even a month for a more stable version; heck, how do I go back to 6.10 and just forgo this mess?

---

### Post by GeDaMo on 2007-04-23
You could try
```
sudo apt-get clean
```
to clear some space

---

### Post by bapoumba on 2007-04-23
> **Baphijmm said:**
> According to that utility, I have 9.2G available, 8.8G of which is being used; however, it still also reads that 100% of the disk space is being used. 
Please post the complete output of **df -H**.
You can make some room on your root(/) partition with **sudo aptitude clean** (you will not need sudo if in recovery mode, with te # promt you are already root), and may be remove some personal files from your /home partition.

---

### Post by Baphijmm on 2007-04-23
Actually, the sudo apt-get clean got me back into the GUI, at the very least; however, now there's absolutely no system text.  It's all that same aforementioned block stuff.  What to do?

Here's the complete readout of df -h, though:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.2G  8.1G  690M  93% /
varrun                379M  144K  378M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
procbususb            379M  156K  378M   1% /proc/bus/usb
udev                  379M  156K  378M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   18M  361M   5% /lib/modules/2.6.17-11-386/volatile
/dev/hda1             3.1G  2.2G  916M  71% /media/hda1
/dev/hda6              25G  6.6G   18G  27% /media/hda6
/dev/hdb1             113G   45G   63G  42% /media/hdb1
```

---

### Post by bapoumba on 2007-04-23
Looks like your /home is in your root file system (no separate /home partition).
Look into your personal files if you have anything you can remove.

---

### Post by Baphijmm on 2007-04-23
I can't read them to see what I can.

---

### Post by Paul41 on 2007-04-23
Do you have fonts in the terminal. If so you can check files there.

```
ls <directory_name>
```

---

### Post by bapoumba on 2007-04-23
> **Baphijmm said:**
> I can't read them to see what I can.
I'm not sure I understand. Cannot you browse your files (you posted you got the GUI), and may be empty your trash ? 
Sorry if I missed something.

---

### Post by Baphijmm on 2007-04-23
My trash remains empty; I rarely ever dump anything there.

I have the GUI back, but cannot read system fonts; as such, I cannot use the GUI to delete files, because I cannot read the file names.  I am currently using the terminal, because I went through the trouble of figuring out how to see file sizes with that to remove the biggest files; however, even so, it's not freeing up nearly as much space as the OS seems to want it to.  The home folder is practically empty, and we're still only at a 774 MB free position.  I'll keep going, though, and see if there's something else I can do.

---

### Post by bapoumba on 2007-04-23
> **Baphijmm said:**
> My trash remains empty; I rarely ever dump anything there.

I have the GUI back, but cannot read system fonts; as such, I cannot use the GUI to delete files, because I cannot read the file names.  I am currently using the terminal, because I went through the trouble of figuring out how to see file sizes with that to remove the biggest files; however, even so, it's not freeing up nearly as much space as the OS seems to want it to.  The home folder is practically empty, and we're still only at a 774 MB free position.  I'll keep going, though, and see if there's something else I can do.
what is the output to **ls -la .Trash** (from your /home file)?
With both GNOME and xfce installed, I have 3.6Go used. So it does not explain why your root partition is almost full.
Edit: **ls /root/.Trash/**
and see if you have any file there.

For your fonts, I'm not sure. Do you have ubuntu-desktop installed?
```
 aptitude show ubuntu-desktop
Package: ubuntu-desktop
State: installed
Automatically installed: no
Version: 1.43
Priority: optional
Section: metapackages

```

---

### Post by digitalis on 2007-04-23
If you've got squares instead of letters in all your menus/apps/etc, it could mean that the upgrade was only partial -  see [http://ubuntuforums.org/showthread.php?t=416510]("http://ubuntuforums.org/showthread.php?t=416510")

If you can get a terminal working, try the manual upgrade as mentioned in that thread.

S.

---

### Post by Baphijmm on 2007-04-23
Well, everything seems to be working okay now (it was indeed an incomplete upgrade); as such, I only have one more question: how do I remount my secondary hard drive?  It's listed in the aforementioned df -h readout as /hdb1.  I remember not knowing how to do this on the previous release either, but don't remember at all how to go about fixing it.  Fix that, and it'll be perfect.

---

### Post by Paul41 on 2007-04-23
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by Baphijmm on 2007-04-23
And that did it.  Thank you muchly!

---

