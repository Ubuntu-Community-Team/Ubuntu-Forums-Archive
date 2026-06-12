---
title: "Root without space in Ubuntu 20.04 even with 30 GBytes"
date: 2020-05-14
forum: Installation &amp; Upgrades
---

### Post by ramonbadoch on 2020-05-14
Hi. First at all, sorry by my English...

I'm an Ubuntu user since 2008, always in dual-boot with Windows. For the last years, I used Linux Mint but now, with a new notebook and the brand new Ubuntu 20.04, I've decided to go back to Ubuntu Gnome.

My notebook has one 128 GB SSD and 1 TB HD. The SSD comes partitioned by factory leaving just 100 GB for Windows. I've reduced this partition to 75 GB (Windows occupied around 60 GB) and I've occupied these 25 GB to install the Ubuntu's **root** (I've installed the **/home** at 1 TB HD).

After installed and configured, the **root** occupied 15 GB, leaving 10 GB free. It was a surprise to me when, the next day, there was a message informing that **root** had no free space (there were only 1.5 GB free). I ran **Bleachbit** and it freed 5 GB but after some hours this message appeared again.

So, I went to Windows and I took another 5 GB and I reinstalled Ubuntu, then with 30 GB for **root**. 2 days after, this morning the message was shown again. And the **Bleachbit** freed only 1.8 GB. 

Running **Disk Analyzer**, the result was: 26.5 GB **root** total. The 2 biggest areas were **var** (16 GB) and **usr** (8 GB).

Inside **var**, 12.7 were occupied by **log**. When I opened **log**, I saw that **journal** occupied 1.3 GB and the rest occupied little space. So, I don't know where were these 12.7 (there were some items without information of disk space: **gdm3, private, speech-dispatcher**).

The **usr** 8.0 GB total, 5.5 were at **lib** and 1.8 at **share**.

Someone can help me with any suggestion how to proceed?

Thanks in advance.

---

### Post by TheFu on 2020-05-14
```
$ snap list
```

You can control the size of the journal logs in the journald.conf file.

A quick way to find large files is with find.

```
sudo find / -type f -size +3G
```
Clean up those huge files, then run it with smaller 
```
sudo find / -type f -size +999M
```

Just modify the size smaller and smaller to find the large files.
Change the "/" to "/var" since that is likely where the storage is being wasted.  I'd guess in snaps and/or containers and/or virtual machines.  Those are all stored under /var/ by default.

---

### Post by Impavidus on 2020-05-15
8GB in /usr is normal. Something is overflowing your log files by printing the same (or at least similar) message all the time. Find the offending log file and find the repeating line.

If you have to clear up space, old log files can be safely deleted.

---

### Post by ActionParsnip on 2020-05-15
What is the output of:

```

df -h; echo; df -i

```

Thanks

---

### Post by ramonbadoch on 2020-05-15
Thank you all for your answers. Following your directions, I noticed that the **syslog.1** file was 11.8 GBytes. When I opened it, I noticed that the messages 

> vboxdrv.sh[5734]: Enter a password for Secure Boot. It will be asked again after a reboot.
vboxdrv.sh[5734]: Enter the same password again to verify you have typed it correctly.
vboxdrv.sh[5734]: Invalid password
vboxdrv.sh[5734]: The Secure Boot key you've entered is not valid. The password used must be
vboxdrv.sh[5734]: between 8 and 16 characters.

were repeated millions and millions of times. So, as **TheFu** had guessed, it is VirtualBox that is generating an excess of messages. I deleted the **syslog.1** file and uninstalled VirtualBox, which I use very little. Now, I will follow up to see if the problem is resolved.

Thank you very much!

---

### Post by TheFu on 2020-05-15
To be fair, my guess for /var/ being full was more for libvirt.  VirtualBox usually places VM files under the user's HOME.  Log files that grow and grow should be managed by the log limiter.  See /etc/logrotate.d/ for some examples.  Size limits can be set for logs. Also, they can be compressed. As text, they compress really, really, well.

Inside VMs, I usually don't use: 
* UEFI
* secureboot
If your VM installs don't use those, perhaps the billions of log entries wouldn't happen?  I think there's a setting to prevent log entries from being displayed more than once every X minutes too.

I've never used virtualbox on Linux hosts.  Been using KVM or Xen since 2007-ish on Linux hosts.

---

### Post by ramonbadoch on 2020-05-15
> **TheFu said:**
> To be fair, my guess for /var/ being full was more for libvirt.  VirtualBox usually places VM files under the user's HOME.  Log files that grow and grow should be managed by the log limiter.  See /etc/logrotate.d/ for some examples.  Size limits can be set for logs. Also, they can be compressed. As text, they compress really, really, well.

Inside VMs, I usually don't use: 
* UEFI
* secureboot
If your VM installs don't use those, perhaps the billions of log entries wouldn't happen?  I think there's a setting to prevent log entries from being displayed more than once every X minutes too.

I've never used virtualbox on Linux hosts.  Been using KVM or Xen since 2007-ish on Linux hosts.

OK, TheFu. I'll follow your advice. Thank you, very much.

---

