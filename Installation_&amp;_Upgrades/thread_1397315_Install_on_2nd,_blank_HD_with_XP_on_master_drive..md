---
title: "Install on 2nd, blank HD with XP on master drive."
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by DJnRF on 2010-02-03
I have XP on the primary HD, and have added a second drive where I would like to install 
Ubuntu.  How would I go about this? At present the second drive is installed as a slave, 
but could it be secondary master? I would like to be able to boot up to Ubuntu to use 
without XP even present so I can get used to Ubuntu well enough to get rid of XP. 

The second drive is one identical to the first that I had just used for a slave spare to 
save some extra files. It has been completely erased. 

Suggestions?

---

### Post by yogesh.girikumar on 2010-02-03
Hi,


       No problem, you can simply install Ubuntu to the second hard disk. Fix both the hard disks and select the second drive (which should be /dev/sdb ) for the installation. Ubuntu installer will automatically detect the existing windows installation and add an entry in the boot menu for booting into Windows.


       Since Windows cannot detect Linux installations, it's good to install Linux after installing Windows. 

Master / Slave setups don't matter during OS installations.
       

HTH,

---

### Post by louieb on 2010-02-03
Since you seem new to setting up dual boot. And guess you want to insure XP will work.  Also guessing these are IDE/PATA drives.


[LIST]
[*]Unplug the drive with XP.
[*]Install the drive you want to put Ubuntu on as Primary Master.
[*]Install Ubuntu. Make sure Ubuntu  boots.
[*]Put the XP drive back in - this time install as Slave.
[/LIST]
Boot to Ubuntu and run 
```
sudo grub-mkconfig   
```

You should now be setup to dual boot XP and Ubuntu. 

More on tthe grub-mkconfig - [IDBS GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")

---

### Post by DJnRF on 2010-02-03
Ok! I did get Ubuntu to install on the slave drive, and when I boot the system I select 
the OS. So far, so good. However, I have encountered two problems. 

First is that when Ubuntu loads to the setup screen it is so large that it will not show the 
entire page, and I can find no way to move it to complete the setup as needed. I have 
no way that I can find to make the page fit the screen; not in Windows, or Ubuntu. 

Next is that after uninstalling, and reinstalling I now do not get a setup screen. It still 
installs Ubuntu, but then I get directed to a sign-in screen which does not accept either 
my user name, or password.  

In Windows I don't use a password. That part is blank, and selected to not appear. 
When attempting the setup of Ubuntu (when that part worked) I did use a password. 

So ...... 
How can I adjust to see the entire page in Ubuntu, and what is needed to be able to 
get it setup to accept my username/password?

---

### Post by yogesh.girikumar on 2010-02-04
Hi,
       I'm not entirely sure what you mean by set up screen. Are you referring to the Ubuntu desktop screen or the boot screen? A screen shot would help too.


Are you able to boot into Windows / Linux?? When does this problem creep up? right after you start your computer? pre/post install / pre / post boot? Please clarify



       Also please check if this discussion  would be of any help: [http://ubuntuforums.org/showthread.php?t=183132](http://ubuntuforums.org/showthread.php?t=183132)

---

### Post by DJnRF on 2010-02-04
> **yogesh.girikumar said:**
> Hi,
       I'm not entirely sure what you mean by set up screen. Are you referring to the Ubuntu desktop screen or the boot screen? A screen shot would help too.


Are you able to boot into Windows / Linux?? When does this problem creep up? right after you start your computer? pre/post install / pre / post boot? Please clarify



       Also please check if this discussion  would be of any help: [http://ubuntuforums.org/showthread.php?t=183132](http://ubuntuforums.org/showthread.php?t=183132)


Right now I have Windows and Ubuntu on two separate HD's with Windows drive as Master, and the Ubuntu drive as a Slave. As such I can select which drive I want to boot into. I can open either; not both at a time, but either OS I want. 

Windows works normally. Since I just did the install of Ubuntu, when it opens it first took me to a display to set up the preferences for the program. After thefirst time, and even after uninstalls, it would just open to a login page. Not only will it not accept any login, but the page resolution makes the image so large that I cannot access anything beyond just what is seen on the screen. I can move the 
entire page image up, or down, but no where near enough to see the whole page. Not even attempts to resize does anything at all. 

My monitor is an unknown make. I have never been able to find any listing for it on the monitor, or when attempting to select individual set-ups with Windows. The only screen resolution I can get is 800 X 600, but when booted into Ubuntu it comes up with something entirely different. Almost enlarged to the point where the only view is about one third of the entire view I should get. It is almost like an 
unmovable magnifier. 

I have tried all I know, but it appears I just don't know enough.

---

### Post by DJnRF on 2010-02-08
> **yogesh.girikumar said:**
> Hi,
       I'm not entirely sure what you mean by set up screen. Are you referring to the Ubuntu desktop screen or the boot screen? A screen shot would help too.


Are you able to boot into Windows / Linux?? When does this problem creep up? right after you start your computer? pre/post install / pre / post boot? Please clarify



       Also please check if this discussion  would be of any help: [http://ubuntuforums.org/showthread.php?t=183132](http://ubuntuforums.org/showthread.php?t=183132)


Hopefully, a clarification of things. 
The Ubuntu OS, having just been installed on a blank HD, first boots into a 
window to set up such things as certain preferences, and login info. The size of 
the image in the window is so large that only about one third of the view 
of what is supposed to be in view is all that can be seen. There is no 'scroll' 
to view the rest of the page to finish any part of the setup. 

When first booting up a screen image of a weird bird appears. The entire window 
is with a orange background with that large bird. Even then, only the top half 
of the bird can be seen. A new image box appears over the top of that for 
the setup. The background image is covered by the setup view, but still 
remains. The setup view box can be moved some, but not to complete a 
thing. The 'desktop' view of the 'bird' cannot be moved. 

A screen shot? No Way!  Since the Ubuntu drive does not have a workable 
OS yet, and is completely separate from Windows (on a separate drive), I 
cannot capture a screen shot. I have to shut down the Ubuntu HD to get into 
the Windows HD just to post in here. The way this is now is just as if I 
were using two different PC's (which is what I will be doing later). 

All the talk about getting into some terminal to enter commands is totally 
a moot issue when the HD is blank, and will not even get loaded in a 
way to open to anything. Even now, after uninstalling the OS, and a 
reinstall, it boots into a login screen, which since the setup could not be 
done means that there is no 'login' info for it to accept to go any further. 

Want a mental image example of the problem? 
Just imagine this text box is my screen. 
Now, enlarge the view until the entire box allows you to only view just 
the first two lines of this paragraph, and there is no way you can 
move, or scroll down to see anything more. 
Now, explain to me how one can possibly do anything further if 
there are things to add, or check boxes to advance to a next stage?

---

