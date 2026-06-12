---
title: "About to install - tips for a newbie?  + some questions"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by nbakewell on 2008-07-17
Hey everyone!  I've been using Windows ever since I started getting on the computer, with the exception of browsing the internet on Red Hat 5 in some general computer labs, and now I am ready to make the (partial) switch to Linux.  I've long since considered it, and my next CS class is all about bash and using the command line on Linux, so I figured now's a great time to start.

Anyways, my desktop at home has two hard drives, so one i'm going to keep running XP and the other one i'm going to install Ubuntu on.  I've downloaded the latest release, burned the ISO, read through the installation docs and general help docs, and now I think i'm ready to try.  But I have a couple of questions before I do...

First, any general advice for a first-timer?  Tricks or tips with the installation & initial use?  I'm backing up all my data on an external HD just in case, even though if my Ubuntu installation goes bad it shouldn't effect my other HD.

Second, and I know this is a newbie question, but I can't seem to find a straight answer - is it possible to switch Ubuntu  between gnome, kde, xfce, etc?

How does Linux/Ubuntu handle themes?  Is it as easy as downloading a provided theme and running some simple installer, or is the process more complicated?

Thanks!  Hope to have everything running nicely in a couple of days :)

---

### Post by chalewa on 2008-07-17
> **nbakewell said:**
> Hey everyone!  I've been using Windows ever since I started getting on the computer, with the exception of browsing the internet on Red Hat 5 in some general computer labs, and now I am ready to make the (partial) switch to Linux.  I've long since considered it, and my next CS class is all about bash and using the command line on Linux, so I figured now's a great time to start.

Anyways, my desktop at home has two hard drives, so one i'm going to keep running XP and the other one i'm going to install Ubuntu on.  I've downloaded the latest release, burned the ISO, read through the installation docs and general help docs, and now I think i'm ready to try.  But I have a couple of questions before I do...

First, any general advice for a first-timer?  Tricks or tips with the installation & initial use?  I'm backing up all my data on an external HD just in case, even though if my Ubuntu installation goes bad it shouldn't effect my other HD.

Second, and I know this is a newbie question, but I can't seem to find a straight answer - is it possible to switch Ubuntu  between gnome, kde, xfce, etc?

How does Linux/Ubuntu handle themes?  Is it as easy as downloading a provided theme and running some simple installer, or is the process more complicated?

Thanks!  Hope to have everything running nicely in a couple of days :)


hi, welcome

yea it is definitely possible to switch between gnome, xfce whatever window manager you like, you just have to log out and log back in with the different manager. 

as far as themes go the potential is limitless. desktops are like snowflakes, you will never see two alike. but to answer your question, yes they are relatively easy to install. essentially you just have to drag and drop. compiz is slightly more complicated, but not much. 


as far as tips go, just be willing to learn, keep an open mind and have fun

---

### Post by nbakewell on 2008-07-17
Thanks chalewa!  Would installing multiple window managers (even though you're only running one at a time) slow system performance?

---

### Post by chalewa on 2008-07-17
> **nbakewell said:**
> Thanks chalewa!  Would installing multiple window managers (even though you're only running one at a time) slow system performance?

nah wouldn't slow a thing as far as i know, i mean it will take up some more space on the HD, but not much at that even. 

now some window managers are faster than others.. xfce, fluxbox, and some other super light window managers are lightning fast.

---

### Post by snowpine on 2008-07-17
> **nbakewell said:**
> Thanks chalewa!  Would installing multiple window managers (even though you're only running one at a time) slow system performance?

Welcome to the forums! Ubuntu only loads the packages that are needed for the active window manager, so there is no performance "hit" (except for the hard drive space used) having multiple windows managers.

One other cool thing about Ubuntu. Let's say you are logged in to a Gnome session, then you want to run a KDE application (for example). At that point, Ubuntu loads the necessary KDE dependencies (which will of course use up some extra RAM). But you don't need to quit the gnome session to run KDE/Xfce/whatever applications.

One other thing, you probably know this already, but Ubuntu=Gnome, Xubuntu=Xfce, Kubuntu=KDE. Let's say you originally installed Kubuntu and are loving KDE, but you want a Gnome desktop as well. You can open a terminal and enter 'sudo apt-get install ubuntu-desktop' to get the entire Ubuntu Gnome desktop environment (including lots of apps, themes, etc) or 'sudo apt-get install gnome-core' to just get the basic windows manager, allowing you to log in to a gnome session.

Hope that helps you!

---

### Post by nbakewell on 2008-07-17
Ok so Linux apps are developed specifically for either gnome, xfce, kde, etc?  And some apps work on all of them (like say OpenOffice) but some only on a particlar windows manager?

---

### Post by snowpine on 2008-07-17
> **nbakewell said:**
> Ok so Linux apps are developed specifically for either gnome, xfce, kde, etc?  And some apps work on all of them (like say OpenOffice) but some only on a particlar windows manager?

You are more or less correct, yes. All applications depend on certain packages. But the beauty of the system is that, when you install an application, it will also install whatever additional packages are required. So you should be able to install, say, an Xfce application in Kubuntu. 

Generally speaking, the applications that are bundled with a particular "distro" will be optimal in terms of system resources, because all dependencies will be met without installing additional packages. But there is no harm in "importing" applications from other distros.

Many of us use multiple windows managers (personally I switch between Fluxbox and Gnome) all the time with no problem whatsoever.

---

### Post by nbakewell on 2008-07-17
Great, thanks everybody!  Any final things I should know before I install Ubuntu on my second hard drive?

---

### Post by lukjad on 2008-07-17
Make a backup, just in case. I don't want to scare you but things can go wrong. Either copy your files to an external HD or write them to *ROM for safe keeping.

---

### Post by nbakewell on 2008-07-18
Real quick, do I need to format my drive to fat32 before I install Linux or does it run fine on NTFS?  I just read that Linux can only read files on ntfs, and not write.

---

### Post by nbakewell on 2008-07-18
Or must it be ext3?  I've never heard of that format before.

---

### Post by SunnyRabbiera on 2008-07-18
You can keep your ntfs in your windows partition, it will work.
Ext3 is a filesystem like ntfs or fat, though doesnt need defragging

---

### Post by nbakewell on 2008-07-18
I just formatted it to fat32, which completed fine.  I tried to format to ext3 but it says "The parameter is not valid."  I was reading through previous threads here and everyone seemed to say that NTFS would not work.  But if it does indeed, which one is better to run Ubuntu on, ntfs or fat32?

---

### Post by nbakewell on 2008-07-19
When I use the /hep command for format it says that my only available options are fat, fat32, and ntfs.  Is ext3 something that I have to reformat as once I already install Linux?

---

### Post by jolx on 2008-07-19
u format ur drives when ur installing

---

