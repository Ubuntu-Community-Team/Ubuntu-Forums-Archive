---
title: "I can't get xp to recognize my ubuntu os no matter what i try"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-24
i have tried everything i could possibly think of even tried in [Networking  & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") forum and nothing i still can't get xp to recognize ubuntu desite the fact that i have managed to share internet connection between the ubuntu to xp but xp still don't recognize netbios name and i still can't share files because of it.

is it possiblem that lucid has uniq problems with networking?

thanks in advance.

---

### Post by ubername on 2010-03-24
You will need to describe in a lot more detail exactly what your problem is. I can not work out what you are asking. When you say xp does not recognise ubuntu, are you saying you have a network with multiple machines on, some of which are running xp, some ubuntu, and the xp machines cannot see the ubuntu machines? Or is it something different? Please be as clear as your level of expertise allows, including any error messages you get.

---

### Post by aviramof on 2010-03-24
i have one machine with xp one with ubuntu they are connected via crossover cable each computer with it's own network card and that it when i enter windows seven in my computer the one with the ubuntu everything is working smoothly becaue the xp is already configured properly i gave xp the ipv4 address 192.168.137.2 and seven\ubuntu 192.168.137.1 in ubuntu i added that address to wire in nm-connection-editor and enabled internet sharing via firestarter but i can't see netbios name in xp networks and i can't share file because of it.

and also i can't access my ubuntu remotly via rdp not from my own xp machine and not from remote xp's machines.

now i have installed samba and samba4 and everything related to them and tried everything i can try in smb.conf and nothing every now and then i can see ubuntu in xp as netbios but i don't know how to replicate it because setting home as workgroup in smb.conf don't seem to be enaf and even then i can't enter shared folders.

and i also can't share printer i managed to install it once via ubuntu and get an open port but it still wasn't printing from my xp machine.

basicly you really need to work a lot about networking in ubuntu because at the moment it's terrible because i'm trying more then a week to get it to work properly to share files,internet connection and printer with no luck except the internet and that's only because i did it via firestarter and not by any file like smb.conf.

---

### Post by garvinrick4 on 2010-03-24
> **aviramof said:**
> i have one machine with xp one with ubuntu they are connected via crossover cable each computer with it's own network card and that it when i enter windows seven in my computer the one with the ubuntu everything is working smoothly becaue the xp is already configured properly i gave xp the ipv4 address 192.168.137.2 and seven\ubuntu 192.168.137.1 in ubuntu i added that address to wire in nm-connection-editor and enabled internet sharing via firestarter but i can't see netbios name in xp networks and i can't share file because of it.

and also i can't access my ubuntu remotly via rdp not from my own xp machine and not from remote xp's machines.

now i have installed samba and samba4 and everything related to them and tried everything i can try in smb.conf and nothing every now and then i can see ubuntu in xp as netbios but i don't know how to replicate it because setting home as workgroup in smb.conf don't seem to be enaf and even then i can't enter shared folders.

and i also can't share printer i managed to install it once via ubuntu and get an open port but it still wasn't printing from my xp machine.

basicly you really need to work a lot about networking in ubuntu because at the moment it's terrible because i'm trying more then a week to get it to work properly to share files,internet connection and printer with no luck except the internet and that's only because i did it via firestarter and not by any file like smb.conf.
I do know that setting up a Windows workgroup in 7 and adding xp machine and using samba on Ubuntu install works like a charm and virtually sets itself up as a Windows Workgroup. Using wired or wireless can see all devices/media/printers the works. Must have a password installed in Window installs to make Windows a workable network.

---

### Post by aviramof on 2010-03-24
i disabled the need for password in xp and enabled empty passwords the problem is not the xp it's the ubuntu either it's smaba and lucid or that i'm doing something wrong but i tried everything i could think of and still it doesn't work well ubuntu don't let me share folder and don't even provide netbios name properly to xp.

---

