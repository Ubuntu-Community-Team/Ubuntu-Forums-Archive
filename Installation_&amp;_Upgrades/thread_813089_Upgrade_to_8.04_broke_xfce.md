---
title: "Upgrade to 8.04 broke xfce"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by matthewboh on 2008-05-30
I just went from 7.10 to 8.04 but now Xfce doesn't work.  It runs through, pulls up the Xubuntu screen with the old background, then it goes to the default Hardy Heron background and a terminal window opens up - but no menus for xfce.

I tried removing xfce and installing it - same thing. 

This is a server that I added xubuntu-desktop so I could use NetworkManager to manage my wireless connections

Any pointers?

---

### Post by dstew on 2008-05-30
At the login screen, options, select sessions, see if you can select xfce. Maybe it is starting a default gnome session, but since gnome is not set up, you get no icons.

---

### Post by matthewboh on 2008-05-31
I don't get that choice - the only time I get to select something is when grub comes up.  Other than that - it just goes straight into the page with the terminal window and the Hardy Heron background.

Since yesterday, I followed the instructions to completely remove xfce (it got a few extra files than just using apt-get remove xubuntu-desktop).  So today, I'm going to try and re-install xfce from my 8.04 iso image.  If you have other suggestions, I'd love to hear them because I've got a lot of data on the box and I know it's going to take me hours to figure out how to mount a cdrom and copy files off the hard disk drive!

---

### Post by garethsimpsonuk on 2008-06-19
This happens for me. I really need to know if this is a bug or not.

I install ubuntu server, enable all repos, update / upgrade then install xubuntu-desktop. 
I get the same thing - terminal and the hardy bird thing wall paper. I then restart and change the session drop down box to xfce. It works but surely the other options shouldn't be there which are gnome and a few others. I assume if you only have 1 gui enviroment installed then it should boot into that. I haven't even got gnome installed.
Anyway the issue comes when I disable the gui at boot up. I can use the cli but when I startx the gdm login screen is disabled ( it's supposed to boot straight into xfce ) I don't have the option to login with a different session.

This is a major issue for me! Is it a bug? Is there a workaround? Please help anyone if you have any info I'm sat with my black terminal screen after doing a reinstall because of this, lucky I'm using empty drives otherwise I'll have the same issues as op.

Thanks

---

### Post by matthewboh on 2008-06-19
I finally broke down and got rid of xfce - and did a new install on my box.  

I'm learning a lot of command line Linux - which is good - and I ended up installing Webmin - which allows me to do most anything I wanted.  You can set up groups, user permissions, create backups.  That's what I would suggest.

You can install Webmin after you get your LAMP server going by typing
```
sudo apt-get install webmin
```
It's pretty painless, then just open a browser window and type localhost:10000 and it should open up.

---

### Post by garethsimpsonuk on 2008-06-19
yea thanx I do use webmin aswell but really would like xfce. so are you saying you don't think there's a solution? i think this is a major issue if its a bug.
It did seem to work o.k when I changed the session with the gdm dropdown box but I like to disable the gui when i dont need it which means it skips straight past long screen so i cant change the session.
i only tried this once, if i install xubuntu-desktop again do you think i'll have the same problem?

---

### Post by garethsimpsonuk on 2008-06-20
> **garethsimpsonuk said:**
> yea thanx I do use webmin aswell but really would like xfce. so are you saying you don't think there's a solution? i think this is a major issue if its a bug.
It did seem to work o.k when I changed the session with the gdm dropdown box but I like to disable the gui when i dont need it which means it skips straight past long screen so i cant change the session.
i only tried this once, if i install xubuntu-desktop again do you think i'll have the same problem?

bump

---

### Post by matthewboh on 2008-06-20
Sorry - I was sleeping!

Well, it does seem to be a bug / issue - but I'm sure it's way down on their list of things to do.  Very few people install a GUI on servers and there's talk of moving xfce support into the Kubuntu (or KDE) release of Ubuntu.

Also, you would have to kill the X sessions along with the KDE / Gnome processes.  I really would suggest just going commando (in the US it means not wearing any underwear) and trust that you can do it in Webmin or the command line.

Good luck!

---

### Post by garethsimpsonuk on 2008-06-20
That's ok. We're on oppostie sides of the pond anyway. 
Well I'm pretty dissappointed with that. I guess in the long run it will be better for me anyway but I'm going to have to reinstall it all. I could just remove xfce but I might aswell repartition my root instead of having all that extra space in there. 
Midnight Commander here I come! 
Yea it means that here to. Hopefully you're suggesting I use the command line rather than walk around with no boxers on ( I don't think that will fix the bug lol )

I may look into fluxbox although I remember last time it took a lot of configuration. I know a bit more now so I may be ok

> **matthewboh said:**
> Sorry - I was sleeping!

Well, it does seem to be a bug / issue - but I'm sure it's way down on their list of things to do.  Very few people install a GUI on servers and there's talk of moving xfce support into the Kubuntu (or KDE) release of Ubuntu.

Also, you would have to kill the X sessions along with the KDE / Gnome processes.  I really would suggest just going commando (in the US it means not wearing any underwear) and trust that you can do it in Webmin or the command line.

Good luck!

---

### Post by garethsimpsonuk on 2008-06-20
I think I may have found a workaround. It seems to be gdm's fault that it starts the heron background and only a gnome term emu. 
I've done a lot of messing around and if I do startxfce4 it seems to start up xubuntu with no problems. startx tries to start gnome ( or whatever it's doing ) so by starting xfce directly it works. it might be worth installing a different login manager but i prefer to leave it out completely.
i just want to check my data / system rescources using sysmon ( i dont like top )
This seems ok for me for now, just thought i'd let you know in case you did want to keep xfce. If anyone can see a problem in what im doing please let me know.

> **garethsimpsonuk said:**
> That's ok. We're on oppostie sides of the pond anyway. 
Well I'm pretty dissappointed with that. I guess in the long run it will be better for me anyway but I'm going to have to reinstall it all. I could just remove xfce but I might aswell repartition my root instead of having all that extra space in there. 
Midnight Commander here I come! 
Yea it means that here to. Hopefully you're suggesting I use the command line rather than walk around with no boxers on ( I don't think that will fix the bug lol )

I may look into fluxbox although I remember last time it took a lot of configuration. I know a bit more now so I may be ok

---

### Post by avtolle on 2008-06-20
A thought; instead of installing gdm, install xdm (should you wish something to do what gdm does). Idea from the Wiki on Low Memory Systems.

---

### Post by garethsimpsonuk on 2008-06-21
> **avtolle said:**
> A thought; instead of installing gdm, install xdm (should you wish something to do what gdm does). Idea from the Wiki on Low Memory Systems.

yea i looked at that to. it's for my home server so i need it to boot into cli, and only into xfce when needed. this is the first time Ubuntu hasn't worked for me. hope fully there's a fix / workaround

---

### Post by lobotheduck on 2008-06-22
> **dstew said:**
> At the login screen, options, select sessions, see if you can select xfce. Maybe it is starting a default gnome session, but since gnome is not set up, you get no icons.

Thanks man, you fixed the problem thats kept me working all night.

If anybody else has this problem you have to log in normally and open up the xfce panels, window manager and desktop through the terminal:

```

xfce4-panel
xfwm4
xfdesktop

```

Then right click the desktop and go to Settings -> Settings Manager -> Sessions and Startup

Then check the box "Display chooser on login" and logout.

Then finally change your session to xfce, login and click yes when it asks if you want xfce to be the default session.

Hope it helps people :D

---

### Post by Deadmode on 2008-07-18
> **lobotheduck said:**
> Thanks man, you fixed the problem thats kept me working all night.

If anybody else has this problem you have to log in normally and open up the xfce panels, window manager and desktop through the terminal:

```

xfce4-panel
xfwm4
xfdesktop

```

Then right click the desktop and go to Settings -> Settings Manager -> Sessions and Startup

Then check the box "Display chooser on login" and logout.

Then finally change your session to xfce, login and click yes when it asks if you want xfce to be the default session.

Hope it helps people :D

I can't get this to save.  So this isn't working for me.  Is there another approach?

---

