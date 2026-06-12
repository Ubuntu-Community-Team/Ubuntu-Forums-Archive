---
title: "upgrade jammy 22.04 to kinetic 22.10 now no out side internet"
date: 2022-11-20
forum: Installation &amp; Upgrades
---

### Post by lance bermudez on 2022-11-20
upgrade jammy 22.04 to kinetic 22.10 now no out side internet. I can reach the other computer on my network just no outside stuff like updates or web cites.
error I get is
```

$ sudo apt update
Ign:1 https://downloads.plex.tv/repo/deb public InRelease
Ign:2 http://us.archive.ubuntu.com/ubuntu kinetic InRelease                        
Ign:3 http://security.ubuntu.com/ubuntu kinetic-security InRelease                 
Ign:4 http://repo.vivaldi.com/stable/deb stable InRelease              
Ign:5 http://us.archive.ubuntu.com/ubuntu kinetic-updates InRelease
Ign:6 http://us.archive.ubuntu.com/ubuntu kinetic-backports InRelease
Ign:2 http://us.archive.ubuntu.com/ubuntu kinetic InRelease
Ign:1 https://downloads.plex.tv/repo/deb public InRelease                          
Ign:3 http://security.ubuntu.com/ubuntu kinetic-security InRelease                 
Ign:4 http://repo.vivaldi.com/stable/deb stable InRelease              
Ign:5 http://us.archive.ubuntu.com/ubuntu kinetic-updates InRelease
Ign:6 http://us.archive.ubuntu.com/ubuntu kinetic-backports InRelease
Ign:2 http://us.archive.ubuntu.com/ubuntu kinetic InRelease
Ign:1 https://downloads.plex.tv/repo/deb public InRelease               
Ign:3 http://security.ubuntu.com/ubuntu kinetic-security InRelease      
Ign:4 http://repo.vivaldi.com/stable/deb stable InRelease
Ign:5 http://us.archive.ubuntu.com/ubuntu kinetic-updates InRelease
Ign:6 http://us.archive.ubuntu.com/ubuntu kinetic-backports InRelease
Err:1 https://downloads.plex.tv/repo/deb public InRelease
  Temporary failure resolving 'downloads.plex.tv'
Err:2 http://us.archive.ubuntu.com/ubuntu kinetic InRelease                 
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:3 http://security.ubuntu.com/ubuntu kinetic-security InRelease          
  Temporary failure resolving 'security.ubuntu.com'
Err:4 http://repo.vivaldi.com/stable/deb stable InRelease
  Temporary failure resolving 'repo.vivaldi.com'
Err:5 http://us.archive.ubuntu.com/ubuntu kinetic-updates InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:6 http://us.archive.ubuntu.com/ubuntu kinetic-backports InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
16 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/kinetic/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/kinetic-updates/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/kinetic-backports/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/kinetic-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch https://downloads.plex.tv/repo/deb/dists/public/InRelease  Temporary failure resolving 'downloads.plex.tv'
W: Failed to fetch http://repo.vivaldi.com/stable/deb/dists/stable/InRelease  Temporary failure resolving 'repo.vivaldi.com'
W: Some index files failed to download. They have been ignored, or old ones used instead

```

---

### Post by ActionParsnip on 2022-11-21
If you run
```

echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf > /dev/null

```
Then rerun the apt command, does it work OK?

---

### Post by lance bermudez on 2022-12-09
this is a temporary fix
```

echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf > /dev/null

```

have to reuse the above command after restart to get things working again.

---

### Post by ActionParsnip on 2022-12-09
Then your system isn't getting DNS settings. When you connect to the VPN you get DNS settings from that and so it works. If you set your DNS settings manually in network manager then you'll be OK. Alternatively you can add them to the resolveconf "head" file and it'll be added that way

---

### Post by lance bermudez on 2022-12-11
I have the dns set in Networ kManager
```

$ sudo service NetworkManager status
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; preset: e>
     Active: active (running) since Tue 2022-12-06 15:22:02 MST; 4 days ago
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; preset: e>
     Active: active (running) since Tue 2022-12-06 15:22:02 MST; 4 days ago
       Docs: man:NetworkManager(8)
   Main PID: 1987 (NetworkManager)
      Tasks: 3 (limit: 5713)
     Memory: 7.1M
        CPU: 14.455s
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;1987 /usr/sbin/NetworkManager --no-daemon

```
[ATTACH=CONFIG]291407[/ATTACH][ATTACH=CONFIG]291407[/ATTACH]

---

