---
title: "I want my old Skype back"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by orhashahar on 2012-12-11
I love having Ubuntu but sometimes is can be so complected...
My Ubuntu automatically upgraded my Skype to 4.1 few month ago and this time I am not so happy about that... I want my old Skype back!
I don't know exactly the number of the old version but the only thing i really remember from it (and miss) is the option to not see your own video (I don't know what about you but I keep staring at myself instead of in the person i'am talking with)

So please: How do I do that?

---

### Post by pqwoerituytrueiwoq on 2012-12-11
you may have the old deb file in /var/cache/apt/archives/
```
ls /var/cache/apt/archives/ | grep skype
```
if your old version is in there 
```
cp /var/cache/apt/archives/mydeb.deb ~/Downloads/
```
then uninstall skype and install the deb in your downloads folder

---

### Post by orhashahar on 2012-12-11
Sorry, but I am new at this. I promise to understand fast if you can explain a bit slower....

---

### Post by pqwoerituytrueiwoq on 2012-12-11
When you install stuff a deb file is downloaded and stored in /var/cache/apt/archives/ the command i gave you will show you every deb file in there with skype in the name, by looking at the file name you can tell if what version it is
assuming the old deb is still there you can copy that deb file to somewhere permanent with the second command (edit the mydeb.deb part as needed)
then you can uninstall skype and install the old one from the deb you just copied
then be careful not to upgrade skype (google lock package synaptic)

---

### Post by orhashahar on 2012-12-12
I am sorry but i still did not succeed... I opened the first code and there are so many .deb files there... Which file should i choose? and What do you mean with "somewhere permanent"?  

Thank you so much for your quick help and patience :)
Happy Hanukkah

---

### Post by RicardoE on 2012-12-12
Ok,

open a terminal, and run:

```
sudo apt-get remove skype
```

and then download one of the following:

for 32 bits:
[http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_i386.deb](http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_i386.deb)

for 64 bits:
[http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_amd64.deb](http://download.skype.com/linux/skype-ubuntu_2.2.0.35-1_amd64.deb)

then just double click the corresponding one, and it will install the old skype again.

*Just notice that, you wont be able to add contacts anymore, and it will halt and dissconect for no reason...*

---

### Post by orhashahar on 2012-12-12
Sorry, did all you told me to do and it's still doesn't work :)
Thank you any way

---

