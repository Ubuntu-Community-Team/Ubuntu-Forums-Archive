---
title: "Fast package reinstall"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by Aphoxema on 2008-08-14
I've reinstalled ubuntu several times for one reason or another, and one thing that's getting me is remembering what all I had installed when I do.

Is there any way to use like, /var/lib/dpkg/status to back up the list of packages I have installed and then use that later to reinstall those packages?

---

### Post by Herman on 2008-08-14
I'm sorry I can't answer your question directly, but I can offer you the following link, how to [Backup installed packages on ubuntu]("http://www.ubuntugeek.com/backup-installed-packages-on-ubuntu.html") - Ubuntu Geek.
A list of packages in /var/cache/apt/archives would give you a pretty good idea,
```
ls /var/cache/apt/archives
```I just make a backup of all the .deb packages (the entire contents) of my /var/cache/apt/archives and them copy of of those into /var/cache/apt/archives in the new installation. 
It means the packages are all there already so I don't need to re-download them again before installing them.
```
mkdir Backup
``````
sudo cp /var/cache/apt/archives/* Backup/
```Then I just re-install the packages again, any old way I like, using apt-get or with the gui add/remove or synaptic, it doesn't matter, the main thing is that nothing needs to be re-downloaded which saves a lot of time and some bandwidth.
That's a nice simple way of doing things.


If you want to be a little fancier, a command you might find useful could be ```
sudo dpkg --list
```You can make a command like that send it's output to a file for you if you want, like this,
```
sudo dpkg --list >> packages.txt
```If you ran the above command in a fresh new installation and then installed all the packages you want, you could run the same command again but creating a second text file,
```
sudo dpkg --list >> addedpackages.txt
```Then you could use the diff command to make you third text comparing those two files and giving you a list of the added packages,
```
diff packages.txt   addedpackages.txt >> addedsoftware.txt
```I have read that a command something like the following might then be useful, it should work but can't remember if I have tested it myself yet,
```
sudo dpkg --get-selections > addedsoftware.txt ; dpkg --set-selections < addedsoftware.txt
```You should be able to have some fun with some of those commands, I hope you'll find something useful there.

Regards, Herman :)

---

### Post by wolfen69 on 2008-08-14
you probably want [APTonCD]("http://aptoncd.sourceforge.net/"). download the .deb file or get it in Synaptic.

---

### Post by Aphoxema on 2008-08-14
Herman, I think that will be very useful. Thank you.

---

### Post by robert shearer on 2008-08-14
Maybe think about backing up your working install to dvd as a live reinstall disk with all your apps and data,(then adding any updates via aptoncd ?)  

see this link for more info   [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)
and this how-to  [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

