---
title: "software index is broken"
date: 2014-02-22
forum: Installation &amp; Upgrades
---

### Post by Peace_Harmony on 2014-02-22
[SIZE=2][FONT=arial]Hello, I am new to Ubuntu.

I am trying to update my software, but I cannot because the software index is broken. 

Here is the error message: 
[/FONT][/SIZE][SIZE=2][FONT=arial]   	 	 	
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[COLOR=#000000][FONT=times new roman][SIZE=2][FONT=arial]I have located the broken packages in Synaptic Package Manager, but I am not sure how to fix them.

Can anyone help me resolve this issue?

-Peace
[/FONT][/SIZE]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-02-22
Peace_Harmony; Hi ! Welcome to the forum .

Many times repairing the package management system is fairly straight forward, once the error condition is known.
Post back the output - between code tags - of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
for our inspection. -> advisement.
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

so a tale
[INDENT][INDENT]is told
[/INDENT][/INDENT]

---

