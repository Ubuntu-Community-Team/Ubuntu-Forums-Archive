---
title: "How do i uninstall ubuntu server and install ubuntu desktop."
date: 2007-04-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by llamadog903 on 2007-04-15
I am using a G4 mac with OS X 10.4.9.  I installed ubuntu server but I want ubuntu desktop.  What do I do?

---

### Post by Scunizi on 2007-04-16
How about just installing the desktop and keep the server portion.  sudo aptitude install xubuntu-desktop or ubuntu-desktop or kubuntu-desktop or edubuntu-desktop.  I have a server installed on an old machine and use xubuntu there.  It's very fast. My other machine has ubuntu with gnome and kde base so I can switch around.

---

### Post by rogerrabbitsclone on 2009-03-04
i know im bringing to life a dead post, but i would like to know how to do this. my friend gave me the server edition telling me how much better it was then desktop, (he's the one who gave me desktop) and how all my data would automaticly transfer and all this nonsence. well i installed it, lost everything, and now neither of us can figure out how to uninstall it. but he's laughing. any help would be great, i really dont want to buy another hard drive.

---

### Post by Scunizi on 2009-03-05
By loosing all your date you mean there isn't ANYthing left of what you had on it previously? or are you just confused by the terminal prompt of the server addition?  Either way if you want the ubuntu desktop back that is pretty easy.. after logging in and getting the terminal prompt type sudo apt-get install ubuntu-desktop..  It will take a while and you will need an active internet connection on that machine.. When it's done you'll have to restart and then you'll have the desktop back.

---

### Post by grommmm on 2009-09-04
man this forum is useless

---

### Post by Jive Turkey on 2009-09-09
AFAIK the server edition doesn't import stuff from an existing OS installation.  Your friend steered you wrong and your data is lost from what I can tell.  There is no "uninstall" feature to the operating system.  What you can do is overwrite it with another install be it ubuntu Desktop, or OSX, or whatever you like.

If you want Ubuntu-desktop edition download and burn the correct CD image (the one with your correct processor type) put it in, and restart your computer.  It should boot to the live CD, follow the easy prompts and go.

---

### Post by grommmm on 2009-09-10
thanks for your suggestion. after letting ubuntu set up further 2-3 partitions with every install and mess up the desktop&server edition (server also started with gui, frozen), i formatted my disk and went back to windows. so much for the great all powerful linux with gread peer-to-peer support.

---

### Post by aimless_e on 2009-09-11
Just encase this thread remains open for others that have similar issues let me make clear the situation and define the solution.

Situation: Friend convinces you to try Ubuntu or you convice your friend that you are ready to give Ubuntu a try. You download or are handed a copy of what you think is the best version (yes there are a lot) and install it. But its not what you wanted, or your afraid of new things, or you downloaded server instead of desktop and your left with a black and white screen asking you to login.

Definitions: 

1. OS (operating system): A program or collection of programs that allow the user to interface with the hardware installed in the computer.[Linux(Ubuntu,etc.),Darwin(OSX),Winnt(XP and higher),Win32(win98,ME),etc.]

2.Ubuntu Server version: Is designed for people who wish to maximize the utilization of the computers hardware for server based operations. It does not start up the GUI by default or have any enduser applications to do day to day operations. 

3. Ubuntu Desktop: Is designed for people who wish to do day to day operations like word processing,email,listen to music,etc. It lacks some of the memory optimizations that Server uses but does allow for users to be "imported" from other OSes.

Note: Ubuntu and Linux is modular you can start with Server and install the desktop packages or vice-versa. YOU DO NOT HAVE TO RE-INSTALL THE ENTIRE OS.

 Solution:

During the install of ubuntu it allows you to setup the partition table to do one of three things.

1. Install Ubuntu beside existing OS found on harddrive/s this requires the original partitions to be resized to make room for Ubuntu.(allows import of users from other OS

2. Use the entire hard drive for ubuntu (does what you think) May or may not allow the import of Users

3.Manual Partitioning.

By default(for Desktop) it will install beside existing OS. If you reinstall Ubuntu after the original resizing of the hard drive it will install beside the original OS and the Version of Ubuntu you previously installed. This will continue until Ubuntu can no longer make new partitions or you run out of space on your hard drive. To avoid this go to manual partitioning and delete or reuse the partions that were created by the first install.

THE ONLY WAY to "un-install" an Operating System is to Delete the partition that the OS resides on. This will make your computer inoperable until you reinstall the original OS.

Final Note: Most if not all this information is available to you during the install of Ubuntu and if you slow down and read what the installer is saying to you. Furthermore if your friend uses Ubuntu and seems to know what he/she is doing. Have him/her there or on the phone to help with the install. If their not willing to help then they aren't much of a friend.

---

### Post by 3L33T on 2009-09-24
> **grommmm said:**
> man this forum is useless

USELESS POINTLESS post like this make this thread useless

---

