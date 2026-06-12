---
title: "How to find program locations?"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-11
If I would like to find where synaptic is located what command should I use??

---

### Post by nemin on 2005-04-11
[QUOTE=bigblop]If I would like to find where synaptic is located what command should I use??[/QUOTE]
Do you mean this?
```
$ which synaptic
/usr/sbin/synaptic

```

---

### Post by dusu on 2005-04-11
Hi,

one way to know what is executed when you run synaptic, is to use :
```
which synaptic
``` 
This should give you the answer : /usr/sbin/synaptic

Another command which is useful is locate : 
```
locate synaptic
``` 
But this will give you a huge list of file whose name contains 'synaptic'.
Before using locate, you should update the data base (if you have modified lots of things recently) by using :
```
sudo updatedb
``` 

I hope you have your answer !

---

### Post by Glanz on 2005-04-11
[QUOTE=bigblop]If I would like to find where synaptic is located what command should I use??[/QUOTE]
 By far the most simple way to find an application is to open a terminal and type "type"...

wtf@wtf:~ $ type synaptic
synaptic is /usr/sbin/synaptic


That will give you the location....., or if the app doesn't exist, isn't installed, you will get an answer like this:

wtf@wtf:~ $ type WTF
bash: type: WTF: not found

---

