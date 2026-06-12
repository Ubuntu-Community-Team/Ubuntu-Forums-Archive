---
title: "ubuntu 8.10 totally wrong, I need help!"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by downloadfreak on 2008-10-04
hello,

I have just upgreadet my ubuntu 8.04 to 8.10. It went totally wrong!! It said something about the graphics so now I'M In low graphics mode. The internet connection doesn't work anymore. What can I do? Can I downgrade to ubuntu 8.04?
I hope someone can help me

downloadfreak

---

### Post by L Campbell on 2008-10-04
> **downloadfreak said:**
> hello,

I have just upgreadet my ubuntu 8.04 to 8.10. It went totally wrong!! It said something about the graphics so now I'M In low graphics mode. The internet connection doesn't work anymore. What can I do? Can I downgrade to ubuntu 8.04?
I hope someone can help me

downloadfreak

Do you have a Live CD from which you originally installed 8.04?

---

### Post by downloadfreak on 2008-10-04
No it was just downloaded and installed

---

### Post by iponeverything on 2008-10-04
at the prompt type:

nm-applet&

After that your network connection should start working again.

as for your graphics, after your network is up -- upload 

/var/log/Xorg.0.log

---

### Post by downloadfreak on 2008-10-04
> **iponeverything said:**
> at the prompt type:

nm-applet&

After that your network connection should start working again.

as for your graphics, after your network is up -- upload 

/var/log/Xorg.0.log

Thanks the internet is working again!! but still the graphics part not... are there other suggestions?

---

### Post by iponeverything on 2008-10-04
upload /var/log/Xorg.0.log

---

### Post by overdrank on 2008-10-04
> **downloadfreak said:**
> Thanks the internet is working again!! but still the graphics part not... are there other suggestions?

Hi and if you upgraded then you will more than likely have to reinstall your drivers for the graphics card. What is the model of the graphics card?


Moved :)

---

### Post by Hairy_Palms on 2008-10-04
what graphics card do you have?
if you installed any restricted drivers you may need to reload the driver module, or install the new nvidia-glx-173 module if your on an nvidia card


P.S. also, ya really shudnt be using 8.10 yet unless your a tester, its still in beta.

---

### Post by downloadfreak on 2008-10-04
When I type in terminal upload /var/log/Xorg.0.log  then it says "no such file or directory"

I have no Idea what my graphics card is. It's a toshiba laptop, some years old

---

### Post by iponeverything on 2008-10-04
> **Hairy_Palms said:**
> 
P.S. also, ya really shudnt be using 8.10 yet unless your a tester, its still in beta.

No going back now!  I do disagree though -- testers or anyone that has a sense of adventure should run it..

---

### Post by iponeverything on 2008-10-04
When you reply to this post scroll down to the "Additional Options" section
and select "Manage Attachments"

---

### Post by Gina on 2008-10-04
> **iponeverything said:**
> No going back now!  I do disagree though -- testers or anyone that has a sense of adventure should run it..Just as long as you don't rely on it working - there are still showstopper bugs with some hardware.

---

### Post by Hairy_Palms on 2008-10-04
> No going back now! I do disagree though -- testers or anyone that has a sense of adventure should run it..
as long as their skill level scales to any problems that occur with their sense of adventure, the OP does seem fairly new.

---

### Post by iponeverything on 2008-10-04
> **Gina said:**
> Just as long as you don't rely on it working - there are still showstopper bugs with some hardware.

I will append to "testers or anyone that has a sense of adventure" and does not mind reinstalling from scratch because there system is not bootable ;)

---

### Post by downloadfreak on 2008-10-04
well maybe a bit stupid of me but I tought it would work and all the basic functions would just work...

---

### Post by Canis familiaris on 2008-10-04
> **downloadfreak said:**
> When I type in terminal upload /var/log/Xorg.0.log  then it says "no such file or directory"

I have no Idea what my graphics card is. It's a toshiba laptop, some years old

Could you post the output of?
```
lspci | grep VGA
```

---

### Post by iponeverything on 2008-10-04
> **downloadfreak said:**
> well maybe a bit stupid of me but I tought it would work and all the basic functions would just work...

look -- if you never try these things, you never learn. I am all for messing things up now and again! It keeps life interesting.

I have made way more than my fair share mistakes and only ones regret are the ones where I hurt someone.

---

### Post by downloadfreak on 2008-10-04
> **Anurag_panda said:**
> Could you post the output of?
```
lspci | grep VGA
```

This is the output:
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)

To Iponeverything: That's treu.

---

### Post by Canis familiaris on 2008-10-04
> **downloadfreak said:**
> This is the output:
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)

To Iponeverything: That's treu.
My Apologies. I don't know much about Intel Graphics. 
However you may try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This may or may not work. Wait for a more experienced user to throw light on the issue.

---

### Post by iponeverything on 2008-10-04
At the prompt type:

sudo apt-get install xserver-xorg-video-intel

then:

sudo pkg-reconfigure xserver-xorg

---

### Post by Mr Fredrick on 2008-10-04
The output from *nm-applet* for me is

```
** (nm-applet:7649): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7649): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

Regards,

Mr Fred.

---

### Post by downloadfreak on 2008-10-04
> **Anurag_panda said:**
> My Apologies. I don't know much about Intel Graphics. 
However you may try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This may or may not work. Wait for a more experienced user to throw light on the issue.

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081004130832

---

### Post by downloadfreak on 2008-10-04
> **iponeverything said:**
> At the prompt type:

sudo apt-get install xserver-xorg-video-intel

then:

sudo pkg-reconfigure xserver-xorg

First one does:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libqt4-opengl librdf0 kdelibs5 phonon
  libqt4-qt3support librasqal0 libsoprano4 redland-utils kdelibs5-data
  phonon-backend-gstreamer libstreamanalyzer0 libphonon4 kdelibs-bin libpq5
  libstreams0 libraptor1 soprano-daemon raptor-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Second says command not found

---

### Post by iponeverything on 2008-10-04
> **iponeverything said:**
> At the prompt type:

sudo apt-get install xserver-xorg-video-intel

then:

sudo pkg-reconfigure xserver-xorg

If that does not fix it try this as short term fix:

cd /etc/X11
nano /etc/Xorg.cong

And change the line that says:

Driver          "intel"

to

Driver          "vesa"

This is not a long term fix, but you can get back to hi-res while you figure out what is going with the intel driver.

---

### Post by iponeverything on 2008-10-04
sorry about the that.. should have been

dpkg-reconfigure !

---

### Post by downloadfreak on 2008-10-04
> **iponeverything said:**
> sorry about the that.. should have been

dpkg-reconfigure !

I had it without the "!" and it gave:
/usr/sbin/dpkg-reconfigure must be run as root

---

### Post by iponeverything on 2008-10-04
:) oh my.

sudo dpkg-reconfigure xserver-xorg

---

### Post by downloadfreak on 2008-10-04
> **iponeverything said:**
> :) oh my.

sudo dpkg-reconfigure xserver-xorg

It says:

 Rather than communicating directly with the video hardware, the X server  &#9474; 
 &#9474; may be configured to perform some operations, such as video mode          &#9474; 
 &#9474; switching, via the kernel's framebuffer driver.                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; In theory, either approach should work, but in practice, sometimes one    &#9474; 
 &#9474; does and the other does not.  Enabling this option is the safe bet, but   &#9474; 
 &#9474; feel free to turn it off if it appears to cause problems.                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Use kernel framebuffer device interface?

---

### Post by iponeverything on 2008-10-04
I think were getting somewhere!

Attach the log file /var/log/Xorg.0.log to your next post.

---

### Post by downloadfreak on 2008-10-04
both yes and no are not clickable maybe I should do the codes again in correct order...

---

### Post by iponeverything on 2008-10-04
> **Mr Fredrick said:**
> The output from *nm-applet* for me is

```
** (nm-applet:7649): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7649): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

Regards,

Mr Fred.

I lost you in the shuffle, where is your thread?

---

### Post by iponeverything on 2008-10-04
> **downloadfreak said:**
> both yes and no are not clickable maybe I should do the codes again in correct order...

You can do a <CTL><ALT><BKSP>  after you do dpkg-reconfigure'ing to see if it took.

---

### Post by downloadfreak on 2008-10-04
> **iponeverything said:**
> You can do a <CTL><ALT><BKSP>  after you do dpkg-reconfigure'ing to see if it took.

It does still look the same

---

### Post by Hairy_Palms on 2008-10-04
if i understand you correctly when you run sudo dpkg-reconfigure xserver-xorg you cant click anything, you must use the keyboard.

---

### Post by downloadfreak on 2008-10-04
> **Hairy_Palms said:**
> if i understand you correctly when you run sudo dpkg-reconfigure xserver-xorg you cant click anything, you must use the keyboard.

Ow... smart me. Thanks, but I have to click yes right? and is it with y for yes and n for no?

---

### Post by iponeverything on 2008-10-04
another possible option:

[http://ubuntuforums.org/showthread.php?t=937765](http://ubuntuforums.org/showthread.php?t=937765)

---

### Post by downloadfreak on 2008-10-04
Nothing is working... Does anybody still have a suggestion?

---

### Post by cariboo on 2008-10-04
You can not run:

```
sudo dpkg-reconfigure xserver-org
```

on your desktop, you have to run from a terminal with gdm preferably stopped. Press Ctrl-Alt-F1 to get into a console, theen type:

```
sudo /etc/init.d/gdm stop
```

Now run:

```
sudo dpkg-reconfigure xserver-org
```

After the above command has finished type

```
sudo /etc/init.d/gdm start
```

If the above seems a little to complicated for you, you could also boot into recovery mode and try xfix from the menu that appears after the os has loaded.

With the above commands, don't just run them blindly, if you are a newbie, just copying and pasting the commands in a terminal are not going to help you learn anything. If you don't understand something,copy the whole command and then paste it into a google search page and read the results you get.

Rmemeber Google is your friend, if you don't understand what you are doing look it up using google.

Jim

---

### Post by rbmorse on 2008-10-04
> **downloadfreak said:**
> Ow... smart me. Thanks, but I have to click yes right? and is it with y for yes and n for no?

THe <tab> key will move between fields  on a page.  The <spacebar> selects/deselects. The <enter> key....ah....enters/advances to the next page.

---

