---
title: "CD hangs during 7.04 server installation"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by opentechmedia on 2007-06-27
Hello,

I am trying to make a fresh install of Ubuntu 7.04 server edition.

I was able to install 6.06 without any problems and did not know how to upgrade from 6.06 to 7.04 and as I do not have too much data on the server yet, I decided to do a fresh install.

During installation, after going through the Language and the keyboard screens, the system starts retrieving files from the CD. After it has finished 5% it stops for a long time and shows that it is trying to retrieve binutils-static-udeb . After that it gives an error saying that the CD integrity might not be good.

I therefore downloaded the iso from another mirror in US and created another CD and started the install. The cd stopped exactly at the same point.

My server is an IBM xSeries 360 dual XEON 1.5 GHz with 3 GB RAM and 3 * 36 GB SCSI HDD. So I am thinking while this is an old server, I think it is adequate to run 7.04.

Any suggestions?

Thanks and regards,

Jeet.

---

### Post by Pumalite on 2007-06-27
You might want to give 'Alternate CD' a try because it gives you more options and it's better at detecting and configuring your hardware.

---

### Post by Gremlinzzz on 2007-06-27
Sounds like its having a problem reading the cd.I would try a new cd.even rewrite's ware out or make sure your computers eye is clean see if it can read other cds.

---

### Post by opentechmedia on 2007-06-27
Thanks for the replies.

I tried to download the alternate CD - but whenever I select Server and 7.04 and check mark the box to download the alternate CD, the server sends me the same file. I looked up the releases at [http://mirrors.kernel.org/ubuntu-releases/feisty/](http://mirrors.kernel.org/ubuntu-releases/feisty/) and saw that the alternate does not say if it is server or desktop. So will it install the server version with the alternate CD?

About the CD eye, it enabled me to install the 6.06 version without any problems. Also, how would the CD crash at exactly the same point?

Finally, I downloaded the [winMd5Sum]("http://www.nullriver.com/index/products/winmd5sum") utility and checked the same against those posted online at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and they do not match.

So is the file getting corrupted during download? I do see on the above site that the file size is 492 MB and my file sizes are also the same. So looks like it is getting downloaded and burnt on the CD and making the CD bootable. 

I guess the easiest way might be to try the alternate CD  - just need to know if it will install the server version also.

Thanks.

---

### Post by Pumalite on 2007-06-27
I'm not sure, but after what you posted about checksum, I would download a new iso first. Torrent is better than HTTP or FTP. Even then your only option might turn out to be the 'Alternate CD' after all, and at least you end up with a workable Ubuntu install. As for the server option: google it to death and you might find the answer. If I'm wrong, somebody else will jump in and correct me. So, be patient and don't give up.

---

### Post by opentechmedia on 2007-06-28
Thank you.

I decided to go the upgrade route.

I upgraded by system from 6.06 to 6.10 and then from 6.10 to 7.04. Took me quite a while, but it is not working fine.

I used the official upgrade mechanism mentioned elsewhere on the forums of running a command in terminal to invoke the upgrade manager and follow the wizard.

Thanks for your help.

---

