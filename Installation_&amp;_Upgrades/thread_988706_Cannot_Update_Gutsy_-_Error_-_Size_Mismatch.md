---
title: "Cannot Update Gutsy - Error - Size Mismatch"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by ZanexGt on 2008-11-20
Can anyone explain why this is happening? I keep getting the Ubuntu tray icon saying that there are updates available and when I try to update I get an error saying that there is a "size mismatch" and the update does not complete. 

I opened up a terminal window and tried manually to update. Here is what I got. 

```
leslie@plagueis:~$ sudo apt-get update --fix-missing
Get:1 http://archive.canonical.com gutsy Release.gpg [189B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]             
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US                 
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [189B]   
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US 
Get:4 http://apt.wicd.net gutsy Release.gpg [189B]                   
Ign http://apt.wicd.net gutsy/extras Translation-en_US                         
Hit http://archive.canonical.com gutsy Release                                 
Ign http://archive.ubuntu.com gutsy/main Translation-en_US           
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US     
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US     
Get:5 http://archive.ubuntu.com gutsy-updates Release.gpg [189B]     
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US 
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com gutsy Release                                    
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://apt.wicd.net gutsy Release                                          
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://archive.ubuntu.com gutsy-updates Release                  
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://apt.wicd.net gutsy/extras Packages                                  
Hit http://archive.canonical.com gutsy/partner Sources               
Hit http://archive.ubuntu.com gutsy/universe Packages                
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Fetched 5B in 1s (5B/s)
Reading package lists... Done
leslie@plagueis:~$ sudo apt-get upgrade -o Acquire::Retries=4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  hpijs hplip hplip-data
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7522kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://security.ubuntu.com gutsy-security/main hplip-data 2.7.7.dfsg.1-0ubuntu5.1 [6898kB]
Get:2 http://security.ubuntu.com gutsy-security/main hplip 2.7.7.dfsg.1-0ubuntu5.1 [290kB]
Get:3 http://security.ubuntu.com gutsy-security/main hpijs 2.7.7+2.7.7.dfsg.1-0ubuntu5.1 [334kB]
Fetched 7523kB in 3m54s (32.0kB/s)                                             
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb  Size mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb  Size mismatch
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
leslie@plagueis:~$ 

```

Can anyone help? How do I fix this?

System Details:
Compaq F730US
1GB Ram
Gutsy 7.10

---

### Post by Pumalite on 2008-11-20
Try changing Server

---

### Post by ZanexGt on 2008-11-20
> **Pumalite said:**
> Try changing Server

I switched servers in software sources and it did not seem to help. Is there anything else I have to do?

Any other ideas?

---

### Post by zaffod on 2008-11-21
yeh i get a similar error : 

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb
  Size mismatch


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_amd64.deb
  Size mismatch


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_amd64.deb
  Size mismatch


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-gui_2.7.7.dfsg.1-0ubuntu5.1_all.deb
  Size mismatch
```

not quite sure why it's happening - i figured canonical broke something.

---

### Post by inventorstechnologies on 2008-11-21
same problem for me
any one help me
[http://www.inventorstechnologies.com]("http://www.inventorstechnologies.com")

---

### Post by javaJake on 2008-11-21
This is a known issue. There was a bug reported, and they're working on fixing it right now. A new package "should" be available today at some point.

[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/300247](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/300247)

---

### Post by HughReid on 2008-11-22
This problem seems to be happening again as I'm getting:
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)
  Size mismatch


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch
Any idea how to submit a bug report to get it fixed??

---

### Post by Markrian on 2008-11-22
javaJake above already pointed out that there's a bug filed for this problem, and linked to it. Here it is again: [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/300247](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/300247)

Gotta say, it's a shame the things like this seem to happen with Ubuntu more and more. It seems to me that their whole release model needs to change, since QA is surely spread quite thin.

---

### Post by javaJake on 2008-11-22
If they're spread too thin, perhaps they need volunteers. **hint hint** ;)

Just because a few bugs like this make it through the system doesn't mean the system is bad. It just means it isn't perfect.

---

### Post by ZanexGt on 2008-11-22
As a workaround, I have taken the URL's, pasted them into Firefox, downloaded the .Deb package files and installed by clicking on the downloaded packages.

After installing all 3 packages, the updater notification goes away. Seems like a good workaround until the Ubuntu team issues out a proper fix. 

Thanks for the responses and help all.

---

### Post by klaasvanschelven on 2008-11-23
Workaround works for me too (nl repos).

Bumping this; hope 7.10 isn't forgotten yet.

---

### Post by Dusenberg on 2008-11-23
> **Markrian said:**
> .......
Gotta say, it's a shame the things like this seem to happen with Ubuntu more and more. It seems to me that their whole release model needs to change, since QA is surely spread quite thin.

I've had 7.10 for about a year and this is first time I've had an update  problem. Ubuntu has been extremely reliable for me.:)

---

### Post by javaJake on 2008-11-23
> **klaasvanschelven said:**
> Bumping this; hope 7.10 isn't forgotten yet.

If you don't want it to be forgotten, the best thing is to add yourself to the bug report by using a newly-added feature in Launchpad. Developers do not generally browse the forums, so bumping a thread is going to do very little.

Sign/register in Launchpad, and then return to the bug I [linked]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/300247"). You'll see text that says "This bug doesn't affect me (change)". Click the link in "(change)" and it'll add you in. This allows the Ubuntu folks to finely prioritize things based on how many people report themselves as being affected.

---

