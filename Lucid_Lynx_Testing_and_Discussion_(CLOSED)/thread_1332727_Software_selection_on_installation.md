---
title: "Software selection on installation?"
date: 2009-11-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Lieter on 2009-11-20
Now I've been thinking:

The dev's want to remove a couple of packages from the default installation/live-cd(see other threads in this forum). So why not take on the ubiquity installer as well. Prior to(or after) installing the base install(aka copy the live cd to the harddisk) have the user select some programs often installed, or special "packs" of programs.

The /target enviroment is already available and most(well I do) users have an internet connection while installing. So why not download those packages and install them as part of the installation process in ubiquity, so the desktop is 'complete' when the user logs in

I was thinking about the following packs:
"Java development" ==> Either Netbeans or eclipse with openJDK
"Webdevelopment (PHP)" ==> Apache(not started by default by upstart)+ mod_php, mysql-server(not autostarted)
"Office/Productivity" ==> Openoffice(full), inkscape etc.
"Graphic Designer" ==> Gimp et al.
etc..

Also(if radeonhd and nouveau aren't feature complete), why not include the possibility to install restricted drivers. So users can enjoy a fully composited and 3d accelerated desktop on first boot.

And maybe an 'advanced' package selector, so it is possible to install e.g. gnome-do and vlc from within the instrallation enviroment.

By doing it that way you won't have to 'fix'(i.e. download loads of packages i always install) your desktop after the first boot. And give the user a bit more possibilities to pre-customize his system.


caveats:
Updates in the repo's. I want to install program foo which depends on bar. bar has had an update in the repo from version x.y-2 to x.y-4. foo is in the repo's with version p.q-8. When installing I need to update bar to x.y-4 first in order to install foo. But completely updating the just installed system takes quite a time(e.g. i install it 4 months after the release).



Any comments/ideas on this?

---

### Post by Gina on 2009-11-20
The Minimal Install CD does something like this.  I use it to install Ubuntu on my ancient AMD k6-2 desktop.  There are similar suggestions in another thread.

---

### Post by forcecore on 2009-11-21
Software selection should be in atleast to choose if Mono, OpenOffice etc... will be installed or not.

---

### Post by seeker5528 on 2009-11-21
> **Lieter said:**
> 
Also(if radeonhd and nouveau aren't feature complete), why not include the possibility to install restricted drivers. So users can enjoy a fully composited and 3d accelerated desktop on first boot.

Better to put the effort into making sure you *can* boot on first boot and let the user add things that create extra potential to screw it up later, just my opinion. ;)

On the other hand if you are letting the user choose what is installed and not limiting it to things that are included on the CD, then there is nothing stopping the user from installing these things.

If the alternate install CD uses the debian installer, doesn't it allow you to install additional software as part of the installation?

Later, Seeker

---

### Post by ronacc on 2009-11-21
they want to keep the install from the live cd as simple and interaction free as possible and ubuntu tries to make it easy on first timers so I think this is right for the livecd . As gina points out there is the alternate install cd or just use the live , its fast and simple then customise on first boot .

---

### Post by 23meg on 2009-11-24
As of 9.10, the alternate installer lets you modify the package selection, the interface being Aptitude.

---

### Post by Sophont on 2009-11-26
All distros have their particulars about how they handle things - that's what defines the various distros in the first place.

A distro like Suse already offers all of the above.

For Ubuntu one of the things that make it Ubuntu is having a useful desktop with the default 1 CD install complete with reasonable default apps. No time spent on making various decisions during install.
It's a choice - and many like it this way. Any further tweaking is fairly easy to do after install for those who actually care.
Ubuntu already tries to activate 3D after install and very few people need a Java IDE - and those who do are exactly those who know what and how to get it.

---

### Post by jerrylamos on 2009-11-26
Software selection?  No problem.  Install Ubuntu then go to:

Ta Da!

The Ubuntu Software Center!

How easy can it be.

Anyway, with 4 test pc's and wild Ubuntu updates I wind up installing Frequently!  I don't need a longer install.

Cheeers,  Jerry

---

### Post by Gina on 2009-11-26
No! I don't either!!

---

### Post by shakaran on 2009-11-26
+1 The user needs choice. Give it and Ubuntu gets many users.

---

### Post by seeker5528 on 2009-11-28
> **shakaran said:**
> +1 The user needs choice. Give it and Ubuntu gets many users.

You have the alternate install and the DVD install, how much choice do you need? :p

Later, Seeker

---

### Post by Swarms on 2009-11-29
Bad idea, Ubuntu is about simplicty (hence being for humanbeings) and the average user will just be confused with too many choices.

---

### Post by Gina on 2009-11-29
> **Swarms said:**
> Bad idea, Ubuntu is about simplicty (hence being for humanbeings) and the average user will just be confused with too many choices.+1

When changing from one type of OS to another the average user will have no idea what all the various apps are.  And by the time people know what they want they're experienced enough to install from the Software Center or Synaptic.  In fact I think the new Software Center shows a lot of promise :)  

The bye-word is KISS :)

---

### Post by shakaran on 2009-11-29
> **seeker5528 said:**
> You have the alternate install and the DVD install, how much choice do you need? :p

Later, Seeker

I suggest a simple menu with normal/advanced options. If you click on advanced ubiquity shows a list where you can click some checkbox with programs (for example, Gimp, Openoffice, etc).
Just like that.

---

### Post by Gina on 2009-11-29
> **shakaran said:**
> I suggest a simple menu with normal/advanced options. If you click on advanced ubiquity shows a list where you can click some checkbox with programs (for example, Gimp, Openoffice, etc).
Just like that.Exactly what I suggested in another thread a while back :lolflag:

---

### Post by cariboo on 2009-11-29
I disagree, there should be no software selection during the install process. Most of the new users coming to Ubuntu probably haven't ever installed an operating system before. The process should be made as easy as possible for these new users. 

I have my list of programs that I install for every new version, so for me the installation process is fairly simple. For a new user, there is so much software available it can be overwhelming. 

I saw somewhere, that the idea was to have a Featured Software page in the software center, where Gimp and other programs could be prominently displayed so that the new usres don't miss out on some of the best software available.

---

### Post by Gina on 2009-11-29
Yes. The development of the UCS to complement a standard CD install to suit those new to Ubuntu (and Linux generally), has prompted me to change my mind.  Not that I need a reason :lolflag:  This is the right approach IMV :)

---

### Post by gnomeuser on 2009-11-29
> **seeker5528 said:**
> You have the alternate install and the DVD install, how much choice do you need? :p

Later, Seeker

And the source code and the tools to build your own.. and the option to use another distro.. and the option to do Linux From Scratch (a recommendable experience for users wanting to learn their exact tolerance for "choice").

Just saying "Choice is good and should just always be not only present but the default" is a poor argument with limited application in the real world.

---

