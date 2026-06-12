---
title: "md5sum always wrong"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by lexmiller on 2007-06-07
I have been trying to download ubuntu 7.04 desktop i386 but I have not succeeded in geting an iso with the correct md5sum.

I have downloaded from 4 different mirrors (using Firefox). Each time the md5sum is different (and not what is should be according to [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)). I then tried using wget with one of the 4 mirror that I had already tried. The md5sum was different yet again.

The file size is the same every time.

I did a fsck -f /dev/hda6 on the file system to which the ISOs were being saved, but it reported no errors.

Does anyone have any suggestions?

---

### Post by taurus on 2007-06-07
Try downloading it with bittorrent.

---

### Post by lexmiller on 2007-06-07
Thanks. I'm trying the bittorrent option now. I'll report back to let you know how it goes.

Any ideas what the cause of the problem might be, or what I might try in order to diagnose it?

---

### Post by taurus on 2007-06-07
If you can tell me where you downloaded it and the md5sum, perhaps I can check it out on my machine to see if I get the same corrupted file/download.

---

### Post by lexmiller on 2007-06-07
[lex@localhost ubuntu]$ ll
total 3587250
-rw-rw-r-- 1 lex lex 731797504 Jun  7 09:29 ubuntu-7.04-desktop-i386.iso.broken1.japan1
-rw-rw-r-- 1 lex lex 731797504 Jun  7 12:55 ubuntu-7.04-desktop-i386.iso.broken2.japan2
-rw-rw-r-- 1 lex lex 731797504 Jun  7 14:40 ubuntu-7.04-desktop-i386.iso.broken3.columbia
-rw-rw-r-- 1 lex lex 731797504 Jun  7 16:07 ubuntu-7.04-desktop-i386.iso.broken4.kernel
-rw-r--r-- 1 lex lex 731797504 Apr 15 22:52 ubuntu-7.04-desktop-i386.iso.broken5.wget.columbia
[lex@localhost ubuntu]$ md5sum *
9e69c18185e128109cdc6842967e4c31  ubuntu-7.04-desktop-i386.iso.broken1.japan1
2f50d41d0e0e1f52b59e1e5a9193f263  ubuntu-7.04-desktop-i386.iso.broken2.japan2
5c7ec0a18ea6c4e19ac77699d466eb75  ubuntu-7.04-desktop-i386.iso.broken3.columbia
f9b2455dcf7ecf349e65bf655b900b2c  ubuntu-7.04-desktop-i386.iso.broken4.kernel
8307d3794c5a8db1b874093742fb9af1  ubuntu-7.04-desktop-i386.iso.broken5.wget.columbia
[lex@localhost ubuntu]$

The 5 sites were:
[http://ftp.ecc.u-tokyo.ac.jp/UBUNTU-CDS/](http://ftp.ecc.u-tokyo.ac.jp/UBUNTU-CDS/) (using Firefox)
[http://ftp.yz.yamagata-u.ac.jp/pub/linux/ubuntu/releases/](http://ftp.yz.yamagata-u.ac.jp/pub/linux/ubuntu/releases/) (using Firefox)
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/) (using Firefox)
[http://mirrors.kernel.org/ubuntu-releases/](http://mirrors.kernel.org/ubuntu-releases/) (using Firefox)
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/) (using wget)

Note that the 2 downloads from columbia were different, leading me to believe that the problem was at my end.

---

### Post by taurus on 2007-06-07
> **lexmiller said:**
> [lex@localhost ubuntu]$ ll
total 3587250
-rw-rw-r-- 1 lex lex 731797504 Jun  7 09:29 [COLOR="Blue"]ubuntu-7.04-desktop-i386.iso.broken1.japan1[/COLOR]
-rw-rw-r-- 1 lex lex 731797504 Jun  7 12:55 [COLOR="Blue"]ubuntu-7.04-desktop-i386.iso.broken2.japan2[/COLOR]
-rw-rw-r-- 1 lex lex 731797504 Jun  7 14:40 [COLOR="Blue"]ubuntu-7.04-desktop-i386.iso.broken3.columbia[/COLOR]
-rw-rw-r-- 1 lex lex 731797504 Jun  7 16:07 [COLOR="Blue"]ubuntu-7.04-desktop-i386.iso.broken4.kernel[/COLOR]
-rw-r--r-- 1 lex lex 731797504 Apr 15 22:52 [COLOR="Blue"]ubuntu-7.04-desktop-i386.iso.broken5.wget.columbia[/COLOR]


Those are the actual files that you saved to your machine!

---

### Post by lexmiller on 2007-06-07
I renamed the .iso files after doing the md5sum so that I remembered where I got them from, and so that they wouldn't be clobbered when I tried downloading another.

The bittorrent download has finished now, and the md5sum for that .iso is correct.

That's great - Thanks. But I wonderwhat is causing the http downloads to become corrupt.

---

### Post by cjax1 on 2007-06-16
Hi,

I have noticed the same problem several times in the past using Ubuntu. I just downloaded an ISO last night using Ubuntu and sure enough it's no good. I don't use bittorrent. It's no faster anyhow and since I used to use Windows I learned to never use P2P software. I know, maybe it's OK in Ubuntu but still. With my luck it'll fail and I'll have just wasted another 3+ hours downloading a no good ISO.

Until someone figures out why all the ISO's are getting corrupted I will continue to use Windows to download the ISO's. Out of all the ISO's I ever downloaded in Windows only one was corrupted and I found out it was the website's fault anyway.

I do wish someone would figure out what the problem is.

---

### Post by trak87 on 2007-06-16
cjax1, 

The advice to use bittorrent is a good one. Bittorrent does checksums throughout the downloading process. I've always ended up with matching md5sums using BT.

---

### Post by cjax1 on 2007-06-16
OK trak87 I'll try it next time. Actually I'll probably download one tonight using BT. I'll post back and let you know how it worked.

Thanks.

---

### Post by Pumalite on 2007-06-16
> **cjax1 said:**
> OK trak87 I'll try it next time. Actually I'll probably download one tonight using BT. I'll post back and let you know how it worked.

Thanks.

It's not the original file that is the problem. It's the mode of transmission; HTTP and FTP are inferior to a torrent in that respect.

---

### Post by cjax1 on 2007-06-16
OK I have bittorrent installed along with the GUI. I probably don't need the GUI but I can't get it working. I have the exact same problem as in the post [here]("http://ubuntuforums.org/showthread.php?t=462732&highlight=how+to+bittorrent")

but no one has came up with an answer. I need to get this working tonight or I have to use Windows again. I don't want to.

Thanks

---

### Post by trak87 on 2007-06-16
I don't know if I understand the problem exactly... but the default bittorrent that comes with Ubuntu is very basic. I don't think there is much of a GUI at all -- and there's not much you can do with them except start a download -- but if you just need to get an Ubuntu distribution ISO, use it: download Feisty, check the md5sum and install Ubuntu. After you get 7.04 going you can install one of the better GUI Bittorrent clients like Azureus. Azureus and other bittorrent clients utilize the bittorrent protocol -- they have just packaged their particular implementation of it differently. Some prefer certain clients over others. But yeah, the default BT client is BASIC!

---

### Post by cjax1 on 2007-06-16
OK I finally figured it out. And I was just getting ready to install Azureus or ktorrent. It would have helped to have an explanation when I started Bittorrent from the Applications menu. You know, something like "Not this way you stupid idiot, go to a website first and download the blahblahblah.iso.torrent file first *THEN* open Bittorrent and find the blahblahblah.iso.torrent file you just downloaded *THEN* you can start the download. Can't you read our minds or pickup on the brain signals with the instructions we're sending you? DUH".

OK, the Bittorrent that came with Ubuntu may be basic but it's working. I'll probably try out the others some other time.

Anyway thanks for the help. I'm downloading the Kubuntu alternate CD now. I'll let you know how it turns out with the MD5sum.

---

### Post by cjax1 on 2007-06-17
OK I just finished downloading ubuntu-7.04-alternate-i386.iso but now I cannot find the md5sum on the site anywhere. I did a search for it too and it came up with nothing. The sum I get in terminal is ff0cc7c9ed5157f0ff8c0f2213973f49. But I have no way of knowing if it is correct. I don't have time for this. It's early in the morning and I need to sleep :-)

Besides I thought I was downloading the Kubuntu alternative CD not the Ubuntu alternative CD. Or is there one? I was following the links for Kubuntu.

I'll just burn the d*** thing in the morning and see if it works.

I hope no one thinks I was trying to hijack this thread. It looked like lexmiller had already solved his problem but still the question remains. What could be corrupting the downloads using http in Ubuntu? In Windows (hate that word anymore) http seemed quite reliable. Could it be FireFox's built in download manager?

---

### Post by trak87 on 2007-06-17
Go here to get the MD5SUMS file:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

Select a mirror site, go into the 7.04 directory and look towards the bottom of the page where the filenames are listed.

---

### Post by cjax1 on 2007-06-17
Thank you very very much trak87. I found the sum and it matches. Bittorrent worked good. I already burned the iso and am loading it now.

Thanks again :-)

---

### Post by mastergandalf19 on 2007-06-18
This has been a problem for me too. Not only are the http downloads corrupted, but bittorrent downloads are corrupted also. I downloaded all of the ISO versions 4 times thru http AND Bt and they all still dont match the md5 sums on the website (this is where i started to bang my head against a wall). Ok fine, so i burned them ALL, and none of them work, they get to the "install ubuntu studio" screen, and then a stack trace/overflow error pops up at the bottom with lots of complicated, un-user friendly numbers, with the key flashing in the top right hand corner. Either there is a serious issue with their bandwith/parity in the actual connections or downloading it in the UK has some massive problem. Ive ruled out bad burning (burnt at x16, x8,x4,x2,and even x1, on a MAC and a PC, using Infra Recorder and the MAC burning software.) Ive ruled out my dvd rw drive because it plays dvds, cds and svcds fine, I checked the cables, the jumpers and even updated the drivers, tried the installs again, and then rolled back and did it all over with no joy. I have even gone to the length of saving the ISO to a flash disk and then trying to boot from it, also with no joy. I just dont understand how 20 odd downloads can all be corrupt. They were done on a college campus line (which is around T3 speeds), ive done it on conventional UK cable and wireless, and theyre all corrupt. Can some one, preferably a moderator or someone with VAST ubuntu experience help me please, I need this install to get at ardour2, as my course requires that I have it ready to use at home.

I appreciate any suggestions comments or solutions
mail me: [email]mastergandalf19@hotmail.com[/email]

cheers matt.:(

---

### Post by mastergandalf19 on 2007-06-18
system specifications: Pentium 4 2.8GHZ, NVidia Geforce FX5200 (old drivers, new ones suck...a lot.), 120GB samsung HDD, DVD RW Drive, 512mb DDR 400 ram, Alesis Multimix 12 Firewire Mixing Desk. Windows XP pro 60gb partition, 60gb free for ubuntu studio. 

P.S, Please do not tell me to install ubuntu 7.04 then upgrade to studio. I havent really got time. Thanks

---

