---
title: "Boot questions"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by shepppard on 2008-09-11
Hey Guys,

Not sure what you would call this or if it is possible but this is what I want to do.
I have 3 HDD in my System right now. What I want to do is Install Ubuntu on 1 and Win XP on the 2nd for gaming reasons... spore coming out and all... Now I love Ubuntu and using it as my primary os is great. This is for when I just need to brows the web and what not. And then use XP to game.
So here is what I want to do
Have to system always boot to Ubuntu without the stupid selection screen. Then from Ubuntu I can boot into Win XP. This configuration is exactly like what they do on the mac with boot camp.
I know I can run wine to get some stuff running but I play crysis and would rather just not bog down my system with all this stuff running.
So how would I manage to do this if it is possible. I'm pretty new at all this Linux stuff so bare with me.

Thanks

---

### Post by Scunge on 2008-09-11
Ok, first of all, you don't need to have a separate HDD for each OS, this is what "partitions" are for - basically you split up your HDD into sections and you can install Windows on one and Ubuntu in another.

Second, if you don't want unnecessary overhead, then you don't want to boot into Ubuntu and then boot into Windows. Instead, you want to boot straight into Windows **or** Ubuntu (which does mean that if you are in Ubuntu and want to play a game in Windows, you need to reboot).

I wrote a long answer [**[color=blue]in this topic[/color]**](http://ubuntuforums.org/showthread.php?t=912040) for someone else who wanted to do a dual-boot with Windows and Ubuntu, and talks about partitioning all on one HDD. Also, contrary to the order you mentioned in your post, you should install Windows **first**, as I describe in that other thread. You can do it the other way, but it adds a big complication later, so it's easier to just do it the "right" way.

Ignore the stuff about a third OS, but you might still like to have a "spare" third primary partition for future OS trials, or in the meantime simply a FAT32 spare storage area.

See if that, or anything else that others have posted, helps you to move forward here.

But check your disk space and if it's tight with the example figures I use, post back here and people can advise on exactly what partition sizes to use.

Now, I know you said you don't want the "stupid selection screen", but you have to choose your OS at some point if you don't want to run wine. As it stands, you can press ESC when it says during bootup in order to bring up that selection menu, and if you're happy to do that then you don't need to make the following change.

But to make that menu appear, once you've got all the installations sorted, log into Ubuntu and go to **Application > Accessories > Terminal**. In the window that opens up, enter ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.safe
```and enter your password. Then type ```
sudo nano /boot/grub/menu.lst
```

In that editor, use the cursor keys to scroll down to the line that says "hiddenmenu". So add a hash and a space (i.e. "# " without the quotes) at the start of that line, and it will bring up the menu of OSs and you select the one you want.

Whether the menu is shown or not, if you do nothing for 3s, it will go into Ubuntu by default, so you only need to pay attention to it if you want Windows.

But something else in that file is also useful to edit if you find 3s too quick - the line starting "timeout". Change that to 10 or something.

If you screw it up, you can always get back how it was by default by doing ```
sudo cp /boot/grub/menu.safe /boot/grub/menu.lst
```

Hope that helps.

---

### Post by caljohnsmith on 2008-09-11
> **Scunge said:**
> Ok, first of all, you don't need to have a separate HDD for each OS, this is what "partitions" are for - basically you split up your HDD into sections and you can install Windows on one and Ubuntu in another.

I agree that shepppard doesn't necessarily need to have extra HDDs, but if he wants to use them and give each OS its own HDD, I don't think we should discourage him from doing so. :)

---

### Post by Scunge on 2008-09-11
Yes, true. So if you do that, shepppard, make sure you have the Windows HDD still connected when you do the Ubuntu installation, and I presume you know about things like "master", "slave" and "cable select"? If not, just post back...:)

---

### Post by shepppard on 2008-09-11
Well Guys thanks for the help. I really didn't even consider this option.

Now the reason for Multiple HDD's (1 for Linux 1 for Windows) is that 
A-I hate partitioning HDD's I find it useless and gives me a false sense of security
B-I like the fact that if my Linux HDD crashes then I can replace it without screwing up my windows installation and vise versa.

Plus I don't really need any speed for my linux distro but I want my windows gaming system to be crazy fast... hence it will probably be a ram disk but that is a whole other project I'm thinking of.

Thanks for the thoughts though

---

