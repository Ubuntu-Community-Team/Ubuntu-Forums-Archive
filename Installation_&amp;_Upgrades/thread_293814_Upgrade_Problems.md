---
title: "Upgrade Problems"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by kevinplinux on 2006-11-05
Ok, so I followed the instructions to upgrade (typed this in the terminal: gksu "update-manager -c" Then I clicked upgrade, things started working)
But then this error comes up:
**Error during update**
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz) 404 Not Found

....how would I go about fixing that so it'll upgrade? I wouldn't even mind removing whatever is causing the problem (probably wine)... just tell me how.
Thanks!

[Also, I have a Java folder locked on my desktop that I can't get rid of... any suggestions?]

---

### Post by Kateikyoushi on 2006-11-05
That package is not avaible now.

Change your sources list.
```
gksudo gedit /etc/apt/sources.list
```

Find the line which begins with wine.budgetdedicated.com, then replace the binary-amd64 with binary-all.

To delete the folder from the desktop.

```
sudo rmdir ~/Desktop/FOLDERNAME
```

---

### Post by kevinplinux on 2006-11-06
thanks, that sounds great! I'll have to try it out later!:o 
I appreciate you straightforward answer!:D

---

### Post by kevinplinux on 2006-11-06
I see this:
# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
](*,) 
I don't see where to change what you mentioned.

Also, when deleting the file I get:
rmdir: /home/kp/Desktop/Java: **Directory not empty**

---

