---
title: "can't start azureus"
date: 2006-03-17
forum: Installation &amp; Upgrades
---

### Post by dus_10 on 2006-03-17
i described this problem in a different thread i made, but decided to just start a new one in case i get help and someone else has this problem they can find it.  ok, so i got azureus through automatix and started it, i then installed these 2 updates that it wanted me to download, one of the was the newest version of azureus and i dont remember what the other file said.  so then i restarted azureus only to get another update download prompt, so this time it was something like gtw, or gwk or something like that ? im not for sure because i dont pay attention to update downloads, so then it tells me to restart azureus again and i click 'restart' in the azureus menu.  now azureus wont start, i have no clue what to do, i tried re-running automatix and downloading and installing azureus again, but it still doesnt start, any help would be awesome, thanks

---

### Post by PhoenixP3K on 2006-03-17
I would uninstall it completely and use the step by step instructions found on [EasyLinux concerning Azureus in Ubuntu]("http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29") But instead get the latest version from the website [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) And correct the instructions accordingly to the file name.

So by downloading it you would then open a terminal and go to where you saved the file then:
```

sudo tar jxvf Azureus_2.4.0.2_linux.tar.bz2 -C /opt
sudo gedit /usr/share/applications/azureus.desktop
```
Add the following to the new file: 
```

[Desktop Entry] 
Name=Azureus
Comment=A Bittorrent client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;
```
Save the edited file 
Applications -> Internet -> Azureus 

You might need to refresh the Gnome menus with **killall gnome-panel**

---

### Post by altonbr on 2006-05-01
I had the same problem but the restart worked after the second time.

I then followed you instructions PheonixP3K and re-installed Azureus... all my broken torrents were still there, so I assume there was some hidden meta file that didn't get uninstalled.

Anyway, I have this error: "Error: Operation not permitted, setLength fails (allocateFiles new:___filename____)". The hard drive it is trying to save to is a fat32 format, shared with windows... the permission say 777 - root... so I really have no guess as to why this error occuring.

Also is there anyway to add Azureus to "Open with: " pop-up in firefox's download manager? Where is the program situated? /opt/azureus/azureus ... is that what I add to the pop-up menu? Thanks for your time.

---

### Post by altonbr on 2006-05-02
The updating also has something to do with permissions... how do I let Azureus update as root?

---

### Post by Serguei_89 on 2006-07-28
Here is how I fixed my problems with Azureus. In dapper 6.06 though, but should work here I hope.

I installed with Automatix and had problem installing updates from azureus.

This I fixed by changing ownership of everything in /opt/azureus folder to my username.

$cd /opt
$sudo chmod <username> Azureus

repeat for anything inside there that causes error when updating.

Second problem I had is downloading to a fat32 partition. 

And while almost everywhere people talk about changing fstab file or permitions to the mounted partition, there is a simple option in Azureus in Tools->Options->Files->Enable incremental File creation. Worked like a charm for me.

Hope this helps.

---

### Post by pierrebnh on 2006-09-24
I think it's ```
$sudo chown *username* /opt/azureus -R
```

---

### Post by blackened on 2006-09-24
If there is an update for azureus, I usually start azureus as superuser, install the update, then restart as normal user. Since I use sudo for a short period of time this seems safer than editing the /opt/azureus permissions permanently.

---

### Post by arnieboy on 2006-09-24
> **blackened said:**
> If there is an update for azureus, I usually start azureus as superuser, install the update, then restart as normal user. Since I use sudo for a short period of time this seems safer than editing the /opt/azureus permissions permanently.

I would recommend the same.
whenever a new update comes up do the following:
close azureus and then from terminal do:
```
sudo azureus
```
install the updates and then close it and then run azureus as normal user.
Please do not change permissions in the azureus install folder.

---

