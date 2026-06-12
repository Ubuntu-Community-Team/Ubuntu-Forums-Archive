---
title: "I cant apt-get update please help"
date: 2005-09-25
forum: Installation &amp; Upgrades
---

### Post by JaS on 2005-09-25
Hi,I just receved my Ubuntu disks in the mail today and wanted to give it a try but 
here is the errors i get,I can't connect to any of the servers to apt-get update.I keep getting connection refused .. and yes i have port 80 open.Although that shouldn't make a diff
####################################################
root@XXXXXXXX:~ # apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused) [IP: 82.211.81.182 80]
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
####################################################
Anyone know how to resolve this?

Thanks in advance for any help.
                   Regards,
                            JaS

---

### Post by ounas on 2005-09-25
The [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) is down or is under some problem condition

**Mirrors can be found at:**
[Ubuntu mirrors](http://wiki.ubuntu.com/Archive) 

Use another mirror near to you, first make a copy of your sources.list with the following comment:

**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup**

then **sudo gedit /etc/apt/sources.list** to edit the file.

It worked for me

-
Ounas ;-)

---

### Post by JaS on 2005-09-25
thanks I will give it a shot

---

### Post by JaS on 2005-09-25
How long has the ubuntu servers had this problem?
any word on how long they will have this problem?

I just would like to use the apt-get servers from the O/S's makers.Its kinda crappy when you try out a new o/s and things like this happen..... :( 
well i hope its soon that the problem is resolved

EDIT : Wow now im impressed.The apt-get servers are up its almost like someone heard me and fixed the problem ... lol.now i have frozen bubble and my girlfrand can be happy ( I'm trying Ubuntu out on her pc :) )

---

### Post by jclose on 2006-05-04
I ran into the same problem as noted above in the original post.  I am trying the different mirrors to see if that will work...

I had some limited success with other mirrors.  I am still getting Connection Refused messages from the mirror that I chose (there happened to be one in the same town I am in).  

Do the main Ubuntu servers often run into this problem?  

Thanks,
JC

---

