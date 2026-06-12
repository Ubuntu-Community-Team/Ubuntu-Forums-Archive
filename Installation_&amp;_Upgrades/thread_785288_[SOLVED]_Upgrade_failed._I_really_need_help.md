---
title: "[SOLVED] Upgrade failed. I really need help"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Arrgoss on 2008-05-07
Hi,

I didn't really want to upgrade my Ubuntu 7.10 until everything had been tested. Today the upgrade was present in my Update Manager, so I went for it. As a result, now I can't access my data through Nautilus and my profile doesn't load at start-up. This is what I did.

1) I run the update manager. I got a message warning me that "Not all updates can be installed" (I used to get this some time ago, I don't know why). I close the warning and run the upgrade anyway.
2) After a lot of downloading and installing, the computer need to be restarted, I do so.
3) After restarting, I get a message saying that the "human interface" cannot be loaded; it loads another one instead. I log in.
4) Then, my "usual" desktop is not shown, I see a nautilus windows blinking a couple of times. If I try to open a folder, I see Nautilus blinking once and then nothing. The only way I can aceess now all my data is via the terminal.
5) There are still some updates to be installed. If I try to do so: i) "Not all updates can be installed". Then, going on, I get the following error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
If a manually run the "dpkg --configure -a", I get:
```
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up powermanagement-interface (0.3.18) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing powermanagement-interface (--configure):
 subprocess post-installation script returned error exit status 127
Setting up foomatic-filters (3.0.2-20071204-0ubuntu2) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 127
Setting up libpaper1 (1.1.23) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 127
Setting up tex-common (1.10) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: dependency problems prevent configuration of foomatic-db-hpijs:
 foomatic-db-hpijs depends on foomatic-filters; however:
  Package foomatic-filters is not configured yet.
dpkg: error processing foomatic-db-hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpaper-utils:
 libpaper-utils depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing libpaper-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.8); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on preview-latex-style; however:
  Package preview-latex-style is not configured yet.
 texlive-latex-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-publishers:
 texlive-publishers depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-publishers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-pdf:
 cups-pdf depends on libpaper-utils; however:
  Package libpaper-utils is not configured yet.
dpkg: error processing cups-pdf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-fonts-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-pictures depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-fonts-recommended (>= 2007-11); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive-math-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-11); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2007-11); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lyx-common:
 lyx-common depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing lyx-common (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

```

Please, help! Can I fix this or go back to where I was before the upgrading?

---

### Post by bapoumba on 2008-05-07
Please make sure you have all the ubuntu repos in your sources.list file and **ubuntu-desktop** installed. Install **utils-linux**. Then run **sudo dpkg --configure -a** again.

---

### Post by Arrgoss on 2008-05-07
How do I check the repos, taking into account that System --> Admin --> Software Sources does not work (I thinks for the same reason)? Moreover, synaptics manager gives me the same message about manually installing the dpkg.

---

### Post by bapoumba on 2008-05-07
> **Arrgoss said:**
> How do I check the repos, taking into account that System --> Admin --> Software Sources does not work (I thinks for the same reason)? Moreover, synaptics manager gives me the same message about manually installing the dpkg.

Please post the output to:
```
cat /etc/apt/sources.list
```
We can use the terminal to fix it :)

---

### Post by Arrgoss on 2008-05-07
Long life the terminal!
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://blognux.free.fr/debian unstable main

```

---

### Post by bapoumba on 2008-05-07
At the bottom of the file, you have all the ubuntu repos. So it should work. We can make it prettier after your problem is solved.
Please post the output to:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

If the upgrade failed at some point, that should finish it.

---

### Post by Arrgoss on 2008-05-07
I went down to the same. After apt-get update:
```
Get:1 http://archive.canonical.com hardy Release.gpg [191B]
Get:2 http://archive.ubuntu.com hardy Release.gpg [191B]             
Get:3 http://security.ubuntu.com hardy-security Release.gpg [191B]          
Ign http://archive.canonical.com hardy/partner Translation-en_US     
Hit http://archive.canonical.com hardy Release                       
Hit http://archive.canonical.com hardy/partner Packages            
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/restricted Packages           
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://security.ubuntu.com hardy-security/restricted Sources            
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com hardy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Hit http://archive.ubuntu.com hardy Release                                    
Get:5 http://archive.ubuntu.com hardy-updates Release [51.2kB]                 
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/multiverse Sources                         
Hit http://archive.ubuntu.com hardy/restricted Sources
Get:6 http://archive.ubuntu.com hardy-updates/universe Packages [7224B]
Get:7 http://archive.ubuntu.com hardy-updates/main Packages [34.1kB]           
Get:8 http://archive.ubuntu.com hardy-updates/multiverse Packages [14B]        
Get:9 http://archive.ubuntu.com hardy-updates/restricted Packages [14B]        
Get:10 http://archive.ubuntu.com hardy-updates/universe Sources [1131B]        
Get:11 http://archive.ubuntu.com hardy-updates/main Sources [7871B]            
Get:12 http://archive.ubuntu.com hardy-updates/multiverse Sources [14B]        
Get:13 http://archive.ubuntu.com hardy-updates/restricted Sources [14B]        
Fetched 102kB in 3m18s (513B/s)                                                
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

And after apt-get dist-upgrade:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

---

### Post by bapoumba on 2008-05-07
Okay, back to my previous thought. Can you install util-linux?
```
sudo apt-get install util-linux
```

---

### Post by Arrgoss on 2008-05-07
The same message :(

---

### Post by bapoumba on 2008-05-07
Okay, I browsed around. Please check [here]("http://ubuntuforums.org/showpost.php?p=4543554&postcount=47"), and two posts below, the missing file is attached. I'm not using the same kernel as you are, I can give you my own, but not sure it will work. In the quoted thread, it's the 2.6.22-14-generic, same as yours. Good luck ..
Edit, I have to got, but will check back here later :)

---

### Post by fixitdude on 2008-05-07
Is there any chance of using the hardy CD to do an install? Make sure it uses all your old data, no formatting partitions etc...

And to let you know, they are not clear on how to do that in the online directions so be very careful, plus do a backup of some sort of all your important data anyway (use the live CD if you have to).

EDIT: This site has more details about what does what on install

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Arrgoss on 2008-05-07
Thanks. I tried, but it didn't work. I copied the file into usr/bin and then run dpkg --configure -a. The output:
```
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up powermanagement-interface (0.3.18) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing powermanagement-interface (--configure):
 subprocess post-installation script returned error exit status 127
Setting up foomatic-filters (3.0.2-20071204-0ubuntu2) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 127
Setting up libpaper1 (1.1.23) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 127
Setting up tex-common (1.10) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing tex-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of foomatic-db-hpijs:
 foomatic-db-hpijs depends on foomatic-filters; however:
  Package foomatic-filters is not configured yet.
dpkg: error processing foomatic-db-hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpaper-utils:
 libpaper-utils depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing libpaper-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 1.8); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on preview-latex-style; however:
  Package preview-latex-style is not configured yet.
 texlive-latex-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-publishers:
 texlive-publishers depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-publishers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-pdf:
 cups-pdf depends on libpaper-utils; however:
  Package libpaper-utils is not configured yet.
dpkg: error processing cups-pdf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-fonts-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base-bin:
 texlive-base-bin depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-pictures depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-fonts-recommended (>= 2007-11); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive-math-extra depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2007); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-11); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2007-11); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lyx-common:
 lyx-common depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing lyx-common (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

```

Do i need to uncompress the file first? If so, how do I do it from the terminal?

---

### Post by Arrgoss on 2008-05-07
> **fixitdude said:**
> Is there any chance of using the hardy CD to do an install? Make sure it uses all your old data, no formatting partitions etc...

Is that an special CD or just the normal installation CD?

---

### Post by fixitdude on 2008-05-07
> **Arrgoss said:**
> Is that an special CD or just the normal installation CD?Most people seem to be using the "alternate" CD with success.

I didn't upgrade that way but from what I have read, pick manual partition when you get to that part so it uses your existing partitions and you don't lose any data (always back up your important stuff first, you can boot the CD and use it to copy files).

---

### Post by bapoumba on 2008-05-07
> **Arrgoss said:**
> Thanks. I tried, but it didn't work. I copied the file into usr/bin and then run dpkg --configure -a. The output:

Do i need to uncompress the file first? If so, how do I do it from the terminal?
Yes, you do. Assuming the file is in your /home/your_username folder:
```
sudo tar -xvvzf getopt.tar.gz -C /home/your_username/
```
I just tried to extract the file, it creates a /usr/bin/getopt file (be careful, these ones are not the ones from your file system, they have the same name, but will be located in your /home).
You can change directory with **cd**.

```
your_username@yourhost:~$ cd usr/bin/
your_username@yourhost:~/usr/bin$ [COLOR="Red"]<-- you are still in your /home, with the ~ prompt, but in the newly created file.[/COLOR]
ls [COLOR="Red"]<-- run ls just like that, the answer should be the line below[/COLOR]
getopt [COLOR="Red"]<-- the ls command will just list what is in the file. You should just get getopt[/COLOR]
your_username@yourhost:~/usr/bin$ sudo cp getopt /usr/bin/ [COLOR="Red"]<-- copy the file where it should be[/COLOR]
```
That should do it.

I'll try to attach the extracted file from the other thread, but not sure the forums will let me upload an executable. Edit, nope, I cannot upload the extracted file.
Good luck again :)

---

### Post by Arrgoss on 2008-05-08
Thanks, bapoumba, I'm not used to use the terminal... I copied the file, did a dpkg --configure -a and it went through apparently ok. Then I've run apt-get update; everything fine! Now, I did a apt-get dist-upgrade and everything seems to work all right. After ~8 to 10 hours of downloading with my super home connection I will know what's the result of all this. Should I do something else, or this will fix my original problem?

I'll keep you posted tomorrow morning if nothing fails!

---

### Post by bobnutfield on 2008-05-08
> **bapoumba said:**
> Okay, I browsed around. Please check [here]("http://ubuntuforums.org/showpost.php?p=4543554&postcount=47"), and two posts below, the missing file is attached. I'm not using the same kernel as you are, I can give you my own, but not sure it will work. In the quoted thread, it's the 2.6.22-14-generic, same as yours. Good luck ..
Edit, I have to got, but will check back here later :)

I am just curious, maybe I missed something, but why is the OP booting into the 2.6.22-14 kernel when Hardy installs the 2.6.24 kernel?  A number of people who elected to keep their original menu.lst file are finding problems like.  Try booting the new kernel.

Bob

---

### Post by bapoumba on 2008-05-08
> **Arrgoss said:**
> Thanks, bapoumba, I'm not used to use the terminal... I copied the file, did a dpkg --configure -a and it went through apparently ok. Then I've run apt-get update; everything fine! Now, I did a apt-get dist-upgrade and everything seems to work all right. After ~8 to 10 hours of downloading with my super home connection I will know what's the result of all this. Should I do something else, or this will fix my original problem?

I'll keep you posted tomorrow morning if nothing fails!
Wow, warm congratulations \o/
Hopefully the dist-upgrade will go through fine. Remember sometimes it needs to be run a couple times in a row. I have no real explanation for it, I had to on occasions, and I read it was normal at the time.

Once everything is okay, we can clean your sources.list file from all the unneeded gutsy repos, and make it a little more organized. I can give you mine. Come back and post it again (cat /etc/apt/sources.list), there is no rush.

/me feels really happy for you, it was not an easy one :)

---

### Post by bapoumba on 2008-05-08
> **bobnutfield said:**
> I am just curious, maybe I missed something, but why is the OP booting into the 2.6.22-14 kernel when Hardy installs the 2.6.24 kernel?  A number of people who elected to keep their original menu.lst file are finding problems like.  Try booting the new kernel.

Bob
Yes, I saw it too, I'm not sure why, thanks to point that out. I just assumed that the upgrade failed at some point because some files did not properly download (thus the missing one(s), and may be the previous kernel) and the dist-upgrade should take care of it. Would you have a link, by any chance?

---

### Post by Arrgoss on 2008-05-08
OK, I will run the dist-upgrade a second time if it's ready before I go to sleep. Tomorrow I'm traveling and not coming back until Tuesday, so don't be surprised if I'm not posting for a couple of days.

Et encore, merci bien!

---

### Post by bapoumba on 2008-05-08
> **Arrgoss said:**
> OK, I will run the dist-upgrade a second time if it's ready before I go to sleep. Tomorrow I'm traveling and not coming back until Tuesday, so don't be surprised if I'm not posting for a couple of days.
Okay, no problem, let us know. Have a safe trip!

> **Arrgoss said:**
> 
Et encore, merci bien!
Mais de rien :)

---

### Post by Arrgoss on 2008-05-08
The dist-upgrade finished smoothly and I'm writing now from my upgraded 8.04 =D> ! I got a couple of messages, though, about some latex packages that could not be upgraded and that I dismissed for the moment. I didn't run a second dist-upgrade, because everything seems to be all right, should I do it anyway?

In my update manager I see some 49 updates available which I'm not going to install at the moment, maybe you suggest to do something else before, bapoumba.

And, again, thank you so much for your help. I don't know how to express my gratitude for what you and others like you are doing.

I'm not closing the thread yet, in order to clean up my sources list. Here it is, and I'll be back in a couple of days!
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://blognux.free.fr/debian unstable main
```

---

### Post by bobnutfield on 2008-05-09
> **bapoumba said:**
> Yes, I saw it too, I'm not sure why, thanks to point that out. I just assumed that the upgrade failed at some point because some files did not properly download (thus the missing one(s), and may be the previous kernel) and the dist-upgrade should take care of it. Would you have a link, by any chance?  

Hello,

There is no link necessary.  The 2.6.24 kernel is there, but many people, when asked during the install, elected to keep their original menu.lst file to keep their boot configuration.  Because of this, Hardy default-boots into the original kernel.  Some people booted Ubuntu from anther distros menu.lst.  In these cases, you simply have to add Hardy's 2.6.24 kernel and , initrd to the menu.lst and, if using Ubuntu's menu.lst, move it to the top to be the default.

Regards

Bob

---

### Post by bapoumba on 2008-05-09
@ Arrgoss: you're more than welcome :)

To make your sources.list a little more organized, you can remove all your gutsy repos and arrange the hardy ones. Here is mine:
```
## General.
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

## Major bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## Backports.
[COLOR="Red"]#[/COLOR] deb http://fr.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
[COLOR="Red"]#[/COLOR] deb-src http://fr.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Canonical's 'partner' repository.
[COLOR="Red"]#[/COLOR] deb http://archive.canonical.com/ubuntu hardy partner
[COLOR="Red"]#[/COLOR] deb-src http://archive.canonical.com/ubuntu hardy partner

## Security.
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
```

You can use it. Please open a terminal and run:
```
sudo nano /etc/apt/sources.list
```
And _replace_ everything with mine. If you want the backports and the partner repos active, just remove the [COLOR="Red"]#[/COLOR] at the beginning of the deb lines (the ones in red). A # means the line is a comment and is ignored by the package managers. Remove it, and the repos will be taken into account. I do not use them, this is why they are commented.

Save the file with CTRL-0 (same name, hit enter)
Exit nano with CTRL-X

```
sudo apt-get update
```
will have the package manager read the new file and check the repos for updates.
```
sudo apt-get dist-upgrade
```
will apply the updates. dist-upgrade checks the dependencies better than a regular upgrade (it is not only to go from one release to another, but to upgrade the whole distribution carefully checking packages dependencies. I always use it :))

You could also make sure **ubuntu-desktop** is installed before doing all of this. It is a meta-package, that depends on all the essential parts of the environment.

> **bobnutfield said:**
> Hello,

There is no link necessary.  The 2.6.24 kernel is there, but many people, when asked during the install, elected to keep their original menu.lst file to keep their boot configuration.  Because of this, Hardy default-boots into the original kernel.  Some people booted Ubuntu from anther distros menu.lst.  In these cases, you simply have to add Hardy's 2.6.24 kernel and , initrd to the menu.lst and, if using Ubuntu's menu.lst, move it to the top to be the default.

Regards

Bob

To answer this question, Arrgoss please post the output to:
```
lsb_release -cd
Description:	Ubuntu 8.04
Codename:	hardy
```
```
uname -a
Linux scorpio 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
```

---

### Post by Arrgoss on 2008-05-23
@ bapoumba:

Hi again. I'm sorry it took me so long to get back to this thread, but here I am. Let's see if I can be of any help for you. Now, when I boot my computer, it gives me the option to choose the kernel: 2.6.24-16 or 2.6.22-14. Choosing one or the other does not apparently change anything I can see by "bare eye". Right now, I'm logged into the 2.6.24-16, and the outpot to your requests

> **bapoumba said:**
> 
To answer this question, Arrgoss please post the output to:
```
lsb_release -cd
Description:	Ubuntu 8.04
Codename:	hardy
```
```
uname -a
Linux scorpio 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
```

are the following:

```
lsb_release -cd
Description:	Ubuntu 8.04
Codename:	hardy
```

and
```

uname -a
Linux izeddin-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```

I hope this is of any help. Can I remove one of the kernels without causing troubles? How would I do that?

PS: I haven't tidied up my sources.list yet. I will follow you instructions this weekend, unless you advice me to send my list back to you again, and check everything still applies.

---

### Post by bapoumba on 2008-05-24
From what I see, you are running hardy with the proper kernel. removing the previous one is safe, but I usually keep *one additional working kernel* (just in case an unfortunate bug comes with a new kernel upgrade).

So if you are happy and everything is working great, you can make your sources.list file a little better organized.
You can use nano (see a couple posts above) to edit the file. If you are not sure, please post yours again:
```
cat /etc/apt/sources.list
```

---

### Post by Arrgoss on 2008-05-26
I will follow your advice and keep the "extra kernel" just in case.
On my sources.list, here it is again. If you were so kind to take a look at it, I will be really happy to organize it as you suggest. And thanks again!

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://blognux.free.fr/debian unstable main

```

---

### Post by bapoumba on 2008-05-29
Sorry it took me so long to answer.

You can edit your sources.list with nano, a small text editor working from the terminal:
```
sudo nano /etc/apt/sources.list
```

**Replace** everything with this:
```
## General.
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

## Major bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## Canonical's 'partner' repository.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

## Security.
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

```
Save the file with CTRL-O (same name, hit enter)
Exit nano with CTRL-X
Reload the file:
```
sudo apt-get update
```
You're done :)

---

### Post by Arrgoss on 2008-06-03
Again,Bapumba, thanks a lot for your useful help. I don'y know how to show you my gratitude.

---

