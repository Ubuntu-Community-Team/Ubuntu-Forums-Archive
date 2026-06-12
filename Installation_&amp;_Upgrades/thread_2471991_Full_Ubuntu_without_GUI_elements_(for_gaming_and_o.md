---
title: "Full Ubuntu without GUI elements (for gaming and other stuff)"
date: 2022-02-15
forum: Installation &amp; Upgrades
---

### Post by naq2 on 2022-02-15
I want to install Ubuntu without GUI elements. I would use it for my gaming laptop so efficiency is important. also I want to customize it what ever I want, so I don't want to download unnecessary softwares. Most of the time use terminals but applications like Steam, dc and Firefox should work as normal.

IMPORTANT:
    While installing, EVERYTHING from my computer should disappear (files and Windows) so I can start from clean table
        Ok, I know how Linux installation works and it's default to remove everything from disk, but to make sure :)
    At start no GUI, I want to build it by myself.
    Terminal based desktop environment (you know, terminals everywhere to control computer [using something like i3])
    OS and GUI should be efficient and lightweight
    No unnecessary applications, I want to download those when I need it.
    Steam, dc, Firefor and other common applications should work

My plan:
    Install base Ubuntu, no GUI (Nothing too fancy, just that core Ubuntu works and it's easy from there to upgrade and customize)
    Install necessary softwares (drivers, voice control, media players, Firefox, Steam)
    Use terminals and window manager (maybe i3) as desktop environment
    customize :)

Problem is that I don't know what Ubuntu version I should download. Here is my thoughts.

Ubuntu desktop (minimal installation):
    + Easy to install
    - I don't want the GUI and unnecessary softwares.

Ubuntu mini CD:
    Good but outdated

Ubuntu server:
    + No GUI
    - It's mainly for server usage, not for home computer. (Maybe?)
    - I read that there comes softwares for server usage, I don't want those.

If I can use Ubuntu server for normal desktop, laptop, pc efficiently, please tell me how and where to start :D

Otherwise what would you suggest on this installation thing?
And about i3 desktop environment? Is it lightweight? Some tips for building terminal based environment?
And can I use applications like Steam easily?

(Bonus: Should I use Fat32 or ntfs? Fat32 is pretty outdated but ntfs for Linux might not be stable. I don't have to transfer data between Linux and Windows, just for personal use.)

---

### Post by MAFoElffen on 2022-02-15
I regret to say that it seems like you have done a lot of reading on the internet which is now very outdated. There are some good ideas, though they are a bit scattered and disjointed. Some other very basic points to your plan will not work for what you want to do, because the logic conflicts with the basic functions of what needs to be there, for what you want to do...

I am being truthful, sincere and kind. I am patient, and if you have the time to read a lengthy response to this, I will have to gather my thoughts on where and how to start to fill the holes in what you have said... Hopefully without offending you. And so that it addresses everything that you have said, in a way that makes sense. It will take a while to prepare a response to all you have said and asked about...

But I think after you read my response to this, you will see what will work, and what will not, and learn enough to make your own decisions on where you can go from there...

Does that sound like a good plan? If not, then I'll let someone else explain things to you...

---

### Post by naq2 on 2022-02-15
It's so kind that you help me! I knew this takes some time and I'm ready to hear your thoughts.

---

### Post by MAFoElffen on 2022-02-15
This post will not be on What or how to install, nor answer any of your questions yet... It will ask questions on information that you left out of your first post, to be able to answer any of the questions you asked, and to be able to address what you said...

What are the hardware spec's of what are you planning to install all this on?

What will be it's job? (What will it need to do when it is done?)

What is your skill level and experience with Linux and Bash CLI?

---

### Post by naq2 on 2022-02-15
Acer Nitro AN515-53
Intel(R) Core(TM) i5-8300H CPU @ 2.30GHz   2.30 GHz
Ram 8Gb
NVIDIA GeForce GTX 1050
1 Tb space
Windows 10 64-bit

I want to use my computer, like normal people do. Play Steam games, talk in discord, go to internet and watch Youtube videos. Maybe some bit of coding, but I usually program on Godot game engine.
Sometimes I program Python and very rarely C++. Games are important thing, not just because I want to play those, but also make games. So Godot, Blender and other game making softwares should work (Those I can download from Steam, so mainly Steam is the thing)

My skill level is on really basic. I know some basic stuff about Linux and Bash. I know few useful bash commands but I'm not really familiar with it. But that's why I want to learn it.
(So pretty much noob)

Hopefully this answers on what you asked :)

---

### Post by The Cog on 2022-02-15
My advice would be to install Linux with a GUI - a lightweight GUI like Lubuntu or Xubuntu. I think you would sorely miss some of the "un-necessary" GUI utilities like a network manager, volume control, configure the time zone etc. You will have your work cut out getting used to Linux and don't need the extra grief of doing it all with lots of utilities missing. They don't slow things down much but their absence will hurt you a lot.

> Bonus: Should I use Fat32 or ntfs? Neither. Linux cannot run on either of those. Use ext4. Let the LInux installer do the formatting - don't try to format partitions first. You may find it convenient later if you have a separate /home partition (maybe 900G) for easier upgrades, the same way people use C: and D: for system and userdata. But that's not critical.

---

### Post by naq2 on 2022-02-15
Thanks for suggestion! I thought that lightweight GUI thing, so I get those volume control etc. applications. However I want to build or customize the GUI by myself and I really don't like to keep unnecessary GUI elements in my computer storage. Should I delete all GUI elements and then start to build? Or should I just let them be and make new desktop environment where my computer boots up?

---

### Post by ActionParsnip on 2022-02-15
I suggest LXDE. Its super light and will leave more resources for your applications. Once you install the minimal or server OS, run
```

sudo apt update
sudo apt -y full-upgrade
sudo apt install -y lxde

```

Select the DM you like (The default is fine) when asked, then reboot and enjoy

---

### Post by naq2 on 2022-02-15
Hey, I think I found what I wanted! I'm so glad there here is a lot of people who have helped me. Thanks for everybody. :D

---

### Post by MAFoElffen on 2022-02-15
> **naq2 said:**
> I want to install Ubuntu without GUI elements. I would use it for my gaming laptop so efficiency is important. also I want to customize it what ever I want, so I don't want to download unnecessary softwares. Most of the time use terminals but applications like Steam, dc and Firefox should work as normal.

IMPORTANT:
While installing, EVERYTHING from my computer should disappear (files and Windows) so I can start from clean table
Ok, I know how Linux installation works and it's default to remove everything from disk, but to make sure
At start no GUI, I want to build it by myself.
Terminal based desktop environment (you know, terminals everywhere to control computer [using something like i3])
OS and GUI should be efficient and lightweight
No unnecessary applications, I want to download those when I need it.
Steam, dc, Firefor and other common applications should work

My plan:
Install base Ubuntu, no GUI (Nothing too fancy, just that core Ubuntu works and it's easy from there to upgrade and customize)
Install necessary softwares (drivers, voice control, media players, Firefox, Steam)
Use terminals and window manager (maybe i3) as desktop environment
customize

Problem is that I don't know what Ubuntu version I should download. Here is my thoughts.

Ubuntu desktop (minimal installation):
+ Easy to install
- I don't want the GUI and unnecessary softwares.

Ubuntu mini CD:
Good but outdated

Ubuntu server:
+ No GUI
- It's mainly for server usage, not for home computer. (Maybe?)
- I read that there comes softwares for server usage, I don't want those.

If I can use Ubuntu server for normal desktop, laptop, pc efficiently, please tell me how and where to start

Otherwise what would you suggest on this installation thing?
And about i3 desktop environment? Is it lightweight? Some tips for building terminal based environment?
And can I use applications like Steam easily?

(Bonus: Should I use Fat32 or ntfs? Fat32 is pretty outdated but ntfs for Linux might not be stable. I don't have to transfer data between Linux and Windows, just for personal use.)
From what you have said, let me weed through a few things... and reword it in a way that makes more sense.

I read this as you want to install an Ubuntu Base system and install the layers and pieces of what is there on your own. You want to start out and console based, without any graphics or GUI based applications, so that you can add them as you need them.

As a goal, you want to end up with a GUI Desktop and GUI applications that you have chosen, installed and configured. Sonething that you can Game on, surf the web, etc.

Before you do anything, I would backup everything you have, so that if later, you find you needed "something", you haven't lost it.

What you are looking at, that makes sense for you to start is to use the Ubuntu Server LiveCD and install a "minimal server" install. That will install a base system that is console based, wihtout much fluff or bloat. 

What I would suggest when you get to the partitioner, is that you choose "other", delete all the partitions there, then create new partitions for your EFI boot, root... and then selct LVM to create LV's for root, home and swap, then mount those used as / (root), /home and swap, respectively. 

While there, you will need to pick a filesystem type... Linux will not boot from anything except a Linux type filesystem. It will not boot a boot or root that is fat, fatXX or NTFS. Standard is ext4. I prefer that. I have done BTRFS, but that is not a fast/performance type of filesystem that I would choose if you want to do gaming. Your Home directory can be anything... But if all you are using is Linux, why not just keep it as ext4?

...Then install it. The one app I would install from that install is openssh-server, which will just be a checkbox along the way in that install.

You will end up with a small, slim, Ubuntu based console system. One that you will have to login and do all commands from Bash CLI. All text.

This assumes that you know Linux commands and what they do... If you do not have much expereince with Linux commands, you will be forced to learn them, because it will not do anything you do not tell it to. (explicitly)

To install the Linux Graphics Layer, for the way you want to do it... you need to do it a certain order. Install the graphics server (XServer, the DM (Desktop Manager = the graphical login manager), then the Desktop Manager.

The i3 Desktop Environment is for advanced Users... There is a lot of manual configuration and scripting to be done to set it up and maintain it. That is what makes it lightweight. There is nothing interpreting it or helping to configure it behind the scenes. If there is a problem with it, it was probably a typo somewhere by whoever set it up (you)... That's why they say it is for Dev's and Advanced Linux Users. You customize it to whatever. Me and my son like it, but we are both System Engineer levels of experience. I would not recomend it for new users.

Even if you do install i3, I would install LXDE-QT as a backup DE. That way you have a lightweight Desktop while you are creating, confgiuring, and (yes) debugging i3 (getting it to work like you want it to).

The DM. Such as LightDM, is lightweight and will allow you you switch between your desktops at login... just because multiplw desktops are installed, does not mean they are taking resources, except a bit of diskspace...

If, on Server you just did
```

sudo apt install lxde-qt

```
That would install XServer, a DM, the LXDE-QT DE and a very slim, light suite of utilities and applications... That would get you going with something very basic and fast, until you build your skills and experience up.

The thing about Linux that I love... Is that it is infinitely customizable. What you start out with doesn't matter. You can add, change, customize  and remove pieces as you wish (within logic and reason). You can personalize it and make it your own. You can have 10 desktops installed and switch between. Custimize your Grub Boot menu, Animated Splashes, Desktop Themining... Applications that you want to learned and use... Whatever.

Welcome to the adventure.

EDIT: Just read your post... I also have "Blender". LOL

---

### Post by naq2 on 2022-02-16
Thank you so much! I really appreciate your effort. I will keep this in my mind.

---

### Post by Impavidus on 2022-02-16
The normal lightweight desktop environments are already designed to work well on computers that are 10 or even 15 years old. The resources used by something like LXDE-QT are insignificant compared to what's used by games and what's available on your system. Going even lighter won't make a significant difference. Don't worry that you may be wasting 3GB of hard drive space on a GUI that you don't really need. There's still 997GB left for other uses.

---

