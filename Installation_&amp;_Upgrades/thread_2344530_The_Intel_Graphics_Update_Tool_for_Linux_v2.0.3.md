---
title: "The Intel Graphics Update Tool for Linux v2.0.3"
date: 2016-11-26
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-11-26
Downloaded from OMG Ubuntu and got the following error messages.  See attachments.



[ATTACH=CONFIG]272385[/ATTACH][ATTACH=CONFIG]272386[/ATTACH]

Henry

PS Cannot delete files uploaded to file update manager.

This is what happens in terminal

```
henry@wyatt:~$ sudo apt update
[sudo] password for henry:          
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates InRelease [102 kB]                                                                   
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                   
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                     
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-backports InRelease [102 kB]                                                                 
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security InRelease [102 kB]                                                                    
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety InRelease                                              
Hit:8 [http://ppa.launchpad.net/libreoffice/libreoffice-5-2/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-5-2/ubuntu) yakkety InRelease                      
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates/main amd64 DEP-11 Metadata [76.6 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates/main DEP-11 64x64 Icons [37.8 kB]                       
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates/universe amd64 DEP-11 Metadata [59.8 kB]                               
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates/universe DEP-11 64x64 Icons [62.5 kB]                                       
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates/multiverse amd64 DEP-11 Metadata [212 B]                               
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-backports/main amd64 DEP-11 Metadata [208 B]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-backports/universe amd64 DEP-11 Metadata [212 B] 
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-backports/multiverse amd64 DEP-11 Metadata [216 B]
Get:18 [https://download.01.org/gfx/ubuntu/16.10/main](https://download.01.org/gfx/ubuntu/16.10/main) yakkety InRelease [3,650 B]
Err:18 [https://download.01.org/gfx/ubuntu/16.10/main](https://download.01.org/gfx/ubuntu/16.10/main) yakkety InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 611B903CAB97EA77
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security/main amd64 DEP-11 Metadata [5,480 B]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security/main DEP-11 64x64 Icons [5,347 B]
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security/universe amd64 DEP-11 Metadata [208 B]
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security/multiverse amd64 DEP-11 Metadata [212 B]
Reading package lists... Done     
W: GPG error: [https://download.01.org/gfx/ubuntu/16.10/main](https://download.01.org/gfx/ubuntu/16.10/main) yakkety InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 611B903CAB97EA77
E: The repository 'https://download.01.org/gfx/ubuntu/16.10/main yakkety InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
henry@wyatt:~$
```

---

### Post by howefield on 2016-11-26
Copy the below to a text file..

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1

mQENBFamqDQBCADCt6zxiWjTsCGuzU7azxTIlnXX54Txcq6ZeZhyB7DdxjjM/bZh
uzxWSVkGhpF4GptY+Fs3+7QydHJ74zWmvQQvq42nX4f/LiGDUCyqZFgc8UZWZlcP
/Mbz35FNYyMjqP3Iu/nO8jF31YjbTx4GtsZxWcCaIPZpmbrYTCmrzjfwFGkAa0LZ
sq6U54wbH5l9ehRD4MFJZJqIbGTHr6mlXHCQabM3G4Mcv9CJMYu258XgAPul2l94
5h0psOP6Y8w5k/SwbVUGWsSL1omIr1TiBzSwKn+itN1Hh/+jbi/0rYadv2uAVloW
XrLztofXa4179w/Onf87EPSoQzy/ZxLzAV7/ABEBAAG0RkVsaW8gTWFydGluZXog
KEluc3RhbGxlciBjb21waWxhdGlvbikgPGVsaW8ubWFydGluZXoubW9ucm95QGlu
dGVsLmNvbT6JATgEEwECACIFAlamqDQCGwMGCwkIBwMCBhUIAgkKCwQWAgMBAh4B
AheAAAoJEFaj3vhjlh05JY0IAKIntJAN/O7IsDbuxSV83U1Yr4AJRWKSE+cnbofs
m7smYX1Cn0xC7dnsBeocoCcRVpsf6LBNu6mCqrH8CJT4nyHT5+ld3HdhDIbUflsx
yqEvyTQ9q1375MtAjjmwmIDddFpHi9I0GBp+jeZVrkPOcEAHBsWLwCxMyPtdnSlf
loQ5b12a7b+j2K3SQej/H5YuwQUAoZd3jwvajxZavA/KGZtGi0CbNVtqIrBNrB+7
+FBDkIoQsULkfmEIoHWgrjL1dWl2Yc63svjNljB+OyxPmpbowlelPE2gqxcZ8Shr
xeJ9lG6FRxtTYcOlEpPB7JPl4zCxIHGunXjO0WCJGZwVM7i5AQ0EVqaoNAEIANuI
hE2OjATA5Vj4EIsyZ5yRK+hLODMSmU/zWgJLMZtp3zIk8BSJU6GOLXaodiN+6SgB
GEzjQkL4wF5IPe0z6mbIHm3jGGgEOItUodvhe3CC7LopHf/F98TBaN8bJTripE6r
o7JBASuLp0sQM27DxrLjZvTvw5fTboXoUDbPDLWeds6GrMBqZ8hHPBLecrt1iC7/
z2p9LfjOcNvbOngA13t6vDpqyo/NYrhnf2nmaW4LjbYeDnGMOBkLi/Fl4Herg9Jd
elO9OkwwzrdV9uBDSs3GMocUMn8/DSTkfT3Mejgtdcop2/p6HVZGyB4/Q5PKAn/x
Hp+5YdkrEGKAaMQI758AEQEAAYkBHwQYAQIACQUCVqaoNAIbDAAKCRBWo974Y5Yd
OcQgB/9+ymf4WCVKjKr/IAJY+kR1NiM+azUqsK9s9a9ilZQxrnUGeqk+GA9LV78b
c3bdUy9sVUPk/33pxMBOSh4KLNdQN26ZKyJM7lZbF6ha6Lm5qoZX0WzRp3Y1P3qJ
mo6pxRXuXd412yJS7eyKejavRDXd2fauCg3EnU27z4N7otQH8cGYTDWEnav0LH0i
INYYbhHIO/q0orX7C4EgT4EevtJn+DteaKW6WvBTPVfjXcQfI5AYhhIeNXfqr4qX
QeG3b40qUhSjcFapdjsZadqEQkuGFQsVqD8LJXZJfavl0qhYeAdEW5CQS2dd9Q8M
7+4QcpM6YeP/0rJBjwqJPEFcWzAe
=4YoI
-----END PGP PUBLIC KEY BLOCK-----
```

Then load up the Software & Updates application > Authentication tab > Import key file and navigate to where you saved the text file and import it.

---

### Post by big-thugs-0 on 2016-11-26
same issue here ,

i tried importing a file with that hashed text , but same issue , the key is not imported

EDIT:

i found a solution:
just run the following command

```
[COLOR=#2A2E2E][FONT=&amp]wget $(echo "https://download".01.org/gfx/RPM-GPG-GROUP-KEY-ilg) -O - | sudo apt-key add -[/FONT][/COLOR]
```

---

### Post by vasa1 on 2016-11-26
From the OMG article:> Please, please pay close attention to the list of known issues, caveats and install info on the downloads page. Take heed the advice to not force-installing packages.

Although the tool does offer Linux users a handy way to get the latest Intel graphics stack, it also has a reputation for breaking things without due diligence.Link: [http://www.omgubuntu.co.uk/2016/11/intel-graphics-installer-support-for-ubuntu-16-10](http://www.omgubuntu.co.uk/2016/11/intel-graphics-installer-support-for-ubuntu-16-10)

---

### Post by Hewjr100 on 2016-11-26
Well both fixes did not work anyway, so I am going to delete intel package and let it be.

Henry

Could not remove intel package:

```
henry@wyatt:~$ sudo apt remove intel-graphics-update-tool_2.0.3_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package intel-graphics-update-tool_2.0.3_amd64.deb
E: Couldn't find any package by glob 'intel-graphics-update-tool_2.0.3_amd64.deb'
E: Couldn't find any package by regex 'intel-graphics-update-tool_2.0.3_amd64.deb'
henry@wyatt:~$
```

Can't run update either:

```
henry@wyatt:~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-updates InRelease [102 kB]                                                                   
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                   
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety-backports InRelease [102 kB]                                                                 
Hit:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                     
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety InRelease                                                         
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security InRelease [102 kB]                   
Hit:8 [http://ppa.launchpad.net/libreoffice/libreoffice-5-2/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-5-2/ubuntu) yakkety InRelease
Get:10 [https://download.01.org/gfx/ubuntu/16.10/main](https://download.01.org/gfx/ubuntu/16.10/main) yakkety InRelease [3,650 B]   
Err:10 [https://download.01.org/gfx/ubuntu/16.10/main](https://download.01.org/gfx/ubuntu/16.10/main) yakkety InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 611B903CAB97EA77
Reading package lists... Done 
W: GPG error: [https://download.01.org/gfx/ubuntu/16.10/main](https://download.01.org/gfx/ubuntu/16.10/main) yakkety InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 611B903CAB97EA77
E: The repository 'https://download.01.org/gfx/ubuntu/16.10/main yakkety InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
henry@wyatt:~$ 
```

Henry

---

### Post by howefield on 2016-11-26
> **Hewjr100 said:**
> 

```
E: Unable to locate package intel-graphics-update-tool_2.0.3_amd64.deb
```

Please use code tags for terminal output.

What is the output of the following terminal command ?

```
apt-cache policy intel-graphics-update*
```

---

### Post by Hewjr100 on 2016-11-26
Ok remove intel from system settings, other software.  Update working.

---

### Post by mc4man on 2016-11-26
This method worked here for a one time use of the tool though I'm not too sure of the advantage of using it
(on my main install I don't use it, just using newer libva & vaapi..
[https://ubuntuforums.org/showthread.php?t=2342137&p=13565767&viewfull=1#post13565767](https://ubuntuforums.org/showthread.php?t=2342137&p=13565767&viewfull=1#post13565767)

---

### Post by Hewjr100 on 2016-11-26
howefiled, this is the output:

henry@wyatt:~$ apt-cache policy intel-graphics-update*
intel-graphics-update-tool:
  Installed: 2.0.3
  Candidate: 2.0.3
  Version table:
 *** 2.0.3 100
        100 /var/lib/dpkg/status
henry@wyatt:~$

---

### Post by Alduins_Khajiit on 2017-03-05
I tried everything listed in this thread to fix the untrusted sources update message but none of them worked for me. Is there anything else to do to fix this problem?

Here is my output

```
shrunken-human@Toilet:~$ apt-cache policy intel-graphics-update*
intel-graphics-update-tool:
  Installed: 2.0.2
  Candidate: 2.0.2
  Version table:
 *** 2.0.2 500
        500 https://download.01.org/gfx/ubuntu/16.04/main xenial/main amd64 Packages
        100 /var/lib/dpkg/status
shrunken-human@Toilet:~$ 


```

---

### Post by oldos2er on 2017-03-06
Thread hijack closed since you have an open thread [here.]("https://ubuntuforums.org/showthread.php?t=2352342")

---

