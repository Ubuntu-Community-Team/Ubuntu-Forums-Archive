---
title: "need help installing &quot;entertainer&quot;"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by addman on 2008-07-23
ok so basicly im creating an in car entertainment system, but before i get started i wanted to test out some software.i decided first im gunna try out the "entertainer" media center thing cause it looked cool. im not very good at linux i can do all my simple tasks but when it comes to coding and terminal and such i basicly copy and paste close my eyes and wait for the fast moving text to finish its job hoping that by the time i open everything will be exactly the way id like it. but unfortunately it didnt work this time. ive pretty much figured out dependencies and stuff but this time i had not luck and im completely stuck.
so...
i was reading this [https://answers.launchpad.net/entertainer/+question/39028](https://answers.launchpad.net/entertainer/+question/39028)
 and i was doing fine until step 3...

3. Extract the code from the compressed file:
    `tar -xvzf entertainer-0.1.tar.gz`

i don't know what compressed file he's talking about i've looked through the whole package and i can't find it. 

and just as a little forecast i dont know what to do for steps 4-7 either so any extra help is much appreciated.

thank you for your time

---

### Post by Partyboi2 on 2008-07-23
Click on the link in step one this will download the  entertainer-0.1.tar.gz probably to your Desktop or where ever you have specified your downloads to go. Open a terminal and cd to your Desktop (or where ever the file has downloaded to)
```
cd Desktop 
```then installing the packages mentioned in step 2
then for step 3 extract entertainer-0.1.tar.gz that you downloaded in step 1
```
tar -xvzf entertainer-0.1.tar.gz

```then enter the entertainer-0.1/src directory which was created when you extracted 
entertainer-0.1.tar.gz
```
cd entertainer-0.1/src

```then type
```
./entertainer-content-management.py
``` and set it up how you want.
then back in the terminal issue the last 2 commands
```
./entertainer-backend.py

``````
./entertainer-frontend.py

```

---

### Post by Layman's terms on 2009-03-24
addman,

Entertainer can now be installed from a regular Ubuntu package. You might have more luck if you check the following information.

[http://wiki.entertainer-project.com/wiki/StartUpGuide](http://wiki.entertainer-project.com/wiki/StartUpGuide) is a good place to start for installation instructions.

You can also ask any question directly to the developers on Launchpad ([https://launchpad.net/entertainer](https://launchpad.net/entertainer)) or on the IRC channel (more info that can be found on the wiki).

---

