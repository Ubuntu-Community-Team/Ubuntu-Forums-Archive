---
title: "Another  'no boot after update'"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by willie2000 on 2010-11-30
Hi all

Sorry to jump straight in with a problem. I'm experiencing the same problem mentioned [here]("http://ubuntuforums.org/showthread.php?t=1629755"); where it was suggested to start an individual thread.

I have been using ubuntu as a dual boot with vista for a couple of months. Apart from a few hiccups I've been very pleased, but after an update I am unable to boot ubuntu. It appears to be the same issue in the link above.

I originally installed 10.4 (because my first attempt with 10.10 would not install (turned out to be duff CD)) and then updated to 10.10. All was fine until this latest automatic update.

I've tried a few things suggested -- copying the c:\ubuntu\winboot\wubildr file over c:\wubildr -- with no luck... I'm worried about making things worse and thought I'd ask first. I hope that's OK.

I also tried working from my liveCD, but it only gave me the option to install (because it's 10.4 and I've updated???)

I can boot into windows, but know even less what I'm doing there. :p

Thanks in advance.

---

### Post by Rubi1200 on 2010-11-30
Hi and welcome to the forums :)

You should be able to start the Ubuntu CD and choose to try Ubuntu?

In any event, take a look here for some possible solutions:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
For a 10.04 install you need to use the fix that involves editing the grub.cfg file.
It may look a little daunting, but I have recently helped a number of users with this problem and it worked for them.

Good luck!

---

### Post by willie2000 on 2010-11-30
> **Rubi1200 said:**
> 
You should be able to start the Ubuntu CD and choose to try Ubuntu?
Thanks for the reply. The first thing I tried was the CD. I've just tried again, the only options I get are:

Install 
Check disk
Test memory
Boot from hard disk
rescue broken system

> **Rubi1200 said:**
> In any event, take a look here for some possible solutions:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
For a 10.04 install you need to use the fix that involves editing the grub.cfg file.
It may look a little daunting, but I have recently helped a number of users with this problem and it worked for them.

Good luck!

Without the liveCD I can't access a terminal. Unless there is another way of doing it?

Cheers

---

### Post by Rubi1200 on 2010-11-30
This an Ubuntu 10.04 CD; full version downloaded from the main site?

I would have thought the option to try would be there.

If you choose the > rescue broken system option where does it take you; to a terminal?

The only thing is this; I have never seen that option :confused:
(which means either I didn't look closely enough or never needed to use it!?!)

It might be better to boot into Windows and download and burn another CD, then try again.

---

### Post by Quackers on 2010-11-30
Did you press a key to get to those options? I only get those options if I press F6
Try pressing esc from that screen

---

### Post by willie2000 on 2010-11-30
> **Rubi1200 said:**
> This an Ubuntu 10.04 CD; full version downloaded from the main site?

I would have thought the option to try would be there.
Yep. From the main site / alternative downloads as a bit torrent, as my first attempt didn't burn properly.

> **Rubi1200 said:**
> If you choose the option where does it take you; to a terminal?

The only thing is this; I have never seen that option :confused: 
(which means either I didn't look closely enough or never needed to use it!?!)

I can't recall now what it did, but I was looking for a terminal and don't remember finding that option. I think it checked settings etc. I'll have another look later. 

I don't remember seeing it before either.

> **Rubi1200 said:**
> It might be better to boot into Windows and download and burn another CD, then try again.
Despite this complete breakdown I'm still thinking of completely removing windows and installing just ubuntu so I need to do that anyway (my only reason for hanging on to windows is itunes - I know there are alternatives, but I'm not convinced...)

This complete conversion is something I need to look into... for example, do I need a sacrificial goat?

---

### Post by willie2000 on 2010-11-30
> **Quackers said:**
> Did you press a key to get to those options? I only get those options if I press F6
Try pressing esc from that screen

No, I didn't press F6 for those options --but I think I  had to when I first tried the disk.

I'll try esc. later, as well.

Thanks

---

### Post by willie2000 on 2010-11-30
Right. The rescue broken system option takes you into the installation process. Last time (and just now) I picked the 'abort installation' option on the first list --languages. 

Hitting esc takes me to a blank screen with

> boot:                       Enter takes me to a less pretty version of the aforementioned menu

Install 
Check disk
Test memory
Boot from hard disk
rescue broken system

... note no 'Try' option.

---

### Post by sikander3786 on 2010-11-30
Hi. I am jumping in here :-)

I doubt if it is an Ubuntu disc as do Rubi and Quackers.

Pop in your disc and browse it on Windows. Navigate to Dists > Lucid/Maverick > Release.txt and see what does that contain. If that file is there, it surely is Ubuntu :D

---

### Post by willie2000 on 2010-11-30
There is no file ending in '.txt', but there are two Release files:
 
Release.gpg   -- which I can't open, no program...
 
and Release   -- which reads
 
>  
Origin: Ubuntu
Label: Ubuntu
Suite: lucid
Version: 10.04
Codename: lucid
Date: Thu, 29 Apr 2010 17:24:55 UTC
Architectures: i386
Components: main restricted
Description: Ubuntu Lucid 10.04
MD5Sum:
4a4dd3598707603b3f76a2378a4504aa 20 restricted/debian-installer/binary-i386/Packages.gz
d41d8cd98f00b204e9800998ecf8427e 0 restricted/debian-installer/binary-i386/Packages
4a4dd3598707603b3f76a2378a4504aa 20 restricted/binary-i386/Packages.gz
59773390a87a4cc9fbbb5ac926c4d210 100 restricted/binary-i386/Release
d41d8cd98f00b204e9800998ecf8427e 0 restricted/binary-i386/Packages
8b1556a56af153b7aefc2971f3235e89 34840 main/debian-installer/binary-i386/Packages.gz
7ba05a182cbcedfaeba073fa9f46e1c7 139715 main/debian-installer/binary-i386/Packages
192aae75fe127a6984c9b99448cbe726 476591 main/binary-i386/Packages.gz
02ee6eaffeb82c5a0051d495243c0165 94 main/binary-i386/Release
7ed7b34e2010a67375defc244d378835 1841486 main/binary-i386/Packages
SHA1:
a0fddd5458378c1bf3c10dd2f5c060d1347741ed 20 restricted/debian-installer/binary-i386/Packages.gz
da39a3ee5e6b4b0d3255bfef95601890afd80709 0 restricted/debian-installer/binary-i386/Packages
a0fddd5458378c1bf3c10dd2f5c060d1347741ed 20 restricted/binary-i386/Packages.gz
4396ba67a008e2a06964f1507e92cbfc8884aa12 100 restricted/binary-i386/Release
da39a3ee5e6b4b0d3255bfef95601890afd80709 0 restricted/binary-i386/Packages
60009db45dc9c552db8dcb0fb9778fa1a1038eeb 34840 main/debian-installer/binary-i386/Packages.gz
a97886ea35856f91f22e699cd873e61a05ed294d 139715 main/debian-installer/binary-i386/Packages
98f3e5a550644e03843d0a0075e248afde98af56 476591 main/binary-i386/Packages.gz
69f0fdfed70fe61502e551f135248d8629885b89 94 main/binary-i386/Release
65f94a2bba6dc7f230d09e31f0c87f150b3d7acb 1841486 main/binary-i386/Packages
SHA256:
f61f27bd17de546264aa58f40f3aafaac7021e0ef69c17f6b1b4cd7664a037ec 20 restricted/debian-installer/binary-i386/Packages.gz
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 restricted/debian-installer/binary-i386/Packages
f61f27bd17de546264aa58f40f3aafaac7021e0ef69c17f6b1b4cd7664a037ec 20 restricted/binary-i386/Packages.gz
26c6c737ad3b145710b745b918b661189e292732c2180e9e0eeee96683d8614f 100 restricted/binary-i386/Release
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 0 restricted/binary-i386/Packages
1dccd1bce400da08039c3c2fce803870829951ab86979defe693b7d6a71d8a39 34840 main/debian-installer/binary-i386/Packages.gz
5aaac4b1f473a38b30cb2153f8ef9273711b580b541ebb5c5706829ad93a82aa 139715 main/debian-installer/binary-i386/Packages
629c8f3cbd18bfce3c8831c5d3eac3a56cc4e12a565952cf080696bf8838a4c9 476591 main/binary-i386/Packages.gz
095f73f9d2fbbc1c1a84426708978959610be17282420ae96f426deb26d54009 94 main/binary-i386/Release
f0890f9f5c2c81b360713f97340e8fab460665b9722ccc05f3aac73da20b55b8 1841486 main/binary-i386/Packages

 
Is that right.

---

### Post by sikander3786 on 2010-11-30
So that surely is Ubutnu disc. Then where did that "rescue broken system" option come from :confused:

Anyhow the issue here is not that option, the issue is to try to recover your Ubuntu install.

What happens if you select the Install option? When on the desktop it might give you an option page with Try or Install option? (That is available on a USB startup disc but... I have no clues).

Or if you select to install and then close the installer at any stage before installation is started, it should automatically drop to a Live Session. Does it?

---

### Post by willie2000 on 2010-11-30
The install option took me into the install process: Select language, etc...
 
I backed out from there as I'm just trying to boot an already installed OS, and worried going further would lose files. 
 
Yes, it drops the live session, but just reboots to the same menu or, if I eject the disk, to the same error.

---

### Post by sikander3786 on 2010-11-30
> **willie2000 said:**
> The install option took me into the install process: Select language, etc...
 
I backed out from there as I'm just trying to boot an already installed OS, and worried going further would lose files. 
 
Yes, it drops the live session, but just reboots to the same menu or, if I eject the disk, to the same error.
Hmmm.

I just noticed that there are quite a few differences between your's and mine Lucid 32-bit disc. MD5SUMS don't match, see yourself.

Your Release file,

```
Origin: Ubuntu
Label: Ubuntu
Suite: lucid
Version: 10.04
Codename: lucid
Date: Thu, 29 Apr 2010 17:24:55 UTC
Architectures: i386
Components: main restricted
Description: Ubuntu Lucid 10.04
MD5Sum:
4a4dd3598707603b3f76a2378a4504aa 20 restricted/debian-installer/binary-i386/Packages.gz
d41d8cd98f00b204e9800998ecf8427e 0 restricted/debian-installer/binary-i386/Packages
4a4dd3598707603b3f76a2378a4504aa 20 restricted/binary-i386/Packages.gz
59773390a87a4cc9fbbb5ac926c4d210 100 restricted/binary-i386/Release
d41d8cd98f00b204e9800998ecf8427e 0 restricted/binary-i386/Packages
8b1556a56af153b7aefc2971f3235e89 34840 main/debian-installer/binary-i386/Packages.gz
7ba05a182cbcedfaeba073fa9f46e1c7 139715 main/debian-installer/binary-i386/Packages
192aae75fe127a6984c9b99448cbe726 476591 main/binary-i386/Packages.gz
02ee6eaffeb82c5a0051d495243c0165 94 main/binary-i386/Release
7ed7b34e2010a67375defc244d378835 1841486 main/binary-i386/Packages
SHA1:
a0fddd5458378c1bf3c10dd2f5c060d1347741ed 20 restricted/debian-installer/binary-i386/Packages.gz
da39a3ee5e6b4b0d3255bfef95601890afd80709 0 restricted/debian-installer/binary-i386/Packages
a0fddd5458378c1bf3c10dd2f5c060d1347741ed 20 restricted/binary-i386/Packages.gz
4396ba67a008e2a06964f1507e92cbfc8884aa12 100 restricted/binary-i386/Release
da39a3ee5e6b4b0d3255bfef95601890afd80709 0 restricted/binary-i386/Packages
60009db45dc9c552db8dcb0fb9778fa1a1038eeb 34840 main/debian-installer/binary-i386/Packages.gz
a97886ea35856f91f22e699cd873e61a05ed294d 139715 main/debian-installer/binary-i386/Packages
98f3e5a550644e03843d0a0075e248afde98af56 476591 main/binary-i386/Packages.gz
69f0fdfed70fe61502e551f135248d8629885b89 94 main/binary-i386/Release
65f94a2bba6dc7f230d09e31f0c87f150b3d7acb 1841486 main/binary-i386/Packages
SHA256:
f61f27bd17de546264aa58f40f3aafaac7021e0ef69c17f6b1 b4cd7664a037ec 20 restricted/debian-installer/binary-i386/Packages.gz
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca4 95991b7852b855 0 restricted/debian-installer/binary-i386/Packages
f61f27bd17de546264aa58f40f3aafaac7021e0ef69c17f6b1 b4cd7664a037ec 20 restricted/binary-i386/Packages.gz
26c6c737ad3b145710b745b918b661189e292732c2180e9e0e eee96683d8614f 100 restricted/binary-i386/Release
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca4 95991b7852b855 0 restricted/binary-i386/Packages
1dccd1bce400da08039c3c2fce803870829951ab86979defe6 93b7d6a71d8a39 34840 main/debian-installer/binary-i386/Packages.gz
5aaac4b1f473a38b30cb2153f8ef9273711b580b541ebb5c57 06829ad93a82aa 139715 main/debian-installer/binary-i386/Packages
629c8f3cbd18bfce3c8831c5d3eac3a56cc4e12a565952cf08 0696bf8838a4c9 476591 main/binary-i386/Packages.gz
095f73f9d2fbbc1c1a84426708978959610be17282420ae96f 426deb26d54009 94 main/binary-i386/Release
f0890f9f5c2c81b360713f97340e8fab460665b9722ccc05f3 aac73da20b55b8 1841486 main/binary-i386/Packages 
```

My Release file,

```
Origin: Ubuntu
Label: Ubuntu
Suite: lucid
Version: 10.04
Codename: lucid
Date: Thu, 29 Apr 2010 10:54:37 UTC
Architectures: i386
Components: main restricted
Description: Ubuntu Lucid 10.04
MD5Sum:
 a5a788ebc3d91f9714b27643f006ba66     1270 restricted/binary-i386/Packages.gz
 59773390a87a4cc9fbbb5ac926c4d210      100 restricted/binary-i386/Release
 692f27010740e5f75acc519535cab5f0     2512 restricted/binary-i386/Packages
 36b85df6c0b1f2501428a6adc4606cd9     9379 main/binary-i386/Packages.gz
 02ee6eaffeb82c5a0051d495243c0165       94 main/binary-i386/Release
 9232c5cf44a999a3f48f3f63d172211f    28781 main/binary-i386/Packages
SHA1:
 f54be4d63936a84a124b74ca00fc913b72d8e9b2     1270 restricted/binary-i386/Packages.gz
 4396ba67a008e2a06964f1507e92cbfc8884aa12      100 restricted/binary-i386/Release
 8a01693332fa6c539c395c165a962e0d7a28c3af     2512 restricted/binary-i386/Packages
 873eed11cb62ad19eade383e38170c9404e157bf     9379 main/binary-i386/Packages.gz
 69f0fdfed70fe61502e551f135248d8629885b89       94 main/binary-i386/Release
 1167660675e02170d287826a2c5e4db3d33ecc43    28781 main/binary-i386/Packages
SHA256:
 ce5bd818a6a9caf264c35d23fb9640a39749d10301f5d1354d1991c1b215cd61     1270 restricted/binary-i386/Packages.gz
 26c6c737ad3b145710b745b918b661189e292732c2180e9e0eeee96683d8614f      100 restricted/binary-i386/Release
 db0cecb19ba1847803dd097764fe9ddd97b299e0f31ca87cb5144e5260cc45d4     2512 restricted/binary-i386/Packages
 d0bb5785f79bd6a9c6c1b8c3e962cfb892010c22598ec5d44238176d1a4fabde     9379 main/binary-i386/Packages.gz
 095f73f9d2fbbc1c1a84426708978959610be17282420ae96f426deb26d54009       94 main/binary-i386/Release
 935dc6481891f58237088f7ebff379f5b84b8558750b31e4ceb4a10f0047514b    28781 main/binary-i386/Packages
```

But if the MD5SUMs were not correct, the disc shouldn't have booted successfully either :confused:

Regardless of that, check the MD5SUM of the image you downloaded.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If thats ok, try burning a new disc at the lowest speed possible (I prefer 4x) and try booting again.

Alternatively if you've got a USB drive and your computer is capable of booting from that, you can use that as well.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by willie2000 on 2010-12-01
Good morning / afternoon / evening [delete as appropriate]

I've burnt a new disk, which gives me the 'Try' option. I've followed the instructions [here]("http://ubuntuforums.org/showpost.php?p=10159040&postcount=5")...up  to the "Delete all lines up to (not including) the first line that starts with "menuentry"" section...

But have a (probably silly) question:

Does 'up to' mean delete everything from the start of the text to the first 'menuentry'? Or delete everything from the end of the text to the first 'menuentry' you come to, or the first 'menuentry' reading from the top down?

:roll:

---

### Post by Rubi1200 on 2010-12-01
It means you need to delete all entries from the beginning of the file up until you reach the first "menuentry." Do not delete the first menuentry or anything after it.
Then, continue with any instructions and you should be able to get back into Ubuntu.

Let us know what happens please.

---

### Post by willie2000 on 2010-12-01
Success!

Thanks for sticking at it, guys. 

So is this this a permanent fix?

Is this another reason to do away with my dual boot set-up and make it a linux only machine?

Thanks again.

---

### Post by Rubi1200 on 2010-12-01
You are more than welcome :)

> So is this this a permanent fix?
Not really; see here for more discussions about this:
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

