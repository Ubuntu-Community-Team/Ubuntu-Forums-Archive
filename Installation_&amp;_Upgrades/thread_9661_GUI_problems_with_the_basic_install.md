---
title: "GUI problems with the basic install"
date: 2004-12-30
forum: Installation &amp; Upgrades
---

### Post by Florence on 2004-12-30
I'm installing Ubuntu on my 5 year old laptop (celeron 500, 128mb, 5gb HD) so I thought 'let's try the basic install' (see: [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)) .

But now I'm having difficulties at the installation of the GUI.

I got some errors after:
# apt-get update
and
# apt-get install icewm

When I typ startx now, I get a dotted grey screen, with a command prompt on the left top side and a huge X as mouse. But there are no buttons or anything like that and i thought I was getting this: [http://www.binonabiso.com/en/img/LDS-screen01-thumb.png](http://www.binonabiso.com/en/img/LDS-screen01-thumb.png) as GUI.

Since this is my first attempt to install Ubuntu (and any other linux distro for that matter) I have no clue what to do now. Can anybody help? thanks

---

### Post by feneks on 2004-12-30
Hi Florence
Which errors did you get?
The content of /etc/apt/sources.list will be interessting.
Did you apt-get the other packages? (I think so but I ask to be sure.)

---

### Post by feneks on 2004-12-30
Besides:
I like this HOWTO because I come from Debian and I disliked the common installation routine which installed several services I din't need. For newbies it's best of course.

So, thanks for telling me about this HOWTO.

---

### Post by Florence on 2004-12-30
[QUOTE=feneks]Hi Florence
Which errors did you get?
The content of /etc/apt/sources.list will be interessting.
Did you apt-get the other packages? (I think so but I ask to be sure.)[/QUOTE]
 errors (this one is for install wdm, but they are all similar):
reading package list: done
building dependency tree: done
w: couldn't stat source package list hpp://archive.ubuntu.com warty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) = stat (2 no such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package icewm

But running apt-get update gives the same error.

The content of sources.list:
untouched, I only deleted the # before: "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe" and "deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe"

I apt-get the other packages, but xdm (not sure :s ) , numlockx and xterm didn't do anything (the 2 others cleary were installing something, these didn't)

Did this make anything clear for you?

---

### Post by feneks on 2004-12-30
[QUOTE=Florence]w: couldn't stat source package list hpp://archive.ubuntu.com warty/universe Packages [/QUOTE]

This looks like a typing-error at your sourcelist.
Look at  "*hpp://*". This should be "*http://*"

I'm sure you'll find this "*hpp*" in /etc/apt/sources.list

---

### Post by Florence on 2004-12-30
[QUOTE=feneks]This looks like a typing-error at your sourcelist.
Look at  "*hpp://*". This should be "*http://*"

I'm sure you'll find this "*hpp*" in /etc/apt/sources.list[/QUOTE]
 Well, that hpp:// was my error since I'm typing this from my laptop to my desktop.

---

### Post by feneks on 2004-12-30
Well all seems to be okay  :confused: 

Let's give this a try:

sudo apt-get remove icewm
sudo apt-get update

Does the error still occur?

---

### Post by Florence on 2004-12-30
[QUOTE=feneks]Well all seems to be okay  :confused: 

Let's give this a try:

sudo apt-get remove icewm
sudo apt-get update

Does the error still occur?[/QUOTE]
 I found that my network wasn't working properly. therefore my computer had no internet connection which makes is logical that updates etc weren't working. By fixing my network, I fixed the rest too.
Thanks for your help.

---

