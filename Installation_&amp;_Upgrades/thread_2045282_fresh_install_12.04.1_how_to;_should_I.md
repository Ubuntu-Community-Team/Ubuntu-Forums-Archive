---
title: "fresh install 12.04.1: how to; should I?"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by dgermann on 2012-08-20
Friends--

I have a GAZV4 running 10.04 lts. I want to go to 12.04.1, and am considering doing a fresh install. It has been a few years and I have done several upgrades, but boot up is takes a long time: and maybe I should just do a general housecleaning.

1. Is there any reason not to do a clean install?

2. What do I need to make sure I do in the clean install?

3. How do I make sure I have all the special System76 software installed?

Thanks!

---

### Post by dgermann on 2012-08-20
Hello Friends--

Have 10.04 lts installed, after having upgraded from lts to lts several times over the years. Because of some issues with the machine (general slowness, and some other things) I want to do a clean install.

1. Any reason not to do a clean install?

2. What tips do you have for making it as painless as possible? I have a lot of special things, like twinview, that I want to make sure work after I reboot....

Thanks!

---

### Post by Easy Limits on 2012-08-20
You will get that "new computer feeling" when you do a clean install.  There is a big difference in look and feel between 10.04 and 12.04.  You may want to run 12.04 in LiveCD to try it out first before you make the leap and install it.

---

### Post by oldfred on 2012-08-20
Do you have /home well backed up or as a separate partition? Since you seem to have some hardware settings also you may want to back up /etc.

I have found with clean installs that sometimes my custom settings are not required anymore & others I need. So I do not just copy back /etc but review the one's I know I need.

You should make a list of installed applications, but houseclean list so you do not install older apps. I was still installing python2.5 until recently, long after it was not needed. Also some like OpenOffice have been replaced with LibreOffice and you do not need both.

My major crash recovery is a new clean install and restore from my backups. This is what I backup.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

If you have room, install to another 25GB / partition to test. I now have all data in separate data partitions, so all my installs are now just 25GB.

---

### Post by Zvezdica27 on 2012-08-22
well,

if I see correctly, this is a bit older piece of hardware... from around 2008, right.

I would remain on 10.04 if I were you, because new versions are not harware friendly as once ubuntu was. You probably won't be able to run unity 3d, but 2d only (which is fine), but there may be some other issues as well.

I suggest: try the liveUSB and just for fun, repartition your disk and have some 10 GiB changed to a new partition. Install 12.04 there and see for yourself how it works, play for a week - no rush to upgrade.

Be careful - you don't want to loose your data. Backup first andsee what you're doing.

Personally, on older computers, i install 10.04, no questions there

Oh, the sys76 driver will do all the work, instructions are on their website. On an older model,you shouldn't even need it.

zz

---

### Post by Carborundum on 2012-08-22
> **Zvezdica27 said:**
> 
I would remain on 10.04 if I were you, because new versions are not harware friendly as once ubuntu was. You probably won't be able to run unity 3d, but 2d only (which is fine), but there may be some other issues as well.
That's just not true. Hardware support has improved immensely over the last two years. Unity 3D works fine on older hardware. It might be a bit slow, but it certainly runs. 10.04 is only supported for 8 more months, so there is no reason to choose it over 12.04. If Unity is running too slow for your taste, try Xubuntu or Lubuntu.

---

### Post by smartboyhw on 2012-08-22
Er, wait till tomorrow to install, it is now (at least for now) still testing and may have bugs... Fresh install: Download the iso: Burn it to a CD/DVD/USB: Boot it in BIOS: Follow instructions!:)
12.04.1 is more stable as in an LTS. You should install..

---

### Post by Bucky Ball on 2012-08-22
12.04 LTS. Five years support from April 2012. Run from LiveCD first, as suggested. A clean install will indeed blow out the cobwebs (boot time will be faster). Be warned, though. 12.04 uses the Unity desktop environment; not everyone's cup of tea. Other DEs can, of course, be installed.

I don't know the specs of your machine but from what people seem to be saying it's not supersonic. Why not try something a little lighter? Xubuntu perhaps? It has a more familiar desktop, is fast on older machines and highly configurable.

---

### Post by dgermann on 2012-08-22
Easy Limits and oldfred--

That is some sound advice. Thank you each.

While /home is not on a separate partition (had not thought of that), it is backed up regularly, along with /etc.

Love that list of stuff.

My main worry is that I have two screens and use twinview and nvidia with those, and I do not want to re-create the universe on those. Any hints for those? 

I know to back up my xorg.conf file, but it looks like it might no longer be a necessary file.

---

### Post by dgermann on 2012-08-22
Zvezdica27, Carborundum, smartboyhw, and Bucky Ball--

Thank you each for helping me! This is the kind of help I was looking for.

I will look into Xubuntu. Anything else light I should check out? Lubuntu? Would like to stay with something in the mainstream. I use these computers for business.

Looks like this computer goes back to at least August 2007--5 years old.

I will try the live CD here and on a couple of other machines I have in the office before I do any installing.

I think I need System76 software for sound support.

Thanks, folks!

---

### Post by ubuntu27 on 2012-08-22
[How to Upgrade You System76 computer to Ubuntu Precise]("http://knowledge76.com/index.php/PreciseUpgrade")

I don't know your hardware specification. But I can tel you this, my laptop that is 7 year old I believe and it run the latest Ubuntu version (with Unity) fine, at bit a little slow I suppose. Your laptop seems to be newer than mine, so it could work well.

I am running Ubuntu 12.04 with Gnome Classic (No Effect). You can also use Xubuntu too.

Whichever you install, just follow [this guide]("http://knowledge76.com/index.php/PreciseUpgrade") and install the system76 driver.

---

### Post by walker195 on 2012-08-22
i personally use kubuntu it runs good on my 2009-2010 laptop

---

### Post by Bucky Ball on 2012-08-22
If you are using the machine for business/production, yes, stick to the LTS releases. Ubuntu 12.04 LTS = 5 years support, Xubuntu = 3. 12.04.1 is where that's at now and pretty stable for me, by 12.04.4 next year should be rock solid.

---

### Post by oldfred on 2012-08-22
I only have one screen and have not had to edit xorg files for many versions. I thought it was obsolete except for special cases. Not sure what special cases are.

After downloading a nVidia driver directly several years ago and having even more issues, I only use the one offered by Ubuntu. But my card now is older, so those with newer cards may have to go thru that hassle as sometimes only the newest driver supports a very new card and Ubuntu is one or two versions back.

---

### Post by Zvezdica27 on 2012-08-23
well...

you know if it isn't broken... 10.04 will serve you years to come, not just up until the end of support (if it's a business laptop, then you should upgrade because of security reasons). I still have a computer at home, running fast on 9.04. Why bother to update and have a comparatively slower 12.04 on it?

but if you do need to/want/must upgrade - just because of age (not talking support, but pure power to run things) - look towards Edubuntu (if it's still on Gnome, I don't know, just search) or xubuntu. Unity will be slow. Or go with ubuntu and install a different DE (like Gnome 2 for the sake of argument) and remove unity.

My priority is a fast DE, so if Unity would be slow - i would not be using it (I love it otherwise).

Your call,

zz

---

### Post by dgermann on 2012-08-23
ubuntu27--

Thanks for the links to installing the System76 software--looks like exactly what I need.

walker195, Bucky Ball, Zvezdica27--

Thanks very much. Yes, this is a business laptop, so I am leaning toward Ubuntu 12.04.1 for security, and maybe exploring using a different DE.

all--

Thanks for your sage advice!

---

### Post by dgermann on 2012-08-23
oldfred--

Thanks. 

I wonder if I could test dual screens by using the LiveCD? Anybody know?

---

### Post by oldfred on 2012-08-23
Someone posted this as I have it in my notes. I do not think it still is gdm, but now is lightdm or whatever 
sudo start gdm
or: gdm, lightdm, xdm, etc 


to test, install Nvidia driver while in the liveCD environment. Do not restart entire system but gdm.
press ctrl+alt+f1.
sudo service gdm restart

---

### Post by Naimar on 2012-08-26
dgermann, try Lubuntu 12.04, you'll love it.

---

### Post by dgermann on 2012-08-27
oldfred--

Thanks! Sounds like it will work right out of the box without a lot of fiddling....

---

### Post by dgermann on 2012-08-27
Naimar--

Thanks!

---

### Post by lisati on 2012-08-28
Duplicate threads merged.

---

### Post by lisati on 2012-08-28
*Thread moved to **Installation & Upgrades**.*

---

### Post by rockstarrem on 2012-08-28
For your setup I would definitely recommend Lubuntu. It worked flawlessly with my PC from 2008. It's specs included:

256MB Radeon X1300
2GB Ram
Intel Core 2 Duo @ 3.0GHz (might have been even slower, I forget)


You should be fine on Lubuntu.

---

### Post by dgermann on 2012-08-28
rockstarrem--

Thanks! I'll give it a look.

---

