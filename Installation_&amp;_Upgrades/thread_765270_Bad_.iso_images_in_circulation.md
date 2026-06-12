---
title: "Bad .iso images in circulation?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by bg1256 on 2008-04-24
Hi all,

I'm just curious if anyone else has run into corrupted .iso image files while trying to download and install Hardy.

I have tried two separate .iso files, and neither of them has worked. By that, I mean both burned successfully, and then both passed the integrity test after booting from the CD. However, both just give me a screen full of colored lines and not a desktop.

So, has anyone else encountered this? Does anyone know of a torrent I could download (and then seed) that is not corrupt?

---

### Post by bg1256 on 2008-04-24
Well, if anyone does read this, you can find some useful torrents here:

[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

It seems to me this must be the official site.

---

### Post by bcms on 2008-04-24
ubuntu-8.04-alternate-i386 doesn't seem to want to burn in my case. It will get about half-way through the process before saying something useful like "unknown error". Same result for that file from the .torrents and also from the overwhelmed mirrors this morning. I don't know what to think, but no worries.

---

### Post by animalk on 2008-04-24
I downloaded the desktop-i386 version from the ubuntu torrent and the download was speedy and uninterrupted. The image burned without a problem.
i get a an I/O warning while the livecd is loading up saying it couldn't find fd0. Regardless the live cd boots up correctly but the partition manager cannot see my hard drive or its partitions yet i can browse my hard disk through ubuntu "explorer".

I used winMd5Sum to test checksum and it came out completely off from what is posted on the ubuntu torrent site.

---

### Post by mrproza on 2008-04-24
Had no problems to burn ubuntu-8.04-alternate-i386.iso
md5check was OK.
But still not able to upgrade.

---

### Post by MonoMatt304 on 2008-04-24
ubuntu-8.04-desktop-i386.iso

When I load the LiveCD, it goes to "Loading Linux Kernel", then it freezes at 100% before saying "Cannot Read from CD" a few minutes later.

I think there's a bad batch floating around.

---

### Post by bg1256 on 2008-04-24
Well, I suppose it's bad news that  so many are having problems.

But, I suppose it's good news in that I'm not hte only one having the problem. Hopefully there will be some news released about it soon, somewhere.

---

### Post by ssam on 2008-04-24
run md5sum on the file. if it matches with the md5sums at [http://releases.ubuntu.com/hardy/MD5SUMS](http://releases.ubuntu.com/hardy/MD5SUMS) then there is 99.999999999999999% chance that there is nothing wrong with the file. you could try reburning at a lower speed, or using higher quality CD-Rs.

```

7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe
```

i dont know of a good way to MD5SUM a file without using a terminal, but is its faily easy.

open a terminal (Applications->Accessories->Terminal)
type 'md5sum' (without the quotes) followed by a space
drag the icon of the file from the file browser to the terminal
press enter
wait a minute for the result

---

### Post by jedimasterk on 2008-04-24
I'm getting a (initramfs)_ prompt after booting the 8.04 cd. Never had this issue with previous versions. I put Ubun tu 7.10 on last week after getting new SATA hard drive and all worked flawlessly.

---

### Post by ptcbus on 2008-04-24
I upgraded using bit-torrents. Had no problems.
(Have listed the steps in here: [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html") )

---

### Post by bg1256 on 2008-04-24
> **ssam said:**
> run md5sum on the file. if it matches with the md5sums at [http://releases.ubuntu.com/hardy/MD5SUMS](http://releases.ubuntu.com/hardy/MD5SUMS) then there is 99.999999999999999% chance that there is nothing wrong with the file. you could try reburning at a lower speed, or using higher quality CD-Rs.

```

7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe
```

i dont know of a good way to MD5SUM a file without using a terminal, but is its faily easy.

open a terminal (Applications->Accessories->Terminal)
type 'md5sum' (without the quotes) followed by a space
drag the icon of the file from the file browser to the terminal
press enter
wait a minute for the result
md5sumc confirms the image is correct. Very strange. I burned in a high quality cd r at x2. Very, very odd.

---

### Post by bg1256 on 2008-04-24
Problem solved. See my post here:

[http://ubuntuforums.org/showthread.php?p=4785388#post4785388](http://ubuntuforums.org/showthread.php?p=4785388#post4785388)

---

### Post by cafe con leche on 2008-04-24
jedi: you need to run using the alternate CD, and before you install, at the install menu hit f6 and add pci=nomsi to the end of the sentence at the bottom of your screen. 

IM me (SN: h4q) if you don't know what i'm talking about.

---

### Post by nroussi on 2008-05-13
I have downloaded ubuntu-8.04-server-i386.iso from 2 different locations and I burned the iso the first time with no problems but when I did a disk integrity check it said that the disk was corrupted. The second download, I mounted the iso image with "Disk Utility" on Mac OSX and selected "Verify Disk" but it gave me an error. Anyone has any ideas?

---

### Post by sean8080 on 2008-05-13
> **jedimasterk said:**
> I'm getting a (initramfs)_ prompt after booting the 8.04 cd. Never had this issue with previous versions. I put Ubun tu 7.10 on last week after getting new SATA hard drive and all worked flawlessly.

I am having the same problem of getting this (initramfs) and had tried on board and external graphic card as well. Both shown the same issue. How did you resolve it? please help...:confused:

---

