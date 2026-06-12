---
title: "Couldn't find any package by regex!!"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by cousinlucky on 2012-09-25
A sudo apt-get install ( file ) gets me a Couldn't find any package by regex!! I'm trying to install wvdial so that I ca access the internet. Can anyone help me out with this? Thanks!

---

### Post by lukeiamyourfather on 2012-09-25
What version of Ubuntu? Your profile says 8.04 LTS, is that still the case?

---

### Post by cousinlucky on 2012-09-25
No, I installed 12.04 and I'm trying to install a wvdial so I can get onto the internet with it.

---

### Post by Bashing-om on 2012-09-25
cousinlucky;

  The wvdial package is available in the repository. Just search for "wvdial" in your ubuntu package manager of choice; select install and it is done. Been a Long time since I used this package, but was no problem to set up (config files) and worked well (seems like back in version 9.04).

[INDENT][INDENT]hth <==BDQ

[/INDENT][/INDENT]

---

### Post by drmrgd on 2012-09-25
That package is definitely in the repository:

```
$ sudo apt-cache showpkg wvdial
Package: wvdial
Versions: 
1.61-4build1 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
                  MD5: b8bf30c8dfd4d09e02af74bf497505d6
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: b8bf30c8dfd4d09e02af74bf497505d6


Reverse Depends: 
  wvdial:i386,wvdial
  wader-core,wvdial
  lubuntu-desktop,wvdial
  ichthux-desktop,wvdial
  gnome-ppp,wvdial
  usb-modeswitch,wvdial
Dependencies: 
1.61-4build1 - ppp (2 2.3.0) debconf (18 0.5.00) cdebconf (0 (null)) libc6 (2 2.4) libstdc++6 (2 4.1.1) libuniconf4.6 (0 (null)) libwvstreams4.6-base (0 (null)) libwvstreams4.6-extras (0 (null)) debconf (18 0.5) debconf-2.0 (0 (null)) wvdial:i386 (0 (null)) 
Provides: 
1.61-4build1 - 
Reverse Provides: 
```

Dumb question: is the computer on which you're trying to apt-get the package connected to the internet, or are you getting it on a different computer and then transferring it?  You won't be able to get packages from the repository without an internet computer.  

Also, what are the results of:

```
sudo apt-get update
```

That will confirm that you can query the repository and have the appropriate ones setup in your sources.list

---

### Post by cousinlucky on 2012-09-25
Gentlemen, I am on the internet using an Antix distro that is on my computer. What I am trying to do is to install wvdial into the Ubuntu 12.04 distro that is also installed onto my computer.

What I need to find out is how to put wvdial into Ubuntu without the on-line package manager!!

---

### Post by josephmills on 2012-09-25
Might work
mount the drive to mnt or something and move the debian package over to the partition that you mounted (12.04) then chroot into the mounted partition and install with dpkg 

```

sudo fdisk -l 

```

Find the partition & mount make sure that 1200 is the correct number like 3 or 4 what ever fdisk says about what partition Ubuntu is  
```
mount /dev/sda12000/mnt
```

move/cp the files

```
cp something.deb /mnt/home/someone/some/place
```

chroot in or just boot Ubuntu then use

```
dpkg -i something.deb
```

Hope this helps

---

### Post by drmrgd on 2012-09-25
> **cousinlucky said:**
> Gentlemen, I am on the internet using an Antix distro that is on my computer. What I am trying to do is to install wvdial into the Ubuntu 12.04 distro that is also installed onto my computer.

What I need to find out is how to put wvdial into Ubuntu without the on-line package manager!!


Ahhhh....that's the missing piece and why apt is not working.  You can't use apt if you're not yet online (a bit of a catch22).  You can download packages for offline installation, although the potential problem is if the package requires extra dependencies, you might have a heck of a time getting it all put together.  

Just saw the post from Joseph Mills...that should work, given you don't need any extra dependencies.

---

### Post by cousinlucky on 2012-09-25
A very good friend sent me a disk containing wvdial and the dependencies. I have extracted them onto Ubuntu 12.04 but the command sudo apt-get install does not install them. Is there another terminal command available to get them installed??

---

### Post by josephmills on 2012-09-25
> **drmrgd said:**
>   

Just saw the post from Joseph Mills...that should work, given you don't need any extra dependencies.


And boy is there :)

---

### Post by oldos2er on 2012-09-25
> **cousinlucky said:**
> A very good friend sent me a disk containing wvdial and the dependencies. I have extracted them onto Ubuntu 12.04 but the command sudo apt-get install does not install them. Is there another terminal command available to get them installed??

If all the *deb files are in one folder, run ```
sudo dpkg -i *.deb
``` from within that folder.

---

### Post by cousinlucky on 2012-09-26
Thanks Everyone!!  I have finally successfully installed the files using the terminal!! However I can not find the files to set up and use the dial up configuration.  Now I need to find out just where the engineers hid the thing.

---

### Post by drmrgd on 2012-09-26
That's great!  After seeing the dependency tree that Joseph Mills posted, I thought this was going to be one heck of a feat.  Glad to see that you got it working.

I had a quick look just to confirm, and it indeed looks like the configuration file is in /etc/wvdial.conf.  This was just the first link that Google pulled for me.  Looks reasonable enough to get you started, though:

[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)

---

### Post by cousinlucky on 2012-09-26
Personally, i think it is unnecessary to make users use a terminal to set up a dial up connection. After I set up the pppconfig and the gpasswd I was supposed to be able to access the internet in the terminal with pon. Instead i get notified  of unrecognized option ' /dev/modem '.

the setup asked for the modem port which I provided. Is there something that I left out??

---

### Post by cousinlucky on 2012-09-27
My humble " Thank You " to everyone that helped me with this, I finally got the modem to work but it took another hour to find the typing error that I had made changing text files that prevented my access to the internet. I have 135 updates to upload and I will surely spend a lot of time trying to figure Ubuntu 12.04 out.

I do not have enough posts registered to change my profile to indicate that Antix 12 and Ubuntu 12.04 are the os on my computer at present!

---

