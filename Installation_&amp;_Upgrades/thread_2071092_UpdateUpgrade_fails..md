---
title: "Update/Upgrade fails."
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by ChristopherAdams on 2012-10-14
I've been having problems getting Ubuntu to update & upgrade on an Acer Aspire. I will get messages about the number of updates I'm missing, but when I try to run 'sudo apt-get update' the process fails.

I tried the following command, as suggested in another thread:
 ```
    sudo rm -vf /var/lib/apt/lists/partial/* 
```This removed a bunch of files, but the OS still won't upgrade.
 
Here are the error messages I get from running "apt-get update --fix missing":
 
"W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 
Ubuntu Archive Automatic Signing Key <[EMAIL="ftpmaster@ubuntu.com"]ftpmaster@ubuntu.com[/EMAIL]>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. 
GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 
Ubuntu Archive Automatic Signing Key <[EMAIL="ftpmaster@ubuntu.com"]ftpmaster@ubuntu.com[/EMAIL]>
 
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. 
GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 
Ubuntu Archive Automatic Signing Key <[EMAIL="ftpmaster@ubuntu.com"]ftpmaster@ubuntu.com[/EMAIL]>
 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...pdates/Release]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release") 
 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...curity/Release]("http://security.ubuntu.com/ubuntu/dists/precise-security/Release") 
 
W: Some index files failed to download. They have been ignored, or old ones used instead."
 
Any help would be appreciated.
-Christopher Adams.

---

### Post by ajgreeny on 2012-10-14
You should be able to solve your problem by following the information at [https://wiki.ubuntu.com/GPGArchiveSignature](https://wiki.ubuntu.com/GPGArchiveSignature)

---

### Post by jerrrys on 2012-10-15
Also check here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG+&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by ChristopherAdams on 2012-10-21
I used the first method outlined in the link provided by jerrrys, and that solved the problem.

Thanks jerrrys & ajgreeny! :P

Christopher Adams.

:guitar:\\:D/=D>=D>=D>\\:D/

---

