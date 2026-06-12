---
title: "Problems after a partial upgrade."
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by junio_buntu on 2010-05-10
Hi,

I am new to Linux, I was using ubuntu 9.04 & 9.10. Recently I  upgraded to 10.04, while doing it I was asked for a **partial upgrade**.  I accepted.

And now I am messed up. Its a worst experience.

I cant see mouse pointer (displayed as 'X'). No maximise, minimise &  close buttons on windows. Cant maximise any window. When I click on  "show desktop button", it says "**Your window manager does not support  the show desktop button, or you are  not running a window manager**".  Complete display is messed up. 

I sorted it out, by changing the visual effects to "Normal" from "None"  in "Appearance preferences". But it is temporary.(plz see the attached  for screen shot)



Every time I reboot, I need to do this.

Can some one fix this, and provide me a permanent solution.

Thanks in advance.

---

### Post by Iowan on 2010-05-10
Moved to new thread.

---

### Post by cariboo on 2010-05-10
Move to a thread of it's own, as it had nothing to do with the thread it was in.

@junio_buntu

Open a terminal and type:

```
sudo apt-get -f install
```

and let  it runs it's course, then in the same terminal type:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

the above commands may solve your problems.

---

### Post by pete_m on 2010-05-10
this thread seems concerned with the same issues. .

[URL="http://ubuntuforums.org/showthread.php?t=1466384"]http://ubuntuforums.org/showthread.php?t=1466384
[/URL]
and i found these notes . .

[http://www.webupd8.org/2009/11/how-t...004-lucid.html]("http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html")

observations from the wise would be most welcome . .

specifically . .. 
[B]
guidance as to the various upgrade levels and techniques available for apt/ synaptic
[/B] [B]
what is the relation between ubuntu and the underlying debian?[/B]
[B]
when/ how to move to new kernels ?


[/B]

---

### Post by pete_m on 2010-05-10
Hi All . .

about to move to 10.04 i found this useful article about getting the most from Lucid.

[http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

Junio - if the system is limping but mostly working . .these observations may help.

X is  already running at the login screen - and you can choose here between X-sessions, thoi  haven't got any alternatives to gnome available here. .

would be good to get guidance as to getting a system equipped to choose between Gnome,KDE ,Xfce, IceWM and such . .

and/or how have a selection of gconf  setups ( themes ? ) to choose from at login time

without having to worry about different ubuntu/kubuntu/xbuntu contortions.

junio_buntu and i are using Gnome . .


so the progs to use are perhaps . . 
gdm  

AYOR
gconf-editor and gconf-tool



when things are fixed you can  use gconf with dump option to put all your gnome settings into a safe xml file

  gconftool-2   --dump > my_gconf_backup.xml

this thread seems concerned with the same issues. .

[URL="http://ubuntuforums.org/showthread.php?t=1466384"]http://ubuntuforums.org/showthread.php?t=1466384
[/URL]
and i found these notes . .

[http://www.webupd8.org/2009/11/how-t...004-lucid.html]("http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html")

observations from the wise would be most welcome . .

specifically . .. 
[B]
guidance as to the various upgrade levels and techniques available for apt/ synaptic
[/B] [B]
what is the relation between ubuntu and the underlying debian?[/B]

my eee pc now on karmic was running (pinned? ) xandros and using first debian etch and subsequently lenny ..

then things went wrong and i've since installed karmic on the ( once readonly) partition leaving a remnant xandros on the second partition with a view to dual-booting . .but tho' grub sees the partition n kernel i have not managed to boot it ..( but not been putting much effort into that)
 
i've been patching lucid and sid repos in and out of my sources.list to try n get a better picture in synaptic of what's moving . .
[B]
when/ how to move to new kernels ?

[/B]

---

### Post by junio_buntu on 2010-05-11
Hi [[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104"),

I did as you told, the safe upgrade removed some 67 packages. but of no use.

Once I reboot its all the same.

---

### Post by pete_m on 2010-05-13
hmm . . .

lately found [http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146) in maverick( next ubuntu release ) discussion
relating the details of partial installs . .

i guess you've got two possibliities to get you back to a fully working system . .

1.. Edit( as root )  /etc/sources.list and replace all instances of **lucid **with ** karmic**
sudo apt-get update
then use synaptic/aptitude  to mark offending packages for re-installaton
gdm and its gnome-* colleagues would be where i'd start.

then metacity and compiz if you're using them

i guess at the worst you cld mark all installed pakages for re-installation and  hope for the best

this **might** get you back to yr 9.10 . .


2. Make a fresh install of 10.04 perhaps from USB. making sure you've backed up all of your stuff.  .
( including but not limited to everything in home/junio )

cp -R /home/junio/* pathto/junio_backup_folder

your gnome setting are in  .gconf and the current state is in .gconfd
i've not had luck in restoring these and have had to rebuild panels 

hope this helps

---

### Post by junio_buntu on 2010-05-14
Hi,

Can you please elaborate how to go back to 9.10. 
It seems better. Once everything sets, I can reinstall 10.04.:confused:

Thanks.

---

### Post by pete_m on 2010-05-15
Junio - i don't know what computer you are using ( relevant here only for managing your screen real estate ) but these hints may be useful as they touch on some of the things involved in customising yr desktop experience.  .

[http://maketecheasier.com/13-ways-to-customize-ubuntu-netbook-remix-for-better-usability/2010/02/07](http://maketecheasier.com/13-ways-to-customize-ubuntu-netbook-remix-for-better-usability/2010/02/07)

screenshots of my work in progress at
[URL="http://www.youtube.com/watch?v=YoI4wRVVjBs"]
http://www.youtube.com/watch?v=YoI4wRVVjBs[/URL]

[SIZE=3][SIZE=2]
To clarify for getting yr system back to a stable 9.10 . . 

Edit( as root )  /etc/sources.list and replace all instances of **lucid **with ** karmic**
sudo apt-get update
( i expect you've done this )

then use **synaptic**  to mark offending packages for re-installaton

if you don't want to do the detective work . . Skip forward . .[/SIZE]
[/SIZE]
[SIZE=1]gdm and its gnome-* colleagues would be where i'd start.

then metacity and compiz if you're using them[/SIZE] 
[SIZE=2]
Mark all **installed** packages for re-installation and  hope for the best

this **might** get you back to yr 9.10 . .[/SIZE] 


looking again at your original post - show desktop complaining about windows manager .  .
this suggests that metacity is/was to blame.. have you got a good desktop now or still having to fiddle. . ?

i think the display stack i've got now goes . .
X11
gdm
metacity
compiz-fusion
emerald

all being well i hope to pursue the upgrade route to Lucid and debian Sid as soon as i have a good .iso of my karmic install.

there are posts about this process .. and its pitfalls.  .i expect that loads of problems will get fixed immediately after the official launch as thousands of users get to work .. 
redoing the upgrade with a newer lucid may result in a smoother experience . .

---

