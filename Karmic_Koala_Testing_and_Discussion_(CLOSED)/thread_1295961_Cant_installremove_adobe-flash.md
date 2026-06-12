---
title: "Cant install/remove adobe-flash"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yossi_s1 on 2009-10-20
Hi
Im running ubuntu 9.10 and wanted to install flash with .deb file.
the installation ended with an error, i cant remember what it said.
now i cant install nor remove any packages.
also, when i try to download the same .deb (flash package), FF seem to DL the package instantly and when i try to install it i get an error about a bad package.

I also tried dpkg -i but failed, maybe thats cuz I just dont know how to use it.

---

### Post by pedro_orange on 2009-10-20
> **yossi_s1 said:**
> Hi
Im running ubuntu 9.10 and wanted to install flash with .deb file.
the installation ended with an error, i cant remember what it said.
now i cant install nor remove any packages.
also, when i try to download the same .deb (flash package), FF seem to DL the package instantly and when i try to install it i get an error about a bad package.

I also tried dpkg -i but failed, maybe thats cuz I just dont know how to use it.

Install flash in one of these ways..

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo apt-get install flashplugin-nonfree
```

The first will install codecs as well, and some other nifty stuff. The second one will simply install flash and nothing else.

---

### Post by yossi_s1 on 2009-10-20
Hm, I said I cant install any packages.
i tried what you said, error:
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it
when trying to install a deb package i get an error that says that the package is corrupted or that i dont have premsion

---

### Post by nothingspecial on 2009-10-20
Try ```
sudo apt-get install -f
```

---

### Post by pedro_orange on 2009-10-20
> **yossi_s1 said:**
> Hm, I said I cant install any packages.
i tried what you said, error:
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it
when trying to install a deb package i get an error that says that the package is corrupted or that i dont have premsion

Okay. When you do a:

```
sudo apt-get update
```

Do you get any errors? Or are they all fine?

(If you get errors) You might need to run a:

```
sudo dpkg --configure -a
```

Then do the update again, to check everything is okay.

If it's all okay, try and remove the installation

```
sudo apt-get remove adobe-flashplugin
```

Let us know the output of that.

---

### Post by pedro_orange on 2009-10-20
Also found this post, which may be of use to you.

[http://ubuntuforums.org/archive/index.php/t-1285455.html](http://ubuntuforums.org/archive/index.php/t-1285455.html)

The bottom post has a suggested fix.

---

### Post by yossi_s1 on 2009-10-20
> **nothingspecial said:**
> Try ```
sudo apt-get install -f
```

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.


> Okay. When you do a:

     Code:
     sudo apt-get update 
Do you get any errors? Or are they all fine?
```
Get:1 http://il.archive.ubuntu.com karmic Release.gpg [189B]
Ign http://il.archive.ubuntu.com karmic/main Translation-en_US
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://il.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://il.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://il.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://il.archive.ubuntu.com karmic-updates Release.gpg
Ign http://il.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://il.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://il.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://il.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release
Get:2 http://il.archive.ubuntu.com karmic Release [65.9kB]
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://il.archive.ubuntu.com karmic-updates Release
Get:3 http://il.archive.ubuntu.com karmic/main Packages [1,353kB]
Get:4 http://il.archive.ubuntu.com karmic/restricted Packages [7,935B]         
Get:5 http://il.archive.ubuntu.com karmic/main Sources [640kB]                 
Get:6 http://il.archive.ubuntu.com karmic/restricted Sources [3,268B]          
Get:7 http://il.archive.ubuntu.com karmic/universe Packages [5,129kB]          
Get:8 http://il.archive.ubuntu.com karmic/universe Sources [2,784kB]           
Get:9 http://il.archive.ubuntu.com karmic/multiverse Packages [192kB]          
Get:10 http://il.archive.ubuntu.com karmic/multiverse Sources [117kB]          
Hit http://il.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://il.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://il.archive.ubuntu.com karmic-updates/main Sources                   
Hit http://il.archive.ubuntu.com karmic-updates/restricted Sources             
Hit http://il.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://il.archive.ubuntu.com karmic-updates/universe Sources               
Hit http://il.archive.ubuntu.com karmic-updates/multiverse Packages            
Hit http://il.archive.ubuntu.com karmic-updates/multiverse Sources             
Fetched 10.3MB in 2min 14s (76.7kB/s)                                          
Reading package lists... Done

```so It seems to be fine, buy trying to remove flash i still get the same error.
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
i also tried the 2nd option you told me, still the same

---

### Post by yossi_s1 on 2009-10-20
> **pedro_orange said:**
> Also found this post, which may be of use to you.

[http://ubuntuforums.org/archive/index.php/t-1285455.html](http://ubuntuforums.org/archive/index.php/t-1285455.html)

The bottom post has a suggested fix.
 
finally! worked! tnx.
but now, how do i install flash without getting errors again?

---

### Post by HotShotDJ on 2009-10-20
Install it using either Applications -> Software Center or System -> Synaptic Package Manager.  You don't need to download it separately.  Since you probably want all the goodies, choose "ubuntu-restricted-extras" in one of the above listed applications.

---

### Post by pedro_orange on 2009-10-21
> **yossi_s1 said:**
> finally! worked! tnx.
but now, how do i install flash without getting errors again?

```
sudo apt-get install ubuntu-restricted-extras
```

---

