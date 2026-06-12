---
title: "SpamAssassin Update?"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by rocksteady on 2006-08-10
Dear readers,

I use Ubuntu 6.06 Server. I installed the SpamAssassin
package (3.1.0a-2ubuntu1.1). Now I need an update from
SpamAssassin to 3.1.4 (or at minimum 3.1.1)
I saw that SA 3.1.3 exists under Edgy. 
Is there any way that I can update my SA easily?
Otherwise I have to download SA from the SA Homepage,
compile and install manually.

Thanks for your help and nay Hints!
benny

---

### Post by bjammin on 2006-08-20
I am in the same boat ... I tried to update the sources.list to reference edgy, but I couldn't figure out how to just make it upgrade the spamassassin package (it wanted to upgrade everything which didn't seem a good idea!)

Is there any other way to install SpamAssassin 3.1.4? 

Thanks
jammin

---

### Post by thomasando on 2006-08-20
I too would like to know if there's an easy way to do this. I could install from Source, but it looks like some reconfiguration will be necessary, as I'm currently running spamassassin through MailScanner...

---

### Post by bjammin on 2006-08-21
I could do it from source as the only thing this machine is doing is running spamd.

Unfortunately I'm a linux n00b so I don't know how.  If anyone is able to post instructions for a manual install I'm happy to give it a go.

Thanks
Jammin

---

### Post by thomasando on 2006-08-21
Download the package from [http://spamassassin.apache.org](http://spamassassin.apache.org), unpack it and read the INSTALL file contained within the archive. That should hopefully give you an idea.

I want to try create a custom deb package - will post here if I'm successful.

---

### Post by bjammin on 2006-08-21
Thanks, it wasn't quite so straightforward as I didn't have the build packages installed, but with a bit of googling I managed it.

For those others who want to do this.  Log in as root and then:

1. First make sure you have make installed
```
apt-get install make
apt-get install build-essential
```

2. Then :
```
cd /tmp
wget http://apache.ausgamers.com/spamassassin/source/Mail-SpamAssassin-3.1.4.tar.gz
```
You can substitute your local mirror here

3. Then
```
tar xvzf Mail-SpamAssassin-3.1.4.tar.gz
cd Mail-SpamAssassin-*
perl Makefile.PL
make
make install
```

This worked for me, but please excuse any mistakes as I literally installed linux for the first time less than 24 hours ago.

---

### Post by bjammin on 2006-08-21
Actually this didn't quite work properly so please don't follow my instructions unless you know what I did wrong.

I ended up installing the 3.1.3 package from edgy instead... that will do until someone backports 3.1.4.

```
cd /etc/apt
cp sources.list sources-dapper.list
vi /etc/apt/sources.list
```
Uncomment all sources and change all references from dapper to edgy
```
apt-get update
apt-get install spamassassin
cp sources.list sources-edgy.list
cp sources-dapper.list sources.list
apt-get update
```

---

### Post by DoLoop on 2007-04-17
Thanks, bjammin.  This saved me some time.

BTW, the version is now up to 3.1.4.

DoLoop

---

