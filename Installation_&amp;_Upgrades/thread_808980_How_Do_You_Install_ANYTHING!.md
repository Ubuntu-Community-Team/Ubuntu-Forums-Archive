---
title: "How Do You Install ANYTHING?!"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by benf101 on 2008-05-27
I've been using Ubuntu for a few months now, and I basically love it, except for one thing... Installing new programs is just about rocket surgery.

If they happen to be in that convenient list of about 12 applications you find under "Add/Remove", then you're in luck, otherwise, you'd better cancel all your other plans for the weekend.

Can anybody set me straight?  How on earth do you install a program?!  Windows has that convenient little "exe" icon you can click on.  Ubuntu has nothing!  What's the problem with this OS?  I must be missing something.

So, if I download openlaszlo, for example, and I have the tarball, then what?  And does that answer apply to every other program as well?  How can anyone learn this? :confused: :confused: :confused:

---

### Post by jrusso2 on 2008-05-27
What do you mean 12 programs in add remove?  There are thousands.

You can use synaptic also and search by name.  Make sure you have all the repositories enabled.

---

### Post by iaculallad on 2008-05-27
Read this [page]("http://monkeyblog.org/ubuntu/installing/") to help you understand the process/steps on how to install "Everything" in Ubuntu. And please, don't post using BIG letterings, Ubuntuforums.org members can read posts with small font letters.

---

### Post by tex4s on 2008-05-27
I am right there with you -- I really really want to embrace the ubuntu society and feel comfortable with it (as much as I do w/ Windows-based OS) but there are a couple of obstacles I cant get my mind around.
1.) Lack of clear explanation (installing programs/drivers/applications) anything.

2.) THIS IS A HUGE ONE: If the advent of technology is supposed to make things easier then why all the need for these 3rd party apps to do mundane things ?  Why is it so UN-clear , how to install a driver (specifically the newly-released driver for my X-Fi soundcard) ?  If this is supposed to be so much better than Windows...then why isnt it easier ?  Why is there even A NEED to use a console-type app ?

and when there are half-*** answers to questions like the one above -- it just frustrates even more....

I am actually a pc hardware engineer and very comfortable with my way around a Windows-based OS, and hardware, of course, but I also enjoy the polished look and feel of those OTHER OSes ...

---

### Post by iaculallad on 2008-05-27
> **tex4s said:**
> I am right there with you -- I really really want to embrace the ubuntu society and feel comfortable with it (as much as I do w/ Windows-based OS) but there are a couple of obstacles I cant get my mind around.
1.) Lack of clear explanation (installing programs/drivers/applications) anything.

2.) THIS IS A HUGE ONE: If the advent of technology is supposed to make things easier then why all the need for these 3rd party apps to do mundane things ?  Why is it so UN-clear , how to install a driver (specifically the newly-released driver for my X-Fi soundcard) ?  If this is supposed to be so much better than Windows...then why isnt it easier ?  Why is there even A NEED to use a console-type app ?

and when there are half-*** answers to questions like the one above -- it just frustrates even more....

I am actually a pc hardware engineer and very comfortable with my way around a Windows-based OS, and hardware, of course, but I also enjoy the polished look and feel of those OTHER OSes ...

That actually is the joy of using Ubuntu or Linux in general. People used in windoze often complain on driver/application installation. 
The problem with driver installation is that card manufacturers hadn't yet embrace open source so the Linux community are getting hard time on coding open source drivers that could be used for that piece of hardware. The Linux community is adjusting on manufacturers and not the other way around.
As for applications, windoze users are used in clicking executable ".exe" files for installation and Linux on the other hand, uses synaptics/apt-get/dpkg/yum/ or rpm on that matter.
Windoze doesn't teach their users to think, they are fond of spoon-feeding while Linux train it's users for resourcefulness and patience to learn since Linux is way too deep for a single day/week to learn.

All I'm saying is that to really learn Linux, we must be patient to do research/readings on topics thats seems very enigma and try to understand them.

---

### Post by Bubba64 on 2008-05-27
There are 100s of explanations in the forum archives that explain how to install things. 1st thing I would do is extract the tar ball many have auto installers in them that you can click on then hit run or install in terminal. Here is a key link that can help you, which I found on Google by typing installing tarballs linux.
[https://help.ubuntu.com/8.04/add-applications/C/install-file.html](https://help.ubuntu.com/8.04/add-applications/C/install-file.html)

---

### Post by lswest on 2008-05-27
> **tex4s said:**
> I am right there with you -- I really really want to embrace the ubuntu society and feel comfortable with it (as much as I do w/ Windows-based OS) but there are a couple of obstacles I cant get my mind around.
1.) Lack of clear explanation (installing programs/drivers/applications) anything.

2.) THIS IS A HUGE ONE: If the advent of technology is supposed to make things easier then why all the need for these 3rd party apps to do mundane things ?  Why is it so UN-clear , how to install a driver (specifically the newly-released driver for my X-Fi soundcard) ?  If this is supposed to be so much better than Windows...then why isnt it easier ?  Why is there even A NEED to use a console-type app ?

and when there are half-*** answers to questions like the one above -- it just frustrates even more....

I am actually a pc hardware engineer and very comfortable with my way around a Windows-based OS, and hardware, of course, but I also enjoy the polished look and feel of those OTHER OSes ...

You can't expect an OS that's created through open source and reverse-engineering to be able to "easily" install unsupported drivers like an OS with billions of dollars of funding and strong ties with manufacturers.  Our answers are not half-***ed, since we could also just NOT reply to your questions, especially when they're posed they way it was in this post.  We could just post a link to google and tell you you'll find all your answers there.  Some people, like me, use google to find solutions for problems (even if that problem isn't mine), and you have this forum to help you install programs that are not fully supported by Ubuntu.  Why use a "console-like" app?  Because some people (me included) find it easier, faster and more **universal**  The reason you find tutorials written with terminal instructions is because they (often) apply to a wider range of Linux OSes than the GUI way, since there are just so many programs to choose from (since it's open-source and we have tens of thousands of apps in the repositories, not just "12").  And you can't compare tar.gz installs to windows .exe files, because they're not even similar in type.  Tar.gz is an archive (like zip) not an executable.  A .deb (or .rpm for red-hat based distros) can be compared to .exe, because they're both binary executable files.  Also, most tar.gz archives contain files called README, and they supply instructions necessary to compile and install the program.  it is recommended you keep that folder then, so you can uninstall it (that's the problem with source-code installs, you have to keep the original folder and then install/uninstall it from there)

If you want help from members of this forum, you should post things with a nice, small font, not make it seem as if you're trying to start a flame war, and descriptive titles (without the use of all-capital words) is nice, and often gives members here a reason to help.

But yes, getting into Linux requires you get your hands dirty, and for you to re-learn a few things.  Why? because linux is not windows.

---

### Post by sloggerkhan on 2008-05-27
Check ubuntu wiki or google, but in summary:
Installing software on Ubuntu:
There are 3 general ways.
Packages
Unpackaged Binaries
Source

Packages are *.deb files that can be installed with synaptic/apt-get/aptitude/dpkg etc
These are the primary and preferred way of installing software on Ubuntu. The general method of getting software should be to identify the app (or kind of app) you want, then search synaptic for it (after enabling all repositories), mark the check box, and hit apply. It will be downloaded and installed. Some websites, such as wine, provide 3rd party repositories for the latest versions of particular software. You can add these locations to software sources and install and update software from them automatically as from the normal ubuntu repos. Sometimes, you may find *.deb files individually. These are the linux analogue to *.exe installers. Click to install, basically. You might find them on websites such as getdeb.net. 

Binaries are the next common form of software distributed for linux.  These have 2 common types: customized install scripts and tar.gz files with resources and executable program. The custom install scripts are mostly used by proprietary software and you should probably install by making sure they have permission to execute and running from the command line, possibly as admin. Generally, the average Ubuntu user isn't going to be encountering this kind of install. The other tar.gz form is common to compiled but unpackaged software. The most obvious example of this is game. Things such as Nexuiz and Warsow often have the latest version available as a *.tar.gz. Just download, extract, make sure it's executable, and run the appropriate binary for your architecture.

Source is compiling things on your own system. You can get source files from repo systems like bazaar and subversion, where you fetch source code from a repository, or by downloading it, often as a .tar.gz with source code instead of binaries. The most common way to work with source it ./configure then make and make install from the command line in the appropriate folder. Installing from source is not too hard, but may be ill advised for new users.

So, in summary, to install software in Ubuntu, you should use synaptic and repositories to get an install software, possibly downloading a few *.deb files or adding a repository or 2 for special software. In rare cases, you may need to get an unpackaged binary or install from source.

---

### Post by benf101 on 2008-05-30
I happen to like large letters.  I'm getting old.  So here we go...

This post of mine simply confirmed that it is exceedingly difficult to install anything on Ubuntu.

I'm trying to put Open Laszlo on my system, and it's just about impossible.  I almost think that anyone who claims it is installed, is bluffing.  I read the read-me file, I looked online.  They talk about having certain Java files installed in the right folder.  So that means that I can't use the automatic installation of Java, rather I have to make it install in a certain place.  Once that's done, then I have to do something else... what it is, I have no idea.

I have similar problems with themes.  Some of them are simple... just download it and drag it to the Appearance Preferences window, and it's done.  Others just get rejected.  They say you have to compile it.  Well why would a programmer not compile their code?  Like I said earlier, I'm missing something.

Maybe I need Linux for Dummies.

And by the way, when you guys criticize someone for the font they use, you sound like a dweeb.

---

### Post by benf101 on 2008-05-30
I guess this will make everyone else happy.  There is such a thing as a hyperbole (hi-per-bow-lee).  It is an exaggeration for effect.  People use it in language to communicate certain things to the recipient.  For example, if I said there were 683 programs in add/remove, then some people would say, "Gosh, that's a big number", and my point would not be taken.  But when I say 12, I KNOW there are more than 12, but it is an exaggeration to make my point that the amount there is not always sufficient.

---

### Post by Slim Odds on 2008-05-30
sudo apt-get install ANYTHING

???:lolflag:

---

### Post by jimv on 2008-05-30
> **Slim Odds said:**
> sudo apt-get install ANYTHING

???:lolflag:

Ha ha, you beat me to it.

Anyhoo, to the OP...

If you don't have the time or desire to figure out how to do what you want with Ubuntu, then by all means, use Windows.  There is plenty of documentation out there that addresses the things you're trying to do, and there are people here who are willing to help you as well.

And OpenLaszlo sounds like some sort of webapp/programming api.  If you can't figure out how to install it, I'm not sure how you're going to know what to do with it once you get it installed.

---

### Post by Pumalite on 2008-05-30
[http://www.openlaszlo.org/documentation](http://www.openlaszlo.org/documentation)

---

### Post by tex4s on 2008-07-20
I want to thank everyone for making my point -- 

In your attempts to "justify" the shortcomings of open-source OS, you just made my point even clearer  - by comparing" Windoze"'s .exe files, you had to list 2 -3, even 4 variations.  "linux teaches its users to think", "windoze users are used to be spoon-fed" --  uhhh?!?!?  When you buy electronics (anything really) - do you purposely go for the one with the least amount of features ?  The one with no bells and whistles, no automation - no "PhD - 'push here dummy'" ?  so you can feel more fulfilled by doing everything th ehard way - to get an almost similiar response ??  No - nobody does, so why on earth should a computer be any different ?

I dont care about the n00b general user that just needs an OS for checking email, and browsing the net - I'm a tinker-er, I want to change/customize the nuts & bolts, have everything set the exact way I want it - and that is where Im frustrated - because all of the "help" ....isnt.

---

### Post by Pumalite on 2008-07-20
I you are a tinkerer; maybe you should sink your teeth in Gentoo

---

### Post by fishbulb1022 on 2008-07-22
I had lots of trouble installing the .tar.gz (or similar extesion) files as well. I found help at this site [http://monkeyblog.org/ubuntu/installing/#source]("http://monkeyblog.org/ubuntu/installing/#source")

I noticed this was posted earlier by someone else, but in case you hadn't looked at it again i figured i'd put it down again.

this site was still a little hard to follow for a complete noob (which i am) so i'll help you get past what took me like an hour to figure out.

ok, 
1. anytime you download a .tar.gz or whatever, just save it to the desktop, its just easier.

2. extract the files by right clicking and hitting "extract here" which will extract it to the desktop.

3. open a terminal window by going to Applications>Accessories>Terminal

4. type "cd Desktop" and make sure to capitalize the D

5. now type "ls" (thats a lowercase LS just for clarity's sake)

6. this should give you a list of all the directories on the desktop, find the one you want, it should be the name of whatever program you're trying to install, but make sure you don't pick the .tar, you want the one you extracted, which will be the same thing without the extension. Highlight and copy the name.

7. Now type "cd" and paste what you just copied after it (remembering the space between cd and the file name)

8. Now type ./configure to automatically configure the program. if it stops in the middle and says it needs a package, copy the name of the package, go to the synaptic package manager (system>administration>synaptic package manager) and do a search for that package. anything that looks the same with -dev on the end is also necessary, get it to. once you've got everything checked, click apply.

9. now back in the terminal (if you closed it, you'll have to navigate back to the directory again, using steps 4-7) type ./configure again

10. repeat steps 8-9 until all the packages necessary have been installed and the configuration completes. 

11. Now type "make" to compile the code

12, now "make install" to install it

I hope this helps, it should work, if it doesn't feel free to ask more questions and check out the link i gave you (you should also check the "Navigating the Terminal" link they have, it was really helpful)

---

### Post by hoax.it on 2008-07-22
but when you installa anything system decrease performance ?

---

### Post by Pat Benson on 2008-07-22
I so feel the same with those who can't figure out Ubuntu. I've been trying for 2 days now to get the drivers work for my graphics card (Raedeon x1950 Pro) and with no success whatsoever.
Apart from that the apps I did/do like in MSWin seem to be easier to modify to my liking.
I'm completely new to Ubuntu but have tried Red Hat some years ago which I didn't find as complicated as this *sigh* though I didn't really learn it/Linux that well.

I have tons of question but can't even figure out where to start ... I just wish that those friggin drivers was possible to install.. so I can atleast run Blender properly.

Edit; typos *sigh* getting sickly tired of this ....](*,)

---

### Post by arsenic23 on 2008-07-22
> **tex4s said:**
> I want to thank everyone for making my point -- 

In your attempts to "justify" the shortcomings of open-source OS, you just made my point even clearer  - by comparing" Windoze"'s .exe files, you had to list 2 -3, even 4 variations.  "linux teaches its users to think", "windoze users are used to be spoon-fed" --  uhhh?!?!?  When you buy electronics (anything really) - do you purposely go for the one with the least amount of features ?  The one with no bells and whistles, no automation - no "PhD - 'push here dummy'" ?  so you can feel more fulfilled by doing everything th ehard way - to get an almost similiar response ??  No - nobody does, so why on earth should a computer be any different ?

Actually I do.  I always go for the most simple and powerful thing I can get.  So yeah, no bells and whistles with as much manual input from me as possible.  I have a need to know how everything I own works, so any 'push this button and let the device do it's thing' kinda products are a turnoff for me.  I normally take everything I buy apart before I use it too.

That said a Window's .exe file can be any number of things, really anything that can be run by clicking on it.  If you get an exe it's not nessisarily an installer.  But with Debian based linux distros, like Ubuntu, if you have a .deb, then that's an installer, it's only an installer and it is nothing else.  You know what you have.  

If you can't find a .deb for your program and it's not in the repositories ( you might also want to see if the people that make the program have a repository you can add to your system ), then someone out there doesn't think that the program is ready for mainstream, or the developers and comunity don't package it for Debian.  There could be a couple different reasons for this but...  You have to understand that many open source programs available are in a state where they wouldn't be released at all if they where closed source, and the developers don't want regular users to install them and then have problems they can't fix.  If your aware of this and still want to use the program the developers will usually have a guide on compiling it.  If you read up on the basics of compiling from source in linux the simple outlines that are provided become fairly straight forward.

---

### Post by Pumalite on 2008-07-22
> **Pat Benson said:**
> I so feel the same with those who can't figure out Ubuntu. I've been trying for 2 days now to get the drivers work for my graphics card (Raedeon x1950 Pro) and with no success whatsoever.
Apart from that the apps I did/do like in MSWin seem to be easier to modify to my liking.
I'm completely new to Ubuntu but have tried Red Hat some years ago which I didn't find as complicated as this *sigh* though I didn't really learn it/Linux that well.

I have tons of question but can't even figure out where to start ... I just wish that those friggin drivers was possible to install.. so I can atleast run Blender properly.

Edit; typos *sigh* getting sickly tired of this ....](*,)

Have you tried Envy?:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by VPz on 2008-07-25
thank you all for helping us noobs on this thread. This info will be put to great use, and will help me realize what I can do with Ubuntu and Linux. You guys rock...I understand from the noobs perspective that things can get a little confusing when dealing with open source OS as opposed to the ease of use of windows, but that is the reason why I switched, to figure out how I can use my computer to its fullest potential...and to be a little more technically involved with my computers apps and progs will definitely help with it. 

So for all the frustrated noobs out there, just ask a question and don't demand answers for something that you don't understand. If all fails and you can't find the answer to your question:popcorn:, switch back to Microsoft...I know you won't be seeing me there any time soon.

8-)

---

### Post by Braaimanook on 2008-09-20
One of the clearest how to's I have read. Thanks a lot

---

### Post by sandy8925 on 2008-10-15
I don't know what you're complaining about.

Personally i like using synaptic and apt.

Just type 'sdo apt-get upgrade' and almost all software is upgraded to latest version in the repositories.

I really prefer this method to searching filehippo everyday to see if there's a newer version.

---

### Post by elustran on 2008-10-16
I don't think anybody's mentioned this yet: installing and compiling from source in Windows is just as hard as it is in Linux, if not harder because Linux has all the compilers you'd ever want within easy reach in its repositories.  It's just that Windows has more stuff that installs itself from .exe files.

The main thing that Linux seems to lack is clear, concise, and complete documentation.  I'm not saying that Windows does, but it is a bit more user friendly.

Every time I've installed Linux, I've had to go through some sort of difficult tweaking process.

**The main difficulties I've had with Ubuntu are:**

- hardware drivers.  You know what I'm talking about.  Non-free drivers are ghettoized and hard to get working, but basically everybody needs them.

- multimedia.  I remember trying to get video to look good - it took me forever to figure out that linux wasn't using gl to render and I needed it to get my video to stretch.  Compiz doesn't play nice with other gl apps.  

- Having to use the GUI for anything beyond BASIC utility.  The inability to move and copy files that require super-user access from the GUI is frustrating.  It should be easy to make a new directory and drag-n-drop, but I can't always do it.  Prompt me for the super-user password from the GUI rather than make me go into the terminal, type through long directory names, make sure access restrictions are set properly, and so on.

- a non-intuitive system of directory organization - programs and files for them are scattered.  Really, I wish there was a nice readme for each program that told me what they stuck in /var, /bin, /usr, /home, /etc, and where they stuck it.

-software that isn't in the repositories can be troublesome because most of it isn't pre-compiled.  Really, this is a minor hurdle.

**I like Ubuntu because:**

-I get basic functionality out of the box.  That's pretty good for something that's free.

-There's plenty of free software that's easy to access and install

-it works with most hardware, file systems, etc.

-I can tell it what to do

-what I see is what I get - I don't have to worry about anybody spying on me quite so much

-no meddling with spyware/adware/virus scanners

---

### Post by Sef on 2008-10-16
> - a non-intuitive system of directory organization - programs and files for them are scattered. Really, I wish there was a nice readme for each program that told me what they stuck in /var, /bin, /usr, /home, /etc, and where they stuck it.

Read Wikipedia's [Filesystem Hierarchy]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

---

### Post by aysiu on 2008-10-16
Closing for necromancy. The support post that revived it has been moved to its own thread.

---

