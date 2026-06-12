---
title: "Edgy upgrade &quot;broke&quot; the X server!"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Scheater5 on 2006-10-29
Ok, so upgrading to Edgy put me in way over my head.  The upgrade seemed to go fine, but when I rebooted, it wouldn't load the X Server!  I'm posting this from Lynx in Recovery Mode.  I don't even know where to start!  I can generally fix problems, but I'm way way out of my legue.  Anyone have any ideas??  What information could I post that would help some of you diagnose the problem, and then if all else fails can I downgrade to Dapper and save my computer?

---

### Post by Aikon- on 2006-10-29
Hmmm.. I can't load the Live CD (it hands when it tries to load X); possibly the same cause =/

I haven't found anything on the forums or on the web to help; I have a thread open here (don't have the link) so here's hoping!

---

### Post by Scheater5 on 2006-10-29
But the live CD worked fine on my laptop.  Even recognized m y wireless driver when Dapper doesn't!  (I had to use a wrapper to get wireless to work in 6.06, it worked out of the box on the live CD of 6.10).  But I upgraded the official way, and now X won't load.  When I went to recovery mode, I got some error messages about not being able to "communicate with X" - or something to that effect.  So, I know Edgy will work with this comp, but something happened in the upgrade process.  Granted, I had a ton of stuff on this laptop, including 4 desktop managers (Gnome, KDE, Xfce, and Enlightenment), but the terminal output during the upgrade seemed to do fine upgrading them all in turn and only gave me a bit of grief about Xfce saying something to the effect of the packages being no longer supported.  Wether or not that has anything to do with X, I have no idea.

---

### Post by Scheater5 on 2006-10-29
success!!

Alright, here's my success story

I tried TSEliot's suggestions in the page "Dealing with problems with the X Server" - there's a link in one of the stickied posts.  
Had no joy at first - the reconfigure xserver-xorg command gave me a blue, white and red prompt with no drop boxes, therefore I could not select "vesa" or "via," and it would not allow me to completely delete the text that was there to put those in manually.  

So, I read through his post a little more.  Not completly understanding the "why" behind some of his instructions, I was starting to get a bit frustrated.  But then I decided to try this command because, hell, what could it hurt?

```
sudo apt-get -f install
```
and then
```
sudo dpkg --configure -a
```

except that I used aptitude, and running in recovery mode "sudo" wasn't necessary.  

And lo and behold, followed that up with a reboot, and everything worked fine.  Got rid of a number of extraneous packages, too (I think they were related to Xfce, which is convient for me because I was going to uninstall it and it's related packages after the update anyway - haven't verified wether or not I still have any desktop managers besides KDE after the upgrade yet).  So, I now have a fully functional Dell Inspiron running Edgy Eft.

---

