---
title: "Ubuntu won't boot"
date: 2014-10-11
forum: Installation &amp; Upgrades
---

### Post by AnotherKevin on 2014-10-11
I had a triple boot system:  Win 8.1, Win 7 and Kubuntu 14.04.  I dumped Win 8.1 and combined the 2 windows partitions into 1 and it's all Win 7 now and working fine.  Now grub never shows when I boot the system, so I tried boot-repair and I got an error just trying to get the file from the repositories. It said the file wasn't there (I did a copy and paste from the Ubuntu wiki).  So, then I used my USB Live Ubuntu and just reinstalled the Ubuntu - still no grub menu.  It just loads Win 7...

Any help?

Thanks,

Kevin

---

### Post by oldfred on 2014-10-11
Is this the link you used?
It was updated with an added command to convert from trusty to saucy as there is not a trusty version of Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If not what link did you use for Boot-Repair.

Best to run Boot-Repair and post link to its summary report.

---

### Post by AnotherKevin on 2014-10-11
> **oldfred said:**
> Is this the link you used?
It was updated with an added command to convert from trusty to saucy as there is not a trusty version of Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If not what link did you use for Boot-Repair.

Best to run Boot-Repair and post link to its summary report.

Yes, that's it.  Just tried again.  This is what I get when giving the second line in the instructions:
```
kubuntu@kubuntu:~$ sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-trusty.list
sed: can't read /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-trusty.list: No such file or directory

```

---

### Post by oldfred on 2014-10-11
Post what happens with all 4 lines. You do have to have working Internet as it is downloaded.

---

### Post by AnotherKevin on 2014-10-11
> **oldfred said:**
> Post what happens with all 4 lines. You do have to have working Internet as it is downloaded.


This is all of it:

```
kubuntu@kubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair Simple tool to repair frequent boot problems.


Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpjmr_ay7j/secring.gpg' created
gpg: keyring `/tmp/tmpjmr_ay7j/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpjmr_ay7j/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
kubuntu@kubuntu:~$ sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-trusty.list
sed: can't read /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-trusty.list: No such file or directory
kubuntu@kubuntu:~$ sudo apt-get update
Ign cdrom://Kubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Kubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Kubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Kubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/multiverse Translation-en_US
Ign cdrom://Kubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/multiverse Translation-en
Ign cdrom://Kubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Kubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign cdrom://Kubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/universe Translation-en_US
Ign cdrom://Kubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/universe Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://archive.ubuntu.com trusty Release.gpg                               
Get:2 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]   
Get:3 http://dl.google.com stable Release [1,347 B]                            
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty Release                                   
Get:4 http://dl.google.com stable/main amd64 Packages [1,182 B]                
Get:5 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Ign http://ppa.launchpad.net trusty Release.gpg                       
Get:6 http://archive.ubuntu.com trusty-updates Release [59.7 kB]      
Ign http://ppa.launchpad.net trusty Release                                    
Get:7 http://security.ubuntu.com trusty-security Release [59.7 kB]             
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:8 http://security.ubuntu.com trusty-security/main amd64 Packages [148 kB]
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                  
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en
Get:9 http://archive.ubuntu.com trusty-updates/main amd64 Packages [339 kB]
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:11 http://security.ubuntu.com trusty-security/universe amd64 Packages [49.8 kB]
Get:12 http://security.ubuntu.com trusty-security/main Translation-en [72.4 kB]
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Err http://ppa.launchpad.net trusty/main amd64 Packages                       
  404  Not Found
Get:13 http://security.ubuntu.com trusty-security/universe Translation-en [29.0 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Get:14 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Ign http://ppa.launchpad.net trusty/main Translation-en                      
Get:15 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [210 kB]
Hit http://archive.ubuntu.com trusty-updates/main Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 978 kB in 4s (236 kB/s)
W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
kubuntu@kubuntu:~$ sudo apt-get install -y boot-repair && (boot-repair &)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair



```

And thanks for helping...

Kevin

---

### Post by AnotherKevin on 2014-10-11
I did another search on Google and found a link to make a live usb boot disk with boot-repair.  I gave it (another) shot and it worked.  

Thanks for the attention and assistance...

Kevin

---

