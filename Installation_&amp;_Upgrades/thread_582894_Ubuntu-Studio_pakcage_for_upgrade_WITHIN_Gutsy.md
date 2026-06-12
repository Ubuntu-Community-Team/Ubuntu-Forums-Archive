---
title: "Ubuntu-Studio pakcage for upgrade WITHIN Gutsy"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Shlomir on 2007-10-20
I had Ubuntu Studio working with Fiesty, now I'm on Gutsy (gutless), when I try to upgrade the Ubuntu Studip packages, it says that all of them need dependencies which aren't avaialble and it won't install anything...

Is this becuase the Repos are all stuffed, or is it just the fact that Gutsy won't run Ubuntu Studio just yet?

Basically when I go to install the Ubuntu-studio-audio, graphics and video packages thru Synaptic, most of them don't have dependencies, but should it locate and install them all, instead of bombing out so quickly?

This is getting frustrating!@#$!

---

### Post by MetalMusicAddict on 2007-10-20
> **Shlomir said:**
> I had Ubuntu Studio working with Fiesty, now I'm on Gutsy (gutless), when I try to upgrade the Ubuntu Studip packages, it says that all of them need dependencies which aren't avaialble and it won't install anything...

Is this becuase the Repos are all stuffed, or is it just the fact that Gutsy won't run Ubuntu Studio just yet?

Basically when I go to install the Ubuntu-studio-audio, graphics and video packages thru Synaptic, most of them don't have dependencies, but should it locate and install them all, instead of bombing out so quickly?

This is getting frustrating!@#$!

Remove the specific ubuntustudio repo line in your sources.list. All of the packages are now in the official Ubuntu repos.

---

### Post by Shlomir on 2007-10-20
It fonud nothing, could you please specifiy exactly what these repos are?

---

### Post by MetalMusicAddict on 2007-10-20
Post your sources.list.

---

### Post by santiagogaitan@gmail.com on 2007-10-20
I'm using ubuntustudio on ubuntu 7.4.

I can't  update to gusty nor to download the repos of the gusty ubuntustudio.

It seems that i lost the update manager.

How can i do to get the ubunutstudio 7.10?

---

### Post by Shlomir on 2007-10-21
Apparently the distros and repos are stoofed, from the website:

A Message From The Emergency Broadcast System.

October 19th, 2007

UbuntuStudio.org is dealing with unforeseen hosting issues. Please be patient.

---

### Post by MetalMusicAddict on 2007-10-21
> **Shlomir said:**
> Apparently the distros and repos are stoofed, from the website:

A Message From The Emergency Broadcast System.

October 19th, 2007

UbuntuStudio.org is dealing with unforeseen hosting issues. Please be patient.

No. That's not what it means. It only refers to why the site hasn't seen a graphic change. If you're using Ubuntu Studio-Feisty and want to go to Gutsy remove the specific ubuntustudio repo line and update to Gutsy like you were using normal Ubuntu. All the updated Ubuntu Studio-Gutsy packages are in the Ubuntu repos now.

---

### Post by Shlomir on 2007-10-21
Can the upgrade be done within Gutsy via the LiveCD?

i.e If I build a Ubuntu-Studio CD/DVd, can I simply upgrade Ubunuut Studio off the Cd within the desktop, or do I have to rebuild the whole OS?

---

### Post by santiagogaitan@gmail.com on 2007-10-22
> **MetalMusicAddict said:**
> No. That's not what it means. It only refers to why the site hasn't seen a graphic change. If you're using Ubuntu Studio-Feisty and want to go to Gutsy remove the specific ubuntustudio repo line and update to Gutsy like you were using normal Ubuntu. All the updated Ubuntu Studio-Gutsy packages are in the Ubuntu repos now.

Thank's!

I'm an ubuntu beginner... how can i remove the feisty ubuntustudio repos? (i think that since  i install them, i lost the natural update manager of ubuntu feisty).

---

### Post by Seamless in Northampton on 2007-11-08
Perhaps I'm being thick, but then I'm a newbie to Ubuntu. I've been running Feisty Fawn with an upgrade to Ubuntu Studio, then I removed the old U.Studio repos from Software Sources and did the auto upgrade to Gutsy.
 
It looks for all the world as if I haveupgraded Ubuntu Studio packages, but I'm not quite sure how to tell. Is this indeed an automatic upgrade of all of the Studio packages as well? From this post, it sounds that way, at least. If so, that was darned easy! Of course, now I can't get the low latency kernel to load the GUI, but that's another post, methinks.

---

