---
title: "Transferring to NFS causes a lockup"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by barbz127 on 2010-04-16
Hi all,

Im running the beta 2 on a spare desktop.

Whenever I try to transfer iso's or other large (+1gb) files across my network to my freenas server VIA nfs the gui locks up and is unresponsive until the transfer is complete.

Any way to fix this?

Cheers
Paul

---

### Post by dino99 on 2010-04-16
does that mean it dont find its way ?
any comments into logs ?
problems are only with large files ?

---

### Post by barbz127 on 2010-04-16
> **dino99 said:**
> does that mean it dont find its way ?
any comments into logs ?
problems are only with large files ?

The file ends up on the NFS share and opens fine - so no data corruption. Just the system hangs.

Nothing in the logs on the NAS and not sure where to start on ubuntu...

The file transfer doesnt take longer than usual just locks up the desktop.

Cheers
Paul

---

### Post by FuturePilot on 2010-04-16
This is happening to me too. :(

---

### Post by cariboo on 2010-04-16
How are you transferring the file, via wireless, or wired? Does it happen both ways?

I just transfered a 3.5 Gb file from my server to my netbook over wireless, and kept on doing some moderator stuff, with no slowdowns.

---

### Post by FuturePilot on 2010-04-16
I'm using wireless. I haven't tested wired yet. I had no problems transferring large files over wireless in Karmic.

---

### Post by cariboo on 2010-04-16
Are you using the same driver for your wireless device as you did in Karmic?

---

### Post by wolfchri on 2010-04-16
> **barbz127 said:**
> Hi all,

Im running the beta 2 on a spare desktop.

Whenever I try to transfer iso's or other large (+1gb) files across my network to my freenas server VIA nfs the gui locks up and is unresponsive until the transfer is complete.

Any way to fix this?

Cheers
Paul

That happens to me since Dapper. I doubt that this is related to 10.04. or its beta status. It improved with 9.10, but large files still keep my system busy.

---

### Post by FuturePilot on 2010-04-16
> **cariboo907 said:**
> Are you using the same driver for your wireless device as you did in Karmic?

Whatever version of the ath5k driver Ubuntu ships with.

---

### Post by barbz127 on 2010-04-16
im transferring via a wired network (Realtek on board).

i remember seeing this in the old older version, but i just cant deal with a full lockup.

---

### Post by GeoPirate on 2010-04-16
I also had the same problem, over a wired network.  It seems to lock up less often when transferring files from another system to the one you're using instead of transferring from the system you're using to another system.

---

### Post by barbz127 on 2010-04-22
has anyone has success using particular flags to mount the nfs share?

Just to confirm for me this is only when uploading a file to a nfs share not when downloading.

Cheers
Paul

---

### Post by red321 on 2010-04-25
I moved my mythtv server to new hardware, and updated to lucid at the same time.

Seems to be some problem with the atl1c driver, or the hardware. Using both lucid and karmic I get hangs on transfers to a debian 5 NAS.  They were so bad that I couldnt even software reboot, had to go for the three pin reset. Shifting to samba for the share has got rid of the hangs. I would rather solve the problem. 

I have seen suggestions to move to the atl1e driver; disable ipv6. Neither seem to fully fix my issues.

Update: tried changing to the atl1e driver, dropping rsize and wsize down to 1024. I can read from the nfs server, but any attempt to write from the myth server to the NAS causes a lockup, that I cant get out of. 

I have the myth server, and a desktop dell (ubuntu 9.10) as clients to a "nfs-kernel-server NAS debian 5.0."

cat /proc/mount shows that NAS is nfs  mounted with exactly same flags on my desktop machine and my myth server.
Both myth server and desktop can read and write over samba, and read from the NAS over nfs.
The dell can write to the NAS, the myth server cant. :-(

Its a new gigabyte motherboard, with a 

02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)

Any suggestions ? Is it just a driver problem ?

---

