---
title: "gutsy network installation help needed"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by tr3s on 2008-06-04
hi!

i,ve been trying to follow this howto [http://www.debuntu.org/how-to-unattended-ubuntu-network-install]("http://www.debuntu.org/how-to-unattended-ubuntu-network-install") to set up a computer lab in our school. so far, i'm already successful in loading the installer from the tftp server, but this tutorial requires an internet connection to install from online repositories. what should i do to be able to get files from the local tftp server?

i already tried installing apache and mounted the iso to /var/www, but the installer fails when the repository is set to the local webserver.

hope to hear from you!

tnx,


tr3s

---

### Post by iaculallad on 2008-06-04
If what you mean is getting files from local mirror repository, try looking at this page.

[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

### Post by tr3s on 2008-06-05
setting up a local mirror repository means downloading all files from the internet repository which will surely take much time.

what im looking at is to use the contents of the ubuntu livecd, mount or copy the contents to the server, and use it as the package repository.

in the howto, it is advised to setup apt-cacher, but that i think will also get packages from the internet repository.

---

### Post by iaculallad on 2008-06-05
> **tr3s said:**
> setting up a local mirror repository means downloading all files from the internet repository which will surely take much time.

what im looking at is to use the contents of the ubuntu livecd, mount or copy the contents to the server, and use it as the package repository.

in the howto, it is advised to setup apt-cacher, but that i think will also get packages from the internet repository.

It surely would not take all the time since you are to download the packages to only one PC w/c serves as your local mirror repository to be used by the whole computer lab PC's for their updates. (Nevertheless, you will still be needing a net connection to download Ubuntu updates)

---

### Post by tr3s on 2008-06-05
> *from [http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)*
Please note that you need a fast internet connection to download all the packages to your mirror as well as a lot of hard disk space. In my tests I mirrored the main, contrib, and non-free sections of Debian Sarge and the main, restricted, and universe sections of Ubuntu Edgy Eft which took about 25GB of hard disk space and about 6 hours of download time on a 16MBit DSL line.

for mine, i think it will take forever to download that whole repository :) since we only have 512 kbps line.

do you think using the ubuntu alternate cd will do the work? i already tried using the livecd to no avail.

tnx for your reply

---

### Post by iaculallad on 2008-06-05
> **tr3s said:**
> for mine, i think it will take forever to download that whole repository :) since we only have 512 kbps line.

do you think using the ubuntu alternate cd will do the work? i already tried using the livecd to no avail.

tnx for your reply

That would be the bottle-neck (512kbps). I doubt it, Alternate CD's can be used for upgrades but not updates. Getting updates would still require you for net connection.

---

### Post by tr3s on 2008-06-05
ok. but the task here is deploying ubuntu over the network, and not updating ubuntu

---

### Post by iaculallad on 2008-06-05
> **tr3s said:**
> ok. but the task here is deploying ubuntu over the network, and not updating ubuntu

If that's the case then you'll only be needing (2) files to get w/c is your tftpd-hpa (tftp) and netboot.tar.gz (PXE bootloader) from the net. Try researching if Alternate CD could work with your deployment.

---

### Post by gsker on 2008-06-06
> **tr3s said:**
> setting up a local mirror repository means downloading all files from the internet repository which will surely take much time.

what im looking at is to use the contents of the ubuntu livecd, mount or copy the contents to the server, and use it as the package repository.

in the howto, it is advised to setup apt-cacher, but that i think will also get packages from the internet repository.

I just did this.  Mount the Alternate CD in a location in your http server.  When the install gets to the point where it asks for the country that the mirror is in, scroll all the way to the top and choose manual.

the preseed entries to do this are:
[FONT=Fixedsys]d-i mirror/country string manual
d-i mirror/http/hostname string 10.10.20.1
d-i mirror/http/directory string /ubuntu
[/FONT]

Then tell it where ubuntu is.

---

### Post by tr3s on 2008-06-10
> **gsker said:**
> I just did this.  Mount the Alternate CD in a location in your http server.  When the install gets to the point where it asks for the country that the mirror is in, scroll all the way to the top and choose manual.

the preseed entries to do this are:
[FONT=Fixedsys]d-i mirror/country string manual
d-i mirror/http/hostname string 10.10.20.1
d-i mirror/http/directory string /ubuntu
[/FONT]

Then tell it where ubuntu is.

yeah that's exactly what i did. i set the local server as the repository for the installation but it always failed saying that the repository doesn't contain files needed for installation.

did you get it to work? what i did is mount the cd under /var/www/ubuntu of the ftp/http server and set the client to look for the installation files from the server ```
mirror repository: http://192.168.0.1 (ip of the server
folder: /ubuntu/
```

i plan to manually enter the parameters during installation. maybe i can use a preseed file later when all is working well.

btw, looking at the directory structure of the alternate cd, it's actually the same with the directory structure of online repositories. so i wonder what i still need to do other than just mounting the cd because it doesn't work

---

### Post by xris_xcess on 2008-08-14
Hi:

I've also been setting up a pxe/netinstall environment... and also came up with the whole local repo idea/thing.

One thing that I could not get past was that SOME downloading must be done, at least with my method, although I think that with a bit of tweaking no downloads could be had.

What I did:

Setup dhcp/pxe/tftp server. I used dnsmaq, which gives you ALL three in a lean pkg.

Install apt-cacher on the server. I used the inetd method as it is more efficient (for few clients at least).

Copied ALL of the .debs and .udebs from the ALT_INSTALL_CD to /var/cache/apt-cacher/import

Run sudo /usr/share/apt-cacher/apt-cacher-import.pl

This will import/move all the pkg's from the import dir to the packages dir AND add them to the current apt-cacher database.

Start up your pxeboot-client. When it aks you for the repo directory there are two optins that I tried/worked:

1- Select a regular repo directory:  xx.archive.ubuntu.com, etc. Then when it asks for PROXY information, give it the details of you apt-cacher server ie: IP:PORT.

2 - Construct a repo address base on the instructions on the apt-cacher webpage (yes, I didn't know it untill then, but apt-cacher seems to be a simple webproxy server that only serves apt requests :->). It goe something like this:

              http://yourserver:PORT/apt-cacher/us.archive.ubuntu.com/ubuntu

I'm not 100% sure if that is what I used, since I also got errors to start with ("the repo does not exist or is unavailable", etc). What I did was to check the debug log for the installer. Press alt-ctrl-F4 to see it. There I saw that the installer was adding "/ubuntu/hardy" to my details. After figuring out exactly what to type in repo details I got the install going.

Next time I will use the repo+proxy method, since after the install the repo's on the client are properly constructed instead of a custom proxy+repo hack. In my case it's not really a big deal since I will continue using my apt-cacher server.

I monitored the apt-cacher logs while the install was taking place and from first impression I would say I got around 80% hit rate. That's for a custom-minimal-gnome-desktop install (install cli task and then add xorg, gnome, etc).

If you have several machines, then only the first one will download extra/updated packages from the net. The ones after that will get everything from the apt-cacher server. Plus the fact that your machines will be immediately up to date!

If you go with the webserver-mount-iso way then I would say that the address the installer is constructing based on your address information is wrong. Check the debug messages on the installer for clues. Once I sorted that one out, almost everything went ok.


Xris.

BTW, what kind of preseed file are you using. Im also interested in setting up unatended installs. The kind that you boot with pxe and then come back to a finished setup, including custom package installs.

---

### Post by xris_xcess on 2008-08-17
Hello Again:


I've since migrated from apt-cacher to apt-cacher-ng. I had trouble running apt-cacher, the after a pxe boot, the installing client would stall around 35%, before loading the partition manager. I tracked the problem to a fault in the apt-cacher/inetd combo. My messages log showed a "server looping, shutting down" for inetd. After looking for a bug or something describing this problem, I stumbled on apt-cacher-ng.

It seems to be based on apt-cacher, but with improvements and more native/system tools doing the heavy lifting, plus it includes (or at least seems to) it's own inetd/xinetd server. It has worked well until now, at least with the pxe client retrieving packages for an install. I have yet to stress test its capabilities with multiple machine updating at thee same time.

Xris.

---

