---
title: "Ubuntu crashes on upgrade"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by kristine12 on 2010-04-07
Help! I'm having problem on upgrading my Ubuntu distribution. The image I've uploaded will show the error prompt I've got.

[IMG]http://i303.photobucket.com/albums/nn152/x_x312/Prob.png[/IMG]

Thank you in advance to those who will help!

---

### Post by whoop on 2010-04-07
Have you tried what apt suggested?
```

sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
sudo dpkg --configure -a

```

---

### Post by kristine12 on 2010-04-07
Yes! I've tried it but same error occurs. 
This is the output of the code you've post:

[INDENT]dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' ![/INDENT]

---

### Post by whoop on 2010-04-07
Oops, it's supposed to be configure not reconfigure...
No harm done.
Try again...

sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
sudo dpkg --configure -a

---

### Post by kristine12 on 2010-04-07
Trying it!

---

### Post by kristine12 on 2010-04-07
> **whoop said:**
> Oops, it's supposed to be configure not reconfigure...
No harm done.
Try again...

sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
sudo dpkg --configure -a

[INDENT]Setting up samba-common (2:3.3.2-1ubuntu3.4) ...

Setting up smbclient (2:3.3.2-1ubuntu3.4) ...
Setting up ubuntu-desktop (1.140) ...
[/INDENT]

I think that do the trick! Thanks for your effort. You are highly appreciated! :)


Five star for the answer! ^_^
:KS :KS :KS :KS :KS

---

### Post by whoop on 2010-04-07
> **kristine12 said:**
> 

I think that do the trick! Thanks for your effort. You are highly appreciated! :)


Five star for the answer! ^_^
:KS :KS :KS :KS :KS

hehe, no problem :)

---

