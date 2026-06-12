---
title: "Unable to update 16.04.6 LTS"
date: 2019-12-18
forum: Installation &amp; Upgrades
---

### Post by oygle on 2019-12-18
Haven't been able to update for a few weeks now. The update only has errors from Brave browser ..

```
$ sudo apt-get update
```

> Err:1 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) xenial InRelease                                                                                                  
  The following signatures were invalid: KEYEXPIRED 1555193394  KEYEXPIRED 1555193394  KEYEXPIRED 1555193433  KEYEXPIRED 1555193433  KEYEXPIRED 1555193394  KEYEXPIRED 1555193394  KEYEXPIRED 1555193433  KEYEXPIRED 1555193394  KEYEXPIRED 1555193394  KEYEXPIRED 1555193433
Hit:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial InRelease                                                                                                             
Hit:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates InRelease                                                                                                     
Ign:5 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 InRelease                                                                                                               
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease                                                                                                      
Hit:7 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 Release                                                    
Hit:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                           
Hit:2 [https://nchc.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](https://nchc.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all InRelease
Hit:10 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) xenial InRelease    
Hit:11 [http://ppa.launchpad.net/gabor-karsay/parlatype/ubuntu](http://ppa.launchpad.net/gabor-karsay/parlatype/ubuntu) xenial InRelease 
Hit:12 [http://ppa.launchpad.net/mc3man/xerus-media/ubuntu](http://ppa.launchpad.net/mc3man/xerus-media/ubuntu) xenial InRelease     
Hit:13 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) xenial InRelease              
Hit:14 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease   
Reading package lists... Done 
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) xenial InRelease: The following signatures were invalid: KEYEXPIRED 1555193394  KEYEXPIRED 1555193394  KEYEXPIRED 1555193433  KEYEXPIRED 1555193433  KEYEXPIRED 1555193394  KEYEXPIRED 1555193394  KEYEXPIRED 1555193433  KEYEXPIRED 1555193394  KEYEXPIRED 1555193394  KEYEXPIRED 1555193433
W: Failed to fetch [https://brave-browser-apt-release.s3.brave.com/dists/xenial/InRelease](https://brave-browser-apt-release.s3.brave.com/dists/xenial/InRelease)  The following signatures were invalid: KEYEXPIRED 1555193394  KEYEXPIRED 1555193394  KEYEXPIRED 1555193433  KEYEXPIRED 1555193433  KEYEXPIRED 1555193394  KEYEXPIRED 1555193394  KEYEXPIRED 1555193433  KEYEXPIRED 1555193394  KEYEXPIRED 1555193394  KEYEXPIRED 1555193433
W: Some index files failed to download. They have been ignored, or old ones used instead.

Then the upgrade keeps giving me this error on a vlc dependency

```
sudo apt-get upgrade
```

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 vlc : Depends: vlc-bin (= 2.2.8-2~xenial3) but it is not installed
E: Unmet dependencies. Try using -f.

So I try this ..

```
sudo apt-get -f install vlc-bin
```

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavdevice-ffmpeg56 libdbd-mysql-perl libdbi-perl libdirectfb-1.2-9 liblircclient0 liblivemedia50 libreadline5 libterm-readkey-perl libudev1:i386 mariadb-common
  vlc-nox
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  vlc-bin
0 to upgrade, 1 to newly install, 0 to remove and 80 not to upgrade.
52 not fully installed or removed.
Need to get 0 B/159 kB of archives.
After this operation, 387 kB of additional disk space will be used.
(Reading database ... 241346 files and directories currently installed.)
Preparing to unpack .../vlc-bin_2.2.8-2~xenial3_amd64.deb ...
Unpacking vlc-bin (2.2.8-2~xenial3) ...
dpkg: error processing archive /var/cache/apt/archives/vlc-bin_2.2.8-2~xenial3_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/cvlc', which is also in package vlc-nox 2.2.2-5ubuntu0.16.04.4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vlc-bin_2.2.8-2~xenial3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by oygle on 2019-12-18
Found a similar issue at [https://askubuntu.com/questions/148383/how-to-resolve-dpkg-error-processing-var-cache-apt-archives-python-apport-2-0](https://askubuntu.com/questions/148383/how-to-resolve-dpkg-error-processing-var-cache-apt-archives-python-apport-2-0)

So, did this ..

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/vlc-bin_2.2.8-2~xenial3_amd64.deb
sudo apt-get -f install vlc-bin
sudo apt-get update
sudo apt-get upgrade
```

and it all looks fine now.  :)

---

### Post by Impavidus on 2019-12-19
That's a dirty solution. There is no vlc-bin in the official repositories for Ubuntu 16.04, so I don't know where you got it and I don't know where you got that vlc that depends on it.

Your problem with Brave browser seems unrelated.

---

