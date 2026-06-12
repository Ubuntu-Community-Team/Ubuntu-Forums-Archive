---
title: "can't run apt update, after failed insync installation"
date: 2023-02-16
forum: Installation &amp; Upgrades
---

### Post by razerez on 2023-02-16
I am using Ubuntu 22.04 and i tried to run 

    ```
sudo apt-get update
```
but got in return:
```
                                                                        
Get:4 http://apt.insync.io/ubuntu jammy InRelease [5,535 B]                                                                                          
Ign:5 https://ppa.launchpadcontent.net/webupd8team/y-ppa-manager/ubuntu jammy InRelease                                        
Err:4 http://apt.insync.io/ubuntu jammy InRelease                                 
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A684470CACCAF35C
Err:7 https://ppa.launchpadcontent.net/webupd8team/y-ppa-manager/ubuntu jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Ign:6 http://cdn-fastly.deb.debian.org/debian jessie InRelease
Get:8 http://cdn-fastly.deb.debian.org/debian jessie Release [77.3 kB]
Get:9 http://cdn-fastly.deb.debian.org/debian jessie Release.gpg [1,652 B]
Ign:9 http://cdn-fastly.deb.debian.org/debian jessie Release.gpg
Reading package lists... Done
W: GPG error: http://apt.insync.io/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A684470CACCAF35C
E: The repository 'http://apt.insync.io/ubuntu jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://ppa.launchpadcontent.net/webupd8team/y-ppa-manager/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://cdn-fastly.deb.debian.org/debian jessie Release: The following signatures were invalid: EXPKEYSIG 7638D0442B90D010 Debian Archive Automatic Signing Key (8/jessie) <ftpmaster@debian.org> EXPKEYSIG CBF8D6FD518E17E1 Jessie Stable Release Key <debian-release@lists.debian.org> 75DDC3C4A499F1A18CB5F3C8CBF8D6FD518E17E1
E: The repository 'http://http.debian.net/debian jessie Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


```[
I tried letting ubuntu troubleshoot it
```

sudo mv /etc/apt/sources.list ~/
sudo touch /etc/apt/sources.list
software-properties-gtk

```
but after tring to cofigure the "ubuntu software" window by checking  "Community- maintained and open source software" and changing the download server to "server for united states" and "updates" window by subscribing to all updates but i got the following error:
[IMG]https://i.stack.imgur.com/6HHTY.png[/IMG]

I proceeded anyway and updated the "/etc/apt/sources.list" file and then i tried to update again with "sudo apt update" but got:
```

Err:6 http://extras.ubuntu.com/ubuntu jammy Release                           
  404  Not Found [IP: 185.125.190.36 80]
Err:4 http://apt.insync.io/ubuntu jammy InRelease                             
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A684470CACCAF35C

Get:42 http://archive.ubuntu.com/ubuntu jammy-security/main amd64 Packages [637 kB]                                                                  
Err:43 https://ppa.launchpadcontent.net/webupd8team/y-ppa-manager/ubuntu jammy Release                                                               
  404  Not Found [IP: 185.125.190.52 443]

E: The repository 'http://extras.ubuntu.com/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://apt.insync.io/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A684470CACCAF35C
E: The repository 'http://apt.insync.io/ubuntu jammy InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://cdn-fastly.deb.debian.org/debian jessie Release: The following signatures were invalid: EXPKEYSIG 7638D0442B90D010 Debian Archive Automatic Signing Key (8/jessie) <ftpmaster@debian.org> EXPKEYSIG CBF8D6FD518E17E1 Jessie Stable Release Key <debian-release@lists.debian.org> 75DDC3C4A499F1A18CB5F3C8CBF8D6FD518E17E1
E: The repository 'http://http.debian.net/debian jessie Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://ppa.launchpadcontent.net/webupd8team/y-ppa-manager/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


```
I also tried to install y-ppa-manager but i got the same errors  and couldn't finish the installation.

I am new to linux and can't find the solution to this problem.
what do i need to do to run "apt update"successfully?

---

### Post by MAFoElffen on 2023-02-16
According to their instructions
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ACCAF35C

```
If for some reason you want to disable their repo from sourcesd, open file /etc/apt/sources.list.d/insync.list and comment out this line
```

[COLOR=#ff0000]#[/COLOR] deb http://apt.insync.io/ubuntu jammy non-free contrib

```

---

### Post by ActionParsnip on 2023-02-16
[http://extras.ubuntu.com/ubuntu/dists/](http://extras.ubuntu.com/ubuntu/dists/)
Doesn't support Jammy, so should be removed

---

### Post by Tadaen_Sylvermane on 2023-02-16
```
Ign:6 http://cdn-fastly.deb.debian.org/debian jessie InRelease
Get:8 http://cdn-fastly.deb.debian.org/debian jessie Release [77.3 kB]
Get:9 http://cdn-fastly.deb.debian.org/debian jessie Release.gpg [1,652 B]
Ign:9 http://cdn-fastly.deb.debian.org/debian jessie Release.gpg
```

It's a miracle your system hasn't had a heart attack yet. You shouldn't mix distros packages. Debian and Ubuntu are not 100% binary compatible.

---

