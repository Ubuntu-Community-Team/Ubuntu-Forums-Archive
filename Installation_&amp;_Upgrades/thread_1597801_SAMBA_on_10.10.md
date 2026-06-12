---
title: "SAMBA on 10.10"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by venik212 on 2010-10-15
I run a print server, and print on it remotely from another machine.  After I upgraded from 10.04 to 10.10 (gnome) on both the client and the servber, the remote machine had no printers.  I tried to restart SAMBA, and discovered that 
sudo /etc/init.d/samba restart 
did not work, although SAMBA was installed.  I went to:
[http://www.unixmen.com/linux-distributions/4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-](http://www.unixmen.com/linux-distributions/4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-)
and tried to follow that HOWTO, but when I click: System-->Adminitration-->SAMBA nothing happens: I see "Starting Samba" at the bottom of the screen, but that is all.  At some point it actually asked me for a password, but then died.
CUPS does not work at all, so I cannot print remotely as I did before 10.10.
What is going on?  Is 10.10 really ready to be used?
Thanks for any help.

---

### Post by luvshines on 2010-10-15
> **venik212 said:**
> I tried to restart SAMBA, and discovered that 
sudo /etc/init.d/samba restart 
did not work, although SAMBA was installed. 
I see "Starting Samba" at the bottom of the screen, but that is all.  At some point it actually asked me for a password, but then died.


You mean /etc/init.d/smbd, right ??
What does it say when you try to restart.

Also after you do a restart, see if it is running or not:
```
ps aux | grep smbd
```

---

### Post by venik212 on 2010-10-16
That worked.  I note, however, that in the past I used to use
sudo /etc/init.d/samba restart
and that is what the HOWTO recommends as well.  I guess Ubuntu is trying to keep us on our toes.
BTW-- CUPS is still broken, so I cannot print.  When I try it, I get: Cannot connect to localhost.. etc.

---

### Post by luvshines on 2010-10-16
> **venik212 said:**
> 
BTW-- CUPS is still broken, so I cannot print.  When I try it, I get: Cannot connect to localhost.. etc.

I haven't worked with printer on Samba.
But what does these commands say:
```
smbclient -L <server-ip> -U<username>%<userpasswd>
testparm -sp
```

---

### Post by venik212 on 2010-10-17
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.5.4]
tree connect failed: NT_STATUS_ACCESS_DENIED

---

### Post by luvshines on 2010-10-17
Is it guest share or username/passwd protected ?

---

