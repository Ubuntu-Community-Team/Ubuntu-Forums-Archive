---
title: "problems with update"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by TheRacerX on 2012-01-09
hey guys me again, my computer REALLY doesnt like me for some reason cause now im getting update errors i do the sudo apt-get update command in the terminal after installing a repo and this is what i get AFTER the repo update is already said and done 


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9D63EE0836DFE71C

it has nothing to do with the new repo i installed cause i checked, any help?

---

### Post by rojaasensei on 2012-01-09
The link below will help you straighten things out :-)

[http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

---

### Post by fantab on 2012-01-09
Run this from Terminal-

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

If that doesn't solve your problem then try this-

```
sudo apt-key adv --keyserver.ubuntu.com --recv-keys
sudo apt-key adv --keyserver.ubuntu.com --recv-keys 4874D3686E80C6B7 4874D3686E80C6B7 9D63EE0836DFE71C
```

---

### Post by raja.genupula on 2012-01-10
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

That was helped me many times . I hope it will work for you.

---

### Post by TheRacerX on 2012-01-10
i tried every single one of those methods none of them worked i kept getting cant receive keys errors cause supposedly keys.ubuntu doesnt exist or something like then i tried the others and got command not found and aptitude errors and download directory is locked permission denied so i dont know whats wrong

---

### Post by raja.genupula on 2012-01-10
could you post the output of terminal here between code tags ? 

I am sure about that link , its work fine .May be somewhere any small mistake also going to be cause for errors .That's why i need terminal code what you have entered and what you got, please paste here . 

Thank you ! :):)

---

### Post by TheRacerX on 2012-01-16
as soon as i get to the second step it gives me this error


oddball@Cunningham:~$ sudo apt-get clean
[sudo] password for oddball: 
oddball@Cunningham:~$ sudo cd /var/lib/apt
sudo: cd: command not found
oddball@Cunningham:~$

---

### Post by plucky on 2012-01-17
> **TheRacerX said:**
> as soon as i get to the second step it gives me this error


oddball@Cunningham:~$ sudo apt-get clean
[sudo] password for oddball: 
oddball@Cunningham:~$ sudo cd /var/lib/apt
sudo: cd: command not found
oddball@Cunningham:~$

That is because the command given are all from the superuser,which is why they have the # in front of them.If you are using sudo the commands become ```
sudo apt-get clean

cd /var/lib/apt

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo apt-get clean

sudo apt-get update
```

Note there is no sudo before the cd command as you don't need it.

Or you could do as the instructions says and use **sudo -i** and then the commands as shown.

Good Luck

---

### Post by Old_Grey_Wolf on 2012-01-17
Try these commands ```
gpg --keyserver keyserver.ubuntu.com --recv 4874D3686E80C6B7

gpg --export --armor 4874D3686E80C6B7 | sudo apt-key add -

gpg --keyserver keyserver.ubuntu.com --recv 9D63EE0836DFE71C

gpg --export --armor 9D63EE0836DFE71C | sudo apt-key add -
```

---

