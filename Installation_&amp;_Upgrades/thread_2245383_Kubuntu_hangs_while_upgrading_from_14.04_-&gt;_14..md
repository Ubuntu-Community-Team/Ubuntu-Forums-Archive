---
title: "Kubuntu hangs while upgrading from 14.04 -&gt; 14.10 beta"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by malkdude on 2014-09-23
hello fellow ubuntu/kubuntu/... users. I just wanted to report this here, maybe it will help someone else. I wanted to upgrade from kubuntu 14.04 -> 14.10, and during the upgrade, which I did by following the official instructions, namely 1) I did an update, and then 2) I ran kubuntu-devel-release-upgrade. Ok so the download went fine, but during the package installation, at some point, the "upgrade" software hung, and then I couldn't do anything, not even close it (for a while).

After a bit of searching, I think the problem was that at some point, the installation software asks you a question, which you have to answer with yes or no, and that's where it hangs, due to some small Python error. More details follow:

in the log file, /var/log/dist-upgrade/main.log

I found

File "/tmp/ubuntu-release-upgrader-s6905wp6/DistUpgrade/DistUpgradeViewKDE.py", line 337, in conffile
    os.write(self.master_fd, "y\n")

TypeError: 'str' does not support the buffer interface

I believe, after looking up this Python error, that a programmer might have forgotten to convert a string to a Utf8 code, or something like that (I leave that to the experts).

Ok, so hopefully this will get fixed before the release. In any case, what I had to do was (USE AT YOUR OWN RISK!), first sudo pkill python and pkill the installation program, and then I had a broken distribution, which I fixed by a sudo dpkg --configure -a. Then I ran an update (sudo apt-get update & sude apt-get upgrade). USE AT YOUR OWN RISK! I had to do that because I had a broken distribution. Of course, for the new users, it is kind of a last resort to kill the installation program, and I do not recommend it (I just had to).

Ok now I am using 14.10 beta version! I hope this helps someone, and maybe some kubuntu developers will see this before the official release. Cheers! I am just posting it in the hope that it might be of some help, and I hope that the kubuntu developers will see this before the release. Is there a need for a launchpad bug? Let me know and I will do it.

---

### Post by grahammechanical on 2014-09-23
I have not read all your post but I will tell you this. I would not do what you have done. And I have been running the development branch of Ubuntu and some of its flavours for more than two years. I have Utopic Unicorn installed for Ubuntu and some of its flavours. I would do a fresh install of the latest daily ISO image.

Why? Because the release is not finished there are still changes to be made to the libraries and the scripts that control the upgrade process are not up to date. Expect breakage like this. It is not a bug. It is just the kind of thing that happens when we upgrade too soon.

What you have done is test the upgrade process but it is too soon to do that. There are Kubuntu users on this forum but I would be very surprised if Kubuntu developers were hanging out here. If you want to get involved with testing Kubuntu then this is where you should go.

[http://qa.kubuntu.co.uk/](http://qa.kubuntu.co.uk/)

Regards.

---

### Post by malkdude on 2014-09-23
Hello Grahammechanical, hmm, thank you so much for your post. Ok so, I have managed to install the beta. I had issues with the upgrade software, which is to be expected, since it is a beta version. Yes, now, my question is, is it better to do a fresh install of the release version once it is out, despite having the beta version installed? Or, is there a way, to get the release version of kubuntu, by doing a sudo apt-get update or upgrade or some other command? Or am I being too optimistic? It is the first time I install a beta version of a flavor of linux. And my aim was not to test it but, I was just eager to get it early (I know it is not wise, but I have been using linux for a while, so I can kind of manage to find my way somehow, using forums and things, plus I find it kind of fun). Your advice (and knowledge) is appreciated! Thank you.

---

