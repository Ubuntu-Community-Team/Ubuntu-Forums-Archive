---
title: "Multiple warnings/errors while updating"
date: 2022-09-15
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2022-09-15
Hello,

I encountered problems while using python...there is a lot of mess with the python staff.
So, I removed python.
Probably something went wrong because after removing python I couldn't use desktop GUI.
So I reinstalled desktop and then tried to update ubuntu from terminal.
Here is what happened:
[COLOR=#000080][FONT=courier new]xxx@ALABAMA:~$ sudo apt-get update
[sudo] password for xxx: 
Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Get:2 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64)  InRelease [1&#8239;581 B]
Err:3 [http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu](http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu) artful InRelease
  403  Forbidden [IP: 2620:2d:4000:1::3e 80]
Hit:4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic InRelease                     
Hit:5 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:6 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) bionic InRelease                
Hit:7 [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) bionic InRelease          
Hit:8 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Hit:9 [https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64](https://nvidia.github.io/libnvidia-container/ubuntu18.04/amd64)  InRelease
Get:10 [https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-container-runtime/ubuntu18.04/amd64)  InRelease [1&#8239;481 B]
Ign:11 [https://mkvtoolnix.download/ubuntu](https://mkvtoolnix.download/ubuntu) bionic InRelease                     
Get:12 [https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64](https://nvidia.github.io/nvidia-docker/ubuntu18.04/amd64)  InRelease [1&#8239;474 B]
Hit:13 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease   
Hit:14 [https://mkvtoolnix.download/ubuntu](https://mkvtoolnix.download/ubuntu) bionic Release                       
Hit:15 [http://ppa.launchpad.net/tomtomtom/k9copy/ubuntu](http://ppa.launchpad.net/tomtomtom/k9copy/ubuntu) bionic InRelease       
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88,7 kB]   
Err:2 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64)  InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A4B469963BF863CC
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [55,2 kB]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [61,0 kB]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]
Reading package lists... Done                                                  
E: Failed to fetch [http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu/dists/artful/InRelease](http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu/dists/artful/InRelease)  403  Forbidden [IP: 2620:2d:4000:1::3e 80]
E: The repository 'http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu artful InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: GPG error: [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64)  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A4B469963BF863CC
E: The repository 'http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/google-chrome.list:3 and /etc/apt/sources.list.d/google-chrome.list:4
xxx@ALABAMA:~$[/FONT][/COLOR]

Any suggestions ?
Thanks

---

### Post by ActionParsnip on 2022-09-15
[http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu/dists/artful/InRelease](http://ppa.launchpad.net/samoilov-lex/aftl-stable/ubuntu/dists/artful/InRelease)

The aftl-stable branch here no longer exists and should be removed
[https://launchpad.net/~samoilov-lex](https://launchpad.net/~samoilov-lex)

You need to get the keys for the Nvidia repo and apply to your system
[http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/3bf863cc.pub](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/3bf863cc.pub)
[http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub)

---

### Post by py-ohayo on 2022-09-15
Ok, Thanks,
I removed "samoilov" and some Nvidia repositories from Software & Updates / Other software 
Then updates worked without error ... although I didn't add keys for Nvidia you proposed (can you provide a link on how to add keys).
Then I proceeded with upgrade.
Ubuntu proposed me upgrade to 20.04.
Unfortunately upgrade failed, again due to python issue (please look at screenshot):
[IMG]https://i.postimg.cc/Kv99N3F8/Screenshot-from-2022-09-15-14-56-28.png[/IMG]

---

