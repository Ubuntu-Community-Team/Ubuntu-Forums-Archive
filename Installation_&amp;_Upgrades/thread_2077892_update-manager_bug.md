---
title: "update-manager bug"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by ubontik on 2012-10-29
I got the following message while running Update Manager
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Please advise

---

### Post by ajgreeny on 2012-10-29
Try ```
sudo rm /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
``` then refresh the sources with ```
sudo apt-get update
```

---

### Post by ubontik on 2012-11-02
**[ajgreeny]("http://ubuntuforums.org/member.php?u=27747")**
I ran those commads and got the following:
============
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2012-11-02
To repair GPG error BADSIG:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG+&as_qdr=all&sa=Google+Search&lang=en)

---

