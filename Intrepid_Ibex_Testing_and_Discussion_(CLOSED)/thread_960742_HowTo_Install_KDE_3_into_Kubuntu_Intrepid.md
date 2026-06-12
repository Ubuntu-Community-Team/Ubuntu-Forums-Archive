---
title: "HowTo Install KDE 3 into Kubuntu Intrepid"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2008-10-27
**Prologue**
I switched to Kubuntu Intrepid from Hardy and I kept KDE 3 because, in my opinion, KDE 4 is not ready to day-by-day pc operations.

This is not a post against KDE 4, so please do not start flame war about KDE.

I understand at large the reasons why Kubuntu team make the decision to switch the WM into KDE 4 and to do not include KDE 3 anymore; in my view this is a simply wrong decision, but it's ok.
Anyway, because I like very much *ubuntu philosophy and KDE, I found a way to continue to use my distribution at the ultimate release (Intrepid) with my favorite (at the moment) WM, KDE 3.

First of all I must say a big thanks to [COLOR="Cyan"][**Madscientist159**]("http://ubuntuforums.org/member.php?u=442214")[/COLOR] that, without his precious works, the solution to use KDE 3 into Intrepid was not possible. Again, Madscientis159, in the full sense of *ubuntu community, invest his time and knowledge into this possibility.

I did the following steps personally, but I do not guarantee that this will work for you, but if I can I'll try to help you.
Please follow the steps indicated if you are a quite experienced user of the system.

**The upgrade from Hardy to Intrepid**
When you are still in Hardy install Gnome environment
```
sudo aptitude install ubuntu-desktop
```
Reboot your machine and log into Gnome
Open a terminal window and do:
```
sudo apt-get update
sudo apt-get dist upgrade
```
Accept the updates if any.
Download on your desktop my source list file [COLOR="Red"]sources.txt[/COLOR] (available at the end of the post); the repositories in the sources.txt are the official one from Ubuntu; then do:
```
sudo cp ~/Desktop/sources.txt /etc/apt/sources.list
```
> Then upgrade the system from Hardy to Intrepid:
To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions.
(I did not make the command above to upgrade, but I used apt-get, the comand above is the official one anyway)

At the end of installation reboot your machine and log into Gnome. Now you are in Intrepid

**Install KDE 3 into Intrepid**
Attention! Install KDE 3 will REMOVE KDE 4
Open the sources.list file
```
sudo gedit /etc/apt/sources.list
```
And add the following lines (the Madscientist159 repository) at the end and save/close the file:
```
###KDE3 on Intrepid
deb http://apt.pearsoncomputing.net/ intrepid main
deb-src http://apt.pearsoncomputing.net/ intrepid main
```
Add GPG to the repository:
```
wget http://apt.pearsoncomputing.net/public.gpg
sudo apt-key add public.gpg 
```
Then do:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kde3 jockey-kde
```
Reboot your machine and log into KDE; now you are in KDE 3 in Intrepid

**Annoyances**
Fix KDM login window
```
sudo ln -s /usr/share/apps/kdm/themes/Krystal/ /usr/share/apps/kdm/themes/kubuntu
```

Remove kde applet for network-manager (is not working)
```
sudo apt-get remove knetworkmanager network-manager-kde
```

Add nm-applet of Gnome into KDE
```
sudo ln -s /usr/bin/nm-applet ~/.kde/Autostart/nm-applet
```

Probably you must reconfigure kicker (KDE app bar and some stuff in kcontrol like fonts and style), if you had previously (in Hardy) installed compiz+emerald the configuration will be kept intact.

Reboot to get your networking works under KDE
Basically now you have finished, just add Medibutu repositories
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get dist-upgrade
```
Accept the updates if any.

**Do you still want KDE 4?**
You can use the Nightly Neon ppa repositories (no GPG for authenticated packages)
Open sources.list
```
sudo kate /etc/apt/sources.list
```
And add the following lines at the end of the file, then save/close the file:
```
###Amarok2 & KDE4 Nightly Neon!!
deb http://ppa.launchpad.net/project-neon/ubuntu intrepid main
```
Then do:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kde-nightly
```
Reboot the machine. Now you can choose 3 WM at the login window:
[LIST]
[*]KDE 3
[*]KDE 4 (Nightly)
[*]Gnome
[/LIST]

That's it.

---

### Post by maybeway36 on 2008-10-28
This is a very nice howto! The only thing I want to note is that it's not necessary to install ubuntu-desktop if you just want GNOME. This should do the trick:
```
sudo apt-get install gnome-core gnome-themes ubuntu-artwork
```

---

### Post by james_xxx on 2008-10-29
Let's just say (hypothetically, of course) that someone followed the instructions in this post, but upon further consideration, decided that he/she would prefer to stick with KDE4 afterall... what should that person do?

I have this 'friend' who might possibly be in this position. He tried to merely comment out the KDE3.5 repos mentioned in this post, remove KDE3, and install kubuntu-desktop from the official Intrepid repos, but was unable to do so. There were reports of broken packages. 

What should my friend do?

Thanks!

---

### Post by vivia on 2008-10-29
Great guide!
Thanks! :)

---

### Post by dentaku65 on 2008-10-29
> **james_xxx said:**
> Let's just say (hypothetically, of course) that someone followed the instructions in this post, but upon further consideration, decided that he/she would prefer to stick with KDE4 afterall... what should that person do?

I have this 'friend' who might possibly be in this position. He tried to merely comment out the KDE3.5 repos mentioned in this post, remove KDE3, and install kubuntu-desktop from the official Intrepid repos, but was unable to do so. There were reports of broken packages. 

What should my friend do?

Thanks!

I don't know. But maybe depends by the error that your friend got when try to reinstall kubuntu-desktop. I think there is no problem if your friend doing this operation inside Gnome or even inside kde-nighly; afaik, the packages of kubuntu-desktop will replace the kde3 packages
```
sudo aptitude install kubuntu-desktop
```
like kde3 packages replaced official kde 4 of kubuntu when you installed them.

But this is not the point, I think your friend should use Hardy with kde 3 and kde 4 and when he decided to use kde 4 switch to Intrepid as normal update (official), in a sense your question is not pertinent to the sense of my post, that means: I want to use Intrepid (because I want to be in the last edition of my distro beside WM) and I want to use KDE 3 because is the WM that simply works for my needs.

---

