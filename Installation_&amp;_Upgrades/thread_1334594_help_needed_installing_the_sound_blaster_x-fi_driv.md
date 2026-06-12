---
title: "help needed installing the sound blaster x-fi driver"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by echo11381618 on 2009-11-22
I am very new to using linux. I have wanted to switch for sometime now and did't due to fears of compatibility with some of my hardware. I recently however got fed up with windows and decided to just commit. After it was installed every thing seemed to run fairly smooth. However, I am now to the point where I would like to have my sound card working (and not have to buy a new one). it's a sound blaster x-fi platinum and I have already downloaded and extracted the compressed file for linux (.tar.gz)from the creative web site. In the terminal i tried to use the sudo apt-get build-dep command but it gave me the error "unable to find a source package for XFiDrv_Linux_Public_US_1.00" (that is the name of the file after extraction) Their readme file is less than helpful especially for a noob like myself. It simply states:
     
     In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install

I would greatly appreciate any help that is given. please remember that i am completely new to using the terminal and will not understand what you are explaining unless the instructions are very explicit. Thank You.

---

### Post by audiomick on 2009-11-22
I am guessing a bit.
When you do something in the terminal, like for instance opening something to edit it, you have to do it from the point in the file system where the file in question is stored. It looks like this is your problem.

I assume you know where the file is that you are trying to build.
In the terminal, you will see a cursor like this:
your_user_name@your_computer_name : ~$

and you are in your home folder.

if you enter ```
ls
```,
you will see its' contents.

```
cd name_of_a_folder
```
will move you "downwards" into a folder.
```
cd ..
```
will move you up one

you need to use this to get to where the file is, then do the build command again

---

### Post by echo11381618 on 2009-11-22
Thanks for all your help! I was able to install the driver after navigating to the correct folder and then using the:

[COLOR="Red"]sudo make[/COLOR]

command followed by the:

[COLOR="Red"]sudo make install[/COLOR]

[COLOR="Red"]sudo apt-get build-dep[/COLOR] was not needed.

I am having another issue now. when I restarted the computer, I now get the drum sound that ubuntu makes at the user login screen, but when i try to play music with rythmbox or on youtube i still get no sound. I know I did something right since it would't make any sound at the login screen before, but it should also play music. will i need to try and re-install it? or is there another fix?

Thanks again for all your help.

---

### Post by lionheardt on 2009-11-24
I seem to be having the same problem but this explanation hasnt helped... I must be a real noob     any help would be great!!!

---

