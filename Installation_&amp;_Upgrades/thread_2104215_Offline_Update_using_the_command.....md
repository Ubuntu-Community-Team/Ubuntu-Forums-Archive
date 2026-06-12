---
title: "Offline Update using the command...."
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by bijupp on 2013-01-12
I have a limited connection therefore I use the following command for updatet 

```
sudo apt-get upgrade --print-uris -y | grep -o "http:.*deb'"  | grep -o .*.deb > list

```


I download the files in the list from another computer (windows Os) and use pendrive to copy the files. and use the following command to update the packages. 



```
sudo dpkg -i *.deb
```



it works well but even after updating the system the update manager shows list to update so i run the above commands again.

[ATTACH]229936[/ATTACH]

but get list file shows nothing.. 

I have 2 doubts to be cleared 

1. is there is any error in above commands or any other commands will do full offline update ??

2. I wish to know whether this command or any other command can be used for installing the software from the "Ubuntu software centre"??

3. If there is any harm in using the command and download using another computer

---

### Post by zvacet on 2013-01-14
You can try [Keryx.]("http://www.webupd8.org/2010/01/keryx-portable-cross-platform-offline.html")

No harm should be done by downloading from other comp.

---

