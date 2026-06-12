---
title: "[Kubuntu 8.10 RC] - where is resolv.conf?"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Asham on 2008-10-24
I just installed the RC as a virtual machine but it seems the file system does not contain "resolv.conf" in the dir "/etc" -- how come? I see there's a folder named "resolvconf"... hmm, is this a mistake or am I missing something?

To install I used the desktop i386 iso file.

---

### Post by kartoshka on 2008-10-24
I believe if it is not there, just create it.

```
touch /etc/resolv.conf
```

---

### Post by Asham on 2008-10-24
I thought it would be there after the installation. :confused:

The file was created when I added a connection from the network manager. I believe your advice would work too. I'll try that for the server installation later. :)

---

### Post by kartoshka on 2008-10-24
Ok just realized resolv.conf is indeed there on my machine. "ls -la /etc/" confirms. Must be a hidden file.

From [http://tldp.org/LDP/nag/node84.html](http://tldp.org/LDP/nag/node84.html)

> When configuring the resolver library to use the BIND name service for host lookups, you also have to tell it which name servers to use. There is a separate file for this, called resolv.conf. If this file does not exist or is empty, the resolver assumes the name server is on your local host.

So if the file really doesn't exist on your machine and you need to specify a nameserver, "sudo nano /etc/resolv.conf" and add:

```
nameserver [nameserver's IP address]
```

---

### Post by Asham on 2008-10-24
I don't think it was hidden but I could be wrong. I usually am. ;)

I use the tab key for filename auto completion in the terminal since I'm rather used by it now, yet I got no matches. After I added a connection with knetmanager the file appeared.

---

### Post by caryb on 2008-10-24
I just checked my resolv.conf & it's there & not hidden. It has my dns servers it picked up from DHCP


Cary

---

