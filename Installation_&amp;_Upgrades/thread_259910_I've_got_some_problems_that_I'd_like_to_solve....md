---
title: "I've got some problems that I'd like to solve..."
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by Meroigo on 2006-09-18
Hello. I switched over to Ubuntu from Windows XP two days ago but I haven't figured out some things yet...

1. First there's Apache (Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1). This is the problem I want to solve the most. I have set up virtual hosts for some domain names and you come to my server when you type in any of those's addresses. When you go to one address, "Not found, The requested URL / was not found on this server." shows up. I have defined the DocumentRoot for every virtual host as "/home/meroigo/www/<domain>/site". Apache's ErrorLog says "[Mon Sep 18 08:23:33 2006] [error] [client 192.168.0.183] File does not exist: /htdocs" and nothing more when I access a site. When i run "apache2 -S" in the Terminal, it says "Syntax OK" and have no warnings. I've searched the configuration files after something that says "/htdocs" but I can't find it. So Apache is reading the configuration files and virtual host configuration since they work, but it doesn't seem to read the things within every virtual hosts' entry or something. I don't know. I used Apache on Windows XP and I never had any problems with it...

Does someone knowing Apache here know how they think I can solve it, maybe have any ideas... or do I need to put up my configuration files?

2. I have a network with another Windows machine and I can access its shared folders in Nautilus but I can't really fully open them if you understand what i mean... Like rar-files, I have to download them to this Ubuntu computer first. Same with movies and such. I'd like to open them over the network, because then I'd save much time... And in most programs, when I choose "Open file", I can't browse the network that I can in Nautilus, and the "connected servers" I have doesn't show up there. Really annoying in like VLC Media Player, when I store most of my movies and such on the other (Windows) computer because its hard drives have much more space.

3. I have Samba so the other (Windows) computer can see this Ubuntu computer. When I'm on the Windows computer and type in \\ubuntu (name of the computer) I get an dialouge where I have to fill in a username and password. I think I've read somewhere in some Samba thing that you fill in a username and password that you login with on Ubuntu. Nothing works. I'd mostly like no password and username so I can access the Ubuntu computer instantly...

4. I have two sound cards, because the one in my primary sound card has a broken microphone input, so I use that one for my earphones and the other one for my microphone. In Audacity you can change which device you want for output and which you want for input, so there it works, but in Skype, you can't choose two, so either I can just talk to people without hearing them, or not talk and just hearing them... And in Ubuntu's sound settings from the System menu, you can't select very much like you can in Windows... In Windows I could have like I have in Audacity. Do there exsist some good sound settings manager program I should try?

5. Is there a way to hide the "connected servers" from the desktop? How?

6. What software for Linux would you recommend for Direct Connect, scheduled backuping of folders to remote locations (over network), IRC and MSN?

7. Does someone have a link to a map or something of the Ubuntu keyboard shortcuts? I'm used to like Windows key + D for showing the desktop, Windows key + L for switching user without logging out etcetra...

8. How do I change which programs should open certain files? For example, I want Azureus to open .torrents, not BitTorrent. And VLC Media Player for all moviefiles, not Totem, etc.

9. I can't scroll on websites by pressing the scroll wheel and moving the mouse at a direction. But I can use it for closing tabs, open links in new tabs etc. In Opera, if i press the scroll wheel, it opens a new URL in the current TAB, they can be different, but often it's some kind of invalid URL...

... ](*,)

---

### Post by kidders on 2006-09-18
What a list!!

[LIST=1]
[*]Apache - Have you restarted apache after each configuration change? If so, it must be getting this reference to "/htdocs" from someplace ... are you sure you've checked *all* the config files?
[*]To get across-the-board access to remote shares, you really need to mount them.
[*]Using Ubuntu's default configuration, you need to set your users up in Samba before they can log in. Remove authentication altogether in your smb.conf on a share-by-share basis, if you want.
[*]Your sound card problem is interesting. You *might* be able to tinker with udev to get things to work the way you want. It's all based on device names as they appear in /dev ... manually specifying them may make things go for you :-)
[*]How to (and whether you can) hide things on your desktop depends on what graphical environment you're using. Of course, if you don't like the way it works, you can switch to another one :-)
[*]Simple scheduled backups can be done easily with cron ... IRC clients are available for Linux by the truckload ... Gaim and aMSN are common MSN Messenger clones for Linux/OSX ... What is "Direct Connect"?
[*]Linux's keyboard shortcuts are too customisable for there to be a definitive "map" ... there is no such thing as "Ubuntu" shortcuts. You can make your keyboard work any way you can possibly imagine, for the mostpart.
[*]How to associate particular programs with files is dependent on the graphical environment you're using.
[*]The way your mouse works is similarly customisable to your keyboard.
[/LIST]

A simple Google search will answer many of your questions far better than we can here. I hope some of these comments help though :-)

Post back if you have any difficulties!

---

### Post by Meroigo on 2006-09-18
> **kidders said:**
> What a list!!

[LIST=1]
[*]Apache - Have you restarted apache after each configuration change? If so, it must be getting this reference to "/htdocs" from someplace ... are you sure you've checked *all* the config files?
[*]To get across-the-board access to remote shares, you really need to mount them.
[*]Using Ubuntu's default configuration, you need to set your users up in Samba before they can log in. Remove authentication altogether in your smb.conf on a share-by-share basis, if you want.
[*]Your sound card problem is interesting. You *might* be able to tinker with udev to get things to work the way you want. It's all based on device names as they appear in /dev ... manually specifying them may make things go for you :-)
[*]How to (and whether you can) hide things on your desktop depends on what graphical environment you're using. Of course, if you don't like the way it works, you can switch to another one :-)
[*]Simple scheduled backups can be done easily with cron ... IRC clients are available for Linux by the truckload ... Gaim and aMSN are common MSN Messenger clones for Linux/OSX ... What is "Direct Connect"?
[*]Linux's keyboard shortcuts are too customisable for there to be a definitive "map" ... there is no such thing as "Ubuntu" shortcuts. You can make your keyboard work any way you can possibly imagine, for the mostpart.
[*]How to associate particular programs with files is dependent on the graphical environment you're using.
[*]The way your mouse works is similarly customisable to your keyboard.
[/LIST]

A simple Google search will answer many of your questions far better than we can here. I hope some of these comments help though :-)

Post back if you have any difficulties!

[LIST=1]
[*]Yes I make a restart each time I change anything, with "apache2 -k restart". Does it really read other config files than httpd.conf? In Windows Apache, that was the only one I needed to change to make things work.
[*]Yes, mount the shared folders. But I can't like go into one mounted folder and open a .avi file, those I have to copy to the Ubuntu computer first (which I don't want to). It won't play if I don't. But pictures for example can I open directly from the network.
And it's stupid that in Nautilus, I can see the mounted network folders to the left, but in a program, as I said, when you want to open a file from the program, no network folder/shortcut or anything is avalible there, that's stupid.
[*]About samba, does it exsist some GUI for it and where can I get it or do I need to edit some configuration file, which one?
[*]Okay, I'll try to figure out how to do that when I come home. :]
[*]I guess I'm using the graphical enviorement that's the standard when I installed the latest version of Ubuntu. What exactly is it? How can I change it or edit it?
[*]Direct Connect is this: [http://en.wikipedia.org/wiki/Direct_Connect_%28file_sharing%29](http://en.wikipedia.org/wiki/Direct_Connect_%28file_sharing%29) ...and now I saw some links to Linux DC clients there so I guess that's the best answer I can get for that. =)
[*]Where do I change the keyboard shortcut except the ones I can change avalible in the Settings menu? I think there should be more things you can set shortcuts for.
[*]Same answer as #5.
[*]Okay, but I can't find anything about it in the mouse settings in the settings menu.
[/LIST]

I'm sorry for being such a newb, but I'm new to Linux and I guess everyone is a newb some time... =)

---

### Post by kidders on 2006-09-18
Hey again,

**Apache**
Yep, if you take a look at Ubuntu's httpd.conf, many other files are included. Of the Linuxes I've used, it's the only one I've seen that modularises its web server config to this extent, but tbh I kinda like it! It makes module installations and virtual hosting a doddle :-) If you don't want to do things that way though, there's no reason you'd *have* to. Feel free to roll your own apache configuration, but bear in mind that apps you install subsequently might require manual configuration as a result.

Incidentally, you should really restart apache with **sudo /etc/init.d/apache2 restart**.

**Mounting shares**
If you've mounted your fileshares properly, copying stuff around is totally unnecessary ... unless of course your LAN is just too slow. If your network can't feed data to your media player at the speed it wants it, your movie will skip and stutter :-( You can check what's mounted by typing **mount** into a terminal.

> it's stupid that in Nautilus, I can see the mounted network folders to the left, but in a program, as I said, when you want to open a file from the program, no network folder/shortcut or anything is avalible there
That suggests to me that you haven't, in fact, mounted any remote locations, and that Nautilus is accessing them on the fly ... something very few apps are able to do (as you seem to have discovered!).

There are lots of GUIs to help you mess around with Samba, depending on exactly what you want to do. Examples include smb4k, KDE's samba configurator, and web-based ones like Webmin. Personally, I find directly editing /etc/samba/smb.conf faster.

**X Environments**
Ubuntu typically comes with Gnome installed by default. Personally, I can't stand it ... there are tens of other possible choices, many of which are quite ... well ... odd-looking! Hehe. You can use Ubuntu's package manager to install some of them, if you want to give a few others a try. Xfce and KDE are common choices, along with Enlightenment, Ratpoison, etc.

**Input Device Configuration**
This is usually done globally for your entire X server on a per-user basis. Tools like xmodmap and xev are pretty useful for sorting out what's what, especially if you have a mouse with lots of buttons, for instance. Basically, how you go about tweaking shortcuts depends on whether your shortcut is application-specific, or whether you'd prefer the underlying X server to intercept it.

Unfortunately, I haven't used Gnome in years, so I don't know much about how to configure mouse/keyboard shortcuts that apply specifically to things like Nautilus.

Hope that helps :-)

---

### Post by Meroigo on 2006-09-18
I solved the mounted disk thing so now my shared network folders are like hard drives or something. :] But when I did that, somehow, now a dialogue where it wants me to type in username and password pops up every time I want to browse the other computer over the network... Like clicking on Places, Network, Windows network, <my workgroup>, <the other computer, Windows>. I've entered that there should be no password promptning, in the samba configuration file... and no username and password works. Is this some bug? Because I can browse the mounted network drives without getting any password thing...

I solved the soundcard problem too. Haha, i just connected my earphones to the soundcard with the microphone. I don't think that worked over in Windows for some reason, but now it does. I can't hear any difference in the sound between the two sound cards so I guess this is fine... Hmm... But when I like listen to music in Rhythmbox, and I want to call someone on Skype, the sound settings stops working. Or it was that when I had called someone on Skype, stopped calling, started Audacity, it said something about the sound unit thing was wrong. So to make it work in Audacity I had to close Skype. And the other way with Skype. (I wonder if someone will understand what I just wrote =D)

About Apache. I've tried to fix it some hours now. It just never works. REALLY FUSTRATING. I'm thinking about going back to Windows again because there Apache worked as it should.. But I don't want to! But still I want a web server because I host several sites on it and my own. Gaah1! >_<;; ](*,)

I've tried to reinstall it several times in different ways, I've tried to uninstall and install some of the apache packages in the packet manager. But I noticed that when I uninstalled "apache2-mpm-preforked" made the "apache2" command not work and impossible to start the server (but that's strange since the Apache2 server is still intact in var\local\Apache2 (No, /var/local/apache2/bin/httpd start/-k start or something like that didn't work either). When it is installed, I get that error I've described before, when it's not installed, the server just won't start. It seems like it totally ignores the configuration files in \var\local\Apache2\conf or something... Linux is weird. =P

I don't really have many problems left now with my Ubuntu. But still the biggest problem of them all remains...

btw, how can I install a binary extracted from a .tar.bz/bz2 file when ./config, make or make install doesn't work? =/

---

### Post by kidders on 2006-09-18
Hi there,

Glad to see you've solved most of your troubles. Your apache issue confuses me though ... there are no apache-related binaries (or ones related to any other program) in /var!

Oddly enough, Linux is apache's native environment ... that it works in Windows at all is the real miracle :-P Perhaps you should just reinstall it from scratch, and read a little of the documentation relating to its configuration. You can, of course, arrange the config file/files any way that suits you personally. Configuration files are located in /etc btw, rather than /var.

Without intending to be rude, if you're looking for something that works like Windows does ... then you should install a Microsoft OS!

Your last question is a bit strange ... binaries, by definition, do not require compilation (./configure && make && make install). To install one, simply copy it to a convenient location. What kind of app are you hoping to install?

---

### Post by Meroigo on 2006-09-19
Hello

Sorry, I meant /usr/local/apache2. But thanks for telling me about /etc/apache2. When I put the configuration in the files in there it actually happens things. But what's the meaning of /usr/local/apache2 then? It's the latest version of Apache I installed from a tarball I downloaded from Apache's website.

But even if it happens things now they aren't good. The server fails to start and so on... So when I come back from school I'm going to completely uninstall all Apache things, reinstall them and go through the configuration carefully and hope I'll solve anything... By the way, if i choose to completely uninstall a package in Synaptic, do everything really disappear? Is it possible to see somewhere exactly where a program has installed (I'm thinking about the Apache I downloaded from Apache's website and used ./configure, make and make install in to install, I have no idea if the files are spread everywhere) so I can remove all the files manually?

I was trying install/run this program. [http://mono.dcsharp.com/](http://mono.dcsharp.com/) I suppose I'm supposed to run the file called "Fildelningsklienten DC#" (or if it's called "File sharing client DC#" in an english Linux or something...) in the Bin folder to start the program. Then it says that it couldn't run the child process "(BINDIR)s/dcsharp". Am I trying to run the wrong file or something? =P

Is it possible to get like a packagage with common package installs or something like that? Because if I download a program, it would likely often want something specific installed, let's call it X. So I google after X and downloads and install it. X wants Y and Z. So I have to go get Y and Z too. And maybe Z wants A, B and C.. Blah. It feels so unnecessary complicated and waste of time to install a program. Why can't they include all the things that's needed? =/

By the way, is there any easy way to make a partition bigger? I only made my Ubuntu OS partition like 10 GB, then a swap partition 512 MB and /home partition the rest of the space. Just wondering, in case I'll run out of space in the OS partition... I've allready used 3,5 GB on the first partition, I didn't think the OS plus some basic programs would take up that much space. O_o

By the way, thank you so much for the help so far. =)

---

### Post by kidders on 2006-09-19
> It's the latest version of Apache I installed from a tarball I downloaded from Apache's website.

This isn't smart, unless you're an experienced Linux user that can deal with the potential side-effects of installing something that hasn't been tweaked by your Linux provider's devs first. You should install one of the versions from Ubuntu's package repository.

Files in /usr are typically binaries, libraries and documentation required to run software you have installed.

> I have no idea if the files are spread everywhere) so I can remove all the files manually?

You *may* be able to remove most of them, assuming the apache you downloaded has an uninstaller. Such uninstallers typically don't touch configuration files though, particularly if you've modified them.

> Why can't they include all the things that's needed?
The simple answer to this is that Linux is all about choice. Often, application X may depend on Y **or** Z, which would make it inappropriate for the developers to make that choice for you. As you've pointed out, these dependency structures can get extremely complicated, so providing everything you could need to run apache, for example, would make the installer several hundred megabytes in size.

Ubuntu provides a package manager which handles all these dependencies for you. When I installed apache the first time, it took me about 10 seconds ... I clicked the right thing in my package manager and tweaked one of the files in /etc/apache2/sites-enabled, and I was done.

With regard to your partition-related questions, the short answer is "possibly", but 10G should be more than sufficient for an average home user. You may find that you've installed some very space-consuming libraries you don't really need, or something.

Just for the sake of clarity, if you install something from source without using Ubuntu's package manager, consider it the equivalent of trying to put Microsoft Office for Windows ME on a Windows NT 4 machine. It might work ... but then again, it might not. If you aren't experienced enough to know how to modify the installation so it *will* work, you really shouldn't try it without help.

---

### Post by Meroigo on 2006-09-19
Thanks for you sharing your knowledge about the things I wondered about, I really appriciate it! It's people like you that makes Internet so great. =)

The major Apache problem is now solved and everything works as it should (I had alot of trouble with PHP too, but I solved it with Google and trying different things myself =])! YES! I've tried to solve this since Saturday (3-4 days of server downtime, not good >_<). I feel like I'm the most leet person in the world or something (but of course I'm absolutely not, if I were, this thread wouldn't exist). xD

So I just uninstalled all the apache things on the computer, then reinstalled it (but only from the package manager). Then I configured the files one thing at a time, moving forward slowly. I did encounter some problems during the configuration but trying different things (...for like 3-4 hours >___<) works good.

Now moving right along. Finding an FTP server I can install without problems and use...

---

### Post by kidders on 2006-09-19
Hehe :-) Glad you're having some success!

There are plenty of FTP servers in Ubuntu's package database. Unless you require support for special features that one may have over another, it won't make too much difference which one you choose. Take a quick peek at each of their websites, for individual feature summaries.

All the best :-)

---

### Post by Meroigo on 2006-09-22
Hello again. I'm back. :]

I decided to inactivate the built-in sound card in the BIOS, because my Sound Blaster card is better... But I can't make the microphone work. Nevermind if I said it didn't worked before in Windows, it turned out it was the microphone that was broken...

Anyways, why can't I record anything even though the mic is connected? I've turned up the Mic volume and enabled it etcetra... =o

And I still can't figure out why a user/password dialogue where no user/password i type works, pops up when I want to browse a computer in the network from the Ubuntu computer. I have "security = share" in my smb.conf if that really should do any different in this problem that seem to be more like a bug. Browsing the Ubuntu computer from the Windows computer though, that works like a charm.

When watching a video on Google Video or YouTube etc, after a while, the sound is ahead of the video. What can the problem be? Some thing for the flash player I can change a setting for or something? :O

By the way, I've tried to make hardware 3D acceleration work in Ubuntu with my ATI Radeon 8500LE but it never works. I've read guides etc. I guess I have to try again some day when I feel like I really need 3D. Right now it's just Google Earh I want to use so it's no bug hurry... Any useful suggestions for me that can come in handy next time I'll try to fix it? ^^

Now it's just minor problems left until I'm completely satisfied with the switch to Linux! =)

---

### Post by Meroigo on 2006-09-24
Anyone? =)

---

### Post by kidders on 2006-09-24
Hi again,

> **Meroigo said:**
> Why can't I record anything even though the mic is connected?Have you turned up the capture volume, rather than the playback volume ... and done it to the right sound card? (Just in case)

> **Meroigo said:**
> When watching a video on Google Video or YouTube etc, after a while, the sound is ahead of the video.I wonder if this is a buffering issue.

> **Meroigo said:**
> By the way, I've tried to make hardware 3D acceleration work in Ubuntu with my ATI Radeon 8500LE but it never works.What driver are you using? There seem to be mixed reports about whether your card is really supported by Linux :-(

---

### Post by Meroigo on 2006-09-24
It looks right to me (and there's nothing wrong with the microphone, it works on other computers and it's pretty new)...
[IMG]http://img148.imageshack.us/img148/6830/micuy4.png[/IMG]
[IMG]http://img148.imageshack.us/img148/8163/mic2dq6.png[/IMG]
[IMG]http://img148.imageshack.us/img148/6880/audacityct3.png[/IMG]

I just know it's not a buffering issue. I think it has to do with the Flash plugin. =/

I've tried with the driver I could download from ATI's website, it said "supports Radeon 8500LE and later" or something (plus fiddling with the X11 configuration etc.. no success).

And I guess you don't know what the Samba problem can be?

---

### Post by Meroigo on 2006-09-24
By the way, if I enable an option called "Mic Select" and select "Mic1" ("Mic2" was selected first), I hear a loud hissing sound in my speakers/headphones and the sound that the microphone catches...

---

### Post by Meroigo on 2006-09-24
According to the following thread, the sound thing in flash videos seems to be a bug. =/ [http://ubuntuforums.org/showthread.php?t=263941](http://ubuntuforums.org/showthread.php?t=263941)

---

