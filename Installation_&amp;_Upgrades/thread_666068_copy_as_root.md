---
title: "copy as root"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by Himie on 2008-01-12
hi im trying to install the splash theme that comes with mac4lin but i need to copy a file as root to /usr/lib/usplash

how do i copy as root?

---

### Post by oldos2er on 2008-01-13
sudo cp /path/to/file /destination

---

### Post by tgalati4 on 2008-01-13
I haven't used mac4lin (as I already have a powerbook so I don't need to emulate Tiger), but you might want to backup the existing files in usplash first.

Files in Dapper, Gutsy may have some differences.

>cd /usr/lib/usplash

>sudo cp  usplash-default.so  usplash-default.bak

Now copy the new usplash, say in your /home/youruser/mac4linstuf/usplash-default.so

>sudo cp /home/youruser/mac4linstuf/usplash-default.so .

I have a link (usplash-artwork.so -> /etc/alternatives/usplash-artwork.so) in the usplash directory that you may have as well).  You probably want to preserve it.

>cd /etc/alternatives

>sudo cp usplash-artwork.so usplash-artwork.bak

Now copy the new artwork file:

>sudo cp /home/youruser/mac4linstuff/usplash-artwork.so .

You might need to reboot to get the files to load.

Again, this is from a Dapper machine, so your Gutsy install may have differences, but the general procedure would be the same.

---

### Post by Himie on 2008-01-13
ok thx but what if i try to copy a whole folder, it tells me 'omiting directory'

---

### Post by zvacet on 2008-01-13
```
sudo cp -r <foldername> /path/to/file /destination
```

---

### Post by Himie on 2008-01-13
it tells me permission denied :(

---

### Post by zvacet on 2008-01-13
```
mv foldername /path/to/file /destination
```

You will not copy folder,just move to direcoty you want it to be.

---

### Post by Himie on 2008-01-13
ok yes i checked its move lol, but it keeps telling me:

```
mv: cannot stat `pidgin': No such file or directory
mv: cannot move `/home/himie/Desktop/Mac4Lin_v0.4/Pidgin' to `/usr/share/pixmaps/Pidgin': 
Permission denied

```

---

### Post by zvacet on 2008-01-14
Why didn´t you told it is on Desktop.

```
cd Desktop
```

```
sudo cp -r <foldername> /path/to/file /destination
```

---

### Post by Himie on 2008-01-14
lol i guess i missed some stuff, sorry but im new to the OS

---

### Post by Himie on 2008-01-14
mm i cant get it to work.. i have the folder 'pidgin' right in the desktop and i want to move it to /usr/share/pixmaps  can u tell me how to? lol sorry im noob at this :P

---

### Post by Himie on 2008-01-14
aww dam now i could get it but it tells me:

```
himie@himie-desktop:~/Desktop$ mv pidgin /home/himie/Desktop/pidgin /usr/share/pixmaps
mv: cannot move `pidgin' to `/usr/share/pixmaps/pidgin': Permission denied
mv: cannot move `/home/himie/Desktop/pidgin' to `/usr/share/pixmaps/pidgin': Permission denied
himie@himie-desktop:~/Desktop$ 
```

how can i get permission?

---

### Post by zvacet on 2008-01-14
I don´t understan why you want to move Pidgin in usr/share/pixmaps.that is the place to put icon in.Anyway you typed wrong command an I should be like this

```
cd Desktoop
```

```
cp -r pidgin /usr/share/pixmaps
```

And I don´t know is folder name Pidgin or pidgin.Use right one.

---

### Post by xc3RnbFO8P on 2008-01-14
You could use Pcman in Add/Remove (all avalible application)

Start Pcman go to tool > open current folder as root, now you have to Pcman open, browse

to desktop with Pcman (root) and the other to /usr/share/pixmaps, drag and drop.

---

### Post by Himie on 2008-01-14
i want to put it there for the pidgin theme that comes in mac4lin 
> 
[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p4](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p4)

11.2 Pidgin OSX Theme

Extract the theme archive(s) in the temporary folder. Now, as root, move the "pidgin" folder to /usr/share/pixmaps. Overwrite the existing one after taking a backup. This will install the OS X Theme for Pidgin.

---

### Post by rafttrip on 2008-05-30
Is there a way to do this in the file browser?

---

### Post by dje on 2008-05-30
To open nautilus (file browser) as root press Alt + F2 and type:
```
gksu nautilus /usr/share/pixmaps
```
That opens nautilus as root and goes to /usr/share/pixmaps

hope that helps,
dje

---

