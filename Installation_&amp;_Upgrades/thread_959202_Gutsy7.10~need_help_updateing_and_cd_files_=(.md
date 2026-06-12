---
title: "Gutsy7.10~need help updateing and cd files =("
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by KEE on 2008-10-26
ok i want teamspeak found in respositories but the java found there is outdated so i update in terminal and get this
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
```
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
then someone tolds me too 

```
$sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

now i get this
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
```
Install these packages without verification [y/N]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free medibuntu-keyring 2008.04.19 [3494B]
Fetched 3494B in 7s (438B/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 141894 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.19_all.deb) ...
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation. You will need to go download one of the
archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


i dont know how to cd any more, can someone help and explain that. i thought did with wow, but i dont know how to install those files of java =( please help and thank you

---

### Post by Partyboi2 on 2008-10-29
Follow what is says, go to
 [http://java.sun.com/javase/downloads/and](http://java.sun.com/javase/downloads/and) download the java se 6 Documentation, then open a terminal and  change to where the downloaded file is so if its your desktop then
```
cd ~/Desktop
```
change the file permission to root
```
 sudo chown root:root jdk-6u10-docs.zip
```
then move it to /tmp
```
sudo cp jdk-6u10-docs.zip /tmp
``` If the jdk-6u10-docs.zip file does not work then you can download the jdk-6-doc.zip from [[COLOR=Blue]here[/COLOR]]("http://www.filewatcher.com/m/jdk-6-doc.zip.54898268.0.0.html") and follow the same process.

---

### Post by KEE on 2008-11-14
> **Partyboi2 said:**
> Follow what is says, go to
 [http://java.sun.com/javase/downloads/and](http://java.sun.com/javase/downloads/and) download the java se 6 Documentation, then open a terminal and  change to where the downloaded file is so if its your desktop then
```
cd ~/Desktop
```
change the file permission to root
```
 sudo chown root:root jdk-6u10-docs.zip
```
then move it to /tmp
```
sudo cp jdk-6u10-docs.zip /tmp
``` If the jdk-6u10-docs.zip file does not work then you can download the jdk-6-doc.zip from [[COLOR=Blue]here[/COLOR]]("http://www.filewatcher.com/m/jdk-6-doc.zip.54898268.0.0.html") and follow the same process.
```
$  sudo chown root:root jdk-6u10-docs.zip
chown: cannot access `jdk-6u10-docs.zip': No such file or directory
```

thats what i get now ...i tried the other the 2008 jdk-6-doc.zip and still nothing...I dont know how it worked for you?!??

---

### Post by KEE on 2008-11-14
> **Partyboi2 said:**
> Follow what is says, go to
 [http://java.sun.com/javase/downloads/and](http://java.sun.com/javase/downloads/and) download the java se 6 Documentation, then open a terminal and  change to where the downloaded file is so if its your desktop then
```
cd ~/Desktop
```
change the file permission to root
```
 sudo chown root:root jdk-6u10-docs.zip
```
then move it to /tmp
```
sudo cp jdk-6u10-docs.zip /tmp
``` If the jdk-6u10-docs.zip file does not work then you can download the jdk-6-doc.zip from [[COLOR=Blue]here[/COLOR]]("http://www.filewatcher.com/m/jdk-6-doc.zip.54898268.0.0.html") and follow the same process.
LOL i tried the jdk-6-doc.zip and i get this "permission denied" ...i think you were close though  ```
$sudo chown root:root jdk-6-doc.zip
```
```
$sudo cp jdk-6-doc.zip /tmp
```
```
$ls -l
```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
total 53672
-rw-r--r-- 1 root root 54898268 2008-10-31 11:14 jdk-6-doc.zip
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

 ```
$./jdk-6-doc.zip
```
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
./jdk-6-doc.zip: Permission denied
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

---

### Post by Partyboi2 on 2008-11-15
Once you have copied over the file to the tmp directory dont use 
```
./jdk-6-doc.zip
``` instead do
```
sudo apt-get update && sudo apt-get install medibuntu-keyring 
```

---

### Post by KEE on 2008-11-15
thanks man =D

---

