---
title: "Unable to install .sh programs on Ubuntu 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Itspriyank on 2011-04-30
[SIZE=3]Hi I today installed 11.04 and tried to install netbeans 7.0. So i downloaded it from oracle.com that comes with jdk pre-bundled. 
```

chmod +x /path/to/file.sh

``````

/path/to/file/sh

```It stuck at Starting Installation wizard[/SIZE] [SIZE=3]only. Please help me. I have even tried to use the installer from netbeans.orghttp://www.itspriyank.com/Screenshot.png.[IMG]http://www.itspriyank.com/Screenshot.png[/IMG]:confused::confused:

[/SIZE]

---

### Post by Biggy on 2011-05-18
Right click on netbeans.sh Properties > Permissions > check Allow executing file as program. Double click netbeans.sh and click Run.

---

### Post by tommcd on 2011-05-19
Itspriyank,
The terminal output is telling you what to do.
```
The program 'netbeans' is currently not installed. You can install it by typing:
sudo apt-get install netbeans
```
Netbeans is in the Ubuntu repos: [http://packages.ubuntu.com/natty/netbeans](http://packages.ubuntu.com/natty/netbeans)
It may not be the newest netbeans, but at least it will work for you.
For future reference, you can post terminal outputs like this in *code tags* like I did (the # at the top of the post window) instead of posting gigantic screenshots of the terminal.

And welcome to the Ubuntu forums!

---

### Post by hexwind on 2011-06-23
> **Biggy said:**
> Right click on netbeans.sh Properties > Permissions > check Allow executing file as program. Double click netbeans.sh and click Run.

Thanks,this worked for me :)

---

