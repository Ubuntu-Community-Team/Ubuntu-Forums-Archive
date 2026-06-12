---
title: "upgrade via flash drive image - system76"
date: 2015-01-28
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2015-01-28
i have an old system76 laptop with 13.10 on it.  i would like to upgrade it to 14.04 LTS.  but i have an issue.  i do not have continuous net access ... not long enough to use the tool that makes a bootable flash drive over the net.  i could download an image file to my server real fast and/or in the background and then download that over a few days and then image a flash drive with dd.  but i cannot find a downloadable image file.  is there one?  is there one specific to system76 (i have a kudu pro with 2x 1tb drives)?

---

### Post by MAFoElffen on 2015-01-28
"Your" server? Ever thought about setting up a temporary local repo on your server? Just for that? Or maybe longer to support that device, if it's going to have continual problems with normal updates also...

Honestly, I feel you. I have a device that has no wired connection, only wireless. I'm of the old-school thought of not doing upgrades over wireless... So I have a USB Ethernet device that I plug into for upgrades.

---

### Post by Skaperen on 2015-01-29
the server can dowload a whole image with wget (need a URL)  but that server is 2000 miles away.   it can only stage an image file there,  then i would download that to my laptop (OK via wifi this way) with rsync and then dd it to my flash drive plugged into the laptop or play with it in a VM.

i just need a URL for an image file of an image appropriate for my system76 kudu pro laptop (maybe the regular image is good enough).

the server is a dedicated server i rent ... i have never been physically near it.  but it does have Ubuntu.
i also run Ubuntu based instances on AWS.

BTW, to me "multi-boot" means also having another distro or maybe BSD ... not Windows.

---

### Post by sudodus on 2015-01-29
It might work better for you to use ***torrents***. Transmission is a good torrent client. Torrents can work with poor internet connections. The file to get (in this case an ISO file) will be divided into small pieces, each of these pieces will be downloaded and checked and re-downloaded until the check-sum matches, and finally it will be put together to a good copy of the original file.

-o-

I suggest that you send a request directly to System 76. They should know, if there is a special image file. Otherwise they should know how to use a regular ISO file, what tweaks might be necessary (for your computer) at and after installation.

---

### Post by Skaperen on 2015-01-30
how do i find it on torrents?

fyi ... we are limited to connecting to ports 80 and 443 ... does torrent use these?  if not then i can't use it.

---

### Post by Skaperen on 2015-01-30
i have sent a request to system76 and got no reply (several weeks so far) i can try the system76 support forum here next

---

### Post by sudodus on 2015-01-30
> **Skaperen said:**
> how do i find it on torrents?

fyi ... we are limited to connecting to ports 80 and 443 ... does torrent use these?  if not then i can't use it.

examples:

Ubuntu: [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads) scroll down on the page ...

Lubuntu: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu/14.04.1](https://help.ubuntu.com/community/Lubuntu/GetLubuntu/14.04.1)

In ***Transmission*** you can select listening port at
[I]
Edit -- Preferences -- tab Network[/I]

> **Skaperen said:**
> i have sent a request to system76 and got no reply (several weeks so far) i can try the system76 support forum here next

They should reply to their customers. Anyway, good luck at their forum!

-o-

Finally, don't give up here, let us hope another user of system 76 reads this link, knows and can help you :-)

---

### Post by Skaperen on 2015-02-02
FYI & unfortunately the ubuntu.com link only has network installers.  i won't even have any net access during the installs.  so i need a full installer image.

modern flash drives are big enough ... 8GB and up.  but i do realize many people would prefer a smaller image for a faster initial download.  and then they would have t wait through a slow install .... nicer where there is really fast internet such as installing servers in a data center.  just thinking that full install images should be readily available.

---

### Post by Skaperen on 2015-02-02
the system76 support site links to an ubuntu.com page to gbuild an image so there may notbe a special image for system 76 ... their drivers may already be in ubuntu or the kernel.

i found an image at the ANL.gov rsync site so i can down load it in parts directly using rsync. i'll do that and try it if system76 never answers.  i can try the LIVE MODE first to see if the right drivers are there ... if that looks good they probably are.

---

### Post by sudodus on 2015-02-02
> **Skaperen said:**
> FYI & unfortunately the ubuntu.com link only has network installers.  i won't even have any net access during the installs.  so i need a full installer image.

Look further down on that page. At least I see *a header for netboot* and below that *a header for torrents* and below that header several links to *desktop* iso files and *server* iso files (not network installers alias mini.iso files).
> 
modern flash drives are big enough ... 8GB and up.  but i do realize many people would prefer a smaller image for a faster initial download.  and then they would have t wait through a slow install .... nicer where there is really fast internet such as installing servers in a data center.  just thinking that full install images should be readily available.

Maybe we are misunderstanding each other. What kind of full install images are you thinking about?


1. Standard desktop iso files, typically within 600 MB - 1.2 GB, from which you run the installer and install Ubuntu - example:

[http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-desktop-amd64.iso](http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-desktop-amd64.iso)

and the corresponding torrent file:

[http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-desktop-amd64.iso.torrent](http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-desktop-amd64.iso.torrent)


2. A really big desktop iso file, from which you run the installer and install - example:

[http://ftp.uni-kl.de/pub/linux/knoppix-dvd/](http://ftp.uni-kl.de/pub/linux/knoppix-dvd/), approximately 4 GB.

But there are so many software packages available for installation into Ubuntu, that it is not possible to create something like a 'full Ubuntu install image' if you mean that 'all' interesting software should be there. You might find some community re-spins with such systems, but I think the vast majority of people use the standard iso file to install a basic Ubuntu desktop system, and then they add whatever software they want.


3. There is also a license limit: Some software is allowed for installation by the end user, but not allowed to be distributed by Ubuntu.


4. A compressed image of a portable installed system, that you can clone to several computers, and that will work as it is without any further tweaking unless the particular computer needs a proprietary driver for the graphics card or wifi card - examples:

[http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu-UEFI-n-BIOS-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_Ubuntu-UEFI-n-BIOS-7.8GB.img.xz)

[http://phillw.net/isos/one-button-installer/dd_images/dd_blank-obi_7.8GB_27_LubuntuTrusty.img.xz](http://phillw.net/isos/one-button-installer/dd_images/dd_blank-obi_7.8GB_27_LubuntuTrusty.img.xz)

5. A compressed tarball of a portable installed system, that you can expand into several computers, and that will work as it is without any further  tweaking unless the particular computer needs a proprietary driver for  the graphics card or wifi card - examples:

[http://phillw.net/isos/linux-tools/OBI/trusty/tarballs/lxle32-12.04.4-oem1.tar.xz](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs/lxle32-12.04.4-oem1.tar.xz)

[http://phillw.net/isos/linux-tools/OBI/trusty/tarballs/Bento12.04.04-oem1.tar.xz](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs/Bento12.04.04-oem1.tar.xz)

---

### Post by MAFoElffen on 2015-02-02
They used to do the Alternate Install ISO, from which you could install without a bet connection. We used to use it as a local repo. Ubuntu doesn't do that ISO anymore, but Lubuntu does.

I looked for DVD images of the repo to use as local, if you don't do that yourself (like I mentioned previously), there is a pay version, that takes 10 DVD's.

---

