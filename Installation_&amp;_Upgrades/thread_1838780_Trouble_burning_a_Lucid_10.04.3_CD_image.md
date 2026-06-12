---
title: "Trouble burning a Lucid 10.04.3 CD image"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by mdlueck on 2011-09-04
I am having some unknown trouble successfully burning a Lucid 10.04.3 i386 Desktop CD image.

I recently updated my CD image to the .3 revision, and attempting an installation ended with an error message that one package checksum did not match.

So I did the following steps:

1) Found the checksum for the file here: [http://mirrors.cs.wmich.edu/ubuntu-releases/lucid/MD5SUMS](http://mirrors.cs.wmich.edu/ubuntu-releases/lucid/MD5SUMS)

f63028da38308d917cd1460e14fb8540 *ubuntu-10.04.3-desktop-i386.iso

2) Verified my download of said file:

~/ISO$ md5sum ubuntu-10.04.3-desktop-i386.iso 
f63028da38308d917cd1460e14fb8540  ubuntu-10.04.3-desktop-i386.iso

3) Checked the box to verify CD created in K3b:

FAIL!

4) Checked the actual CD burned:

$ sudo umount /media/cdrom0
$ md5sum /dev/sr0
f63028da38308d917cd1460e14fb8540  /dev/sr0

Where oh where might the problem be?

Back to installing from my 10.04.1 CD for now I guess.

---

### Post by mörgæs on 2011-09-05
First of all: If you can install using 10.04.1, why do you bother burning another CD?

---

### Post by mdlueck on 2011-09-05
> why do you bother burning another CD?

Fine, forget the fact "I have a 10.04.1 CD burned and it works properly." :-|

"I burned a copy of 10.04.3 and have an installation error. I ran the self-check of the CD and it shows one file in error. However the burned CD image, and the .iso file, all have matching checksums with the checksum file on the server. Please explain where the problem is."

Installing from a newer version:

1) Verifies that the newer version still installs properly... (obviously that is not true)
2) Eliminates the need to do so much updating when the installation completes.

(head shaking)

<><><>

I suspect if indeed that is the correct checksum for the CD image, then the CD image was built with one package/file with an invalid checksum.

---

### Post by mdlueck on 2011-09-30
The solution was to download the full ISO image and not use Jigdo to update from the previous ISO image.

---

