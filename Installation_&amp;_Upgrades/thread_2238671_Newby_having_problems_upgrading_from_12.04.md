---
title: "Newby having problems upgrading from 12.04"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by sean51 on 2014-08-09
Hello all,

I am a relative newby, as I only fire up my Ubuntu system every now and then but, I was having problems with my 12.04 version, not enough space on my extended partition to upgrade, not being how to work out how to resize my extended partition, despite there being space etc. So, I deleted a few files and simply tried to upgrade from a CD to 12.10.

Unfortunately, since then, I have not been able to access my drives because of the following error:

Unable to mount 218 GB Volume

Adding read ACL for uid 1000 to `/media/sean' failed: Operation not supported

And when I try to upgrade any software as it says I don't have internet connection, which obviously I do as I am typing here.

When I use the command sudo apt-get upgrade or update I get a load of fetch errors such as:

sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources/DiffIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources/DiffIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports Release.gpg       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal Release                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates Release             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports Release           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Sources/DiffIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Sources/DiffIndex  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Translation-en
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Sources
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.201 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

I've found a few similar "help" threads but none seem to be similar enough for me to decipher how to sort this problem. Most seem to suggest its about my source list but my source list has not looked like those in help threads and I can't how to adapt it as described.

My source list looks like this:

# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main #Third party developers repository
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main

I assume these problems are simple to solve and I am just being dumb but any help would be much appreciated.

Thanks in anticipation

Sean

---

### Post by grahammechanical on 2014-08-09
> [COLOR=#000000]I assume these problems are simple to solve[/COLOR]

Yes, it is simple to solve if you accept that re-installing Ubuntu 12.04 is the simple option.

Ubuntu 12.10 is end of life. We cannot now upgrade from 12.04 to 12.10. Besides which upgrading to a newer release is not necessarily the fix for problems. We might find that the problems have carried over to the upgraded version. Based upon my experience a fresh/new install often fixes problems.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

My advice is to download either Ubuntu 12.04.5 or Ubuntu 14.04.1 and use a live session to back up any documents that you do not want to lose and then install afresh.

Regards.

---

### Post by sean51 on 2014-08-09
To be honest, I have all my docs etc. on a separate partition for just this reason so, I may have a rew files on my desktop but nothing really critical.

So, your suggestion is to simply install a fresh version of Ubuntu over the last one and it should be OK?

I have to say, I've followed guides (I think, including the link you gave) to try and increase the size of my extended partition, that Ubuntu is installed on, and none of the solutions seem to work.

I'll try again.

Thanks for your help

Sean

---

### Post by ubfan1 on 2014-08-09
Resizing the partitions (assuming you do it right) is the first step, then look at the resize2fs command (man resize2fs).  The reinstall is probably still a good idea, but be REALLY careful and do NOT select the live media's offer to "update Ubuntu" or words to that effect -- the missing part of the offer is "WIPE DISK and" , so everything you think is safe in another partition will be wiped.

---

