---
title: "PLease help, Emergency!!!!!!"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by jasonodoom on 2010-08-29
I can't install software without it telling me that its not trusted! 

When I reload the software sources it gives me this. PLease HELP, I really don't know how to fix this.:

Could not download all repository indexes

T**_he repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct._**











GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912EGPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AA2BB78B7AE26941GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CFFailed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch file:/home/repository/dists/SuiteCodename/main/binary-i386/Packages.gz  File not found
Failed to fetch file:/home/repository/dists/SuiteCodename/restricted/binary-i386/Packages.gz  File not found
Failed to fetch file:/home/repository/dists/SuiteCodename/universe/binary-i386/Packages.gz  File not found
Failed to fetch file:/home/repository/dists/SuiteCodename/multiverse/binary-i386/Packages.gz  File not found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Sub101 on 2010-08-29
According to this article: [http://techpad.co.uk/content.php?sid=84](http://techpad.co.uk/content.php?sid=84)

```
cd /etc/apt
sudo rm *.gpg
gpg --export -a 437D05B5 | sudo apt-key add -
sudo apt-get update
```

However it is not something I have dealt with myself. I would also strongly suggest backing up the gpg files before removing them.

---

### Post by jasonodoom on 2010-08-30
How do I back up my gpg files?

---

### Post by jasonodoom on 2010-08-30
> **Sub101 said:**
> According to this article: [http://techpad.co.uk/content.php?sid=84](http://techpad.co.uk/content.php?sid=84)

```
cd /etc/apt
sudo rm *.gpg
gpg --export -a 437D05B5 | sudo apt-key add -
sudo apt-get update
```

However it is not something I have dealt with myself. I would also strongly suggest backing up the gpg files before removing them.
It didn't work. :(

---

### Post by wojox on 2010-08-30
You just need to run these two commands to import the keys

```

gpg --keyserver pgpkeys.mit.edu --recv-key  FC918B335044912E 
gpg -a --export FC918B335044912E | sudo apt-key add -

```

```
sudo apt-get update
```

Do that for each key that it throws back at you until the key situation is done.

---

### Post by wojox on 2010-08-30
Then post back this in 

```
cat /etc/apt/sources.list
```

Make sure you put them in # ([CODE]) tags.

---

### Post by jasonodoom on 2010-08-30
Thanks. It gave me this, don't think its working...... This is my second year of using Ubuntu, I'm still learning :)


[IMG]http://ubuntuone.com/p/EPn/[/IMG]

---

### Post by wojox on 2010-08-30
Now do the same for this number

```

gpg --keyserver pgpkeys.mit.edu --recv-key  40976EAF437D05B5 
gpg -a --export 40976EAF437D05B5 | sudo apt-key add -

```

```
sudo apt-get update
```

Do that for each key that it throws back at you until the key situation is done.

---

### Post by jasonodoom on 2010-08-30
After I put this in: cat /etc/apt/sources.list it gave me this: [IMG]http://ubuntuone.com/p/EPt/[/IMG]

---

### Post by wojox on 2010-08-30
I also noted you rooted. If you didn't run around in root you may not have half these problems. :D

---

### Post by wojox on 2010-08-30
That line about 

```
deb file:///home/
```

All needs to be removed.

---

### Post by jasonodoom on 2010-08-30
Whats ROOT? How do I get out of it?

---

### Post by wojox on 2010-08-30
Type

```
exit
```

Then hit *Enter*

Anytime your terminal begins with root@ and ends with # your root. 

You want yourUserName@ and ending with a $ and just use sudo.

Read [RootSudo]("https://help.ubuntu.com/community/RootSudo")

Anyhow have you entered all those keys yet?

---

### Post by jasonodoom on 2010-08-30
Yes I did enter the keys, it didn't work :(.  Can you please help me to get out of ROOT? I typed it in and it said unknown command.... I can't believe this happened! And I was getting ready to upgrade to Ubuntu 10.10!!!!

---

### Post by wojox on 2010-08-30
If you reboot your computer, you log right in as root? You don't enter some command to become root? Are you using the root terminal?

---

### Post by jasonodoom on 2010-08-30
My Computer has two user accounts, so I cancel the automatic login to the first and type in the password to my account. So I guess, yes?

---

