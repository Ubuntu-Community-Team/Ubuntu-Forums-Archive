---
title: "help. problem with my update"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by miko16 on 2008-10-12
guys, need help. i installed a limewire on my ubuntu gutsy, but it failed to continue. now i cannot access the synaptic package manager.
this message appears 

There is another synaptic running in non-interactive mode. Please wait for it to finish first.

but there is nothing running with that. and also i cannot update my system anymore.. this message appears when i install the update.

An error occured

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



how do i correct this guys? thank you..

---

### Post by Elfy on 2008-10-12
The problem with that error message is that it assume you were root when you were working with the packages (which you were, synaptic opens with root rights) so you need to become root to run the command - and any that affect the system, you need to use sudo, open a terminal from accessories - it will need your normal password to continue.

Password will not appear when you type it - it is there though.

```
sudo dpkg --configure -a
```

---

### Post by miko16 on 2008-10-12
> **forestpixie said:**
> The problem with that error message is that it assume you were root when you were working with the packages (which you were, synaptic opens with root rights) so you need to become root to run the command - and any that affect the system, you need to use sudo, open a terminal from accessories - it will need your normal password to continue.

Password will not appear when you type it - it is there though.

```
sudo dpkg --configure -a
```


after i entered that this message appears 
Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place


after that i run the update manager. this message appears 

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

what should i do next?:(

---

### Post by Partyboi2 on 2008-10-12
In a terminal do as it suggests, type
```
sudo apt-get install -f
```

---

### Post by miko16 on 2008-10-12
thank you peeps. you guys really help me a lot. my ubuntu is fine now. thanks

---

