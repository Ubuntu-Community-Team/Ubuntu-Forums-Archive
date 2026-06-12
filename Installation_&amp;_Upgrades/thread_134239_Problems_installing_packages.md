---
title: "Problems installing packages"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by Connollyir on 2006-02-21
I recently installed Ubuntu on my machine again (didn't like the 64 edition) and I can't seem to download some of the packages I want. The error output looks like this:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2_1.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2_1.4.3-0ubuntu1_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/artsbuilder_3.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/artsbuilder_3.4.3-0ubuntu1_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/akode_3.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/akode_3.4.3-0ubuntu1_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkcal2a_3.4.3-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkcal2a_3.4.3-0ubuntu3_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkdepim1_3.4.3-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/libkdepim1_3.4.3-0ubuntu3_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/akregator_3.4.3-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/akregator_3.4.3-0ubuntu3_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdetoys/amor_3.4.3-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdetoys/amor_3.4.3-0ubuntu2_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/ark_3.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/ark_3.4.3-0ubuntu1_i386.deb)
  Size mismatch

........etc. You get the idea. If you need package names it was the "kde, kde-core", and "kubuntu-desktop" packages and their dependancies, with a few others thrown in (total is too numerous to list).

I have all repositories enabled. I thought it might have been a problem with backports, so I took it out so I could get the packages and worry about updating them later.... still have the problem. I thought it might have been that the servers were down, but that wouldn't explain the "Size mismatch" error would it?


Thanks

-Ian

---

### Post by heimo on 2006-02-21
There's something wrong in the repositories, not your system. This is fourth thread I see of this subject. Try again later.

---

### Post by Connollyir on 2006-02-21
[QUOTE=heimo]There's something wrong in the repositories, not your system. This is fourth thread I see of this subject. Try again later.[/QUOTE]

Awesome. Thanks.

-Ian

---

