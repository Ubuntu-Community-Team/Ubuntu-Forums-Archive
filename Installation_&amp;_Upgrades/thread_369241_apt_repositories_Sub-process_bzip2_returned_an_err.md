---
title: "apt repositories: Sub-process bzip2 returned an error code (2)"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by gerdt on 2007-02-24
Hello, I have a problem with my sources.list. I have search this forum for quite some time now, but I haven't found a (full) solution to my problem.

First of all, I have this problem with Dapper. I use Kubuntu.

I installed Kubuntu on a new PC, and I got the problem that I couldn't do a correct apt-get update. 
I got all these kind of errors:
```
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

```
```
Sub-process bzip2 returned an error code (2)
```
```
Failed to fetch http://URL/Packages.bz2  Sub-process bzip2 returned an error code (2)
```

At first I thought that there was a problem with bzip2 or something, but after looking through the ubuntuforums I found a partial solution to my problem: Change all http's in your sources.list into ftp's. And it worked!!! But only for the *.ubuntu.com repositories. Not for the others... 

Here is my sources.list:

```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

deb ftp://nl.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src ftp://nl.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb ftp://nl.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src ftp://nl.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb ftp://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src ftp://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb ftp://nl.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src ftp://nl.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## Medibuntu - Ubuntu 6.06 LTS "dapper drake"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
[B]deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free[/B]

```

When I do apt-get update everything goes well, except for medibuntu:

```
[B]Get:1 http://medibuntu.sos-sts.com dapper Release.gpg [191B]
Hit http://medibuntu.sos-sts.com dapper Release[/B]
Hit ftp://nl.archive.ubuntu.com dapper Release.gpg
Hit ftp://nl.archive.ubuntu.com dapper-updates Release.gpg
Hit ftp://security.ubuntu.com dapper-security Release.gpg
Hit ftp://nl.archive.ubuntu.com dapper-backports Release.gpg
Get:2 ftp://security.ubuntu.com dapper-security Release [50.9kB]
Get:3 ftp://nl.archive.ubuntu.com dapper Release [34.8kB]
Hit ftp://security.ubuntu.com dapper-security/main Packages
Hit ftp://security.ubuntu.com dapper-security/restricted Packages
Get:4 ftp://nl.archive.ubuntu.com dapper-updates Release [50.9kB]
Hit http://medibuntu.sos-sts.com dapper/free Packages
Hit ftp://security.ubuntu.com dapper-security/universe Packages
Hit ftp://security.ubuntu.com dapper-security/multiverse Packages
Hit ftp://security.ubuntu.com dapper-security/main Sources
Hit ftp://security.ubuntu.com dapper-security/restricted Sources
Get:5 ftp://nl.archive.ubuntu.com dapper-backports Release [38.4kB]
Hit ftp://security.ubuntu.com dapper-security/universe Sources
Hit ftp://security.ubuntu.com dapper-security/multiverse Sources
[B]Get:6 http://medibuntu.sos-sts.com dapper/non-free Packages [1671B]
99% [Query] [Waiting for headers]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:7 http://medibuntu.sos-sts.com dapper/free Sources [880B]
Err http://medibuntu.sos-sts.com dapper/non-free Packages
  Sub-process bzip2 returned an error code (2)
Hit ftp://nl.archive.ubuntu.com dapper/main Packages
99% [Waiting for headers]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://medibuntu.sos-sts.com dapper/free Sources
  Sub-process bzip2 returned an error code (2)
Hit http://medibuntu.sos-sts.com dapper/non-free Sources
[/B]Hit ftp://nl.archive.ubuntu.com dapper/restricted Packages
Hit ftp://nl.archive.ubuntu.com dapper/universe Packages
Hit ftp://nl.archive.ubuntu.com dapper/multiverse Packages
Hit ftp://nl.archive.ubuntu.com dapper/main Sources
Hit ftp://nl.archive.ubuntu.com dapper/restricted Sources
Hit ftp://nl.archive.ubuntu.com dapper/universe Sources
Hit ftp://nl.archive.ubuntu.com dapper/multiverse Sources
Hit ftp://nl.archive.ubuntu.com dapper-updates/main Packages
Hit ftp://nl.archive.ubuntu.com dapper-updates/restricted Packages
Hit ftp://nl.archive.ubuntu.com dapper-updates/universe Packages
Hit ftp://nl.archive.ubuntu.com dapper-updates/multiverse Packages
Hit ftp://nl.archive.ubuntu.com dapper-updates/main Sources
Hit ftp://nl.archive.ubuntu.com dapper-updates/restricted Sources
Hit ftp://nl.archive.ubuntu.com dapper-updates/universe Sources
Hit ftp://nl.archive.ubuntu.com dapper-updates/multiverse Sources
Hit ftp://nl.archive.ubuntu.com dapper-backports/main Packages
Hit ftp://nl.archive.ubuntu.com dapper-backports/restricted Packages
Hit ftp://nl.archive.ubuntu.com dapper-backports/universe Packages
Hit ftp://nl.archive.ubuntu.com dapper-backports/multiverse Packages
Hit ftp://nl.archive.ubuntu.com dapper-backports/main Sources
Hit ftp://nl.archive.ubuntu.com dapper-backports/restricted Sources
Hit ftp://nl.archive.ubuntu.com dapper-backports/universe Sources
Hit ftp://nl.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 177kB in 4s (40.5kB/s)
[B]Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]
```

So to summarize my problem: I believe that for some reason, apt-get on this machine does not understand http, and therefor I cannot place repositories in my sources.list that do not have ftp access.
I hope some of you can help me out, thank you all in advance!

---

### Post by n8bounds on 2007-02-25
When I ever get the bzip error, I think I am downloading headers as they are being changed.  In any case, waiting a few and trying again always cleared it up for me.

---

### Post by gerdt on 2007-02-25
n8bounds, thank you for your reply, but in this case this is not a solution. This problem is going on for several weeks now (almost 2,5 months now) ever since I installed it.
I was thinking, could this be a firewall related problem? As I said in my post above, the sources.list appear to work perfectly as long as the repositories are ftp locations, therefor I never considered the possibility of a firewall related problem. 
Does apt use different ports for repositories working with http or ftp ???

---

