---
title: "script create folder on linux"
date: 2018-07-24
forum: Installation &amp; Upgrades
---

### Post by grofstepe on 2018-07-24
hello
i am sorry for my english
i have installed OGP (open game panel)
i have addons and i need litle help
[http://www.ubc-cs.com/pic1.png](http://www.ubc-cs.com/pic1.png)

this with green its ok is writen a new line on on cstrike/addons/amxmodx/configs/plugins.ini

but i want to create a new folder called fastdl on home path here (second pic)
[http://www.ubc-cs.com/pid2.png](http://www.ubc-cs.com/pid2.png)

but is not created
i halve tried with mkdir fastdl
but its created on cstrike folder inside like this (pic3)
[http://www.ubc-cs.com/pic3.png](http://www.ubc-cs.com/pic3.png)

but i need to create it here (pic4)
[http://www.ubc-cs.com/pic4.png](http://www.ubc-cs.com/pic4.png)

i tried with milion commands but i dont still same i know where is problem bcz on 1 pic the path is cstrike/addons and here in addons install
but how to get back from cstrike folder and which commands i need to crate on homepath or root or how its called

please for help

---

### Post by TheFu on 2018-07-24
Appears you are confused between absolute paths and relative paths.

Absolute paths always begin with a /.   That means the top level directory. Specifying an absolute path is completely independent of the CWD - current working directory. Some examples of absolute paths:
* /etc/
* /home/grofstepe/bin
* /var/log

Relative paths NEVER begin with /. They are relative to the CWD.    Some examples, each is dependent on the CWD, which you can see by running the 'pwd' command:
* if you are in /home/grofstepe, then  ../../ is the same as absolute path /
* if you are in /home/grofstepe, then  bin/ is the same as absolute path /home/grofstepe/bin (can also be called ~/bin if your userid is grofstepe or ~grofstepe/bin if you are any other userid on the system.
* if you are in /home/grofstepe, then  ~/ is the same or /home/grofstepe or $HOME if your userid is grofstepe

Clear as mud?

So, when you are scripting, the pwd/CWD matter of you don't use absolute paths everywhere.  What it appears is happening above, is using relative path when in the wrong CWD for your intentions.

BTW, I don't see any images (which is good). For posting data here, please use a shell and copy/paste text.  Be kind to people who pay internet by the byte.  Thanks.

---

