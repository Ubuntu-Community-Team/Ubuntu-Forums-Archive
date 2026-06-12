---
title: "Aborted 7.10-&gt;8.04 Upgrade - Damage control?"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by soluphobe on 2008-05-30
Hi, All,
[B][SIZE="3"]
Long:[/SIZE][/B] Sorry for being an idiot, but I've got myself into a jam.  The situation was that I was sitting at a place with wifi, no ride, and my gutsy laptop.  I figure I've got a few hours to kill, so I boot up and upgrade to Hardy.  At least, that's what I wanted to do.  After all files have been downloaded, the installer begins unpacking/replacing my stuff.  With 1:19 left to go, my ride shows up.  Now, because of [really boring story] my laptop has NO battery (I survive on outlets).  Because of scheduling, it ends up I **need** to leave **now**.  I have to kill the install, shut down, and get out.  

It's some time later, I want to continue the upgrade.  (I have no internet where I am now on the laptop.)  

So I boot up and, as expected, there are severe errors that won't let me log in.  I boot into restore mode and get in as root.  This works.  I run ```
apt-get upgrade
``` which tells me to run ```
dpkg -something?
Maybe:  dpkg --configure -a
```
I run these commands for a while, and I've reached a standstill.  Running '*dpkg --configure -a*' gets me a literal error overflow.

**[SIZE="3"]tldr:[/SIZE]**  I aborted my Gutsy->Hardy upgrade, my system's screwed up but I can boot into restore mode.  Any magic commands?

Please help the noob!  Thank you all!

---

### Post by Pumalite on 2008-05-30
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
(one at the time)

---

### Post by soluphobe on 2008-05-30
Thanks!

I'll try that now.

EDIT: '*dpkg --configure -a*' gives me the usual error spam, and '*apt-get -f install*' gives me:
```
dpkg: erE: Sub-process /usr/bin/dpkg exited unexpectedly
```

EDIT 2: By the way, here's the last lines of the output from '*dpkg --configure -a*' :
```
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion '!queuelen' failed.
Aborted
```

(and thanks for the fast reply!)

---

### Post by soluphobe on 2008-05-30
It seems that all my errors are with dependency.  Is there any way I can manually force dpkg to configure, say, dbus?  I know I can use '*dpkg -i dbus*' but I don't know where the installer stored the package files.  In my /tmp/ folder there's just one file, which is the Hardy installer...

---

### Post by Pumalite on 2008-05-30
Use 'sudo' at the beginning of the command
Make me a sandwich
No
sudo make me a sandwich
OK.

---

### Post by soluphobe on 2008-05-30
I'm already root, shouldn't that be no issue?  (Love xkcd, though)


Could I use '*aptitude dist-upgrade*' and then clean it up after?

---

### Post by Pumalite on 2008-05-30
If you are root; that's fine. It looks to me like a reinstall, but I tend to be less laborious than some other guys in this forum. So; you might want to wait for a better answer.

---

### Post by soluphobe on 2008-05-30
Well, thanks for your help!  I'm just going to use aptitude and see how it goes.  I backed up my files a while ago, so...

Note to self:  plan upgrades

---

### Post by Pumalite on 2008-05-30
A clean install beats them all.

---

### Post by soluphobe on 2008-05-30
Yeah.  Clean installs are easy compared to updates (for me).

I've botched a few updates, including one that took place locked in a briefcase with a race between the updater and the battery life.  I'm thinking of ditching the hardware (it was low-end about 2 yrs ago) and getting a machine with a nice big hard drive so that I don't have to store everything on 15 gigs.

---

### Post by Pumalite on 2008-05-30
I've done a couple of upgrades, to test them and with good results. But all my 4 working Hardies are clean install.

---

### Post by soluphobe on 2008-05-30
Well, aptitude finished.  I rebooted into the recovery and I tried to fix it up with your commands.  They failed (but only because of WiFi), but there were a relatively few number of errors, so it got to the bit where it tries to download new packages.

So I'll remember your commands - they look like they're working, but my lack of WiFi is irksome.

And I've got the Hardy Recovery Menu, so I think the upgrade was technically successful.  I'm calling it solved ;) Thanks!

---

### Post by soluphobe on 2008-05-31
Update:  Here's how I fixed it:

1.  Hijack ethernet cable from a local computer
2:  Log into an xterm session, then run:```
sudo ifconfig eth0 up
sudo dpkg --configure -a
sudo apt-get -f install #this gave me a 'no need' message
sudo apt-get upgrade    #this also said 'all fine'
sudo shutdown -r now

```
3:  Log back into an X session
4:  ...
5:  Profit!

Pumalite:  Thanks so much for your commands - they fixed my system!

---

### Post by Pumalite on 2008-05-31
Cheers!

---

