---
title: "DPKG Package List Missing"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Bottesford on 2008-01-05
Having big problems with dpkg.
I recently attempted an install of Pro-FTPD server via Webmin interface which just hung forever.
I went into terminal to try and got all sorts of locking errors within dpkg folder. I followed advice online to remove lock files and trying:

sudo apt-get clean
sudo apt-get update

But now I get the error:
'The package lists or status file could not be parsed or opened'.
The status folder under dpkg was missing so I put it back but still I get this error. 
Can I rebuild my pakage list somehow? 
I cannot use any installation tools or updates at the moment. I've tried rebooting to no avail. 
I'm fairly new to Ubuntu & Linux and am trying to setup a web server (well LAMP server) for my website but I'm getting a bit nervous as it seems extremely easy to break your computer!

---

### Post by Bottesford on 2008-01-05
Anyone? 
Or must I reinstall the entire OS? I'm a little reluctant to do that after only a few weeks of using Ubuntu since I'm intending to use the machine as a web server. If it can't survive a simple install of an FTP server how can I rely on it to run my whole web site? Fine if it's easily fixed but all the solutions on the web have not worked for me so far...

---

