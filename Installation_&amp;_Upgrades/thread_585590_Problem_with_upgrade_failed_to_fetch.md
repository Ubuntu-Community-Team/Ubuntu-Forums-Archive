---
title: "Problem with upgrade: failed to fetch"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Melbridge on 2007-10-21
Using Update Manager it goes through the first part, downloads some files then  comes up with the following error:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

Any help would be appreciated - please keep it simple - I'm not what you'd call a Linux expert!!

Thanks,  Dean.

---

### Post by Tosa on 2007-10-21
Hah, neither am I...

But the same thing happend to me an hour ago. I went to medibuntu site (medibuntu.org) and used their links for repositories that seems to work.

HTH

---

### Post by pushkaraj on 2007-10-21
This is the problem I am getting - and I think it is similar to the one quoted earlier in this thread - the message I get during the upgradation is

 Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dapper/dists/universe/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dapper/dists/universe/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dapper/dists/universe/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dapper/dists/universe/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dapper/dists/dists/universe/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dapper/dists/dists/universe/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/dists/mjpegtools/.//binary-i386/Packages.gz](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/dists/mjpegtools/.//binary-i386/Packages.gz) 404 Not Found

Please help,Thanks
Pushkaraj

---

### Post by Melbridge on 2007-10-21
Does that do a normal upgrade? ie Ubuntu gnome desktop?

thanks,  Dean

---

### Post by Tosa on 2007-10-21
Sorry, but is your question addressed to me or to previous poster?

---

### Post by pushkaraj on 2007-10-21
I am sorry to have not clarified. The question IS addressed to you because I thought you had a solution to the first query and hence would have one to mine too.
So, how do I overcome this problem?
Thanks,
Pushkaraj

---

### Post by Melbridge on 2007-10-21
Sorry Tosa, yes you, didn't realize someone else had posted in between.

---

### Post by Melbridge on 2007-10-21
This is getting complicated !!!

---

### Post by pushkaraj on 2007-10-21
Hey Melbridge,
I think you and I are both addressing Tosa.
Tosa, can you help me out of this?
Thanks,
Pushkaraj

---

### Post by JTux on 2007-10-21
> **Melbridge said:**
> Using Update Manager it goes through the first part, downloads some files then  comes up with the following error:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibunt u.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibunt u.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

Any help would be appreciated - please keep it simple - I'm not what you'd call a Linux expert!!

Thanks,  Dean.

Try disabling the medibuntu repositories in Synaptic.

1. System> Administration>Synaptic package Manager 
2. Enter the administrator password when prompted.
3. Settings>Repositories>Third-Party Software.
4. Untick all the medibuntu repositories. 

Hope this helps

---

### Post by Tosa on 2007-10-21
Sorry for the mess guys, **I** should have specified whom I was addressing in the first place...

Anyway, I had exactly the same issue as **Melbridge;** I browsed the Medibuntu site and I've taken URLs they posted there and put them in repository list, and after that the update of codecs etc, went fine.

@ Pushkaraj
I'm sorry, but all I can figure out is that files you're trying to get doesn't exist. I'm most probably wrong, but could you check the spelling? In my repository list *universe* and *multiverse *are separated from the rest of the address with spaces, not slashes.

---

### Post by BnetTheAwesome on 2007-10-21
I had a similar error message:

"A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://download.tuxfamily.org/3v1deb...86/Packages.gz](http://download.tuxfamily.org/3v1deb...86/Packages.gz) 404 Not Found
Failed to fetch [http://download.tuxfamily.org/3v1deb...rce/Sources.gz](http://download.tuxfamily.org/3v1deb...rce/Sources.gz) 404 Not Found
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/di...6/Packages.bz2](http://hendrik.kaju.pri.ee/ubuntu/di...6/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/di...6/Packages.bz2](http://hendrik.kaju.pri.ee/ubuntu/di...6/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ubuntu.beryl-project.org/dist...86/Packages.gz](http://ubuntu.beryl-project.org/dist...86/Packages.gz) 404 Not Found [IP: 195.114.19.35 80]
Failed to fetch [http://ubuntu.beryl-project.org/dist...rce/Sources.gz](http://ubuntu.beryl-project.org/dist...rce/Sources.gz) 404 Not Found [IP: 195.114.19.35 80"

What should I do for this? I want Gutsy soon, and I'm a noob at Ubuntu.

---

### Post by BnetTheAwesome on 2007-10-21
Please, I need help here seriously.

---

### Post by Skight on 2008-03-13
JTux  @ #10 is right. Thank you!

---

