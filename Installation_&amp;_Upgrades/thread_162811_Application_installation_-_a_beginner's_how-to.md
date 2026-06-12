---
title: "Application installation - a beginner's how-to?"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by dglp on 2006-04-19
Three days after figuring out how to install Kubuntu 5.10 on my laptop, I am now wondering how to add new applications. I see that the apt-get command is used a lot to retrieve files from some internet location - but I do not have network card for this machine, so cannot use that method. (I barely know anything about using command-line editors in fact, if Kubuntu uses *gedit*, I don't know about it. I only see Konsole. I should add that I know nothing about setting up network shares/Samba either...)

I can download .tar files to a Windows machine and copy them across with a portable drive, so then the issue is what to do next. I do not know if I have to do things to repositories, and am not quite clear on that concept - even after reading [https://wiki.ubuntu.com/AddingRepositoriesHowto#head-3af7264a0e97edbc5bf039e5bdb971f46c43269a.]("https://wiki.ubuntu.com/AddingRepositoriesHowto#head-3af7264a0e97edbc5bf039e5bdb971f46c43269a") 

So I am looking for a general explanation of what happens in the installation process, and some general instruction about installing applications I've copied off the 'net.

---

### Post by Jagot on 2006-04-19
Take a look here - this may help you with some stuff:

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

---

### Post by dglp on 2006-04-19
Good stuff!

This> However, there is a graphical version of apt-get. For Ubuntu, it's Synaptic Package Manager. For Kubuntu, it's Adept.  explains three things in one sentence. I've been seeing 'Synaptic' all over the place, wondering WTH it is, and now I know: It's a different version on Adept ...whatever *that *is...;)
> Instead of listing a bunch of applications you want to install, you mark each one for installation (or removal), and then click *Apply Changes* or *Commit Changes* and then everything's downloaded and installed (or uninstalled). Okay - except that I don't get to do the download part... So I need to know where to drop files, and how to do the equivalent of running *setup.exe.*
> Download the .deb file to your desktop. For this example, let's use Opera [...] opera_8.50-20050916.6-shared-qt_en_etch_i386.deb. [...] open up a terminal and type these commands: 
 ```
 cd Desktop
sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
``` Good. Coming along quite nicely!> **Manual installation of a .rpm**
Occasionally, for a program, you're just not able to find a .deb. There may seem to be, however, a plethora of .rpm files for the program. [...]One-time deal, just to get alien: ```
sudo apt-get update
sudo apt-get install alien
``` Hmm. No can do. Skip that one.
>  There's also Checkinstall: Once checkinstall is installed, instead of typing sudo make install you type sudo checkinstall -D and the program creates a .deb file which is then installed. This sounds interesting. I'll have to go look to see if there's an explanation of how to install it. 

Back in a bit.

No luck there. > 
**Installation**
   sudo apt-get install checkinstallMaybe I should change the title of this post to 'Installing without apt-get: how to?'

---

### Post by aysiu on 2006-04-19
Software installation without internet is going to be painful.

Just wanted to let you know.

That said, [this add-on CD project](http://www.ubuntuforums.org/showthread.php?t=136955) may help.

---

### Post by dglp on 2006-04-19
[quote=aysiu]Software installation without internet is going to be painful.[/quote]

Okay. Thanks for the warning!
:D

---

### Post by Jagot on 2006-04-19
Packages that come in the form of a .tar packages you will need to build from source.  You cannot build from source with a default Ubuntu installation.

---

### Post by dglp on 2006-04-19
[quote=Jagot]Packages that come in the form of a .tar packages you will need to build from source.  You cannot build from source with a default Ubuntu installation.[/quote] 
Okay. Thanks for that clarification. The stuff above about .deb was a bit of a clue that I'd been looking at/for the wrong kind of files, so my reference to .tar was based on not knowing what to look for.

So the focus should shift to how I get this old thing networked....

---

### Post by Jagot on 2006-04-19
OK, Sorry if I misled you a bit with that link.  Having an internet connection all the time with my Ubuntu comp, I forgot about the extra packages you would need to install before you can install other stuff.  .deb's are pretty much the easiest way to install programs unless you have access to apt-get.  If you can't immediately find a .deb for the program you want then have a search around because some people do produce them unofficially.

---

### Post by dglp on 2006-04-19
I'm still making my way through the thread, wiki, etc, but I see that the list of Generally Approved Packages is quite short. I have a suggestion: it would be good to have an application that could respond to apt-get from a local drive, i.e, something that gave apt-get the option of looking locally as an alternative to the internet. That would be a boon for us off-line folk. Is such a thing possible? Is it possible that a command-line switch could be implemented, even?

---

### Post by dglp on 2006-04-19
Okay. 

Here's another thought: if I install Kubuntu on a machine that's networked, and run apt-get from it, is there some way of 'moving' the installation across to another machine via portable drive or CD? I would guess that's not possible - but hey, I'm still gonna ask!

---

### Post by Jagot on 2006-04-19
I'm fairly certain that on a default Ubuntu installation, one of the sources from which apt gets files is the Ubuntu cd.  I'm not in Ubuntu at the moment, but you may want to have a look at your /etc/apt/sources.list and see what the format is for this - I'm sure it could be adapted to point to a local drive.

---

### Post by dglp on 2006-04-19
Yes indeed, I would think that it is just a matter of pointing the right way. I opened the list in Kate, and see that various repositories point to a web address. The first item says ```
##Uncomment the following two lines to fetch updated software from the network
# deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted
``` I would hope that 'network' could include the root folder or some such.

---

### Post by yoink23 on 2006-04-19
[QUOTE=dglp]I have a suggestion: it would be good to have an application that could respond to apt-get from a local drive, i.e, something that gave apt-get the option of looking locally as an alternative to the internet. That would be a boon for us off-line folk. Is such a thing possible? Is it possible that a command-line switch could be implemented, even?[/QUOTE]

Sources for apt are spelled out in sources.list.  The ubuntu cd (which is local, assuming you have it in the tray) is in sources.list by default, so yes, it does look locally as well.  If you are thinking about downloading a whole repository onto portable media, whether that is possible is beyond my knowledge.

Keep it up, its so worth it once you get going!

PS. If this is not helpful, then please disregard, but: a few dollars on a network card might be worth the pure pleasure of using a great system like apt without any complications.  It makes life so easy.  If that is definately not an option, then sorry for mentioning it, but I thought I might save you some blood sweat and tears.

---

### Post by dglp on 2006-04-19
[quote=yoink23]PS. If this is not helpful, then please disregard, but: a few dollars on a network card might be worth the pure pleasure of using a great system like apt without any complications.  It makes life so easy.  If that is definately not an option, then sorry for mentioning it, but I thought I might save you some blood sweat and tears.[/quote]

Yep, ten pounds will get me a USB-to-network dongle, but since it hasn't arrived yet, and I need to get some files converted/opened on the laptop, I was hoping to install conversion software and keep working in the meantime. BUt it's also worth knowing how thigns work, and so much of linux/Ubuntu is so very strange still, that a good overview of how it works is a very helpful thing.

Back to my main concern: I see that Adept associates deb types with a variety of locations and components. One of the locations is file:///cdrom. What would happen if I made a new repository at file:///home/apps? What components would it need in order to install a deb file from within that folder?

---

### Post by dglp on 2006-04-19
Okay, I've figured out a few things...

One: if an application is available in .deb format and is known to be free of dependencies, then it can be installed using Adept, Konsole and Konqueror.

Two: the *.deb file needs to sit in an easy-to-locate directory. I created one: Home/User/Software and dropped a *.deb file into it.

Three: Fire up Adept (K Menu|System|Package Manager). In Adept, select Manage Repositories under the Adept menu (Adept|Manage Repositories).  Note that the display columns are Type: URL, Distribution, and Components. Also note that the first item on the list is [deb  file:///cdrom/   breezy  main restricted].
If you right-clisk on a row with your mouse, you will se an option to Clone the row. That's what I did with the cdrom repository.

[IMG]http://tbd[/IMG]

I then modified the clone to point to my new Software directory. The result was [deb  file:///home/dp/Software   breezy  universe]. I clicked on the Apply button and exited Adept. The overall process is about creating a repository. (I gather that it can also be done by editing **/etc/apt/sources.list **using Kate.)Having done that, I went into Konsole and issued a command. 

On opening Konsole I am prompted by username@node:~. I 'became root' by issuing 'sudo -i' and entering my password when prompted. I then navigated to the Software directory: 'cd /Home/dp/Software' so that the command line prompt looked like this: 
root@hayseed:/home/dp/Software#
I then issued a dpkg command: dpkg -1 app_i386.deb and was rewarded by the message 'Selecting previously deselected
package' and a few lines about reading database and setting up code. 

That seems to have done the trick. If so, the main issue sems to be about knowing which apps have no dependencies, although my guess is that  Adept might be able to deal with that issue.

---

