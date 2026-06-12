---
title: "File Dialog Box very very slow"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by tito_pt on 2010-01-20
Recently I updated My Ubunto instalation to the 9.10 and a few issus were solved (graphics driver is better!!), but now I have a wired problem, every time a file dialog box opens in any aplication the window freezes turns dimed and some times lasts for over 15 sec to open de folders list.
after a quick analisis I realized tha the problem is a few network shares I mouted in FSTAB if i comment them it works ok.

//192.168.6.6/F /media/DiscoI cifs auto,user,username=Agostinho,password=,uid=1000,gid=100,umask=0,rw 0 0
//192.168.6.5/F /media/DiscoH cifs auto,user,username=Agostinho,password=,uid=1000,gid=100,umask=0,rw 0 0 
//192.168.6.4/G /media/DiscoG cifs auto,user,username=Agostinho,password=,uid=1000,gid=100,umask=0,rw 0 0
//192.168.6.3/F /media/DiscoF cifs auto,user,username=Agostinho,password=,uid=1000,gid=100,umask=0,rw 0 0
//192.168.6.7/F /media/DiscoX cifs auto,user,username=Agostinho,password=,uid=1000,gid=100,umask=0,rw 0 0 
//192.168.6.4/Qmultimedia /media/Musicas cifs auto,user,username=Agostinho,password=,uid=1000,gid=100 0 0

Does any one know why these give the stranje behavier, on the file window box?

---

