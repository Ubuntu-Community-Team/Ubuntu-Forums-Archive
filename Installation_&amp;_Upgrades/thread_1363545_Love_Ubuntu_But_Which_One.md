---
title: "Love Ubuntu But Which One"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by chris1379 on 2009-12-24
I'm currently running 8.04 on a 700 Mhz PIII laptop with 256MB of RAM. It seems a little slow at times but no slower than Win98SE. So, I have a few questions. I installed the XFCE Desktop, which is supposed to be lighter, but it onl;y uses 20MB less than Gnome right after boot, or about 140MB. Is this because some components of Gnome are also running? I am also wondering if running 9.04 would use more resources because I believe it would solve some hardware issues. If I decide to play with it, what software will give me a reliable image of my current installation to make it easy to go back.
 
Thanks,
Chris

---

### Post by gsmanners on 2009-12-24
I would use remastersys to backup the system when you're ready.

[http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html)

As for applications, there are some good lightweight ones, although they may require a bit more work to configure or may not have as many features.

With that little RAM, I would seriously consider using LXDE or Fluxbox rather than Xfce. I'm not sure if there's a good Ubuntu variant for those desktops.

---

### Post by chris1379 on 2009-12-26
Thanks for the tip on remastersys. As for the Desktop, I see that LXDE is in the repositories for 9.04 and can be added for 8.04. Can't hurt to try, right. This is not my primary computer. and I'm not trying to do video editing or anything like that. It's just a cheap laptop that I use on the road every couple of weeks for web browsing. So far the only thing it comes up short on is playing Hulu videos. Just don't have enough CPU for that.

---

### Post by julianb on 2009-12-26
many people recommend lxde for machines with low ram. 

i think there's a good chance your processor can handle Hulu videos, but not without more RAM. switching to LXDE probably wouldn't do the trick, buying more RAM might do it.

Or switching to tiny core linux.

---

### Post by phillw on 2009-12-26
xubuntu is designed for that RAM spec --> [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

It's a nice install. 256MB will allow you all the graphics on, it can run on less - but slowly.

As with all things- do backup your data 1st - and do a clean install. You'll already have a swap area, the xubuntu install will see that & automatically use it.

Regards,

Phill.

---

### Post by chris1379 on 2009-12-27
That's basically what I did but I didn't remove the Gnome packages. Am I correct in assuming that some Gnome components are still using memory even though I'm in the Xfce session?

---

### Post by snowpine on 2009-12-27
> **chris1379 said:**
> That's basically what I did but I didn't remove the Gnome packages. Am I correct in assuming that some Gnome components are still using memory even though I'm in the Xfce session?

Only if you use a Gnome application like Nautilus.

You can try removing everything Gnome if you want, but I don't think it will make a difference. Check out this tutorial (make sure you choose the correct version of Ubuntu): [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

With a computer that old, I would expect slow performance regardless of the desktop environment... the applications you choose are more important (for example, Abiword instead of Openoffice, Midori or Kazehakase instead of Firefox, etc. and avoid websites with lots of Flash!)

---

### Post by ugm6hr on 2009-12-27
I would also suggest a base install + XFCE or LXDE.

Xubuntu has a lot of Gnome libraries that are not strictly necessary, especially if you don't use bluetooth etc.

---

### Post by chris1379 on 2009-12-27
OK, looks like I've got some things to try. Unfortunately, Flash is what I was trying for. I know it's not going to be perfect on this machine but I'd like to make it the best I can. Youtube streams fine but I can download videos and watch them in Movie Player anyway. Hulu works with Firefox and Flash but drops frames like crazy. My office apps are only used occasionally to open an emailed doc from work. The main thing I do with this laptop is reading email and forums which sometimes include video. Hulu would just be a plus.

Chris

---

