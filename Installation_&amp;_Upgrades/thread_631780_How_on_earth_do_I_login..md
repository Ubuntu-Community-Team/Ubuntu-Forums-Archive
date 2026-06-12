---
title: "How on earth do I login."
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by user481516 on 2007-12-04
I installed ubuntu and this is what I get when I boot up.  Sorry the images are so big.  But I have no idea why it goes to this screen and not the ubuntu login screen.  Does anyone have any insights?  Did I miss a step?
[http://www.panoramio.com/photos/original/6305214.jpg](http://www.panoramio.com/photos/original/6305214.jpg)
[http://www.panoramio.com/photos/original/6305224.jpg](http://www.panoramio.com/photos/original/6305224.jpg)
[http://www.panoramio.com/photos/original/6305237.jpg](http://www.panoramio.com/photos/original/6305237.jpg)
[http://www.panoramio.com/photos/original/6305254.jpg](http://www.panoramio.com/photos/original/6305254.jpg)
[http://www.panoramio.com/photos/original/6305269.jpg](http://www.panoramio.com/photos/original/6305269.jpg)

---

### Post by lisati on 2007-12-04
Looks like you actually did log in, but in a text-mode interface rather than with a graphical interface....

Did you install the SERVER edition of Ubuntu?

---

### Post by nilgiri on 2007-12-04
First of all, I'm trying not be be rude, but you really need to take the time to make those images small enough to fit on the screen at the very least no more than 800px wide would be idea.  Resize them and edit your post ASAP before too many people hit them and bog the forum.

Now, to your problem, you need to enter the user name you put in when the installer asked for them.  If you don't know what they are, then you will need to reinstall, watch for the relevent dialog, and take not of what you entered.

After once logged in, we can start addressing what the issue preventing your GUI from starting up might be.

Please ask me for clarification if I am being too technical here.

---

### Post by oldos2er on 2007-12-04
The first screen is your grub bootloader.
 Not sure why you're not getting a graphical login. Try typing "[SIZE=-1]sudo /[B]etc/init.d/gdm start"

[/B][/SIZE]

---

### Post by user481516 on 2007-12-04
I sure hope not.  I installed it using a reboot internet installer.  I chose the option for Ubuntu Desktop.  I guess I will just try installing it again.  Ugghh.  I want so badly to switch to Linux and enjoy it.  Sooo badly.  I am just not computer savvy enough.

---

### Post by nilgiri on 2007-12-04
oop, sorry, missed the bottom of that last image that shows you were successfully logged in.  The images are so big, I hope you understand how this might happened.

Yes, the first question is as above: did you install the server version?  If not, then you will need to start trouble shooting your xserver configuration.  I'd try searching for your video card in the wiki and forums, then maybe the make and model of your computer.

---

### Post by user481516 on 2007-12-04
sorry about my images!  I will delete them.  But I am logged in.  I tried the suggested command and it said "command not found"

---

### Post by user481516 on 2007-12-04
this whole "ubuntu: linux for human beings" advertisement is very misleading.  it should be "ubuntu: linux for human beings with a compatible computer or a lot of time on their hands to install it"

---

### Post by Pumalite on 2007-12-04
Reinstall after doing md5sum of your iso, burn new CD, etc.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Make sure you know what you are installing.

---

### Post by user481516 on 2007-12-04
First of all you guys.  Give me a little credit for having better grammar than all of you.  Second of all, give me a little credit because I installed without a cd drive.  Maybe that had something to do with it.  BUT, I HAVE INSTALLED LINUX ON OTHER SYSTEMS without any problems.  It just seems to be this version of linux with this system.  I have tried everything, cds, thumb drives, you name it, it doesn't work.  Anywho, anyone who cannot properly construct an insult in the english language should not even attempt at it.

---

### Post by jjross on 2007-12-04
try typing "startx" to start the xserver and let us know what that gives you,
it should take you into the graphical interface

---

### Post by PilotJLR on 2007-12-04
If the startx command above results in "command not found", then could you please elaborate on how you installed this?
I'm not familiar with "reboot internet installer". Specifics on what you booted and installed will help.

Like the other poster(s) here, I think it looks like you installed the server version of the OS, which does not include a GUI by default. That would explain why the gdm script was not found as well.

---

### Post by nilgiri on 2007-12-06
> **briantadhorrocks said:**
> First of all you guys.  Give me a little credit for having better grammar than all of you.  Second of all, give me a little credit because I installed without a cd drive.  Maybe that had something to do with it.  BUT, I HAVE INSTALLED LINUX ON OTHER SYSTEMS without any problems.  It just seems to be this version of linux with this system.  I have tried everything, cds, thumb drives, you name it, it doesn't work.  Anywho, anyone who cannot properly construct an insult in the english language should not even attempt at it.

Sorry Brian, I couldn't find any obvious attempts at insults, bad grammar or otherwise.  Maybe you could quote the offending text next time?  But on the flip side, give us some credit for at least trying to help.  I happen to have excellent grammar skills but a terrible knack for typos.  I imagine many of others suffer from the same ailments.  Oh, and I just might be the worlds worst speller. =)  Bad spellers of the world, UNTIE!

Anyway, I also agree with you on the issues surrounding installation complexities and then stability of desktop systems as well.  Ubuntu on my new HP Laptop has been very disappointing.  If I could just find a list of Ubuntu tried and true machines some where besides Dell (F**K DELL!), I would have likely bought from that list.  However, the epeat and energy star ratings would likely have been hard to find and that's more important to me right now.

The point is, I too struggle with a great number of ought-to-just-work issues in getting Linux working on my new machine, but it was not just Ubuntu.  I tried sever flavours of Ubuntu, but also Fedora 8 and Debian 4.  I had the same problems with them all, but was only able to find solutions under Ubuntu in the end.  To be fair, I only spent real time on Ubuntu, but  I still have several unresolved issues.  I am hoping I can ignore most of them until a future release as most of them have bug reports related to them.  

Basically, I will always love Linux for my servers, but I have always found it difficult at best to configure.  I'm not the smartest guy in the world, but I'm not the dumbest, and if they want to live up to their moto, they do have a long way to go to reach the masses.

I can say it is the nicest free OS I have used, and the best for interacting with Linux servers, but if I were not doing much work on Linux servers, I would likely switch back to XP for a while at this point.

The point of all this rambling is that I feel your pain, and unless you are already hooked on the OS (it is awesome once you get used to it and if you happen to not have any hardware compatibility issues the lock the machine randomly), your best strategy maybe to stick with XP for 6 more months and try again with the next release.

God, it hurts to say that. =/

---

