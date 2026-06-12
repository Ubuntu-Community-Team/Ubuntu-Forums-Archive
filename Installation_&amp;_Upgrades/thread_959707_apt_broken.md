---
title: "apt broken"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by David Deharbe on 2008-10-26
Fellow Ubuntu users,

I run Ubuntu 8.04 in a virtual machine under MacOS using Sun's Virtual Box.

I had to do a hard reset and this seems to have damaged several things in my installation:  first, and foremost, being the package system.

Whenever I try to run synaptic or apt-get I get the following message:
[INDENT][FONT="Courier New"]david@linuxbox:~$ sudo apt-get check
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
[/FONT][/INDENT]

How could I repair my installation?

Best,

David.

---

### Post by ghantoos on 2008-10-26
Did you try the following command?
```
sudo apt-get -f install
```Hope this helps,

Cheers,

---

### Post by David Deharbe on 2008-10-27
> **ghantoos said:**
> Did you try the following command?
```
sudo apt-get -f install
```Hope this helps,

Cheers,

Unfortunately not, I get the error message.

```

E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
```

I should note that the file system has been compromised and fsck was run in a maintenance shell at boot time. This has probably corrupted apt's data base somehow.

David.
--

---

### Post by bapoumba on 2008-10-27
> **David Deharbe said:**
> 
I should note that the file system has been compromised and fsck was run in a maintenance shell at boot time. This has probably corrupted apt's data base somehow.

David.
--
Hmm, do you still have the /etc/apt/sources.list file ?

---

### Post by Kevbert on 2008-10-27
Please try this in terminal:
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```
It looks like your package status file has been corrupted.

---

### Post by David Deharbe on 2008-10-27
> **Kevbert said:**
> Please try this in terminal:
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```
It looks like your package status file has been corrupted.

Thanks, that was exactly my problem. When I tried to cat the contents of the /var/lib/dpkg/status file, it gave me an I/O error. So I copied the contents of status-old over status and updated apt-get. The error message disappeared.

Thanks all for your kind help.

David.

---

