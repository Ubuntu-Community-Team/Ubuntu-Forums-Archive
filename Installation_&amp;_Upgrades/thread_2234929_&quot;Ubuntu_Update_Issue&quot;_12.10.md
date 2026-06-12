---
title: "&quot;Ubuntu Update Issue&quot; 12.10"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by brad26 on 2014-07-17
Hello all I am completely new to Ubuntu and Linux. I am currently taking a Linux class for college and figured "why not install Linux on an old laptop." This machin is an Acer Extensa 4630Z with 2g of RAM and a 500g HD. After making an ISO image for 14.04 LTS and trying to install it would freeze during the installation. After searching thre internet someone else had the same issue and could not install 14 either. So I played around with all of the different versions and was able to get Ubuntu 12.10 installed. The problem I am having is that I cannot get the apt-update to work. Any help will be appreciated, (I have searched to no avail) and as you know I might need the "layman's terms, Thanks! Here is the output:  Oh BTW how do I past this in a text box?

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Translation-en
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by grahammechanical on 2014-07-17
The reason for this is that Ubuntu 12.10 reached End of Life 16th May this year. The software repositories for 12.10 are now closed. You could try either 12.04 or 14.04 using an F6 option.

At the first purple screen with the icons of a keyboard and a human press Enter. At the next screen select the language press Enter. At the underlying screen with the option to TRY - INSTALL press F6. Look for a menu as shown in this link section 6.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Select nomodeset and press Enter and the press Esc to get back to the TRY - INSTALL men u. And go from there. T=You might need to use a combination of those F6 options, 

Regards.

---

### Post by brad26 on 2014-07-17
I had the 12.04 previously, but the same thing was happening when trying to update from Terminal. I tried to move forward and install one OS version to the next, but it freezes from update 13+ I have tried F6 with various options and it always hangs or freezes. I'm sure there is some hardware issue going on with my laptop but do not know the correct method(s) to bypass. Interesting how previous versions work but not the more recent.

---

