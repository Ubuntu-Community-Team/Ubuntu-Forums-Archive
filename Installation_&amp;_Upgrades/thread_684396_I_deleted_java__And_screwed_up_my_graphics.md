---
title: "I deleted java?  And screwed up my graphics?"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by makilgore06 on 2008-02-01
So I was trying to install sun-java-jdk on gutsy, thinking that's what I had to do because I had to do that on Fedora 8.  So I got to the license screen and it was blue and had <Ok> at the bottom but would not let me select it or type y or /y or sudo y or OMGHELP, so I closed terminal.  Now I am getting this error when I try to install or uninstall or reinstall or purge or do ANYTHING to sun-java5-jdk, sun-java5-jre, sun-java6-jdk, sun-java6-jre, and also the bin files... This is what I'm seeing:

[INDENT]mike@the:~$ sudo aptitude install sun-java5-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  sun-java5-jre 
The following NEW packages will be automatically installed:
  odbcinst1debian1 unixodbc 
The following NEW packages will be installed:
  odbcinst1debian1 unixodbc 
The following packages will be upgraded:
  sun-java5-bin 
1 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 68.1MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-jre package. This might mean you need to manually fix this package. (due to missing arch)
[/INDENT]
and I also got the "wasnt able to locate file" error for sun-java5-jdk.

Also, on another note, I have a nVidia GeForce Go 8400M (I think its 8400, maybe 8600M but no dfiference they use the same driver).  I tried to put Ubuntu's attempt at decoding the proprietary driver, and it didn't work.  Two of my repositories to download the file were offline, so my driver was left hanging and it won't let me uninstall it or install another.  So I can't install things because I destroyed my java, and it's 1000x harder to fix it because I'm looking at a skull number 800x600 resolution.  I have a 17" monitor that is just being recognized as PnP Monitor and won't display validly for any selection from the dropdown list of generic LCD monitors.

Also, I keep having to type "dpkg --conf -a"  or something like that to open programs.  I also had to rescue my display out of text boot like 5 times trying to fix the graphics driver problem.. The graphics worke dbefore I tried to enable stupid effects!

We won't mention the Broadcom 1390 Wireless Mini-Card.  I would do more searching but I've been searching for hours and haven't found anything.  If you can help or even post a link, please do.  *cries*

Inspiron 1720
nVidia GeForce 8400M
2.0gHz, 3.5GBram

---

### Post by zvacet on 2008-02-01
Go to the** synaptic>edit>fix broken packages**.If that doesnt help

```
sudo apt-get --purge remove sun-java5-bin
```

or 

```
sudo dpkg --remove --force-remove-reinstreq  sun-java5-bin
```

My advice is to remove it and install it with 


```
sudo apt-get install ubuntu-restricted-extras
```

you will get Java,Flash,plugins...

---

### Post by zvacet on 2008-02-01
Go to the** synaptic>edit>fix broken packages**.If that doesnt help

```
sudo apt-get --purge remove sun-java5-bin
```

or 

```
sudo dpkg --remove --force-remove-reinstreq  sun-java5-bin
```

My advice is to remove it and install it with 


```
sudo apt-get install ubuntu-restricted-extras
```

you will get Java,Flash,plugins...

P.S. To accept EULA use right array key.

---

### Post by zvacet on 2008-02-01
First of all,sorry for double post.Before you do what I described in previous post you will need graphic,so type in terminal 

```
sudo dpkg-reconfigure xserver-xorg
```

and when you come to drivers stage select** vesa** driver and continue ti the end.Restart and you will have basic graphic.Now you can do what I advice you in last post.once again,sorry for overlook.

---

### Post by makilgore06 on 2008-02-01
Thanks a lot, this seems to be working.  A lot of my problem was trying to figure out how to accept EULA... Thanks a ton!  I'll keep you posted on successfulness.

---

### Post by makilgore06 on 2008-02-01
Okay so that did not work so well.  I think I misconfigured some things in the autoconfig for my xserver so now my graphics will not load at all, it just keeps giving me the init error over and over for my bcm43xx wireless which I am sooo not worried about at this point.  I am loaded by CD and want to replace just the broken directories.  So I have a question.  How do I access my filesystem, and when I access it, what folders should I back up to save all of my installation downloads?  Does gutsy keep the downloaded package set on to the physical secondary or does it delete it as soon as ts used?

I have decided to reinstall gutsy, because too much stuff on my laptop works with this and not Fedora 8 **which I had to reinstall 4 times before downloading this**.  This is my first experience with linux, but I am decently technically proficient and understand some of what I'm doing.  

Anywho, how can I keep the hours of downloads and get rid of the graphics mess that I can't seem to rid myself of?
The file it gives me when it hands in the auto-text startup is something to do with /etc/rc.local (there may be a typo).. If you think it would help, I can locate the exact error and give it to you.

Thanks for all the great help, those commands you gave help me understand syntax a little bit better here and appreciate the complexity of using a shell over a 100% GUI interface like windows.  Thanks again =)

---

### Post by zvacet on 2008-02-01
If I´m not to late with the answer try again to reconfigure xserver.Accept all exept drivers wich will be vesa for this time.If I remember well after that comes monitor detection and mouse detection.let it do that for you and when you come to screen select simple(maybe this is a step where you typed something wrong) and that is it,as far I can remember.You should have basic graphic after restart.Sorry if I was not clear enough and that lead you to some kind of mistake.

---

