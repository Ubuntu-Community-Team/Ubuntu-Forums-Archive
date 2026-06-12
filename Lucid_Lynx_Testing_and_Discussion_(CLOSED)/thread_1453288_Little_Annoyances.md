---
title: "Little Annoyances"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by HolidayQueen on 2010-04-13
After reformatting 3 of my computers and installing from scratch... i really must point out how annoying it is to repeat the same procedure 3 times lol

Install chromium, deluge, emesene
Remove firefox, transmission, empathy, gwibber

Does the alternate install cd help avoid this tediousness, if not, could they possibly add a step in the installation where the user can choose his preferred applications?

---

### Post by sonicb00m on 2010-04-13
> **HolidayQueen said:**
> After reformatting 3 of my computers and installing from scratch... i really must point out how annoying it is to repeat the same procedure 3 times lol

Install chromium, deluge, emesene
Remove firefox, transmission, empathy, gwibber

Does the alternate install cd help avoid this tediousness, if not, could they possibly add a step in the installation where the user can choose his preferred applications?

Why don't you create a bash script to do it for you? That way it's not as irritating :lolflag:

---

### Post by teh603 on 2010-04-13
Not all of us know how to make a bash script, or what one is. Are they like the old .bat files from DOS?

---

### Post by knarf on 2010-04-13
It is the other way around: MS-DOS batch files were and Windows .cmd files are weak derivatives of Bourne/Korn shell scripts. Bash is the 'Bourne Again SHell' and supports a superset of the Bourne shell's instructions.

To learn more about shell scripting I'd suggest having a look at the contents of your /usr/bin directory using the file command. Open a terminal first, then type the following command followed by the 'Enter' key:

```
file /usr/bin/*|grep shell|less
```The 'file' command with the given parameter shows the content type of all files in /usr/bin. The '|' or 'pipe' symbol feeds the output of the left-hand command to the input for the right-hand command. The 'grep' command shows all lines containing the letter sequence 'shell'. The pipe symbol feeds the output of the grep command (being all files of some 'shell' type) to the 'less' command. Less is a 'pager', a program which shows its input in page-sized chunks. Press the space bar or the 'Page Down' (or PgDn) key to see the next file.

All the files you see named are shell scripts. Have a look at them using the 'less' command to see what is going on inside them, eg.:
```
 less /usr/bin/apport-bug
```

You can learn more about bash by reading the man page (short for 'manual page'):
```
man bash
```This shows the contents of the bash manual page in the terminal.

---

### Post by Seren on 2010-04-13
A blog explaining a trick to reinstall a list of package from a list, for example your list of all currently installed packaged.

It is very easy, it is only a handful of cmd line.

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

---

### Post by meborc on 2010-04-13
you will spend more time on making this short cut rather than speeding your installation process

what is so bad about: ```
sudo apt-get remove package1 package2 package3 && sudo apt-get install package4 package5 package6
```

anyway, once you tinker and tune your ubuntu to your liking you can always create a iso from your existing system... now if i only find the link to that info

edit: there is some old info here [https://help.ubuntu.com/community/LiveCDCustomization?action=show&redirect=LiveCDCustomization%2F6.06](https://help.ubuntu.com/community/LiveCDCustomization?action=show&redirect=LiveCDCustomization%2F6.06) not sure if it is still valid though

---

### Post by appultaart on 2010-04-13
> **meborc said:**
> 
anyway, once you tinker and tune your ubuntu to your liking you can always create a iso from your existing system... now if i only find the link to that info


You might want to try Remastersys. It worked very nice for me on Karmic (have not tested yet on Lucid): [http://www.geekconnection.org/remastersys/remastersystool.html]("http://www.geekconnection.org/remastersys/remastersystool.html"). 

Basically, you install your Ubuntu, add and remove all the packages that you fancy, fiddle around to get your WiFi and video card working, change your Desktop background and get your Compiz settings etc., then run Remastersys. This program creates an .iso for you that contains your current system.

---

### Post by meborc on 2010-04-13
> **appultaart said:**
> You might want to try Remastersys. It worked very nice for me on Karmic (have not tested yet on Lucid): [http://www.geekconnection.org/remastersys/remastersystool.html]("http://www.geekconnection.org/remastersys/remastersystool.html"). 

Basically, you install your Ubuntu, add and remove all the packages that you fancy, fiddle around to get your WiFi and video card working, change your Desktop background and get your Compiz settings etc., then run Remastersys. This program creates an .iso for you that contains your current system.

yeah, that is the thing I forgot :) thanks

---

### Post by QLee on 2010-04-13
[QUOTE=HolidayQueen]After reformatting 3 of my computers and installing from scratch... i really must point out how annoying it is to repeat the same procedure 3 times lol[/QUOTE]


Wow, you have 3 machines to devote to testing beta software, I envy that.


[QUOTE=HolidayQueen]Does the alternate install cd help avoid this tediousness, if not, could they possibly add a step in the installation where the user can choose his preferred applications?[/QUOTE]

There are strategies for unattended install which can be carried out by system admins who have lots of boxes to do but sys admins know how to do this.

There is the dpkg --set-selections that has already been mentioned, as well as scripting the changes you want.

If it were me doing it, I would probably semi-clone (not the same UUID) the  partitions.

If you want something in the installer (similar to say, Debian) it would probably be a good idea to see if there are any wishlist bugs asking for what you want and, if not, perhaps file one yourself.

---

### Post by thomasyen on 2010-04-13
If you're planning to do something similar in the future, you might want to check out [Kickstart]("http://www.linux-mag.com/id/6747/"). Basically this will generate a list of settings (including what packages to install) and save it to a boot floppy. After booting from this floppy, the computers will automatically download the Ubuntu images over a network and install/uninstall the indicated packages.

---

### Post by lovinglinux on 2010-04-13
> **lovinglinux said:**
> To replicate your packages selection on another machine (or restore it if re-installing), you can type 

dpkg --get-selections > ~/my-packages 

move the file "my-packages" to the other machine, and there type 

sudo dpkg --set-selections < my-packages && apt-get dselect-upgrade

[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Upgrade Difficulties: I don't appreciate[/color]]("http://ubuntuforums.org/showpost.php?p=6115023")

[*]**Tags:** [[color="DarkSlateGray"]Upgrade Difficulties I dont appreciate[/color]]("http://www.google.com/search?q=Upgrade+Difficulties+I+dont+appreciate+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by cheapsaket on 2010-04-13
Try the utility by Andrei, it comes with a GUI and allows you to customize a new install of Lucid: [http://www.webupd8.org/2010/04/ubuntu-1004-first-time-use-script-02.html](http://www.webupd8.org/2010/04/ubuntu-1004-first-time-use-script-02.html)

---

### Post by HolidayQueen on 2010-04-13
I used to have a bash script actually, but they stopped working after a while because some ppa's tend to change or disappear. 

And to the one who said i had three computers w/ which to do beta testing... don't worry, thats not the case :P i upgraded on one of them, and found that the whole system ran on less ram, then i decided to do a fresh install on all 3, and i reclaimed half a hard drive on one of them by disposing of windows (it used to have awful usb tranfer speeds on that tower in ubuntu)

---

### Post by QLee on 2010-04-13
[QUOTE=HolidayQueen]
And to the one who said i had three computers w/ which to do beta testing... don't worry, thats not the case :P i upgraded on one of them, and found that the whole system ran on less ram, then i decided to do a fresh install on all 3, and i reclaimed half a hard drive on one of them by disposing of windows (it used to have awful usb tranfer speeds on that tower in ubuntu)[/QUOTE]

Well, you can chose to do whatever you want, HolidayQueen.

But I hope people who chose to use this beta will remember the warning from the top of this sub-forum.

**"Lucid Lynx Testing and Discussion**
 **Ubuntu Lucid Lynx is in development, use only for testing purposes**!!!" 

Some people have become mired in the volatility and occasional bug in this unreleased software. Glad you are experienced and knowledegable enough to solve any issuses that occur.

---

### Post by HolidayQueen on 2010-04-13
I usually resist installing alpha releases for obvious reasons.

But over the last fiteen years ive gotten used to beta's. The inconveniences seem to be minor. And to be honest, anyone intelligent enough to operate the calculator program would know to google whatever problems they encounter, im rarely the first to experience any such problems.

Though its worth noting that screensaver is broken.
and the latest round of updates also broke apache, something about a missing file (req_timeout), i had to comment it out in some config file to get apache started.

---

