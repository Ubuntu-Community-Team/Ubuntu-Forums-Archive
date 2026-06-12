---
title: "cannot apt-get update and upgrade properly , help needed here."
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by maizuddin35 on 2010-12-25
Hello guys. 

I need your help with this one, I never face this problem before.Ok.

I just installed ubuntu 10.10 . Installation when smoothly like normal. After installation , I restart and the grub went missing, I fixed it, and it done, but when I want to sudo apt-get update and sudo apt-get upgrade

this , come out :

```
sudadib@maizuddin35:~$ sudo apt-get update
Get:1 http://extras.ubuntu.com maverick Release.gpg [65B]
Get:2 http://my.archive.ubuntu.com maverick Release.gpg [198B]              
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/main Translation-en         
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Get:3 http://my.archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:4 http://my.archive.ubuntu.com maverick Release [39.8kB]
Err http://my.archive.ubuntu.com maverick Release                              
  
Get:5 http://my.archive.ubuntu.com maverick-updates Release [31.4kB]           
Err http://my.archive.ubuntu.com maverick-updates Release                     
  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Get:6 http://extras.ubuntu.com maverick Release [57.3kB]
Err http://extras.ubuntu.com maverick Release           
  
Get:7 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:8 http://security.ubuntu.com maverick-security Release [27.2kB]
Err http://security.ubuntu.com maverick-security Release
  
Fetched 663B in 4s (139B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://my.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://my.archive.ubuntu.com maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://my.archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://my.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
adib@maizuddin35:~$ 

```

and when I sudo apt-get ugprade ,the result is this :

```
adib@maizuddin35:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adib@maizuddin35:~$ 

```

This doesn't seem correct , cause , I just installed my ubuntu without any internet connection and I can not also enable my nvidia graphic card driver, cause there is no drivers listed .

Please help me with this one. Thank you in advanced.

---

### Post by susema on 2010-12-25
After that command, try again;

```
sudo sh -c "echo 'Dir::Ignore-Files-Silently:: \"(.save|.distupgrade)$\";' > /etc/apt/apt.conf.d/99ignoresave"
```

---

### Post by maizuddin35 on 2010-12-25
ok, thanks for the reply, I'm trying now

---

### Post by maizuddin35 on 2010-12-25
should put the quotes together ?

ok , i now confuse, I need to run that one first, than I run apt-get update?

---

### Post by maizuddin35 on 2010-12-25
Updated from me, I think I solved one of the problem . Where I change the server connection from my country server to the main server via Ubuntu Software Center 

and when I sudo apt-get update, here is the result :

```
adib@maizuddin35:~$ sudo apt-get update
Get:1 http://extras.ubuntu.com maverick Release.gpg [65B]
Hit http://archive.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Get:2 http://extras.ubuntu.com maverick Release [57.3kB]
Err http://extras.ubuntu.com maverick Release           
  
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-security Release.gpg                    
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en    
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US 
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://archive.ubuntu.com maverick Release                                 
Hit http://archive.ubuntu.com maverick-updates Release                         
Hit http://archive.ubuntu.com maverick-security Release                        
Hit http://archive.ubuntu.com maverick/main Sources                            
Hit http://archive.ubuntu.com maverick/restricted Sources                      
Hit http://archive.ubuntu.com maverick/universe Sources                        
Hit http://archive.ubuntu.com maverick/multiverse Sources                      
Hit http://archive.ubuntu.com maverick/main i386 Packages                      
Hit http://archive.ubuntu.com maverick/restricted i386 Packages                
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Sources
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Fetched 66B in 18s (4B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
adib@maizuddin35:~$ 

```

but the weird thing is, I get the a error at the last part , what does that mean??? 
can please anyone tell ? thanks in advanced.

---

### Post by karthick87 on 2010-12-25
> **susema said:**
> After that command, try again;

```
sudo sh -c "echo 'Dir::Ignore-Files-Silently:: \"(.save|.distupgrade)$\";' > /etc/apt/apt.conf.d/99ignoresave"
```

Can you explain us?Actually what that command does??

---

### Post by susema on 2010-12-25
Ok. Look at this please;

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1642254](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1642254)

---

### Post by susema on 2010-12-25
@karthick87, look at that, is it enough?

[http://www.absolutelytech.com/2010/08/27/solved-ignoring-file-distupgrade-save-in-directory-etcaptsources-list-d-as-it-has-an-invalid-filename-extension-on-ubuntu-10-10/](http://www.absolutelytech.com/2010/08/27/solved-ignoring-file-distupgrade-save-in-directory-etcaptsources-list-d-as-it-has-an-invalid-filename-extension-on-ubuntu-10-10/)

---

### Post by Verbeck on 2010-12-25
[SIZE=3][COLOR=DarkRed][**Known Maverick Meerkat issues/bugs with workarounds**]("http://ubuntuforums.org/showthread.php?t=1588889")[/COLOR][/SIZE]
> 
**_GPG Errors_**: If you get the following error message:
[QUOTE]W: An error occurred during the signature verification. The repository   is not updated and the previous index files will be used.
GPG error: [http://extras.ubuntu.com]("http://extras.ubuntu.com/")   maverick Release: The following signatures couldn't be verified  because  the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)

Run:

```
gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
gpg –export –armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```[/QUOTE]

---

### Post by karthick87 on 2010-12-25
> **susema said:**
> @karthick87, look at that, is it enough?

[http://www.absolutelytech.com/2010/08/27/solved-ignoring-file-distupgrade-save-in-directory-etcaptsources-list-d-as-it-has-an-invalid-filename-extension-on-ubuntu-10-10/](http://www.absolutelytech.com/2010/08/27/solved-ignoring-file-distupgrade-save-in-directory-etcaptsources-list-d-as-it-has-an-invalid-filename-extension-on-ubuntu-10-10/)


Thankyou :)

---

### Post by maizuddin35 on 2010-12-25
@Verback, right now Im updating and upgrading my ubuntu, I'll try that one after Im done updating it. thanks for reply

---

