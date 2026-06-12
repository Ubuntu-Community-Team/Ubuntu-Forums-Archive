---
title: "Updates no longer working"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by Odense on 2013-11-08
I am running Ubuntu 12.04 on an Samsung RV510 laptop

In my Update Manager I have the following message:

"Software updates may be available for your computer.
The package information was last updated 9 days ago."

Even though I can download and install some updates in the Update Manager the message persists.

I have tried to use the Terminal Window also with the following commands:

sudo apt-get update && sudo apt-get dist-upgrade

The results from this is:

"W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead."

After that I opened the Update Manager and I still have the following message:

"Software updates may be available for your computer.
The package information was last updated 9 days ago."

WHat can I do to rectify the problem ?

---

### Post by Bucky Ball on 2013-11-08
That indicates that this repo server is currently down:

 [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release) 

You might want to try it again tomorrow or try changing the server by opening Update Manager, clicking 'Settings' at bottom left and changing the server in the first tab window.

You have added this repo manually, yes?

---

### Post by Odense on 2013-11-08
Hmm - it was also not working yesterday - but it has been working well for a long time.
What is included in a Repo ? I have added a few sources/applications manually ?
If I click on the [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release) I get:

Origin: LP-PPA-app-review-board
Label: Application Review Board PPA
Suite: precise
Version: 12.04
Codename: precise
Date: Fri, 15 Feb 2013 15:05:54 UTC
Architectures: amd64 armel armhf i386 powerpc
Components: main
Description: Ubuntu Precise 12.04
MD5Sum:
 7e0a2dc5fb8c8bf6922bbe396d66addc              136 main/binary-amd64/Release
 529267ce92bc20387c1de25a745a8f31            11858 main/binary-amd64/Packages.gz
 c3265772d26cc0846fe30c18477c9d8f            35415 main/binary-amd64/Packages
 4019d042f1f2fe7644056a366b3364f1            10788 main/binary-amd64/Packages.bz2
 5d3e88adf3808442dfd95ac307793647            29551 main/binary-armel/Packages
 7345b995ca20588334bbf61f225eb13a             8776 main/binary-armel/Packages.bz2
 54a0f788fa15a5732e41ce407c94865f              136 main/binary-armel/Release
 ee008f3671557b31e107483e54272e9f             9606 main/binary-armel/Packages.gz
 ee008f3671557b31e107483e54272e9f             9606 main/binary-armhf/Packages.gz
 e977bbd456b73f23a02d3231429b5149              136 main/binary-armhf/Release
 7345b995ca20588334bbf61f225eb13a             8776 main/binary-armhf/Packages.bz2
 5d3e88adf3808442dfd95ac307793647            29551 main/binary-armhf/Packages
 d236b9461089746334d3f4ea9c593aa3            35407 main/binary-i386/Packages
 cd8c2ae9970ced4a773275ef46c0bbe5              135 main/binary-i386/Release
 a7111e0bc5e918b8ef316ef933bf6e23            10788 main/binary-i386/Packages.bz2
 90a15cdf190b2c7ba2b67ca12be21806            11855 main/binary-i386/Packages.gz
 7345b995ca20588334bbf61f225eb13a             8776 main/binary-powerpc/Packages.bz2
 ee008f3671557b31e107483e54272e9f             9606 main/binary-powerpc/Packages.gz
 5d3e88adf3808442dfd95ac307793647            29551 main/binary-powerpc/Packages
 d4ec4b93f4d563c89dfd4875a3daa7c4              138 main/binary-powerpc/Release
 29c1057ebae356e25d1a0490708239b6               29 main/debian-installer/binary-amd64/Packages.gz
 d41d8cd98f00b204e9800998ecf8427e                0 main/debian-installer/binary-amd64/Packages
 4059d198768f9f8dc9372dc1c54bc3c3               14 main/debian-installer/binary-amd64/Packages.bz2
 56ce1d97b0803f40249a6a63a43a2cc2               29 main/debian-installer/binary-armel/Packages.gz
 d41d8cd98f00b204e9800998ecf8427e                0 main/debian-installer/binary-armel/Packages
 4059d198768f9f8dc9372dc1c54bc3c3               14 main/debian-installer/binary-armel/Packages.bz2
 56ce1d97b0803f40249a6a63a43a2cc2               29 main/debian-installer/binary-armhf/Packages.gz
 d41d8cd98f00b204e9800998ecf8427e                0 main/debian-installer/binary-armhf/Packages
 4059d198768f9f8dc9372dc1c54bc3c3               14 main/debian-installer/binary-armhf/Packages.bz2
 d41d8cd98f00b204e9800998ecf8427e                0 main/debian-installer/binary-i386/Packages
 56ce1d97b0803f40249a6a63a43a2cc2               29 main/debian-installer/binary-i386/Packages.gz
 4059d198768f9f8dc9372dc1c54bc3c3               14 main/debian-installer/binary-i386/Packages.bz2
 d41d8cd98f00b204e9800998ecf8427e                0 main/debian-installer/binary-powerpc/Packages
 4059d198768f9f8dc9372dc1c54bc3c3               14 main/debian-installer/binary-powerpc/Packages.bz2
 56ce1d97b0803f40249a6a63a43a2cc2               29 main/debian-installer/binary-powerpc/Packages.gz
 846b1db68b483af56f067810e524da71              137 main/source/Release
 ada8dc6d96857e5153a591e41452979d            33257 main/source/Sources
 453da4ed9a91f00ad4664ca7373aef02             8130 main/source/Sources.bz2
 f836984d44dfe2237709f37693f96bfa             8776 main/source/Sources.gz
SHA1:
 94f342e54c2ea0e8bd6b9d20284a7d84f03be033              136 main/binary-amd64/Release
 a3df790cecc0ca0fadbbcf2c7329c3435aea2766            11858 main/binary-amd64/Packages.gz
 e92a7cea285cce18561b5b9dbb5d1d788977208b            35415 main/binary-amd64/Packages
 807d780e437efcd456ec9302504b04f1edfdb13f            10788 main/binary-amd64/Packages.bz2
 23a90a828046b5a7812e755ae5ba6873b735a1a7            29551 main/binary-armel/Packages
 4364e496f93771ea60f90a1a4d55e19cc2b612f8             8776 main/binary-armel/Packages.bz2
 5cd8bbb59c463bff28469e234d56044adbd9e601              136 main/binary-armel/Release
 18324affba5585548e019ea4fcf6e6cc906e4509             9606 main/binary-armel/Packages.gz
 18324affba5585548e019ea4fcf6e6cc906e4509             9606 main/binary-armhf/Packages.gz
 96dced579ee29582ba5ec0797452bd839529c7ff              136 main/binary-armhf/Release
 4364e496f93771ea60f90a1a4d55e19cc2b612f8             8776 main/binary-armhf/Packages.bz2
 23a90a828046b5a7812e755ae5ba6873b735a1a7            29551 main/binary-armhf/Packages
 c9fbee537bdebf51887afbdde878837bd397b7fc            35407 main/binary-i386/Packages
 620a4d6771cb74d8cb60492df9d2f018b7760eca              135 main/binary-i386/Release
 3556d8d91cf3c102dd7e338e447df4c5d820ecb7            10788 main/binary-i386/Packages.bz2
 6e9de906fc07cf8d3b3137e7301a3f11f12fa505            11855 main/binary-i386/Packages.gz
 4364e496f93771ea60f90a1a4d55e19cc2b612f8             8776 main/binary-powerpc/Packages.bz2
 18324affba5585548e019ea4fcf6e6cc906e4509             9606 main/binary-powerpc/Packages.gz
 23a90a828046b5a7812e755ae5ba6873b735a1a7            29551 main/binary-powerpc/Packages
 87d96bff16d3339305207102ff23f6236e30fb99              138 main/binary-powerpc/Release
 a8914e153d367323e964d3e448dceec21069604f               29 main/debian-installer/binary-amd64/Packages.gz
 da39a3ee5e6b4b0d3255bfef95601890afd80709                0 main/debian-installer/binary-amd64/Packages
 64a543afbb5f4bf728636bdcbbe7a2ed0804adc2               14 main/debian-installer/binary-amd64/Packages.bz2
 3cf473a5f06dc68d1915ab03c05dfe451873436b               29 main/debian-installer/binary-armel/Packages.gz
 da39a3ee5e6b4b0d3255bfef95601890afd80709                0 main/debian-installer/binary-armel/Packages
 64a543afbb5f4bf728636bdcbbe7a2ed0804adc2               14 main/debian-installer/binary-armel/Packages.bz2
 3cf473a5f06dc68d1915ab03c05dfe451873436b               29 main/debian-installer/binary-armhf/Packages.gz
 da39a3ee5e6b4b0d3255bfef95601890afd80709                0 main/debian-installer/binary-armhf/Packages
 64a543afbb5f4bf728636bdcbbe7a2ed0804adc2               14 main/debian-installer/binary-armhf/Packages.bz2
 da39a3ee5e6b4b0d3255bfef95601890afd80709                0 main/debian-installer/binary-i386/Packages
 3cf473a5f06dc68d1915ab03c05dfe451873436b               29 main/debian-installer/binary-i386/Packages.gz
 64a543afbb5f4bf728636bdcbbe7a2ed0804adc2               14 main/debian-installer/binary-i386/Packages.bz2
 da39a3ee5e6b4b0d3255bfef95601890afd80709                0 main/debian-installer/binary-powerpc/Packages
 64a543afbb5f4bf728636bdcbbe7a2ed0804adc2               14 main/debian-installer/binary-powerpc/Packages.bz2
 3cf473a5f06dc68d1915ab03c05dfe451873436b               29 main/debian-installer/binary-powerpc/Packages.gz
 d5688343a7f20d641714aa595e89585ce9137659              137 main/source/Release
 8c8fee17e697dba3847d1aaa9b39d4f6329dea40            33257 main/source/Sources
 f83c70f95ef77d587d084009da609c272ed7fa3f             8130 main/source/Sources.bz2
 d5a73643846f0a24f0b7dee7c3b71dad3c60e513             8776 main/source/Sources.gz
SHA256:
 bbda604820414fcbf343ba57ef628a30d349be875b6e32e6a7026325a03c8936              136 main/binary-amd64/Release
 faf6d6be597ce557d8e53b4aac2efb1f6f9669e683091f8c123d34f0b407f361            11858 main/binary-amd64/Packages.gz
 c6b2a552889748dc0fe0a5c1e95c1647b4496c5bb431f260cf2f454e60f919a3            35415 main/binary-amd64/Packages
 41bb5837826fd66d37b5c520a948f5f50a9abf1e317d1d53f46d506260b85db7            10788 main/binary-amd64/Packages.bz2
 4c21bcef043f94e6df7c21401536cff469103ba9fc0bb20d3b81e430209cac32            29551 main/binary-armel/Packages
 e6d7b68198fe7ae6c28d7a8dcbc1851c6966493925e47b3e85fea63996edde95             8776 main/binary-armel/Packages.bz2
 64c80121ff85919781b9cf8481440c2471c31b8e3f7eb5d0b2e47363d696efff              136 main/binary-armel/Release
 8cb1c1dfa3356cb0170db8bf98f78bf5f4be0a523869ac55c1f993d5eff729cd             9606 main/binary-armel/Packages.gz
 8cb1c1dfa3356cb0170db8bf98f78bf5f4be0a523869ac55c1f993d5eff729cd             9606 main/binary-armhf/Packages.gz
 64a0821c214413a52107f04191c7835e8a10bbb38f0d5dbe881d59c85e481457              136 main/binary-armhf/Release
 e6d7b68198fe7ae6c28d7a8dcbc1851c6966493925e47b3e85fea63996edde95             8776 main/binary-armhf/Packages.bz2
 4c21bcef043f94e6df7c21401536cff469103ba9fc0bb20d3b81e430209cac32            29551 main/binary-armhf/Packages
 baad38fb53994fec48fb328d72f8a450b84074798699c8358c24f899f260748c            35407 main/binary-i386/Packages
 cc157b368e3fd12ab260ec54206baa4df2ce9681b005c61cc62767f83c1a36be              135 main/binary-i386/Release
 203da9b31b1bae2e808bd68b5fdee7ee2c09c6d18ea00e191c683459f3fa772e            10788 main/binary-i386/Packages.bz2
 870a5deea4cf7229e72659514208d03d4967b0c6404b950f3fe8907291d7a183            11855 main/binary-i386/Packages.gz
 e6d7b68198fe7ae6c28d7a8dcbc1851c6966493925e47b3e85fea63996edde95             8776 main/binary-powerpc/Packages.bz2
 8cb1c1dfa3356cb0170db8bf98f78bf5f4be0a523869ac55c1f993d5eff729cd             9606 main/binary-powerpc/Packages.gz
 4c21bcef043f94e6df7c21401536cff469103ba9fc0bb20d3b81e430209cac32            29551 main/binary-powerpc/Packages
 5019bc6f92880a9f297f80e5484e26b55f6786de69f880603e9a4b1bf7238822              138 main/binary-powerpc/Release
 f27eb57a763812430b8d0bee3e5cb10772ee262fff7662922a3e7ffa803187c5               29 main/debian-installer/binary-amd64/Packages.gz
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855                0 main/debian-installer/binary-amd64/Packages
 d3dda84eb03b9738d118eb2be78e246106900493c0ae07819ad60815134a8058               14 main/debian-installer/binary-amd64/Packages.bz2
 dfe7258d917627becb959e4f492a89ea270ecdefc5d4cd733fed4dd1e236a2ea               29 main/debian-installer/binary-armel/Packages.gz
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855                0 main/debian-installer/binary-armel/Packages
 d3dda84eb03b9738d118eb2be78e246106900493c0ae07819ad60815134a8058               14 main/debian-installer/binary-armel/Packages.bz2
 dfe7258d917627becb959e4f492a89ea270ecdefc5d4cd733fed4dd1e236a2ea               29 main/debian-installer/binary-armhf/Packages.gz
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855                0 main/debian-installer/binary-armhf/Packages
 d3dda84eb03b9738d118eb2be78e246106900493c0ae07819ad60815134a8058               14 main/debian-installer/binary-armhf/Packages.bz2
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855                0 main/debian-installer/binary-i386/Packages
 dfe7258d917627becb959e4f492a89ea270ecdefc5d4cd733fed4dd1e236a2ea               29 main/debian-installer/binary-i386/Packages.gz
 d3dda84eb03b9738d118eb2be78e246106900493c0ae07819ad60815134a8058               14 main/debian-installer/binary-i386/Packages.bz2
 e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855                0 main/debian-installer/binary-powerpc/Packages
 d3dda84eb03b9738d118eb2be78e246106900493c0ae07819ad60815134a8058               14 main/debian-installer/binary-powerpc/Packages.bz2
 dfe7258d917627becb959e4f492a89ea270ecdefc5d4cd733fed4dd1e236a2ea               29 main/debian-installer/binary-powerpc/Packages.gz
 0419c26616340747eecdfcf30b9d414955267255d275b4b259c7dca7a7b4ed56              137 main/source/Release
 cf950772bf26bd56aced4f94011ee8fc631d71dd681e0470c24bd3bc5c2e8fcb            33257 main/source/Sources
 81d0facc17cd2a93eb28ad610cbd547963a3cf32bac51db952ac70ba44aafbee             8130 main/source/Sources.bz2
 23188367087851e922370479e5c73efa8f4204f15121f21ec7667d499f6908da             8776 main/source/Sources.gz

---

### Post by Bucky Ball on 2013-11-08
A repository is a PPA, or personal package assistant. It basically holds a bunch of apps. You have added this repository (or PPA) manually and whatever server you are accessing it from is either down or the PPA has been removed. Untick that repository in the Software Sources 'Other Software' tab and see if you still get errors. 

That link for the repo I gave is not for clicking on, it is the address of the repo. While the PPA may be broken on the server you are accessing it on, it may be fine on another, so as I say, you could try changing servers in the Software Sources 'Ubuntu Software' tab (drop down list of servers).

---

### Post by Odense on 2013-11-08
Ahh I see - thanks.
I tried 3 different servers now - but no luck.

What ppa should I disable ? the ones I have are:

Independent
Independent (source code)
Canonical Partners
[http://repository.spotify.com](http://repository.spotify.com) stable non-free
[http://repository.spotify.com](http://repository.spotify.com) stable non-free (source code)
[http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise main
[http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise main (source code)
[http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu) precise main
[http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu) precise main (source code)
[http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable main

---

### Post by plucky on 2013-11-08
> "W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

That is the error you need to fix.


If you un-tick the "Independent" repositories it should not then try to access the "extra" repository and you can see if the error goes away.


After you un-tick the Independent server (both source code & main), open a terminal and run ```
sudo apt-get update
```

If that runs without any errors,try running ```
sudo apt-get upgrade
``` to see if your system updates your software.

---

### Post by Odense on 2013-11-08
Thanks for trying to explain - I must be slower than I hoped but as I said - I cannot SEE that this "[http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release" repository is added anywhere.

The ones I have are:
"Independent
Independent (source code)
Canonical Partners
[http://repository.spotify.com](http://repository.spotify.com) stable non-free
[http://repository.spotify.com](http://repository.spotify.com) stable non-free (source code)
[http://ppa.launchpad.net/stebbins/ha...eleases/ubuntu]("http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu") precise main
[http://ppa.launchpad.net/stebbins/ha...eleases/ubuntu]("http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu") precise main (source code)
[http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu) precise main
[http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu) precise main (source code)
[http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable main"

So what ppa should I disable ?

---

### Post by Bucky Ball on 2013-11-08
Untick the 'stebbins' PPAs. Update and report back. If that doesn't clear it, could you open a terminal and issue this:

```
nano /etc/apt/sources.list

```
Post the results back here please (between [code] tags if you will). ;)

---

### Post by Odense on 2013-11-08
It did not work - below is pasted the result of "nano /etc/apt/sources.list"

[Code]
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

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

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

# 1. Add this line to your list of repositories by
#    editing your /etc/apt/sources.list
# deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # disabled on upgrade to oneiric

deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free]
[Code]

---

### Post by heir4c on 2013-11-08
> 
"W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>


I delete my first answer because of a wrong command, Sorry!
Here a link to a solutions:
[http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors](http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors)

---

### Post by Odense on 2013-11-08
Not sure what I did - but I followed the instructions - I don't think it worked though - this is the error message after using the "sudo apt-get update && sudo apt-get upgrade":

Code[Fetched 2,202 kB in 7s (304 kB/s)                                              
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.]

---

### Post by heir4c on 2013-11-08
Sorry, it was the wrong command. See my previous post with a link to a solution: 
[http://ubuntuforums.org/showthread.php?t=2186626&p=12842323#post12842323](http://ubuntuforums.org/showthread.php?t=2186626&p=12842323#post12842323)
(I hope this is the right one.)

---

### Post by Odense on 2013-11-08
Thanks - answer no. 2 there ([http://askubuntu.com/questions/1877/...sig-gpg-errors]("http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors")) seems to be working for me.

---

### Post by heir4c on 2013-11-08
I'm glad it worked.

---

