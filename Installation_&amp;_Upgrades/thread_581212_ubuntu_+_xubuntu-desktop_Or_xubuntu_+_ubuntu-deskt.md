---
title: "ubuntu + xubuntu-desktop Or xubuntu + ubuntu-desktop"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by mailmaldi on 2007-10-19
a few questions before i move from feisty to gutsy.

1. is a xubuntu install + ubuntu-desktop  the same as ubuntu + xubuntu-desktop ? (apt-get install ubuntu-desktop)
I ask this because I think that fluxbuntu removes a lot of modules and services for faster performance. So is a xubuntu base the same as ubuntu base differing only in the desktop environment?

2. also, have people with intel 915 motherboards and gma 900 faced any issues with gutsy? If it has, then I am loath to remove my sweet running feisty. ( 80gb hdd with 2 winxp, so  no way of trying out gutsy on another partition)

thanks, and hoping that gutsy will be everything that i've been waiting for.

---

### Post by ArtInvent on 2007-10-20
No expert here, but have a little experience. Yes, Ubuntu and Xubuntu are basically the same. I installed Ubuntu and then Xubuntu on top of that which is easy. (Removing Xubuntu, on the other hand, is less easy.) Whenever you login you can select a regular Ubuntu (Gnome) session or a Xubuntu session. I believe the same is true if you install Xubuntu first and then install the Gnome packages to turn it into reg. Ubuntu.

Fluxbuntu is a whole different ball of wax. It's not an official Ub. project and is more of a stripped down v. of Ub. without a lot of key packages. It's more to compete with Damn Small Linux while being able to use the Ubuntu repos which at this point are probably the most complete in the Linux world and the slickest to use. You could probably load any package you wanted from Gnome or KDE or XFCE portfolios, but it would take a lot to bring it up to a full Ubuntu package and at that point you'd be much better off just installing the real (*)Ubuntu you want.

I'm actually interested in trying Fluxbuntu because I didn't really find that Xubuntu Gutsy was all that much lighter on resources than a regular Ubuntu with desktop effects off. My old laptop needs something very light indeed.

Hope this helps a little.

---

### Post by Jouke74 on 2007-10-24
Ubuntu + Xubuntu desktop will load a lot more than just Xubuntu on it's own. E.g. all openoffice programs and evoluation instead of just Thunderbird and OpenofficeWord. If you need to watch your system resources it is better to start with a Xubuntu install and add programs. An issue is that some of the convinient stuff you use in Ubuntu may not be present in the standard Xubuntu install.

The end result of Xubuntu+Ubuntu desktop vs Ubuntu+Xubuntu desktop is probably very similar, but why you want to do that? Choose one ;-)

---

### Post by mailmaldi on 2007-10-24
> The end result of Xubuntu+Ubuntu desktop vs Ubuntu+Xubuntu desktop is probably very similar, but why you want to do that? Choose one 

i prefer xfce usually cuz of its snappiness but cant live without gnome, thats why wondering if x+u is the same effect as u+x.Will try x + gnome then :D

---

### Post by jis on 2007-10-24
> **Jouke74 said:**
> An issue is that some of the convinient stuff you use in Ubuntu may not be present in the standard Xubuntu install.


Could you be more specific? Do you mean I can not install xubuntu-desktop on Ubuntu?

---

### Post by aysiu on 2007-10-24
> **mailmaldi said:**
> i prefer xfce usually cuz of its snappiness but cant live without gnome, thats why wondering if x+u is the same effect as u+x.Will try x + gnome then :D
Xubuntu + Ubuntu is the same as Ubuntu + Xubuntu.

It all depends on what you *use*, not what you *install*.

If you use Xubuntu, it won't matter if it's installed on top of Ubuntu or if Ubuntu is installed on top of Xubuntu.

If you like the snappiness of Xfce, you're not going to get it by logging into Gnome (installed first or second--**it doesn't matter what order**).

Just install Xubuntu if you want the snappiness.

---

### Post by jennymanda on 2007-10-24
I wanted Ubuntu to be clean, so installed that. On another partition I installed Xubuntu, then downloaded KDE. This means I can frig around with GG between desktops and try the various apps on each without worrying about borking Ubuntu as my primary OS.

---

### Post by jis on 2007-10-24
mailmaldi, to your 2nd question, I guess there are issues with Intel motherboard laptops, see [here.]("http://ubuntuforums.org/showthread.php?t=578158")

---

### Post by jis on 2007-10-25
> **jis said:**
> Could you be more specific? Do you mean I can not install xubuntu-desktop on Ubuntu?

I found out that aptitude will remove totem-gstreamer, if you install xubuntu-desktop. How does it affect to Ubuntu and can you use some Xubuntu software to do the job of totem-gstreamer in Ubuntu?

---

### Post by mailmaldi on 2007-10-25
@jis: i am not sure, but totem-gstreamer is only the gstreamer plugin for totem. Dont think it will actually break anything. Besides, vlc and mplayer are much better players if it does indeed break totem playback.

> If you like the snappiness of Xfce, you're not going to get it by logging into Gnome (installed first or second--it doesn't matter what order).
yes i know that, what i meant was sometimes i use gnome(login to)  but most of the time xfce.

---

### Post by aysiu on 2007-10-25
> **mailmaldi said:**
> 
yes i know that, what i meant was sometimes i use gnome(login to)  but most of the time xfce. If you use both Gnome and Xfce, both need to be installed, but it doesn't matter what order you install them in.

---

### Post by jis on 2007-10-29
I installed Gutsy from Ubuntu desktop CD first and then installed xubuntu-desktop. After every login I get gnome background and I have to check "Allow Xfce to manage the desktop" every time in Desktop Settings to make it Xfce desktop. Also the startup screen looks different before the login screen: Ubuntu instead of Xubuntu

---

### Post by Dwood108 on 2007-10-29
You can try this, I had the same problem and it worked for me.

1. In the XFCE session manager (Settings > XFCE4 Session and Startup Settings), check the box that says "Show session selection at startup."
2. Log out and log back in.
3. Click 'New Session' when the session selector appears, and name it whatever you want.
4. The next time you log in, select the session you created in the previous step. XFCE should be managing the desktop right at startup, with no need to re-check the "Allow XFCE to manage desktop" box.

once this works you can turn off the session selector at startup and go directly to your new session on future logins.

If you are using Nautilus run it using the comand nautilus --no-desktop or gnome will take over the desktop again.

---

### Post by jis on 2007-10-30
> **Dwood108 said:**
> [...]
If you are using Nautilus run it using the comand nautilus --no-desktop or gnome will take over the desktop again.

Thanks for the hack, but there must be better way. It seem like gnome is dominating the desktop anyway: You really have to take care that you don't accidentally launch nautilus without the option. If you do launch it without the option, the session is raped and can not be recovered, and you have to create new session again.

---

### Post by aysiu on 2007-10-30
> **jis said:**
> Thanks for the hack, but there must be better way. It seem like gnome is dominating the desktop anyway: You really have to take care that you don't accidentally launch nautilus without the option. If you do launch it without the option, the session is raped and can not be recovered, and you have to create new session again.
Actually, the session can be recovered: ```
killall nautilus
nautilus --no-desktop &
```

---

### Post by jis on 2007-10-30
> **aysiu said:**
> Actually, the session can be recovered: ```
killall nautilus
nautilus --no-desktop &
```

I just found nautilus taking much CPU time when running in background; I didn't even know it was running there since, if I remember right, I did not explicitely start it. Another was trackerd, which I don't remember from Xubuntu Feisty times.

How do you remove those extra sessions you have created?

---

### Post by jis on 2007-11-12
I have installed xubuntu-desktop after installing Ubuntu and every time I connect USB DISK or CD, Nautilus is opened (in addition to Thunar) even if I'm at Xfce session.

---

### Post by aysiu on 2007-11-12
> **jis said:**
> I have installed xubuntu-desktop after installing Ubuntu and every time I connect USB DISK or CD, Nautilus is opened (in addition to Thunar) even if I'm at Xfce session.
Go to System > Preferences > Removable Drives and Media and uncheck the box about opening mounted drives.

If you install the *volman* plugin for Thunar, you can have Thunar manage the whole mounting/opening process instead.

---

### Post by jis on 2007-11-12
I suppose I have to do it in Gnome session as there is no System > Preferences in Xfce.

---

### Post by jis on 2007-11-16
aysiu, I read your instructions at [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce). Isn't requirement of using aptitude outdated, since apt-get has autoremove function? Also, does removing ubuntu-desktop remove its recommended applications like openoffice.org?

---

### Post by aysiu on 2007-11-16
> **jis said:**
> aysiu, I read your instructions at [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce). Isn't requirement of using aptitude outdated, since apt-get has autoremove function? Also, does removing ubuntu-desktop remove its recommended applications like openoffice.org?
In my experience, no. For the huge metapackages like *xubuntu-desktop*, I don't believe *autoremove* would work.

---

### Post by jis on 2007-11-16
BTW Why do you always have to run ```
sudo aptitude update
``` before installing something by aptitude? I think you don't have to use ```
sudo apt-get update
``` before installing something by apt-get and even then you can remove by ```
sudo apt-get autoremove [package name]
```.

---

### Post by aysiu on 2007-11-16
```
sudo aptitude update
``` checks to see what is installed and what's available. You don't have to run it in order to install via *aptitude*, but I think it helps for *aptitude* to remember what was installed together. I haven't done full experimentation on this, though.

---

### Post by jis on 2007-11-16
Synaptic asks to reload when you change repositories. Maybe the update is needed then aswell, but I neither am not sure about whether it is needed or not in other cases.

---

### Post by maybeway36 on 2007-11-16
The reason it's so hard to remove Xubutntu is the baffling contents of the /etc/apt/apt.conf.d/01autoremove file [(see bug #128681.)]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681")
Namely the second part of the file, where it says to mark all dependincies of metapackages as manually installed. It was added in gutsy.

---

