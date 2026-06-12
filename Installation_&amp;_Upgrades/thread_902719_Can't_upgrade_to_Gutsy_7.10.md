---
title: "Can't upgrade to Gutsy 7.10"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by brenbren on 2008-08-27
Hey All,
I've been trying to upgrade to Gutsy 7.10 but I can't seem to get past the fetching stage. The files are fetched and then these errors comes up:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80] 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80] 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80] 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80] 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz) 404 Not Found 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found

And I have no clue how to fix this. I initially thought to reinstall Fiesty (what I'm on now) but can't figure it out.
Any thoughts?

---

### Post by prshah on 2008-08-27
> **brenbren said:**
> 
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)[color="red"]edgy[/color]/universe

Looks like you still have lines for Edgy's repositories; Edgy (Ubuntu 6.10) support lifetime has ended, and the repositories for it have been offlined. If you are sure that you're using Feisty Fawn (7.04), then you should edit your "/etc/apt/sources.list" file, and remove/comment out lines related to "edgy".

To check your version, Open a terminal (Applications-Accessories-Terminal) and give the command ```
cat /etc/lsb-release
```

To update the sources list:```
sudo nano /etc/apt/sources.list
#now a text editor will open up, place a "#" in front of lines
#that contain the word "edgy"
#Press Ctrl+X to quit, and give "Y" when prompted to save
sudo apt-get update && sudo apt-get upgrade

```
if the last command(s) finish successfully, you are now ready to upgrade!

---

