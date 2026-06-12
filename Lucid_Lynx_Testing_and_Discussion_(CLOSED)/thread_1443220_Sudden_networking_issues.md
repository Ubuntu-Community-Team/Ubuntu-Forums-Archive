---
title: "Sudden networking issues"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mltucker on 2010-03-30
I upgraded to Lucid Lynx (64-bit ubuntu), and everything was fine for a few boots.  At some point, there was a bad suspend (never suspended... an error message I didn't think to write down or find in a log -- I wouldn't even know where to find it unfortunately).

Now I am having issues with my wired ethernet.  After booting, I'm not assigned an IP address, and need to run dhclient before my internet will work.

I don't really mind running this when I reboot, but the bigger issue is that samba sharing also doesn't work.  I have read some troubleshooting guides, but I am stuck in what is usually the first step (and it never says what to do when this happens):

```

$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------

```

i.e. findsmb doesn't find anything.  I know that the network is up since other computers in the house can share files with each other, but nothing with this one.

I have always used the default samba.conf without any issues.  Sometimes smbd and nmbd seem to not be running, but even after starting them I get an error when I double click the "Windows Network" icon in Nautilus: "Unable to mount location -- Failed to retrieve share list from server".

Any suggestions?  Thanks!

-Mark

EDIT: more relevant info... I can ping the other computers on the network, and they can ping me.  Also, the problem remains with the firewall completely off.

---

