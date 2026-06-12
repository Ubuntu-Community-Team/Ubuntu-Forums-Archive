---
title: "automatix"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by newbemac on 2007-06-03
Hi to all
When I attemt to install automatix in 7.04 via the terminal window I receive the following message
"tom@tom-laptop:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
tom@tom-laptop:~$ wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
tom@tom-laptop:~$ 
and that the end of the install.
I have tried several times in the past several weeks with no luck.
the goal is to get my toshiba laptop to play dvd's
I have tried via  synaptic package manager also,
I'm stumped,
mac

---

### Post by arnieboy on 2007-06-03
> **newbemac said:**
> Hi to all
When I attemt to install automatix in 7.04 via the terminal window I receive the following message
"tom@tom-laptop:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main" | sudo tee -a /etc/apt/sources.list
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
tom@tom-laptop:~$ wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
tom@tom-laptop:~$ 
and that the end of the install.
I have tried several times in the past several weeks with no luck.
the goal is to get my toshiba laptop to play dvd's
I have tried via  synaptic package manager also,
I'm stumped,
mac

Go to System--->Preferences--->Network Proxy and Change proxy to "Direct Internet Connection"
Now try the following again:
```
wget http://www.getautomatix.com/keys/automatix2.key
```

```
gpg --import automatix2.key
```
```

gpg --export --armor E23C5FC3 | sudo apt-key add -
```

```
 sudo apt-get update
```
```

 sudo apt-get install automatix2
```

---

### Post by newbemac on 2007-06-03
Thanks for the quick reply
I tried this also however also with no luck
please refer to the last line from the terminal window to see this new issue
thanks mac


tom@tom-laptop:~$ wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
--11:46:31--  [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
           => `automatix2.key'
Resolving [www.getautomatix.com](www.getautomatix.com)... 216.120.255.9
Connecting to www.getautomatix.com|216.120.255.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,706 (1.7K) [application/pgp-keys]

100%[=============>] 1,706         --.--K/s             

11:46:31 (100.41 MB/s) - `automatix2.key' saved [1706/1706]

tom@tom-laptop:~$ gpg --import automatix2.key
gpg: /home/tom/.gnupg/trustdb.gpg: trustdb created
gpg: key E23C5FC3: public key "Arnav Ghosh (Automatix Team Lead) <greyrod@gmail.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
tom@tom-laptop:~$ gpg --export --armor E23C5FC3 | sudo apt-key add -
OK
tom@tom-laptop:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release          
Get:2 [http://ftp.debian.org](http://ftp.debian.org) sarge Release.gpg [378B]    
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Translation-en_US  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge Release                 
Err [http://ftp.debian.org](http://ftp.debian.org) sarge Release                 
  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Get:5 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9480B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release  
Get:6 [http://ftp.debian.org](http://ftp.debian.org) sarge Release [34.6kB]      
38% [5 Packages bzip2 0] [Release gpgv 50880] [Waiting fbzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages    
  Sub-process bzip2 returned an error code (2)
Get:7 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9480B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:8 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9480B]
Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9480B]
Get:10 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9480B]
80% [7 Packages bzip2 0] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages    
  Sub-process bzip2 returned an error code (2)
80% [8 Packages bzip2 0] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages    
  Sub-process bzip2 returned an error code (2)
80% [9 Packages bzip2 0] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages    
  Sub-process bzip2 returned an error code (2)
80% [10 Packages bzip2 0] [Waiting for headers] [Waitingbzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages    
  Sub-process bzip2 returned an error code (2)
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:12 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
Get:13 [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages [9480B]
84% [13 Packages bzip2 0] [Waiting for headers] [Waitingbzip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages    
  Sub-process bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge Release                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release 
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
Get:14 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release [7232B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Get:15 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages [7361B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Get:16 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages [7361B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Get:17 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages [7361B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
99% [16 Packages bzip2 0]bzip2: (stdin) is not a bzip2 file.
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
  Sub-process bzip2 returned an error code (2)
99% [17 Packages bzip2 0]bzip2: (stdin) is not a bzip2 file.
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
  Sub-process bzip2 returned an error code (2)
Fetched 50.0kB in 1s (30.0kB/s)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://packages.medibuntu.org/dists/feisty/free/binary-i386/Packages.bz2](http://packages.medibuntu.org/dists/feisty/free/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://packages.medibuntu.org/dists/feisty/free/binary-i386/Packages.bz2](http://packages.medibuntu.org/dists/feisty/free/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_feisty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_feisty_non-free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_feisty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_feisty_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
tom@tom-laptop:~$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package automatix2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package automatix2 has no installation candidate
tom@tom-laptop:~$

---

### Post by arnieboy on 2007-06-03
Your proxy issue got taken care of.. Now we need to fix your well-broken sources.list..
Please paste the results of the following command:
```
cat /etc/apt/sources.list 
```

---

### Post by newbemac on 2007-06-03
ok done,
tom@tom-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://ftp.debian.org](http://ftp.debian.org) sarge main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
tom@tom-laptop:~$

---

### Post by newbemac on 2007-06-03
shall i run the lines in the terminal window from the first reply?

---

### Post by arnieboy on 2007-06-03
> **newbemac said:**
> shall i run the lines in the terminal window from the first reply?

no.. **dont**.
first delete the last 9 lines from your sources.list after opening it up as root thusly:
```
sudo gedit /etc/apt/sources.list
```
now delete the last 9 lines from the file:
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://ftp.debian.org](http://ftp.debian.org) sarge main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

so that it ends up looking as follows:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
Now save and close the file and do:
```
sudo apt-get update
sudo apt-get install automatix2
```

---

### Post by newbemac on 2007-06-03
ok, done
now what??

---

### Post by arnieboy on 2007-06-03
> **newbemac said:**
> ok, done
now what??
now run automatix from applications --> system tools and see what it has to offer.

---

### Post by newbemac on 2007-06-03
automatix does not appear in "applications" " system tools"
hmmmmmm
very confused????

---

### Post by arnieboy on 2007-06-03
> **newbemac said:**
> automatix does not appear in "applications" " system tools"
hmmmmmm
very confused????
what is the ouput of the following command:
```
sudo apt-get install automatix2
```
run it from terminal:
```
automatix2
```

---

### Post by newbemac on 2007-06-03
ok,
 I went to synaptic pacage manager and locatex "automatix" there.  I completed the down loan and now "automatix" appears in applications, system tools, but when i click on it nothing happens

hmmmmm?
mac

---

### Post by newbemac on 2007-06-03
from the terminal I get

tom@tom-laptop:~$ sudo apt-get install automatix2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
automatix2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libktnef1 libglib1.2 libmpeg3-1 sysvinit
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

when i enter AUTOMATIX2 in the terminal window i get

tom@tom-laptop:~$ automatix2
  File "/usr/bin/automatix.py", line 34, in <module>
    from resin_config import *
  File "/usr/lib/automatix2/resin_config.py", line 16, in <module>
    import xml_functions as xml
  File "/usr/lib/automatix2/xml_functions.py", line 11, in <module>
    import libxml2
ImportError: No module named libxml2

---

### Post by newbemac on 2007-06-03
thanks for your help,
i must leave now but will check the thread in a few hours
mac

---

### Post by arnieboy on 2007-06-03
> **newbemac said:**
> from the terminal I get

tom@tom-laptop:~$ sudo apt-get install automatix2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
automatix2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libktnef1 libglib1.2 libmpeg3-1 sysvinit
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

when i enter AUTOMATIX2 in the terminal window i get

tom@tom-laptop:~$ automatix2
  File "/usr/bin/automatix.py", line 34, in <module>
    from resin_config import *
  File "/usr/lib/automatix2/resin_config.py", line 16, in <module>
    import xml_functions as xml
  File "/usr/lib/automatix2/xml_functions.py", line 11, in <module>
    import libxml2
ImportError: No module named libxml2

```
sudo apt-get install python-libxml2
```
and then run automatix

---

### Post by newbemac on 2007-06-03
thank you, it works......
many many thanks
mac

---

