---
title: "Edgy and VMware Server"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by FrankVdb on 2006-11-01
I've upgraded to Edgy and, in the process, got rid of a connection lag on my wireless laptop. However, upgrading brought me another problem. I've spent almost the whole day trying to get VMware Server installed on Edgy but it simply doesn't work.

The error I get after installing is:
"Starting VMware httpd.vmware:-ne     failed".

I've patched the installation for a known bug with a script I downloaded from vmware.com, but the error remains. 

Whenever I start Applications>VMware Server Console, the programme hangs and nothing happens. It uses 100% CPU power and needs two be killed twice before it is really dead. :???: 

I also installed the browser user interface, but it doesn't show up anywhere, nor do I have a starter to launch it...

I've been searching the net for hours, trying this en trying that. Maybe I should downgrade back to Dapper...

Anyone with a similar experience? Most people seem to get the VMware stuff installed without many problems... 

BTW, I followed this tutorial to install VMware Server: 
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

Thanks for any input.

---

### Post by thoolihan on 2006-11-01
Have you tried rerunning the install or config script?  Edgy uses a new kernel version which would require the kernel modules to be rebuilt for vmware.

---

### Post by FrankVdb on 2006-11-01
Yes I re-ran both.

---

### Post by aroswald1977 on 2006-11-01
> **FrankVdb said:**
> I've upgraded to Edgy and, in the process, got rid of a connection lag on my wireless laptop. However, upgrading brought me another problem. I've spent almost the whole day trying to get VMware Server installed on Edgy but it simply doesn't work.

The error I get after installing is:
"Starting VMware httpd.vmware:-ne     failed".

I've patched the installation for a known bug with a script I downloaded from vmware.com, but the error remains. 

Whenever I start Applications>VMware Server Console, the programme hangs and nothing happens. It uses 100% CPU power and needs two be killed twice before it is really dead. :???: 

I also installed the browser user interface, but it doesn't show up anywhere, nor do I have a starter to launch it...

I've been searching the net for hours, trying this en trying that. Maybe I should downgrade back to Dapper...

Anyone with a similar experience? Most people seem to get the VMware stuff installed without many problems... 

BTW, I followed this tutorial to install VMware Server: 
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

Thanks for any input.

Same mess here.. I couldnt run codeforge in the new eft, so i decided to run the old dapper in vmware... guess what? vmware server wont work either.

the install runs fine and I can start vmware from the prompt, but when I try to power on a machine, it just hangs and eats up the cpu.

I may have to dual boot 6.06 and 6.10 until I can get these both working in eft.

I'm still working on the problem, and will let you know as soon as I figure something out.

Eft uses something other than inittab, and that may be the root of my problem.:-k

---

### Post by sebbe1991 on 2006-11-01
It is a bug with having two libdbus .. just uninstall libdbus-1-2
```

sudo apt-get remove libdbus-1-2

```

Edit: libdbus-1-2 not libdbus-1.2

---

### Post by FrankVdb on 2006-11-02
Doesn't work either:
E: Couldn't find package libdbus-1.2

I appreciate your help guys, I'll let you know as soon as I find a solution...

---

### Post by FrankVdb on 2006-11-02
Finally, I got it solved... 

The problem was indeed the double library. The lib name was libdbus-1-2 (not libdbus-1.2), but the double did prove to be the problem.
I had a libdbus-1-2 and a libdbus-1-3 library on my system. After removing the libdbus-1-2 library, VM server fires up nicely. 

What a relief, thanks a lot Sebbe!

---

### Post by dentaku65 on 2006-11-02
See my post here
[http://yep.it/?3mnpef](http://yep.it/?3mnpef)
how to get vmware works on edgy :cool:

---

### Post by hikaricore on 2006-11-02
> **FrankVdb said:**
> Doesn't work either:
E: Couldn't find package libdbus-1.2

I appreciate your help guys, I'll let you know as soon as I find a solution...

> **FrankVdb said:**
> Finally, I got it solved... 

The problem was indeed the double library. The lib name was libdbus-1-2 (not libdbus-1.2), but the double did prove to be the problem.
I had a libdbus-1-2 and a libdbus-1-3 library on my system. After removing the libdbus-1-2 library, VM server fires up nicely. 

What a relief, thanks a lot Sebbe!

thank you both, this fixed my problem as well :)  it also removed libnautilus-burn3 but I don'treally use cd buring in nautilus anyway.

cheers

---

### Post by saumilshah on 2006-11-04
A simple solution for me was to change the /bin/sh symlink from "dash" to "bash".

rm -f /bin/sh
ln -s /bin/bash /bin/sh

httpd.vmware now runs properly.

My next problem is that "root" is not allowed to authenticate in VMware MUI.  I shall have to waste a few hours over mucking around with PAM and "security restrictions".

---

### Post by spidernik84 on 2006-11-04
AHA YES!!! Great, that did the trick, thank u so much sebbe ;)

---

