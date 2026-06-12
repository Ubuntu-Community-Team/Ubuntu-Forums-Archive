---
title: "Installing Doom 3 from Steam in LINUX!"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by cybermatthieu on 2010-08-25
Since we're still waiting for a NATIVE Linux client... :(

I've fooled around a bit to make the Steam version of Doom 3 work in Linux.

**Step 1 - Getting your cdkeys**
Install Doom 3 in Steam
Start the game
Once the game has started, exit it

Fire up regedit (Start->run type in regedit)
Check theses keys.

For Doom 3:
```
HKEY_CURRENT_USER\Software\Valve\TestApp9050\SteamKey
```

For Resurrection of Evil:
```
HKEY_CURRENT_USER\Software\Valve\TestApp9070\SteamKey
```

Copy the keys in a text file and save it on your drive. (but you could always note it down)

Reboot in Linux.

**Step 2 - Installing Doom 3 in Linux**

Download the latest version of Doom 3 from id Software's ftp.
[ftp://ftp.idsoftware.com/idstuff/doom3/linux/]("ftp://ftp.idsoftware.com/idstuff/doom3/linux/")

Start a terminal.

Make the downloaded file executable and execute it:
```
chmod +x doom3-linux-x.x.xxxx.x86.run
sudo ./doom3-linux-x.x.xxxx.x86.run

```

Mount your Windows partition.
```
sudo mount /dev/<your windows drive:parition> /media/WINDOWS
```

Copy the missing base files.
```
cd /usr/local/games/doom3/base/
sudo cp /media/WINDOWS/Program\ Files\ \(x86\)/Steam/steamapps/common/doom\ 3/base/pak00*.pk4 .
```

Copy the missing d3xp files.
```
cd /usr/local/games/doom3/d3xp/
sudo cp /media/WINDOWS/Program\ Files\ \(x86\)/Steam/steamapps/common/doom\ 3/d3xp/pak000.pk4 .
```

Start the game.
```
doom3
```

Enter your cdkeys and enjoy! :cool:

I've based this small tutorial on this Ubuntu doc:
[https://help.ubuntu.com/community/Doom3]("https://help.ubuntu.com/community/Doom3")

Here's a good reference to fine tune your config:
[http://www.widescreengaming.net/wiki/Doom_3]("http://www.widescreengaming.net/wiki/Doom_3")

---

### Post by kiddykoff on 2011-07-23
Going to try this out. will post afterwards.

---

### Post by kiddykoff on 2011-07-23
Alright, so i started Doom3 but is there anyway to run it as a normal user rather than Administrator?

It doesn't work for me without using sudo. here's my output
```
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface wlan0 - 192.168.1.2/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
WARNING: idFileSystemLocal::OpenFileRead: fs_caseSensitiveOS 1 could not open /usr/local/games/doom3/base/pak000.pk4
WARNING: idFileSystemLocal::OpenFileRead: fs_caseSensitiveOS 1 could not open /usr/local/games/doom3/base/pak001.pk4
WARNING: idFileSystemLocal::OpenFileRead: fs_caseSensitiveOS 1 could not open /usr/local/games/doom3/base/pak002.pk4
WARNING: idFileSystemLocal::OpenFileRead: fs_caseSensitiveOS 1 could not open /usr/local/games/doom3/base/pak003.pk4
WARNING: idFileSystemLocal::OpenFileRead: fs_caseSensitiveOS 1 could not open /usr/local/games/doom3/base/pak004.pk4
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/kurtis/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg

```

EDIT:
I figured out that one can run this
```
cd /usr/local/games/doom3/base/
sudo chmod a+r pak00*.pk4
```

---

