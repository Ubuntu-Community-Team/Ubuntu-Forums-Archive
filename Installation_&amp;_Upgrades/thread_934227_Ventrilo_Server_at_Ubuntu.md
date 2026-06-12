---
title: "Ventrilo Server at Ubuntu"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by Hardmann on 2008-09-30
Hello all.

I am not sure if this is the right place for this thread, but i am new XD ..
I am looking for some solution to my problem with Ventrilo server..

I wanna run a ventrilo server at my ubuntu mashine, but i cant get it working.. i have downloaded the Windows version, and installed it by "WINE".. And evrything looks right, but when i try to start the Ventrilo Server program, it just dont show up.

Somene who can help a little ??


Hardman :)

---

### Post by jerome1232 on 2008-09-30
They have a linux version of the server, I run it very well on my Ubuntu server.

[http://www.ventrilo.com/dlprod.php?id=102](http://www.ventrilo.com/dlprod.php?id=102)

you just download, it extract it, cd ventsrv, ./ventrilo_srv


on a side note I haven't gotten the client program to work under wine, I'm sure it's possible but i'm happy with teamspeak and use that instead, it has a native client and server.

---

### Post by Hardmann on 2008-09-30
> **jerome1232 said:**
> They have a linux version of the server, I run it very well on my Ubuntu server.

[http://www.ventrilo.com/dlprod.php?id=102](http://www.ventrilo.com/dlprod.php?id=102)

you just download, it extract it, cd ventsrv, ./ventrilo_srv


on a side note I haven't gotten the client program to work under wine, I'm sure it's possible but i'm happy with teamspeak and use that instead, it has a native client and server.

Sorry my noobnish XD.
But cant you explain it a little more "chilish"?
I understand that they have a linix version, but, when i have downloaded that, what to do then? :D

---

### Post by jerome1232 on 2008-09-30
Okay, after downloading you probably end up with a .tar.gz file on your desktop, since it is a command line program I'm going to give you command line instructions on how to run it.

Pop open a terminal (Applications->Accessories->Terminal)
```
mv Desktop/ventrilo_srv-3.0.2-Linux-i386.tar.gz ventsrv.tar.gz
tar xzvf ventsrv.tar.gz
cd ventsrv
./ventrilo_srv
# Now your server is up and running! You'll have to consult it's help documentation to learn how to config it to your liking
```

Some explanation of my commands

'mv Desktop/ventrilo_srv-3.0.2-Linux-i386.tar.gz ventsrv.tar.gz'
moves the file you downloaded to your home directory and renames it to ventsrv.tar.gz to save on typeing


'tar xzvf ventsrv.tar.gz'
Extracts, decrompresses, and tells you what files are being extracted from the archive

'cd ventsrv
./ventrilo_srv'
changes into the new ventsrv directory that was created when you extracted the archive, then executes the ventrilo server.

---

### Post by Hardmann on 2008-09-30
> **jerome1232 said:**
> Okay, after downloading you probably end up with a .tar.gz file on your desktop, since it is a command line program I'm going to give you command line instructions on how to run it.

Pop open a terminal (Applications->Accessories->Terminal)
```
mv Desktop/ventrilo_srv-3.0.2-Linux-i386.tar.gz ventsrv.tar.gz
tar xzvf ventsrv.tar.gz
cd ventsrv
./ventrilo_srv
# Now your server is up and running! You'll have to consult it's help documentation to learn how to config it to your liking
```

Some explanation of my commands

'mv Desktop/ventrilo_srv-3.0.2-Linux-i386.tar.gz ventsrv.tar.gz'
moves the file you downloaded to your home directory and renames it to ventsrv.tar.gz to save on typeing


'tar xzvf ventsrv.tar.gz'
Extracts, decrompresses, and tells you what files are being extracted from the archive

'cd ventsrv
./ventrilo_srv'
changes into the new ventsrc directory that was created when you extracted the archive, then executes the ventrilo server.

'
I have tryed that now, but at the first command, it says "No such dictory" bla bla bla ...
But the file is on the desktop :s

---

### Post by Hardmann on 2008-09-30
oh, hold on. i think i got it working.. just moved it to my home folder manualy.. 

2min

---

### Post by jerome1232 on 2008-09-30
Linux is case sensitive, are you using a capital D instead of a lowercase d?

try using autocompletion (using the tab key)

try mv Des[hit tab now]\ven[hit tab again]

edit: Drag and drop works too :)

---

### Post by Hardmann on 2008-09-30
Where can i se what the IP adress is and the port number? :)

---

### Post by jerome1232 on 2008-09-30
if you browse into your ventsrv directory there is a .html file that tells you how to config ventsrv, for the most part you can just use a text editor and set your options in the .ini file

default port number is 3794

(likely) if you are connected to a router  you can go [here]("http://whatismyip.org/") to see your ip, you will also need to config your router to forward port 3794 if you want people to connect to your server.

(less likely) If you are connected directly to a modem, the command ifconfig will give your ip address.

---

### Post by Hardmann on 2008-09-30
Everything works like a charm XD
Thanks for the help. 

Have a really nice day ..

---

