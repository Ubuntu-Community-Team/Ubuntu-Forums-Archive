---
title: "How much for /root if /swap and /home are on different drive"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by PendragonUK on 2012-11-15
I'm going to reconfigure my Gaming/Desktop PC.

I need it to be dual boot with Win7 and Ubuntu. 

I will be splitting both the 256GB SSD and 1TB HD between the two OS's
Most of the SSD will be for Win7 but I would like some idea how much space I would need for /root on the SSD if /swap and /home will be on the 1TB HD. We all know how hungry Win7 can be plus a few games will benefit from being on the SSD for performance reasons. My concern is that after time the /root partition will become too small. Would 40GB be enough for the long term?

---

### Post by SlugSlug on 2012-11-15
I give / 20GB 

its plenty not sure I even use 10gig

and use other drives for music / films etc

---

### Post by PendragonUK on 2012-11-15
Thanks, I was thinking that 40GB was a little over the top, I just want to be careful. 

I know this sounds like a dumb question but where do the programs you install go. Is it /home because when I look at the home directory there are a lot of hidden stuff. If the programs are going there I would like them on the SSD. I just want to put data on the HD. The contents of the regular folders found in /home not the hidden folder. Or are these just config files specific to my login. Would there be any advantage to having these on the SSD. If I just wanted the contents of the visible folders on the HD I could imagine that I'm going to tie myself in knots.

---

### Post by SlugSlug on 2012-11-15
it's just configs mainly I have both / and /home on the ssd but I don't store much in my /home just a few docs

I sym link stuff like music to my home eg

rm ~/Music -Rf #remove Music folder in home directory
ln -s /path/to/data/Music ~/Music #link Music to home

This gives me a Music link in my home folder to my data drives Music folder

---

### Post by Mr_JMM on 2012-11-15
> **PendragonUK said:**
> I know this sounds like a dumb question but where do the programs you install go.

Not a dumb question at all. As far as I recall, the applications reside within /root (e.g. /opt /etc is common if installed manually) but the settings for the applications mostly resides in /home. It's this separation that keeps /root size minimal and makes upgrading via fresh installs so much easier. The only reason for larger /root partitions is if you have large number of big applications. Wine applications though will install to /home.

If you use logical partitions then resizing should you ever need to, is a little less stressful. But as above 10-20GB is usually more than enough.

If you keep on top of housekeeping you can further reduce the necessary size of /root.

```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get clean
```

Once a week if you're anal about like me.

---

### Post by NikTh on 2012-11-15
Hi , 

as you said SSD , have a look at these articles 
[http://askubuntu.com/questions/18903/how-to-enable-trim](http://askubuntu.com/questions/18903/how-to-enable-trim)
[http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd](http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd)
and this video 
[http://www.youtube.com/watch?v=nXbkoFSHoy0&feature=g-hist](http://www.youtube.com/watch?v=nXbkoFSHoy0&feature=g-hist)

Thanks

---

### Post by PendragonUK on 2012-11-15
Thanks guys... :)

---

