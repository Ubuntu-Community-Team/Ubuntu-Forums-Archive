---
title: "Is going to 5.10 via network possible?"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by kline on 2005-11-11
Since I don't have a CD burner and since I'd rather not bother Ubuntu for a CD, can I pull the src over the net and build/install 5.10 myself?  I could then upgrade all packages over several days... .

I like the way Ubuntu keeps my packages current; also, that I can run Gnome, KDE, and ctwm (in /root).  I just finished upgrading one of my FreeBSD servers to 5.4--it took < a day to download, install, and for me to hack /etc.   As nice as Debian/Ubuntu is, not being able to upgrade the kernel via the net is a gotcha.

Any feedback from the wizards?

gary kline

---

### Post by adwait on 2005-11-11
Umm.......If I understand you correctly, you want to upgrade from 5.04>5.10 right? If that's the case, ofcourse you can do it over the internet. Just open up the file /etc/apt/sources.list with
```
sudo gedit /etc/apt/sources.list
```

Change all the references to the word "hoary" with the word "breezy". Save the file and exit. Now run
```
sudo apt-get update
sudo apt-get dist-upgrade
```

This will download and install all the updates etc.

---

### Post by whittycat on 2005-11-11
I should be able to do that but what happens to the current configuration. I had to tweak things to configure ethernet, wireless, mail, 
postfix, etc.  If I upgrade to 5.10 do I have to read a different set of 100p documents and do the tweaks again?

---

### Post by adwait on 2005-11-11
Well your configuration remains the same since the config files are stored in your home directory (that would be basically your personalised settigns). As for the tweaks that you might have done to config files in /etc, the installer asks you every time if you would like to replace a certain config file with the new one so you can accordingly answer.

---

### Post by ranf on 2005-11-11
[QUOTE=adwait]Well your configuration remains the same since the config files are stored in your home directory (that would be basically your personalised settigns). As for the tweaks that you might have done to config files in /etc, the installer asks you every time if you would like to replace a certain config file with the new one so you can accordingly answer.[/QUOTE]
And if you decide to keep your settings it stores the new .conf as .conf.dpkg-new. So if there is a need for some new settings you still have them available.

---

### Post by kline on 2005-11-11
[QUOTE=adwait]Umm.......If I understand you correctly, you want to upgrade from 5.04>5.10 right? If that's the case, ofcourse you can do it over the internet. Just open up the file /etc/apt/sources.list with
```
sudo gedit /etc/apt/sources.list
```

Change all the references to the word "hoary" with the word "breezy". Save the file and exit. Now run
```
sudo apt-get update
sudo apt-get dist-upgrade
```

This will download and install all the updates etc.[/QUOTE]

Thanks!  Here's what I've done; in cmd-line format.  Please tell me if this is what you meant:


// In a terminal:
% su
# cd /etc/apt;
# perl -pi.bak -e 's/hoary/breezy/g' sources.list;
// then I cut and pasted your sudo apt-get commands.  

Watching things in an terminal,  the update is happening.  It seems to me that if doing an upgrade via the net is *this* simple, this should be scripted so that command-line hackers could exec the script; then go have a cup of coffee and a long nap ;)

---

### Post by whittycat on 2005-11-11
I have just done it and it really is that simple. I didn't watch it all but I caught sight of a compilation error in gstreamer; I'll report that elsewhere. Thanks

whittycat

---

### Post by kline on 2005-11-12
[QUOTE=kline]Thanks!  Here's what I've done; in cmd-line format.  Please tell me if this is what you meant:


// In a terminal:
% su
# cd /etc/apt;
# perl -pi.bak -e 's/hoary/breezy/g' sources.list;
// then I cut and pasted your sudo apt-get commands.  

Watching things in an terminal,  the update is happening.  It seems to me that if doing an upgrade via the net is *this* simple, this should be scripted so that command-line hackers could exec the script; then go have a cup of coffee and a long nap ;)[/QUOTE]

Apologies for replying to my own post, but my ** apt-get upgrade** gave me the following two "W" warnings.  Do I have to sweat these two missing packages?
And now what?  Reboot into 5.10/breezy?

thanks much!

[INDENT]
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/INDENT]

---

### Post by ranf on 2005-11-12
I'd simply comment out the Hoary CD in sources.list. You don't need it.

---

### Post by kline on 2005-11-12
[QUOTE=ranf]I'd simply comment out the Hoary CD in sources.list. You don't need it.[/QUOTE]

Will do.  Now that I've got 5.10--and the required stuff from source.list--should I reboot?  There are hundreds of package upgrades waiting.  Should I pull these in first, or does it make any difference?

I'm cautious because of the other users who have had lots of trouble; the last thing I want to have happen is to reboot and find thinngs broken.

thanks for your insights.

---

### Post by adwait on 2005-11-12
Now run 
```
sudo apt-get dist-upgrade
```

That will download and install all those packages and eventually restart your computer and boot you into Breezy.

---

### Post by kline on 2005-11-13
[QUOTE=adwait]Now run 
```
sudo apt-get dist-upgrade
```

That will download and install all those packages and eventually restart your computer and boot you into Breezy.[/QUOTE]

Hmm.  I ran 'apt-get dist-upgrade' and after it began downloading pakages, I went to bed.  There are dozens of errors like this::

[BLCKQUOTE]
E: Prior errors apply to /var/cache/apt/archives/python-numeric_23.8-4_all.deb
Extracting templates from packages: 94%E: Could not open file /var/cache/apt/arc hives/python-netcdf_2.4.9-2ubuntu1_i386.deb - open (2 No such file or directory)
E: Unable to determine the file size - fstat (9 Bad file descriptor)
E: Read error - read (9 Bad file descriptor)
E: Prior errors apply to /var/cache/apt/archives/python-netcdf_2.4.9-2ubuntu1_i3 86.deb[/BLOCKQUOTE]

I've got lots of diskspace.  Do I have to to a /bin/rm -rf of the *.deb files?  Try again?  <Other?>

gary

---

### Post by az on 2005-11-13
You may have a package that corrupted the dpkg database.

Try running

sudo dpkg --clear-avail

and then 

sudo apt-get -f install

---

### Post by kline on 2005-11-13
[QUOTE=azz]You may have a package that corrupted the dpkg database.

Try running

sudo dpkg --clear-avail

and then 

sudo apt-get -f install[/QUOTE]
[INDENT]
I'm using the synaptic app; it indicates that ~50 packages need to be rm'd, hundreds upgraded; more than 1100 mods total.  Should be done in 12 hours.
If the "Smart" synaptic option fails, I'll try your commands and tee the output to
/tmp.  Gotta be a way of doing this over the net...  


Seems to me that if a script fails, it would conditionally try work-arounds that you suggest.   ...[??][/INDENT]

---

### Post by kline on 2005-11-18
[QUOTE=kline]Will do.  Now that I've got 5.10--and the required stuff from source.list--should I reboot?  There are hundreds of package upgrades waiting.  Should I pull these in first, or does it make any difference?

I'm cautious because of the other users who have had lots of trouble; the last thing I want to have happen is to reboot and find thinngs broken.

thanks for your insights.[/QUOTE]
[FONT="Times New Roman"]
Well, (again, responding to my own post),  after 5 days of working on this **carefully**, I'm fully running 5.10.  Most of the time was waiting as hundreds of megs came across.  As of this morning there was no indication that I needed to download more files.  But the "term" screen from synaptic had dozens of lines of err output.  Mostly that I ran out of memory.  

I started yet-another synaptic download, but quit and decided to use apt-get .  Where are the packages stored before installation?  Are they tarballs or named *.deb?  Or something else?

For the past half hour I', trying apt-get -f install.   Over my ISDL line it looks like things should be done in two hours.   I hope firefox works this time; and everything else!  When everything is done, **if** I can finish the upgrade without trashing the install, I'll breath easy.

[/FONT]

---

### Post by ranf on 2005-11-18
[QUOTE=kline]
I started yet-another synaptic download, but quit and decided to use apt-get .  Where are the packages stored before installation?  Are they tarballs or named *.deb?  Or something else?
[/QUOTE]
They are .deb's and stored under /var/cache/apt/archives.

I prefer aptitude over synaptic. It has a menu entry to clean this cache (but maybe synaptic has that as well).

---

