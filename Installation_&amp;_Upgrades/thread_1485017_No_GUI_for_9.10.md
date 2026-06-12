---
title: "No GUI for 9.10"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Lakeside5 on 2010-05-16
I decided to install 9.1o Server edition Ubuntu instead of Lucid Lynx, as Lucid Lynx has ho gui and I thought the 9.10 server had a GUI.  But I installed the 9.10 using a flash drive, and the installation seemed to go ok. But then on reboot, I don't have a GUI.  I just seem to be in something like an Ubuntu terminal, and it's telling me to enter a sudo type comman (this was after I entered my username and password of course). Did I misunderstand something, is there another step I need?  Probably I need to do a command to install the gnome gui from a supository (seem to remember somthing like that).  Thanks for any help.

---

### Post by zenek89 on 2010-05-16
You can just use 

```
sudo apt-get install ubuntu-desktop
```I have the same problem, and one more, because in order to install it I gotta be connected to the internet, but I don't know how to do it using terminal. I'm using wireless adapter so I have to choose ESSID and I don't know how to type the password for this network.

---

### Post by ajgreeny on 2010-05-16
If you don't need all of ubuntu-desktop you can use ```
sudo apt-get install gnome-core
```much simpler and without all the bells and whistles but still more than adequate for a server, which as you have found always comes with no GUI, irrespective of which version of ubuntu.

You couls also, of course choose a much simpler window manager like openbox.

---

### Post by zenek89 on 2010-05-16
uhmmm but is there any way to get **GUI** from **ubuntu CD**? without connecting to the internet? all I need now is just "**synaptic package manager**" so I could install the rest of interface...

---

### Post by ajgreeny on 2010-05-16
Synaptic will not work without the rest of the GUI, so you're wasting your time trying to do that.  As for using the CD, I don't actually know about the server CD, but with the Live CD you can not use it for that purpose; you need the alternate install CD.  Perhaps the server CD will act like that so you may be able to add it to the sources.list file, or just uncomment the CD line (remove the # from the front).  Have a look at the file with ```
sudo nano /etc/apt/sources.list
``` and look for a CD line near the top.

But why do you need synaptic?  What is wrong with simply using ```
sudo apt-get install packagename1 packagename2 etc etc
``` which will do exactly the same thing but without the GUI.

---

### Post by Lakeside5 on 2010-05-16
Thanks for the help everyone, I used the apt-get install ubuntu-desktop command.  A lot of things installed, but at the end, there were a lot of lines indicating that some things couldn't be installed, or a file was locked etc. I rebooted after that, thinking I would magically see the gnome environment, the gui desktop, but I was back at the promt.  I entered my username, and password and then think, now what? How do I get that gui, surf the net, check my email etc. lol.

---

### Post by Lakeside5 on 2010-05-19
Well, I still can't figure out how to get my gui to show.  I entered the code to install the gnome desktop, but still nothing.

---

