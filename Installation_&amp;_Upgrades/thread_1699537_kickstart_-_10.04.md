---
title: "kickstart - 10.04"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by hyuk48 on 2011-03-03
hi~ there is problem with installation from ubuntu kickstart
 
need information -------------------------------------------------------------------------
1. I made my one local repository. 
 
like this 
 
export GNUPGHOME=/home/mirrorkeyring
arch=amd64
section1=main,restricted,universe,multiverse,main/debian-installer,restricted/debian-installer,universe/debian-installer,multiverse/debian-installer
section2=main,restricted,universe,multiverse
release1=lucid
release2=lucid,lucid-security,lucid-updates
server=de.archive.ubuntu.com
inPath=/ubuntu
proto=http
outPath=/repo/ubuntumirror
debmirror       -a $arch \
                --no-source \
                -s $section1 \
                -h $server \
                -d $release1 \
                -r $inPath \
                --progress \
                --nocleanup \
                -e $proto \
                $outPath
debmirror       -a $arch \
                --no-source \
                -s $section2 \
                -h $server \
                -d $release2 \
                -r $inPath \
                --progress \
                --nocleanup \
                -e $proto \
                $outPath

result ....
 
drwxr-xr-x 5 root root 4096 2011-03-03 23:33 .
lrwxrwxrwx 1 root root   30 2011-03-03 23:33 stable -> /repo/ubuntumirror/dists/lucid
drwxr-xr-x 6 root root 4096 2011-03-03 09:27 ..
drwxr-xr-x 6 root root 4096 2011-03-03 09:27 lucid
drwxr-xr-x 6 root root 4096 2011-03-03 09:27 lucid-security
drwxr-xr-x 6 root root 4096 2011-03-03 09:27 lucid-updates

---------------------------------------------------------------------------------------------------
 
but I failed to install new server 
dhcp & tftpd setting looks good.
what is problem? 
 
below is dubug log for installation.
 
log ----------------------------------------------------------------------------------------------
Mar  4 01:26:14 main-menu[427]: (process:2092): bound to 10.248.225.153 -- renewal in 285 seconds.
Mar  4 01:26:14 main-menu[427]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Mar  4 01:26:14 main-menu[427]: DEBUG: resolver (libc6): package doesn't exist (ignored)
Mar  4 01:26:14 main-menu[427]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Mar  4 01:26:14 main-menu[427]: INFO: Falling back to the package description for console-setup-udeb
Mar  4 01:26:14 main-menu[427]: INFO: Falling back to the package description for console-setup-udeb
Mar  4 01:26:14 main-menu[427]: INFO: Menu item 'network-preseed' selected
Mar  4 01:26:14 preseed: successfully loaded preseed file from [http://10.248.224.88/netinstall/vmware.cfg](http://10.248.224.88/netinstall/vmware.cfg)
Mar  4 01:26:14 main-menu[427]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Mar  4 01:26:14 main-menu[427]: DEBUG: resolver (libc6): package doesn't exist (ignored)
Mar  4 01:26:14 main-menu[427]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Mar  4 01:26:14 main-menu[427]: INFO: Falling back to the package description for console-setup-udeb
Mar  4 01:26:14 main-menu[427]: INFO: Falling back to the package description for console-setup-udeb
Mar  4 01:26:14 main-menu[427]: INFO: Menu item 'choose-mirror' selected
Mar  4 01:26:14 anna-install: Queueing udeb apt-mirror-setup for later installation
Mar  4 01:26:14 choose-mirror[3377]: DEBUG: command: wget -q [http://10.248.224.88/ubuntu/dists/karmic/Release](http://10.248.224.88/ubuntu/dists/karmic/Release) -O - | grep ^Suite: | cut -d' ' -f 2
Mar  4 01:26:14 choose-mirror[3377]: DEBUG: command: wget -q [http://10.248.224.88/ubuntu/dists/stable/Release](http://10.248.224.88/ubuntu/dists/stable/Release) -O - | grep ^Suite: | cut -d' ' -f 2
Mar  4 01:26:14 choose-mirror[3377]: DEBUG: command: wget -q [http://10.248.224.88/ubuntu/dists/lucid/Release](http://10.248.224.88/ubuntu/dists/lucid/Release) -O - | grep ^Codename: | cut -d' ' -f 2
Mar  4 01:26:14 choose-mirror[3377]: INFO: codename set to: lucid
Mar  4 01:26:14 choose-mirror[3377]: DEBUG: command: wget -q [http://10.248.224.88/ubuntu/dists/lucid/main/binary-amd64/Release](http://10.248.224.88/ubuntu/dists/lucid/main/binary-amd64/Release) -O - | grep Architecture
Mar  4 01:26:14 anna-install: Queueing udeb lucid-support for later installation
Mar  4 01:26:14 main-menu[427]: (process:3370): wget: server returned error: HTTP/1.1 404 Not Found
Mar  4 01:26:14 main-menu[427]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Mar  4 01:26:14 main-menu[427]: DEBUG: resolver (libc6): package doesn't exist (ignored)
Mar  4 01:26:14 main-menu[427]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Mar  4 01:26:14 main-menu[427]: INFO: Falling back to the package description for console-setup-udeb
Mar  4 01:26:14 main-menu[427]: INFO: Falling back to the package description for console-setup-udeb
Mar  4 01:26:14 main-menu[427]: INFO: Menu item 'download-installer' selected
Mar  4 01:26:14 anna[3408]: wget: server returned error: HTTP/1.1 404 Not Found
Mar  4 01:26:14 anna[3408]: cat: can't open '/tmp/net-retriever-3412-deduplicate/*': No such file or directory
Mar  4 01:26:35 anna[3408]: WARNING **: bad d-i Packages file
Mar  4 01:26:35 main-menu[427]: INFO: Menu item 'download-installer' succeeded but requested to be left unconfigured.
Mar  4 01:26:35 main-menu[427]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Mar  4 01:26:35 main-menu[427]: DEBUG: resolver (libc6): package doesn't exist (ignored)
Mar  4 01:26:35 main-menu[427]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Mar  4 01:26:35 main-menu[427]: INFO: Falling back to the package description for console-setup-udeb
Mar  4 01:26:40 main-menu[427]: INFO: Falling back to the package description for console-setup-udeb
Mar  4 01:26:40 main-menu[427]: INFO: Menu item 'save-logs' selected
Mar  4 01:26:49 main-menu[427]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Mar  4 01:26:49 main-menu[427]: DEBUG: resolver (libc6): package doesn't exist (ignored)
Mar  4 01:26:49 main-menu[427]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Mar  4 01:26:49 main-menu[427]: INFO: Falling back to the package description for console-setup-udeb

 
thanks for reading.

---

### Post by Ben Jao Ming on 2011-03-08
It occurs to me that most of the guides for PXE installation/booting Ubuntu are obsolete, so when I'm done with this nightmare, I'll write down a concise guide for it.

Meanwhile, to get you going: You need to add the repository "main/debian-installer" to both lucid-updates and lucid-security -- also, I think "restricted/debian-installer" needs to go in lucid-updates.

The general technique is to look for anything "debian-installer" in a genuine repository and make sure to include it: [http://dk.archive.ubuntu.com/ubuntu/dists/](http://dk.archive.ubuntu.com/ubuntu/dists/)

Good luck and let us know, if you find some other odd, undescribed solutions.

Also, I'm pretty sure that the netboot image in Ubuntu 10.04.1 is broken. Dunno, if you're using that one... my solution was to use the one from 10.04. I still need to confirm if this is a fact.

---

### Post by Ben Jao Ming on 2011-03-08
Btw do use apt-mirror for your mirroring needs... it's probably a lot cleaner to run than what you're doing in your above script.

---

### Post by richard_wu0313 on 2011-04-13
i also met the same error, have you done with your document? may i have a look? thanks

---

### Post by omkar_022 on 2011-04-15
i am in urgent need of the our Document on PXE-BOOT for 10.04  can you send me the document or upload it here.

---

### Post by odonnmi on 2011-10-05
Has any update documentaion been on local network installs?  I seen a number of posts with the following error.  This is the only solution I see,  I added the debian-install repos, but I still get the following error.  Any help would be much appreciated. 

Oct  6 00:12:20 anna[2389]: cat: can't open '/tmp/net-retriever-2429-deduplicate/*': No such file or directory
Oct  6 00:12:22 anna[2389]: WARNING **: bad d-i Packages file

---

### Post by fumarola on 2011-10-07
Hi,

Same error to me too. :(
Is there any solution?

> **odonnmi said:**
> Has any update documentaion been on local network installs?  I seen a number of posts with the following error.  This is the only solution I see,  I added the debian-install repos, but I still get the following error.  Any help would be much appreciated. 

Oct  6 00:12:20 anna[2389]: cat: can't open '/tmp/net-retriever-2429-deduplicate/*': No such file or directory
Oct  6 00:12:22 anna[2389]: WARNING **: bad d-i Packages file

---

### Post by Izachi on 2012-04-12
> **odonnmi said:**
> Has any update documentaion been on local network installs?  I seen a number of posts with the following error.  This is the only solution I see,  I added the debian-install repos, but I still get the following error.  Any help would be much appreciated. 

Oct  6 00:12:20 anna[2389]: cat: can't open '/tmp/net-retriever-2429-deduplicate/*': No such file or directory
Oct  6 00:12:22 anna[2389]: WARNING **: bad d-i Packages file

A little up, I have the same problem and there is no solution on google :(
So please help me to solve this problem :)

Thank you

---

