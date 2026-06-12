---
title: "Error Upgrading from Edgy to Feisty"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by elloello on 2007-12-01
Hi,
I am a newb to ubuntu and linux in general.  I am trying to upgrade from Edgy to Feisty and it keeps failing due to the following error message:  Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code(1).
Does anyone know why this keeps happening or how to fix it?  It says it is probably a network problem and to check my connection, but my connection is working fine.  Any help would be appreciated.

---

### Post by Pumalite on 2007-12-01
Maybe if you change servers you'll have better luck.

---

### Post by elloello on 2007-12-01
What server would you recommend switching changing to?

---

### Post by elloello on 2007-12-01
and how do I do that?

---

### Post by Pumalite on 2007-12-01
System>Administration>Software Sources.
See what are your choices. In the U.S:, I'd say Main.

---

### Post by elloello on 2007-12-01
I changed to the main server and I am still getting the same error.  Additionally when I check for updates in Software Updates it tells me it could not access that same repository index.  Do you have any other suggestions?  Should I just copy the ISO of Gusty to disk and boot from that? Will it allow me to upgrade to the latest version that way, or would I have to first uninstall Edgy?  The reason I ask is I don't really have any documents that I would need to back up on my Linux partition yet, so if I can just uninstall 6.10 and put 7.10 on that partition instead, do you think that might resolve my issue?

---

### Post by Pumalite on 2007-12-01
You can upgrade with CD, but has to be the Alternate CD.

---

### Post by elloello on 2007-12-01
all right I'll try that

---

### Post by Pumalite on 2007-12-01
Good luck.

---

### Post by elloello on 2007-12-01
Do you know how I can just remove Edgy and use that partition to install Gusty instead? It says on the ubuntu site that I need to have Feisty before I can use the alternate cd for gusty.  I already have the regular disk with Gusty on it (I should've used that in the first place), but I was trying to learn from a book to get started and they included a copy of Edgy with the book so I just figured I would upgrade later.  I guess I can't uninstall it without having a screwed up MBR now though can I?  (In the meantime I am downloading the iso for the alternate cd for Feisty, but thats gonna take another 40 minutes or so, and then I would most likely have to do the same for Gusty)...seems silly when I have a copy of Gusty right in front of me and nothing that I really need to save on that partition.
     Another thing that I found odd is that when I had installed initial software updates right after I got Edgy up and running, instead of just replacing my old 6.10 version with 6.12, the GRUB bootloader now lists both of them as boot options.  Do you know if that's normal?  Sorry if I'm being a pain... I just have no clue what to do at this point if I have a defective copy of Linux.  Everything else with it seems to work fine except updating though so I guess its not so bad.

---

### Post by Pumalite on 2007-12-01
Can you boot that copy of Gutsy you have?

---

### Post by elloello on 2007-12-01
Sorry had to go away for a bit.  Yes I can boot from it, but for some reason I can't get it to connect to the internet in live distro mode, which is wierd because I followed exactly the same steps for my wireless connection that I followed when setting up Edgy.  This is getting quite confusing.  Anyway, I am in the midst of upgrading via a burned alternate cd of 7.04.  I'm probably going to have updates to install once I am done upgrading...(I told it to skip trying to get the updates immediately from the internet, because it threw the same error message at me when I originally told it to try).  Hopefully with the upgrade installed it won;t give me the same error again.  But iit does I'm not sure where to go from there.  I obviously can't just never update my software.  I appreciate your help.  I'll let you klnow what happens.

---

### Post by Pumalite on 2007-12-01
You have to be wired to the Internet to install. Wireless is configured later.

---

### Post by elloello on 2007-12-01
Allright!   I'm all up and running now.  I did the upgrade from the alt cd for Feisty all my software updates went without any problems.  I think there was a bug in the program that sets up the list of servers on my copy of Edgy, because now I can actually choose a server from a large list, whereas before my only options were Main Server or Server in America.   Weird huh?  Thanks for all your help.  It was greatly appreciated.  Take care.

---

