---
title: "This is not funny"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by Krogen on 2005-06-11
Nothing's wrong with my computer. Nothing is wrong with my DSL line.

I tried downloading Ubuntu 5.04 i386 three-four times today (and twice yesterday) and I keep getting my iso corrupted. I tried downloading from Azureus Bittorent and directly from one of the official Ubuntu servers. ALL got corrupted. What exactly? The firefox package (in all the cases) and one or more of the python packages. Amazing.

If people are seeding a corrupted copy, everyone who is downloading has one. Not funny.

Or am I going crazy?

---

### Post by SGC on 2005-06-11
How do you know it is corrupted?, is the md5 check doesn't match?

I didn't understood what  firefox and paython has to do with the corrupted iso. could you clearify this?

---

### Post by Krogen on 2005-06-11
[QUOTE=SGC]How do you know it is corrupted?, is the md5 check doesn't match?

I didn't understood what  firefox and paython has to do with the corrupted iso. could you clearify this?[/QUOTE]

Yes, I checkedsumed the iso and it was corrupted. I extracted the iso and checked the contents with the included checksum file and got those packages corrupted. (they did not match...)

---

### Post by Krogen on 2005-06-11
Just to make sure, I downloaded BitComet and opened the torrent and rechecked the iso. 100% done.

The iso checksum returned an error. The whole cd checksum (file on the cd) returned 8 errors.

Just some proof...  ;-) 

[[IMG]http://img51.echo.cx/img51/156/proof18sq.th.jpg[/IMG]](http://img51.echo.cx/my.php?image=proof18sq.jpg)
[[IMG]http://img203.echo.cx/img203/5525/proof25gb.th.jpg[/IMG]](http://img203.echo.cx/my.php?image=proof25gb.jpg)

---

### Post by SGC on 2005-06-11
Why are you checksuming all the files inside the iso, just do it for the iso, if it match then it is not corrupted

Here is the checksum for ubuntu 5.04, compare it with the one you have:

f6b3f164c99761234858a4d2c12d0840    
ubuntu-5.04-install-i386.iso

765dc370887735af71bc2cf6fcc9fafd       
ubuntu-5.04-dvd-i386.iso

77a1a8be45e0cc93a14c9b9bf00f6648   
ubuntu-5.04-live-i386.iso

---

### Post by Krogen on 2005-06-12
[QUOTE=SGC]Why are you checksuming all the files inside the iso, just do it for the iso, if it match then it is not corrupted

Here is the checksum for ubuntu 5.04, compare it with the one you have:

f6b3f164c99761234858a4d2c12d0840    
ubuntu-5.04-install-i386.iso

765dc370887735af71bc2cf6fcc9fafd       
ubuntu-5.04-dvd-i386.iso

77a1a8be45e0cc93a14c9b9bf00f6648   
ubuntu-5.04-live-i386.iso[/QUOTE]


> f6b3f164c99761234858a4d2c12d0840
ubuntu-5.04-install-i386.iso

I did, got an error.

---

### Post by anish on 2005-06-12
Did you try downloading it from different sources?

It looks like only some packages are corrupted. Why not burn the CD anyway and do an update to replace those packages?

If all else fails, order the CD  :grin:

---

### Post by Krogen on 2005-06-12
[QUOTE=anish]Did you try downloading it from different sources?

It looks like only some packages are corrupted. Why not burn the CD anyway and do an update to replace those packages?

If all else fails, order the CD  :grin:[/QUOTE]


I tried installing it from the cd, all went well but after reboot (when it was extracting the packages) it gave me an error and prompted me to put in the cd. I did so and a new download-update-install screen came up. I selected all packages and downloaded them.... Unfortunetely, something went wrong and it kept giving me A LOT of errors. 

I just downloaded Bit Comet (a Bittorrent client) and I opened the downloaded torrent, it fixed the iso. I force rechecked the downloaded iso, fine. 

Now, when I check it with md5summer.exe, it gives me an error. If I check it with md5sum.exe, it says it's fine. If I extract the iso (with WinRAR) and check it with md5summer.exe, it says it found 8 errors. I checked it with md5sum.exe, it couldn't read two files and found errors in one.

I won't order the cd... I'm not that desparate... Yet :)

---

### Post by alt4 on 2005-06-13
[QUOTE=anish]
If all else fails, order the CD  :grin:[/QUOTE]

I've ordered and received a bunch of Ubuntu CD's via Shipit, but I'm not sure if they are ok. I checked every CD creating the ISO of it and then calculating it's MD5. All MD5 checksums were equal, but they didn't match the one listed in [http://releases.ubuntu.com/hoary/MD5SUMS](http://releases.ubuntu.com/hoary/MD5SUMS). Actually the resulting ISO was about 300 kbytes bigger than the one listed in download section (I created standard ISO's both under Windows and Linux with the same result). Nevertheless when running self-check from the CD's it says "the CD-ROM is valid". Has anybody come across a similar problem?

---

### Post by frühstück on 2005-06-13
well, bittorrent is doing the checksum tests automaticly, but bitcomet is known to be garbage, maybe you should use a real bittorrent client.

---

### Post by kvidell on 2005-06-13
I wonder how this little problem with the standard ubuntu repo mirrors is going to affect new users doing the netinstall... That could be part of his problem when trying to do the updates after installing from the bunk CD...

You could always try just downloading a straight copy off of the Ubuntu website. That's what mine all are..
- Kev

---

