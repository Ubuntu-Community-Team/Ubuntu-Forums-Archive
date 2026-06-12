---
title: "ubuntu 10.10 /home encryption question"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by kuco87 on 2011-05-23
hey :)
i reinstalled 10.10/32bit (11.04 causes too many problems atm) and decided to encrypt my /home directory (no /home partition!) during the process. usually - when the installer finishes and ubuntu starts the first time - there will be a "popup" which generates an encryption-hash. i guess i closed that windows in a reflex or it didnt even show for some reason.

i'm not even sure if my /home directory is encrypted now. how can i check ? 
if it is...what is my hash ?
if it isnt...is there any way to encrypt /home without deleting and recreating my user account ? 

thanks in advance :)

---

### Post by nuffink666 on 2011-05-23
try this 
 
[http://ubuntu.shapado.com/questions/how-to-encrypt-home-directory-after-install](http://ubuntu.shapado.com/questions/how-to-encrypt-home-directory-after-install)

---

### Post by kuco87 on 2011-05-23
Thanks for helping :)

Once i run ecryptfs-setup-private i'll get this output :

mkdir: kann Verzeichnis &#8222;/home/kuco87/.ecryptfs&#8220; nicht anlegen: Die Datei existiert bereits
ERROR:  wrapped-passphrase file already exists, use --force to overwrite.

the first line should be something like this in english :
mkdir : cant create directory  &#8222;/home/kuco87/.ecryptfs. file already exists.

so i assume, my /home directory is already encrypted. i never chose any password or hash though. how can i see my hash/password ? i want to write it down in case, i have manually recover my data some day.

/edit

Ok, using 
[B]sudo ecryptfs-unwrap-passphrase  wrapped-passphrase
[/B]
I got my Passphrase. But is encryption really in use ? How can i check ? :3 thanks

---

