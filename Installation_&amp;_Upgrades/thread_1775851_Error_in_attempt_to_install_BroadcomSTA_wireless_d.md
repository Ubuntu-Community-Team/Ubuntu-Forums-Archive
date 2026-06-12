---
title: "Error in attempt to install BroadcomSTA wireless driver"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by mafaldaspeaks on 2011-06-05
I just installed Ubuntu 11.04 on my laptop. When I tried to install the additional driver (Broadcom STA for wireless driver) for the laptop's wireless feature, an error message keeps coming up halting the installation. Honestly, I don't understand what the message means.

I've attached screenshots of what I was trying to install and of the error message. I hope someone can explain to me the next steps I should take.

---

### Post by mikewhatever on 2011-06-05
The message is saying, look at the log:

```
cat /var/log/jockey.log
```

Jockey.log is just a text file, possibly with clues of what went wrong.

---

### Post by mafaldaspeaks on 2011-06-05
> **mikewhatever said:**
> The message is saying, look at the log:

```
cat /var/log/jockey.log
```

Jockey.log is just a text file, possibly with clues of what went wrong.

Thanks, I found the text file but I don't really understand what it all means. I'm attaching it here. I hope you can help me understand it.

---

### Post by mikewhatever on 2011-06-06
To be honest, I don't know what it means either. Try installing the driver from a teminal with the following command:
```
sudo apt-get install bcmwl-kernel-source
```
Hopefully, the output will be more meaningful.

---

### Post by mafaldaspeaks on 2011-06-06
> **mikewhatever said:**
> To be honest, I don't know what it means either. Try installing the driver from a teminal with the following command:
```
sudo apt-get install bcmwl-kernel-source
```
Hopefully, the output will be more meaningful.
Thanks for replying. I did what you suggested and this is what I got:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Would you have any other ideas?

---

### Post by mikewhatever on 2011-06-06
I take it that it still doesn't work, so try purging it and then reinstalling:
```

sudo apt-get purge bcmwl-kernel-source

sudo apt-get install bcmwl-kernel-source
```

---

### Post by mafaldaspeaks on 2011-06-07
> **mikewhatever said:**
> I take it that it still doesn't work, so try purging it and then reinstalling:
```

sudo apt-get purge bcmwl-kernel-source

sudo apt-get install bcmwl-kernel-source
```
I did the first code and below is what came out. I'm getting more baffled :(

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,367 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134461 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules

Error! There are no instances of module: bcmwl
5.100.82.38+bdcom located in the DKMS tree.
dpkg: error processing bcmwl-kernel-source (--purge):
 subprocess installed pre-removal script returned error exit status 3
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

