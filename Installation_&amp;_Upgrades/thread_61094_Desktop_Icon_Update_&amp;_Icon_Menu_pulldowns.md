---
title: "Desktop Icon Update &amp; Icon Menu pulldowns"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by kb7ypf on 2005-08-30
Hi-

I am wondering if there is an update software to add programs I installed with the Ubuntu Package Software Installer or other methods of software installation?

The problem is: when I install an program it does not show up anywhere on the the Ubuntu Desktop or the pull down Icon menu.  I have searched but have not found anything yet.

Does anyone know how I can have installed programs show up?

Thanks in advance.



Dick

---

### Post by sumadartson on 2005-08-31
Hi,

The solution to most of your menu related problems would be smeg. You can just run

```
sudo apt-get install smeg
```

Next, launch smeg from the applications/system tools menu. Fortunately, it does show up in there  :) .

Also, to refresh your gnome panels simpy

```
killall gnome-panel
```

This will cause the all gnome panels to restart.

Hope this is helpful.

---

### Post by kb7ypf on 2005-08-31
Thanks for your response.

Ok now, I have read the FAQ/Users Guide/and others.  I tried to install "smeg" by using Apt-get Install smeg.  It started out like it was going to work, but the final statement was smeg could not be found.  

**Don't know what is going on there.  I tried to install other programs by this method, but I get the same error message at the end.  ** 

**Do you have any suggestions as to how to fix this problem?  ** 

I then tried the Package Install program and searched for "smeg" and could not find it?   I am wondering if it really exist ?   :) 

Thanks again for your help


Dick

---

### Post by sumadartson on 2005-08-31
You can find more info on smeg [here](http://ubuntuforums.org/showthread.php?t=38183&highlight=smeg) or [here](http://www.realistanew.com/projects/smeg/).

The solution for your apt-get problem is probably in [this thread](http://ubuntuforums.org/showthread.php?t=54432&highlight=apt-get+install+smeg). Also, make sure you have the extra repositories enabled in your sources list and then do
```
sudo apt-get update
```
The other option is to try synaptic, the graphical version of apt-get. It should be under applications/system tools/add remove programs in gnome, IIRC.

---

### Post by kb7ypf on 2005-08-31
Thanks once again sumadartson-

I will give it a shot tonight when I get home from work.  If I can solve this issue I only have one more to tackle.

Again, Thanks  :) 


Dick

---

### Post by sumadartson on 2005-08-31
You're welcome.

By the way, if you're new to Ubuntu and Linux, I can highly recommend reading [the ubuntu guide](http://www.ubuntuguide.org/)  and the sticky threads in [the absolute beginners forum](http://ubuntuforums.org/forumdisplay.php?f=73).

---

### Post by kb7ypf on 2005-08-31
Hi Again sumadartson-

The procedure worked.  The pointer threads worked great.  Up and running.  Also, thanks for the recommended reading.

If anyone is having trouble with download "smeg" and other programs see the threads supplied by sumadartson, especially the one about the apt-get thread.   A quick cut and paste works great   \\:D/ 

I am new to Linux and Ubuntu.  Still have a lot to learn, but with your help, soon I can answer a few questions from new Linux users.

Thanks,
Dick

---

