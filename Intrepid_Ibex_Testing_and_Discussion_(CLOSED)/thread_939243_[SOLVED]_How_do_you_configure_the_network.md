---
title: "[SOLVED] How do you configure the network?"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by The Cog on 2008-10-05
I feel really stupid asking this, but here goes...

I can't find System->Administration->Network in Intrepid. I can't see any other menus that look like good candidates either. I also read that Intrepid ignores the contents of /etc/network/interfaces, so I guess I can't just edit that. So how do you configure the network in Intrepid?

---

### Post by plun on 2008-10-05
No its not stupid....:)

I filed a bug about it and I also didnt find any matching package
so I filed it against Ubuntu.... thats maybe stupid.
There are nevertheless at least 20 packages directly involved.

Networking is discussed within this thread:
[http://ubuntuforums.org/showthread.php?t=932208](http://ubuntuforums.org/showthread.php?t=932208)

On my server it works ok, manually setup and also Ebox running.

Its totally "mission impossible" for me to connect to my Ubuntu client from a Windows client.

Setup NFS from Nautilus  ?

shares-admin   ?

Maybe to file a new against Nautilus...everything starts there..

---

### Post by The Cog on 2008-10-05
Sorry, it's not setting up file sharing thats the problem - its configuring my IP address and my WEP/WPA wireless key. I can't find a menu for doing that.

---

### Post by wgrant on 2008-10-05
> **The Cog said:**
> Sorry, it's not setting up file sharing thats the problem - its configuring my IP address and my WEP/WPA wireless key. I can't find a menu for doing that.

You want Network Manager. You'll find it in your notification area.

---

### Post by The Cog on 2008-10-06
Ah! And there it is. Thank you.

---

