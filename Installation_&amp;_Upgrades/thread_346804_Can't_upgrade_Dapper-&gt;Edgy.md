---
title: "Can't upgrade Dapper-&gt;Edgy"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by IamAcoconut on 2007-01-26
I was just trying to upgrade my Dapper to Edgy using ```
gksu "update-manager -c"
```
By the end of 'downloading and installing updates' I got an error.
```
Couldn't install "linux-image-2.6.17-10-386"
Update is canceled. Please send a report about error of 'update-manager' packet attaching files in /var/log/dist-upgrade/.

subprocess post-installation script returned error exit status 9
```
Now I can't run most programs, firefox' a little f**d up, and I am r e a l l y  anxious to reboot my computer. 

What could go wrong? 
Or if you can't tell, then perhaps you can help me reverse the changes I've done?

Thanks in advance

---

### Post by IamAcoconut on 2007-01-26
```
sudo dpkg --configure -a
```
Gives me a screen full of errors...
Help...

---

