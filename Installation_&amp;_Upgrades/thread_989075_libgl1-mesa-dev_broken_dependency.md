---
title: "libgl1-mesa-dev broken dependency"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by VHans on 2008-11-21
Since upgrading to 8.10 (amd64) I have a problem with a broken package (libgl1-mesa-dev).
I tried to repair the dependency using apt-get -f install but then I get following error:

```
root@Foton:/home/hans# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgl1-mesa-dev
The following packages will be upgraded:
  libgl1-mesa-dev
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29,8kB of archives.
After this operation, 8192B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 243142 files and directories currently installed.)
Preparing to replace libgl1-mesa-dev 7.0.3~rc2-1ubuntu3 (using .../libgl1-mesa-dev_7.2-1ubuntu2_all.deb) ...
Unpacking replacement libgl1-mesa-dev ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dev_7.2-1ubuntu2_all.deb (--unpack):
 error creating symbolic link `./usr/lib/libGL.so': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-dev_7.2-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Foton:/home/hans# 


```

The file /usr/lib/libGL.so does exist on my system, but I am not sure about the '.' in './usr/lib/libGL.so' in the error message. Should it be there?

---

### Post by dstew on 2008-11-21
It is possibly an error in the dpkg install script. The 'dot' means 'the current directory'. So, if the directory the script is running from is anything other than the root directory, the script might fail that way. Try changing to the root directory, and running the installer from there.```

cd /
apt-get -f install
```Just a guess.

---

### Post by VHans on 2008-11-22
> **dstew said:**
> It is possibly an error in the dpkg install script. The 'dot' means 'the current directory'. So, if the directory the script is running from is anything other than the root directory, the script might fail that way. Try changing to the root directory, and running the installer from there.```

cd /
apt-get -f install
```Just a guess.

I already tried running apt-get from / but it gives the same error. As you say, the reference to the current directory is probably a bug in the install scripts. Am I the only one who has a problem with this?

---

### Post by dkavraal on 2010-11-25
if this problem emerges for any of the users here is what happened for me:

The point is I have an intel 855gm onboard and had installed not-yet-supported package for driver, when first I was using 10.04. I upgraded to 10.10. Then realized Ubuntu dist-update had had edited my sources list for synaptic. I wanted to install libgl1-mesa-dev but reasoning broken dependency it was rejected. 

I added the repos as refered at [1]. And the broken dependencies resolved. I could install.

just:
sudo add-apt-repository ppa:glasen/intel-driver 
sudo add-apt-repository ppa:glasen/855gm-fix
sudo apt-get update

thats it.

[1] [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by bbotee on 2011-05-27
Thank you soooo much! I almost gave up due to the broken packages but this finally solved my problem! Thanks again!

---

### Post by olawlor on 2011-08-25
Another way to work around this error is to:

sudo mkdir /usr/lib/nvidia/
sudo touch /usr/lib/nvidia/libGL.so.xlibmesa

And then try the install again.  This looks like a very stupid bug in the libgl1-mesa-dev script, trying to undo the NVIDIA libGL.  Works fine, unless you've never had an NVIDIA driver on your machine!

---

