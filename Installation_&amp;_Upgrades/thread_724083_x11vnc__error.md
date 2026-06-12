---
title: "x11vnc  error"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by rasco on 2008-03-14
I installed x11vnc :
sudo apt-get install x11vnc

then run the comand :
 x11vnc -forever -usepw -httpdir /usr/share/vnc-java -httpport 5800


i get the following error any ideas?>

14/03/2008 08:23:19 httpProcessInput: open: No such file or directory
14/03/2008 08:23:25 httpd: get '' for 129.42.208.182
14/03/2008 08:23:25 httpd: defaulting to 'index.vnc'
14/03/2008 08:23:25 httpProcessInput: open: No such file or directory

The reason i installed x11vnc is cause i can't get the normal remote desktop to start service.
everytime i log off there is no conection

---

### Post by krunge on 2008-03-14
> **rasco said:**
> 

then run the comand :
 x11vnc -forever -usepw -httpdir /usr/share/vnc-java -httpport 5800

14/03/2008 08:23:19 httpProcessInput: open: No such file or directory
14/03/2008 08:23:25 httpd: get '' for 129.42.208.182
14/03/2008 08:23:25 httpd: defaulting to 'index.vnc'
14/03/2008 08:23:25 httpProcessInput: open: No such file or directory

What does
```
ls -l /usr/share/vnc-java 
```
reveal?  Doe the directory exist?  Does it have the files "index.vnc" and "VncViewer.jar" in it?

---

