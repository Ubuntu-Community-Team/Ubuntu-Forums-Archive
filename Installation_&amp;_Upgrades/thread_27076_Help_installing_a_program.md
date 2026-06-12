---
title: "Help installing a program"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by Hoeser on 2005-04-14
I am trying to install Steam Dedicated Server Software, Specifically built for linux.
I am on a AMD machine, xp 1700+. 256 pc 2100 ram, 20 gig hard drive, K7 MSI motherboard.
I have no clue how to install this program, it says im supposed to go to properties and go to 'open with' and select a program to open my program with. i am SO new to linux, and Very confused. I have the latest version of Ubuntu.. i highly appreciate help, and your patience with another noob. Thank you
-Ryan

---

### Post by az on 2005-04-14
[QUOTE=Hoeser]I am trying to install Steam Dedicated Server Software, Specifically built for linux.
I am on a AMD machine, xp 1700+. 256 pc 2100 ram, 20 gig hard drive, K7 MSI motherboard.
I have no clue how to install this program, it says im supposed to go to properties and go to 'open with' and select a program to open my program with. i am SO new to linux, and Very confused. I have the latest version of Ubuntu.. i highly appreciate help, and your patience with another noob. Thank you
-Ryan[/QUOTE]

What kind of file is it?

If it is a bin file, go into the file manager and change the properties of the file to make it executable.

PLaces - Home folder - Right-click on file  - Properties -Permissions (Read Write Execute)

Then click on the file.  Good Luck!

If it is a deb open up a console and do
sudo dpkg -i <file.deb>

If it is any other kind of file, post back here.

---

### Post by Hoeser on 2005-04-14
"the  file name "hlsupdatetool.bin" Indicates that this file is of type "unknown". the contents of this file indicate the the file is of type "executeable" 
The message goes on.... i dont know really what to do, i tried setting the Chmods like yo said, i set them to 777 but i still get that error

---

### Post by speedman on 2005-04-14
Open a term, cd to the directory that the file is in and issue this command:

sudo ./hlsupdatetool.bin


Regards,

SM

---

### Post by Hoeser on 2005-04-14
"command not found" is what it said

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=Hoeser]"command not found" is what it said[/QUOTE]

Are you sure you moved to the right directory, and made sure to do **sudo ./hlsupdatetool.bin** and not **sudo hlsupdatetool.bin**. If it helps, you can copy commands from the browser window and paste them into your terminal using the middle mouse button.

---

### Post by Hoeser on 2005-04-14
i can move a terminal to a directory?? Im so confused. sorry for all the trouble. i tried the sudo ./hlsupdatetool.bin (the bin is on my desktop) and it said "command not found"

---

### Post by speedman on 2005-04-14
cd ~/Desktop

cd stands for change directory, so the command above will change your location in the term to your desktop.  Once you are there issue the command:

sudo ./hlsupdatetool.bin


Regards,

SM

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=Hoeser]i can move a terminal to a directory?? Im so confused. sorry for all the trouble. i tried the sudo ./hlsupdatetool.bin (the bin is on my desktop) and it said "command not found"[/QUOTE]

Hmmm... when you said you were a newbie, I didn't think to assume that you'd never worked a command line before. That's no problem. 

The first thing you should do is move the .bin file from your Desktop to your home directory. Once you've done that, open your terminal again and run the command. Or, if you like, you can [read this page first for a quick tutorial on basic commands and shortcuts](http://www.unixguide.net/linux/linuxshortcuts.shtml); I remember being given a very similar cheatsheet when I took my introductory Unix course in college seven years ago. :)

---

### Post by Hoeser on 2005-04-14
YARG it still says "command not found"
edit *I have used command lines, just not in linux...lol*

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=Hoeser]YARG it still says "command not found"
edit *I have used command lines, just not in linux...lol*[/QUOTE]

Post the contents of the terminal window you're using to try to install the program, please? I'd like to see for myself what's going on.

---

### Post by Hoeser on 2005-04-14
[QUOTE]ryan@ryanubuntu:~$ sudo ./hlsupdatetool.bin
sudo: ./hlsupdatetool.bin: command not found
ryan@ryanubuntu:~$ cd ~ /Desktop
ryan@ryanubuntu:~$ sudo ./hlsupdatetool.bin
sudo: ./hlsupdatetool.bin: command not found
ryan@ryanubuntu:~$ sudo./hldsupdatetool
bash: sudo./hldsupdatetool: No such file or directory
ryan@ryanubuntu:~$ cd ~ /Desktop
ryan@ryanubuntu:~$ sudo ./hldsupdatetool.bin
sudo: ./hldsupdatetool.bin: command not found
ryan@ryanubuntu:~$ sudo ./hldsupdatetool.bin\
>
sudo: ./hldsupdatetool.bin: command not found
ryan@ryanubuntu:~$ sudo ./hldsupdatetool.bin
sudo: ./hldsupdatetool.bin: command not found
ryan@ryanubuntu:~$
ryan@ryanubuntu:~$
[/PASTE]

There u go

---

### Post by Stormy Eyes on 2005-04-14
Did you try **sudo /home/ryan/hlsupdatetool.bin**? Sudo might not handle the "./" shortcut correctly. Also, try doing **chmod +x /home/ryan/hlsupdatetool.bin** before running it. I don't trust Nautilus to handle setting file permissions properly. :)

---

### Post by Hoeser on 2005-04-14
okay, i tried everything you just said, and it still does not work
i am so lost, i dont get why it wont work, im looking at the file on my desktop (or whatever you call it in linux) and i see the file there..

---

### Post by speedman on 2005-04-14
Maybe your path is out of whack.  Post the results of these commands:

echo $PATH

And ...

which sudo

Another method that you can use in Gnome to quickly complete the path to a file follows:

Right click on the desktop and open a terminal.  If the file you wish to work with is on your desktop enter:

sudo <space>

... then drag the file on to the terminal window and release it.  This will complete the path to the file as per this example:

sudo /home/<username>/Desktop/<file_name>

You can also drag files from the Nautilus file browser into a terminal window to accomplish the same thing.

HTH


Regards,

SM

---

### Post by Stormy Eyes on 2005-04-14
Delete the file you've downloaded, and try doing the following in a new terminal window. I just did this myself, and got the Steam installer to display the license agreement:

1. wget [http://www.steampowered.com/download/hldsupdatetool.bin](http://www.steampowered.com/download/hldsupdatetool.bin)
2. chmod +x ./hldsupdatetool.bin
3. sudo ./hldsupdatetool.bin

---

### Post by Hoeser on 2005-04-14
ryan@ryanubuntu:~$ chmod +X ./hldsupdatetool.bin
chmod: cannot access `./hldsupdatetool.bin': No such file or directoryryan@ryanubuntu:~$ sudo /home/ryan/Desktop/hldsupdatetool.bin
Password:
sudo: /home/ryan/Desktop/hldsupdatetool.bin: command not found
ryan@ryanubuntu:~$  Echo $PATH
bash: Echo: command not found
ryan@ryanubuntu:~$ ECHO $PATH
bash: ECHO: command not found
ryan@ryanubuntu:~$ Which sudo
bash: Which: command not found
ryan@ryanubuntu:~$

---

### Post by speedman on 2005-04-14
Lesson number one - UNIX and Linux shells are case sensitive.  :) 

"chmod +X" is not the same thing as "chmod +x"

"Which sudo" is not the same thing as "which sudo"

"Echo $PATH" is not the same thing as "echo $PATH"

Copy the commands verbatim from previous posts to this thread and you should be in better shape.

Good luck.


Regards,

SM

---

### Post by Hoeser on 2005-04-14
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
ryan@ryanubuntu:~$ sudo /home/ryan/Desktop/hldsupdatetool.bin
Password:
sudo: /home/ryan/Desktop/hldsupdatetool.bin: command not found
ryan@ryanubuntu:~$

---

### Post by speedman on 2005-04-14
The bin file is not set executable.

I downloaded the file to provide this example:

chris@i8500:~/Desktop $ ls -al hldsupdatetool.bin
-rw-r--r--  1 chris chris 3513408 2005-04-14 23:27 hldsupdatetool.bin
chris@i8500:~/Desktop $ sudo ./hldsupdatetool.bin
sudo: ./hldsupdatetool.bin: command not found
chris@i8500:~/Desktop $ chmod +x ./hldsupdatetool.bin
chris@i8500:~/Desktop $ sudo ./hldsupdatetool.bin
<Valve license text SNIPPED>
Enter 'yes' to accept this agreement, 'no' to decline:

So, to recap - if the file is still on your Desktop:

right click on the desktop and open a terminal

cd ~/Desktop

chmod +x ./hldsupdatetool.bin

sudo ./hldsupdatetool.bin

HTH


Regards,

SM

---

### Post by Hoeser on 2005-04-14
Okay i got thart all done and i got liscence agreement
i typed ok and it extracted to desktop, i double clicked "steam" and nothing happens. all the help is highly appreciated.
-Ryan

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=Hoeser]Okay i got thart all done and i got liscence agreement
i typed ok and it extracted to desktop, i double clicked "steam" and nothing happens. all the help is highly appreciated.
-Ryan[/QUOTE]

[Read this, starting with the command **chmod +x ./steam**.](http://jap.servicez.org/steam/install.html)

---

### Post by Hoeser on 2005-04-15
LOL after all the work i downloaded the WRONG program,. and now im trying to find the right one ( i needed a dedicated server for counter strike source) LOL but thanks anyways guys, you extended my knowledge!

---

### Post by speedman on 2005-04-15
No knowledge is bad knowledge Hoeser.  Best of luck with your Linux adventures.


Regards,

SM

---

### Post by dclaridge on 2005-07-22
[QUOTE=Hoeser]YARG it still says "command not found"
edit *I have used command lines, just not in linux...lol*[/QUOTE]
 if it says 'command not found' it means you have not set your terminal to the correct directory.

i think the problem may be that a source dedicated server is usually called 'hldsupdatetool' not 'hlsupdatetool' - make sure the file 'hldsupdatetool.bin' (all lowercase) is on your desktop, then right click on the desktop, open a terminal window and do the following:

cd ~/Desktop [ENTER]
chmod a+x hldsupdatetool.bin [ENTER]
sudo ./hldsupdatetool.bin [ENTER]

you will be asked for your user password... type

password [ENTER] (replacing 'password' with whatever your password is

installer should now run

note the installer simply presents you with a licence that you must accept before it copies a .tar.gz file into the current directory

for a better guide on how to set up a STEAM server on linux - use the following guide.. note under ubuntu you should probably put 'sudu ' before all the commands they suggest

[http://server.counter-strike.net/server.php?cmd=howto&show=linux#installing](http://server.counter-strike.net/server.php?cmd=howto&show=linux#installing)

---

### Post by dclaridge on 2005-07-22
just adding to that ---

running and maintaining a counter-strike server on linux requirers a through understanding of the way linux, and servers on linux, generally are operated. I suggest you learn the ropes of getting around your new OS before you set out to become a |337 S3rV3R 4DMin$

understanding of the way file permissions, and just generally using the shell effictively (that spelling error before never would have been encountered if you pressed 'TAB') -- is vital. Nobody will play on a CS:S server that laggs like hell because the admin didn't know how to set it up properly.

---

