---
title: "Beryl installation"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by torikulhasan@yahoo.com on 2006-12-20
Hello,

I m new in this forum. just registered few minutes ago.

I want to install the beryl repository:
I m following the procedures of the page:
[http://64.233.161.104/search?q=cache...ient=firefox-a](http://64.233.161.104/search?q=cache...ient=firefox-a)

applied the following command:

sudo nano /etc/apt/sources.list

I added the following link in source.list as instructed in the page

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx

then applied following command

sudo apt-get update

the outcome of this command is as:

Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper Release.gpg [191B]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 194B in 9s (21B/s)
Failed to fetch [http://ubuntu.beryl-project.org/dists/dapper/Release](http://ubuntu.beryl-project.org/dists/dapper/Release) Unable to find expected entry aiglx/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


CAN ANYBODY HELP ME IN THIS REGARD, TO COMPLETE THE INSTALLATION OF BERYL IN MY PC

Rgds,
Hasan

---

### Post by raul_ on 2006-12-20
Did you add the key?
```

Add this line:

deb http://ubuntu.beryl-project.org/ dapper main aiglx

Make sure to get the public key for the repository:

wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -

Update the package list and upgrade your system before installing

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by torikulhasan@yahoo.com on 2006-12-20
i added the link:

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx

Got the public key from:

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

Updated the package list and upgraded the system also

the outcome of the command   [COLOR="Magenta"]sudo apt-get update
is as follows:[/COLOR]


Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper Release.gpg [191B]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 194B in 9s (21B/s)
[COLOR="Magenta"]Failed to fetch [http://ubuntu.beryl-project.org/dists/dapper/Release](http://ubuntu.beryl-project.org/dists/dapper/Release) Unable to find expected entry aiglx/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/COLOR]

---

### Post by robgill on 2006-12-20
I'm not sure the dapper repo is still active, but you still can have the MOST recent version (svn > 0.1.3). I use it and it works great, I have no problems.

First install 0.1.1 from ubuntu repo (search beryl in synaptic).

Next go [here](http://forum.ubuntu-it.org/index.php?PHPSESSID=4bd8c6bdb0fc0827aaa4cea601b14910&topic=45451.0)

It's in Itallian, but easy to follow.  Download latest package (I have 1949 and it works great) at the bottom of the first post.

Extract the downloaded file and navigate to the directory in terminal and type

```
sudo dpkg -i *.deb
```

Now you've got the latest version on dapper.

Anytime you want repeat the last few steps - thanks to the pakager, it couldn't be much easier.

---

### Post by torikulhasan@yahoo.com on 2006-12-20
to download beryl 0.1.3 from   [COLOR="Magenta"]http://forum.ubuntu-it.org/index.php?PHPSESSID=4bd8c6bdb0fc0827aaa4cea601b14910&topic=45451.msg241885#msg241885[/COLOR]
as u mentioned,  I need to register. But while trying to register the reply is as:

E'accaduto un errore!
Spiacente, non ti è permesso registrare account multipli nello stesso momento dallo stesso computer.

---

### Post by robgill on 2006-12-20
You shouldn't have to worry about regestering - you may have clicked on the wrong link?

here's the direct link to svn 1949 dapper

[http://rapidshare.com/files/8299629/beryl-svn-1949-dapper.tar.gz.html](http://rapidshare.com/files/8299629/beryl-svn-1949-dapper.tar.gz.html)

It's the link after (1949) near the bottom of the first post, I hope this helps.

---

### Post by torikulhasan@yahoo.com on 2006-12-21
i tried the link 
[http://rapidshare.com/files/8299629/...er.tar.gz.html](http://rapidshare.com/files/8299629/...er.tar.gz.html)

but reply is requested url could not be found

in fact all the 4 links of top of this link shows not found error

---

### Post by robgill on 2006-12-21
That's weird, it still works for me.  If you want I can e-mail you one of the packages.

---

### Post by torikulhasan@yahoo.com on 2006-12-21
Yes. please email to me the packages at [email]torikulhasan@yahoo.com[/email] 
it will be great help for me becoz i cannot access those links at all ( not found error)

Thank you

---

### Post by torikulhasan@yahoo.com on 2006-12-23
Thanks for giving the beryl_svn_1949_dapper.tar.gz

i uncompressed and installed using sudo dpkg -i *.deb

but when i give beryl-manager command in the terminal it shows the following

XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
beryl: No composite extension

plz help to complete the installation

This is HP machine
display adapter is--> Intel(R) 82915G/GV/910GL Express Chipset Family


thanks u in advance

---

### Post by robgill on 2006-12-23
It appears you don't have a composite extension.  Depending on what kind of video card you have you will have to follow different steps.  I have a intel card, so that's the only one I know how to set up.  Here's a howto for an intel card and AIGLX(composite extension) on dapper.

[HTML]http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX[/HTML]

Reading again, it seems that this is the same guide you were trying to use... so I'll look around and see if I can find any other ways to get AiGLX.

---

### Post by robgill on 2006-12-23
OK, I think if you just skip to the install AiGLX that starts with 

```
sudo apt-get install xserver-xorg-air-core
```

and follow until the install beryl (which you've already done) it should work for you.

---

### Post by robin.w on 2006-12-29
Hi guys,

I would like to try Beryl but I've got exactly the same issue like [email]torikulhasan@yahoo.com[/email]. I couldn't download a package from rapidshare.com

Please, be so kind and mail me package - my email: [email]robin.w@seznam.cz[/email]. I've found so many info about Beryl include install packages but all only for Edgy and I'm going on Dapper.

Thanx a lot!!! All Ubuntu users rock!!!

---

