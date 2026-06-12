---
title: "uninstalling information"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by jnicita on 2006-10-15
I have a quick question.
I have a few applications that I installed into my 6.06.1 installation. There were a few that I took the time to download the sources, compile the applications, and use the make and make install's to install them.

I basically used this method because I started using these applications before ubuntu's 5.04 release and they were not listed or easily obtainable via the X based installation tools. 

I'll just focus on gdesklets, since its one that I most recently had issues with.

I downloaded the binaries and compiled the application myself. It kicked out various errors about various pieces of my python install that had issues. One at a time I used sudo apt-get install "phython piece" until I got the application to successfully complete the configure routines.

I finally got a no error installation with make and make install, but when I tried to run the application, from the applications -> wherever -> gdesklets, I get a taskbar field showing its starting but then nothing ever progesses and it just goes away. I check for the applicaton with top and ps -ef and dont see it, it obviously is failing. 

I later then discoved that I think it might have been auto-installed with a  "Gnome desktop enhancement" package  (a batch file with a series of apt-get install _app_) that I found on another site (from now on Im paying attention to the pieces something like this installs), like I said, I wasnt aware that I could or might have installed it with  synaptic package manager, but It was now "installed" via the package manager. Plus I know I installed it with the self compiled version using configre, make, make install. 

Now, the app never worked, so I figure I'll start removing all traces of it and start over. Using the pacakge manager is simple to remove, but I dont know how to remove all the work that I did with the make install. To be honest, I havent checked or did a search on removing apps installed manually with make install. I'll do this just as soon as I post this message. Thanks for any help....

JN

---

### Post by taurus on 2006-10-15
You need to download the source for that package and instead of running the "sudo make install" to install it, you want to run "sudo make uninstall" to remove it...

---

### Post by jnicita on 2006-10-15
Thanks, but I found a even weirder scenario.
I used all the of the "package" uninstall obtions, I.e. used the synaptic manager to completely uninstall, and then used the apt-get remove app app-extras.

Then from the command line, I hit gdesk[tab] and it found the gdesklets that I had complied previously, I hit enter to run it and was presented with the starting deamon and short bloat message I remember, and just like thatI was presented with the running applicaiton icon in the notification location of my pannel.

Now I just need to go make sure it auto-starts and all should be good to go..

Now to find some packages of applets for it..

---

### Post by taurus on 2006-10-15
I hope you know that you can get gdesklets & gdesklets-data from the repos...

---

