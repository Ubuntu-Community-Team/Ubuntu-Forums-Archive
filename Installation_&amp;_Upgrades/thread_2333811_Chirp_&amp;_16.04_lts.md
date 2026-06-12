---
title: "Chirp &amp; 16.04 lts"
date: 2016-08-13
forum: Installation &amp; Upgrades
---

### Post by David2009 on 2016-08-13
Hello.  I recently upgraded 14.04 t0 16.04.  I have been trying to put CHIRP back on to the laptop, so I can program one of my amateur radios.  

Bottom line up front: I received a message saying that an error is not able to be reported. 

I am going to post the output, and I hope that someone can teach me what went wrong.  Thank you.

```
david@david-Satellite-A305:~$ sudo apt-add-repository ppa:dansmith/chirp-snapshots
[sudo] password for david: 
 
 More info: [https://launchpad.net/~dansmith/+archive/ubuntu/chirp-snapshots](https://launchpad.net/~dansmith/+archive/ubuntu/chirp-snapshots)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmprxx_altg/secring.gpg' created
gpg: keyring `/tmp/tmprxx_altg/pubring.gpg' created
gpg: requesting key 3BC5163F from hkp server keyserver.ubuntu.com
gpg: /tmp/tmprxx_altg/trustdb.gpg: trustdb created
gpg: key 3BC5163F: public key "Launchpad PPA for Dan Smith" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
david@david-Satellite-A305:~$ sudo apt-get update
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Hit:3 [http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu](http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu) xenial InRelease
Ign:4 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease               
Hit:5 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release                 
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]
Hit:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [314 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [310 kB]
Fetched 814 kB in 2s (350 kB/s)                            
Reading package lists... Done
david@david-Satellite-A305:~$ sudo apt-get install chirp-daily
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcdaudio1 libdirectfb-1.2-9 libenca0 libfaac0 libmpcdec6 libslv2-9
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  python-suds
The following NEW packages will be installed:
  chirp-daily python-suds
0 upgraded, 2 newly installed, 0 to remove and 6 not upgraded.
Need to get 530 kB of archives.
After this operation, 3,410 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu](http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu) xenial/main amd64 chirp-daily amd64 20160813~xenial~1 [385 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 python-suds all 0.7~git20150727.94664dd-3 [146 kB]
Fetched 530 kB in 0s (1,082 kB/s)    
Selecting previously unselected package python-suds.
(Reading database ... 231382 files and directories currently installed.)
Preparing to unpack .../python-suds_0.7~git20150727.94664dd-3_all.deb ...
Unpacking python-suds (0.7~git20150727.94664dd-3) ...
Preparing to unpack .../chirp-daily_20160813~xenial~1_amd64.deb ...
Unpacking chirp-daily (20160813~xenial~1) ...
dpkg: error processing archive /var/cache/apt/archives/chirp-daily_20160813~xenial~1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/chirpw', which is also in package chirp 1:20160110-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/chirp-daily_20160813~xenial~1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by howefield on 2016-08-13
Try uninstalling the existing chirp installation before installing the chirp-daily package.

```
sudo apt remove chirp
```

---

### Post by David2009 on 2016-08-13
Thank you for the suggestion.  I just deleted & reinstalled.  Now, I'll restart and let you know how it turns out.

---

### Post by howefield on 2016-08-13
> **David2009 said:**
> Thank you for the suggestion.  I just deleted & reinstalled.  Now, I'll restart and let you know how it turns out.

Should be fine, I tested it.

Fingers crossed :)

---

### Post by David2009 on 2016-08-13
I ran away to try out your suggestion before I saw your next note.  

Yes, your suggestion worked perfectly.  Thank you very much.  My HT now has United Kingdom frequencies programmed, and I'm listening away.

Have a nice weekend.

David

---

### Post by howefield on 2016-08-13
Glad to hear it, seems that you had chirp installed previously which was carried through on upgrade to 16.04. Installing chirp-daily required chirp to be uninstalled first. You could probably have used the forceoverwite option but things start to get messy.

Happy listening :)

---

