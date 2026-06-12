---
title: "ZLIB_1.2.9 not found after upgrade/new install of Ubuntu 17.10"
date: 2017-10-28
forum: Installation &amp; Upgrades
---

### Post by dhavalbbhatt2 on 2017-10-28
Hello all,
I was using Ubuntu 17.04 quite OK and with the new release of 17.10, I got bitten by the bug to upgrade to the new version. I have a few niche programs that I used to run (most important one being PixInsight - it is an astrophotography tool). After the upgrade I tried to run PixInsight, however, it would not open up. Given that this is a new system, I did a new install of Ubuntu17.10 with no change in behavior as it relates to PixInsight. 

I took a look at the syslogs and found the following two lines - I am hoping someone can help:

"/opt/PixInsight/bin/PixInsight: /opt/PixInsight/bin/lib/libz.so.1:  version `ZLIB_1.2.9' not found (required by  /usr/lib/x86_64-linux-gnu/libpng16.so.16)"

"/PixInsight/bin/PixInsight: error while loading shared libraries:  libssl.so.10: cannot open shared object file: No such file or  directory".

What happened as part of Ubuntu 17.10 that is breaking the PixInsight program? Can anyone shed some light? I can make this work on Elementary OS (which is what I am running right now, but not liking Elementary OS as much). Is it a case of simply missing some files that are no longer included in 17.10? If so, can I install those?

Thanks,
Dhaval

---

### Post by fanialivio on 2017-11-04
Hi,

I have exactly the same problem with Ubuntu 17.10 by using ffmpeg to render an animation sequence made with Krita :

/usr/bin/ffmpeg: ./lib/libz.so.1: version `ZLIB_1.2.9' not found (required by /usr/lib/x86_64-linux-gnu/libpng16.so.16)

Any help is appreciated,
liviux

---

### Post by bronaldo on 2017-11-08
Hi, 
I found the same issue on ubuntu 17.10. I solved the problem in this way: moving the libz.so.1 from the folder and creating a link for libz.so.1 in lib/x86_64-linux-gnu/libz.so.1. In particular the commands are:
cd /your_directory_software/../lib/ (the directory in which is present libz.so.1)
sudo mv libz.so.1 libz.so.1.old
sudo ln -s /lib/x86_64-linux-gnu/libz.so.1

After that the applications should work fine as in my case.
Simone

---

### Post by ian-weisser on 2017-11-08
Please use the 'ubuntu-bug' application to file a bug report about the issue, including the solution.

---

### Post by martinpi on 2017-12-27
> **bronaldo said:**
> Hi, 
I found the same issue on ubuntu 17.10. I solved the problem in this way: moving the libz.so.1 from the folder and creating a link for libz.so.1 in lib/x86_64-linux-gnu/libz.so.1. In particular the commands are:
cd /your_directory_software/../lib/ (the directory in which is present libz.so.1)
sudo mv libz.so.1 libz.so.1.old
sudo ln -s /lib/x86_64-linux-gnu/libz.so.1

After that the applications should work fine as in my case.
Simone

Thanks a lot, this solved the problem!

---

### Post by pbhatt on 2018-02-22
> **bronaldo said:**
> Hi, 
I found the same issue on ubuntu 17.10. I solved the problem in this way: moving the libz.so.1 from the folder and creating a link for libz.so.1 in lib/x86_64-linux-gnu/libz.so.1. In particular the commands are:
cd /your_directory_software/../lib/ (the directory in which is present libz.so.1)
sudo mv libz.so.1 libz.so.1.old
sudo ln -s /lib/x86_64-linux-gnu/libz.so.1

After that the applications should work fine as in my case.
Simone

Thank you so much. It worked for me too!

---

### Post by abhijitdas on 2018-05-18
> **bronaldo said:**
> Hi, 
I found the same issue on ubuntu 17.10. I solved the problem in this way: moving the libz.so.1 from the folder and creating a link for libz.so.1 in lib/x86_64-linux-gnu/libz.so.1. In particular the commands are:
cd /your_directory_software/../lib/ (the directory in which is present libz.so.1)
sudo mv libz.so.1 libz.so.1.old
sudo ln -s /lib/x86_64-linux-gnu/libz.so.1

After that the applications should work fine as in my case.
Simone


Thank you very very much bro it really solved the problem. In my case the problem was that the Mathematica application was not  opening :-
/usr/local/Wolfram/Mathematica/9.0/SystemFiles/FrontEnd/Binaries/Linux-x86-64/Mathematica: /usr/local/Wolfram/Mathematica/9.0/SystemFiles/Libraries/Linux-x86-64/libz.so.1: version `ZLIB_1.2.9' not found (required by /usr/local/lib/libpng16.so.16)
After your solution it started working brilliant!!! Otherwise I was going to downgrade my ubuntu to lower versions because of this problem!!! Really happy!!! :guitar:

---

### Post by jsperezc on 2018-12-28
> **bronaldo said:**
> Hi, 
I found the same issue on ubuntu 17.10. I solved the problem in this way: moving the libz.so.1 from the folder and creating a link for libz.so.1 in lib/x86_64-linux-gnu/libz.so.1. In particular the commands are:
cd /your_directory_software/../lib/ (the directory in which is present libz.so.1)
sudo mv libz.so.1 libz.so.1.old
sudo ln -s /lib/x86_64-linux-gnu/libz.so.1

After that the applications should work fine as in my case.
Simone

Perfect! Thanks

---

