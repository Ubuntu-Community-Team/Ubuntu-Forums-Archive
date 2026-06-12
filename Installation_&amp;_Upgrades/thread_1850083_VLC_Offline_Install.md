---
title: "VLC Offline Install"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by moniker127 on 2011-09-25
Howdy folks. Heres my situation:

I have two computers that I can't hook up in any way, one has internet access, and is running windows, the other has no internet access and is running ubuntu 10.10, which was recently installed directly from an ubuntu dvd. 

I'm trying to install VLC media player on the computer with no internet access via a USB thumb drive, but I'm having a problem in that It seems impossible to get all he packages and dependencies manually. I've been downloading the .debs from packages.ubuntu.com for VLC, but every time I download one package, it tells me I have unsatisified dependencies for that package, and, looking over it, i'm probably going to have to spend hours downloading hundreds of seperate files in order to get them all.

My question is- is there some easier way to install VLC on the offline computer? I'd love just a downloadable installer for VLC on ubuntu, does such a thing exist? It doesn't seem right that it is such a complicated process to install anything if your ubuntu machine doesn't have internet access.


Here is what i've tried so far:
-Keryx ([http://keryxproject.org/](http://keryxproject.org/)) This failed, when I tried to execute it on the ubuntu box, it asked me to associate a program with executable files. It wasn't a .exe I clicked on, it looked like a normal linux application. It had no extension.

-A synaptic package download script as per instructions on [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) .
This did not work, when I generated the script, it created an empty script file that I believe called up the terminal and exited.

---

### Post by zvacet on 2011-09-25
In com with internet make folder and name that folder as you wish ( player maybe).From [this]("http://packages.ubuntu.com/maverick/vlc") page download all packages marked with red ball and you can also download green and blue ones.After that download vlc package on the bottom of the page( be sure you download right architecture).Put all that packages in previously made folder (player) and put folder on stick and transfer it to Ubuntu comp.Put folder in home directory and after that run in terminal

```
cd player
sudo dpkg -i *deb
```

---

### Post by tgalati4 on 2011-09-26
Find a way to hook the computer up to the internet.

---

### Post by oldos2er on 2011-09-26
> **moniker127 said:**
> Here is what i've tried so far:
-Keryx ([http://keryxproject.org/](http://keryxproject.org/)) This failed, when I tried to execute it on the ubuntu box, it asked me to associate a program with executable files. It wasn't a .exe I clicked on, it looked like a normal linux application. It had no extension.

Instead of clicking on the Keryx app, try running it in a terminal.

---

### Post by plant pot on 2011-09-28
I had a lot of trouble. Then I wrote up my solution. 

 "Keryx v1.0 Ubuntu 11.04 mini-guide --it DOES work"
 [http://keryxproject.org/forums/index.php?topic=130&limit=1#p556](http://keryxproject.org/forums/index.php?topic=130&limit=1#p556)

 It looks to me like my link will directly solve your problem.
--

---

### Post by moniker127 on 2011-10-01
Keryx seemed like too much of a problem. I'll post what I did for those who run into this on google later:


-I went to packages.ubuntu.com on my online computer, downloaded the packages for vlc/wine/whatever else I needed

-I copied them over to the ubuntu box, put them into a folder and used sudo dpkg -i *.deb like that one guy suggested

-I copied the terminal's output into text editor, ran a search for "is not installed", and deleted all the lines that didnt contain that phrase.

-I deleted everything but the names of the packages on the lines, and replaced them so that they were links, then made it into a page with links to the package download page ([http://packages.ubuntu.com/maverick/i386/packagename/download](http://packages.ubuntu.com/maverick/i386/packagename/download)).

-I then copied that html file over to the online computer, clicked all the links, and copied the debs back.

-It took a few times of doing this to get all the dependencies, but it was the lowest hassle method that was direct enough and hacky enough for my liking.

---

