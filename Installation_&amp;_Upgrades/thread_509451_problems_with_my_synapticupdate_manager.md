---
title: "problems with my synaptic/update manager"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by yehudaco on 2007-07-25
[http://security.ubuntu.com/ubuntu/dists/...kages.bz2:](http://security.ubuntu.com/ubuntu/dists/...kages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/...kages.bz2:](http://security.ubuntu.com/ubuntu/dists/...kages.bz2:) Sub-process bzip2 returned an error code (2)

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9


What does it mean? i get this announcment every time i open my synaptic/update manager...
does anyone have a clue??

---

### Post by Seisen on 2007-07-25
It means you need to download the gpg key for it so it can be authenticated. Here is how to add the key

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
``` then
```
sudo apt-get update
```

---

### Post by NewJack on 2007-07-25
Maybe the key for that repo has changed and you need to get an updated one.  Do a search here on the forums and see if that has happened and just add the new key to your keyring.

---

### Post by yehudaco on 2007-07-25
i've done what you've suggested but the response was the same as i tried to do the reloading...
an idea?

---

### Post by yehudaco on 2007-07-25
what kind of key should i look for? i don't exactly follow...
can you be more specific about how to define what i'm looking for?

---

### Post by Seisen on 2007-07-25
Did you put this in the terminal?

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
``` and post your source list```
gksudo gedit /etc/apt/sources.list
```

---

### Post by yehudaco on 2007-07-25
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe

here it is...

---

### Post by Seisen on 2007-07-25
Take eyecandy out of this line for one thing

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
``` other than that I don't see any other problems with you source list. Post what happens when you put this in the terminal

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

---

### Post by yehudaco on 2007-07-25
i get this after i deleted the line you've suggested:

:~$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
--21:30:48--  [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [text/plain]

100%[====================================>] 4,180         --.--K/s             

21:30:50 (31.23 KB/s) - `-' saved [4180/4180]

OK

and  after i used reload in synaptic one error has gone indeed and the other stayed the one that stayed:
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by Seisen on 2007-07-25
I'm blind I found another problem in your source list which might be the problem. Take this line out

```
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe

``` and add the multiverse and universe to this line

```
deb http://il.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
```
the do the 

```
sudo apt-get update
```

---

### Post by yehudaco on 2007-07-25
after i deleted the line you've said and put instead:

deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe

i got this source.list:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse universe 

and then:

yehuda@Yehuda:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-he
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-he
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-he
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-he
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-he
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-he
Get:2 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Translation-he
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [54.1kB]
99% [3 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
  Sub-process bzip2 returned an error code (2)
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/restricted Translation-he   
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Translation-he
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/multiverse Translation-he
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Translation-he
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Translation-he
Get:4 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Translation-he
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Translation-he
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Translation-he
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Translation-he
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/multiverse Translation-he
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/universe Translation-he
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [54.1kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
99% [5 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  Sub-process bzip2 returned an error code (2)
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Translation-he
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/universe Translation-he
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty Release
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates Release
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/restricted Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/restricted Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Packages
Get:6 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/multiverse Packages [1263B]
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/universe Packages
Fetched 1268B in 3s (333B/s)
&#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
&#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Translation-he (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_dists_feisty_main_i18n_Translation-he)
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_dists_feisty-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/universe Packages (/var/lib/apt/lists/il.archive.ubuntu.com_ubuntu_dists_feisty-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

and the 2 errors i mentioned still there...
anyway thank you very much!!!!!!!
i really appreciate it!

---

### Post by DaOg75 on 2007-07-25
Hi, I had this same problem for a while and seemed to solve it by opening up the synaptic package manager and under the settings/repositories changed the server download tab from custom to server for the united states. Then re-run an apt-get update. Hope it helps.

---

### Post by Seisen on 2007-07-25
Try this source list.

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by yehudaco on 2007-07-25
these 2 errors still shows up....:oops:
any idea?

[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by Seisen on 2007-07-25
Try this
```
sudo apt-get clean
sudo apt-get check
``` if any errors pop up post them.

---

### Post by yehudaco on 2007-07-25
only the 2 errors that shows up when i press reload in synaptic i've mentioned before....
yehuda@Yehuda:~$ sudo apt-get clean
yehuda@Yehuda:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
yehuda@Yehuda:~$

---

### Post by Seisen on 2007-07-25
Comment out these two lines then ```
sudo apt-get update
```
if that doesn't pop up any errors than uncomment these two line and run ```
sudo apt-get update
``` let me know if the errors go away.

```
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
``` to comment the lines out put this **# **in front of them

---

### Post by yehudaco on 2007-07-25
i'm sorry, don't really understand what do you mean by comment and uncomment...

---

### Post by Seisen on 2007-07-25
To comment a line out you put this **"#"** in front of it so the line would look like this

```
#deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
```

---

### Post by NewJack on 2007-07-25
By putting this

##

in front of the line you wish to leave there, it will not  check that source  in your source list

(If I explained that correctly)

---

### Post by yehudaco on 2007-07-25
it's done!!!!!!!!!!
you've done it!!! (i didn't understand a thing though..)
no error messages at all!!
Thank you!!

---

### Post by Seisen on 2007-07-25
Unfortunately that is only a temporary fix now see what happens when you uncomment those two lines. Just take out the **"#"** and then run ```
sudo apt-get update
```

---

### Post by yehudaco on 2007-07-25
i've already done it it is working no errors messages!

---

### Post by Seisen on 2007-07-25
Good deal, took long enough to figure out the problem but at least it got solved.

---

### Post by yehudaco on 2007-07-25
cheers!!!
thanks -Again!!!

---

