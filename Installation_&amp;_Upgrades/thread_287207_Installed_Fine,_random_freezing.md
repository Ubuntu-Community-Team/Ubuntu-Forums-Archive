---
title: "Installed Fine, random freezing"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by robertwoes on 2006-10-28
I installed Dapper off of the live cd.  the computer froze up completely during the installation, like 5 times, but finally it installed and i booted into gnome.  I clicked around, and it was great.  very fast and responsive.  I clicked on a few openoffice documents and read through them, looked at powerpoint presentaion, then clicked on a movie file and when it started playing fine.  I clicked on the titlebar of the active window and started to move it across the screen and the computer completely locked up.  I couldn't even jump to a terminal or move the mouse or nothing.  I rebooted and everything was cool again. i started nautilus and began navigating around the filesystem and like 20 minutues into my fun, it completely froze again!  How do I determine what is causing this?  I checked around the forums and i see a lot of people are having difficulty installing, but i am past that point.  It runs great and i love it, but out of nowhere, it just locks up !  Thank God i dual boot, and can come here to ask you nice people.  
Any help would be appreciated.  How do i even begin to diagnose the problem?
Robert

---

### Post by robertwoes on 2006-11-08
OK, I think I may have isolated the problem.  I have an ATI Radeon 9200 SE video card.  I was looking around the forum to see how I can get 3D graphics on my desktop, and I realized that is probably what is going on here.  So I changed my xorg.conf from using "ati" to "vesa" and all of the freezing and locking up stopped.  So I went to ATI's website, and the current driver doesn't support my video card.  It is too old.  I asked around about how others got it working and, to be honest, it's too complicated for me at this point.  So, I am just going to save up and get NVIDIA.  This ATI problem is getting tired.  I have been dealing with cruddy 2D junky video since 1999, when I first started using Linux on my desktop.  Enough is enough.  I am just going to research my hardware better before I buy.  Hasta la vista, ATI & linmodems.  Sick and tired of it all.

---

