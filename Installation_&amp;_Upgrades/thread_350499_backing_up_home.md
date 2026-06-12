---
title: "backing up /home"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by Hacim on 2007-01-31
hello,before I attempt to install edgy I thought I should probably back-up my home folder.
What would be the best way of doing this should I just roll a tarball of the /home folder and send it to my other pc?

---

### Post by taurus on 2007-01-31
Can the whole thing fit onto a DVD?

---

### Post by Hacim on 2007-01-31
no even if i cleaned up a bit I still wouldn't be able to because as of the moment I don't have 
dvd burner.

---

### Post by grahams on 2007-01-31
I use rsync to backup my /home directory on a regular basis. It is an excellent tool.

I simpler tool if this is a one off backup is scp which is part of openSSH.

scp -r  /home login@hostname:/backup

where login is an account login on the target system, and  hostname is the hostname for the pc you copying data to (can also be the IP address). /backup is where you want to copy to on that system.

If you're on a slow network use -C to compress the data. 

This assumes your target is another linux box. If windows you can install pscp (google it) and pull the data from your ubuntu client.

---

### Post by Hacim on 2007-01-31
ok I'll try that,many thanks.

---

