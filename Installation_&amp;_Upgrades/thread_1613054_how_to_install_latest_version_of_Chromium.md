---
title: "how to install latest version of Chromium?"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by bealox on 2010-11-04
Hi guys 

I have Ubuntu 9.10
I have already installed chromium but its out of date
is there anyway I can update to latest version?
is this the website I should be looking for?[http://build.chromium.org/f/chromium/continuous/linux/LATEST/](http://build.chromium.org/f/chromium/continuous/linux/LATEST/)

Thanks :D

---

### Post by sikander3786 on 2010-11-04
Add the testing ppa to your software sources.

[https://launchpad.net/~chromium-daily/+archive/beta](https://launchpad.net/~chromium-daily/+archive/beta)

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by garvinrick4 on 2010-11-04
[COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]deb [/SIZE][/FONT][/COLOR][http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu)[COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2] maverick main[/SIZE][/FONT][/COLOR]                   
 ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
``````
sudo apt-get update
``````
sudo apt-get install chromium browser
```[COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]##Add first line of this post to: (change maverick to whatever version you are using.)
[/SIZE][/FONT][/COLOR]
```
gksudo gedit /etc/apt/sources.list
```[COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]run the next three in terminal[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]will get daily updates of chromium
[/SIZE][/FONT][/COLOR]

---

### Post by sikander3786 on 2010-11-04
> deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) **maverick** main

Shouldn't it look like

```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu **karmic** main
```

And wouldn't it just be simple to add **ppa:chromium-daily/ppa** on Other Software tab under Software Sources?

---

### Post by garvinrick4 on 2010-11-04
> **sikander3786 said:**
> Shouldn't it look like

```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu **karmic** main
```And wouldn't it just be simple to add **ppa:chromium-daily/ppa** on Other Software tab under Software Sources? I told him to change maverick to whatever his version is.
I did not remember if that choice was there in what version for chromium ppa so I
just gave what I know works on them all. And also if other new users read this with whatever version they are using they will get it right. Having said that it is a lot easier
to use the other software tab if it is in their version of course.

---

### Post by sikander3786 on 2010-11-04
> I told him to change maverick to whatever his version is.

Sorry my ignorance. I missed that totally.

---

### Post by garvinrick4 on 2010-11-04
Starting to Karmic/9.10, adding the PPA and its key is as simple as:
  ```
  sudo add-apt-repository ppa:chromium-daily/beta
```slkander3786 this above is copied and pasted from your link given in earlier post:
If I would have read this launchpad page I would know this is a one line install of chromium ppa
starting at Kamic. I should pay more attention myself I am glad I learned something.
This was your correct site:
[https://launchpad.net/~chromium-daily/+archive/beta]("https://launchpad.net/%7Echromium-daily/+archive/beta")

---

### Post by bealox on 2010-11-04
hey guys

Thanks for the quick replies.
I have followed the steps but when I try to install chromium again shows

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package browser

I also tried to use deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main

the version of ubuntu is 9.10 karmic koala

---

### Post by garvinrick4 on 2010-11-04
Open a terminal and copy and paste:
```
  sudo add-apt-repository ppa:chromium-daily/beta
``````
sudo apt-get update
``````
sudo apt-get install chromium-browser
```Now should be under Application/Internet

---

### Post by bealox on 2010-11-04
hey garvinrick4

Thanks, its working
if next time there is a new update, should I follow those steps?

---

### Post by garvinrick4 on 2010-11-04
No, everytime you update and upgrade it will be upgraded it does it everyday.
 
deb [http://ppa.launchpad.net/chromium-daily/beta/ubuntu](http://ppa.launchpad.net/chromium-daily/beta/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/chromium-daily/beta/ubuntu](http://ppa.launchpad.net/chromium-daily/beta/ubuntu) maverick main
These above are found in file system to etc / apt to sources.list.d to chromium to open with text editor. In Maverick and natty.
Enjoy your Ubuntu.

---

