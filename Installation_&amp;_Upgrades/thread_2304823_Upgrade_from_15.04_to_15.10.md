---
title: "Upgrade from 15.04 to 15.10"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by nabz0r on 2015-11-30
Hi guys,

As the title says, I want to upgrade from 15.04 to 15.10 and the last time (3 weeks ago) I did upgrade my pc crashed and after few hours of struggling I managed to fix it but my version was 16.04. :(
Now my question is if I want to upgrade to 15.10 would these two commands do the trick? Also, do I need to disable PPA before the upgrade?

```

sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get dist-upgrade

```

Edit: I run Ubuntu Gnome btw.

---

### Post by grahammechanical on 2015-11-30
> I managed to fix it but my version was 16.04

Is it  still 16.04? Have you reinstalled 15.04? You cannot upgrade to 15.10  from 16.04. I am guessing that you used a certain command to upgrade  from 15.04 to 15.10 but the command you used was for upgrading to a  development version. And that is why you ended up with 16.04.

What command did you use to try to upgrade from 15.04 to 15.10?

When  Ubuntu 15.10 was first released I used a version of that sed command to  upgrade from wily werwolf (15.10) development version to xenial xerus (16.04)  development version. But I would not use it to upgrade from 15.04 to  15.10 because the code differences are too great.

If you are  indeed still on 15.04, then use Update Manager. It will run on upgrade  scripts designed by the developers to avoid problems.
> 
The simplest way to upgrade to a newer Ubuntu release is to start the Software Updater (update-manager). In Ubuntu with Unity: 


[LIST]
[*]Open  the Dash by hitting Super key on your keyboard. This may be done by  either clicking the key between Ctrl and Alt that may have a Windows  logo, or by clicking the Ubuntu logo in the upper left corner of the  screen. 
[*]Type "updater". 
[*]Click the "Software Updater" icon under Applications. 
[*]If a release upgrade is available, the **Upgrade** button will be active. Click it to begin upgrading. 
[/LIST]


[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

Regards

---

### Post by nabz0r on 2015-11-30
I fresh installed 15.04 after the upgrade. When I upgraded to 15.10 I used Update Manager but it failed and got stuck. I googled and I found somewhere that I could remove the unused kernel which in my case was 4.x and after doing that I was able to install from command line and I guess I used -d if I am not mistaking. 

I want to upgrade to 15.10 but to be honest I am a little afraid to upgrade. Are the commands I posted OK? And do I need to disable the PPAs?

---

### Post by mörgæs on 2015-11-30
If you want 15.10 why did you install 15.04?

---

### Post by nabz0r on 2015-11-30
> **mörgæs said:**
> If you want 15.10 why did you install 15.04?

Because I wasn’t sure if it will work or not. And a colleague of mine installed 15.10 on his laptop (Lenovo W540) and it didn't work for him so I thought I might not work for me either.

---

### Post by mörgæs on 2015-11-30
You can't expect 15.10 (or any other version) to behave in a similar way for different kinds of hardware so don't let his experience scare you. Many people here find that 15.10 is one of the most stable releases to date.

Best you can do is trying 15.10 in a live boot before deciding.

---

### Post by nabz0r on 2015-11-30
It scared me because I use the same hardware. I want to upgrade and use 15.10 but not sure which commands will upgrade without upgrading to 16.04. Are these two commands enough for upgrading to 15.10?
```
sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by mörgæs on 2015-11-30
I'm not sure I understand your posting. If you want 15.10 then it's better to install it from scratch than installing 15.04 and trying to upgrade.

---

### Post by nabz0r on 2015-11-30
> **mörgæs said:**
> I'm not sure I understand your posting. If you want 15.10 then it's better to install it from scratch than installing 15.04 and trying to upgrade.

I already have 15.04 installed on my machine. LOL if I would install 15.04 then upgrade. :P
I guess it seems a good idea to backup everything and fresh install 15.10.

---

