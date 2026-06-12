---
title: "How to update Synaptic offline"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by EthioJOB on 2011-01-31
I have Ubuntu 10.10 installed on my offline PC and I was wondering if any of you can help me get an updated repository for Synaptic using a online PC elsewhere. I need this so that I could generate package scripts to be used elsewhere to download software.

I'd appreciate a step by step instruction.

---

### Post by zvacet on 2011-02-01
Try [Keryx.]("http://keryxproject.org/")

---

### Post by Frogs Hair on 2011-02-01
Here is an off line repository link .[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by EthioJOB on 2011-02-26
> **Frogs Hair said:**
> Here is an off line repository link .[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Hey, it been a while. I followed the instructions but it keeps on failing to reload Synaptic. It just displays the following.

```
W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-backports/Release.gpg  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://et.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/i18n/Translation-en_US.bz2  Could not resolve 'et.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch file:/dists////ethiojob/repository/dists/maverick/source/Sources.gz  File not found

W: Failed to fetch file:/dists////ethiojob/repository/dists/main/source/Sources.gz  File not found

W: Failed to fetch file:/dists////ethiojob/repository/dists/restricted/source/Sources.gz  File not found

W: Failed to fetch file:/dists////ethiojob/repository/dists/universe/source/Sources.gz  File not found

W: Failed to fetch file:/dists////ethiojob/repository/dists/multiverse/source/Sources.gz  File not found

W: Failed to fetch file:/dists////ethiojob/repository/dists/maverick/binary-i386/Packages.gz  File not found

W: Failed to fetch file:/dists////ethiojob/repository/dists/main/binary-i386/Packages.gz  File not found

W: Failed to fetch file:/dists////ethiojob/repository/dists/restricted/binary-i386/Packages.gz  File not found

W: Failed to fetch file:/dists////ethiojob/repository/dists/universe/binary-i386/Packages.gz  File not found

W: Failed to fetch file:/dists////ethiojob/repository/dists/multiverse/binary-i386/Packages.gz  File not found

W: Some index files failed to download, they have been ignored, or old ones used instead.

```It also asks me to insert the CD-ROM, and when I do it doesn't reload it, still failing.

What am I missing here?

(Also, some of the files to be downloaded -the 'Release' ones - are .html. Is it OK to use them as they are or do I have to copy-paste the text in them in a text file/convert them to text files?)

---

### Post by EthioJOB on 2011-03-03
Bump.

---

### Post by Frogs Hair on 2011-03-03
I have no further instructions other than the community documentation . When asked to insert disk are you using the Ubuntu ISO or the repository disk you created ?

You still need internet access to create your repository disk that can be used on an off-line computer

---

### Post by sreilly@alionscience.com on 2011-03-03
I'm having the same problem, and it appears to be because the community documentation referenced above is incomplete.  In addition to the [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) directory data that they show you how to use, you also need to grab the appropriate *.deb files from the .../pool/ directories.  Now all that I have to do it to figure out how to guess which of these *.deb file are the appropriate ones.

I need to do this, because my local IT department requires use to keep up-to-date with security patches even if those systems have no network connection.  My current effort is to use wget on a windows box (cuz that what my IT person has) and the following script

echo on 
pushd "C:\Program Files\GnuWin32\bin" 
wget --mirror --no-parent --accept *ubuntu5_amd64.deb,*ubuntu5_all.deb ^ 
 --directory-prefix="%HOMEPATH%\My Documents"^ 
 http://archive.ubuntu.com/ubuntu/pool/main^ 
 [http://archive.ubuntu.com/ubuntu/pool/restricted](http://archive.ubuntu.com/ubuntu/pool/restricted) 
wget --mirror --no-parent --reject *.html*^ 
 --directory-prefix="%HOMEPATH%\My Documents"^ 
 http://archive.ubuntu.com/ubuntu/dists/lucid/Contents-amd64.gz^ 
 http://archive.ubuntu.com/ubuntu/dists/lucid/Release^ 
 http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg^ 
 http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/^ 
 [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/) 
popd 
pause

Note that ^ is the Windows line continuation character and that "%HOMEPATH%\My Documents" is just the Windows home directory for the current user.  Once I'm done, I should be able to make a CD, carry it to the off-line machine and pick up with the community documentation reference.

Anyone know of a more automated way to do this?

---

### Post by EthioJOB on 2011-03-04
> **Frogs Hair said:**
> I have no further instructions other than the community documentation . When asked to insert disk are you using the Ubuntu ISO or the repository disk you created ?

You still need internet access to create your repository disk that can be used on an off-line computer

It asks for the CD ROM when I'm trying to use the repository I created. Which brings me to the question as to why it asks for the CD when I don't want to use it. I *do* have internet access elsewhere; I just need to know how to utilize it for use on my offline PC.

@sreilly@alionscience.com

You could be right about the documentation being incomplete, and if you are, then apparently we could be stuck.

Jeez, ubuntu can really leave you out cold if you're offline.

---

### Post by sreilly@alionscience.com on 2011-03-04
Fortunately, we still have each other.  The windows batch file is getting closer.  It is using --accept *_amd64.deb,*_all.deb instead of just gabbing the ubuntu5 files. 
 
rem *
rem * Windows batch file that uses "wget" utility to create a mirror 
rem * of select directories from archive.ubuntu.com.  User then copies the 
rem * "dists" and "pool" directories onto a CD-ROm with "ubuntu" 
rem * in the volume label.
rem *
echo on
pushd "C:\Program Files\GnuWin32\bin"
rem *
rem * apt-get indices for lucid distribution (main, restricted)
rem *
set SITE=ftp://archive.ubuntu.com/ubuntu/dists/lucid
wget --mirror --no-parent --reject *.html*^
 --directory-prefix="%HOMEPATH%\My Documents"^
 %SITE%/Contents-amd64.gz^
 %SITE%/Release^
 %SITE%/Release.gpg^
 %SITE%/main/binary-amd64/^
 %SITE%/restricted/binary-amd64/
rem *
rem * apt-get indices for lucid-updates distribution (main, restricted)
rem *
set SITE=ftp://archive.ubuntu.com/ubuntu/dists/lucid-updates
wget --mirror --no-parent --reject *.html*^
 --directory-prefix="%HOMEPATH%\My Documents"^
 %SITE%/Contents-amd64.gz^
 %SITE%/Release^
 %SITE%/Release.gpg^
 %SITE%/main/binary-amd64/^
 %SITE%/restricted/binary-amd64/
rem *
rem * apt-get indices for lucid-security distribution (main, restricted)
rem *
set SITE=ftp://archive.ubuntu.com/ubuntu/dists/lucid-security
wget --mirror --no-parent --reject *.html*^
 --directory-prefix="%HOMEPATH%\My Documents"^
 %SITE%/Contents-amd64.gz^
 %SITE%/Release^
 %SITE%/Release.gpg^
 %SITE%/main/binary-amd64/^
 %SITE%/restricted/binary-amd64/
rem *
rem * debian packages for actual binaries
rem *
set SITE=ftp://archive.ubuntu.com/ubuntu/pool
wget --mirror --no-parent --accept *_amd64.deb,*_all.deb ^
 --directory-prefix="%HOMEPATH%\My Documents"^
 %SITE%/main^
 %SITE%/restricted
rem *
rem * downloads complete
rem * 
popd
pause
 
I suspect that this is going to cause me to grab a bunch of older files that I don't want.  The right way to do it would be to parse the Packages.gz and Packages.bz2 files.  But, that would be pretty darn hard to do in Windows.  I give the "too much data" method a try and tell you what I find out.
 
Sean

---

### Post by sreilly@alionscience.com on 2011-03-07
Giving up on the Windows script. I'll get it working in bash first, then backfit it to windows later. Here is the script so far:
 
```
 
#!/bin/bash
# uses wget to create a repository for updating off-line Ubuntu systems
 
set -x -e # show commands as they happen, exit on errors
 
# define download parameters
# hardcoded for now
REPO=ftp://archive.ubuntu.com/ubuntu
CODENAME=lucid-security
ARCH=amd64
DEST=~/mydocuments
 
# download the indicies for this CODENAME
# limit to "main" and "restricted" components
SITE=$REPO/dists/$CODENAME
wget --mirror --no-parent --directory-prefix=$DEST \
    $SITE/Contents-$ARCH.gz $SITE/Release $SITE/Release.gpg \
    $SITE/main/binary-$ARCH/ $SITE/restricted/binary-$ARCH/
 
# search these indicies to find the *.deb files to download
# repeat for both "main" and "restricted" components
DIR=$DEST/${REPO/ftp:\/\//}/dists/$CODENAME/main/binary-$ARCH
gunzip --to-stdout $DIR/Packages.gz | grep "Filename: " \
    | sed {s/"Filename: "/${REPO//\//\\\/}\\\//} > packages.txt
DIR=$DEST/${REPO/ftp:\/\//}/dists/$CODENAME/restricted/binary-$ARCH
gunzip --to-stdout $DIR/Packages.gz | grep "Filename: " \
    | sed {s/"Filename: "/${REPO//\//\\\/}\\\//} >> packages.txt
 
# download the *.deb files for this CODENAME
wget --mirror --no-parent --directory-prefix=$DEST -i packages.txt
rm packages.txt
 

```

---

