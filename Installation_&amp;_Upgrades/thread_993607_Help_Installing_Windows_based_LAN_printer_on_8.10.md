---
title: "Help Installing Windows based LAN printer on 8.10"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by mrmagill on 2008-11-25
I'm a technology teacher with minimal Linux experience. Using Ubuntu 8.10 which installed flawlessly after I found a compatible box. I need to have Ubuntu print to a shared printer, but don't know enough yet to know where to look for help. I've searched forums various ways, but am not finding it. I need to solve this issue quickly, as it's the only thing in my immediate way of using Ubuntu for my students. 

Particulars: Distro is Ubuntu 8.10
System: Pentium 4 PC, about 40GB free, and a gig of memory.
Printer: Installed on Windows 2000 Server, it's an HP 820CSE. 
Other system issues/Problems: None at all!:)

Can someone get me pointed in the right direction? Once this is out of the way I can take my time learning the rest. Only other thing I really need is a good typing tutor for middle-school age kids (8-12 years old)

Mark Magill
Kingsview Christian School
North Bend, Oregon USA

---

### Post by theozzlives on 2008-11-25
1.Install samba
```
sudo apt-get install samba
```
1.Make sure you belong to the right workgroup
```
sudo gedit /etc/samba/smb.conf
```
3.look under "global" for workgroup=
4.make sure your windows printer is shared
5.go to system-administrative-printing
6.add new printer, select windows, smb printer... browse to the printer and follow the instructions from there

---

### Post by mrmagill on 2008-11-25
> **theozzlives said:**
> 1.Install samba
```
sudo apt-get install samba
```

Thank you for such clear, concise, and speedy instructions. I saw mention of Samba when I created a launcher to a spreadsheet my aide was using on the server, the property started "smb:/pathname" and it mentioned Samba. That the same thing you're talking about here?

Mark

PS: 18 minutes from question to answer... Not bad... :)

---

### Post by deeaycee on 2009-01-16
If only it was that easy.

I've been looking for an answer to this question for over a month. I feel like I've tried every possible thing. I actually got this to work on a 8.10 box for about 10 days and it mysteriously quit working. I have NO idea how I did it. 

-basic home network with 2 win boxes, and 2 ubuntu intrepid boxes
-hpG85 printer on one of the win boxes thats always on and printer IS shared
-I can't see nix to win through nautilus, but can through a web browser pointed at the ip
-I can see win to win
-I can see nix to nix
-I can see win to nix

I can't even remember if I saw that this is a known bug. I'm ready to stick a cheapo printer next to the nix box that needs printing and forget samba

this is the biggest problem i've had since switching to 8.10

---

