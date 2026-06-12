---
title: "Custom installCD, ubuntu-keyring"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by mcgru on 2007-11-13
I encountered problems with ubuntu-keyring.
I try to create a custom installation CD (Kubuntu 7.10).

My steps are similar to those described in [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization) (concerning keyring):
1. Create my own gpg key pair
2. Install sources of ubuntu-keyring
2a. install dpkg-dev, fakeroot (necessary to package rebuilding)
3. gpg --import < ubuntu-archive-keyring.gpg
4. gpg --export  > ubuntu-archive-keyring.gpg
5. Rebuild .deb and .udeb with: dpkg-buildpackage -rfakeroot -m"near my name" -kMYOWNKEY
6. Copy .deb and .udeb to /cdrom/pool/main/u/ubuntu-keyring (folder on hdd, but then it will be on cd)
Then i should use apt-ftparchive as described in [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization) , but instead i decided to slightly change existing files /cdrom/dists/gutsy/main/binary-i386/Packages and /cdrom/dists/gutsy/main/debian-installer/binary-i386/Packages (then made gzipped files).
7. In Packages files i changed there md5 checksums of newer .deb and .udeb, and cut off sha1- and sha256- checksums.
8. Then i manually changed corresponding records in /cdrom/dists/gutsy/Release (put there new md5 checksums of Packages and Packages.gz files)
9. Sign Release file with: gpg -bao Release.gpg Release (then providing passphrase for MYOWNKEY)
10. Burn CD and boot it on another computer.

During installation process debian-installer shows error with text like "... ubuntu-keyring_....deb is corrupted ...". It goes then to impossibility to install a kernel.

Switching to tty2 and chrooting to /target, i found, that list `apt-key list`consists only from default "Ubuntu Archive Key" (or smth like that). My own key is missing.

Where i get wrong during preparation of custom install cd?
Or how to put my own key into APT during ubuntu install process?

---

### Post by mcgru on 2007-11-13
Made another run, creation of custom install CD.
Try to repeat procedure on ubuntu-keyring preparation, as described in [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

i. Prepared the boot CD from 
2d7bd8c5883975ca7fb99c3be7b0474a kubuntu-7.10-alternate-i386.iso

ii. Booted that CD and installed Kubuntu with unplugged network cable. Rebooted into installed Kubuntu, kdm loaded, network cable plugged, /etc/apt/sources.list edited (added local gutsy repository, and uncommented deb-src repo).

iii. Copied CD into local directory
```
mkdir -p /opt/cd-image; mount /cdrom; cd /cdrom; find . | cpio -p /opt/cd-image;
cd ~;
```

iv. GPG keys pair creation.
```
# I created the pair earlier, so i just import the secret and public keys from another computer. S&P keys stored in keypair.key
scp root@another-host:/keys/keypair.key .
gpg --import keypair.key
gpg --list-keys
  # i see my key

```
v. Install fakeroot and dpkg-dev
```
aptitude install fakeroot dpkg-dev
```

vi. Downloaded source of ubuntu-keyring
```
apt-get source ubuntu-keyring
  gpg: Signature made ....... DSA key ID 10FA4CD1
  gpg: Can't check signature: public key not found
  dpkg-source: extracting....
  dpkg-source: unpacking ubuntu-keyring_2007.06.11.tar.gz

```
vii. Exporting my keys into ubuntu-archive-keyring.gpg
```
cd ubuntu-keyring-2007.06.11/keyrings
gpg --import < ubuntu-archive-keyring.gpg
  gpg: key 437D05B5 .... imported
  gpg: key FBB75451 .... imported
gpg --list-keys
  # i see all 3 keys
gpg --export B6576EB0 437D05B5 FBB75451 > ubuntu-archive-keyring.gpg
cd ..

```
viii. Preparation of .deb and .udeb files
```
dpkg-buildpackage -rfakeroot -m"My Name <my.email@my.host>" -kB6576EB0
  # it asked me 2 times to type the password while signing the .dsc and .changes files
cd ..
cp ubuntu-keyring*deb /opt/cd-image/pool/main/u/ubuntu-keyring

```
ix. Building the repository with apt-ftparchive
```
mkdir -p /opt/indices /opt/apt-ftparchive
cd /opt/indices/
DIST=gutsy; wget http://archive.ubuntu.com/ubuntu/indices/override.$DIST.{extra.main,main,main.debian-installer,restricted,restricted.debian-installer}

```

Then i repeated all that described in [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization) from block "Building the repository with apt-ftparchive" until block "Burning the image to CD" including "Burning (building) the CD". Just changed "dapper" on "gutsy" and YOURKEYID on B6576EB0 (my key id).
Encountered 1 error concerning extras, but i had no extras in this run.
Provided the passphrase to unlock the secret key while signing /opt/cd-image/dists/gutsy/Release.gpg

```
aptitude install mkisofs
bash buildiso.sh

```
where buildiso.sh consists of:
```
IMAGE=custom.iso
BUILD=/opt/cd-image/

mkisofs -r -V "Custom Ubuntu Install CD" \
            -cache-inodes \
            -J -l -b isolinux/isolinux.bin \
            -c isolinux/boot.cat -no-emul-boot \
            -boot-load-size 4 -boot-info-table \
            -o $IMAGE $BUILD

```

Then i copied this ISO to the host with K3B, burned the CD and tried to boot it...
Will see results in few minutes... (now i'll post this message to the board, then i'll edit it)

---

### Post by mcgru on 2007-11-13
> **mcgru said:**
> Will see results in few minutes... (now i'll post this message to the board, then i'll edit it)
Too much to edit :) , so i'll begin another message.

After booting the new CD, installation process interrupted with error "Coudn't configure PPPoE" or "no concentrator found on eth0".
I have no pppoe connections. It is strange, because in original CD there were no such error.
OK, i continued installation from menu item "Configure the network".

During installation more questions asked, probably it is because of lower priority (boot parameter) of installation.

Why it takes so long to understand that if i have my network cable unplugged, it is not necessary to check http method to get packages? Definitely, it's a todo for developers.


Well, it seems that all done OK. After my full run on customizing install CD there were no errors like "ubuntu-keyring is corrupted" as it were before.
So...
&#1084;&#1086;&#1088;&#1072;&#1083;&#1100; &#1089;&#1077;&#1081; &#1073;&#1072;&#1089;&#1085;&#1080; &#1090;&#1072;&#1082;&#1086;&#1074;&#1072;: &#1085;&#1077;&#1093;&#1088;&#1077;&#1085; &#1080;&#1079;&#1074;&#1088;&#1072;&#1097;&#1072;&#1090;&#1100;&#1089;&#1103; &#1089;&#1086; &#1074;&#1089;&#1103;&#1082;&#1080;&#1084;&#1080; &#1084;&#1072;&#1085;&#1091;&#1072;&#1083;&#1100;&#1085;&#1099;&#1084;&#1080; &#1090;&#1077;&#1088;&#1072;&#1087;&#1080;&#1103;&#1084;&#1080;.
&#1057;&#1082;&#1072;&#1079;&#1072;&#1085;&#1086; &#1073;&#1099;&#1083;&#1086; &#1076;&#1077;&#1083;&#1072;&#1090;&#1100; &#1095;&#1077;&#1088;&#1077;&#1079; apt-ftpsrchive - &#1090;&#1072;&#1082; &#1080; &#1085;&#1072;&#1076;&#1086; &#1073;&#1099;&#1083;&#1086; &#1076;&#1077;&#1083;&#1072;&#1090;&#1100;!
&#1059;&#1073;&#1080;&#1083; 3 &#1076;&#1085;&#1103; &#1085;&#1072; &#1090;&#1086;, &#1095;&#1090;&#1086;&#1073;&#1099; &#1088;&#1072;&#1079;&#1086;&#1073;&#1088;&#1072;&#1090;&#1100;&#1089;&#1103; "&#1072; &#1087;&#1086;&#1095;&#1077;&#1084;&#1091; &#1091; &#1084;&#1077;&#1085;&#1103; &#1085;&#1077; &#1087;&#1086;&#1083;&#1091;&#1095;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1086;&#1076;&#1089;&#1091;&#1085;&#1091;&#1090;&#1100; &#1089;&#1074;&#1086;&#1081; &#1082;&#1083;&#1102;&#1095;&#1080;&#1082;"... 
&#1051;&#1091;&#1095;&#1096;&#1077; &#1073; &#1089;&#1088;&#1072;&#1079;&#1091; &#1088;&#1072;&#1079;&#1086;&#1075;&#1085;&#1072;&#1083;&#1089;&#1103; &#1080; "&#1072;&#1087; &#1089;&#1090;&#1077;&#1085;&#1091;".

The problem is solved.
I will not delete this thread to let other people see my mistakes (in first, manual, run) ;)

---

### Post by bdk6m2007 on 2008-02-08
Did you ever figure out a solution to the PPPoE concentrator problem?  I'm trying to make a fully automated install disk and it is mostly working except that I get this error (same situation - there's not pppoe stuff at all so I'm pretty confused).:confused:

---

