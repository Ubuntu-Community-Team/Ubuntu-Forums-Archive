---
title: "Intrepid Remaining Bugs"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Hairy_Palms on 2008-09-27
Hello there, i was just going through my system today, compiling a list of bugs ive still got, im very guilty of "if i leave it and update itll be fixed" so i figured id take a more proactive approach

1, Intrepid sees my second hard Disk as a picture CD, only a minor annoyance, but it continually shows me the box asking me if i want to open brasero, which i dont, because if i did id open from the menu.
as far as i know not an fstab issue as that hasnt changed from hardy
```
/dev/sdb1       /media/media    ext3    defaults	0	0
```

2,[CONFIRMED][FIX FOUND] Slow to start Gedit, i mean really slow, i found other people with this issue, no solution though, and gedit takes about 8 seconds according to time, or enough time for compiz to grey it out, on a dual core with 2gb of ram thats fairly shocking for a text editor.
to fix, disable the file browser pane plugin in gedit.

3,[FIX FOUND] Suspend Icon in the new shutdown dialog is missing, purely cosmetic, just thought id point it out, for anyone who needs to fix the places Documents icon, you must have a link to 
gtk-directory.png
inode-directory.png in your icon theme. presumably the human theme maintainers will do that.
also ive found that the suspend icon needs an icon called sleep, which is being fixed already.

4,[FIXED] last is the big one, none of intrepids kernels boot at all on my computer, as soon as i press them in grub i get a kernel panic, no errors, just a black screen and a blinking cursor, as i result i still boot from 2.6.24-20 from hardy. no idea how to even look into the problem on this one.
8-Oct the kernel updates finally fixed it :) just the picture CD issue now :)

so this post is to see if anyone can confirm im not just missing something obvious before i hit launchpad.

---

### Post by Sand &amp; Mercury on 2008-09-27
I may well be wrong but I don't think your sdb1 should be set as /media/media... that's probably why it's seeing it as a picture CD. I've two partitions, one set as / and the other as /home.

I'm having the same issue with Gedit too.

---

### Post by Hairy_Palms on 2008-09-27
well its been set as /media/media since Hoary Hedgehog, and its always worked fine,changing its path and remounting didnt make a difference so i dont think thats the problem, ill try and find a launchpad bug to confirm for the gedit one,

---

### Post by mc4100 on 2008-09-27
> **Hairy_Palms said:**
> For anyone who needs to fix the places Documents icon, you must have a link to 
gtk-directory.png
inode-directory.png in your icon theme. presumably the human theme maintainers will do that.
Thanks, I'd been wondering what the icon linking to the usual folder was called, in my case, the following worked:
```
ln -s ~/.icons/gnome-brave/scalable/places/folder.svg ~/.icons/gnome-brave/scalable/places/inode-directory.svg
```

---

### Post by Hairy_Palms on 2008-09-27
yea, took a bit of searching, i have to thank the elementary theme maker, i searched for a theme that had the correct icon and then compared the links and icons it had to what human theme lacked till i found the correct one.
anyone unable to boot the Intrepid kernels? it cant be just me can it?

---

### Post by nystire on 2008-09-27
I can confirm the problem with the second partition showing as a picture CD. It happens on my install which was updated from Hardy.

---

### Post by BwackNinja on 2008-09-27
The gedit problem is from the file browser pane plugin. Disable it (unless you use it) and you'll be fine.

I can also confirm the problem with a partition showing as a picture cd. Happens with my external hard drive.

---

### Post by Hairy_Palms on 2008-09-28
ah thanks for the gedit fix bwack, worked like a charm :)

---

### Post by perfectska04@hotmail.com on 2008-09-30
> **Hairy_Palms said:**
> 
for anyone who needs to fix the places Documents icon, you must have a link to 
gtk-directory.png
inode-directory.png in your icon theme. presumably the human theme maintainers will do that.

This is a really, really bad workaround. When you use an inode-directory icon, you're pretty much forcing the same folder icon for everything. This means when you drag n' drop an item into a folder, it won't show an "open" folder receiving the item. Also, when you're not in nautilus' browse mode (fedora style), opened folders won't appear as the "folder-visiting" icon, but as a regular folder.. There are many, many other regressions by using this fix. I have no idea why GNOME 2.24 has this issue, since everything worked perfectly in previous releases without having to force an inode-directory icon.

I'm still looking for a proper fix for my own icon themes, but I don't even know if this bug has been filed or not.

---

### Post by mc4100 on 2008-09-30
> **perfectska04@hotmail.com said:**
> This is a really, really bad workaround. When you use an inode-directory icon, you're pretty much forcing the same folder icon for everything. This means when you drag n' drop an item into a folder, it won't show an "open" folder receiving the item. Also, when you're not in nautilus' browse mode (fedora style), opened folders won't appear as the "folder-visiting" icon, but as a regular folder.. There are many, many other regressions by using this fix. I have no idea why GNOME 2.24 has this issue, since everything worked perfectly in previous releases without having to force an inode-directory icon.

I'm still looking for a proper fix for my own icon themes, but I don't even know if this bug has been filed or not.
Hairy_Palms' workaround does seem to mess up the theme, I noticed this after I tried it. And coincidentally, I'm using *your* theme. But to be honest, I kept the changes because I use the panel more than drag-n-drop so having it look right was the lesser of two evils.
Also, here's the bug-report (status:unconfirmed): [http://bugzilla.gnome.org/show_bug.cgi?id=539286](http://bugzilla.gnome.org/show_bug.cgi?id=539286)

---

### Post by Hairy_Palms on 2008-09-30
> This is a really, really bad workaround.

Ah i didnt even notice that till you pointed it out, yea it does break it.

> I kept the changes because I use the panel more than drag-n-drop so having it look right was the lesser of two evils.

same situation as mc4100

---

### Post by perfectska04@hotmail.com on 2008-10-04
> **Hairy_Palms said:**
> Ah i didnt even notice that till you pointed it out, yea it does break it.



same situation as mc4100

Ok, I finally found a true solution for this issue. The problem is not with gnome-panel, but with gnome-icon-theme. The newer builds now have an inode-directory, so any icon theme that inherits icons from gnome-icon theme will have this bug.

The solution is very simple, just:
sudo rm -f /usr/share/icons/gnome/scalable/places/inode-directory.svg
sudo rm -f /usr/share/icons/gnome/32x32/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/24x24/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/22x22/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/16x16/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/icon-theme.cache
sudo gtk-update-icon-cache -qf /usr/share/icons/gnome

And logout afterwards.

There, now every icon theme should work correctly.

---

### Post by Hairy_Palms on 2008-10-04
> sudo rm /usr/share/icons/gnome/scalable/places/inode-directory.svg
sudo rm /usr/share/icons/gnome/32x32/places/inode-directory.png
sudo rm /usr/share/icons/gnome/24x24/places/inode-directory.png
sudo rm /usr/share/icons/gnome/22x22/places/inode-directory.png
sudo rm /usr/share/icons/gnome/16x16/places/inode-directory.png

Thats not the problem, it actually makes it worse. any theme without its own inode-directory.png will show a blank icon after doing that, anyone who did the above i recommend running 
sudo apt-get install --reinstall gnome-icon-theme
to fix it.

---

### Post by perfectska04@hotmail.com on 2008-10-04
> **Hairy_Palms said:**
> Thats not the problem, it actually makes it worse. any theme without its own inode-directory.png will show a blank icon after doing that, anyone who did the above i recommend running 
sudo apt-get install --reinstall gnome-icon-theme
to fix it.

As I said, try logging out and logging back in afterwards. Perhaps I should have pointed it out more clearly, but it will only show up blank until you're logged back in. The reason it shows up as blank until you log out, is because the cache needs to be refreshed. 

Edit: I've attached an image, in case someone still does not understand.

---

### Post by inxygnuu on 2008-10-04
does anyone know why the new kernal is booting up soooooo slow?
I thought that something went wrong with the installation of Intrepid, and i freaked out! all I see is it checking things, and i eventually thought that since it was the first boot it would do this, but maybe I was wrong...

---

### Post by shafin on 2008-10-04
> 1, Intrepid sees my second hard Disk as a picture CD
I have this problem also

Another persisting problem is Nautilus is painfully slow when I run it with sudo. It also crashes frequently when run as root.

---

### Post by exploder on 2008-10-04
The Usplash in Intrepid does not work right on shut down and re-start. I get the screen with the network manager errors, just like in Hardy. In Hardy I could use a work around to fix this, the fix does not work in Intrepid.

---

### Post by Hairy_Palms on 2008-10-04
> As I said, try logging out and logging back in afterwards. Perhaps I should have pointed it out more clearly, but it will only show up blank until you're logged back in. The reason it shows up as blank until you log out, is because the cache needs to be refreshed.

Edit: I've attached an image, in case someone still does not understand.

well here if you remove them and logout it still shows blanks, no matter if you reboot or logout or whatever

---

### Post by perfectska04@hotmail.com on 2008-10-05
> **Hairy_Palms said:**
> well here if you remove them and logout it still shows blanks, no matter if you reboot or logout or whatever

Hey, I tried to troubleshoot why the icons would stay blank for you and I found a solution.

Since Ubuntu does not include by default a cache for gnome-icon-theme, it shows up correctly after logging out. In your case, you probably had an icon cache, so I added two more lines that deal with updating the cache.

It should now work in special cases where there's a cache for gnome-icon-theme, and in other distributions where this cache is included by default (Fedora, Mandriva, etc)

---

### Post by MagicPaul on 2008-10-25
that workaround still didn't work for me. the basic human icon theme has been fixed but any of my custom icons now just have blank spaces. i had to manually go into the .icons folder in my home and make a copy of folder.svg in the various /places folders of the icon theme and rename it inode-directory.svg for anything to change.

---

### Post by perfectska04@hotmail.com on 2008-10-25
> **MagicPaul said:**
> that workaround still didn't work for me. the basic human icon theme has been fixed but any of my custom icons now just have blank spaces. i had to manually go into the .icons folder in my home and make a copy of folder.svg in the various /places folders of the icon theme and rename it inode-directory.svg for anything to change.

I have tested the workaround in post # 12 in dozens of setups and it should work perfectly as long as you **log out afterwards** and switch icon themes in the appearance preferences after logging back in. The few times the blank icons persist is when there is an existing icon cache for gnome-icon-theme and it is not rebuilt (i.e. by not running the last two commands in post # 12).

If for any reason it still does not work for you (due to some special variation in your setup), it's best to return everything to default by running "sudo dpkg-reconfigure gnome-icon-theme" and visiting the following two bug report pages and ask for a proper fix from the GNOME developers:

[http://bugzilla.gnome.org/show_bug.cgi?id=539286]("http://bugzilla.gnome.org/show_bug.cgi?id=539286")

[https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/278033]("https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/278033")

You can also keep creating inode-directory icons for all your downloaded icons, but this has many regressions and is just a generally annoying to have to do.

---

### Post by perfectska04@hotmail.com on 2008-10-25
Oh, I just noticed that running
sudo killall gnome-panel
Does the same thing as logging out (by reloading the panel) and you can see the results of the workaround immediately.

---

### Post by AaronMT on 2008-10-25
I seem to have a problem where dimming my display on idle (AC Power) is activated at random instead of the interval set in gconf-editor (30 seconds).

I have no idea why this is happening. I have made another thread here.

[http://ubuntuforums.org/showthread.php?t=955526](http://ubuntuforums.org/showthread.php?t=955526)

---

