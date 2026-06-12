---
title: "How do I run X configure??"
date: 2005-04-04
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-04
I would like to run the X configure program for Ubuntu.

I have read "Unofficial Ubuntu 4.10 Starter Guide" but nothing were mentioned about configure!! Would it not be rather appropriate to have something like that in a Starter guide??

Where should I look to find such basic information when they are not supplied in the Starters Guide?

---

### Post by erkki70 on 2005-04-04
Hi,
in case you need to configure your X server, you have to type the following command in a terminal or console:
```
sudo dpkg-reconfigure xserver-xfree86
```
Enter your password and here you are, you can configure. ;-)
This applies for Warty which runs XFree86. 
For Hoary wich runs Xorg it's the same command but you must replace -xfree86 with -xorg.

I think that you should also use the search tool on the forum and not only rely on only one source for documentation, eg starter guide as it is a work in progress and also very general.

I'm sure you'd find a lot of useful info just selecting the appropriate forum section, in your case: 
[http://www.ubuntuforums.org/forumdisplay.php?f=43]("http://www.ubuntuforums.org/forumdisplay.php?f=43")

In case you're refering to this:
[http://www.ubuntuforums.org/showthread.php?t=23570&highlight=configure]("http://www.ubuntuforums.org/showthread.php?t=23570&highlight=configure")
It's a totally different story... :wink:
 > After having a look to your other posts... 
Ok, it looks like you need to set your Danish keyboard.
The first command will do fine.:D

If you want to receive help, you need to be more precise in your requests and give infos and details, preferably with attached files if possible. (just as you did when posting your .conf file).

Hope this helps.

Cheers,
Erkki

---

### Post by az on 2005-04-04
sudo dpkg-reconfigure xserver-xfree86


Or, on Hoary

sudo dpkg-reconfigure xserver-xorg

---

### Post by bigblop on 2005-04-04
Where do I look for basic information like this so I don't have to fill this group with these newbie questions all day long.

I tried the "Unofficial Ubuntu 4.10 Starter Guide" but nothing was mentioned there. Is there a more comprehensive manual that I don't know of or is the only way to find out about such things to ask?

---

### Post by bigblop on 2005-04-04
> **erkki70]Hi,
in case you need to configure your X server, you have to type the following command in a terminal or console:
```
sudo dpkg-reconfigure xserver-xfree86
```
Enter your password and here you are, you can configure.  said:**
> http://www.ubuntuforums.org/forumdisplay.php?f=43[/url]

In case you're refering to this:
[http://www.ubuntuforums.org/showthread.php?t=23570&highlight=configure]("http://www.ubuntuforums.org/showthread.php?t=23570&highlight=configure")
It's a totally different story... :wink:
  
Ok, it looks like you need to set your Danish keyboard.
The first command will do fine.:D

If you want to receive help, you need to be more precise in your requests and give infos and details, preferably with attached files if possible. (just as you did when posting your .conf file).

Hope this helps.

Cheers,
Erkki



Thank you!

Regarding to my Keyboard problem I have just run the reconfigure program but it does not help.

I noticed that in the configure program it was possible to define keys for various functions. Maybe its possible to get the Alt-Gr key assigned to the function that I wan't eventhough it seems as bit of hack. Do you know how to make Alt-Gr work together with other keys when I would like to type AT, tilde, pipe, backslash etc?

---

