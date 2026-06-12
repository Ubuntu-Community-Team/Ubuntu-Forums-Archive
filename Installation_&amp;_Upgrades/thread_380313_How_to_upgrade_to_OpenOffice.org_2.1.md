---
title: "How to upgrade to OpenOffice.org 2.1?"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by kramer65 on 2007-03-09
Hello,

I have ubuntu edgy and now I want to update openoffice.org to version 2.1 If I download the package I need to all this configure and make stuff with which I ran into HUGE problems once before, so I'm trying to avoid that method for now.. Does anybody know how I can install/update openoffice to version 2.1 (preferably in an easy way..:-))

---

### Post by moore.bryan on 2007-03-09
[I]a quick look around seems to say you have to convert the rpm's to deb's...  here's a step-by-step:
[http://bodmas.org/blog/?p=545](http://bodmas.org/blog/?p=545)
[/I]

---

### Post by kramer65 on 2007-03-09
Thanks! I just found [this one]("http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml") as well..

Hopefull I succeed now.. :-)

---

### Post by kramer65 on 2007-03-09
It still doesn't work. I followed [this guide]("http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml"), and I come until the last bit. It does create all these .deb things. Then i copy-paste the last command:  "sudo dpkg -i *deb openoffice.org-debian-menus_2.1-5_all.deb" (while being in that folder) and then it gives me this:

dpkg: regarding openoffice.org-debian-menus_2.1-5_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.1-5_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
dpkg: regarding openoffice.org-debian-menus_2.1-5_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.1-5_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org-debian-menus_2.1-5_all.deb
 openoffice.org-debian-menus_2.1-5_all.deb

Any idea?

---

### Post by mikewhatever on 2007-03-09
> **kramer65 said:**
> Thanks! I just found [this one]("http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml") as well..

Hopefull I succeed now.. :-)

Can you please post back whether or not it worked. Thanks kramer.

---

### Post by moore.bryan on 2007-03-09
*it sounds like you need to uninstall oo first...*

---

### Post by kramer65 on 2007-03-09
ok, and how do I uninstall openoffice? I tried applications > Add/Remove, but that doesn't work.

In the synaptic package manager there are so many results when I search for openoffice that i don't know which one to click..

I found [this]("http://www.bytebot.net/openoffice/faq.html#Installation11"), saying that I need to use ./setup and chose the Remove option. But I don't know where the setup file is of the original (I installed [Ubuntu ultimate]("http://ubuntusoftware.info/ultimate/index.html").. edgy). I did a search for setup

Is there another way to uninstall it?

---

### Post by moore.bryan on 2007-03-09
[I]```
sudo aptitude remove --purge openoffice.org
```
[/I]

---

### Post by mikewhatever on 2007-03-09
Found a thread on OO2.1 with different approaches. By the way, what's in 2.1 that isn't in the present one.

[http://ubuntuforums.org/showthread.php?t=318865&highlight=open+office+2.1](http://ubuntuforums.org/showthread.php?t=318865&highlight=open+office+2.1)

---

### Post by kramer65 on 2007-03-09
I tried that code you gave (sudo aptitude remove --purge openoffice.org) and it sdeems to go ok. 
It says this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
The following packages have been kept back:
  skype 
The following packages will be REMOVED:
  openoffice.org 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 28.7kB will be freed.
Writing extended state information... Done
(Reading database ... 256968 files and directories currently installed.)
Removing openoffice.org ...

then I tried the openoffice.org-debian-menus_2.1-5_all.deb again with that command. same error. Then I just tried to click it. it says:

Error: Confilcts with the installed package 'openoffice.org-core'.

So I tried to uninstall that trough the synaptic package manager but that says:

Could not apply changes! Fix broken packages first.

What packages? What is broken? I can still start openoffice so that apparently didn't uninstall either.. Or maybe partly.. (I already feel new errors coming up..) What now?

@ mikewhatever
in 2.1 it has draw as well. But next to this (now seemingly little detail), it just annoys me so much that you can't just update something easily in linux. i've been spending hours on this now and it frustrates me more and more. I always run from one problem into the next. (see above). Sorry for saying this, but with windows I could just download the stuff and install. If I wanted to get rid of it i just went to control panel where I could remove everything.. I really hope i can finally fix this. If not I just leave it. i am getting really close to the kramer65WHATEVER point.. ;-)

---

### Post by moore.bryan on 2007-03-09
[I]well, it's a problem since you're trying to install something not in the repos... then it would be easy.

if synaptic's giving you an issue, once again use the command line
```
sudo aptitude remove --purge openoffice.org-core
```
[/I]

---

### Post by moore.bryan on 2007-03-09
a*re you aware 2.2.13 is the latest release?  are you trying to install an old one?*

---

### Post by kramer65 on 2007-03-09
ok, when I do "sudo aptitude remove --purge openoffice.org-core" it does some stuff and then:

Resolving dependencies...
The following actions will resolve these dependencies:

Upgrade the following packages:
openoffice.org-base [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
openoffice.org-calc [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
openoffice.org-core [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
openoffice.org-draw [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
openoffice.org-evolution [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
openoffice.org-gnome [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
openoffice.org-gtk [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
openoffice.org-impress [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
openoffice.org-math [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
openoffice.org-writer [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]
python-uno [2.0.4-0ubuntu2 (edgy, now) -> 2.0.4-0ubuntu4 (edgy-updates)]

Score is -499

Accept this solution? [Y/n/q/?] 

I just said a couple times "n" and then I just said "q". So it stopped resolving all dependencies (ot said). 

But openoffice is still installed. I can still start it. When clicking the openoffice.org-debian-menus_2.1-5_all.deb file it still says that it conflicts with openoffice.org-core...

What now..?

ps. 2.2.13? if I go to [www.openoffice.org](www.openoffice.org) I see the current download is 2.1? Well anyway. 2.1 would be enough for now.. :(

---

### Post by konungursvia on 2007-03-09
Damn, why can't it update itself like Opera?

---

### Post by moore.bryan on 2007-03-09
[I]i see where i got confused!  the ooo website has 2.1 as the version, but the button read >2.2.13... weird.  anyway... i would install from the source then.  i know you said it didn't work in the past, but it might be the best way.  besides, it'll give some feedback about what might be wrong.  download the file and
```
tar -xvzf OOo_2.1.0_LinuxIntel_install_en-US.tar.gz
cd OOo_2.1.0_LinuxIntel_install_en-US
./configure
make
sudo make install
```
if you're missing anything, the config will tell you.  post that and we can go from there...
[/I]

---

### Post by kramer65 on 2007-03-09
If I do that I don't get the folder OOo_2.1.0_LinuxIntel_install_en-US as you would expect but it creates the folder OOE680_m6_native_packed-1_en-US.9095 In there are only 3 folders of which one is RPMS. So no config file. From there we get to [this]("http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml") again. (which I tried before). And from there we get back to the fact that openoffice is alreay installed.

I would really like to thank you but I am really really tired. My computer should work for me, not the other way around. It's ok. I give up... the computer won...

Thank you very much for your efforts!

---

### Post by mikewhatever on 2007-03-09
> n 2.1 it has draw as well. But next to this (now seemingly little detail), it just annoys me so much that you can't just update something easily in linux. i've been spending hours on this now and it frustrates me more and more. I always run from one problem into the next. (see above). Sorry for saying this, but with windows I could just download the stuff and install. If I wanted to get rid of it i just went to control panel where I could remove everything.. I really hope i can finally fix this. If not I just leave it. i am getting really close to the kramer65WHATEVER point.

You are right here. It is a lot easier to install software in Windows, which is an advantage and also a drawback. I have not even considered updating OO, since it looked too advanced for my level of experience and since there seemed to be no urgent need to. Hope your 2.04 version is still ok and sorry it did not work :)

---

### Post by moore.bryan on 2007-03-10
> **kramer65 said:**
> If I do that I don't get the folder OOo_2.1.0_LinuxIntel_install_en-US as you would expect but it creates the folder OOE680_m6_native_packed-1_en-US.9095 In there are only 3 folders of which one is RPMS. So no config file. From there we get to [this]("http://news.softpedia.com/news/Install-OpenOffice-org-2-1-in-Ubuntu-Kubuntu-46182.shtml") again. (which I tried before). And from there we get back to the fact that openoffice is alreay installed.

I would really like to thank you but I am really really tired. My computer should work for me, not the other way around. It's ok. I give up... the computer won...

Thank you very much for your efforts!
[I]alright... i downloaded the tar.gz to see what was going-on and it turned out the same way for me.  it looks like ooo only has rpm install packages.  that's not the end of the world, though.  you can install alien, an rpm package "changer," for debian systems... it's even in the repos.
```
sudo aptitude install --with-recommends alien
```then, although it's a little time consuming, all you have to do is install each of the rpm's in the RPM folder.  
```
sudo alien -i NAMEOFTHE.rpm
```

just as a side-note, why isn't the ooo in the repos good enough?  why so "cutting-edge?"  ;-)
[/I]

---

