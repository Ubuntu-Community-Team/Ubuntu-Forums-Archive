---
title: "apt-get vs rpm"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by LT72884 on 2008-02-14
Ok i have made the switch from fedora to ubuntu. i couldnt stand fedora because it was never stable. All the new drivers would NOT detect my hardware. It couldnt read my GPU or my wireless card. So i needed something more stable and a friend who uses Linux every day for his job told me to use nothing but ubuntu. Well i got really used to using rpm and yum. The one thing i really liked about rpm was the fact that i could list what rpms were installed and what not. For example i could go to a terminal and type:

rpm -qa mad

and it would search the rpm database for anything that started with mad that was installed on my system. Does apt get have that function? can i see what packages i have installed and where they reside? 

Thanks

Matt

---

### Post by Rocket2DMn on 2008-02-14
Synaptic is the GUI for apt-get, it's much easier to search in there (System->Administration->Synaptic Package Manager), but with apt-get, you would just run
```
sudo apt-get install *programnae*
``` to download and install from the repositories using the temrinal - it will build the necessary dependencies.
If you have a .deb file (essentially a debian version of an rpm), you can install with
```
sudo dpkg -i *filename.deb*
``` as long as the dependencies are present.  apt-get is the suggested method, though, since it uses Ubuntu's massive repositories.

---

### Post by LT72884 on 2008-02-14
> **Rocket2DMn said:**
> Synaptic is the GUI for apt-get, it's much easier to search in there (System->Administration->Synaptic Package Manager), but with apt-get, you would just run
```
sudo apt-get install *programnae*
``` to download and install from the repositories using the temrinal - it will build the necessary dependencies.
If you have a .deb file (essentially a debian version of an rpm), you can install with
```
sudo dpkg -i *filename.deb*
``` as long as the dependencies are present.  apt-get is the suggested method, though, since it uses Ubuntu's massive repositories.


i thought that 

apt-get install

installed a program. I want it to list programs all ready installed or packages all ready installed.

thanx

---

### Post by dje on 2008-02-14
Try this:
```
dpkg -l mad
```
Hope that helps

dje

---

### Post by Rocket2DMn on 2008-02-14
Try
```
dpkg --list | less
```
Or output the list to a file in your home directory
```
dpkg --list > packge_list.txt
```

---

### Post by LT72884 on 2008-02-14
> **dje said:**
> Try this:
```
dpkg -l mad
```
Hope that helps

dje

it didnt like that command. i tired

dpkg -l n

no packages matching n found.

im trying to get it to list any package that starts with n.

---

### Post by Ardrias on 2008-02-14
Personally I use ```
sudo apt-cache search packagename
``` to find new packages, and ```
sudo apt-cache show packagename
``` to view info about it.

---

### Post by hyperair on 2008-02-14
apt-get is comparable to yum, dpkg to rpm, in terms of purpose anyway. If you compare apt-get to rpm, something's obvioulsly not going to satisfy you then.

The Ubuntu equivalent of the rpm command you posted is as shown by dje. Basically, whatever functionality you used before in rpm, you should look for in dpkg, and functionality used in yum should be looked for in apt-get.

---

### Post by LT72884 on 2008-02-14
> **hyperair said:**
> apt-get is comparable to yum, dpkg to rpm, in terms of purpose anyway. If you compare apt-get to rpm, something's obvioulsly not going to satisfy you then.

The Ubuntu equivalent of the rpm command you posted is as shown by dje. Basically, whatever functionality you used before in rpm, you should look for in dpkg, and functionality used in yum should be looked for in apt-get.
yeah because i liked how the command:

rpm -qa n

would list anything that started with n. it made it easy so i did not have to memorize all the packages by name. I tired a dpkg -l adobe and it said no matches found for adobe when i know i hav adobe reader. Also dpkg -l will list ALL packages but no adobe is listed.

---

### Post by Rocket2DMn on 2008-02-14
You can search in synaptic for packages, since the packages have descriptions, you don't usually need to know the exact package name.  If you search for "adobe", you will probably find what you're looking for.

---

### Post by dje on 2008-02-14
Sorry i think i made a mistake in that first command try:
```
dpkg -l 'n*'
```

dje

---

### Post by LT72884 on 2008-02-14
> **Rocket2DMn said:**
> You can search in synaptic for packages, since the packages have descriptions, you don't usually need to know the exact package name.  If you search for "adobe", you will probably find what you're looking for.


lol true. I have done it that way many times but i have to find a command line way of doing it. My professor says i need to spend more time in CLI than in a GUI. My RCHT class requires me to know command line and GUI

---

### Post by LT72884 on 2008-02-14
> **dje said:**
> Sorry i think i made a mistake in that first command try:
```
dpkg -l 'n*'
```

dje

OMG OMG i love you man. thats what i was looking for. i forgot what the 'n*' is. are those expressions or regular expressions or wildcards. so much stuff to learn about linux.

---

### Post by LT72884 on 2008-02-14
Ok now onto the next part of apt-get. adding repos using the command line and gui.

i owe you guys lunch. somehow i will find a way.lol

---

### Post by dje on 2008-02-14
You're very welcome ;)
An asterisk is a wildcard

dje

---

### Post by LT72884 on 2008-02-14
im gonna recruite people to these forums

---

### Post by jaytek13 on 2008-02-14
> **LT72884 said:**
> it didnt like that command. i tired

dpkg -l n

no packages matching n found.

im trying to get it to list any package that starts with n.


Try using a wildcard:
```
dpkg -l n*
```

Whoops... guess I'm a little late.

---

### Post by dje on 2008-02-14
**Adding software repos from command line:**
Completely:
```
sudo vim /etc/apt/sources.list
```
Using graphical text editor:
```
sudo gedit /etc/apt/sources.list
```

**Adding software repos from GUI:**
Go to System >> Administration >> Software sources
You can add repos from there

Hope that helps you
dje

---

### Post by LT72884 on 2008-02-14
> **dje said:**
> **Adding software repos from command line:**
Completely:
```
sudo vim /etc/apt/sources.list
```
Using graphical text editor:
```
sudo gedit /etc/apt/sources.list
```

**Adding software repos from GUI:**
Go to System >> Administration >> Software sources
You can add repos from there

Hope that helps you
dje


yup it does. thanx much man.

now if i can get kismet to work i would be happier. LOL

---

### Post by dje on 2008-02-14
Again you're welcome
Sorry but I don't know about kismet so can't help you, I'm sure if you start a new thread you will get all the answers you need

dje

---

