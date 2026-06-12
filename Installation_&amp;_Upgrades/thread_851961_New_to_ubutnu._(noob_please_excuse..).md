---
title: "New to ubutnu. (noob please excuse..)"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by revenge2 on 2008-07-07
Hey guys ive only just started using ubuntu even though i made an account here awhile back. But anyway i got the internet up and running and now i want to know how to install applications.

what different file formats are there and what are the ways of installing.

And i want first of all install these two applications
Skype and Vlc.
I got the skype .deb file and i tried installing it however it started downloading some stuff extremely slowly and i had to close it.

And for vlc i have no idea.

So um any help is much appreciated
-thanks:)

---

### Post by lisati on 2008-07-07
When I've installed skype on Ubuntu, it usually likes to download some extra files that it needs when I've opened the .deb file to install it. If you have a slow connection (e.g. dial-up) you might need to exercise some patience. Frustrating, isn't it?

As for VLC, I haven't used it so can't comment.

---

### Post by deNoobius on 2008-07-07
VLC is in the repositories and can be installed via synaptic.

To make sure all the repositories are enabled, go to System/Administration/Software sources and make sure they are all checked.

Then go to System/Administration/Synaptic Package Manager and search for VLC.

---

### Post by revenge2 on 2008-07-07
Hello there, i got skype working, the files were downloaded.
And what are repositories  and how do i use them?

-thanks

---

### Post by deNoobius on 2008-07-07
The repositories are where Linux software packages are made available.  Synaptic package manager automatically searches the repositories--just follow my previous instructions.

---

### Post by satanic-yobbo on 2008-07-07
this link will help you install almost everything you need to make ubuntu run most programs [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) it is a pretty thorough how to

---

### Post by gunashekar on 2008-07-07
> **revenge2 said:**
> Re: New to ubutnu. (noob please excuse..).........So um any help is much appreciated
-thanks:)

Sad to see that new users have to feel apologetic while asking for help on Ubuntu forums .

---

### Post by satanic-yobbo on 2008-07-07
this is true i agree it is sad when they only want to do that which we all had to do at some stage and ask for help to learn something new

---

### Post by Sef on 2008-07-07
> what different file formats are there and what are the ways of installing.

You install them generally upon installing the OS.  

As for types, see [Wikipedia's File Systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems").

---

### Post by revenge2 on 2008-07-07
Hey guys well im not completely sure of what i did, but i didnt use the "synpatics packager" because i didnt know what i was looking at.

Anyway i entered the following in the terminal
```

   % sudo apt-get update
   % sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```

EDIT:
Ahh voila its under "sound and video"- one question though.. how do i delete it when i need to and how does it know where to install it self?

Do all programs install on to a specific place instead of us specifying it?

EDIT 2:
Are there any equivalents to msn messenger other than pidgin?

---

### Post by Partyboi2 on 2008-07-07
To uninstall vlc vlc-plugin-esd mozilla-plugin-vlc you could either use add/remove  or synaptic package manager (System>Admin>Synaptic Package Manager) or from a terminal
```
sudo apt-get remove vlc vlc-plugin-esd mozilla-plugin-vlc
``` if you wanted to remove all the config files as well you would use the --purge option
```
sudo apt-get remove --purge vlc vlc-plugin-esd mozilla-plugin-vlc
```[[COLOR=Blue]Here is a useful page[/COLOR]]("http://monkeyblog.org/ubuntu/installing/") of info on installing programs.
>  Are there any equivalents to msn messenger other than pidgin?      amsn is another program you could use. 
[[COLOR=Blue]Here[/COLOR]]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html") is a table of equivalents that could be of use

---

### Post by revenge2 on 2008-07-08
Cheers partyboi, i downloaded the .tz file, and extracted it. But i dont know how to install it, how do i do this?

---

### Post by hyper_ch on 2008-07-08
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by Partyboi2 on 2008-07-08
> **revenge2 said:**
> Cheers partyboi, i downloaded the .tz file, and extracted it. But i dont know how to install it, how do i do this?
What are you trying to install?
If its amsn then you can go to Add/remove (Applications>Add/remove) and search for it and install it or from the terminal.
```
sudo apt-get install amsn
```If you cannot find the program you are wanting in the ubuntu repository by searching through add/remove or synaptic and need to compile it from source you will need to enter the extracted directory and read the readme or install file to see how to install. Normally to install from source you would cd (change directory) into the extracted directory and type
```
./configure 
```(installing any missing dependencies that get listed) then
```
make 
```
if no errors then
```
 sudo make install
```

---

