---
title: "simple way to download packages and dependencies in windows?"
date: 2006-05-11
forum: Installation &amp; Upgrades
---

### Post by pinballkid on 2006-05-11
I've just bought a new laptop, and the wireless card is giving me trouble. From what I've seen on these forums I should be able to get it working by downloading and installing the right packages, but unfortunately I cant get internet access where I am without using wireless :( 

What I'd like to do is use windows to download the packages, and then load up ubuntu and install them. Thats easy enough with packages.ubuntu.com, but its a bit slow to go through each package that I need and download all of its dependencies - and all of their dependencies, etc.

anyone know of an apt-get style program that will run on windows and get these packages and their dependencies for me the way that synaptic does?

thanks!

---

### Post by Nequeo on 2006-05-11
[QUOTE=pinballkid]I've just bought a new laptop, and the wireless card is giving me trouble. From what I've seen on these forums I should be able to get it working by downloading and installing the right packages, but unfortunately I cant get internet access where I am without using wireless :( 

What I'd like to do is use windows to download the packages, and then load up ubuntu and install them. Thats easy enough with packages.ubuntu.com, but its a bit slow to go through each package that I need and download all of its dependencies - and all of their dependencies, etc.

anyone know of an apt-get style program that will run on windows and get these packages and their dependencies for me the way that synaptic does?

thanks![/QUOTE]

Someone might know a better way... but what I usually do is visit [http://packages.ubuntu.com](http://packages.ubuntu.com) and download what I need there, and transfer it over on USB flash-drive. Then you install it with "sudo dpkg -i whatever.deb". Of course, you'll need to deal with depedencies and such automatically... but the website tells you what you need, and you can check your Ubuntu installation to find out what you already have.

Btw, if you downloaded the install CD, Ndiswrapper (if that happens to be the package you are after), should already be on the CD. Just not installed by default. A simple 'apt-get install ndiswrapper' should prompt you for the CD.

---

### Post by pinballkid on 2006-05-11
Hmm... I hadn't thought of using ndiswrapper - good idea.

I've got the Intel 3945ABG wireless card. I saw somewhere that it might work out of the box with linux-restricted-modues 2.6.15-22 so thats what I want to install.

---

### Post by Nequeo on 2006-05-11
[QUOTE=pinballkid]Hmm... I hadn't thought of using ndiswrapper - good idea.

I've got the Intel 3945ABG wireless card. I saw somewhere that it might work out of the box with linux-restricted-modues 2.6.15-22 so thats what I want to install.[/QUOTE]

You might already know this, but you'll need the 2.6.15-22 kernel as well. The restricted modules on their on won't work/won't install without it. 

I've had hellish problems with NDIS wrapper under Ubuntu 5.04 (on other people's machines... I don't by hardware without checking the Linux HCL!). But it's all been fine since Breezy. In fact, Dapper uses a couple of new Linux wireless card drivers that cause hard freezes. So I blacklist the kernel modules and use ndiswrapper instead. 

If you have the windows drivers for your card, I'd try ndiswrapper first. I'm not sure how safe it is to dpkg kernel packages. Then you can just use 'apt-get dist-upgrade' to pick up the latest kernel modules along with everything else.

Then after booting with the updated kernel, you can check to see if the card works without NDIS wrapper.

---

### Post by pinballkid on 2006-05-12
I wrote a python script that uses [beautifulsoup]("http://www.crummy.com/software/BeautifulSoup/") to scrape packages.ubuntu.com to get download links for a package and all its dependencies and dump them all into an html file as links. Then I used [downthemall]("http://www.downthemall.net/") to download them all.

Your way was a lot smarter, but I've been looking for an excuse to try beautifulsoup and this seemed like a good place to try it out. I've attached the code for anyone who cares.

---

### Post by kendall14 on 2008-07-23
Sorry to bring up an old thread but I really could use that script of your's but I don't know how to use it. I know php and java but not python, if you could give an example I would be so grateful.

---

