---
title: "Installing Version 12.04"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by meuser1 on 2013-03-06
Hi
I got my Dell Vostro 2520 few days back with Ubuntu 11.10.
I would like to know how I can install Ubuntu 12.04 either fresh (no important data as of now to backup) or as an upgrade as I need to install some software which runs only 12.04. 

I tried to upgrade using update manager and I am getting an error like 'Authentication failed. there might be a problem with the server or with the network'. Not sure what this means and how to resolve.
I tried to run from command line and I got some messages as attached in the text file.
Particularly in the last line I got an error saying  
"E:Some index files failed to download. They have been ignored, or old ones used instead."

Can some one help me in this. Desparately looking for a solution. 
Thanks in advance

---

### Post by fballem on 2013-03-06
Hi,

I've been using ubuntu for a few years. As a general rule, if I want to change to a new version, I will do a clean installation off of a CD or DVD (depends on the release). If you download and burn the latest release of 12.04, it will be 12.04.2, which installed on my PC with no issues.

The following link contains additional information and suggestions that may be helpful: [https://wiki.ubuntu.com/fballem/Software%2012.04](https://wiki.ubuntu.com/fballem/Software%2012.04)

Your laptop has Intel graphics, not nVidia graphics, so please ignore any instructions that relate to the nVidia drivers.

Hope this is of some help to you,

---

### Post by dino99 on 2013-03-06
for a fresh installation:
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

for an upgrade:

```
sudo gedit /etc/apt/sources.list
```
there, change "oneiric" by "precise", then

```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

---

### Post by meuser1 on 2013-03-06
@dino99
Thanks for your inputs. I tried to save the changes in the sources.list, but I could not as the file has only read permission and the file is owned by root.
How can I change this permission. I think this is the reason the upgrade is failing. Any suggestions?

---

### Post by meuser1 on 2013-03-06
One more observation from my side
I also saw that 'Trusted software providers' list under the tab 'Authentication' in update manage utility is blank. Not sure whether the Authentication failed error is due to this.

---

### Post by fantab on 2013-03-06
Did you use "SUDO" in 

```
$ sudo gedit /etc/apt/sources.list
```

?

---

### Post by meuser1 on 2013-03-06
Hi
This is what I could see
sudo gedit /etc/apt/sources.list
[sudo] password for meuser: 


(gedit:4444): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.8Z8LTW': No such file or directory


(gedit:4444): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by darkod on 2013-03-06
That error is not important, gedit opens in new window.

But anyway, since you said there is no data to backup, just do a new clean 12.04 LTS installation. Much better than upgrading.

---

### Post by meuser1 on 2013-03-06
How can I proceed with clean installation. The update manager is not recognizing the CD image (I just burnt the DVD after download)
Should I use the setup option while booting my laptop or there are any other options

---

### Post by darkod on 2013-03-06
You need to boot the computer with the cd/dvd. Update manager has nothing to do with it.

Make sure the optical drive is the first device to boot in bios, or use the computer boot menu if it has one (usually by pressing F12 during boot). After it boots from the cd it will ask you if you want to Try or Install. You might as well select Try one time to see if it will load the live desktop correctly on your hardware. There is Install icon on the desktop to install from live mode.

---

