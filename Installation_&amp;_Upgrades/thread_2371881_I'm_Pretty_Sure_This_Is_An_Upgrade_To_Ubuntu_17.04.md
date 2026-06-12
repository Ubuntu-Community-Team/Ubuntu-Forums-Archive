---
title: "I'm Pretty Sure This Is An Upgrade To Ubuntu 17.04"
date: 2017-09-19
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2017-09-19
Hi all, for the past three days I've gotten this message after running a ```
sudo apt-get update
```

I'm pretty sure it's the 17.04 upgrade.  The problem is after I click to install it tells me there isn't enough disk space.  I'm using a 1 TB HDD which hasn't even used half of it's space!  Are there any ideas on how to free up the minimal space for it?

---

### Post by Bucky Ball on 2017-09-19
Try this:

```
sudo apt autoremove
sudo apt update
```

There is NO WAY the 'sudo apt update' command will upgrade your release from one to the next. A couple of questions.

* Are you actually wanting to upgrade to 17.04? If so, why? I would presume you are running 16.04 LTS. Is there a problem? That is supported until April 2021. 17.04 is supported until next January.
* What makes you think that the command you gave will upgrade your release to 17.04? 

Just one more note: the terminal update command does not open the Software Update GUI so I presume you are doing that manually to show us.

For a full update/upgrade of your current release (not an upgrade to a newer release) use these commands.
```

sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Let us know if you get any errors. Autoremove may not be enough to free up the space you need so further measures required.

---

### Post by shane_faulkinbury2 on 2017-09-19
I guess what I should of asked is how I make the Boot and Grub space larger?

---

### Post by vasa1 on 2017-09-19
Post the output of```
df -h
```

---

### Post by shane_faulkinbury2 on 2017-09-19
```
~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         7.8G     0  7.8G   0% /dev
tmpfs                        1.6G  9.5M  1.6G   1% /run
/dev/mapper/ubuntu--vg-root  901G  265G  590G  31% /
tmpfs                        7.8G  5.5M  7.8G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda2                    473M  443M  5.7M  99% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        1.6G   72K  1.6G   1% /run/user/1000

```

---

### Post by vasa1 on 2017-09-19
And what does```
dpkg -l | grep -i "ii  linux-headers" | cut -c -80
```show?

---

### Post by oldos2er on 2017-09-19
17.04 is not an LTS. LTS versions are only released in even-numbered years, so the next one will be 18.04 LTS.

And no, the screenshots you posted show updates are available for your current Ubuntu version/apps, not a version upgrade.

---

### Post by shane_faulkinbury2 on 2017-09-19
oldos2er, then why can I run a sudo apt-get update fine, but not this?

```
~$ dpkg -l | grep -i "ii  linux-headers" | cut -c -80
ii  linux-headers-4.10.0-27                     4.10.0-27.30~16.04.2            
ii  linux-headers-4.10.0-27-generic             4.10.0-27.30~16.04.2            
ii  linux-headers-4.10.0-28                     4.10.0-28.32~16.04.2            
ii  linux-headers-4.10.0-28-generic             4.10.0-28.32~16.04.2            
ii  linux-headers-4.10.0-30                     4.10.0-30.34~16.04.1            
ii  linux-headers-4.10.0-30-generic             4.10.0-30.34~16.04.1            
ii  linux-headers-4.10.0-32                     4.10.0-32.36~16.04.1            
ii  linux-headers-4.10.0-32-generic             4.10.0-32.36~16.04.1            
ii  linux-headers-4.10.0-33                     4.10.0-33.37~16.04.1            
ii  linux-headers-4.10.0-33-generic             4.10.0-33.37~16.04.1            
ii  linux-headers-4.10.0-35                     4.10.0-35.39~16.04.1            
ii  linux-headers-4.10.0-35-generic             4.10.0-35.39~16.04.1            
ii  linux-headers-4.8.0-58                      4.8.0-58.63~16.04.1             
ii  linux-headers-4.8.0-58-generic              4.8.0-58.63~16.04.1             
ii  linux-headers-generic-hwe-16.04             4.10.0.35.37    
```

---

### Post by vasa1 on 2017-09-19
Have you told us what you see when you run```
sudo apt-get autoremove
```as suggested by BuckyBall in the second post?

---

### Post by shane_faulkinbury2 on 2017-09-20
Thanks BuckyBall for the recommendation!  It seems to have done the trick.  I, however, do not get the update message now, so who knows if more space was created?  I'll keep this open until the end of the week unless I get more errors.  Oh yeah, thanks also vasa1, for looking into this.

---

### Post by vasa1 on 2017-09-20
> **shane_faulkinbury2 said:**
> ...  so who knows if more space was created? ...

Run ```
df -h
```again and compare!

---

