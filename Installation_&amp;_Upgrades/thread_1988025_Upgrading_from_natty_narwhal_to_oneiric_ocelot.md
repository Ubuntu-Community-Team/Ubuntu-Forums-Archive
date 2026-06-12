---
title: "Upgrading from natty narwhal to oneiric ocelot"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by 3v3rgr33n on 2012-05-26
Hi

I have problems upgrading. I'm currently using Natty, Ubuntu 11.04 and I want to upgrade to 11.10 but my update manager does not want to detect new releases. The only advice I've had so far is to change my settings in the update manager. I was told to set "Release upgrade" to "Normal releases" but that didn't help.

I also did the following:
```
sudo do-release-upgrade
```
That didn't help
 and I did the following:
```
update-manager -c
```
Still hasn't helped

Thanx in advance

---

### Post by mörgæs on 2012-05-27
You already have trouble with upgrading to 11.10, and after that you might want to upgrade again to 12.04... 

Have you thought of a fresh 12.04 install?

---

### Post by irv on 2012-05-27
First make sure your 11.04 is up to date. Do these commands from a terminal.
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

---

### Post by 3v3rgr33n on 2012-05-28
> **mörgæs said:**
> You already have trouble with upgrading to 11.10, and after that you might want to upgrade again to 12.04... 

Have you thought of a fresh 12.04 install?

Lol, I don't want to use 12.04 just yet. I like being one step behind.

With regards to ```
sudo apt-get update
sudo apt-get upgrade
```

That was the first I tried doing before asking for help... It didn't work.

---

### Post by irv on 2012-05-28
One other thing you can try. Download the iso file and burn a CD/DVD. When you do a fresh install pick the same partition you have the older version on but do this. Do not format and make sure you use the same user name and password. This will install over the old version but keep all your home directory files in tack. I have done upgrades in the past this way. It's called a dirty install, but it works if you follow these steps.
(The importance is) No format, and using the same name and password.

---

### Post by Rex Bouwense on 2012-05-28
irv,  If this works I have wasting a great deal of time backing up stuff and then re-installing it.  I wish I had known about this.

---

### Post by irv on 2012-05-28
> **Rex Bouwense said:**
> irv,  If this works I have wasting a great deal of time backing up stuff and then re-installing it.  I wish I had known about this.

It's still a good practice to backup data to be safe. I learn this trick some years ago in a howto. I looked for it, but couldn't fine it.
I actually do things a little different now. I keep all my files in a folder in ubuntuone, and make a list of all the apps I have installed and do a clean install and then reinstall all the apps. I find things run much better with less problems. I do a lot of alpha/beta testing on new releases so it seems I am doing installs all the time. I also keep an extra hard drive for testing and just swap it out. It's only a matter of removing six screws in my laptop and I can swap the drives out. I also test some distros on pen drives.
With all the installs I've done, I always come back to Ubuntu with Unity.

---

