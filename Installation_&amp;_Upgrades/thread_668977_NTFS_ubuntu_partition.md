---
title: "NTFS ubuntu partition"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by silverhammermba on 2008-01-16
I've been using Ubuntu for a couple of weeks now and now that I've worked out the kinks, I've been thinking about what I'll do differently next time I install.

I know that the standard Ubuntu installation has the /home/, /root/, and /swap/ partitions and that they default to ext3. However, I want to dual boot with Windows and I don't like the redundancy of having Windows' "My Documents" as well as Ubuntu's /home/. So here's my question, is it possible to install Ubuntu such that Windows and /home/ share an NTFS partition? If not, can /home/ at least be NTFS so I can access my Ubuntu files from Windows?

---

### Post by balak on 2008-01-16
I am not sure about /home but I had an additional partition when I used to dual-boot. 
I'll just call it /data and declare it as NTFS and this is where I stored most of my files.

hope this helps

---

### Post by schauerlich on 2008-01-16
> **balak said:**
> I am not sure about /home but I had an additional partition when I used to dual-boot. 
I'll just call it /data and declare it as NTFS and this is where I stored most of my files.

hope this helps

+1

Have an NTFS Windows Partition, then ext3 /, then NTFS data, then swap

---

### Post by silverhammermba on 2008-01-16
So how would /data/ work? What's the difference from /home/?

What I would really like is only three partitions: /, /swap/, and then one NTFS for both Windows and Ubuntu user stuff. Is this not possible then?

---

### Post by phoenix81000 on 2008-01-17
mount your windows install in your current Ubuntu setup.. create a new account and set home to /media/WINDOWS PARTION/USER/My Documents ? never tried but i dont see why that would not work.

Just read the man pages.. there is a flag for picking your homedir, now make sure u also have the ntfs-3g thing installed :D I might try it now actually and see if it works

---

