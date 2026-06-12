---
title: "Problem on apt-get update over brand new instalation of UBNT13.04 desktop"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by marconobre on 2013-06-07
Hi all.

I am in Brazil, and have selected a server repository from here.

After complete instalation process I am going to do a #apt-get update and got this error:

root@mnobreVBoxUbnt1304:/etc/apt**# apt-get update**
Get:1 [http://sft.if.usp.br](http://sft.if.usp.br) raring Release.gpg
Get:2 [http://sft.if.usp.br](http://sft.if.usp.br) raring-updates Release.gpg                          
Get:3 [http://sft.if.usp.br](http://sft.if.usp.br) raring-backports Release.gpg                        
Get:4 [http://sft.if.usp.br](http://sft.if.usp.br) raring-security Release.gpg                         
Get:5 [http://sft.if.usp.br](http://sft.if.usp.br) raring Release                                      
Ign [http://sft.if.usp.br](http://sft.if.usp.br) raring Release                                        
E: GPG error: [http://sft.if.usp.br](http://sft.if.usp.br) raring Release: The following signatures were invalid: NODATA 1 NODATA 2

Reading some of the forum posts here, I made a few unsuccessful attempts. Some of them were:

(1) Try: update de gpg keys with: (and then try to #apt-get update)
root@mnobreVBoxUbnt1304:/etc/apt**# apt-key update**
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
[COLOR=#ff0000]>> [/COLOR][COLOR=#ff0000]the error [/COLOR][COLOR=#ff0000]remains the same[/COLOR]

(2) Try: generate other source.list with [http://repogen.simplylinux.ch](http://repogen.simplylinux.ch) (and then try to #apt-get update)
[COLOR=#ff0000]>> [/COLOR][COLOR=#ff0000]the error [/COLOR][COLOR=#ff0000]remains the same[/COLOR]

(3) Try: update or add the gpg (signatures) exposed (recomended) into the generated source.list, with:
root@mnobreVBoxUbnt1304:/etc/apt# cat mygpgkeys.sh 
#!/bin/sh -e
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 75198A89
wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
[COLOR=#ff0000]>> [/COLOR][COLOR=#ff0000]the error [/COLOR][COLOR=#ff0000]remains the same[/COLOR]



So my attempts have been exhausted. What should I do to upgrade and continue my installation?


TIA

Marcos Nobre

---

### Post by fantab on 2013-06-07
Change the Server to 'Main' and try again.

---

### Post by marconobre on 2013-06-13
I've done that and it did not work.





   Anyone else have any other ideas?

---

### Post by fantab on 2013-06-13
Try:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update

---

