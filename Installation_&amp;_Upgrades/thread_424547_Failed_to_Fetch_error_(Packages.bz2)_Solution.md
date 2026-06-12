---
title: "Failed to Fetch error (Packages.bz2) Solution"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by skwishybug on 2007-04-26
[COLOR=Black]After much searching and finding no working solution, I did some mucking around to upgrade from Edgy to Feisty.

The error I was receiving was: 
[/COLOR]  [COLOR=Black]Failed to fetch [http://security.ubuntu.com/ubuntu/di...6/Packages.bz2]("http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2") Sub-process bzip2 returned an error code (2)
[/COLOR][COLOR=Black]Failed to fetch [http://security.ubuntu.com/ubuntu/di...6/Packages.bz2]("http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2") Sub-process bzip2 returned an error code (2)

The Solution I came up with was as follows:

1. Visit: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)   and generate a new source list.

2. Edit your source list:   
```
gksu gedit /etc/apt/source.list
```3. Copy the generated source list from the website and paste it over the existing list

4. Save the source list

5. Run the update manager
```
gksu "update-manager -c"
```

Hope this works for you too. Let me know if it does.[/COLOR]

---

### Post by aethralis on 2007-10-01
Had similar problem. Solution did indeed work. Thanks.

---

### Post by shanport on 2008-02-01
Web page no longer exists from original post.

---

### Post by zvacet on 2008-02-01
You can use this one

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
 #deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) edgy free non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
```
sudo apt-get update && sudo apt-get upgrade
```

```
gksu "update-manager -c"
```

---

### Post by johnc1970 on 2008-03-23
Got the following when upgrading from feisty to gutsy:

[FONT="Courier New"]Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)[/FONT]

Tried the fix listed above and tried to upgrade from the command line, but got the following error:

[FONT="Courier New"]sudo apt-get update && sudo apt-get upgrade

Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [118kB]
99% [6 Packages bzip2 0] [Waiting for headers][COLOR="Blue"]bzip2: (stdin) is not a bzip2 file[/COLOR].
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  Sub-process bzip2 returned an error code (2)

Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [118kB]
99% [Working][COLOR="Blue"]bzip2: (stdin) is not a bzip2 file[/COLOR].
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  Sub-process bzip2 returned an error code (2)[/FONT]

I can browse to the file in Firefox ok, so I don't think it's a network issue...  Any help would be appreciated.


Thanks,
John

---

### Post by johnc1970 on 2008-03-27
I downloaded a Feisty update to bzip (on 26 March 08) and the error messages have now changed:


[FONT="Courier New"]Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2) MD5Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2) MD5Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz) Bad header line
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz) Bad header line
[/FONT]

I still haven't managed to upgrade...


Cheers,
John

---

