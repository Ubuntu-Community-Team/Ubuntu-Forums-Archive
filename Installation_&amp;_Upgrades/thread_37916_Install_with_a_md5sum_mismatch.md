---
title: "Install with a md5sum mismatch?"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by saintsel on 2005-05-29
Hi,

I'm thinking of install Ubuntu to make a dual-boot with XP. I downloaded ubuntu-5.04-install-i386.iso and got the md5sum correct. But after burning the image to a CD (tried it twice at low burning speeds) the md5sum is wrong compared to the md5sum.txt on the image. I even tried to check the md5sum before burning, with mounting the iso-file in Deamon tools, and got the same md5sum mismatch. So it seems like that the burning process isn't the problem. It's one file that has the wrong md5um, and two files I can't access:

"NOT FOUND    *****        ./install/netboot/pxelinux.cfg/default
FAILED       MD5          ./install/netboot/pxelinux.0
NOT FOUND    *****        ./pool/main/m/mozilla-firefox-locale-all/mozilla-firef
ox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb

1 checksums failed
2 file errors".

Anybody knows what the problem is? Shold I continue the install, or is this a big risk?

---

### Post by stevenyu on 2005-05-29
never burn or install a linux distro with a MD5 checksum error, I would suggest you to use [jigdo]("http://atterer.net/jigdo/#download") to repair it

---

### Post by saintsel on 2005-05-29
Ok, thanks for the tip. I'll try jigdo, but seems like their server is down at the moment, so guess I'll have wait a bit.

---

### Post by saintsel on 2005-05-29
After using jigdo I found out that the image I had was OK. Weird though, beacuse I've downloaded 3 different images (ftp and torrent), and they all gave me the same error when inspecting the checksum for each file. I've also tried two different checksum programs.

Difficult to say what's wrong. My first thought was that the md5sum.txt on the image was wrong, but since no one else has noticed this that's probably not it. Anyway, I'll try install with the image jigdo said was OK.

---

### Post by Scoodaddy on 2005-06-05
There's definitely something strange going on:  Under WinXP Pro I downloaded the i386 install ISO and checked its md5sum and it was fine.  Then I burned it to CD under WinXP and ran a check of all the individual files using the md5sum.txt file on the install CD and got the *exact same* error message you did, involving the same 3 files.  I used a couple of different Windows md5 programs, and always had the same problems with those same 3 files.  So I made a new ISO image file from the install CD I'd burned, and compared it to the original ISO, and the ISO files matched exactly.

Then things get weirder:  under Linux (RedHat 9) I again checked md5sum.txt file (md5sum -c md5sum.txt) and those 3 files were fine!  However, I got an error regarding a *different* file:

  md5sum: ./pool/main/t/tcl8.4/tcl8.4_8.4.7-1ubuntu1_i386.deb: Input/output error
  ./pool/main/t/tcl8.4/tcl8.4_8.4.7-1ubuntu1_i386.deb: FAILED open or read

So I ran the *exact same command* a second time, and this time the above file reported "OK" but yet *another* file gave me an I/O error:

  md5sum: ./pool/main/t/tiff/libtiff4_3.6.1-5_i386.deb: Input/output error
  ./pool/main/t/tiff/libtiff4_3.6.1-5_i386.deb: FAILED open or read

So I copied  the lines from md5sum.txt for the above 2 files to a new text file and ran an md5 check against it several times, and it consistently reported that the 2 files were OK.

So there's something consistently inconsistent about checking the md5 sums under Windows, and something inconsistently inconsistent about checking them off the CD under Linux.

I'm now going to go ahead and install using the CD I burned, and see what happens.

BTW I'm a relative Linux newbie so if anyone can shed any light on the above weirdness I'd appreciate it!

---

### Post by beebelo on 2005-08-15
I wish I'd seen this thread earlier (I was looking in kubuntu forums and posted over there).   

I've been having the exact same problem with my kubuntu iso download -- the exact same files:  pxelinux.cfg, pxelinux.0, and the mozilla file.  As with you, the iso checked fine, but the md5s in the text file stored in the image did not pass the test.  

Saintsel and Scoodaddy, how did you come out with this issue???

---

### Post by bugmenot on 2005-08-15
Saw this thread too late, here's the same problem explained: [http://ubuntuforums.org/showthread.php?t=19228&highlight=pxelinux.0](http://ubuntuforums.org/showthread.php?t=19228&highlight=pxelinux.0)

---

