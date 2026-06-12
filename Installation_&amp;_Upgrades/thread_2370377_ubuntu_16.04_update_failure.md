---
title: "ubuntu 16.04 update failure"
date: 2017-09-02
forum: Installation &amp; Upgrades
---

### Post by elim-qiu on 2017-09-02
```

395 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
Need to get 49.7 MB/587 MB of archives.
After this operation, 97.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Err:1 https://deb.opera.com/opera-stable stable/non-free amd64 opera-stable amd64 45.0.2552.635
  404  Not Found
E: Failed to fetch https://deb.opera.com/opera-stable/pool/non-free/o/opera-stable/opera-stable_45.0.2552.635_amd64.deb  404  Not Found

```

tried
sudo apt-get install --reinstall ubuntu-extras-keyring
gpg --keyserver keyserver.ubuntu.com --recv 3E5C1192
gpg --export --armor 3E5C1192 | sudo apt-key add -

```
sudo apt-get updateIgn:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                             
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                             
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]            
Hit:5 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease                      
Hit:6 http://archive.canonical.com/ubuntu xenial InRelease                             
Get:7 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]             
Hit:9 http://www.geogebra.net/linux stable InRelease                                   
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]         
Hit:8 http://screenshots.getdeb.net xenial-getdeb InRelease                            
Get:12 https://deb.opera.com/opera-stable stable InRelease [2,592 B]               
Err:12 https://deb.opera.com/opera-stable stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
Fetched 309 kB in 2s (151 kB/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://deb.opera.com/opera-stable stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: Failed to fetch https://deb.opera.com/opera-stable/dists/stable/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D615560BA5C7FF72
W: Some index files failed to download. They have been ignored, or old ones used instead
```

```
sudo apt-get upgrade 395 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.Need to get 49.7 MB/587 MB of archives.
After this operation, 97.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Err:1 https://deb.opera.com/opera-stable stable/non-free amd64 opera-stable amd64 45.0.2552.635
  404  Not Found
E: Failed to fetch https://deb.opera.com/opera-stable/pool/non-free/o/opera-stable/opera-stable_45.0.2552.635_amd64.deb  404  Not Found



```


Thanks in advance for your help!

---

### Post by elim-qiu on 2017-09-02
```
[COLOR=#111111][FONT=Ubuntu]By far the simplest way to handle this now is with Y-PPA-Manager (which now integrates the [/FONT][/COLOR]launchpad-getkeys[COLOR=#111111][FONT=Ubuntu] script with a graphical interface).[/FONT][/COLOR]
[LIST=1]
[*][FONT=inherit]To install it, first add the webupd8 repository for this program:[/FONT]
sudo add-apt-repository ppa:webupd8team/y-ppa-manager

[*][FONT=inherit]Update your software list and install Y-PPA-Manager:[/FONT]
sudo apt-get update
sudo apt-get install y-ppa-manager

[*][FONT=inherit]Run y-ppa-manager (i.e. type y-ppa-manager then press enter key).[/FONT]

[*][FONT=inherit]When the main y-ppa-manager window appears, click on "Advanced."[/FONT]

[*][FONT=inherit]From the list of advanced tasks, select "Try to import all missing GPG keys" and click OK.[/FONT]
[FONT=inherit]You're done! As the warning dialog says when you start the operation, it may take quite a while (about 2 minutes for me) depending on how many PPA's you have and the speed of your connection.[/FONT]
[/LIST]

```

---

### Post by BenginM on 2017-09-03
Hiya , if you disable these third party PPA's you shouldn't have trouble updatin' in the first place. as for a GPG key issues, one should consult the official site for such third party package and add the new updated key probably.

---

