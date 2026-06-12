---
title: "[SOLVED] I ant install my nvidia drivers"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by Alaxandar on 2008-07-12
I downloaded the recommenced nvidia package for drivers then I enter this in my terminal: sh NVIDIA-Linux-x86-177.13-pkg1.run
and I get this:sh: Can't open NVIDIA-Linux-x86-177.13-pkg1.rundo I need a special program or is there errpr some wheere thank you

---

### Post by overdrank on 2008-07-12
> **Alaxandar said:**
> I downloaded the recommenced nvidia package for drivers then I enter this in my terminal: sh NVIDIA-Linux-x86-177.13-pkg1.run
and I get this:sh: Can't open NVIDIA-Linux-x86-177.13-pkg1.rundo I need a special program or is there errpr some wheere thank you

Hi and you need to stop x before using that command, cd to the directory of the file location. it should run as sudo. ```
sudo sh NVIDIA-Linux-x86-177.13-pkg1.run
```

---

### Post by Alaxandar on 2008-07-12
sorry I am really slow to this how do I stop x then do then do the next thing I put in the code and got the same error

---

### Post by shad0w_walker on 2008-07-12
Going that way is going to be overly complicated. Look in System > Administration > Hardware drivers (Or possibly 'Restricted hardware/drivers)

That is a much simpler and easier way to get the Nvidia drivers installed.

---

### Post by Alaxandar on 2008-07-12
OK I opened it up How do i put in the new drivers it is already enabled but my you tube vids are slow so I know I need this new driver so how do I change them

---

### Post by shad0w_walker on 2008-07-12
Assuming you have ticked the box to enable the drivers, there is a green tick next to the driver name and you have rebooted then you should be using the drivers. Updating the drivers won't make anything noticeably faster and in all likelyhood it's a problem with flash itself.

To confirm you have the drivers running do this:

Open a terminal (Applications > Accessories > Terminal) and run this command:

```
glxinfo | egrep "vendor|direct"
```

Copy and paste that, run it and post the results.

---

### Post by Alaxandar on 2008-07-12
alexander@alexander-desktop:~$ glxinfo | egrep "vendor|direct"
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
alexander@alexander-desktop:~$ 
so ya its running, but I had xp a month ago and you tube worked perfectly, also my games now dont work very well And I don't have the same interface I did with xp, as in I don't have a whole program to to set it up

---

### Post by overdrank on 2008-07-12
> **Alaxandar said:**
> alexander@alexander-desktop:~$ glxinfo | egrep "vendor|direct"
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
alexander@alexander-desktop:~$ 
so ya its running, but I had xp a month ago and you tube worked perfectly, also my games now dont work very well And I don't have the same interface I did with xp, as in I don't have a whole program to to set it up

Hi and that is because Ubuntu is not windows. What games are you trying to use and if you are using wine to play them? If you are having issue with youtube have you tried this command ```
 sudo update-alternatives --config java

```

---

### Post by Alaxandar on 2008-07-12
which one should I chose 1 2 or 3

---

### Post by overdrank on 2008-07-12
> **Alaxandar said:**
> which one should I chose 1 2 or 3

What are the option you have, I have only 2
```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 


```

---

### Post by Alaxandar on 2008-07-12
[sudo] password for alexander: 

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-gcj/jre/bin/java
*+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 
alexander@alexander-desktop:~$

---

### Post by innocenceisdeath on 2008-07-26
> **shad0w_walker said:**
> Going that way is going to be overly complicated. Look in System > Administration > Hardware drivers (Or possibly 'Restricted hardware/drivers)

That is a much simpler and easier way to get the Nvidia drivers installed.

I need to install the same Nvidia driver, but it isn't appearing here. Is there a way to make it appear? And if not can someone please explain how to install it manually?

Thanks

---

### Post by shad0w_walker on 2008-07-26
Which bit isn't appearing? The restricted drivers manager? Or the actual driver listing for Nvidia drivers?

If you want to install the drivers without restricted driver manager (Or don't have it if you are running an older version of Ubuntu, Before 7.04 I believe) then you might want to look into this:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

It is a simple program that will install ATI/Nvidia drivers for you.

---

### Post by innocenceisdeath on 2008-07-26
I know of Envy, however these drivers aren't appearing in it. The drivers aren't showing up in the restricted drivers section either see.

---

### Post by shad0w_walker on 2008-07-26
You haven't said what isn't showing up. Envy just gives you a button to install/uninstall the drivers. It isn't possible for the driver to 'not show up'

---

### Post by innocenceisdeath on 2008-07-26
Sorry. In EnvyNG there are options to automatically and manually choose drivers right? Selecting automatic tells me that the driver for my card isn't available, selecting manually lists the ones available, the 177.13 drivers needed are not listed. I hope this clears things up.

---

### Post by shad0w_walker on 2008-07-26
Ah. I can't suggest why it isn't showing up, however I do have a suggestion for a round about way to get things done.

Envy automatically installs all the things needed to compile/install the Nvidia drivers when it installs them, which takes away the dependency hell of manual installation. If you install different version drivers with Envy, you get all of the stuff needed to then just run the 177.13 drivers package and install them that way.

---

### Post by innocenceisdeath on 2008-07-26
Ah, I see. So you mean I should install the newest set of drivers that envy offers and then attempt to install 177.13 myself?

---

### Post by shad0w_walker on 2008-07-26
Basically yes. The reason that manual install is normally a pain is that the drivers need a large list of things before you can compile/install them. Envy would take care of that so you don't have to worry about it when you manually install your wanted version.

---

### Post by innocenceisdeath on 2008-07-26
Presumably I have to stop x? How would I do this?

---

### Post by shad0w_walker on 2008-07-26
Disclaimer: This probably isn't 'recommended' or standard practice, but I have done it before with no harm.

Stopping X is a formality. You can bypass the lock by running this command:

```
sudo mv /tmp/.X0-lock /tmp/.X0-lock-backup
```

This will let the Nvidia driver continue thinking that X isn't running. When you have finished installing the drivers, run this command to restore the lock file to its rightful place:

```
sudo mv /tmp/.X0-lock-backup /tmp/.X0-lock
```


If you would prefer to just stop the X server all together then you can run this:

```
sudo /etc/init.d/gdm stop
```

---

### Post by innocenceisdeath on 2008-07-27
=D Thanks, it worked!

---

### Post by shad0w_walker on 2008-07-27
Congrats on getting it going. Wanna mark the thread as solved? Should be an option in the thread tools bit near the top of the page.

---

### Post by innocenceisdeath on 2008-07-27
Don't think I can, I didn't start this thread. I tagged on as it seemed relevant.

---

### Post by overdrank on 2008-07-27
> **shad0w_walker said:**
> Congrats on getting it going. Wanna mark the thread as solved? Should be an option in the thread tools bit near the top of the page.

Maybe the OP Alaxandar, will see this and mark it solved.

@ innocenceisdeath way to hijack a thread   J/K :lolflag:

---

### Post by shad0w_walker on 2008-07-27
Whoops, didn't notice that you weren't the OP. :lolflag:

Ah well, it's sorted either way.

---

