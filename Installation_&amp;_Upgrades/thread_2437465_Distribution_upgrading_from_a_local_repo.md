---
title: "Distribution upgrading from a local repo"
date: 2020-02-24
forum: Installation &amp; Upgrades
---

### Post by daryl9 on 2020-02-24
I originally posted this in the General Help forum, but I'm not getting any help, so I thought that I would try reposting in the "Installation & Upgrade" forum.  I guess this question better fits in the forum anyway.


I am attempting to create a local repository for the following distributions, Trusty, Xenial and Bionic.  The location in which I'm in has a WIFI connection, so I put up an RPi4 with a small internal network on the backend and a NAS storage device on the internal network. 


Using apt-mirror I mirrored the three repositories to the NAS.  I do a fresh install using Edubuntu (which is Trusty, v14.04).   The repos are cifs shares, so I can mount them on the newly built machine.  I update the sources.list file to see the new path and run apt update.  Apt see's the Trusty share just fine and tells me there are over 500 update available.  Great. Works as I would expect.  However, for some reason, I can't get it to see that a new distribution is available.  


I think that I have everything configured correctly.  If I browse to [http://archive.ubuntu.com](http://archive.ubuntu.com) I see ubuntu -> dists and then a list of distributions.  If I browse the mount point on the machine that I just built I can see the same path, ubuntu -> dists -> trusty, or xenial, or bionic.   So I think that I have the path configure correctly.  I don't see anything wrong.  But if I execute "do-release-upgrade", I get some like "No upgrade available", or something like that.  (don't remember the exact wording at the moment).


How does do-release-upgrade, or the upgrade-manager work? What is it looking for to determine if an upgrade is available?  I know from working with this that apt-mirror doesn't download everything.  It seems to miss a lot of stuff.  For example, the sources directory.  As I work through errors I often have to manually download the sources directory and all of its content.  So I'm thinking that perhaps apt-mirror has missed something that I need to download.   There must be something out there that triggers an upgrade, but I just don't know what.


Any thoughts or suggestions will help.


Thank you.


Daryl

---

### Post by EuclideanCoffee on 2020-02-24
Does this article help? [https://makandracards.com/makandra/12439-setup-an-ubuntu-mirror-that-enables-local-release-upgrades](https://makandracards.com/makandra/12439-setup-an-ubuntu-mirror-that-enables-local-release-upgrades)

I use Debian Mirror.

debmirror --verbose --postcleanup --method=http --host=us.archive.ubuntu.com --root=ubuntu --dist=bionic--arch=i386,amd64 --section=main,restricted,universe --nosource --check-gpg --keyring=Release.gpg --rsync-extra=none ./

---

### Post by daryl9 on 2020-02-24
> **EuclideanCoffee said:**
> Does this article help? [https://makandracards.com/makandra/12439-setup-an-ubuntu-mirror-that-enables-local-release-upgrades](https://makandracards.com/makandra/12439-setup-an-ubuntu-mirror-that-enables-local-release-upgrades)

I use Debian Mirror.

debmirror --verbose --postcleanup --method=http --host=us.archive.ubuntu.com --root=ubuntu --dist=bionic--arch=i386,amd64 --section=main,restricted,universe --nosource --check-gpg --keyring=Release.gpg --rsync-extra=none ./


I just happened to find that command prior to reading your post.  I'll give it a try and report back. 

Thank you very much for the suggestion.

Daryl

---

### Post by daryl9 on 2020-02-27
> **daryl9 said:**
> I just happened to find that command prior to reading your post.  I'll give it a try and report back. 

Thank you very much for the suggestion.

Daryl

EuclideanCoffee,

I successfully downloaded Trusty and Xenial.  I did a fresh install of Trusty and patched from the local repository.  Upon reboot, the test machine found the Xenial repo and prompted me to upgrade.  Great, exactly what I want.  However, I'm having difficulties downloading the Bionic repo.

I tried using the string that you posted, but I get the following error: 
> Getting meta files ...[  0%] Getting: dists/bionic--arch=i386/Release... Download of dists/bionic--arch=i386/Release failed: 404 Not Found
[  0%] Getting: dists/amd64/Release... Download of dists/amd64/Release failed: 404 Not Found
Errors:
 Download of dists/bionic--arch=i386/Release failed: 404 Not Found
 Download of dists/amd64/Release failed: 404 Not Found
Failed to download some Release, Release.gpg or InRelease files!

I also tried using the script from the following [debmirrror ]("https://help.ubuntu.com/community/Debmirror")wiki, but I get a similar error: 
> Ubuntu Release file: using Suite (bionic-security).[  0%] Getting: dists/bionic-updates/Release...          #** GET [http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/Release) ==> 200 OK
ok
[  0%] Getting: dists/bionic-updates/InRelease...        #** GET [http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease) ==> 200 OK
ok
[  0%] Getting: dists/bionic-updates/Release.gpg...      #** GET [http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/Release.gpg) ==> 200 OK
ok
[GNUPG:] NEWSIG
[GNUPG:] ERRSIG 3B4FE6ACC0B21F32 1 10 00 1582832398 9 -
[GNUPG:] NO_PUBKEY 3B4FE6ACC0B21F32
gpgv: Signature made Thu 27 Feb 2020 01:39:58 PM CST
gpgv:                using RSA key 3B4FE6ACC0B21F32
gpgv: Can't check signature: No public key
.temp/.tmp/dists/bionic-updates/Release.gpg signature does not verify.
[GNUPG:] NEWSIG
[GNUPG:] ERRSIG 3B4FE6ACC0B21F32 1 10 01 1582832398 9 -
[GNUPG:] NO_PUBKEY 3B4FE6ACC0B21F32
gpgv: Signature made Thu 27 Feb 2020 01:39:58 PM CST
gpgv:                using RSA key 3B4FE6ACC0B21F32
gpgv: Can't check signature: No public key
.temp/.tmp/dists/bionic-updates/InRelease signature does not verify.
Ubuntu Release file: using Suite (bionic-updates).
Errors:
 .temp/.tmp/dists/bionic/Release.gpg signature does not verify
 .temp/.tmp/dists/bionic/InRelease signature does not verify
 .temp/.tmp/dists/bionic-security/Release.gpg signature does not verify
 .temp/.tmp/dists/bionic-security/InRelease signature does not verify
 .temp/.tmp/dists/bionic-updates/Release.gpg signature does not verify
 .temp/.tmp/dists/bionic-updates/InRelease signature does not verify
Failed to download some Release, Release.gpg or InRelease files!
WARNING: releasing 1 pending lock...


I'm not sure if it can't find the Release file, or just can't verify the signature.  Any idea what it's complaining about?  

Thanks

Daryl

---

### Post by daryl9 on 2020-03-08
I thought that I would give an update to this and see if someone can help me figure out what is going on and how to resolve this issue.

So the last suggestion was to use debmirror instead of apt-mirror to download the repositories, which I did.  The location where I normally do my work is a location with very limited WIFI access, and downloading hundreds of gigs of data is very difficult.   I temporary moved my operation to a lotion with high speed download capabilities, my house.  I put the RPi4 on my local LAN and downloaded to a 2TB USB drive.  Initial testing worked great.  I did a fresh Trusty Tahr install, updated the most recent packages, 500+, the update-manager saw that an upgrade was available and I upgrade, then patched and upgraded.  Worked exactly as I think that it should, all on my local LAN.  However....

I took the data back to my work location and transferred it to a NAS storage device. The plan is to use the RPi4 as the means to download the updates from the online repositories and update the local repo which is on the NAS.  It has an Apache instance which is used to update and upgrade the equipment.  I share the repository to the PI and link it to the Apache instance, e.g. /var/www/html/ubuntu -> /Repos.  I can browse the repo just fine on the PI as well as the machine that I want to update/upgrade.  This is all on an internal local LAN.  I only have a couple of machines on this LAN so use mostly IP addresses.  I put "192.168.0.100/ubuntu" in the browser and I can see the repo just fine.  I can drill down the various distributions and see everything just fine, but I get tons of errors. I get "404 File not Found".  I get "Hash Sum Mismatch" errors.  I get "Some index files failed to download.  They have bee ignored, or old ones used instead".  

I exhausted my research on this.  Everything that I've seen tells me to issue the "apt-get clean" command followed by removing the contents of /var/lib/apt/lists and then rerunning the "apt-get clean" command.  I've researched the "Some index files failed to download" error.  Somewhere I read that the index file is stale, but I have no idea what index file its looking at, or how to refresh it.  Other post say that i need to point the sources.list file to an "old.archive.ubuntu.com" repository.  However, this is a local repository.  Now the one difference between my home environment and the working environment is that I have DNS enabled on my local LAN, but I don't on the working LAN. I tried faking it out using FQDN's in the /etc/hosts file, but that didn't seem to make any difference. I ran the apt-get clean command a million time, cleaned out the /var/lib/apt/lists directory a million times and tweaked the sources.list file a million times, but I can't get past these errors.  I've added the --fix-missing to the apt-get update. At first it appeared to work, but then after updating nearly 500+ files, I get "Hash Sum Mismatch".  

One thing that I forgot to mention was that if I put the 2TB USB drive back on the PI, and update from it, I can update just fine, no errors, however, I'm not able to upgrade via the USB device.  For some reason the update-manager doesn't see that there is a newer distro on the device.  

What I don't understand is why the Ubuntu developers make this so damn difficult?  If this was another flavor of Linux, I could have had this completed months ago.  I hate to abandon this project because I've put so much into this.  Not just this one portion of the project, but the overall project.  I've built several machine and put them in the hands of needy children in the Philippines.  I picked Edubuntu because of all of the educational programs that come pre-installed. This isn't something that is easily duplicated using another platform.  The reason why I have to go this route is because Edubuntu is no longer updated. Whoever was developing it stopped at Trusty Tahr.   Installing a fresh version of Bionic and then installing each and every educational program would be a nightmare, especially with the number of machines that I work with.  It would take me months to build enough machines to make a donation to a school.  I really need to make this work, if not, then I'll have to abandon Edubuntu and go a different path.

Any help is appreciated. 

Thank you.

Daryl

---

### Post by daryl9 on 2020-03-09
Curiosity question, does update-manager/do-release-upgrade require a route to the outside?  As I reported, I can "apt-get update" using the USB device that I initially downloaded the repositories to, just not from the NAS device.  However, I can't upgrade from the USB device.  It doesn't matter if I issue the update-manager or do-release-upgrade, I get "No new release found" or similar.  

When I did this on my home network, it worked just fine, however, in the closed network that I have, with no route to the outside world, the upgrade fails.  There is no explanation, no logs, nothing.  I have absolutely no idea why it can't find the next release.  

Any thoughts or comments are appreciated.

Thank you

Daryl

---

### Post by EuclideanCoffee on 2020-03-11
There's a lot of domain specific information in here. I'm not familiar with your project enough to provide any advice.

The update is meant for networked devices, yes. There appears nothing inherit in the documentations that require networked connections: [http://manpages.ubuntu.com/manpages/bionic/man8/do-release-upgrade.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/do-release-upgrade.8.html)

However, you should be able to accomplish what you want with some symbolic links, apt sources, and mounting your USB drive.

First I would check if you can apply updates and install software from your USB. You would need to make sure your USB is mounted and then the apt configuration is set correctly.

---

### Post by daryl9 on 2020-03-11
> **EuclideanCoffee said:**
> There's a lot of domain specific information in here. I'm not familiar with your project enough to provide any advice.

The update is meant for networked devices, yes. There appears nothing inherit in the documentations that require networked connections: [http://manpages.ubuntu.com/manpages/bionic/man8/do-release-upgrade.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/do-release-upgrade.8.html)

However, you should be able to accomplish what you want with some symbolic links, apt sources, and mounting your USB drive.

First I would check if you can apply updates and install software from your USB. You would need to make sure your USB is mounted and then the apt configuration is set correctly.

Thanks for the feedback. 

A few years ago when I first started my foundation I did something similar.  My work environment had zero internet connectivity, so in order to update the equipment that I was working wtih, I used apt-mirror to mirror v14.04 onto a USB device at a remote location, then after building a machine I would plug in the USB device tweak the sources.list to see the mounted USB device.  Worked well.  Time consuming, and a pain in the rear, but when I shipped a machine it was patched to highest level that I could at that time.  

I am now trying to improve on that.  I am now in an environment that has limited internet access, so that gave me the idea to have a local repository, but for some reason it just isn't working as intended.  

Yes, I've verified mount points multiple times.  I can mount the NAS shares on the Pi and browse them just fine from the client machine.  I get on the client machine, pull up a browser, type in [http://192.168.0.100/ubuntu](http://192.168.0.100/ubuntu) and I see the repository just fine, same if I link the USB device to the apache www/html directory.  I can mount the USB device to the Pi, ln -s /var/www/html/ubuntu -> /mnt/Repos, get on the client machine, pull up a browser, type in [http://192.168.0.100/ubuntu](http://192.168.0.100/ubuntu) and browse the repository just fine.  But, when I have the NAS share mounted/linked, and if I issue a apt-get update/do-release-upgrade I get all sorts of errors. 

 I just don't get it.   Unless there is something in the sources.list file that is missconconfigured, but I really don't think there is.  I just need to change "http://archive.ubuntu.com/ubuntu" "http://192.168.0.100/ubuntu"  everything else should be the same.  I don't remember the rest of the string off the top of my head, but the only differnce should be where I'm pulling the updates from.

Again, I just don't get it.  BTW, I've read the man page for do-release-upgrade and update-manager, muliple times.  Not much help.

Thanks

Daryl

---

### Post by EuclideanCoffee on 2020-03-12
That's difficult to say because it leaves me wanting to troubleshoot.

My hunch is that it's something to do with NAS. Earlier, I wanted a similar setup, but I wasn't able to use NAS. I had to use SAN.

---

### Post by daryl9 on 2020-03-17
I finally got this to work, at least for the moment....:D

I wiped out everything that I had previously downloaded and redownloaded just the Bionic repository directly to the NAS.  It took several day's and failed a few times due to the flacky WIFI access that I'm using, but I finally got it.  Previously, I downloaded from a remote location, to a USB attached harddrive, then copied the contents to the NAS.  For some reason, the data on the NAS differed from what was on the USB harddrive.  

On another board I had posted a similar question and someone there pointed out to me that Edubuntu-desktop was in the repositories.  I had never looked for Edubuntu before, only the individual educational programs, but once I realized that Edubuntu was in the repo, I was able to bypass the older distirbutions install Ubuntu 18.04, install the edubuntu-desktop and all the educational programs.  Works great.  

So now I can move forward with geting equipment built and shipped out.

Thank you.

Daryl

---

