---
title: "uBuntu Minimal Install Package"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by Woodzrul on 2010-08-24
Hello
 
I have currently got uBuntu 10.04 minimal installed on a desktop PC.
 
I am wanting to install VDIView onto this PC. [http://code.google.com/p/vmware-view-open-client/downloads/list](http://code.google.com/p/vmware-view-open-client/downloads/list)
 
Can I do this? If so, how?
 
Apologies if this is a noob question. I'm new to the world of Linux.
 
Thanks in advance.

---

### Post by terdon on 2010-08-24
Hi, first of all never apologize for a noob question, thats what this forum is for! :)

Now, the easiest way to install software under Ubuntu is to use a .deb package. This is the equivalent of the setup.exe programs in windows.

Do you know if you are running a 32 or 64 bit system?
If not, open a terminal (Accessories=>terminal) and type this command:
```
uname -m
```

That will print out your system's architecture. If the output is "x86_64" you are running a 64bit system if it is something like "i686" you are running a 32 bit one. So, go to the link you posted and download either the 64-bit or the 32-bit deb. You then double click the file and install.

Good luck

---

### Post by Woodzrul on 2010-08-24
Hi
 
Appreciate the quick response.
 
As I've installed uBuntu minimal it is all command line based. How would I go about installing the deb package and then launching?
 
Is this possible?

---

### Post by terdon on 2010-08-24
Well, assuming you want the 32bit version, from the command line do: ```
wget http://vmware-view-open-client.googlecode.com/files/VMware-view-open-client_4.5.0-271013_i386.deb 
```

This will download the package, now do ```
sudo dpkg -i  VMware-view-open-client_4.5.0-271013_i386.deb
```

This will install the package.

---

### Post by Woodzrul on 2010-08-24
Ok, the download worked a treat. GOOD MAN!!
 
I then ran the second command and it appeared to do something. But then I got the below errors back.
 
dependancy problems - leaving unconfigured
errors were encountered while processing
 
I'm assuming that it hasn't installed.
 
Is there anyway I can check by browsing to the install dir?

---

### Post by Woodzrul on 2010-08-24
I can also confirm I did install the 32 bit version.
 
Sorry for missing that out.

---

### Post by Woodzrul on 2010-08-24
Just looked through the logs.
 
It also says;
 
Package rdesktop is not installed
Package libgtk 2.0-0 is not installed
 
Could be why it failed???

---

### Post by terdon on 2010-08-24
Yup, thats exactly why it failed. You need to install missing packages. Specifically, rdesktop and  libgtk 2.0-0.

OK, try rhis:```
sudo apt-get install  libgtk 2.0-0 rdesktop
```

Then try the dpkg -i command again.

---

### Post by Woodzrul on 2010-08-24
Did the above but it said alot of dependencies were required.
 
So I ran 'apt-get -f install' without any install packages like it said. It said the account I'm logged in as doesn't have permission, so wondering if I have to used ROOT. Only problem is, during the install I wasn't prompted for a ROOT password.
 
Is there a default pw?
 
If not, I'll re-install uBuntu LTS again.

---

### Post by terdon on 2010-08-24
The command sudo gives you root privileges. So, just run:```
sudo apt-get -f install
```

---

### Post by Woodzrul on 2010-08-24
Forgot to include sudo. Lol!
 
Will be back in a minute with my results.

---

### Post by Woodzrul on 2010-08-24
Ok, VMware VDI installed without any erros this time.
 
Last message displayed was
 
Processing triggers for man-db.
 
Has this installed? Where would I browse to, to execute the application?

---

### Post by terdon on 2010-08-24
Whohoo! It worked :)

Processing triggers for man-db just means it is installing the manuals (if any) associated with the packages you just installed. 

By the way, the man command is extremely useful. just try man <program name> to see the manual of a program. eg```
man dpkg
```

---

### Post by Woodzrul on 2010-08-24
That's handy, cheers. Though just ran man against the name of the package and it said there were no manuals. :-(
 
So how do I go about launching my newly installed package?

---

### Post by terdon on 2010-08-24
Maybe the package you installed has no manuals. The manual database (man-db) is "processed" every time you install something irrespective of whether it has a man page or not.

Anyway, the man command works on program not package names. So, try 
```
 man VMware-view-open-client
```

If it has a manual that should bring it up.

---

### Post by Woodzrul on 2010-08-24
Came back saying;
 
No manual entry for VMware-view-open-client.
 
Let me have a look on the website. Unless you can think of anything else?

---

### Post by terdon on 2010-08-24
Well there is always the info command. But chances are that VMware-view-open-client has no man page. Didn't think it would I just wanted to let you know that they exist :)

---

### Post by Woodzrul on 2010-08-24
Fair enough.
 
Curious, but when installing applications, does it goto a default folder? Like C:\Program Files in Windows.
 
Am thinking if I can find the VMware folder, maybe I can launch it that way?

---

### Post by terdon on 2010-08-24
Oh, you want to launch? Sorry, just type the name and hit enter:```
VMware-view-open-client
```

Generally, in linux, commands are called by name. So, if you have a program installed called foo, just type foo and hit enter to run it.

If you are unsure of the name just type in the first few letters and hit tab TWICE. That will give you a list of all possible completions. So, for your VMware client, try typing V and then TAB twice.

And programs are generally installed in the /usr/ directory. You can find the executables under /usr/bin.

---

### Post by Woodzrul on 2010-08-24
No worries. I really do appreciate your help as this is all new to me.
 
I typed in V tab tab and it came back with vmware-view. So I typed vmware-view and got an error of
 
Gtk: cannot open display.
 
Guessing this application requires a GUI????

---

### Post by terdon on 2010-08-24
You are very welcome :)

And yes, it does sound like you need a GUI. As far as I know vmware is a graphical virtual machine emulator. 

Are you sure it is what you need? A couple of things, what are you trying to do? Why do you want vmware?

And why do you have the minimal ubuntu version installed? Your life would be much simpler with a normal install.

---

### Post by Woodzrul on 2010-08-24
Basically VMware View is part of VDI. It allows you to connect to a virtual desktop.
 
I can confirm the normal uBuntu works, but it comes with all the built in software. I was looking for a solution whereby the physical PC boots up quickly, has no software on it apart from the VDI View client.

---

### Post by Woodzrul on 2010-08-24
Just thought.
 
Can I install normal uBuntu without any applications? Of course I would want to turn off the start bar.
 
At the end of the day I just want the VDI View icon on the desktop, and nothing else!!

---

### Post by terdon on 2010-08-24
OK, you could try installing the xserver package, with no window manager. 
```
sudo apt-get install xserver-xorg
```

Once installed, you should have a command called startx which will give you a minimal graphical interface. From there you should be able to launch VDI View.

In fact, by editing some configuration files you should be able to set it up so that once you log in, VDI View, and nothing else, is launched automatically. Let me know if you want to try this and I'll walk you through it.

BTW, I assume you do not want a full install because of disk space or old hardware. If you CAN run a full ubuntu and just want your users to see only VDI View when they log in, there are easier ways. 

For example, you could install a minimal window manager such as WMaker or fluxbox and set it up so that the only thing visible after a user logs in is an icon for VDI View.

---

### Post by Woodzrul on 2010-08-24
I ran 'sudo apt-get install xserver-xorg' and then tried executing 'startx'. But then it told me I need to run 'sudo apt-get install xinit' (Something along those lines). Once completed I ran 'startx' and got a white screen, and then the computer crashed. :-(
 
What is WMaker & Fluxbox? Are these seperate OS's or do they run on uBuntu minimal? Can this then launch VDI View?
 
Basically, what I want is something similar to the below
 
Install uBuntu 10.04 (Full) Still having a quick boot
Remove all programs, or have a locked down desktop
Have a generic account which auto logs in
No Start-Menu, no access what so ever, apart from the Shutdown/Reboot icon
Automatically launch VDI View
 
I'm open to ideas, but I like the idea of having a minimal OS as there is no un-wanted applications in the first place!!!

---

### Post by terdon on 2010-08-24
Right, what do you mean the computer crashed? Symptoms?

WMaker and Fluxbox are window managers. WMs are separate programs that run on the X-server. Under Unix/linux the graphical interface is managed by the xserver, thats the white screen you saw. By editing /usr/bin/startx you should be able to change its behaviour.
The window manager runs on top of the xserver to give you pretty displays and windows. The most common WMs are KDE and Gnome. 


Its been a while since I used these programs so I don't really remember but if you look around for old threads with the keywords xinit, xinitrc or startx you should get some pointers. The crash may be because you have no window manager installed and startx tries to load one. Have a look at /usr/bin/startx.

Anyway, I think the easiest would be to install WMaker:```
sudo apt-get install wmaker wmakerconf
```

That should also install the graphical login manager gdm. After restarting you'll get a graphical login screen. Log in and that should take you to your WMaker desktop. This is pretty minimal, with no menu (you can get some menu options by right clicking on the desktop).

With a bit of work, you can set this up the way you want.

---

### Post by Woodzrul on 2010-08-25
Good morning.
 
Well, I've had alot of success thanks to you. My boss was very pleased.
 
Here's the steps which I've done;
 
1/ Installed uBuntu 10.04 32Bit minimal
2/ Executed wget [http://wmware-view](http://wmware-view)........ blah blah blah
3/ Executed sudo apt-get -f install
4/ Executed sudo apt-get install libgtk2.0-0 rdesktop
5/ Executed sudo dpkg -i WMware-view-open-client.deb
6/ Executed apt-get install xserver-xorg
7/ Executed apt-get install wmaker wmakerconf
8/ Reboot
9/ Launch 'startx'
10/ Right clicked the desktop and chose run
11/ Typed in vmware-view - JOB DONE!!
 
So, my next questions are;
 
1/ How do I make it so uBuntu automatically logs in?
2/ Launches 'startx' automatically?
3/ Launches VMware-view automatically?
 
I did notice that when I right clicked on the desktop when in startx that Mozilla Firefox was in the list. I did click it but nothing happened, which is good, but just wondered why it was showing.
 
Seriously, I really do appreciate your help, and if you know the answers to the above then that would be grand.
 
Cheers.

---

### Post by terdon on 2010-08-25
Hi, glad its working!

OK, lets try the following (adapted  from [http://blogs.koolwal.net/2009/03/15/howto-autologin-into-your-linux-system-without-xdm-gdm-kdm-etc/](http://blogs.koolwal.net/2009/03/15/howto-autologin-into-your-linux-system-without-xdm-gdm-kdm-etc/))
```

sudo apt-get remove gdm
sudo gedit  /etc/rc.local

```

The first line will remove the graphical login. The secons opens a file for editing. Paste this into the file you just opened:```

su - <username> -c startx 
su - <username> -c VMware-view
```

Now you should log in automatically. The next step is to edit the WMaker menu and remove the options you dont like. Open a terminal (right click -> run -> xterm) and run wmakerconf.

---

### Post by Woodzrul on 2010-08-25
I get an error of
 
'Glk WARNING: Cannot open display' when attempting to execute 'sudo gedit /etc/rc.local'.
 
Can I use NANO instead on rc.local?

---

### Post by terdon on 2010-08-25
Sorry, my bad, yes you can use any editor. I forgot you had no X server running.

---

### Post by Woodzrul on 2010-08-25
No worries.
 
Ok, it logged in automatically and launched startx, but VMware-view didn't launch :-(
 
Any ideas??

---

### Post by terdon on 2010-08-25
Yeah, I was afraid that might not work. Ok, open /etc/rc.local and delete the line with vmware. Then open the file ~/.xinitrc (~/ means the user's home directory) and paste this line into it:
```

VMware-view &

```
Save the file then make it executable:```
chmod a+x ~/.xinitrc
```

Log out and log back in.

---

### Post by terdon on 2010-08-26
I take it that worked then?

---

### Post by Woodzrul on 2010-08-31
Apologies for the late reply. Work has been manic and I haven't had a chance to properly test.
 
Hoping I'll get a few minutes this afternoon.

---

### Post by Woodzrul on 2010-08-31
Hello
 
Ok so I ran sudo nano ~/.xinitrc and added 'VMware-view &'.
 
I then ran sudo chmod a+x ~/.xinitrc.
 
Rebooted, and it no longer boots up wmaker automatically. Removed the 'VMware-view &' line, rebooted and still wmaker didn't automaitcally start.
 
What's the reverse to chmod a+x ~/.xinitrc? Assuming this is stopping wmaker from launching??
 
Thanks.

---

### Post by terdon on 2010-09-02
Right, the problem is one of permissions. You created the ~/.xinitrc using sudo. This creates a file owned by the superuser (root). ~/.xinitrc should be owned by the user in whose home directory it is.
First delete the file:```
 sudo rm ~/.xinitrc
```

Now create a new one with the right permissions:
```
echo "VMware-view &" > ~/.xinitrc
chmod a+x ~/.xinitrc

```

The echo command simply echoes what you tell it to (try typing echo "hello world" to see what I mean. The ">" redirects the output of a command into, in this case, a file. It is just a faster way of creating a file then using a text editor. Of course, you can always use a text editor if you so desire.

Now log out, log back in. It should work.

---

