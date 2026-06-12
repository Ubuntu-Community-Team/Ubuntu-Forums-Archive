---
title: "Can't upgrade from 14.10 to 15.04"
date: 2015-05-21
forum: Installation &amp; Upgrades
---

### Post by subfer1 on 2015-05-21
When I start the update process, everything goes smoothly untill the packages should start installing, at which point i get the following message:
"Failed to fetch [http://cr.archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-binaries_2014.20140926.35254-6build1_amd64.deb](http://cr.archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-binaries_2014.20140926.35254-6build1_amd64.deb) Connection failed"

After this, I rebooted and then tried the partial upgrade (as the installation had most of the packages already downloaded), but it gives me the message again. Any idea why this might be happening or how to fix it?

Thanks in advanced,

---

### Post by Hodevah on 2015-05-21
Hi can you post output of: 

```
cat /etc/apt/sources.list
```
and 
```
cat /etc/resolv.conf
```

```
ps aux | grep dns
```

can you browse sites on the net without problems?
Are you on a static IP?

If the above answers are (1) yes, and (2)  no, then do the following:

```
sudo gedit /etc/resolv.conf
```
> nameserver 8.8.8.8

save the above and ping in terminal:
```
ping www.google.com
```

Then do :


```
sudo apt-get --download-only --reinstall install resolvconf
sudo dpkg --purge --force-depends resolvconf
sudo apt-get install resolvconf
```

If this procedure fails, then do the following:

Edit your Network connections and edit the IPv4 settings and change to Automatic (DHCP) from Automatic (DHCP) addresses and enter in the Additional DNS servers field, 8.8.8.8j. Save those settings.
Go to */etc/resolve.conf *and check that you have 8.8.8.8 for a nameserver and can ping Google again. 


If the above doesn't work, go back and re-do the changes to what they were before (initially at start before editing them). 
Instead go to Network settings and change/check that proxy is set to Manual and leave HTTP, HTTPS, FTP Socks host blank. 

then do 
```
sudo apt-get update && sudo apt-get dist-upgrade
```

hope this helps. Please let us know. If none of the above works, then I suspect that your sources list is corrupt. That can easily be resolved. But please try the above first.

---

