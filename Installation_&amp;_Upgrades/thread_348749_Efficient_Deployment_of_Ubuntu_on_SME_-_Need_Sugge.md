---
title: "Efficient Deployment of Ubuntu on SME - Need Suggestions on (Pre)Install"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by Macchi on 2007-01-29
Dear Ubuntu Fellows,

I am about to help another Small Business Enterprise to switch completely to Ubuntu Desktops (and later add an Ubuntu Server). The traditional installation and manual configuration procedures consume a lot of time and are very prone to errors. Thus we have to find a way to deploy Ubuntu efficiently for at least half a dozen machines on a minor enterprise network. We are not yet using LDAP nor NIS-servers.

This time I got tired of extensive manual work during installation and configuration, thus I would like to collect suggestions and share experiences on how to to speed up the whole process. What do you think about the following installation procedure:

1) Create a Ubuntu OEM installation system image and copy it to a few NEW harddisks; 

2) Insert a harddisk (as slave) on a computer with an existing windows system (as the master disk);

3) Start again the computer system an initiate the installation (preferably as automatic as possible); 

4) Do some minor individual configuration adjustments for user data on every machine, (since I don't use a LDAP-server).


This procedure would have the advantage of keeping all previous data (hopefully) intact on the original master harddisk, facilitating migration of data. The possibility to boot on the original windows installation is also a good fallback solution for the transition phase. 

Later we intend to remove the disks with windows installations an archive them for some period, just as a backup. Eventually we may even perform a ritual destruction :) of those archived disks,  as part of the service. But only when the users approve completely the new Linux environment.

By inserting a new hard disk we are obviously also upgrading disk capacity. The disadvantage of such a procedure is that it requires physical changes to every client machine that is going to be reused. The technical work and additional equipment required (a new hard disk) are not a big burden, as long as we can pay our bills.
The information on the systems is much more valuable, and reuse of the existing hardware is a bonus. There is also a risk for damaging hardware in the field. 


Do you have any suggestions or experiences to share?

Best Regards,

---

### Post by Macchi on 2007-02-03
Five days, 27 views and no comments yet. I can only assume that it is difficult to get in touch with other users interested in professional deployment of Ubuntu for business enterprises. Or maybe this is simply the wrong time or place to ask. Or a wrong formulation of the problem.

Presently I am making manual installations of Ubuntu on every machine, with post-configuration performed through scripts. It takes quite long time to add and extra harddisk and install a dual-boot system, keeping the windows disk intact (with exception from the MBR).
The most time-consuming task has been the migration of data along with many manual adjustments for email accounts, messages, addressbooks, desktop settings, and favorites. 

I have used Thunderbird as a temporary solution but now need (desperately) a good migration tool and good methods for more efficient deployment.

---

### Post by mcglnx on 2007-02-03
I don't know if it can helps, but you can use apt-get to install all the necessary programs. 

With dpkg you can get the list of installed programs on one machine:
<pre>dpkg --get-selections</pre>
And then re-install them.

To save time you can as well use a local filesystem for storing deb packages and re-install other machine using this one.

For the user data, you'll maybe find more usefull to have a centralized server for storing. It will ease your backups as well!

HTH.

---

### Post by Macchi on 2007-02-04
Thanks mcglnx,

My goal with this thread is to get some input from the community on methods to install a customized version of Ubuntu simultaneously on several machines. It has to be fast and reliable for professional use in the field.

Yes I do use already the apt-get  to install and remove a list of predefined applications, in order to trim Ubuntu-desktop for a business enterprise. But that is the easy part of the job: just running manually a script from a USB-disk after the installation and system update.
Presently I am just using plain alternate-installation disks and repetitive manual work. I prepare every machine with a new harddisk, start them with the cd and install the system. Later I run the post-configuration scripts from a USB-disk. The most demanding part is the migration of data for user accounts with files, email, contacts, and favorites.

Actually I am looking for a more elaborate scheme that would only require installing an additional harddisk prepared with Ubuntu, and starting the installation with a standardized cd. This would not require setting up a network nor internet access. 

The ability to keep the Windows system disk intact has been a precondition, (with exception of the original MBR, that is saved to a file).  

I have previously used local servers for instaling SuSE (quite a lot). But it was slow, somewhat cumbersome and prone to errors. A local server can be very easily improvised with a laptop only for the installation procedure. This may be the method that I will choose, eventually combined with a cd to start the machines with no network boot. 

Another solution would be an adapted version of the alternate install CD. 

My resistance to a network install is the fear that the network would be a huge bottle-neck while installing several machines. A solution relying completely on install CDs can be difficult for practical purposes. Every update would require burning a new set of cds, to get the latest updated packages from start.

The idea of carrying the installation system on the harddisk would require some extra time to copy the image to the disks, but could be a quite fast way to transfer information within the system. 

I will continue my experiments with network install.

---

### Post by mcglnx on 2007-02-05
Well, on many companies (including my current) we are suing network install. It's quite powerfull and the only efficient way once you have more than 10 machines! (we have thousands!!!).
This is what I'd suggest for a unattended version... You'll have to net boot first - of course. The advantage is that you can use the same idea to propagate updates.

Using a 100Mb network it should be ok to update a couple of mahine at a time. True! And it's not a big deal since I suspect you won't do the process every day.

One alternative would be to have an install on an USB disk. I got one of 120G as a backup... It could be a good way as well + you would be able to update your changes. On the cons, you won't be able to updage many machines at a time :(

Regarding the data, I'd suggest to have them on a networked filesystem. It's safer and easier to backup. You could even use  distgributed filesystem like AFS [http://www.faqs.org/faqs/afs-faq/](http://www.faqs.org/faqs/afs-faq/) which is quite efficient and reliable.


HTH,
M.

---

### Post by cyber_bushi on 2007-02-06
Depending on the size of your installation you might want to install one machine, make an image of it and just put that on cd/dvd and just copy it to the harddisks of the other machines...
That of course only works if the hardware is identical on each machine. And you would have to change some things like name of the machine and so on... later... but that could be done by script...

---

### Post by cyber_bushi on 2007-02-06
Hej hej, läget? I just saw that you're from sweden...
anyways... maybe this is what you're looking for...
[http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html](http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html)
if you have any success, let me know. Would be interested, too!

cheers,

cb

---

### Post by Macchi on 2007-02-07
Thanks **cyber_bushi** and **mcglnx** for the comments and hints!

The link on [_Automatic Installation_ ]("http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s06.html") was what I needed. Network install is the way to go, and the data transfer bottlenecks are secondary issues. 
  
I will continue my experiments and intend to report the results back to this comunity.
In the meanwhile it is always good to collect here some notes and opinions from everyone interested on the subject!

PS: Yes I live in Stockholm, the beautiful capital of Sweden. Today we had a nice winter day, with sun shining on the snow and temperatures around -6 C (21 F).

Back to the subject, I have used the method with pre-installed images for windows and know that it works for cloning systems with identical hardware. Unfortunately I am not yet deploying a large number of machines, not a number that would justify the effort for cloning. The main challenge has been the manual customization of different machines. Users have their valuable data in the machine and are willing to move towards Linux for increased security, better software reliability(?), and lower costs on equipment and maintenance. 
Paradoxically, reusing the hardware and extending the life of existing computers has been causing some reliability problems on a few computers. Furthermore, data migration is really painful, most probably because I have not yet found the right tools.

Effective deployment of Linux desktops is indeed a serious challenge.

---

### Post by mcglnx on 2007-02-08
Welcome!

Pretty intereseting link! good!

On my sided I formelly used 'dd' (back in 1996) to re-install windows machine for testing client side applications developped in Visual C++ on Windows98 and NT. We wanted to be able to start from a brand new machine. It was pretty useful and worked well. I just had some issue with the MBR - but was easy to fix.

Regarding applications, they are some links around to propose 'equivalent' programs on Linux.
The only _probelm_ is the huge amount of choice which can be confusing for a new user.

I'd suggest you to choose a suite for Office and stick with it! (OppenOffice, Gonme Office or KDE office) I presonaly like Gnome applications. (Abiword, Gnumeric,...etc...)

Good luck Machi!

---

### Post by Macchi on 2007-02-09
> **mcglnx said:**
> 
Regarding applications, they are some links around to propose 'equivalent' programs on Linux.
The only _problem_ is the huge amount of choice which can be confusing for a new user.

I'd suggest you to choose a suite for Office and stick with it! (OppenOffice, Gonme Office or KDE office) I presonaly like Gnome applications. (Abiword, Gnumeric,...etc...)


Yes mcglnx, I agree and here is a short description of:
MY PRESENT EXPERIENCE ON MOVING WINDOWS USERS TO UBUNTU
One of the problems experienced by novice office desktop users with the standard Ubunbtu installation is a "big" number of choices that they are not familiar with.
Thus I remove many applications and items from the menus in order to make clear which applications are available and what they do. I edit the menus to add good explanations on what the programs actually do. Otherwise the transition from Windows to Linux has been quite okey. Data conversion and character encoding is still a problem and for instance users get confused on when to use .doc, .pdf or .odf. With windows they just shared .doc files (ugly!).   

PS: My customizations are approximately:
OpenOffice is enough, and I remove references to base to avoid confusion. I hide most items from Applications->Sound&Video, Accessories, Internet, and hide System Tools. Games are not applicable for serious professional desktops thus they are removed from the machine. I add a ssh-server for remote administration and install restricted codecs, plugins for firefox etc. At last I used to add a FreeNX server for remote access and support  through a remote encrypted desktop, but for the moment I have no alternative on that fron since NoMachine changed their policy and VNC variants do not offer ssh encryption out of the box (compressions and X optimization seems limited compared to NX).

---

### Post by mcglnx on 2007-02-10
Seems pretty nice!

Regarding the document extension, I share some ideas with others.

The Open/Save buttons are coming from the dark ages of the computer when saving was a l ong process, on a slow-mono task-floppy based computer. Now we have virtually no limit on HDD size, multi-process and speed.

I'd suggest the application to automatically save files (see Tomboy)- as well as delta (see Eclipse local history). No format, nothing, just finding documents by name / subject,....etc and edit close. That's it. 
Then for sharing - just select 'Export/Import' entries. 

Of course, for the 'power user', it would be possible to come back to the 'dark ages mode'. Frankly speaking, I would not :)

BTW: I'd be curious on a report on the success after 6 months! :)

Cheers,
M.

---

### Post by cyber_bushi on 2007-06-03
Deploying harddisk or partition images over the network in a ghost-like manner:
[http://www.feyrer.de/g4u](http://www.feyrer.de/g4u)
I like it and use it. Don't forget to donate, if you like it, too...
You can also google for Daniel Ettle's YAGI...
regards,

cb

---

