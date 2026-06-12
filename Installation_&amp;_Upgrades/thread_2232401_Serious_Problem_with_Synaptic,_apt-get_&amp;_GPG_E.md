---
title: "Serious Problem with Synaptic, apt-get &amp; GPG Errors"
date: 2014-07-01
forum: Installation &amp; Upgrades
---

### Post by taytaybongsong on 2014-07-01
This only started happening today, and I did nothing unusual, so I can't figure out why. I checked for updates a few hours ago via the command line with ```
sudo apt-get update
``` and then repeatedly attempted to see if the issue was resolved using Synaptic (simply by clicking the "Reload" button). Every time I received some variation on the following: ```
W: GPG error: http://debian.drdteam.org stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 392203ABAF88540B
W: GPG error: http://security.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://apt.mucommander.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 030BBF253A687AFF
W: GPG error: http://archive.getdeb.net trusty-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://download.videolan.org  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6BCA5E4DB84288D9
W: GPG error: http://us.archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 14E4942973C62A1B
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```
I proceeded to use Y PPA Manager's "Try to Import All Missing Keys" feature, but that did not work, and the error messages still show up whether reloading through Synaptic or doing an apt-get update in the terminal. Can the knowledgeable amongst you please chime in?

P.S. I am running Xubuntu 14.04.

---

### Post by taytaybongsong on 2014-07-01
Did some googling around and decided to try the following:```
sudo rm -rf /var/lib/apt/lists/*
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
```
Now it seems to throw out less errors, but the core ones are still there. I receive the following whenever I try to reload through Synaptic or do an apt-get update now:
```
W: GPG error: http://debian.drdteam.org stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 392203ABAF88540B
W: GPG error: http://security.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://us.archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://apt.mucommander.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 030BBF253A687AFF
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.getdeb.net trusty-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: http://us.archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://download.videolan.org  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6BCA5E4DB84288D9
W: GPG error: http://us.archive.ubuntu.com trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 14E4942973C62A1B
```
Any help would be greatly appreciated.

---

### Post by oldos2er on 2014-07-01
Use ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` replacing KEYID with the alphanumeric shown after NO_PUBKEY.

---

### Post by taytaybongsong on 2014-07-01
> **oldos2er said:**
> Use ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` replacing KEYID with the alphanumeric shown after NO_PUBKEY.
went through that and discovered this bug: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540) which led me to solve my problem. will post details as exact as possible in next reply.

---

### Post by taytaybongsong on 2014-07-01
Ok, so I solved the problem as follows (bear in mind that Thunar is my file manager):
Step 1. In a terminal I opened up my file manager with root privileges:
```
gksudo thunar
```
Step 2. I navigated to "/etc/apt/trusted.gpg.d/" and deleted any file with a size of "0 bytes".
Step 3. I opened up Synaptic and carefully went over the PPAs in the "Other Sources" tab, to see which ones I'm actually using. I left that window open for reference.
Step 4. In my file manager I sorted the files in "/etc/apt/trusted.gpg.d/" by name, and deleted any ones that were associated with PPAs I was no longer using.
Step 5. I navigated to "/etc/apt/sources.list.d/", sorted the files in there by name, and deleted any ones that were associated with PPAs I was no longer using.
Step 6. I executed the following commands in my terminal, one by one: ```
sudo rm -rf /var/lib/apt/lists/*
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
```
Step 7. I enjoyed being able to use Synaptic and apt-get without issues once again.

Sources I used to solve the issue:
[http://stream-recorder.com/forum/w-gpg-error-http-ppa-launchpad-net-t6741.html](http://stream-recorder.com/forum/w-gpg-error-http-ppa-launchpad-net-t6741.html)
[http://www.linux.com/learn/answers/view/1267-help--how-can-i-fix-this--i-cant-update](http://www.linux.com/learn/answers/view/1267-help--how-can-i-fix-this--i-cant-update)
[https://answers.launchpad.net/ubuntu/+source/synaptic/+question/191283](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/191283)
[https://answers.launchpad.net/ubuntu/+source/synaptic/+question/175016](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/175016)
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540)
[http://ubuntuforums.org/showthread.php?t=2195579](http://ubuntuforums.org/showthread.php?t=2195579)

Hope this will be of help to anyone who has dealt or will deal with this issue in the future.

---

### Post by saparonia2 on 2015-05-14
I don't know if this will be useful to you if you have this problem but this is how I got rid of it. I have a mixture of Linux with elementary os base. Every time I tried to generate updates in Synaptic I got this message: 
 W: GPG error: [http://download.videolan.org](http://download.videolan.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6BCA5E4DB84288D9

Firstly I used software centre to remove / uninstall VLC Player and then I took out the videolan links from the repositories. This solved it, no more GPG errors

---

