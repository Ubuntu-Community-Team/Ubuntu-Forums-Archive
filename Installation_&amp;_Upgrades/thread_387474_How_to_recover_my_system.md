---
title: "How to recover my system"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by javalang on 2007-03-18
Hi everyone, i just f*ck my system. I install a font packager that was required by another package but it becomes broken, when i tried to reinstall it also remove a lot of my applications like azureus, firefox and so on. Is there a way to recover my system to the point before this? Ubuntu come with such tool?
I´ve noticed that those removed application remains on "Not installed(residual conf)" section in synaptic, i´ve tried to install one by one but everytime it say "Depends: package-name but it is not going to be installed". It also say that i could run "apt-get -f install" but it list a lot of packages to remove that i want and use.
I desperate, my system was so great, how could i fix that? Quickly please, i think i can´t reboot.

Thank you.

---

### Post by bulldog on 2007-03-18
If you're install programs from outside the repositories,this kind of thing can happen,sorry.

And there's no recovery tool like in windows,although it never worked for me anyway.

So this left you with not much options I'm afraid.
You have to remove the packages which aren't from the official repositories and try to recover your system,after that you can try and install them again on your own risk of course.
Also it can be a wise choice  to disable the 'foreign repo's' from your sources.list till you have recovered ubuntu.

---

### Post by javalang on 2007-03-18
I've run command 'apt-get -f install' and then reinstall gnome and those applications that remains on "Not installed(residual conf)" section, i think everything is as stable as before.
But it be nice to have a recovery point tool like windows.
:)

---

### Post by bulldog on 2007-03-18
> **javalang said:**
> I've run command 'apt-get -f install' and then reinstall gnome and those applications that remains on "Not installed(residual conf)" section, i think everything is as stable as before.
But it be nice to have a recovery point tool like windows.
:)

Yes,it could be nice to have a tool like that.
As mentioned it never did anything good for me :) ,so I disabled it.
But if you're a little careful with the installed applications,you probably never need it.

It's wise to make a separate /home,though,it will hold all your preferences and when you have to do a reinstall,you can even make all the applications you've had reinstall almost automatically.
There's a script I picked up on the forum which is very useful.
Here it is,

```
dpkg --get-selections > mypackages 
#writes all installed packages to "mypackages"
# save "mypackages" on a USB stick, copy it to a fresh install
cat mypackages | sudo dpkg --set-selections 
#selects all packages from "mypackages"
sudo apt-get dselect-upgrade #installs them
```

---

