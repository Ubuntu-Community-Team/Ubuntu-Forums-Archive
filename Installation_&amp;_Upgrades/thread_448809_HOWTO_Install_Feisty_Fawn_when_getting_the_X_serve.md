---
title: "HOWTO: Install Feisty Fawn when getting the X server error."
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by Ub1476 on 2007-05-19
I've seen many people, including me, have had problems installing Ubuntu 7.04, due to the problem that xorg.conf is not set up correctly. Follow this guide if Ubuntu cannot start from live cd, because you get an error message about that your graphical interface (X server) could not be started. 
[I]
(EE) No devices detected

Fatal server error:
No screens found [/I]

The bug is well known, just look at this link: [[COLOR="Red"]Linky[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853") and this one: [[COLOR="Red"]Linky[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103945/comments/1") 

You do not need internet connection when following this guide, because we will not download anything (except for fglrx drivers when Ubuntu is_ installed_) .
[I]
[COLOR="Red"]Note: This guide is based upon Ubuntu 7.04, so commands like "gedit" and "gdm" will not work with Kubuntu/Xubuntu/Edubuntu. Like, in Kubuntu "gdm" is "kde" and so on.[/COLOR][/I]

**[SIZE="3"]Let's get started:)[/SIZE]**

After booting from the live cd, choose "no" to view the X details. You'll end up in the terminal. Press enter to log in and write:

```
sudo nano /etc/X11/xorg.conf
```

In the "Monitor" section add the following lines:

```
HorizSync                36-52
VertRefresh              36-60
```

It should look like this:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	36-52
	Vertrefresh	36-60
EndSection
```

Now go to the "Screen" section. Remove all other resolution than "640x480". So it will look like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"640x480"
	EndSubSection
EndSection
```

Click F2 to save and quit. Now write:

```
sudo killall gdm
sudo gdm
```

Ubuntu should now start. Install Ubuntu. When Ubuntu is installed go to terminal and write: 

```
sudo apt-get update
sudo apt-get upgrade
```

Now go to System>Administration>Enable Restricted Drivers Manager. Check the unchecked graphic driver. Go back to the terminal and write:

```
sudo gedit /etc/X11/xorg.conf
```

Add your default resolution you removed earlier in the guide. If 1280x800 is your resolution it should look like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"    "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"    "640x480"
	EndSubSection
EndSection
```

Click on save and exit. Restart Ubuntu, and everything should be working perfect now. 

If you want to install XGL/AIXGL and Beryl follow this [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29").

For XGL: Scroll down to ..Alternate method: Using closed source FGLRX drivers from ATI.. and follow the guide from there.

Hope this helps for everyone who had this problem!:)

Ub

---

### Post by Psyk1 on 2007-05-23
Nice!

Thanks a lot. I was really struggling with this issue.
Now, lets hope i did not mess up my Vista, oh well. I did not like it anyway ;)

---

### Post by neuropsychguy on 2007-05-26
Sweet post! It saved me a ton of pain. :KS \\:D/

---

### Post by mig96 on 2007-06-12
will this work on Gutsy?  I've gotten the daily build and it doesn't start up the x server either.  YES I AM BOOTING FROM LIVE CD DIDN'T INSTALL.  My computer doesn't work with ANY ubuntu versions.  Or Kubuntu.
So what do I do?

---

### Post by Ub1476 on 2007-06-23
No clue, but worth a try, I guess.

---

### Post by iLinux on 2007-06-27
I dont understand how to get into the terminal...all I get is to rstart GDM server or somtin....it happens everytime... I think its really supposed to show the local host login screen for the terminal..This never happens on my computer

---

### Post by Ub1476 on 2007-06-28
You choose the the option "Install or start Ubuntu" right? And after the you get the error message, just choose no to view details, and get a black screen with white text (like default terminal) then simply click enter. You should be logged in as "ubuntu@ubuntu" or something, I don't really remember:p

---

### Post by ryanxdurst on 2007-07-04
I think I'm stuck on the "sudo killall gdm" part. I'm not sure where or when to do that. It just says "no process killed". What do you think I should do?

---

### Post by Ub1476 on 2007-07-08
You can try "sudo gdm" after that, since it's already dead. Or you can just retry, cause gdm should have been loaded there, but.. Anyway you can't possible screw anything, cause your on a live cd:)

---

### Post by RelativelyQuantum on 2007-12-23
When I run "sudo nano..." it builds me another document, and I can't access the information already in my xorg.conf file. I'm using Edgy, mind you; is that causing the problem?

---

### Post by RelativelyQuantum on 2007-12-27
Just wondering, would this also work with Edgy or Dapper?

---

