---
title: "Package Mirror Troubleshooting"
date: 2013-09-22
forum: Installation &amp; Upgrades
---

### Post by Starfleet_Engineer on 2013-09-22
I setup a package mirror on my local server box using apt-mirror. My problem is that my Ubuntu installs don't seem to recognize it.

I followed the guide from this website [http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

I kept getting the error
> Bad archive mirror
An error has been detected while trying to use the specified Ubuntu archive mirror

Possible reasons for the error are: incorrect mirror specified; mirror is not available
(possibly due to an unreliable network connection); mirror is broken (for example because
an invalid Release file was found); mirror does not support correct Ubuntu version.

Additional details may be available in /var/log/syslog or on the virtual console 4.

Please check the specified mirror or try a different one.
I thought it might be a problem with how my server box was configured so I tried it again from a clean minimal install.
The only things it has installed after the minimal baseline is openssh and apt-mirror.
I then get this error
> The installer failed to download a file from the mirror. This may be a problem with your
network, or with the mirror. You can choose to retry the download, select a different
mirror, or cancel and choose another installation method.

Downloading a file failed:


What am I doing wrong? Where do I start troubleshooting?

---

### Post by Starfleet_Engineer on 2013-10-02
Still haven't worked out how to get this to work. I can connect to the Apache default webpage and administer the server over SSH. What am I doing wrong?

---

