---
title: "Compiz / KDE Issue"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Saner on 2010-04-09
Hiya, 

Last time I used KDE it was KDE3, so I thought I would have a look at KDE4 so I installed the stuff, and looked, and was really impressed, so much so I am thinking of switching from gnome to KDE as a permanent thing.

One problem though, I just dont seem to be able to save my visual effects settings.

As you can see, compiz is working (I tryed to catch it being wavey)

[http://pokemonger.com/kde.png](http://pokemonger.com/kde.png)

When i click on keep settings, it just hangs, or a way to manually enable on the startup of kde without using the appearance prefrences.

the system seems stable enough, but its an annoyance.

any ideas ?

---

### Post by Seren on 2010-04-09
Have a look in system settings, there is a place to configure advanced visual effects. Kwin natively implements  effects similar to Compiz.

So unless you specifically need Compiz, there is no need to use it under KDE 4.

Youtube video of some Kwin effects in 4.3, Lucid uses 4.4 so you should have some more :
[http://www.youtube.com/watch?v=XqWd4fNRy8Q](http://www.youtube.com/watch?v=XqWd4fNRy8Q)

---

### Post by Saner on 2010-04-09
About the only compiz feature I would miss is wibbly windows, it just feels so right.

Do you know if thats in the kwin settings (or something very similar) I cant see it, but I have only had a quick glance.

If not I will drop back to gnome, and just try kubuntu by itself at some point when I have time and no doubt that will shake it.

---

### Post by Saner on 2010-04-09
Nevermind found it, not convinced I like it as much, but then I feel like that with anything new.

Will give it a go.

---

### Post by lovinglinux on 2010-04-09
> **Saner said:**
> Nevermind found it, not convinced I like it as much, but then I feel like that with anything new.

Will give it a go.

I switched to KDE a couple of months ago because I couldn't live without Compiz and you know it won't run wit gnome-shell on Gnome 3. Anyway, I didn't like Kwin at first, but decided to try it when KDE 4.4 was released. I'm loving it. It is much easier to configure, has all the plugins I need and performs great.

It might feel strange to use it initially, but I think you won't regret.

---

### Post by Saner on 2010-04-09
I must admit, its a lot nicer (and feels lighter) than the last version of KDE I used, I have a feeling it was KDE3, but then it could have been earlier than that.

I know its more bloated than gnome, but after farting about with gnome-shell I am unimpressed with the direction they are taking, but KDE seems to be improving.

---

### Post by lovinglinux on 2010-04-09
> **Saner said:**
> I must admit, its a lot nicer (and feels lighter) than the last version of KDE I used, I have a feeling it was KDE3, but then it could have been earlier than that.

I know its more bloated than gnome, but after farting about with gnome-shell I am unimpressed with the direction they are taking, but KDE seems to be improving.

I didn't look back. I'm very happy with KDE 4.4. BTW, I don't install Kubuntu, but **kde-minimal** and **kdeplasma-addons** over a command-line only installation of Ubuntu. It doesn't feel bloated.

---

### Post by Saner on 2010-04-09
Interesting, I may have to give that a go at some point.

I am planning on re-doing this PC once 10.04 goes final, as I still have a 200 gig Windows partition for gaming, and I just dont need that amount, so I will have a look at doing it that way.

---

### Post by lovinglinux on 2010-04-09
> **Saner said:**
> Interesting, I may have to give that a go at some point.

I am planning on re-doing this PC once 10.04 goes final, as I still have a 200 gig Windows partition for gaming, and I just dont need that amount, so I will have a look at doing it that way.

Here is what I do:

1) Download the Ubuntu alternate CD
2) When prompted for installation, hit F4 and select command-line only system, then hit the Install
3) after booting into command-line, log in and then run this:

```
sudo apt-get install xorg kdm kde-minimal kdeplasma-addons jockey-kde
```

I also install Firefox at this step, because I use it to install my package list backup from previous KDE installations (see [UMarks](http://lovinglinux.megabyet.net/?page_id=534)).

Then I run:

```
sudo reboot
```

and voilà...

Install graphics driver from "Applications >> System >> Hardware drivers". I don't have a wireless connection, so it connects directly via DHCP. 

Here I some additional packages that I consider important :

```
kate kwalletmanager gnupg-agent kgpg pinentry-qt4 wine bum update-manager anacron apport-kde apturl-kde ark kcron userconfig ksystemlog gtk2-engines-qtcurve kde-style-qtcurve kwin-style-qtcurve qtcurve kcm-gtk plasma-scriptengine-python plasma-scriptengine-kimono plasma-scriptengine-qedje plasma-scriptengine-ruby plasma-scriptengine-superkaramba plasma-scriptengine-webkit plasma-scriptengines k3b pulseaudio alsa-base alsa-oss ubuntu-restricted-extras kmix okular gimp gwenview
```

---

### Post by The Punisher on 2010-04-09
compiz-kde doesn't work since the KDE 4.4 release, even on Kubuntu 9.10
On compiz.org there is a patch since february but nobody implemented It yet
The problem seems to be the decorator, the core work.
So, are the Saints coming?

---

### Post by Saner on 2010-04-10
Well I followed your steps (to an extent) and I agree KDE does feel lighter (I am not convinced it feels as light as a base gnome install though)

I am still stumbling a little because I am so used to gnome, but I do think that KDE 4 is a fantastic improvement over the last version I used, so I am going to stick with it for a while, because gnome-shell made me feel a little "Urgh" and I need to get used to something else before that become default :D

---

