---
title: "Gdm"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by xworld on 2012-04-21
I actually had two questions about themes. First off, I am having trouble installing emerald theme manager in Precise Pangolin. I tried to run ```
sudo apt-get install emerald
``` No dice.  Second, I am trying to install a GDM theme and every source tells me to go to applications -> administration -> login window. Trouble is, I'm using gnome classic on precise and there is no option for login window. This seems like it should be really simple and is frustrating.  Thanks

---

### Post by jerome1232 on 2012-04-21
> **xworld said:**
> I actually had two questions about themes. First off, I am having trouble installing emerald theme manager in Precise Pangolin. I tried to run ```
sudo apt-get install emerald
``` No dice.  Second, I am trying to install a GDM theme and every source tells me to go to applications -> administration -> login window. Trouble is, I'm using gnome classic on precise and there is no option for login window. This seems like it should be really simple and is frustrating.  Thanks

Ubuntu no longer uses gdm, we use lightdm now. I believe there should be a simple-lightdm-manager for precise in the repos you can install.

---

### Post by jerrrys on 2012-04-21
GDM is not a theme, its a display manager.  12.04 used lightdm by default.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gdm&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gdm&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=lightdm&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=lightdm&sa=Search&cof=FORID:9)

---

### Post by xworld on 2012-04-21
So then I would have to search for lightdm themes instead? I just tried installing the ppa and I got the same error as I did when trying to install emerald ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package simple-lightdm-manager

```

This would be a lot easier if there was just the login window option in administration. But it's not there. I know it's a basic thing but can someone tell me where to find the login window option in Precise Pangolin using Gnome classic?

---

### Post by jerrrys on 2012-04-21
In terminal enter:

sudo apt-get install lightdm

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=emerald&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=emerald&sa=Search&cof=FORID:9)

---

### Post by jerome1232 on 2012-04-21
> **xworld said:**
> So then I would have to search for lightdm themes instead? I just tried installing the ppa and I got the same error as I did when trying to install emerald ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package simple-lightdm-manager

```

This would be a lot easier if there was just the login window option in administration. But it's not there. I know it's a basic thing but can someone tell me where to find the login window option in Precise Pangolin using Gnome classic?

As I said, Ubuntu no longer uses GDM, the login window isn't an option anymore. We now use lightdm, did you update your package list after adding the ppa? try searching for for it, I was under the impression that it came in the repo's by default

Try looking in Ubuntu Software Center for it.

```
sudo apt-get update
apt-cache search lightdm manager
```

---

### Post by xworld on 2012-04-21
It looks like I was able to install it using ```
sudo apt-get install lightdm
```I can't seem to find it now though. I figured it would just be under applications. So with this I am able to change my login screen to something else that I have downloaded?

---

### Post by jerrrys on 2012-04-21
Its not an application, its a display manager.

---

### Post by xworld on 2012-04-21
Is there any other way to change your login screen other than lightdm manager? Also can someone please answer my other question about installing themes in precise pangolin? I've read everywhere to install emerald(doesn't work) or to go to preferences -> appearance (the appearance option isnt there) So I am completely at a loss

---

### Post by jerrrys on 2012-04-21
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+theme+oneiric+11.10&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+theme+oneiric+11.10&sa=Search&cof=FORID:9)

---

### Post by xworld on 2012-04-21
That literally turns up the same results as regular google. Which I've done. Alot

---

### Post by oldos2er on 2012-04-21
[http://www.webupd8.org/2012/01/install-emerald-in-ubuntu-1110-oneiric.html](http://www.webupd8.org/2012/01/install-emerald-in-ubuntu-1110-oneiric.html)

---

### Post by xworld on 2012-04-21
I've already stated that installing emerald that way did not work. I also could not find it in the software center either. This is ridiculous

---

### Post by jerrrys on 2012-04-21
Maybe you would have better luck installing a GTK-3 theme.

[http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=6bbea7dbb1e8950358bee3b80422b569](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=6bbea7dbb1e8950358bee3b80422b569)

---

### Post by xworld on 2012-04-21
Oh my god finally! I feel stupid. Thank you it worked. I guess I can figure out the login screen themes on my own

---

### Post by dantus88 on 2013-04-24
Its a year later so... for anyone looking at this in the future. The repositories for GDM2, at the moment, no longer seem to be supported. Trying to manually get the theme manager through terminal gives you an error "E: Unable to locate package python-gdm2setup" which to my understanding is what you would use to change themes. Without it you can't use your downloaded themes? Looks like we're stuck with other alternatives unless someone can explain a different way of doing this? To be clear you can still download GDM itself you just cant theme it.

---

### Post by Iowan on 2013-04-24
From Code of Conduct:> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

