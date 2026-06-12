---
title: "Just coming back to ubuntu - what happened?"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by bmavbeard on 2013-07-19
Hello, this is my first post.  A long time ago (2008) I started using  ubuntu.  I used for a little while but I ran into trouble installing an  email manager (the one my university was using) and I pretty much quit.  I am not a computer idiot but it is a learning curve when you come to linux and I had some trouble with the basics.  Long story short I am trying to  come back to ubuntu.

I have a dell desktop that came with windows xp.  Before I got ubuntu the first time I got a 250 gb hard drive and devoted 75 gb to ubuntu and a lot of space for windows.  I also installed a wireless card on my desktop (not a usb one, an actual card).  Everything worked fine.  THe fact that I dual boot is part of the reason I did an upgrade and not a fresh install.  I have a lot to do on my Windows partitions before I can do a fresh install in case something happens.  

As you can imagine I had a lot of updating  to do (I had jaunty).  I loved jaunty it was soooo fast on my computer.  I could explore the menus.  I liked the idea of getting packages (a lot like app shopping).  

After searching forums like this one I finally got updated to 12.04.  I am just wondering what happened?  It takes a long time to boot up to bring up the log in screen.  Then when I log in it is crazy looking. I have did some searching and I know that it is unity that I am using.

First question: Is there any way to get the menus back!  

Apparenty to use anything I have to go through dash.  It works but when I had menus I could EXPLORE.  That was the great part.  I got to look in every nook and cranny and try this and that.  I could look under accessories or look at other tools or packages, etc.  The problem with dash is you have to know what you are looking for before you can look for it.  (I have searched and I cannot find out how to get the menus back other than logging in under gnome classic.)

So after reading the posts I decided to try gnome classic.  I liked it better but then suddenly keyboard stopped working and things didn't show up right and then all could see was desktop icons no menus at all (I couldn't even log out or shut down becuase that menu was gone)

Second question: Sometimes my gnome classic just messes up like above but unity does not (what could be the problem).

Another problem I ran into after the update was my wireless stopped  working. However, I will post that to a different part of the forum.

For my third question, I was just curious if ubuntu 12.04 code had gotten so much more complicated that it takes that much more time to boot up and is so slow (compared to what I was used to for ubuntu jaunty on this machine).  It just seemed like everything was so simple back in the day and everything is like using a mac now, cannot find anything.  It is also like windows now in that it is just as slow to boot up (used to beat them hands down).  

I appreciate all the help on this and if you have any ubuntu tips please share.  I learned that ctrl + alt + t opens the terminal.  I leaned that ctrl + q lets you quit an app.  Is there one for shut down?

One more time, thanks, and remember a fresh install is not an option at the moment.

---

### Post by ibjsb4 on 2013-07-19
Yep, 12o4 takes more resources to run.  If your lacking the ram or cpu maybe you should look at xubuntu, its built to run better/faster on older equipment.

---

### Post by bmavbeard on 2013-07-19
I have 2 gb of ram and I think a pretty good processor but that isn't exceptional.  Thanks, I may have to use the old windows 7 partition to give xubuntu a try.  (How will that affect grub?)

You say it takes more resources does that mean it can offer a whole lot more than what jaunty did?  I guess I am trying to ask what are some cool new things I can do now after this update.  Thanks for the reply :)

Maybe one day I will be able to help other people out on this thing.

---

### Post by Cheesehead on 2013-07-19
> **bmavbeard said:**
> THe fact that I dual boot is part of the reason I did an upgrade and not a fresh install.  I have a lot to do on my Windows partitions before I can do a fresh install in case something happens. 

As written, that does not make sense.
If Ubuntu and Windows are on separate partitions, you may reinstall either at any time.
Simply update the bootloader after install.



> **bmavbeard said:**
> I am just wondering what happened?  It takes a long time to boot up to bring up the log in screen. 

Er, is your Ubuntu partition ext3/4 or NTFS? If NTFS, have you defragged it recently? 


> **bmavbeard said:**
> Apparenty to use anything I have to go through dash.  It works but when I had menus I could EXPLORE.  That was the great part.

Not true. The Nautilus File Manager is still included in Ubuntu. It's also in the Launcher Bar.
The Dash is a very convenient way to locate files and applications if you do not recall where you put them.


> **bmavbeard said:**
> For my third question, I was just curious if ubuntu 12.04 code had gotten so much more complicated that it takes that much more time to boot up and is so slow (compared to what I was used to for ubuntu jaunty on this machine).

Did Ubuntu grow and become more complex? Yes.
Did it grow and become more hugely more complex to the point where booting takes much longer? No.
We could sit around for weeks guessing why your boot is slow and mine is fast, and not get anywhere.
Install the bootchart package and find out.

---

### Post by oldfred on 2013-07-19
Unity seems to require better video systems. But it still runs on my 6 year old laptop with 1.5GB of RAM. 

I change to the old menu style (gnome-panel or fallback) and do not use Unity normally.

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by snowpine on 2013-07-19
> **bmavbeard said:**
> I have 2 gb of ram and I think a pretty good processor but that isn't exceptional.  Thanks, I may have to use the old windows 7 partition to give xubuntu a try.  (How will that affect grub?)


Xubuntu is easy to install. It uses the Xfce interface, which is what I personally use on my main computer; I find it to be very intuitive and "classic." Simply install the "xubuntu-desktop" package with a couple of mouse clicks in the Software Center. Here's a tutorial and screenshots: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

Regarding the overall premise of your post: Every version of Ubuntu that has ever been released, or ever will be released, is different than the version that came before it. This trend is likely to continue; in a few years, people will be saying "what happened to Ubuntu? it is unrecognizable from 12.04!! how do I make it go back to the old familiar unity interface???" ;)

---

### Post by bmavbeard on 2013-07-19
> **Cheesehead said:**
> As written, that does not make sense.
If Ubuntu and Windows are on separate partitions, you may reinstall either at any time.
Simply update the bootloader after install.

Yes, you are right.  I was trying to be concise.  My windows side needs to be backed up and it is going to take me some time to find all the drivers and save them somewhere in case something goes wrong when I do the re-install.  Along with writing down all the programs I have, etc.  But, yes, you are right I could do it I just haven't backed up yet and I know it will be time consuming.

> **Cheesehead said:**
>   Er, is your Ubuntu partition ext3/4 or NTFS? If NTFS, have you defragged it recently? 

It is extension 3 I see that when it starts.  I don't know what that means though.  Should it be extension 4?  I think it is fat32 but I will have to check.  I never thought about needing to defrag for ubuntu.  Makes sense I will look up how to do that one.

> **Cheesehead said:**
> Not true. The Nautilus File Manager is still included in Ubuntu. It's also in the Launcher Bar.
The Dash is a very convenient way to locate files and applications if you do not recall where you put them.

I didn't mean to say that I dislike dash. Yes it is convenient. Rather that I dislike not being able to look around.  I was hoping someone like you would tell me what you just did that there is a file manager I can look around in.  I just want to look at applications or accessories.  I have tried and tried to find it I just cannot.  I will google Nautlis File Manager to see how it works in 12.04.  Thanks!

> **Cheesehead said:**
> Did Ubuntu grow and become more complex? Yes.
Did it grow and become more hugely more complex to the point where booting takes much longer? No.
We could sit around for weeks guessing why your boot is slow and mine is fast, and not get anywhere.
Install the bootchart package and find out.

Thanks, I will look bootchart up.  I guess I was more trying to find out if something was wrong with mine. It takes like 12 seconds longer (or around that) than what jaunty used to take.  Is that normal?  It is still faster than Vista and 7 on my laptop.  I just notice the dashes light up 3 to 4 times when it is booting up and I thought that seems slower than what it should be.  There might not be a problem at all I just wondered if that is what I should expect.

Thanks CheeseHead!  I am really interested to find out what extension 3 versus extension 4 means.

---

### Post by bmavbeard on 2013-07-19
> **oldfred said:**
> Unity seems to require better video systems. But it still runs on my 6 year old laptop with 1.5GB of RAM. 

I change to the old menu style (gnome-panel or fallback) and do not use Unity normally.

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Just to clarify, gnome-panel runs on which version of the dektop when I log in.  I can choose gnome, gnome 2, ubuntu, ubuntu 2d  Or does it work on all of them.

Does your classic just sometimes lose everything but the desktop icon?  I have been really forced to use unity because the others mess up. I just wondering if I am somehow pressing a combination of keys and don't know it.

I will look all of this up, thanks so much!

---

### Post by bmavbeard on 2013-07-19
> **snowpine said:**
> Xubuntu is easy to install. It uses the Xfce interface, which is what I personally use on my main computer; I find it to be very intuitive and "classic." Simply install the "xubuntu-desktop" package with a couple of mouse clicks in the Software Center. Here's a tutorial and screenshots: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

Regarding the overall premise of your post: Every version of Ubuntu that has ever been released, or ever will be released, is different than the version that came before it. This trend is likely to continue; in a few years, people will be saying "what happened to Ubuntu? it is unrecognizable from 12.04!! how do I make it go back to the old familiar unity interface???" ;)


I guess I am just trying to clarify here.  I know there is kubuntu and xbuntu etc.  It seems that I can go to software center and get desktop packages for either of these.  Are these like emulators?  Where they take ubuntu and make it like xbuntu?  Another way of asking my question is this.  I know ubuntu is a version of linux.  Is xbuntu a different version of linux not based off of ubuntu?  Just like you might burn an iso of ubuntu and run it is there an iso for "xbuntu" that you run and install that as your operating system.  I hope that question makes sense.

As for the other part, you are right, change is inevitable. I don't think change is bad I guess I am just trying to figure it out.  I kind of went crazy when I couldn't find a simple menu or go to something called accessories.  I guess I have gotten too reliant on GUI.  This new one isn't as intuitive as I had hoped doesn't mean it cannot be figured out. Thanks for all the help.

---

### Post by snowpine on 2013-07-19
Ubuntu is Ubuntu with the unity desktop environment.
Xubuntu is Ubuntu with the xfce desktop environment.
Kubuntu is Ubuntu with the kde desktop environment.
etc.

You can install as many desktop environments as you like, and switch between them each time you log in. It is the same core system underneath, not a separate operating system by any means. :)

---

### Post by bmavbeard on 2013-07-19
> **snowpine said:**
> You can install as many desktop environments as you like, and switch between them each time you log in. It is the same core system underneath, not a separate operating system by any means. :)

Got you!  Thanks so much.  I am glad you understood my question. Y'all have been great.  Now, just to find out what extension 3 versus extension 4 means and I can probably close this thread.  I really appreciate all the help.

---

### Post by ibjsb4 on 2013-07-19
Ext3 hasn't been in use for quite a while, so the ext3 vs ext4 debate is long over with.  Default install on all the ubuntu flavors is ext4.

[http://en.wikipedia.org/wiki/Ext4_filesystem](http://en.wikipedia.org/wiki/Ext4_filesystem)

---

### Post by bmavbeard on 2013-07-19
> **ibjsb4 said:**
> Ext3 hasn't been in use for quite a while, so the ext3 vs ext4 debate is long over with.  Default install on all the ubuntu flavors is ext4.

[http://en.wikipedia.org/wiki/Ext4_filesystem](http://en.wikipedia.org/wiki/Ext4_filesystem)

Sorry, I am not trying to cause debate just simply asked a question.  I am a newbie at this.  Thanks for the wiki.  I will look and try to learn what it even means.  I will see if there is a way to change.  Remember, I first installed ubuntu with Jaunty and have only upgraded (so I am guessing back then they used extension 3.  I do appreciate the information and I guess I won't ask so as not to stir up debate.

---

### Post by cybrsaylr on 2013-07-20
I remember and used Jaunty which seems like ages ago.
Lot of changes in everything since then in Linux, Windows and Mac.
If anything the only constant is change in whatever OS you use.

Using 12.04LTS right now and love it including Unity. 
It's rock solid and just runs with no issues. 
What more can you ask for?

---

### Post by bmavbeard on 2013-07-20
> **cybrsaylr said:**
> I remember and used Jaunty which seems like ages ago.
Lot of changes in everything since then in Linux, Windows and Mac.
If anything the only constant is change in whatever OS you use.

Using 12.04LTS right now and love it including Unity. 
It's rock solid and just runs with no issues. 
What more can you ask for?


Yes, lots of changes.  I really appreciate all the help.  I have learned that I should be on extension 4 not extension 3.  I have learned that there are still menus and I can still explore.  I have learned that you can defrag on ubunut.  I have determined that with these things and a few of my own problems I am just going to have to break down and back up my Windows partition then reinstall a fresh 12.04 so I can see it run most efficiently.  (Heck might as well do a fresh install of both while I am it and go ahead and reformat so I wont have to worry about defrag).  I expect that there might be issues but everyone says there 12.04 runs smoothly so something must be wrong with mine I will see how it is after the fresh install.  

Thanks for all the help, marking it closed.

---

### Post by bmavbeard on 2013-07-20
actually, I don't know how to mark it closed. Now I feel stupid.

---

### Post by QIII on 2013-07-20
Hello, bmavbeard!

Don't feel stupid!  The plugin for marking threads solved is broken.  Please see the link in my signature for a work-around.

Cheers

---

