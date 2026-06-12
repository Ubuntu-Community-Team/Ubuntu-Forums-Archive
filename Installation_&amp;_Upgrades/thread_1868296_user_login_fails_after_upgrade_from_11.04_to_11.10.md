---
title: "user login fails after upgrade from 11.04 to 11.10"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by james2b on 2011-10-24
My user login fails after upgrade from 11.04 to 11.10, it just cycles back to the log on screen when I click my user name and then enter my password, (and no password error message is given). But I can log into the new 11.10 upgrade with the guest account. Can this issue be related to the nvidia driver problem since my PC does have a nvidis video card ? So do I need to create a new user account, and then remove that old user, or how do I fix this issue?

---

### Post by raja.genupula on 2011-10-24
Hi i have something that gonna  help you to solve this issue .

[http://ubuntuforums.org/showthread.php?t=1861940](http://ubuntuforums.org/showthread.php?t=1861940)

[http://ubuntuforums.org/showpost.php?p=11359168&postcount=11](http://ubuntuforums.org/showpost.php?p=11359168&postcount=11)

All the best.

---

### Post by james2b on 2011-10-24
I have fixed this log in issue by changing ownership of my /home folder to my user name, and group too with that chown command. I guess there is a bug in the Ubuntu 11.10 upgrade option which has root the owner of your /home.? Also I did try that; "sudo rm /home/.Xauthority" which was shown to solve this issue in another forum thread, but it said either file not found, or no such command. Thanks :

---

### Post by james2b on 2011-10-24
What is the best way to search for a specific file such as that one called; .Xauthority ? It is needed to either change directory to where a file or folder is located, or give the full path with the command, right ? I could not find that .Xauthority file in my /home folder, is that . included in front of the file name? Is the search command this; grep ?

---

### Post by raja.genupula on 2011-10-25
> **james2b said:**
> What is the best way to search for a specific file such as that one called; .Xauthority ? It is needed to either change directory to where a file or folder is located, or give the full path with the command, right ? I could not find that .Xauthority file in my /home folder, is that . included in front of the file name? Is the search command this; grep ?

```
locate filename
```

I hope this gonna help you.

---

