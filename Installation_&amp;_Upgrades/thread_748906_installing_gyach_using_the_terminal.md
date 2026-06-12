---
title: "installing gyach using the terminal"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by girlleo19 on 2008-04-07
does anybody here know how to install gyach using the terminal?? can someone help me cause i can't use my webcams when I talk to my friends..

---

### Post by Partyboi2 on 2008-04-07
one way to install is to covert the rpm's to deb packages then install the deb packages. Here is how-to
First install alien
```
sudo apt-get install alien
```then download the rpm packages to Desktop
[Gyach-Enhanced-pYVoiceChat-1.0.7-1-i586.rpm]("http://downloads.sourceforge.net/phpaint/Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm?modtime=1112610599&big_mirror=0")
[Gyach-Enhanced-Encryption-Plugins-0.2-1.i586.rpm]("http://downloads.sourceforge.net/phpaint/Gyach-Enhanced-Encryption-Plugins-0.2-1.i586.rpm?modtime=1082975502&big_mirror=0")
[Gyach-Enhanced-Media-Package-0.2-1.i586.rpm]("http://downloads.sourceforge.net/phpaint/Gyach-Enhanced-Media-Package-0.2-1.i586.rpm?modtime=1112610579&big_mirror=0")
[Gyach-Enhanced-XMMS-Plugin-0.4-1.i586.rpm]("http://downloads.sourceforge.net/phpaint/Gyach-Enhanced-XMMS-Plugin-0.4-1.i586.rpm?modtime=1101724353&big_mirror=0")
Then change directory to Desktop
```
cd Desktop
```then convert rpm to deb packages
```
sudo alien -d Gyach-Enhanced-pYVoiceChat-1.0.7-1.i586.rpm Gyach-Enhanced-Encryption-Plugins-0.2-1.i586.rpm Gyach-Enhanced-Media-Package-0.2-1.i586.rpm  Gyach-Enhanced-XMMS-Plugin-0.4-1.i586.rpm
```then install packages 
```
sudo dpkg -i  gyach-enhanced-pyvoicechat_1.0.7-2_i386.deb
``````
sudo dpkg -i gyach-enhanced-encryption-plugins_0.2-2_i386.deb
``````
sudo dpkg -i gyach-enhanced-media-package_0.2-2_i386.deb
``````
sudo dpkg -i gyach-enhanced-xmms-plugin_0.4-2_i386.deb
```then to start type
```
gyach
```

---

### Post by girlleo19 on 2008-04-08
i st ill couldn't work it out...hmm..

---

### Post by Partyboi2 on 2008-04-08
Where are you getting stuck?

---

### Post by girlleo19 on 2008-04-08
it asks me for a cd??

---

### Post by TenPlus1 on 2008-04-08
Here is the actual gusty .db file for GyachE:

[http://downloads.sourceforge.net/gyachi/gyachi_1.1.0-1_i386_gutsy.deb?modtime=1194233326&big_mirror=0](http://downloads.sourceforge.net/gyachi/gyachi_1.1.0-1_i386_gutsy.deb?modtime=1194233326&big_mirror=0)

Enjoy... works fine here...

---

### Post by Partyboi2 on 2008-04-08
Thanks TenPlus1 for that! Saves converting rpm's :)


> girlleo19 -it asks me for a cd??
 You may need to untick the cdrom box in Software Sources to install other packages you may want in the future.
Open up Software Sources (System>Admin>Software Sources) and on the first tab  untick "installable from cdrom/DVD" But TenPlus1 has the better answer for installing gyach so take his advice.

---

### Post by girlleo19 on 2008-04-09
but when i downloaded gych in that link it didin't work either..there's an errror message

---

### Post by Partyboi2 on 2008-04-09
What is the error message you are getting?

---

### Post by loell on 2008-04-10
snip---

---

