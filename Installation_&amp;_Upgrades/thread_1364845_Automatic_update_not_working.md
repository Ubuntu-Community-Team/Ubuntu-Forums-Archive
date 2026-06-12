---
title: "Automatic update not working"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by AM4880 on 2009-12-26
hmm every time i try to update my system (ubuntu netbook remix 8.04/8.10) i get an error message saying:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

ba-arizona.archive.canonical.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5GPG error: [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9FDA6BED73CDC22GPG error: [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-base Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9FDA6BED73CDC22GPG error: [http://netbook-remix.archive.canonical.com](http://netbook-remix.archive.canonical.com) hardy-netbook-remix Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9FDA6BED73CDC22Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

then i close this and another error box comes up

An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

any ideas how i can fix this? thank you all so much =)

---

### Post by bapoumba on 2009-12-26
Please try with the main servers, then reload/upgrade. From synaptic, change the repositories, reload then upgrade.

---

### Post by AM4880 on 2009-12-26
okay cheers

---

### Post by bapoumba on 2009-12-26
Please post here if you have any problem.
```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by edog76 on 2009-12-27
Also running hardy, and also have this problem with the main servers. Ran the code you listed and still coming up with the NO_PUBKEY error after ```
sudo apt-get update
``` The problem started a couple days ago I think.

---

### Post by AM4880 on 2009-12-28
I tried running that but just got the same error message, 

Edog76: would you say around 16 days ago it happened to you aswell?

Thanks everyone

---

### Post by edog76 on 2009-12-28
Well, I haven't been adding software or doing anything that would have brought the problem to my attention until a few days ago. It's certainly possible that the error has been there that long.

---

### Post by MX5EdL on 2009-12-29
I am receiving a similar error when I run Update manager in 8.04.

If I click check updates, it appears the files are downloading, but then I get the no public key message.

*_W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B9FBE5158B3AFA9_*

And then the Update Manager then says system up to date.

Is this issue on my end or the servers?

Thanks.

Ed L.

---

### Post by edog76 on 2009-12-29
Okay, did some digging and have happened upon the solution. Ubuntu has started a pubkey authentication mechanism, so that the packages that we download are the authentic versions rather than malicious ones. The error we see is b/c we lack the pubkey that verifies the ppa for one of the third party sources.

Background info is here:
[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

Here is a script, that didn't work for me, but maybe for others?:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

Here is a video showing how to do this in graphical mode for gnome-do; I think it does a decent job of explaining conceptually what is going on (about 5mins in length):
[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

And here is a terminal version:
[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

From System>>Admin>>Software Sources I unticked gnome-do, banshee, and gilir (which, I think is for cairo-dock) in the 3d party sources tab. When I ran ```
sudo apt-get update
``` I got no errors, thus I think it is lack of pubkey for one of the three 3d party sources I unticked. I then just followed the tutorial to get the pubkeys for each one. All is well. :guitar:

Can both AM4880 and MX5EdL give this a shot and report back? If this works for everyone, AM4880 would you mark the thread as solved so other people can quickly solve the same issue.

---

### Post by MX5EdL on 2009-12-29
No joy.

I followed the screen cast and when that did not work I tried the script and command line method.

Still getting the public key not found.

what's interesting is if I click on the public key file I pulled down and saved per the video, the system sees it and says key imported, but still no good.

Any other suggestions?

Ed

---

### Post by AM4880 on 2009-12-30
no joy for me either im afraid,

I followed the instructions of the video but am still getting the same error when trying to update

are there any other ideas?

cheers,

Alexander

---

### Post by edog76 on 2009-12-30
Did both of you just download the pubkey for gnome-do in the video or did you also extrapolate to your other 3d party sources? You have to get pubkeys for all of them.

You can also just do a quick troubleshooting check, as I did, and untick all the third party sources, then run sudo apt-get update and see if the error comes up. I've attached screenshots of my sources list and the authentications. When I started, only the top three authentications in the list were present.

---

### Post by MX5EdL on 2010-01-01
Guys:

I finally got it to work.  I'm running a Dell system that came loaded with Ubuntu and it was the Dell-Team public key that was missing!?

Hopefully this process is simplified in the future.

If you post this as a fix in a FAQ, I would make it very clear you need to search out the key for every vendor on the list.


Thanks and Happy New Year!

Ed

---

### Post by AM4880 on 2010-01-02
tis' working for me to
thanks for your help everyone

again thanks :) :)

---

### Post by edog76 on 2010-01-02
Great! Glad you guys got it working.

---

