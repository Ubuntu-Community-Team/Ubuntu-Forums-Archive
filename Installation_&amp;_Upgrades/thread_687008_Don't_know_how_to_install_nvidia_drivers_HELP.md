---
title: "Don't know how to install nvidia drivers??? HELP"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by hydrochetta on 2008-02-03
I do not have a clue on how to install any drivers on Linux. I am new to Linux, I was introduced to it by one of my teachers, I went to nvidia.com and found my driver update for my 7600 gt. I downloaded the file and it was called "NVIDIA-Linux-x86-169.09-pkg1.run". I double clicked the file and got this, "could not open the file /home/hydro/deskto...Linux-x86-169.09-pkg1.run." It also says, "gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a character coding from the menu and try again." It is already set on Current Locale (UTF-8 ) so i would figure it would be the other one that worked. Well that's not the case. The other one is called Western (ISO-8859-15). I have tried to find forums through searches on google, I have found some information but being a newbie that has never seen Linux before  I am very confused. If someone could explain the process to me as if I were a two year old, I'd greatly appreciate it. Thanks.

---

### Post by hydrochetta on 2008-02-03
I forgot to mention that i also get this message when I try to run this program called Envy, "envy_0.9.10-0ubuntu2_all.deb". That is the file name. But anywho the message I get is, "Failed to run gdebi-gtk '--non-interactive' '/home/hydro/desktop/envy_0.9.10-0ubuntu2_all.deb as user root" Mind you, by this point I am completely confused because on the forum I read this program envy makes the installation of your nvidia driver easier, and it doesn't even install? Well it also says, "The unerlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator." Now being used to Microsoft I'm used to seeing problems like this. I don't understand Linux but I have a feeling I'm going to have to find where this (sudo) program lies and remove it or disable it. I have no knowledge in Linux so i don;t know where to start. I will continue to post other factors that I think might affect my situation.

---

### Post by Orange Juice on 2008-02-03
A program called [Automatix2]("http://www.getautomatix.com/") will do that for you. I don't know how to explain it very well, but there's this list of programs within the program that are really popular. All you have to do is double click one of the popular programs, and it will automatically install it for you. They have Nvidia drivers built into it as well as many other programs. :)

---

### Post by PmDematagoda on 2008-02-03
This is what you need to do to install the Nvidia driver:-

1) Kill the GUI using:-
```
sudo /etc/initd/gdm stop
```

2) Install the required prerequisites for the Nvidia driver installer using:-
```
sudo apt-get install build-essential
```

3) Navigate to where the Nvidia driver file is using the following commands:-
```
cd
```
to change directory
and
```
ls
```
to list the files of a directory

4) After you find the file, execute it using:-
```
sudo sh nameoffile
```

5) After the installation is successful, reconfigure the X-Server using:-
```
sudo dpkg-reconfigure xserver-xorg
```
select the driver as "nvidia" and any other options you might want.

6) Restart the GUI using:-
```
sudo /etc/init.d/gdm start
```

---

### Post by PmDematagoda on 2008-02-03
> **Orange Juice said:**
> A program called [Automatix2]("http://www.getautomatix.com/") will do that for you. I don't know how to explain it very well, but there's this list of programs within the program that are really popular. All you have to do is double click one of the popular programs, and it will automatically install it for you. They have Nvidia drivers built into it as well as many other programs. :)

A word of warning, Automatix still does not work well with Ubuntu and is likely to cause problems with the OS, so only use that as a last resort.

---

### Post by hydrochetta on 2008-02-03
I have another post up which mentions Sudo, I am now thinking this is the key thing thats stopping me from installing drivers. If someone could explain to me what it is, it's purpose and how to disable, i would appreciate it. Thanks again.

---

### Post by PmDematagoda on 2008-02-03
I recommend this [guide]("https://wiki.ubuntu.com/RootSudo") which explains what you need to know.

---

### Post by aysiu on 2008-02-03
> **hydrochetta said:**
> I have another post up which mentions Sudo, I am now thinking this is the key thing thats stopping me from installing drivers. If someone could explain to me what it is, it's purpose and how to disable, i would appreciate it. Thanks again.
Disabling sudo will not help you get the Nvidia driver installed. I don't know where you got that idea.

Try this:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

It's a step-by-step guide to install Nvidia drivers, and it's screenshot-driven (no terminal use needed).

---

