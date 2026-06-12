---
title: "vmware doesn't start..."
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Mr.Fahrenheit on 2007-05-22
Hello,

I'm nearly a complete newbie at linux, so it's very likely I've done something wrong.

I installed vmware through automatix, and whenever I attempt to start the program, it appears to be loading something for roughly 30 seconds, then nothing happens. What's going on here?

---

### Post by compiledkernel on 2007-05-22
In a terminal type vmware-server-console, 

what output do you recieve?

---

### Post by Mr.Fahrenheit on 2007-05-22
I got this:
```
bash: vmware-server-console: command not found
```

---

### Post by compiledkernel on 2007-05-22
hmmmm, 

what about what happens when you type 

vmware

---

### Post by Mr.Fahrenheit on 2007-05-22
```
ldd: /usr/lib/vmware-player/bin/vmware: No such file or directory
/usr/lib/vmware-player/lib/wrapper-gtk24.sh: 299: /usr/lib/vmware-player/bin/vmware: not found
ldd: /usr/lib/vmware-player/bin/vmware: No such file or directory
/usr/lib/vmware-player/lib/wrapper-gtk24.sh: 353: /usr/lib/vmware-player/bin/vmware: not found

```

---

### Post by compiledkernel on 2007-05-22
Id have to refer you back to [http://getautomatix.com](http://getautomatix.com) for support at this point. 

Im assuming that it installed VMplayer in some capacity causing the issue. 

What I would recommend from here is 

sudo apt-get remove vmplayer (or use automatix to uninstall it) 

and follow this guide. 

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

---

### Post by Mr.Fahrenheit on 2007-05-22
Thanks, I'll try that.

---

