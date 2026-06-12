---
title: "installting packages from cd-rom with dependencies"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by it_suppport on 2008-10-22
Dear All,

I'm Newbee to Ubuntu & trying to configure the Ubuntu 8.04 LTS server.
How should I manually install some packages with their dependencies from the cd-rom?

I want to install & configure some packages in Ubuntu manually, for which I were searching on the net but couldn't get the satisfactory answer for the same. I tried using the site server guide but didn't helped me much. 

I tried using **# apt-get install <package>** but didn't helped me. 
I also tried the **dpkg -i ** package.deb to install, but it fails due to some or the other dependencies failure.

Can someone help me / tell me the procedure to install any package from the cd-rom?
Also can you tell me, where will I get the complete package(including dependencies) in deb format.
Its not there on packages.ubuntu.com site, as I've checked it.

---

### Post by mikewhatever on 2008-10-22
Can you please clarify why apt-get install <package> didn't work. What was wrong? Did you get any errors?

---

### Post by it_suppport on 2008-10-23
Mike,

thanks for the reply.
I've newly installed the Ubuntu server & want to install verious packages mannually. Whenever I tries to install any package with **# apt-get install <package_name>**, it says Couldn't find the package. Although the package is available on the Ubuntu cd.

apt.conf & souuce.list files are the default one on there location /etc/apt/

If I tries to install the same package with # dpkg -i package.deb, then it asks me for one or the other dependencies. & it goes on for some other.

---

### Post by robert shearer on 2008-10-23
Once  Ubuntu has been installed it usually does not list the install cd as a source.
I think it assumes you are going to download the latest package information and install up to date packages.

You can install from the cd by adding it as a repository.

In a terminal type

```
sudo apt-cdrom add
```

you will be prompted to insert your cd and the package info will be added to the sources list.

then try to install the package/s

```
sudo apt-get install "package name'
```

However, the packages on the cd are likely to be out of date and as soon as you update ,from the net, the package information you will be prompted to update and have to download them anyway.

Don't forget to remove the cd from the sources list once you have the packages you want installed.

Edit.  you may have to run the following (whilst not connected to the net) after the cd is added and before the you try to install packages...but try the above first..


```
 sudo apt-get update
```

---

### Post by it_suppport on 2008-10-23
wow robert,
it worked [:)] thanks a lotz. It is helping me a lot taking out all my tension of checking dependencies & other things. It does all automatically :)
gr8, this is what I was looking for.....

Thanks mike also

---

### Post by robert shearer on 2008-10-23
Good to see that worked for you:)

Here are a couple of links to the apt manual...

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)
[http://linux.die.net/man/8/apt-cdrom](http://linux.die.net/man/8/apt-cdrom)

and one to the forum's install how-to 

[http://ubuntuforums.org/showthread.php?t=644478](http://ubuntuforums.org/showthread.php?t=644478)

and one to the beginners page.This has very useful info!

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by it_suppport on 2008-10-25
wanted to ask you one more question,
why am I not able to download & install the packages from the internet.
I've enabled all the download links enabled in ny source.list file.

I'm behind our proxy server, which I've configured with the export command. i.e. 
**export http_proxy=serverip:port**

It is happening that I'm trying to install the synaptic in my ubuntu server & it asks for soooooooo many dependencies for it to manually install.

I want all this to be happened over the net & download all the necessary supporting packages & dependencies for it.

One more thing, synaptic is just an example. I've many other things to do.
which I'm not getting on the ubuntu Cd & need mannual install of it.

Please tell me what I'm missing.

---

### Post by robert shearer on 2008-10-27
> it_suppport;6029575]wanted to ask you one more question,
why am I not able to download & install the packages from the internet.
I've enabled all the download links enabled in ny source.list file.

From my earlier post did you....

> Don't forget to remove the cd from the sources list once you have the packages you want installed.

Either comment out( put # in front of the lines that list the Ubuntu install cd) or remove completely.

This should force the package manager to use the on line repositories and the latest packages.

Then.

```
sudo apt-get update
```

to get the information on the updated packages.

and,

```
sudo apt-get upgrade
``` 

if you want to update all the packages on your system.
Or look through the package lists and update only those you want.

---

### Post by it_suppport on 2008-10-29
Hi robert,

Thanks a lotz. You have been helping me a lot. 
Here I've some more questions for you. I hope I'm not bothering you ppl with all my queries.

As I'm doing some RnD on my ubuntu system, many times I do reinstall of my ubuntu server for testing. During this I don't want to go over an internet & download the packages everytime I do the format/re-install of OS.
Is there any place where We can get a cd/dvd kind of media which contains all the packages requied/applicable on Ubuntu server along with their dependencies?

If any such media does not exist, can I create the customized one which suits my requirements. In such senario, how can I Just download the packages along with their required dependencies & store them at one location and create the **apt-get** compatiable cd/dvd media?

The basic intension behind all this effot is to avoid going on the internet every now n then for each & every package. Also, there are places, where servers does not have an access to internet. In such case  the customized cd/dvd media will help me & few other peoples like me.

---

### Post by it_suppport on 2008-10-29
I found it in **/var/cache/apt/archives** folder.

---

### Post by robert shearer on 2008-10-29
You found it! Great work.

I am sorry I only know some basics, and nothing about servers so am helping where I can.
I am sure you will overtake my limited knowledge very soon!.

The two packages I use for backing up are both GUI apps.

'aptoncd' is available through the Ubuntu repositories.

```
sudo apt-get install aptoncd
```

This lets you backup the cache of your installed packages to a cd so that if you re-install from scratch you do not have to download all those packages again.BUT it is a GUI app.

The other one I use is 'remastersys' that lets you make a live dvd of your installed (and modified/customized) system that you can use to re-install from scratch just as you would install from the official Ubuntu cd.

It can be made either with your customised and tweaked install and all installed packages. ie with your personal data.

OR you can make the same dvd Without your personal data so that you can give it to someone else to use as an install disc!
Just like the official ubuntu disc but with extra packages.

The link for this is here...

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

and a couple of howto links

[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Again it is a GUI app so I don't know if it will be of use to you if you are running a server.?

But you may be running Hardy Heron LTS Desktop?? 
Let me know.

Happy Experiments.:)

---

### Post by it_suppport on 2008-10-30
ya robert,
Thanks for the help. 
I'm running the ubuntu 8.04 Hardy Heron LTS server, but I've downloaded and installed the ubuntu desktop on it so that I can use the GUI as well.

These packages I can very well go and run from the GUI mode of the server.
I'll try that. Thanks again.

---

