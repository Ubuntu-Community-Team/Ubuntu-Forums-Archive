---
title: "[SOLVED] Ubuntu to Kubuntu - upgrade?"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by radamo on 2008-04-22
I am currently running the Ubuntu Hardy Beta with the latest updates.  If I want to move to Kubuntu once Hardy is released can I use the upgrade process?  Or would a clean install be cleaner?

Thanks,
Rich

---

### Post by Ayuthia on 2008-04-22
If I am understanding correctly, what you want to do is change your desktop manager from Gnome to KDE.  You don't necessarily have to wait until the release if you don't want.  It would just be a matter of installing the kubuntu-destop from the repositories.  However, if you do this, you will have a mixture of Gnome and KDE programs.  You will then most likely want to clean up your menu.  This option gives you the best of both worlds because you can switch back and forth between the two.  This will also take up some extra hard drive space.

The other option is to go with the clean install.  This will give you a KDE only environment.  It will take up less disk space since the Gnome programs are not there.  The down side to this is that if you don't like KDE, you will have to install ubuntu-desktop to get back the Gnome packages or else do a reinstall.

---

### Post by radamo on 2008-04-22
> **Ayuthia said:**
> If I am understanding correctly, what you want to do is change your desktop manager from Gnome to KDE.  You don't necessarily have to wait until the release if you don't want.  It would just be a matter of installing the kubuntu-destop from the repositories.  However, if you do this, you will have a mixture of Gnome and KDE programs.  You will then most likely want to clean up your menu.  This option gives you the best of both worlds because you can switch back and forth between the two.  This will also take up some extra hard drive space.


First off, thanks for the quick reply.  So if I just load the kubuntu-desktop I would also be adding the kde specific apps that would install with a kubuntu clean install?  If that is the case it seems like a good option.  

Appreciate the reply.
Rich

---

### Post by Ayuthia on 2008-04-22
> **radamo said:**
> First off, thanks for the quick reply.  So if I just load the kubuntu-desktop I would also be adding the kde specific apps that would install with a kubuntu clean install?  If that is the case it seems like a good option.  

Appreciate the reply.
RichAs far as I can remember, that is what it does.  Once it is installed, you might have to do a dpkg-reconfigure kdm so that it will use the kdm manager instead of Gnome's. It has been a while since I have done it.

---

### Post by AlanR8 on 2008-04-22
Personally I'd do a clean install of K. Let's face it the installation process is only about 20 mins max. Just make sure you're all backed up data wise......

---

### Post by martrn on 2008-04-22
```
sudo apt-get udate
sudo apt-get upgrade

sudo apt-get install kdm
sudo apt-get install kubuntu-desktop
sudo apt-get install kde 
sudo dpkg-reconfigure kdm

sudo apt-get install kubuntu-artwork-usplash
sudo apt-get install kubuntu-grub-splashimages

sudo apt-get purge --remove gdm

```

Thats I think is about it.  You have to log on to change the setings in kde to use the kde styles in GTK applications or else your GTK applications and QT applications look a little odd.  Simply :-

```
Kmenu ->> System ->> KControl Centre 

and..
SELECT --> use KDE styles in my GTK applications.<--
```

I thinks that is err about it and the majority of the diffreces.

---

### Post by radamo on 2008-04-22
> **AlanR8 said:**
> Personally I'd do a clean install of K. Let's face it the installation process is only about 20 mins max. Just make sure you're all backed up data wise......

Just not sure I want to abandon all of my tweaking in Gnome... Mostly due to the fact that I am so new at this I am learning everyday and I am sure I will re-screw-up the items I discovered so far.  

If I can allocate the disk space maybe I will just setup a new partition to try it.

Thanks,
RA

---

### Post by radamo on 2008-04-22
> **martrn said:**
> ```
sudo apt-get udate
sudo apt-get upgrade

sudo apt-get install kdm
sudo apt-get install kubuntu-desktop
sudo apt-get install kde 
sudo dpkg-reconfigure kdm

sudo apt-get install kubuntu-artwork-usplash
sudo apt-get install kubuntu-grub-splashimages

sudo apt-get purge --remove gdm

```

Thats I think is about it.  You have to log on to change the setings in kde to use the kde styles in GTK applications or else your GTK applications and QT applications look a little odd.  Simply :-

```
Kmenu ->> System ->> KControl Centre 

and..
SELECT --> use KDE styles in my GTK applications.<--
```

I thinks that is err about it and the majority of the diffreces.

Thanks for the info... I will save this...
RA

---

### Post by GepettoBR on 2008-04-22
Quick question: Since this method keeps both GNOME and KDE, why replace GDM for KDM?

---

### Post by martrn on 2008-04-22
On an install of ubuntu, then replaceing ubuntu with kde or kubuntu ? you end up with a minute second where gdm loads the human theme and then loads the kubuntu theme.  The process of removing gdm removes the human theme and is easier for kde users to install themes.  

If you install kubuntu, there is no need to do this as it uses its own themes and doesn't have a difficulty in selecting the diffrent themes, and I at the time I did it found it easer than looking for the reason why it loads the human (or ubuntu theme)  and then the kde theme.

---

### Post by GepettoBR on 2008-04-22
> **martrn said:**
> On an install of ubuntu, then replaceing ubuntu with kde or kubuntu ? you end up with a minute second where gdm loads the human theme and then loads the kubuntu theme.  The process of removing gdm removes the human theme and is easier for kde users to install themes.  

If you install kubuntu, there is no need to do this as it uses its own themes and doesn't have a difficulty in selecting the diffrent themes, and I at the time I did it found it easer than looking for the reason why it loads the human (or ubuntu theme)  and then the kde theme.

But wouldn't that make the same problem happen again when you select GNOME as a session instead of KDE?

---

### Post by martrn on 2008-04-22
> **GepettoBR said:**
> But wouldn't that make the same problem happen again when you select GNOME as a session instead of KDE?

gdm and kdm are very diffrent, even although they undertake exactly the same tasks.

I do not know how gdm manages its theme or login configurations and I also do not know how, or why, but on an installation where ubuntu was installed and the user has switched to kde as a default login session and then (from kde) has changed the background to the login screen, then all I can say is that it first displays a coffee coloured background for a second (possiable looking at the default gnome files) then the background you have selected as your background (possiable a nice kubuntu one.

If you login to gnome, then on a reboot, login to a kde session, when kdm first loads, it loads the default background you selected through kde as its background (no coffe-coloured stuff).  So to answer your question after you have had a gnome session, no kdm doesn't try to display coffee coloured backgrounds for even a fraction of a second like gdm does.

Kdm also handles the last login sessions diffrently, when I login it will remember the last session I logged in as gnome/kde and log me in at in that session.  As a prefered kde user this makes sence.  gdm consistantly nags me when I log in if I would prefer to use gnome as my default session .  Err no I prefer kde.  

From my personal persepective the kdm just makes a little more sense to use as your desktop manager.

---

### Post by GepettoBR on 2008-04-22
I see. Thanks for the explanation!

---

### Post by LitusMayol on 2008-04-23
> **martrn said:**
> ```
sudo apt-get udate
sudo apt-get upgrade

sudo apt-get install kdm
sudo apt-get install kubuntu-desktop
sudo apt-get install kde 
sudo dpkg-reconfigure kdm

sudo apt-get install kubuntu-artwork-usplash
sudo apt-get install kubuntu-grub-splashimages

sudo apt-get purge --remove gdm

```

Thats I think is about it.  You have to log on to change the setings in kde to use the kde styles in GTK applications or else your GTK applications and QT applications look a little odd.  Simply :-

```
Kmenu ->> System ->> KControl Centre 

and..
SELECT --> use KDE styles in my GTK applications.<--
```

I thinks that is err about it and the majority of the diffreces.


If I wanna do the same process but in the other way Kubuntu-Ubuntu (I've already installed the Ubuntu-desktop) should i do the same but changing by "gdm", "gnome"...?

And there's anyway to change from Kdm to Gdm without "sudo apt-get purge --remove kdm". I would like to preserve it by the way.

---

### Post by LitusMayol on 2008-04-23
Sorry...

Can anyone explain me the differences between GTK and QT? GTK is KDE and QT is Gnome, no? 
But i don't know what are they and the differences.

Thanks, and pardon the newbie!

---

### Post by martrn on 2008-04-23
> **LitusMayol said:**
> If I wanna do the same process but in the other way Kubuntu-Ubuntu (I've already installed the Ubuntu-desktop) should i do the same but changing by "gdm", "gnome"...? And there's anyway to change from Kdm to Gdm without "sudo apt-get purge --remove kdm". I would like to preserve it by the way.


I do not know the complete answer to that, haven't tried it.

```
sudo apt-get install gdm
sudo apt-get install ubuntu-desktop
sudo apt-get install gmome 
sudo dpkg-reconfigure gdm

// reboot
sudo apt-get install ubuntu-artwork-usplash
sudo apt-get install ubuntu-grub-splashimages
sudo apt-get purge --remove kdm
```

Should theretically be the reverse. Then manage themes from gnome.

> **LitusMayol said:**
> Sorry... Can anyone explain me the differences between GTK and QT? GTK is KDE and QT is Gnome, no? But i don't know what are they and the differences. Thanks, and pardon the newbie!

GTK is an widgets set (windows speak / application programing framework) for applactions written for the gnome desktop.

QT is a widgets set (or windows speak / application programming framework) for applications written for the kde desktop.

So QT is to KDE what GTK is to Gnome.

[To Update]
If you would like to preseve it and it is working exactly the way you want it to - don't change it.  Regardless of weather you use KDM or GDM as your login manager, they both usually work very simular, and you do not need gdm to run gnome or kdm to run the kde desktop.  One or the other will survice, and do very simular things.

---

### Post by LitusMayol on 2008-04-23
Thanks man!

specially for the widgets set's explanation! thanks!

---

