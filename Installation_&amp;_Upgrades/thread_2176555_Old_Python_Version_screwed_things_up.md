---
title: "Old Python Version screwed things up"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by noisysoul on 2013-09-24
Greetings from Chile :)

Everything has been ruined by an old version of Python and so I beg you to help me. Please allow me to give you some background information first.

I used Ubuntu for 2 years and after doing some distro-hopping, I've been using (Arch-based) Manjaro for a while. Therefore I've lost track of newer Ubuntu packages and versions. Don't get me wrong, I like Ubuntu and I know how to use the terminal (at least basic commands like cd, sudo, apt-get and so on), yet I'm really going to need your help in order to solve this hell of a problem.

A friend brought me today his Ubuntu-powered laptop (12.04) because he needs (IDLE) Python in order to do some tasks for college (he's in an engineering program). The thing is I previously installed Python 3.2 a long ago so that he could use it without any problem. Unfortunately, he told me that his professor is now asking everyone to use ONLY Python 2.7.5 (which from my point of view is stupid as the newer version can perfectly do whatever he may need to do). Consequently, he must have (IDLE) Python 2.7.5 running in his laptop. (Windows is a choice we'd like to avoid).

First, I uninstalled the newer version with USC, then I downloaded and installed a couple of .deb files I found within Ubuntu's repositories in order to get Python 2.7.5 working properly (through Gdebi and the terminal). Once again, dependencies ****ed my life and I really messed things up trying to fix the problem. I now cannot run USC or the update client, yet I can use the terminal and Synaptic.

If I try to remove the old package in conflict, it says it would also remove Unity and most of Ubuntu's main components (I understand Python is widely used there, but I don't want to ruin the entire system). I really don't know that to do, I've read tons of posts and articles on the net. I even tried the following commands, yet I couldn't work things out...

sudo apt-get update
sudo apt-get upgrade
## both with and without -f

sudo apt-get -f install
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get --fix-broken install
sudo rm /var/lib/apt/lists/* -vf
sudo dpkg --configure -a

I even installed newer glibc packages. Dependencies are still in conflict while packages keep on breaking (5 by now as I could fix 2) :(

If you have any ideas, please let me know about them so that my friend doesn't fail his only programming course.

I just want to install (IDLE) Python 2.7.5 and be able to install updates from the other packages without destroying the while OS.

Thank you so much!!

---

