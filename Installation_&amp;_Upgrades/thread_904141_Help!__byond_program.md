---
title: "Help!  byond program"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by tercelkisor on 2008-08-29
when i used windows i used to play this game thing called byond so i tried downloading it but i dont know what to do.  i got everything and its unzipped but what do i do next.  the readme file it  comes with is complete garbage so i really need help.

---

### Post by cariboo on 2008-08-29
> from the readme.txt:

Installation procedure:

1. Unzip byond-linux.zip.  (You probably already did this.)

2. Type 'make' and follow the instructions.  Basically, you have the option
   of installing here (for your personal use alone) or on the entire system.

That seems pretty simple to follow. Make sure you have build-essential installed:

```
sudo apt-get install build-essential
```

Jim

---

### Post by tercelkisor on 2008-08-29
k im new to linux.. so when they say type make, do they mean in the terminal?  cause i tried that and it says 

> No targets specified and no makefile found.  Stop.

so i guess "make byond" and 

> No rule to make target `byond'.  Stop.

---

### Post by Partyboi2 on 2008-08-29
Those errors are probably because you are not in the source directory. So if you downloaded it to your Desktop open a terminal and  change to your Desktop directory
```
cd ~/Desktop
```then extract the zip file with
```
unzip 426.996_byond_linux.zip
```*change 426.996_byond_linux.zip to correct name if you downloaded another version.
Then you have 2 options
1st option
If you want to install the program so that all users can use it (Easiest)
enter the newly created directory by typing
```
cd  byond
```Once in the byond directory type
```
sudo make install
```2nd option
If you are wanting to install just for you, you will need to move the byond folder to where ever you want to install it. So for example if you want to install it in your /home directory you will need to move the byond to your /home folder with
```
mv byond /home/username
```*Replace username with your username.
then change into the directory
```
cd /home/username/byond
```*Replace username with correct one.
then to install type:
```
make here
```then run the command that is displayed eg.
```
source /home/username/byond/bin/byondsetup
```
*Replace username again with correct one.

---

### Post by tercelkisor on 2008-08-29
sorry for being such an idiot, but whats after that?  nothing happened when i put ion that last code it just gave me a new bar like i presses enter without typing anything.

how to i actually get the game??

sorry

---

### Post by Partyboi2 on 2008-08-29
Having a  look at the byond website at the linux version I came across this:
> In this article, we will look at installing the command-line version of BYOND on Linux.

The command-line version of BYOND is suitable for hosting servers but not for playing games, as it does not come with a graphical interface.

You have installed the command line version, probably not what you are wanting. You might be able to play the games using [[COLOR=Blue]wine[/COLOR]]("https://wiki.ubuntu.com/Wine"), but I am not sure how you would do that.

---

### Post by tercelkisor on 2008-08-29
ohh that sucks..

thanks anyways

---

### Post by Dlanir on 2008-09-18
Cool such a hope smasher that's why it won't work lmao finally thanks dude.

---

### Post by digitalmouse on 2009-01-04
had the original poster did a little reading, he would have noticed that the BYOND website clearly states that the Linux/MacOS X versions are command line only, typically used as a game host.  You still need the Windows version of BYOND, which includes the game 'client' DreamSeeker, to play games made with BYOND.

alternatively, you can look at the Wine support of BYOND via the BYOND Linux Guild: [http://www.byond.com/members/LinuxGuild](http://www.byond.com/members/LinuxGuild) - not 100%, but very decent support so far.

lastly, using VirtualBox and something like TinyXP gives you Windows running on top of Ubuntu, so you can use the native Windows version of BYOND, albeit a little slower due to emulation.

:popcorn:

---

### Post by hamburgefonstiv on 2012-01-10
> **digitalmouse said:**
> had the original poster did a little reading, he would have noticed that the BYOND website clearly states that the Linux/MacOS X versions are command line only, typically used as a game host.  You still need the Windows version of BYOND, which includes the game 'client' DreamSeeker, to play games made with BYOND.

alternatively, you can look at the Wine support of BYOND via the BYOND Linux Guild: [http://www.byond.com/members/LinuxGuild](http://www.byond.com/members/LinuxGuild) - not 100%, but very decent support so far.

lastly, using VirtualBox and something like TinyXP gives you Windows running on top of Ubuntu, so you can use the native Windows version of BYOND, albeit a little slower due to emulation.

:popcorn:

If you had done a little research you would have noticed that the BYOND site only mentions that the Linux install is host-only on the linux installation help page. It makes no mention of that on the actual download page.
[http://www.byond.com/download/](http://www.byond.com/download/)

:popcorn:

---

### Post by digitalmouse on 2012-01-11
> **hamburgefonstiv said:**
> If you had done a little research you would have noticed that the BYOND site only mentions that the Linux install is host-only on the linux installation help page. It makes no mention of that on the actual download page.
[http://www.byond.com/download/](http://www.byond.com/download/)

:popcorn:

if you had been with the BYOND community long enough you would have noticed that the website has gone through several design changes since 2009, and would understand why my reply - ***posted *three* years ago*** - would be out of date now, making your response little more than trolling and essentially resurrecting a dead thread for no good reason.

---

### Post by Elfy on 2012-01-11
Closed.

---

