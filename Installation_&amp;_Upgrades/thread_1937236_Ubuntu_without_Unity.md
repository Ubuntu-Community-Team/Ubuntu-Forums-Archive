---
title: "Ubuntu without Unity"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by Meadow of Flowers on 2012-03-07
Is there a distribution of Ubuntu with Gnome (like previous versions) but without the mandatory Unity interface?

I don't have a touch monitor so Unity serves me no usefull purpose. I don't think it is particularly attractive nor does it add anything to (in fact it hinders) the experiecnce on a machine without touchscreen, not to mention the extra unneccessary resource overhead. I also don't want to have to uninstall it every time I install or upgrade Ubuntu when it could have been provided as an option and I think the way it leaves the interface selection drop down box behind even after it has been (mostly) removed is untidy.

I am considering Lubuntu (or possibly Xubuntu), but Ubuntu 9 and 10 were just fine before Unity so I was hoping there is a distro that maintains the original Gnome configuration.

PS, also since I have a nice new motherboard and Intel i3 processor in my machine, should I use a 64 bit version? Some threads suggest that there is a performance benefit, but the 32bit version is 'recommended' on the Ubuntu download page.

---

### Post by sudodus on 2012-03-07
You can select Gnome 3 and configure that instead of the 'vanilla' Unity DE. But I think that [KXL]ubuntu are worth testing from a live CD or USB drive before deciding what to install. And wait until the LTS version is official (and maybe another month to get rid of the worst bugs ;-)

---

### Post by winh8r on 2012-03-07
Have a look at this thread :

[http://ubuntuforums.org/showthread.php?t=1859960]("http://ubuntuforums.org/showthread.php?t=1859960")

Hope this helps

---

### Post by Meadow of Flowers on 2012-03-08
Thanks winh8r. I had a look at that with interest, including the linked walkthrough page at [http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)

Its obvious from the screenshots that this doesn't remove Unity as its still available as an installed option that is presumably consuming resources, although it does at least add Gnome classic back to the available options. I would have preferred not have had it installed in the first place. However even with this approach the appear to be caveats:

> Also note: In order to make changes to the panel settings, you have to use **alt+right click**, instead of just a regular right click.

So it seems that in order to 'encourage' us to use Unity, the folk at Canonical are now resorting to making the original classic environment less comfortable to use. I can accept that Unity may be the future of Ubuntu when touchscreens become mainstream. But the problem is that Unity is being foisted on a loyal user base far too soon when most users will not yet have the hardware to make the most of it. It clearly should be an OPTION or maybe enabled only when you have the appropriate touch screen equipment available, not a mandatory upgrade regardless of whether the computer it is being installed on supports it properly or not. Canonicals position is unfortunate as like a number of others (if the forums are anything to go by), I am forced to consider ditching  the mainstream Ubuntu and using another distro.

---

### Post by Meadow of Flowers on 2012-03-08
PS. Does anyone know how long 10.10 LTS will be supported for? Just noticed it is still a downoad option.

---

### Post by sffvba[e0rt on 2012-03-08
> **Meadow of Flowers said:**
> PS. Does anyone know how long 10.10 LTS will be supported for? Just noticed it is still a downoad option.

Ubuntu 10.04 LTS will be supported until April 2013.  Ubuntu 10.10 support expires this coming April.


404

PS - As a side note, a lot of changes to Ubuntu has nothing to do with Unity but the fact that Gnome 2 has been replaced by Gnome 3 (by the Gnome Foundation) and things like the changes to the classic mode has nothing to do with Ubuntu or Canonical.

---

### Post by Weatherlawyer on 2012-04-11
> **not found said:**
> Ubuntu 10.04 LTS will be supported until April 2013.  Ubuntu 10.10 support expires this coming April.


404

PS - As a side note, a lot of change to Ubuntu has nothing to do with Unity but the fact that Gnome 2 has been replaced by Gnome 3 (by the Gnome Foundation) and things like the changes to the classic mode has nothing to do with Ubuntu or Canonical.

I too am looking for a simple update experience without the Unity problems that saw me get rid of my last computer (an old one I thought had expired with an upgrade that borked all my video drivers.)

Ubuntu has just told me my present version (presumably 10.04 ) has expired and that no new upgrades to that are available.

Can I just download the 10.10 until there is another Gnome Ububntu available?

TIA.

Mike.

Edit:

***

It is fairly easy to get back to the 'classic' gnome desktop as opposed to Unity.

 You can just run this in a terminal:

```
sudo apt-get install gnome-session-fallback
```
Reboot and then select "Gnome Classic" on the login screen.

***

Not if the screen won't light up.  I had the problem with a computer magazine free disk. So I am not blaming anyone and certainly no one at Canonical.

---

### Post by 2F4U on 2012-04-11
> **Weatherlawyer said:**
> I too am looking for a simple update experience without the Unity problems that saw me get rid of my last computer (an old one I thought had expired with an upgrade that borked all my video drivers.)

Ubuntu has just told me my present version (presumably 10.04 ) has expired and that no new upgrades to that are available.

Can I just download the 10.10 until there is another Gnome Ububntu available?

TIA.

Mike.

Edit:

***

It is fairly easy to get back to the 'classic' gnome desktop as opposed to Unity.

 You can just run this in a terminal:

```
sudo apt-get install gnome-session-fallback
```Reboot and then select "Gnome Classic" on the login screen.

***

Not if the screen won't light up.  I had the problem with a computer magazine free disk. So I am not blaming anyone and certainly no one at Canonical.

Support for Ubuntu 10.10 has been dropped on April 10, while Ubuntu 10.04 will be supported until April 2013.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_10.10_.28Maverick_Meerkat.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_10.10_.28Maverick_Meerkat.29)

---

### Post by Lemuriano on 2012-04-11
Thanks to Gnome 3, I discover Xubuntu / xfce.:p

---

### Post by Weatherlawyer on 2012-04-11
> **2F4U said:**
> Support for Ubuntu 10.10 has been dropped on April 10, while Ubuntu 10.04 will be supported until April 2013.

It sounds daft that an .04 is supported beyond a .1.

This machine should cope with a later upgrade but I just didn't like the Unity interface. I found it a nuisance. maybe I will try the 12.0 when it is stable.

Thanks for the prompt help.

> **Lemuriano said:**
> Thanks to Gnome 3, I discover Xubuntu / xfce.:p

I had a version of Ultimate Edition on another hard drive ages ago. I REALLY liked that. I'll take a look a Xubuntu first. Thanks.

---

### Post by DWade on 2012-04-11
Don't get upset, I like Gnome too., but if you install the Cairo dock, you get some of the gnome features. and you make it look something like a Mac!

---

### Post by anejo on 2012-04-12
Given where I came from I have to say that I like Unity!
But then I've only been using Ubuntu for a few weeks... I was a Mint user until a few weeks ago. 

After months of using gnome3  in default and classic modes--and on occasion defaulting to Cinnamon--I struggled to buy into the new way of working. Classic G and  Cinnamon at the end of the day, are about getting into a G2 way of  working albeit with G3. I can buy into those alternatives... but back then they were  not stable enough and dare I add, not user friendly in the customizing  department.

Recently I had the opportunity to install both Ubuntu and Xubuntu 11.10. Being a ex-XFCE user, it was easy to  be impressed with Xubuntu but I digress... back to Unity. After playing  on the live-CD, I made a partition and for awhile dual booted.  I didn't get what the fuss with Unity was about. 

Ok. So the 'docky' is a  'dash' and instead of sitting horizontally it sits at the left vertical.  It didn't look cool at first... but it works. And their dash  button--imho--works better than the one in G3. Listen... after using Cinnamon, this Unity is really great! Its certainly not sluggish and has  more features than the G3 dash--imho--and its  very customizable.

Sure... you don't have  to use dash and you can revert to G3 methods but I find that having 'classicmenu-indicator' handy satisfies that particular need enough but best of all, I have my fav compiz features working again for me, which under G3 are not available.

---

