---
title: "ubuntu 9.10 won't let me login"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by balise on 2010-01-28
I inadvertently destroyed a wonderful 9.04 version and downloaded and installed 9.10 from DVD successfully, specifying automatic logging on of my user.  Did a lot of cosmetic changes and it rebooted Ok at least once.  It's probably a red herring, but the last thing I did was comment out a line in /etc/default/grub that had "splash" in it, and afterwards ran the script that creates menu.cfg.

Well, the splash is still there but now it ends with the login screen.  I give it the correct password, and it splashes again and comes backs to the login screen.  Repeatedly.  i.e. I can't login at all.  Any ideas?

---

### Post by sonnyxleet on 2010-01-28
I"m having the exact same problem... And the only thing I did was remove a few programs, installed wine and google chrome... It logged in successfully once, and now it just repeatedly splashes back ot the login screen. I'm sure that my information is correct. Any ideas?

---

### Post by balise on 2010-01-28
I haven't figured it out yet, but booting into my other operating system (XP) and afterwards rebooting, choosing Ubuntu 9.10 allows me to auto-login into Ubuntu.  But, reboot from Ubuntu, and I'm back to the can't login problem.  What the hell?

Would anybody know where to start looking?

---

### Post by sonnyxleet on 2010-01-28
I'm still not having any luck. :( And now when I start up there is a text login for about a millisecond and then the splash screen (before the login screen) just keeps looping. :( sometimes it'll make way to the login screen and sometimes it'll keep looping and then fall back to the text login. so confused..

---

### Post by balise on 2010-01-28
Well, I *seem* to have a handle on it in my case.  I'm used to mounting partitions outside of Ubuntu using entries in fstab.  Just deleting them has let me reboot Ok - so far.

Now to figure out how fstab has changed with respect to startup.  And then, figure out how to revert to grub, rather than this stupid
grub2.  I think Ubuntu 9.10 has made mistakes, and I even wonder about linux itself.  They are getting too clever, and always are changing things.  Found a TON of complaints about 9.10 ...

---

### Post by balise on 2010-01-28
Switching from the 9.10's version of grub to the regular kind brings me back to the same problem: the startup splashes cycling me back to a login.  Every once in a while I can login, if I don't try to add to fstab, or change menu.lst.

Ubuntu sucks.

---

### Post by sonnyxleet on 2010-01-28
Ok. I've fixed my problem. It seems that when I tried to login, it couldn't start a session so it loops back to the login menu/screen. I had to sudo apt-get install ubuntu-desktop, and reinstall/upgrade a lot of packages (although I already did). I noticed gnome-session and gnome-applets were not installed... For whatever reason, once I did that everything was fine and Ubuntu logged in automatically. I would suggest you check to make sure gnome-session is installed. I'm not certain, if this is the root cause, but it's fixed on my part.

Also, I don't think Ubuntu sucks, I just think there are a lot of mistakes/errors that go un-noticed. With time I think it will be a great OS, but it needs a lot of work. Especially with compatibility, but that's Linux as a whole. More people are using Linux now than ever, so I see nothing but good things in the future for Linux, in particular, Ubuntu. :)

Good luck with your problem. I'll stick around and try to help.

---

### Post by presence1960 on 2010-01-29
> **balise said:**
> Well, I *seem* to have a handle on it in my case.  I'm used to mounting partitions outside of Ubuntu using entries in fstab.  Just deleting them has let me reboot Ok - so far.

Now to figure out how fstab has changed with respect to startup.  And then, figure out how to revert to grub, rather than this stupid
grub2.  I think Ubuntu 9.10 has made mistakes, and I even wonder about linux itself.  They are getting too clever, and always are changing things.  Found a TON of complaints about 9.10 ...

GRUB2 is way better than GRUB Legacy 0.97. The reason so many people have problems with it is they are not willing to learn GRUB2. It is not hard but it is "totally different" than GRUB Legacy.

Soon GRUB Legacy will not be able to boot the monster hard disks coming out. GRUB Legacy hasn't been updated for a long time. It's time has come. it is time to move on. lamenting about the good ole days of GRUB Legacy will not help you use Ubuntu  the way you want. If you have been using Linux this long you are bright enough to learn GRUB2. Start here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by presence1960 on 2010-01-29
> **sonnyxleet said:**
> Ok. I've fixed my problem. It seems that when I tried to login, it couldn't start a session so it loops back to the login menu/screen. I had to sudo apt-get install ubuntu-desktop, and reinstall/upgrade a lot of packages (although I already did). I noticed gnome-session and gnome-applets were not installed... For whatever reason, once I did that everything was fine and Ubuntu logged in automatically. I would suggest you check to make sure gnome-session is installed. I'm not certain, if this is the root cause, but it's fixed on my part.

Also, I don't think Ubuntu sucks, I just think there are a lot of mistakes/errors that go un-noticed. With time I think it will be a great OS, but it needs a lot of work. Especially with compatibility, but that's Linux as a whole. More people are using Linux now than ever, so I see nothing but good things in the future for Linux, in particular, Ubuntu. :)

Good luck with your problem. I'll stick around and try to help.

Linux is not like windows in the fact that windows basically does everything for you with a mouse click. Not so in Linux. There are a multitude of options and usually more than one way to accomplish the task you choose to do. In this respect Linux is far superior to windows. But the drawback is some windows users come to Linux expecting it to be like windows but better. That couldn't be farther from the truth. Linux's strengths lie in it's differences from Windows and to change them to suit some people who don't want to learn linux but rather have linux change to suit them is a huge mistake. For people who are squeamish on trial and error learning experience my opinion is linux is not for that type of computer user and that person should stick with windows.

Read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

That is my opinion and you can take it with a grain of salt!

---

### Post by presence1960 on 2010-01-29
> **balise said:**
> Switching from the 9.10's version of grub to the regular kind brings me back to the same problem: the startup splashes cycling me back to a login.  Every once in a while I can login, if I don't try to add to fstab, or change menu.lst.

Ubuntu sucks.

**_No one is forcing you to use it!_**

I really like Sabayon and it is faster than ubuntu. It is based on Gentoo. Maybe you can install that and give it a whirl.

---

### Post by sonnyxleet on 2010-01-29
> **presence1960 said:**
> Linux is not like windows in the fact that windows basically does everything for you with a mouse click. Not so in Linux. There are a multitude of options and usually more than one way to accomplish the task you choose to do. In this respect Linux is far superior to windows. But the drawback is some windows users come to Linux expecting it to be like windows but better. That couldn't be farther from the truth. Linux's strengths lie in it's differences from Windows and to change them to suit some people who don't want to learn linux but rather have linux change to suit them is a huge mistake. For people who are squeamish on trial and error learning experience my opinion is linux is not for that type of computer user and that person should stick with windows.

Read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

That is my opinion and you can take it with a grain of salt!

What? Lol. I don't understand the significance of your reply.. No disrespect, but I wasn't saying that Linux should be easy. I prefer Linux to Windows because, in my eyes, it is far superior, like you said... But it still needs work, as does everything with computers. Nothing will go flawlessly. In fact, most "problems" with Linux doesn't really have anything to do with Linux itself but more so the hardware developers lack of support for it.So far I've had very few "good times" with Ubuntu, but it doesn't make me /quit. And I've tried Sabayon it took some getting used to, but I still chose Ubuntu over it. Although I do still use Sabayon.

---

### Post by presence1960 on 2010-01-29
> **sonnyxleet said:**
> What? Lol. I don't understand the significance of your reply.. No disrespect, but I wasn't saying that Linux should be easy. I prefer Linux to Windows because, in my eyes, it is far superior, like you said... But it still needs work, as does everything with computers. Nothing will go flawlessly. In fact, most "problems" with Linux doesn't really have anything to do with Linux itself but more so the hardware developers lack of support for it.So far I've had very few "good times" with Ubuntu, but it doesn't make me /quit. And I've tried Sabayon it took some getting used to, but I still chose Ubuntu over it. Although I do still use Sabayon.

actually linux is easy once you unlearn what you know about windows. Every thing and every one can always improve no matter how good they are. There is always room for improvement. But what I see when most people complain about Linux not being ready for the desktop or not ready to overtake windows is that they are looking at linux through the filter of their experience with windows. Linux is not like windows in many ways. Windows is mass marketed & is run by a corporate giant with lots of resources. It is strictly a for profit venture. linux on the other hand is not. Somewhere along the way users of linux let their egos get in the way and now believe that it is their responsibility to see to it that linux overtakes windows as the desktop of choice. That would be nice but if it is going to happen it won't be because we pressed the issue. My personal feeling is that linux is not for everyone and therefore the push to overtake windows will be it's undoing because to reach that dubious distinction we will have to make major changes to appeal to those who don't like linux or are not computer savvy enough to run it. Those things that make linux "not ready" are exactly the things that set it apart from Windows and are the things that make linux so powerful. As with religion humans water down the truth with their own perspective. I believe we do the same thing with linux in trying to make it "easy" for everyone. Linux is what it is and we should give up the self-serving notion that it is up to us to see that it overtakes windows.

P.S. if you don't see the significance of my remark you can always ignore it. It is only my opinion not necessarily fact.

---

### Post by sonnyxleet on 2010-01-29
> **presence1960 said:**
> actually linux is easy once you unlearn what you know about windows. Every thing and every one can always improve no matter how good they are. There is always room for improvement. But what I see when most people complain about Linux not being ready for the desktop or not ready to overtake windows is that they are looking at linux through the filter of their experience with windows. Linux is not like windows in many ways. Windows is mass marketed & is run by a corporate giant with lots of resources. It is strictly a for profit venture. linux on the other hand is not. Somewhere along the way users of linux let their egos get in the way and now believe that it is their responsibility to see to it that linux overtakes windows as the desktop of choice. That would be nice but if it is going to happen it won't be because we pressed the issue. My personal feeling is that linux is not for everyone and therefore the push to overtake windows will be it's undoing because to reach that dubious distinction we will have to make major changes to appeal to those who don't like linux or are not computer savvy enough to run it. Those things that make linux "not ready" are exactly the things that set it apart from Windows and are the things that make linux so powerful. As with religion humans water down the truth with their own perspective. I believe we do the same thing with linux in trying to make it "easy" for everyone. Linux is what it is and we should give up the self-serving notion that it is up to us to see that it overtakes windows.

P.S. if you don't see the significance of my remark you can always ignore it. It is only my opinion not necessarily fact.

Well, I understood what you meant. I just sort of misunderstood your intent. But, I understand what you mean. And for beginners, Linux isn't too hard, depending on which version you use I guess.  Plus there are a lot of people that let their laziness stop them from experiencing all of Linux. When someone comes across an error they just expect an answer. Nor Windows or Linux will provide an instant solution for every problem that occurs. People tend to forget that as well. If people took the time to read and exercise practice in Linux to understand it better, they would like it a lot more. For me, the trial and error process just draws me further into it.

---

### Post by presence1960 on 2010-01-29
> **sonnyxleet said:**
> Well, I understood what you meant. I just sort of misunderstood your intent. But, I understand what you mean. And for beginners, Linux isn't too hard, depending on which version you use I guess.  Plus there are a lot of people that let their laziness stop them from experiencing all of Linux. When someone comes across an error they just expect an answer. Nor Windows or Linux will provide an instant solution for every problem that occurs. People tend to forget that as well. If people took the time to read and exercise practice in Linux to understand it better, they would like it a lot more. For me, the trial and error process just draws me further into it.

My intent was that if you or someone who complains about linux falls into the category I described then maybe linux is not for that person. A lot of people come to use linux (and some not so new) and at the sign of trouble they complain. All that energy spent complaining could have been put to use finding a solution. By your own admission the trial and error phase draws you more into linux, so obviously my comments are not meant for you now that I know that. When I post a response to something I have 3 objectives (usually): 1. solve the problem, 2. present it in a way so that the persom with the problem can begin to understand the problem and the solution & 3. This is a broader objective. A lot of people read the threads in here so I gear some of what I post to that effect even though it may or may not apply specifically to the OP.

I love the quote a community member has in his/her signature. it goes something like this: "Linux does not prevent you from doing stupid things because then you would not be able to do brilliant things." It is that exact quality of linux I am addressing. To some the freedom and ability to customize your OS which is nothing like windows is too overwhelming. Those users prefer to be led by the hand. For them I suggest Windows.

P.S. I do not mean to say that complaints are not welcome but that this forum is not the proper channel to vent them most times. The best thing to do is file a bug report or submit an idea to Brainstorm.

---

### Post by balise on 2010-01-30
True, all true.  But, Ubuntu is starting to insist on things I don't like.  I can't touch fstab.  I can't touch menu.lst (with the grub2 downgraded to legacy), lest I *not be able to login*.  It's like the opposite of what they advertise for upstart.

So Gentoo, yes.  Indeed!

---

