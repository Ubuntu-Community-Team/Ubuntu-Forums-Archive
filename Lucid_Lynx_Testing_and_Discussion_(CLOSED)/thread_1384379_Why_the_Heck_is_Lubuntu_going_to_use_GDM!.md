---
title: "Why the Heck is Lubuntu going to use GDM?!"
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Psumi on 2010-01-18
See this page: [https://wiki.ubuntu.com/Lubuntu/Applications](https://wiki.ubuntu.com/Lubuntu/Applications)

It's horrid that Lubuntu has to use GDM, when LXDM or SLiM are available.

---

### Post by kerry_s on 2010-01-18
could it be policy kit related? a lot of stuff gets broken when gdm is not used.

---

### Post by cariboo on 2010-01-18
Have a look [here]("http://blog.lxde.org/?p=514") you will see that work on lxde is continuing, they are just using gdm until it is finished.

---

### Post by seeker5528 on 2010-01-20
What's wrong with GDM, other than the lack of configuration options in the current incarnation?

Later, Seeker

---

### Post by BwackNinja on 2010-01-20
> **seeker5528 said:**
> What's wrong with GDM, other than the lack of configuration options in the current incarnation?

Later, Seeker

How it pulls in a lot of gnome libraries that you wouldn't want to have in a more minimal installation like lubuntu.

---

### Post by gnomeuser on 2010-01-21
This could be because the alternative currently doesn't currently support the transition from Plymouth or some other such technical requirement.

It is also a better supported option for the developers as both Ubuntu and upstream GNOME are committed to the code, you are going to be pulling in a lot of the libraries anyways for applications such as OpenOffice.org and Firefox so that is likely not going to matter much in the general case.

---

### Post by seeker5528 on 2010-01-21
> **BwackNinja said:**
> How it pulls in a lot of gnome libraries that you wouldn't want to have in a more minimal installation like lubuntu.

Like gnomeuser said, much of what GDM depends on is likely to end up being pulled in by things the user chooses to install anyway.

GDM is used by Xubuntu and Mythbuntu and while choosing a different display manager may make a marginal difference in the amount of stuff on the installation CD, it shouldn't make a difference in how heavy the installed desktop feels.

Slim does look like it has potential, but, IMHO, there's a bigger advantage in sticking with GDM at the moment, in particular when you consider the cycle of Ubuntu development in regard to being an LTS release and getting Plymouth and KMS issues sorted.

Later, Seeker

---

### Post by meborc on 2010-01-21
that is the problem with all those "low memory" systems...

nobody actually is concerned about the memory :) just to preserve the ubuntu look (gdm, gnome apps just because the GUI looks consistent)

I can understand for the need to have eye candy, but i also have used slim (2 years ago) and can vouch for it's stability

if we have something, that depends on GDM... do we really need it in lubuntu?

i mean, we already have ubuntu, kubuntu and xubuntu... let lubuntu be really slim and low on memory/hdd consumption - lets get rid of all that fancy stuff which will probably be too slow on low memory systems anyway

---

### Post by scottuss on 2010-01-21
> **meborc said:**
> that is the problem with all those "low memory" systems...

nobody actually is concerned about the memory :) just to preserve the ubuntu look (gdm, gnome apps just because the GUI looks consistent)

I can understand for the need to have eye candy, but i also have used slim (2 years ago) and can vouch for it's stability

if we have something, that depends on GDM... do we really need it in lubuntu?

i mean, we already have ubuntu, kubuntu and xubuntu... let lubuntu be really slim and low on memory/hdd consumption - lets get rid of all that fancy stuff which will probably be too slow on low memory systems anyway


If you want to use SLIM instead, you are free to do so! It's just a load of tweaking but it's do-able.

Also, if you want a really slim, lean system, why not build it up from something like Arch? I know it has it's downsides, but the fastest and leanest "fully featured" distro I've ever used is Arch...

---

### Post by hikaricore on 2010-01-21
Real men use **startx**.

---

### Post by phillw on 2010-01-21
> **hikaricore said:**
> Real men use **startx**.

One day some one will explain what startx is (or I'll **finally** go and google it ;-) ) .. I did an update of my 9.10 system the other day & got dropped to CLI ... the only x command i could remember was startx ... Heck, it worked :D

Regards,

Phill.

---

### Post by xebian on 2010-01-21
> **phillw said:**
> One day some one will explain what startx is (or I'll **finally** go and google it ;-) ) .. I did an update of my 9.10 system the other day & got dropped to CLI ... the only x command i could remember was startx ... Heck, it worked :D

Regards,

Phill.

It means **start** your **X** server.

That's what various login manager does anyway and then prompts you your userid/password.

---

### Post by VMC on 2010-01-21
> **meborc said:**
> that is the problem with all those "low memory" systems...

nobody actually is concerned about the memory :) just to preserve the ubuntu look (gdm, gnome apps just because the GUI looks consistent)

I can understand for the need to have eye candy, but i also have used slim (2 years ago) and can vouch for it's stability

if we have something, that depends on GDM... do we really need it in lubuntu?

i mean, we already have ubuntu, kubuntu and xubuntu... let lubuntu be really slim and low on memory/hdd consumption - lets get rid of all that fancy stuff which will probably be too slow on low memory systems anyway

Also makes it easier for Ubuntu developers. Not having to learn another DE. But who says if one installs Lubuntu that your going to run OO. Kind of defeats its purpose, being a low memory, slim install. There are other alternatives. If you want to use OO then use Ubuntu.

---

### Post by lykwydchykyn on 2010-01-21
is slim back in Lucid?  It was dropped from Karmic.  Too bad, because it's a great lightweight DM.

Everything else has heavy dependencies or looks like butt.

EDIT: Ok, I checked and slim is back in Lucid.  Yeah!

---

### Post by Simian Man on 2010-01-21
> **gnomeuser said:**
> This could be because the alternative currently doesn't currently support the transition from Plymouth or some other such technical requirement.

I have used SLiM with Fedora, which obviously uses Plymouth, and there was no problem there.  I think there was a moment of black screen between the two rather than the smoothness that is Plymouth->GDM though.

---

### Post by meborc on 2010-01-21
> **scottuss said:**
> If you want to use SLIM instead, you are free to do so! It's just a load of tweaking but it's do-able.

Also, if you want a really slim, lean system, why not build it up from something like Arch? I know it has it's downsides, but the fastest and leanest "fully featured" distro I've ever used is Arch...

are you saying that lubuntu's goal is not to make a low memory system??? of course i am free to do what i want :) but that is not the point... the point is that there is yet-another "low memory" version of ubuntu, which is totally bogged down by trying to give the users same visual experience like ubuntu

there is nothing wrong with that, but then they should advertise lubuntu as lxde + full ubuntu experience... not as lubuntu for lower memory systems

> **VMC said:**
> Also makes it easier for Ubuntu developers. Not having to learn another DE. But who says if one installs Lubuntu that your going to run OO. Kind of defeats its purpose, being a low memory, slim install. There are other alternatives. If you want to use OO then use Ubuntu.

the lubuntu developers are not ubuntu developers... lubuntu project was started from community forum by some guys, who wanted a low memory system... they were tired of xubuntu running bogged down by gnome apps


sorry if i sound harsh... i don't even own a system that would need a slimmed down operating system... BRING ON THE BLING :)

but i was so exited about fluxbuntu (it died)... then xubuntu (i still have a partition with it)... and now lubuntu... but i see nothing new, just new window manager + all the usual ubuntu programs (gnome dependencies)

---

### Post by snowpine on 2010-01-21
I see Lubuntu as "Ubuntu for people who prefer LXDE to Gnome." If it happens to use less RAM, that is a bonus. :)

---

### Post by meborc on 2010-01-21
> **snowpine said:**
> I see Lubuntu as "Ubuntu for people who prefer LXDE to Gnome." If it happens to use less RAM, that is a bonus. :)

i can see that... they even say it on their wiki... i was more talking about this bit:> Members of the Lubuntu team take care of LXDE and other packages that are part of the planned Lubuntu install. Please join us and contribute to creating a lighter, less resource-hungry and more energy-efficient flavour of Ubuntu.

---

### Post by ranch hand on 2010-01-21
If you download the CD you will find that it is much smaller than Ubuntu CDs and Xubuntu CDs.

I suppose that it will take less space on your drive though I have never gotten the installer to work so I do not know for sure.

---

### Post by kahumba on 2010-01-21
I just tried LXDE on karmic.
If LXDE was more mature (doesn't know what an .mp3 file is etc etc) I'd switch to it.
Unlike Nautilus and Thunar, the LXDE file browser doesn't just claim to be fast, it actually is.
Only with such a DE I could say with a straight face that the Ubuntu desktop is snappier than XP.

---

### Post by scottuss on 2010-01-22
> **hikaricore said:**
> Real men use **startx**.

I use xinit on my Arch box, so I guess I'm just as cool? :p

---

### Post by ranch hand on 2010-01-22
I have gimp, gthumb, ubuntu-restriced-extras added to the Lubuntu install along with 2 kernels.  Root partition has 1.6Gb used.

I used an existing OS to install over and did not format /home.  It has some files backed up from the other test OS' and a lot music and images but the whole thing is 5.7Gb

An Ubuntu version that is very like the Lubuntu install as far as what iis on it is 6.7Gb with out the backup files on it.

---

### Post by Psumi on 2010-01-22
By the way, if anyone has searched for it yet, you'd know lxdm isn't in lucid repos at the moment.

---

### Post by ranch hand on 2010-01-22
Lxdm is in Lubuntu though.  You can choose it or gdm.

---

### Post by Psumi on 2010-01-23
> **ranch hand said:**
> Lxdm is in Lubuntu though.  You can choose it or gdm.

How DO we choose it if lxde.org doesn't provide a PPA, or download nor is it in the ubuntu repos?

---

### Post by ranch hand on 2010-01-23
It is installed in Lubuntu already.  It is part of the meta package Lubuntu Desktop I think.

I know gdm is because I had to reinstall Lubuntu Desktop and had the option presented to me to choose gdm or lxdm.

Yes I was "exploring" possibilities.  One thing I wanted to remove needed to remove Lubuntu Desktop.  On reinstalling I got the one back that I was trying to loose.

Hey, if it ain't broke I can break it.

Lubuntu, at this point, on this box, runs better than Ubuntu by the way.

---

### Post by VMC on 2010-01-23
Is this where you got [Lubuntu alpha1]("https://lists.launchpad.net/lubuntu-desktop/msg00396.html") . I can't find alpha2 for Lubuntu.

---

### Post by ranch hand on 2010-01-23
Yes, according to the mailing list A2 will arrive toward the end of the week.  A1 updates from it to current just fine.

I just did that today.  Played with it on another drive and decided I would replace one of my ohter Lizards with it so just formated the root and did it.  Updated fine.

---

### Post by VMC on 2010-01-23
According to that [link]("https://lists.launchpad.net/lubuntu-desktop/msg00396.html") I gave, here is some features:

```
Features :
- LXDE packages up-to-date [1]
- **LXDM**
- The new pcmanfm for testing (type "pcmanfm2" in a terminal)
- Many wallpapers and start icons from lxde forum, gnome-look or Leszek
Lesner, to be able to switch easily and to test the result
- First customization with a splash screen from Leszek Lesner
- Installable with ubiquity (but upgrade from this Alpha 1 to next
release is not guaranteed)
```

Edit: there is 236 members on the mailing list. You would think someone there would see this topic and respond. I read their reasoning behind using GDM for now.

---

### Post by seeker5528 on 2010-01-23
Tried Slim.

While using Slim it starts the xsession in a way that allows me to do:

```
sudo -H gedit some_file
```

Without getting a complaint about not being able to connect to display 0, which is good.

But it has a static list of X sessions to choose from, and requires you to edit '/etc/slim.conf' if you need to add a session that wasn't included in the list. That's a big negative to me. It's 2010, display managers should just look at the .desktop files in '/usr/share/xsessions' and display the sessions that are actually available, without the user having to do anything.

Other than that I don't have any issues with it.

Later, Seeker

---

### Post by Hero of Time on 2010-02-04
LXDM is already in the repo for more than a week. See [http://packages.ubuntu.com/lucid/lxdm](http://packages.ubuntu.com/lucid/lxdm). I'm using it instead of SLiM on Karmic and installed Lubuntu the same way I installed my current Xfce system, from a minimal setup only picking the packages I need. When I look at GDM, I still need like a dozen extra libs, while I already have OOo installed. Go figure, GDM is bloated. Gnome is starting to get bloated just like KDE. The only DE's that are fast and lightweight, are LXDE and Xfce, if you install it properly. Don't trust the default meta packages that Ubuntu create. Install using the Alternative installer, with F6 switch to expert and skip the second package install step, so you end up with only Ubuntu Minimal.

---

### Post by Psumi on 2010-02-04
> **Hero of Time said:**
> LXDM is already in the repo for more than a week. See [http://packages.ubuntu.com/lucid/lxdm](http://packages.ubuntu.com/lucid/lxdm). I'm using it instead of SLiM on Karmic and installed Lubuntu the same way I installed my current Xfce system, from a minimal setup only picking the packages I need. When I look at GDM, I still need like a dozen extra libs, while I already have OOo installed. Go figure, GDM is bloated. Gnome is starting to get bloated just like KDE. The only DE's that are fast and lightweight, are LXDE and Xfce, if you install it properly. Don't trust the default meta packages that Ubuntu create. Install using the Alternative installer, with F6 switch to expert and skip the second package install step, so you end up with only Ubuntu Minimal.

Just glad ayttm will be 0.6.1 in lucid, as you can't connect to yahoo in karmic with ayttm, and MSN disconnects after about 5 minutes in the karmic version.

ayttm doesn't require gnome depends (pidgin does, gconf specifically.)

---

### Post by VMC on 2010-02-04
> **Hero of Time said:**
> LXDM is already in the repo for more than a week. See [http://packages.ubuntu.com/lucid/lxdm](http://packages.ubuntu.com/lucid/lxdm). I'm using it instead of SLiM on Karmic and installed Lubuntu the same way I installed my current Xfce system, from a minimal setup only picking the packages I need. When I look at GDM, I still need like a dozen extra libs, while I already have OOo installed. Go figure, GDM is bloated. Gnome is starting to get bloated just like KDE. The only DE's that are fast and lightweight, are LXDE and Xfce, if you install it properly. Don't trust the default meta packages that Ubuntu create. Install using the Alternative installer, with F6 switch to expert and skip the second package install step, so you end up with only Ubuntu Minimal.

Hero of Time, thanks for this info. Is there a tutorial of what you just described somewhere. I use Alternate install mainly because I've had so may problems with ubiquity. I never thought of trying the advance method. Or I think in the past I tried it but not sure what to include and what not. I'm speaking only on Lubuntu installs. Ubuntu could be done the same way, I'm interested in the new Lubuntu Lucid. Thanks.

---

### Post by Hero of Time on 2010-02-04
> **VMC said:**
> Hero of Time, thanks for this info. Is there a tutorial of what you just described somewhere. I use Alternate install mainly because I've had so may problems with ubiquity. I never thought of trying the advance method. Or I think in the past I tried it but not sure what to include and what not. I'm speaking only on Lubuntu installs. Ubuntu could be done the same way, I'm interested in the new Lubuntu Lucid. Thanks.
I don't have a howto or anything, it's something I did myself. I can write one for you if you like, but all I did was skip the last install phase, let Grub install, fix the apt sources since it doesn't copy sources.list.apt-setup to sources.list and disables the cdrom and use aptitude with 'install recommended' off to get the rest of my packages. When I'm missing something, I just open aptitude again and look for the missing packages. It's useful to have apt-file installed too.

If you need more details, send me a PM and I'll see what I can do.

---

