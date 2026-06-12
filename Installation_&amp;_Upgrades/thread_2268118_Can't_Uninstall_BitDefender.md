---
title: "Can't Uninstall BitDefender"
date: 2015-03-06
forum: Installation &amp; Upgrades
---

### Post by adam_dickens on 2015-03-06
Hello,

Im very new to Ubuntu/LInux and i tried installing BitDefender but i dont think i done it correctly. EAch time i try to install something from the SOftware Centre i get the following (picture/attachment). I have tried installing the software manager but it wont let me. I have tried the following cmds in terminal aswell with no luck:

sudo apt-get remove BitDefender-Scanner
sudo apt-get purge BitDefender-Scanner
sudo apt-get purge BitDefender-Scanner-GUI
sudo apt-get purge BitDefender-Scaner BitDefender-Scanner-GUI

[FONT=arial]i get the following errors with the above: [/FONT]
find: ‘/opt/BitDefender-scanner/share/locale’: No such file or directory
dpkg: error processing package bitdefender-scanner (--remove):
 subprocess installed post-removal script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

[ATTACH=CONFIG]260489[/ATTACH]

---

### Post by yancek on 2015-03-06
From what I have read about BitDefender, only the business edition will work on Linux.  Did you buy the business edition?  The message you are seeing is for  ClamTK which is another piece of antivirus software which will run on Linux.  More details on what you did, if you installed BitDefender, which version and how you did it.

---

### Post by sammiev on 2015-03-06
If you have Synaptic installed, do a search for bitdefender and select remove.

---

### Post by slickymaster on 2015-03-06
What happen to your **/opt/BitDefender-scanner/share/locale **file? Did you delete it?

Probably the easiest way is to re-install the Bitdefender package to restore missing files and folders and then uninstall it.

---

### Post by sammiev on 2015-03-06
> **yancek said:**
> From what I have read about BitDefender, only the business edition will work on Linux.  Did you buy the business edition?  The message you are seeing is for  ClamTK which is another piece of antivirus software which will run on Linux.  More details on what you did, if you installed BitDefender, which version and how you did it.

Bitdefender has a free version for Linux, I have been using it for years.

---

### Post by adam_dickens on 2015-03-06
its the free version of bitdefender and i have tried installing Synaptic as it comes up with the same error as in picture. struggling to reinstall bit defender too

is there not a cmd i can input to get rid of it??

---

### Post by sammiev on 2015-03-06
To install [Bitdefender]("http://linuxg.net/how-to-install-bitdefender-on-ubuntu-13-04-raring-ringtail-and-linux-mint-15-olivia/") I used this.

---

### Post by slickymaster on 2015-03-06
> **adam_dickens said:**
> is there not a cmd i can input to get rid of it??
Did you tried my suggestion, [here]("http://ubuntuforums.org/showthread.php?t=2268118&p=13240499&viewfull=1#post13240499")?

---

### Post by adam_dickens on 2015-03-06
i only installed ubuntu yesterday as a dual boot with windows. is it easy just to to a system recovery or restore back to yesterday? or would this ruin the dual boot?

i think the issue is i didnt install as deb file instead i done it as rpm. this may be whats causing the issue and it didnt install properly but there are traces of it still which i cant remove

---

### Post by slickymaster on 2015-03-06
How did you install that rpm package? Did you converted into deb with Alien? Converting rpms with alien works, but it's really not the best option.

Why on earth did you use an rpm package?

---

### Post by adam_dickens on 2015-03-06
ok so i have installed the correct bitdefender version for ubuntu and have installed synaptic. can you talk me through how to remove the 32bit (wrong) version please

---

### Post by sammiev on 2015-03-06
I really haven't played around much with rpm, so I'm not much help on removing such an failed install of one. Likely others will come by with more info.

---

### Post by slickymaster on 2015-03-06
Thing is, the way you install it in the first place is not the recommended way to install software packages in Ubuntu. If at all possible, install packages from Ubuntu's repositories using Add/Remove, apt-get, or the Synaptic Package Manager.
Package dependency conflicts may occur when attempting to install RPM packages. The Synaptic Package Manager may be able to fix or remove any broken packages.

---

### Post by Dave_M. on 2015-06-17
I removed mine just now by doing the following:

```
sudo find / -type f -iname "bitdefender*"
```

And then delete everything found manually on the command line.  NOTHING else I did would let me remove it all.  Now I can install anything I want without that last bit about how I have to tackle removing bitdefender first.  Done.

---

