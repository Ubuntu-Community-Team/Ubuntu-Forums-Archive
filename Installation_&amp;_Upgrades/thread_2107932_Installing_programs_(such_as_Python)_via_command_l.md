---
title: "Installing programs (such as Python) via command line"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by Dymphy on 2013-01-23
Hi,

I'm fairly new to the world of Ubuntu (have my own laptop with Ubuntu since late september, only used the graphic interface so far) and working with the command line can sometimes drive me mad.

I want to install Python versio 3.3, from this page [http://www.python.org/download/releases/3.3.0/](http://www.python.org/download/releases/3.3.0/) and I was thinking to install one of the tar balls listed at the bottom of the page via the command line.

My two questions are as follows:
- Am I installing the right version of python,

and more importantly
- When I use the command line, I've been taught to use 

```
sudo apt get
```Is this right? I also have problems to list the right directory (the main problem with installing. I think the right directory is /home/goossens/Documenten, where 'goossens' is the name of my laptop and 'Documenten' is dutch for 'Documents', but I'm not sure. Can anyone help me?

---

### Post by dino99 on 2013-01-23
stay with the gui for ease : nautilus, synaptic

---

### Post by ibjsb4 on 2013-01-23
Apt-get commands

[https://help.ubuntu.com/community/AptGet/Howto#Installation_commands](https://help.ubuntu.com/community/AptGet/Howto#Installation_commands)

---

### Post by omeomi on 2013-01-23
> **Dymphy said:**
> I also have problems to list the right directory (the main problem with installing. I think the right directory is /home/goossens/Documenten, where 'goossens' is the name of my laptop and 'Documenten' is dutch for 'Documents', but I'm not sure. Can anyone help me?

To get to the right directory in terminal type
```
cd /home/goossens/Documenten
```
Then you can type 
```
ls
```
to list the contents of that directory.

To install the version of Python from that website you can't use apt-get because it is source code. You have to compile it manually, which is a bit more complicated.

---

