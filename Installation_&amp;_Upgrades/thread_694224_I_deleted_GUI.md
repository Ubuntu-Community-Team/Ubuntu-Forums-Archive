---
title: "I deleted GUI"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by twodayslate on 2008-02-11
A couple days ago I installed dpkg but quit in the middle of installation. I then finished installation today and then decided I didn't need it (It didn't seem like it did anything). My computer worked fine without it, it seemed.

So I deleted it and said "Y". Bang! It said it was deleting ubuntu-desktop, fast-user-switch-applet, ubufox, etc; I closed the terminal hoping it would not bring havoc on my machine to bad. 

I now have no internet (used to be wireless) and no GUI. I do have access to the install CD and the command line.

Thanks for the help. I would usually just reinstall ubuntu completely but I do not really want to loose all my files again.

These are the threads I found but they are not in my exact position.
[http://ubuntuforums.org/showthread.php?t=197819](http://ubuntuforums.org/showthread.php?t=197819)
[http://ubuntuforums.org/showthread.php?t=133960](http://ubuntuforums.org/showthread.php?t=133960)

---

### Post by HappyFeet on 2008-02-11
just do the opposite
```
sudo apt-get install ubuntu-desktop
```

---

### Post by twodayslate on 2008-02-11
I did but the sources don't match up or something.
"Package ubuntu-desktop has no installation candidate"

I commented everything out of the source list but the CD. So everything but one line.

Thanks for the reply.

---

### Post by zvacet on 2008-02-12
> I now have no internet (used to be wireless) and no GUI.

In that case it is not your source list where is the problem.Put Cd in drive and try 

```
sudo apt-cdrom add
sudo apt-get install ubuntu-desktop
```

---

### Post by twodayslate on 2008-02-12
That is wierd. It recognizes the CD but I still get the 
"Package ubuntu-desktop has no installation candidate"
error.  Thanks though. 
> Package ubuntu-desktop is not available, but is referred to by another package This may mean the package is missing, has been obsoleted or is only available form another source
E: Package ubuntu-desktop has no installation candidate

Could anyone tell me what dpkg is and why it removes everything when removed?

---

### Post by chipants on 2008-02-12
dpkg is a tool to install packages on a debian-based system (such as ubuntu).

[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

in short, it is a lower-level way of installing packages than apt or synaptic, which do all kinds of fancy dependency checking, and can pull software from multiple sources, etc.

it should have *already* been installed on your system, i think. and, if for some reason it wasn't, what would have possessed you to install it in the first place?

as far as reinstalling ubuntu goes, you shouldn't necessarily lose all of your files. just boot the live-cd and back everything up first!

when installing any linux distro, i *always* setup a mountpoint for /home on its own partition. that way, when suddenly required to reinstall the OS, your home folder isn't affected.

---

### Post by twodayslate on 2008-02-12
I was trying to install a theme (murrine) and I was going to use the editor. When I typed * ./editor.py or something like that I think the * has something to do with dpkg and it told me to install it. 

So I am screwed? I have to reinstall? How do I set up a mountpoint for home? Links?

Oh, my friend said the ubuntu sometimes takes a backup image. How do I get that? Could that work?

---

### Post by chipants on 2008-02-13
i think that the best and easiest option for you right now would to be to boot from the live cd, mount your hard drive, navigate to your important files you'd like to keep, and copy them to a thumb drive or something.

after that, reinstall from scratch.

i think the scope of repairing this may be more intensive than you're used to dealing with.

it'd likely be quicker to just reinstall.

---

### Post by mordox on 2008-02-13
well reinstalling everything again when a problem comes up is the windows way of doing things.

ubuntu-desktop is a dummy package.

try and install gnome. 

goto the terminal

$ sudo aptitude

you will se a package manager similar to synaptic.

If you have just installed files from a cd it should have packages only from the cd. so start selecting packages that you had accidentally deleted. that should fix it.

---

### Post by chipants on 2008-02-13
indeed, reinstalling everything may be 'the windows way' of doing things. however, it seems like the original poster was having a bit too much trouble installing the dummy ubuntu-desktop package when he tried.

i think that in some cases, a reinstall can be quicker and easier. pop in the livecd, and once booted, mount the hard drive, backup personal files to thumbdrive. then reinstall.

it's pretty quick. and definitely more intuitive for the user, seeing as how they've done that at least once before.

in the time he's spent searching for solutions, considering he already tried to install the ubuntu-desktop package, he could have had a full working desktop already.

i will reiterate: a complete reinstall is not the best solution, usually. however, when an new or average user severely changes the functionality of an operating system install, does not know exactly how it happened or why, and has tried to fix it unsuccessfully, sometimes the quick and dirty fix is the best.

---

### Post by twodayslate on 2008-02-13
OK
I did sudo aptitude gdm 
I got the error:
> No Candidate version found
I also did sudo aptitude and went through the list. I went to gdm and where exactly do I got to download?
gdm is gnome so I don't get it.

So is there such a thing as ubuntu taking a backup image of the os? Can I get that image?

---

### Post by zvacet on 2008-02-14
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
Other solution is to remove # from  cdrom line in your sources list and save file.

```
sudo apt-get update
```

After that 

```
sudo aptitude
```

That will give you graphic to work with aptitude.Read [this](http://doc.ubuntu.com/ubuntu/serverguide/C/aptitude.html) to see how it works.With this method you should be able to install ubuntu-desktop from CD.

---

### Post by twodayslate on 2008-02-15
I did that and then the cd files were in green but it said they were ignored.

Trying again and commenting out all online files again

I can remove packages but when I press the + to install it never turns green so it says when I press g that no packages are selected.

---

### Post by zvacet on 2008-02-16
Sorry for my constant and idiotc overlook.You have live Cd and of course you can not install ubuntu-desktop from it.You need alternate Cd to do it.But you don´t have internet and you can not download it (if you have net you will not even need it).You have two options
1.get wired connection (if it is posible)
2.reinstall (back up your files of course)

Once again,sorry for wasted time.

---

