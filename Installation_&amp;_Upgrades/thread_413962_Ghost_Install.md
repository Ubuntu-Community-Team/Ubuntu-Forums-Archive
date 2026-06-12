---
title: "Ghost Install"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by blazercist on 2007-04-19
I installed Feisty beta a while back and have been upgrading since and everything is peachy.  I have installed all the packages and configured everything the way I like it.

Now I have the untamable urge to make things go breaky breaky...

I was wondering if there was a way to write a ghost install of my current install to a DVD?  So that when I break everything I can just install back from the DVD and have everything the way it is now.

Edit: Let me make things clearer...  I have a dual boot Feisty/WinXP on my 100 gig harddrive in my laptop.  BOTH WINDOWS AND FEISTY ARE FRESH INSTALLS.  There are no programs or other crap that are not ABSOLUTELY ESSENTIAL, just drivers and a few tweaks and configurations done.  I want to ghost, JUST THE FEISTY partition to a DVD.  In case I need to I want to be able to copy from the dvd back to hard drive and have everything just the way it was.

Is this possible?  If so, how?

I'm sure that I'll be able to format the feisty partition in case it breaks,  I need to know how to copy everything under the hood to a DVD and I need to know how I would go about copying the files back onto the blank partition.

If I format the Feisty partition will i lose grub?  The menu.lst file is on the Feisty partition isn't it?  If so I will need a way to reinstall grub to the MBR as I would have to do the FIXMBR trick from the windows cd to get it to boot after removing Feisty.  

Any help or suggestions are appreciated.

---

### Post by Smuve on 2007-04-19
I've used partimage.  It's really easy to use, just pay attention to all the options, like file splitting and such.  We don't have to do that with ext3, but if you're putting anything on a fat32 drive, it could make a difference.  It allows you to create drive images and restore them.  Do a little research, but it's pretty simple.  

sudo aptitude install partimage

---

