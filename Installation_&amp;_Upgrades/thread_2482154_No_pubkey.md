---
title: "No_pubkey"
date: 2022-12-21
forum: Installation &amp; Upgrades
---

### Post by tedox1 on 2022-12-21
Hello, 
first thanks in advance to those who take care of my problem. I have not been able to update or upgrade for some time now, so unfortunately my laptop is still running Ubuntu 20.04.5. This is apparently due to a problem with my public keys. I have already read through every blogpost but unfortunately no suggested solution seems to work and now I am a bit desperate. 
So when I type "Sudo apt update" I get the following error messages: 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291431&stc=1[/IMG]

Sorry that my terminal is in German. (Fehl. = Error)
I have also tried to add the specified public keys manually (e.g. "gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv 8cae012ebfac38b17a937cd8c5e224500c1289c0"), which unfortunately did nothing. In the course of my research I have also times the list of my gpg-keys output 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291432&stc=1[/IMG]

where I wonder if there is not once "------------------------------------------------" missing whereby the two keys that are thereby connected do not work? I don't know how to add this to the gpg-files, because with "cat *.gpg" I only get something like "n1u&#65533;&#65533;&#65533;&#65533;B&#65533;D&#65533;&#65533;&#65533;&#65533;Hi&#65533;".  I had also read that it can happen with Ubuntu that you get this error because you have more than 40 active keys which is not the case with me, because with "apt-key list" only 13 are displayed. Even if I have installed something over 3000Pkg. Even if I try to verify the keys manually and individually I get the error "gpgv: verify signatures failed: Unexpected error " for each one (even the ones that actually work) with "apt-key verify deadsnakes_ubuntu_ppa.gpg". Furthermore I get an error for "Error:22 [https://packagecloud.io/ookla/speedtest-cli/ubuntu](https://packagecloud.io/ookla/speedtest-cli/ubuntu) focal InRelease" although I didn't install ookla speedtest anymore. Which is almost funny. 
But what confuses me the most is the output " The following signatures could not be verified because their public key is not available: NO_PUBKEY C5E224500C1289C0". What is meant there by "my public key"? But the most important question is: How do I get this major problem fixed so that II can update again?

---

### Post by mIk3_08 on 2022-12-22
To add pubkey just run the following command below with the given pubkey in your terminal. Regards and cheers
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <PUBKEY>
```

---

### Post by ActionParsnip on 2022-12-22
```

curl -L https://linux.teamviewer.com/pubkey/currentkey.asc | gpg --dearmor | sudo apt-key add -

```

---

### Post by tedox1 on 2022-12-22
Thanks for the quick reply. The suggested methods have partially worked. However, most of it still does not work. I was able to interrupt the errors on 
```

Fehl:16 http://ppa.launchpad.net/ehoover/compholio/ubuntu focal Release                                                                                  
  404  Not Found [IP: 2620:2d:4000:1::3e 80]
Fehl:17 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu focal Release                                                                                 
  404  Not Found [IP: 2620:2d:4000:1::3e 80]
Fehl:18 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu focal Release                                                                                                         
  404  Not Found [IP: 2620:2d:4000:1::3e 80]
Fehl:19 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu focal Release                                                                                                                    
  404  Not Found [IP: 2620:2d:4000:1::3e 80]
Fehl:20 https://linux.teamviewer.com/deb development InRelease                                                                                                                           
  403  Forbidden [IP: 2600:9000:2017:d000:1c:3aaa:b100:93a1 443]
Fehl:21 https://packagecloud.io/ookla/speedtest-cli/ubuntu focal InRelease
  Die folgenden Signaturen konnten nicht überprüft werden, weil ihr öffentlicher Schlüssel nicht verfügbar ist: NO_PUBKEY 8E61C2AB9A6D1557

```
 though. (Fehl. = Error), (Re error 21: The following signatures could not be verified because their public key is not available)
Errors 16 to 19 are 404 with the same IP address. I'm a little afraid to delete them all especially with gnome because gnome is already somehow important. 
I tried, since I do not really use ookla to delete the public key of ookla (sudo apt-key del 8E61C2AB9A6D1557 ), which has brought nothing. The key does not appear in apt-key list anymore. I also don't understand why ookla uses packagecloud for their public keys.  I'm sorry that the title of the topic is no longer correct because it is no longer only about Public.Keys, do not take it amiss it is my first post.

---

### Post by ActionParsnip on 2022-12-22
[http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/)

The PPA doesn't support Focal and should be removed. Not all PPAs support all releases of Ubuntu

---

### Post by ActionParsnip on 2022-12-22
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/)

The WINE PPA doesn't support Focal and should be removed. Not all PPAs support all releases of Ubuntu

---

