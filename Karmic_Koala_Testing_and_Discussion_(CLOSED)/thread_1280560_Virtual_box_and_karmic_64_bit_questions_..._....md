---
title: "Virtual box and karmic 64 bit questions ... ..."
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2009-10-02
Hello.

I ma currently using jaunty, and downloading the 64bit beta of karmic, with the intention of installing it.

now i have virtual box installed and an xp vm set up, is there a way i can trnasfer the vm to the new system when i have it installed, with out having to go through the hassle of installing xp again ? I had wondered if i can save the .virtualbox folder thats in my home directory and then one the new system is installed, install vb and then put the file in my home directory, but for some reason this seems to simple a solution to me, so i thought i would check, so any advice would be appreciated.

the other thing is i like to have flash installed (an essential evil) and i also use the bbc's iplayer desktop, as far as i can tell there is a beta (or may have been alpha) version of flash for 64bit linux os's, and apparently you can install iplayer (which uses adobe air) on 64 bit machines, providing you install the 32bit libraries, so again any advice would be appreciated.

i have various how to's bookmarked (which i will save before i install karmic) but i would appreciate advice from anyone who has both the 64bit version of flash installed and iplayer as well.

cheers

---

### Post by HarrisonNapper on 2009-10-02
VirtualBox should store everything in a virtual hard drive file ending in .vdi or something like that.

---

### Post by jeroen.kurvers on 2009-10-02
I had a Win7 machine in Virtualbox on 9.04. When I did a new installation of karmic and installing Virtualbox, copying the .virtualbox folder back to my homefolder was enough to use my machine again.

---

### Post by HarrisonNapper on 2009-10-02
> **techno-mole said:**
> Hello.

I ma currently using jaunty, and downloading the 64bit beta of karmic, with the intention of installing it.

now i have virtual box installed and an xp vm set up, is there a way i can trnasfer the vm to the new system when i have it installed, with out having to go through the hassle of installing xp again ? I had wondered if i can save the .virtualbox folder thats in my home directory and then one the new system is installed, install vb and then put the file in my home directory, but for some reason this seems to simple a solution to me, so i thought i would check, so any advice would be appreciated.

the other thing is i like to have flash installed (an essential evil) and i also use the bbc's iplayer desktop, as far as i can tell there is a beta (or may have been alpha) version of flash for 64bit linux os's, and apparently you can install iplayer (which uses adobe air) on 64 bit machines, providing you install the 32bit libraries, so again any advice would be appreciated.

i have various how to's bookmarked (which i will save before i install karmic) but i would appreciate advice from anyone who has both the 64bit version of flash installed and iplayer as well.

cheers


Sorry, I got cut off before the full reply was made. You can check in your Settings which file type extension your VMs use and where they're stored and then just stick a copy somewhere. As far as flash is concerned, you needn't worry for the WinXP environment as long as it is 32-bit, but inside of ubuntu, Adobe has actually released a preliminary version of flash player for 64-bit. There's also a handy script for wrapping the 32-bit version, but that one's a bit of a cpu hog (-shakes fist at npviewer.bin-). 

Here's the link to adobe's: 
[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

---

### Post by techno-mole on 2009-10-02
cheers, i will see what happens, now all i need to do is actually get karmic to install, it gets to setting users and passwords, then just sits there at 26% and goes no further, this has happened twice so far.

i have checked the disc for errors and it didnt show any, so i am a little miffed to be honest.

cheers

---

### Post by mikewhatever on 2009-10-02
> now i have virtual box installed and an xp vm set up, is there a way i can trnasfer the vm to the new system when i have it installed, with out having to go through the hassle of installing xp again ? I had wondered if i can save the .virtualbox folder thats in my home directory and then one the new system is installed, install vb and then put the file in my home directory, but for some reason this seems to simple a solution to me, so i thought i would check, so any advice would be appreciated.

Is this another camouflaged Windows help request?

---

### Post by ubersolid on 2009-10-02
> **techno-mole said:**
> Hello.

I ma currently using jaunty, and downloading the 64bit beta of karmic, with the intention of installing it.

now i have virtual box installed and an xp vm set up, is there a way i can trnasfer the vm to the new system when i have it installed, with out having to go through the hassle of installing xp again ? I had wondered if i can save the .virtualbox folder thats in my home directory and then one the new system is installed, install vb and then put the file in my home directory, but for some reason this seems to simple a solution to me, so i thought i would check, so any advice would be appreciated.


Why don't you use the export function that VirtualBox has? Nothing could be easier. Then you just import it later.

---

### Post by techno-mole on 2009-10-07
> **mikewhatever said:**
> Is this another camouflaged Windows help request?

nope, i have stuff on my vm that i need for my photography work (works better on the vm than it does through wine) and i have stuff for my open university course, i would rather not go through the hassle of having to reinstall windows xp on a vm as it takes forever due to the monumental amount of updates that xp seems to need.

i am an avid user and supporter of linux based operating systems, i just wish i knew more about them than i do, although the open university does have a linux course waiting for approval, i will be taking it as soon as it becomes available.

---

### Post by techno-mole on 2009-10-07
> **ubersolid said:**
> Why don't you use the export function that VirtualBox has? Nothing could be easier. Then you just import it later.

thanks, found the feature you mentioned and i have now created the relevant files needed to import a vm when and if i change os, or version of os, i tend not to use the upgrade feature in favour of a flat out re-install from disc, i have less problems this way.

cheers for the help.

---

