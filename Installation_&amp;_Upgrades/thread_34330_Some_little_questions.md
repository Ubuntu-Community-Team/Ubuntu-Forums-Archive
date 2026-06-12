---
title: "Some little questions"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by LinxNew on 2005-05-14
Hi,

I've installed Hoary and I have some questions:

**Synaptic Package Manager :**
How can I install a new package ? I select it, but after...  :-? 
I would like to remove OOo 1.1.3 for 1.9.100. are there problem to remove it or other application ?

**root user :**
Can I give permission to my user to use 'll' command ? How ?

**Security/Firewall**
I haven't see any application (ex. shorewall) installed. Is there a good application to use ?
Can I use shorewall, or I must use other program ? What ?

**Totem**
- I try to play mp3 files, but I haven't any codec. What about xmms ? Is it better than Totem ?
- I try to play avi files, but I haven't any codec. is it correct to install libavcodec-dev from repositories ? is there some codec package that is better than other ?


I know. I'm newbie, so excuse me, for my little problem.

Thanks for all you support.

---

### Post by DJ_Max on 2005-05-14
For Synaptic, click apply.

If you need root privilegs, use sudo. Example
```
sudo reboot
```

You have iptables, which is all you need. Shorewall, Firestarter, KissMyFirewall all help you with configuring iptables.

I'm not exactly sure about all the codecs you need. Totem is more of a movie player.

---

### Post by kvidell on 2005-05-14
[QUOTE=LinxNew]Hi,

I've installed Hoary and I have some questions:

**Synaptic Package Manager :**
How can I install a new package ? I select it, but after...  :-? 
I would like to remove OOo 1.1.3 for 1.9.100. are there problem to remove it or other application ?

**root user :**
Can I give permission to my user to use 'll' command ? How ?

**Security/Firewall**
I haven't see any application (ex. shorewall) installed. Is there a good application to use ?
Can I use shorewall, or I must use other program ? What ?

**Totem**
- I try to play mp3 files, but I haven't any codec. What about xmms ? Is it better than Totem ?
- I try to play avi files, but I haven't any codec. is it correct to install libavcodec-dev from repositories ? is there some codec package that is better than other ?


I know. I'm newbie, so excuse me, for my little problem.

Thanks for all you support.[/QUOTE]
 To fix the codec issues (both MP3 and AVI/Indeo) do this:
```
sudo apt-get install w32codecs
```That should fix those. And XMMS is a much better MP3 player than totem. Totem is for movies, it doesn't do playlists. XMMS and Beep-Media-Player(which I prefer over XMMS) will play ogg, ape, aac, mp3, flac, etc... and they do playlisting.
- Kev

---

### Post by spd106 on 2005-05-14
Hi, to play propriety encoded files like mp3 you will need to install some plugins that can not be supplied by canonical ie by default. So you will have to add some universe/multiverse repositories.

Look at this guide for step by step instructions.
[http://ubuntuguide.org/](http://ubuntuguide.org/)

Good luck

---

### Post by az on 2005-05-14
You probaly do not need a firewall using ubuntu out-of-the-box.  If you run stuff you know is risky and want one, you can use firestarter.  Guarddog is also good.  Search synaptic for firewall and see what you have to pick from.

Enable the universe repository to get these, of course.

---

### Post by DutchLau on 2005-05-14
For your codecs do this follow the steps of the Ubuntu guide:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

At the Ubuntu guide website, there are also a list of other things you can do that will ease your life.

Good luck,

DutchLau

---

### Post by LinxNew on 2005-05-15
Thank you to all  :grin: 

I have another little question :

after I've installed ubuntu, I cannot see my win partition. 
I can insert manually in fstab my partition, or I must install nfs package to supporto NTFS file system ?

---

### Post by DutchLau on 2005-05-15
How do you mean you cannot see your windows partition? 

Type " sudo fdisk -l " (SUDO FDISK -L) to see if it's listed. Then take the partition and follow the steps of the Ubuntu guide for mounting the partition!

Good luck,

DutchLau

---

### Post by LinxNew on 2005-05-16
I see and it's listed. 
But can I set to mount my partition at boot ? 

My other question :

where I can see my services that start at boot ?
I would like to remove auto syncronize with ntp.ubuntulinux.org

---

### Post by Ali_Baba on 2005-05-16
You have to edit /etc/fstab file.There you can set  to mount your partition at boot.
You should first create a folder to be your mount point.
[http://www.ubuntuforums.org/showthread.php?t=34578](http://www.ubuntuforums.org/showthread.php?t=34578) here is a thread of that kind of problem :)

---

### Post by LinxNew on 2005-05-16
I've tried to install xmms from repositories (1.2 version) but when I load a mp3 xmms goes to spleeing... It's block...  :-? 

For services, is there a metod to select what automatically boot ?

---

