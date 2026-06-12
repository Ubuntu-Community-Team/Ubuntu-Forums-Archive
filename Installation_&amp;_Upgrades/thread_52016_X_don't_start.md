---
title: "X don't start"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by tommy_gun on 2005-07-26
after installing ubuntu the system reboot. unfortunately the x server wont start. there was a message that it is not installed properly. what can i do?

thanks for help

tommy

---

### Post by heimo on 2005-07-26
This comes straight from my memory (can't test if these are correct). Here's what I'd do first: Login to terminal (ctrl+alt+F1), and run
 ```

sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
sudo dpkg-configure -all

``` 

If you get errors, try running those again and see if messages change. If you no longer get errors, try starting gdm
 ```
sudo /etc/init.d/gdm start

``` 
If that won't start X (graphical user interface with login screen), try reconfiguring it with
 ```
sudo dpkg-reconfigure xserver-xorg

``` 

And don't hesitate to post back your results and more information, so me and others can give you more spesific advice. Thanks.

---

### Post by tommy_gun on 2005-07-26
i tried the things you wrote. but i can not start gdm.

---

### Post by heimo on 2005-07-26
Any spesific error messages on screen or in files
/var/log/Xorg.0.log
/var/log/messages

could help solve the puzzle. You can use
 ```
less /var/log/Xorg.0.log
less /var/log/messages

``` 
to read those files (q to quit). Or you can always try to reinstall, but it may come back to the exactly same problem. Did you get any errors or warning when running those commands on my previous post?

---

### Post by tommy_gun on 2005-07-29
now i sit in front of my system an d can give you more specific error messages. on startup ther comes a message:

x-server could not be started. probably it is not installed correctly.  would you see the exact messages.

and the exact messages are:

x window system version 6.8.2 (ubuntu 6.8.2-10)
release date 9. 02. 2005
x protocol version 11, revision 0 release 6.8.2
build operating system: linux 2.6.10 i686 [ELF]
current operating system: linux ubuntu 2.6.10-5-386 #1 tue Apr 5 12:12:40 utc 2005 i586
build date: 05 april 2005
module loader present
os kernel: linux version 2.6.10-5-386....
makers: (--) probed, (**)from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational

after showing this appears a message:
the x-server is now deactivated, restart gdm if it is installed correctly.

i have to say that it is a very small system with a geode processor at 300MHz with  128MB RAM. could it be a driver problem?

thanks for help

tommy

---

### Post by heimo on 2005-07-29
It could be wrong driver for graphics card. Which GPU are you using? It's probably integrated on motherboard? You could try again the reconfiguring (as shown abowe), and choosing general graphics driver called [i]vesa


[/i]

---

### Post by williamlwright on 2005-07-30
I seem to have the same problem...  I have updated with no joy.   I have even set to the generic driver and still get no boot...  using an nvidia fx5600..  have been working on this for 10hrs now and have re-installed it 6 times and have never gotten past the x server load screen..  PLEASE HELP

---

### Post by heimo on 2005-07-30
If you can attach your Xorg.log (exact name of the file in previous post), it'd help a lot. Also xorg.conf could give some clues - basicly any information you can give. Just "it doesn't work" is very hard point to begin debugging. Error messages, what happens when you go through the previous suggestions and so on. Or at least exact description about what happens when booting - does the screen flicker at the end, does it go to console (text mode / shell), try hitting ctrl+alt+F1, ctrl+alt+F7 and ctrl+alt+backspace.

---

