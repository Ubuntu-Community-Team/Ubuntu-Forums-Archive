---
title: "Ubuntu 10.04 broken during software installation"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by rothbert on 2011-03-25
I did a very noobish thing and broke my 10.04 installation and need help to pull it back from the brink. 

I began an install of LAMP using tasksel. Ignorantly I unchecked two pre selected packages - ubuntu desktop and a print related one whose name I can't recall.

During the install I noticed that the installer was merrily uninstalling a whole bunch of stuff. Read later that if you uncheck the preselected options it actually uninstalls them. Perfect.

Second foolish action was that in a panic to stop what I thought was a total wipe of my ubuntu installation, I just turned off the computer. Yup - bad move. I know that now.

So on bootup it first just hung with a black screen. Tried to repair with a live CD but got an 'unrecoverable error' message.

Managed to get a bit of life with purging then reinstalling ubuntu-desktop but still hangs on bootup showing the ubuntu symbol and progress bar.

So I have accessed via a Grub2 disk and logged in, in a 'low graphics' mode - actually no graphics. am using aptitude to see what the state of things is, but can't get a connection to any repositories. 'Temporary failture resolving 'nz.archive.ubuntu.com'etc with [ERROR] 

Have had a look at /ect/apat/sources.list and it's still all there. But I am basically stumped as to what to do next. Pretty sure most things are still there. And really don't want to do a fresh install.

So actually what i need to do is sort out why I don't have a connection anymore. 
ping google.com fails and I can't ping my network.
Clearly something is missing. 
Any suggestions?

Any help for a total noob appreciated.

---

### Post by Hedgehog1 on 2011-03-26
rothbert,

I think waht you are are after is to have network (which I am assuming you can get when booting off the LiveCD/LiveUSB), but be on the hard drive to start the rescue.

If you boot off the LiveCD/LiveUSB, and in the terminal do:

 ```
sudo mount /dev/sd**a5** /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` 

*Please swap the /dev/sd**a5** for your actual root ('/') partition.*

```
cd /mnt
```

You should be able to run 'apt-get' and such from there, yes?

After you have restored what you can, exit this way:

```
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo shutdown -r now
```


***The Hedge***

:KS

p.s. This suggestion comes with no warranty, expressed or implied. It is my best guess.  Hedgehogs are very good guessers and all, but still...

---

### Post by rothbert on 2011-03-26
Hey thanks hedgehog1 - didn't get round to trying your suggestion but it is book marked as that was exactly the kind of thing I was after...

After some poking around and logging in and out from the Live CD, it seemed to fix itself (but also ran sudo dhclient3 eth0) and I was able to reinstall the desktop from Aptitude. 

Lesson learned - always read through the comments on a post when it suggests you try something you're not familiar with - research thoroughly!

thanks again

---

### Post by Hedgehog1 on 2011-03-26
Happy to hear you are operational again.

***The Hedge***

:KS

---

### Post by rothbert on 2011-03-26
BTW if anyone arrives here looking for a LAMP installation guide for 10.04 this one is very good: 
[http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)

---

