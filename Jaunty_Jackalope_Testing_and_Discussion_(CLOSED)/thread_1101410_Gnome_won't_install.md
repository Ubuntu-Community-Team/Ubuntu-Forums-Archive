---
title: "Gnome won't install"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-03-20
I know there have been a lot of 'python' updates recently, but I still can not get **'gnome'** to install.
Via terminal I get this:
Can't install gnome as it depends on serpentine
can't install serpentine as it depends on **python-4suite-xml**
ok, so when I try to install **python-4suite-xml**  I get this;
 
[B]The following packages have unmet dependencies:
  python-4suite-xml: Depends: python (< 2.6) but 2.6.1-0ubuntu3 is to be installed[/B]
 So, is there any way to solve this yet, or are there more python fixes on the way?
It would be nice if I could get 'gnome' to install some how.
Thanks

---

### Post by pdoma on 2009-03-20
Dumb question but did you try installing the hole Ubuntu Desktop package?

---

### Post by taavikko on 2009-03-20
Have you enabled some 3rd party repositories?
Are you using main server for repositories?

There shouldn't be any issues remaining, most of it is gone through the grinder, AFAIK.

```
sudo apt-get -f install ubuntu-desktop
```

---

### Post by DougieFresh4U on 2009-03-20
> **pdoma said:**
> Dumb question but did you try installing the hole Ubuntu Desktop package?

Not a dumb ?, but it's installed

---

### Post by KCG102282 on 2009-03-20
Where you upgrading for Intrepid or something because I have Gnome completly installed and just had 9 updates again this morning before I came to work and still works good.

---

### Post by DougieFresh4U on 2009-03-20
> **taavikko said:**
> Have you enabled some 3rd party repositories?
Are you using main server for repositories?

There shouldn't be any issues remaining, most of it is gone through the grinder, AFAIK.

```
sudo apt-get -f install ubuntu-desktop
```

Yes i use 'Main' and I do have a couple of ppa's  and 'Medibuntu' installed, but I don;t see how that could interfere with installing 'gnome' unless I am missing something???
Thanks for reply

---

### Post by taavikko on 2009-03-20
> **DougieFresh4U said:**
> Yes i use 'Main' and I do have a couple of ppa's  and 'Medibuntu' installed, but I don;t see how that could interfere with installing 'gnome' unless I am missing something???
Thanks for reply

Erros message is caused by version mismatch, some repo is providing a newer version and that one hasn't been pinned down, that causes conflicts.

Check with "apt-cache policy <pkg>"

---

### Post by DougieFresh4U on 2009-03-20
> **taavikko said:**
> Erros message is caused by version mismatch, some repo is providing a newer version and that one hasn't been pinned down, that causes conflicts.

Check with "apt-cache policy <pkg>"

Thanks for your assist. Is there some thing I could post (sources list, etc) that would help  you assist me in finding the prob?
dumb question, but where would I find (how) ** "apt-cache policy <pkg>"**. 
Thanks

---

### Post by taavikko on 2009-03-20
Open terminal->
```
apt-cache policy python-4suite-xml
```

My best advice would be that #comment every unofficial repos
do full upgrades and try again.

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by taavikko on 2009-03-20
You can use apt-get to install specific version of available packages, if there's more than one available

```
sudo apt-get install python2.6=2.6.1-0ubuntu3
```
Note the = in command, that is used for installing pgk version of your choice
attained via apt-cache policy


You'll catching up :) 

BTW, my eyes will never be the same after viewing your screenshot;)

ps. All these thing should be able to achieve via synaptic, but since I havent been using that one for a long time, I support you via CLI

---

### Post by DougieFresh4U on 2009-03-20
Ok, I did a couple of things; (sorry for the eyes, sunglasses:D) Been playing with colors, lol

```
dougie@DougiesLeanMachine:~$ apt-cache policy python-4suite-xml
python-4suite-xml:
  Installed: (none)
  Candidate: 1.0.2-7
  Version table:
     1.0.2-7 0
        500 http://archive.ubuntu.com jaunty/universe Packages 
```
I also # out all the ppa's and left just the 'official' ones. but no luck yet..
I also removed 'python 2.5 minimal. don't know if that was a no no but 'python 2.6 minimal' is installed, therefore did I do any harm in removing 'minimal 2.5'?
Thanks for your help, don't know what else to try.

```
dougie@DougiesLeanMachine:~$ sudo apt-get install python2.6=2.6.1-0ubuntu3
[sudo] password for dougie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '2.6.1-0ubuntu3' for 'python2.6' was not found

```

---

### Post by andrewsomething on 2009-03-20
DougieFresh4U,

You've done nothing wrong. There is a real and known bug here:

[https://bugs.edge.launchpad.net/ubuntu/+source/python-4suite/+bug/338079](https://bugs.edge.launchpad.net/ubuntu/+source/python-4suite/+bug/338079)

It is being worked on. My question is have any of the others in this thread tried to install serpentine? 

Also, serpentine is not a part of ubuntu-desktop any more. Brasero has replaced it as the default burning application. In fact this happend at least in Intrepid (possibly Hardy?). Upgrades wouldn't have removed it, but it isn't in a fresh install.

---

### Post by DougieFresh4U on 2009-03-20
> **andrewsomething said:**
> DougieFresh4U,

You've done nothing wrong. There is a real and known bug here:

[https://bugs.edge.launchpad.net/ubuntu/+source/python-4suite/+bug/338079](https://bugs.edge.launchpad.net/ubuntu/+source/python-4suite/+bug/338079)

It is being worked on. My question is have any of the others in this thread tried to install serpentine? 

Also, serpentine is not a part of ubuntu-desktop any more. Brasero has replaced it as the default burning application. In fact this happend at least in Intrepid (possibly Hardy?). Upgrades wouldn't have removed it, but it isn't in a fresh install.

Thank you so much. 
I thought it strange no one else has had near same issue.

---

