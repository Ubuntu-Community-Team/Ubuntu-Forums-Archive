---
title: "update issues"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by ricoris on 2013-10-23
Hi, I've using Ubuntu for some time but I still know mostly only the basics. I am currently using version 12.04. I have trouble trying to get new updates. I get the following message:

W:GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-ca](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-ca)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-ca](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-ca)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Does someone know what it means and how to solve the problem? Thanks in advance

---

### Post by grahammechanical on 2013-10-23
You are not the only person getting those error messages. Do you remember installing the Medibuntu PPA? And the Spotify PPA? They are what is causing these error messages. You need to remove those PPAs.

Re-installing the Spotify PPA may solve the problem. I do not know if it will. But there is nothing to be done about the medibuntu PPA. It no longer exists.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

The Spotify public key is listed in this web page but it is the same key that apt-get is saying is not available.

[https://www.spotify.com/uk/download/previews/](https://www.spotify.com/uk/download/previews/)

[http://www.omgubuntu.co.uk/2013/01/how-to-install-spotify-in-ubuntu-12-04-12-10](http://www.omgubuntu.co.uk/2013/01/how-to-install-spotify-in-ubuntu-12-04-12-10)

Regards.

---

