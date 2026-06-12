---
title: "can't upgrade &quot;404 not found&quot;"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by bobdobbs on 2011-09-10
I'm trying to upgrade from 10.04 to 11.04.

As far as I can tell, this means I have to update to 10.10 first. 
When I try to uprade with 'do-release-upgrade',  the upgrade fails with this message:

> 

Could not download the upgrades 

The upgrade has aborted. Please check your Internet connection or 
installation media and try again. All files downloaded so far are 
kept. 

Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/r/rtmpdump/librtmp0_2.3-2_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/r/rtmpdump/librtmp0_2.3-2_amd64.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/g/gio-sharp/libgio-cil_2.22.2-2_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/g/gio-sharp/libgio-cil_2.22.2-2_all.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/g/gnupg/gnupg-curl_1.4.10-2ubuntu2_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/g/gnupg/gnupg-curl_1.4.10-2ubuntu2_amd64.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/i/ibus-m17n/ibus-m17n_1.3.0-1_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/i/ibus-m17n/ibus-m17n_1.3.0-1_amd64.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/libg/libgnomeprint/libgnomeprint2.2-0_2.18.7-1_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/libg/libgnomeprint/libgnomeprint2.2-0_2.18.7-1_amd64.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/libg/libgnomeprint/libgnomeprint2.2-data_2.18.7-1_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/libg/libgnomeprint/libgnomeprint2.2-data_2.18.7-1_all.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/libg/libgnomeprintui/libgnomeprintui2.2-0_2.18.5-1_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/libg/libgnomeprintui/libgnomeprintui2.2-0_2.18.5-1_amd64.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/libg/libgnomeprintui/libgnomeprintui2.2-common_2.18.5-1_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/libg/libgnomeprintui/libgnomeprintui2.2-common_2.18.5-1_all.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/libs/libservlet2.4-java/libservlet2.4-java_5.0.30-12_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/libs/libservlet2.4-java/libservlet2.4-java_5.0.30-12_all.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/d/defoma/psfontmgr_0.11.11ubuntu1_all.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/d/defoma/psfontmgr_0.11.11ubuntu1_all.deb) 
404 Not Found 
Failed to fetch 
[http://nz.archive.ubuntu.com/ubuntu/pool/universe/t/traceroute/traceroute_2.0.14-1_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/t/traceroute/traceroute_2.0.14-1_amd64.deb) 
404 Not Found 



Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done


My internet connection is fine. The host where the files are supposed to be hosted on exists. I'm guessing the files themselves dont exist.

How do I upgrade?

---

### Post by Alwimo on 2011-09-10
Try changing the server you're downloading from.

Go to the software centre, go to Edit > Software Sources and change the server in the drop box. 

There was another thread about a kiwi server having a 404 problem a few days ago, so it's probably a problem with that server.

---

### Post by bobdobbs on 2011-09-10
> **Alwimo said:**
> Try changing the server you're downloading from.

Go to the software centre, go to Edit > Software Sources and change the server in the drop box. 

There was another thread about a kiwi server having a 404 problem a few days ago, so it's probably a problem with that server.

That worked.

Thanks.

---

### Post by raydar on 2012-03-11
Ditto: Changing from the U.S. server to the Main server worked for me, updating 12.04 beta 1 a week after having upgraded to it from 11.10 (though I changed the server in the Update Manager settings, rather than in the Software Center).

---

