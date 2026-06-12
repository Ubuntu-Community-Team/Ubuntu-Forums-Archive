---
title: "I need help with Hardy login"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Kayel1992 on 2008-04-26
Ok let me start by saying i love linux. i love ubuntu. i want to get it to work. i really do... now for my story :

1. i installed gutsy 2 months ago on a partition of my hard drive
2. it took 1-2 months to finally get desktop efects going. everything was fine
3. 3 days after i got everytihng working i decided to upgrade to hardy beta
4. Hardy beta worked but was excrutiatingly slow
5. I update to Hardy final. TOO SLOW
6. Someone with same problem was told that xgl configure should be removed... it took to long to even get to terminal so i decide to start fresh.
7. download ubuntu live cd. burn. run. i try to log into live and it doesn't work. don't remember why not... i try to install i get black screen with errors after errors ( from what i can tell.. ) 
8. reinstall gutsy
9. upgrade gutsy to hardy
10. i try to log in and now every time i imput my username/password it goes to light brown screen, i hear ubuntu start up sound and then i get bounced back to login. over. and . over. again
11. i bang my head on wall.
12. i go here [https://answers.launchpad.net/ubuntu/+question/28129](https://answers.launchpad.net/ubuntu/+question/28129) and do that. from what i can tell i just reset my username/password. still doesn't work.

PLEASE HELP ME. I AM HATING MY LIFE RIGHT NOW. 

i can't believe i'm gratefull for having a micro-crap partition so i can ask for help.

System
[http://reviews.cnet.com/desktops/emachines-t6410-media-center/4507-3118_7-31466283.html](http://reviews.cnet.com/desktops/emachines-t6410-media-center/4507-3118_7-31466283.html)

---

### Post by piano_man9009 on 2008-04-26
hey, im having the exact same problem as you.  i'm using pretty close to the same computer as you.

[http://reviews.cnet.com/desktops/emachines-t6524/4507-3118_7-31556305.html]("http://reviews.cnet.com/desktops/emachines-t6524/4507-3118_7-31556305.html")

sometimes i notice some different colored lines at the top of the screen before it goes back to login again.  about a quarter of an inch across the top. i think usually green and mostly vertical lines.  does this happen to you too?  i really don't know what that would matter though.

---

### Post by lemming465 on 2008-04-26
The different colored lines thing is a typical for systems where the video chip is borrowing some of the main RAM.  As long as the video goes back to normal, it's harmless. (If not, you usually have an unsupported video chip; probably not one of the problems here.)

One way to get excrutiating slowness is to have the CPU caches turned off; running directly out of main memory with no cache is about 30x slower.  So the first thing I'd check on a slow system is the BIOS settings for the L1 and L2 cache; they should both be on.  (If there is any L3 cache, that should be on too; many systems don't have that many layers yet.)

Running memtest for about 30 minutes wouldn't hurt either.

If you are having problems with a graphical login, try a text console login.  Press simultaneously the three [Control]+[Alt]+[F1] key chord to switch from the graphics console to the first text console.  (Once there, [Alt]+[F2] will go to console 2, and so on; typically ubuntu has usually 6 virtual terminal consoles running. [Alt]+[F7] or maybe Alt]+[F8] will resume the graphical console.  There should be a login prompt.  Type your login user name, press [enter], get a password prompt, type that (not echoed), press [enter].  If you can't log in, follow the password reset link previously quoted in this thread.

A virtual console is a lot like a terminal window.  Try running "top", to see if anything is hogging the CPU.  If not, the next most likely cause of excrutiating slowness is progressive disk failure - if the error rate on the IDE disk is high and growing, it takes an insane number of retries to get some files off, and a Gnome login needs to read thousands of files.

If the text or virtual console login is responsive, but you still have graphical login problems, check the log files, particularly "less /var/log/Xorg.0.log" for X problems.  Or "sudo less /var/log/messages" for general system problems.

To see if you have disk problems, try "smartctl -a /dev/sda".  Probably you have to do "sudo apt-get install smartmontools" first.  Read errors and remapped sectors should be low, like 0-10.

Basically, there are so many possible causes that we are all going to be guessing in the dark until you tease out more specific symptoms and failures.  

Good luck with it; it is possible to fix these things with persistence and effort, though you might end up having to learn way more than you ever wanted about the system innards.

---

### Post by piano_man9009 on 2008-04-27
> **lemming465 said:**
> The different colored lines thing is a typical for systems where the video chip is borrowing some of the main RAM.  As long as the video goes back to normal, it's harmless. (If not, you usually have an unsupported video chip; probably not one of the problems here.)

actually im pretty sure my video chip is unsupported.  its ati and when i was on 7.10 it was a pain in the neck to get working, and apparently so was this first guy's.  
as for the slowness you mentioned fixing, it doesn' matter whether or not it is excruciatingly slow yet, becuse it won't get past the login screen without just looping back to it!

actually, i just remembered.   when i was trying out opensuse, i had to install my video driver from text commands.  i'll try that soon, and report back if it works, as long as i can remmebber/figure out how.

---

### Post by Kayel1992 on 2008-04-27
piano man you're like a brother to me :)

i tried openSUSE and it didn't work either... ati xpress 200m is a bitch to install. 

i will try to use the ctrl alt f1 thing and then keep changing terminals see if i get to the gui. the problem is why is this happening with heron? i mean nothing changed hard ware wise and nothing can be unsuported since the previous version was fine and dandy ( yes i had to enable ati restricted, and i had to do sudo apt-get xgl-config [i think] but once i knew the problem it took only 5 minutes to get it up and running and even before that it worked w/ standard VESA drivers just no compiz function)

gee wizz i really wanted heron too....

---

### Post by piano_man9009 on 2008-04-27
ok, im getting closer.  its been a while since i've used linux, so i'm really rusty.

i found this guide to installing the driver.  [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

but it says i need to enable the restricted repository, but i cant figure out how to do it.

i tried 
sudo gedit /etc/apt/sources.list
but it says cannot open display.

---

### Post by lemming465 on 2008-04-27
gedit is the gnome text editor, it only runs under X windows.  If you are on a text console, try "sudo nano ...".  Fans of vim or emacs are welcome to use something fancier than nano, but nano can be used by pretty much anyone without needing to study it first.

---

### Post by piano_man9009 on 2008-04-27
ALL RIGHT KAYEL!!!

i got it to work!


so first i went in and did this:
[http://linuxcooking.com/2007/12/31/recipe-enable-the-universe-and-multiverse-repositories-ubuntu-804/]("http://linuxcooking.com/2007/12/31/recipe-enable-the-universe-and-multiverse-repositories-ubuntu-804/")

but instead of using gedit, make sure you put nano

after that i did this:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

i restarted the computer and hardy booted right up!

---

### Post by Kayel1992 on 2008-04-27
ok ima wet myself if this works. going to try now.


Edit :

That took longer than expected but it worked. thank you for your help and im glad that emachines are not banished from the land of hardy heron :P

---

