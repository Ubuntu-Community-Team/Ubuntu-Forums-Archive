---
title: "[SOLVED] Installing files in Ubuntu"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by nir2000 on 2008-11-15
Hello!
I am quite new to Ubuntu, and I am a little confused from the complexity of installing an applet or a program in Linux. I know that there are compressed files but I don't know what "open" or "extract" means. I also do not know what is the equivalent in linux to the "exe" file in Windows.
In addition, I do not understand where the files that I download from the internet  go. And last but not least, do I have to create more folders in my file system to accommodate new programs and files, and where do I create them?
I will appreciate a comment or a redirection to an article or a site which explains all those things.
Thank you for your patience.
Nir****[FONT="Arial Black"][/FONT]

---

### Post by Herman on 2008-11-15
It's actually very easy and simple for most programs, unless we're installing something extremely unusual. We don't need to go extracting or opening compressed files ourselves, the installation programs do all that stuff for us.

In Ubuntu, the traditional way to install our software and programs is by using an 'apt-get' command.
For example, '[FONT=Bitstream Vera Sans Mono]sudo apt-get install youtube-dl[/FONT]' will install a command-line program we can use for downloading youtube videos.
```
sudo apt-get install youtube-dl
```We can install a lot of packages with apt-get, I typed 'sudo apt-get install ' ..and pressed my 'Tab' key for auto - completion, here's what came up in my terminal, 'Display all 34044 possibilities? (y or n)'.

There are some 'command-line' programs and after you install those they probably won't appear anywhere in any menus. Instead, we just remember that they're there and they are started by typing the command for them on the command line, for example, I might type 'youtube-dl' (without the inverted commas), as a command and paste a URL after it for a youtube video I like.

Other applications are 'GUI' (Graphic User Interface) programs and you'll normally find an icon and a link for those in your 'Applications' menus somewhere, according to what heading they come under.

Synaptic Package Manager is a GUI for apt-get, 'System'-->'Adminstration'-->'Synaptic Package Manager'. It might take all day just to scroll through the whole list of packages in Synaptic, especially if you take a minutes to read a little description about what each package is for. Fortunately there are excellent sorting and search functions.

A somewhat shorter list of all the most popular software can be found and installed through 'Applications'-->'Add/Remove Applications.'  That's a lot quicker and easier and can be used most of the time.

Free software is available from 'repositories' on the internet, [Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu"), and there are various different kinds of repositories, according to the various standards that software must meet to be allowed to be presented in each repository. Here is a link that explains why we have "Main", "Restricted"," Universe, and "multiverse", [Components]("http://www.ubuntu.com/community/ubuntustory/components").

There are some very good security measures in place to help keep us safe, [SecureApt - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SecureApt").
However, it is up to the user to decide which repositories to enable and there theoretically could exist some repositories that might not be so trustworthy, so be careful about adding strange repositories to your /etc/apt/sources.list file. Also be careful about downloading .deb files from websites on the internet and installing them. 

We have .deb files instead of .exe files, and they are stored in a directory called /var/cache/apt/archives. 
You can make a backup of those .deb files if (unlikely), you might need to re-install for some reason. That may save you from having to re-download them all again.
On the other hand if you're running Ubuntu in a flash memory stick you might want to run 'sudo apt-get clean', to delete them all and save disk space.
 They're only good for the same version of Ubuntu, and they get superseded fairly quickly, so they're not worth keeping for long.

If you need to see where all the files associated with an installed package went to, (for some reason), one way to do so is to open Synaptic Package Manager and search for the program or package in question.
Then, right-click on it and click 'Properties', and select the 'installed files' tab.
You'll be able to see exactly where all the files from the installed package are in your system that way.

For a more comprehensive and better coverage of information about how to install software in Ubuntu, see Ubuntu Web Forums Sticky: [Complete Guide to Installation in Ubuntu]("http://ubuntuforums.org/showthread.php?t=500020") by starcraft.man.

Regards, Herman :)

---

### Post by nir2000 on 2008-11-15
Herman, thank you very much for taking your time and explaining all this to me.
I realy appreciate this .
bye

---

### Post by Herman on 2008-11-15
:) Okay, this is kind of an interesting subject, and it's rather an important one too.

**Some thing NOT to do** -(unless you really need to and you really know what you're doing).

I remember the trouble I had at first. 
When I was new with Ubuntu, one of the first things I noticed was a pop-up in my firefox web browser that advised me that I needed to install some extra software to see everything on that page -  (more advertisements probably).
But curiosity got the better of me, and I was led to another website where one could click to install something for Windows, but for Linux we had to download a .tar file and there were instructions for how to install it in 'Linux', something like; [Build, Install software on your system]("http://www.faqs.org/docs/securing/chap13sec111.html"),
```
tar jxf file.tar.bz2
ls
cd path-to-software/
sudo ./configure
sudo make
sudo make install 
```After following these 'Linux' instructions, - my system was coming up with strange error messages like 'the software index is broken' or something like that, and I wasn't able to update my Ubuntu or install any more software until I fixed it.
Since I didn't know how to fix it I had to re-install.

What I think happened is, there are around 100 or so different Linux distros, and the instructions I was faithfully following, (and probably the software too) were really intended for Redhat Linux or Redhat based Linux distros, like Fedora and the like.
Ubuntu was new in those days, and installing software made for Redhat in Ubuntu might be a little bit like installing Chev parts in a Ford. (Some parts might just fit or be made to fit if you're an expert with a machine shop, but other parts just will never work as well as the genuine parts).
I'm not sure if that's a good analogy or not, but that's my impression.

So, unless you have already checked in 'Add/Remove Applications', 'Synaptic' and 'Apt-get' for the version of that software that's made for Ubuntu and can be installed automatically, there's no need to install foriegn software from tarballs.
(Unless you're doing something special and you either know what you're doing or are following instructions from a well known and reputable site). :)

---

### Post by Herman on 2008-11-15
**Another thing to be careful of is installing 'services'.**

By 'services' I mean various networking or file sharing types of software that opens 'ports' in your Ubuntu system.

A fresh installation of Ubuntu will come up as pure 'stealth' on all ports if we give it a port scan from another Ubuntu computer in the same local area network.

In the computer to be scanned, you need to know the IP address (number). 
The easiest way to get that is just to go to the other computer and run 'ifconfig | grep 'inet addr:', (or just run 'ifconfig').

From the scanning computer go 'System'-->'Administration'-->'Network Tools', and click on the 'Port Scan' tab.
Type in the IP address of the other computer you want to scan for open ports, and hit 'scan'.
The scan only takes a few seconds and it should not find any open ports.

If it does you should probably consider either uninstalling the software that opened that port, or else configure the firewall.
Firewalls work great when they're in lockdown mode, and they can stop you from being able to do a lot of fun or useful things.
Linux IP Tables filter (firewall), and tools for configuring it are extremely flexible and versatile, and it can be very interesting to read and learn how to use them. 
not everyone has that much spare time or  is interested in becoming an IP Tables or firewall expert though.
If we're going to install 'services', really we should try to learn a few things about filters or 'firewalls' first. 

The main problem with firewalls is that nut behind the keyboard. :)
Most Windows users feel safe behind their proprietary firewalls but then they always choose to 'allow' any service access to the internet because they want to get their work done or have some fun with their computer. Usually their in too much of a hurry to google what the application is and whether or not it's 'safe'. Then usually it's not so simple to decide if it's actually 'safe' or not. After a while most people chose to just 'allow' anything and everything through their firewalls.
What's the use of installing a firewall at all if we're then going to allow everything and anything in or out through it?
That's worse than having no firewall at all, because the user has a false sense of security.

In Ubuntu, while we stick to just using software from the official Ubuntu repositories we're pretty safe.
These programs are checked constantly for vulnerabilities and updated with patches if any vulnerabilities are found.
We can be sure we won't be installing any 'rogue' programs that will 'call home' and install some kind of a 'rootkit', as may happen with certain 'other' operating systems where the users are in the habit of installing software from random internet web sites.

What if we want to install something like 'Skype' so we can communicate with our friends who use Windows? 
Really we're supposed to use Ekiga Softphone instead, but then we can only communicate with our fellow Linux users. 
Skype is a program that's not officially supported by Ubuntu, so it can't be guaranteed to be safe. Probably it's okay though.
To install Skype, we just go to the Skype website and download the latest Ubuntu 7.04+ .deb file for it and double-click on it to install it.
I have skype in one of my computers and it's great! [*Skype* - Community Ubuntu Documentation]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=9&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FSkype&ei=9pwfSb_SOpr0sAOFn9XICA&usg=AFQjCNH3aSDvXYDCrCq0WW66nKaiRqhC2w&sig2=yhobsz9Yo-DCE74lrTupYA") 

Another one a lot of people like is a file sharing program called 'Frostwire'.
Frostwire can be installed similar to Skype. It's a program for sharing all kinds of files, but most people use it for sharing music and movies.
[*FrostWire* - Community Ubuntu Documentation]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=5&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FFrostWire&ei=sJsfSfSHLpr0sAOmntHICA&usg=AFQjCNGUFn46vKf9fmyhL0pVY4ICamXnvg&sig2=_62xfM6nh1YMl0H-c2EBVA")

The trouble with installing programs like that is that they are hard to make safe. After all, you are inviting anyone in the world into your computer. 
There are features built into the program for making sure people can only go into directories that you have allowed though, or in the case of skype, perform functions with your hardware that you expect, (like see your picture in real-time through your webcam and hear your voice). What if there is some vulnerability that a cracker might discover in one of those programs that can be 'exploited' to allow them access to your personal files or to take more control over your computer than you expected?

My suggestion to people who want to run programs that might or might not be so 'safe' is to have a whole separate Linux installation just for those programs.

---

### Post by oldos2er on 2008-11-15
[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

 [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by PhiberOptik24 on 2008-11-15
Herman,

Thanks for the very clear and detailed explanation regarding installing programs on ubuntu.  I'm in the same boat as the OP.  It takes practice and it's also hard to withdraw from Windows protocols and processes.  .

If I downloaded a program and save it on my desktop, how do I direct synaptic manger or add/remove to the desktop location?


Desi :guitar:

---

### Post by Herman on 2008-11-15
> If I downloaded a program and save it on my desktop, how do I direct synaptic manger or add/remove to the desktop location?That's a bit like the old riddle about how you get down off an elephant? (You don't, you get down off a duck). :)
What I mean is, if you had to download a program from somewhere on the internet, you probably shouldn't be installing it in Ubuntu, (unless you're an expert and you know what you're doing or are under expert instructions).

First check in Add/Remove Programs and in Synaptic Package Manager to see if there's a program in the repositories that will do the job you want to do.
Most of the time there's already a Ubuntu version of the same programs already in the repositories. It's a lot easier to install programs that are in the repositories and which Ubuntu developers approve of and support before resorting to a foreign program from somewhere on the internet.

If there is a program that will do most of the things you want but not quite everything, try to find out if that program has it's own Web Forum, and/or maybe even get in touch with the developer of that program. Most developers welcome suggestions for how their programs can be improved if we ask them the right way.

To answer your question, if it's a .deb file and you really want to install it by directing Synaptic to it, (theoretically that would be possible, but I can't see why it would be practical), I imagine you would be able to add the path to your download folder to your /etc/apt/sources.list file. We can do that if we want to get software from a CD or DVD.
Like I already said though, if it's a .deb file made for Ubuntu like the ones for Skype or Frostwire, we just need to double-click on them.

Regards, Herman :)

---

### Post by Herman on 2008-11-15
Here's a link to an interesting thread,
[Cool applications you use that others might not know of]("http://ubuntuforums.org/showthread.php?t=382137&highlight=cool+software+heard")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=382137&highlight=cool+software+heard") [2]("http://ubuntuforums.org/showthread.php?t=382137&page=2&highlight=cool+software+heard") [3]("http://ubuntuforums.org/showthread.php?t=382137&page=3&highlight=cool+software+heard") ... [Last Page]("http://ubuntuforums.org/showthread.php?t=382137&page=129&highlight=cool+software+heard"))

It can be lots of fun browsing through 'Add/Remove' or 'Synaptic' and installing any programs that look interesting and trying them out.

Even if these programs were only assumed to be worth one dollar each on average, with over 34,000 programs all together, that would be at least $34,000 worth of free software! :)

We never know what we'll find, some of these programs are excellent, well finished programs that have far more functions built into them than equivalent programs you might pay $1000 for to install in a proprietary operating system.

There are tips 'n tricks and maybe a few secrets to be learned in order to get the most out of each program.
If you have a Linux or Ubuntu club or group in your town or area it could be a lot of fun for each club member to try researching one program and learning how to use it well, and making a presentation on it for the others.
(You don't need to have a very formal club for that, just any group of friends who enjoy using Ubuntu can have a lot of fun helping each other).

If the use of a program you want to try our doesn't have enough information in the 'help' or documentation, it might have a web forum where you can go to take a look around and ask questions, (or at least a website). 
Sometimes the best way to learn is by running your own experiments too.
Of course, there's the Ubuntu Web Forums here, as well as google.

---

### Post by Marcus Derekus on 2008-11-15
One reason linux files come in compressed packages is so you can install them on different distros

---

