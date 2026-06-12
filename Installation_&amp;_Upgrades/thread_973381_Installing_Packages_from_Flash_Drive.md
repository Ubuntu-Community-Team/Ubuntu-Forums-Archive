---
title: "Installing Packages from Flash Drive"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by taxirick on 2008-11-06
Hello,
My situation is that because I no longer have internet access at home I need to find out if it is possible to download packages to a flash drive and then take them home. I have to use a public library computer which is windows based on top of that.

 So my questions are as follows, where do I find a public download site to download from first (using a public windows machine) then how do I get Synaptic to let me use those packages to manage my home computer?

 As a side note where do I find the packages I already downloaded with Synaptic so that I can use them to update a secondary machine also with no Interent access. That obviously is not as important but I would like to know where the store is. 

Another side note, I was able to download and install 8.10 on a spare partition of my second machine and all went well exept of course getting restricted extras was not possible w/o internet.
My life without windows is excellent but unfortunately the library forces it on me when I want to collect my email.

Thankyou in advance,
Rick

---

### Post by bigbrovar on 2008-11-07
> Installing Packages from Flash Drive
Hello,
My situation is that because I no longer have internet access at home I need to find out if it is possible to download packages to a flash drive and then take them home. I have to use a public library computer which is windows based on top of that.

i also have that problem .. and being a member of a linux user group in my country here are the things i did to get round it.

> So my questions are as follows, where do I find a public download site to download from first (using a public windows machine) then how do I get Synaptic to let me use those packages to manage my home computer?
 although i have not tried it before but there is a tool called wuddepends which can do just that [http://downloads.sourceforge.net/wubdepends/wubdepends3.exe?modtime=1181483223&big_mirror=0&filesize=6832554]("http://downloads.sourceforge.net/wubdepends/wubdepends3.exe?modtime=1181483223&big_mirror=0&filesize=6832554")  this tool  enables a user to download any package in the ubuntu repositories, its dependencies and every tier of its dependencies dependencies. simily put it allows you to download an ubuntu packages in windows and all the dependencies that the package would need to run. although i have not used the tool before. it should not be too difficult to use and you can sure give it a try.


> As a side note where do I find the packages I already downloaded with Synaptic so that I can use them to update a secondary machine also with no Interent access. That obviously is not as important but I would like to know where the store is.
packages downloaded with synaptic are cached localy on your system and can be found here /var/cache/apt/archives. you can also try this tool called aptoncd. its very easy to install and use. what it does it package all the applications you have ever downloaded on your computer using apt-get or synaptic and put them into a cd/dvd so that there can be added to synaptic and used on another computer. like a tool for creating a cd/dvd repository and can be used to setup ubuntu on offline computers. i used the tool alot in my work a linux user group member since many people in my country dont have internet connection.


one way you can use wubdepends and aptoncd is to use wubdepends on windows to download ubuntu packages then tranfer them to an ubuntu pc. open nautilus as root ```
gksu nautilus
``` and transfer the packages downloaded from windows to /var/cache/apt/archives. after which you can then now use aptoncd to create a dvd/cd repository for other computers. hope i was able to help. if you have another question please let me know cheers


PS aptoncd can be installed from synaptic or using apt-get
```
sudo apt-get install aptoncd
```

---

