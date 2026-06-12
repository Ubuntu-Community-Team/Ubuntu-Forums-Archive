---
title: "Problem Installing Ubuntu on iMac G3"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by Warcrafter on 2006-08-26
I decided to install Ubuntu on my old iMac G3 because I don't use it. During the first installation it seemed that everything was going fine but then once Power Managment loaded The screen went completely black.  I left it running all night hoping that it would load the installer but the screen just stayed black.  What could be the problem and how do I fix it.

---

### Post by linear on 2006-08-26
The installer does not write the correct display settings for the iMac G3 into xorg.conf. You will need to fix manually:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt, may take a couple of tries)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome

Modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

### Post by Warcrafter on 2006-08-27
It went past power managment this time but i think it did only because i put ram in it and then afeer a proccess loaded (i forget which one) i did ctrl-option-F1 and the command screen came up i type the sudo nano /etc/x11/xorg.conf and nothing happened then a minute later i heard music coming from the computer.

---

### Post by linear on 2006-08-27
The command is case-sensitive: **sudo nano /etc/_X_11/xorg.conf**, with a capital "X".

---

### Post by Warcrafter on 2006-08-27
I realized that after I posted.  So I changed everything u told me to but when i restarted it say Stop ing Gnome    OK
Starting Gnome   Failed in red letters.  What should I do Now

---

### Post by linear on 2006-08-27
Sounds like you are working from the Dapper LiveCD.

Use this command instead to restart Gnome:

**sudo killall -HUP gdm**

---

### Post by Warcrafter on 2006-08-27
now when I do sudo nano /ext/X11/xorg.conf the big dialog comes up but no text show and it says in the top left GNU 1.3.10 and no text within the box except the stuff I type.  then when I type 
sudo killall -HDU gdm it says unknown signal and i am using a Dapper Live CD I downloaded the iso for ppc and burned it onto a disc

---

### Post by Warcrafter on 2006-08-27
sorry when I type sudo killall -HUP gdm I wait a couple seconds and then the screen goes black

---

### Post by Warcrafter on 2006-08-27
after the screen goes back a couple seconds later that sound I told u about earlier plays but it still stays black

---

### Post by linear on 2006-08-28
> **Warcrafter said:**
> now when I do sudo nano /ext/X11/xorg.conf the big dialog comes up but no text show and it says in the top left GNU 1.3.10 and no text within the box except the stuff I type.  then when I type 
sudo killall -HDU gdm it says unknown signal and i am using a Dapper Live CD I downloaded the iso for ppc and burned it onto a disc

Double-check spelling and case when you type those commands - you should see the contents of a file after entering "sudo nano /etc/X11/xorg.conf".

If you're still booting from the LiveCD (haven't installed), try again.

---

### Post by Warcrafter on 2006-08-28
Now whenever I type sudo nano /ext/X11/xorg.conf nothing comes up.  At all it just shows wat i typed and nothing happens.  I think this happened after I changed the hoizsnyc and vertisync and the DRI because nothing comes up at all and i even made another disc but still nothing.

---

### Post by Warcrafter on 2006-08-28
now I sfter I type sudo nano /etc/X11/xorg.conf nothing comes up it stays black but shows the words I typed.  I tried burning another disc with ubuntu on it but it still does the same thing

---

### Post by Warcrafter on 2006-08-28
when I do sudo killall -HUP gdm nothing happens.  what should I try now?  and will I be able to get this to work

---

### Post by Warcrafter on 2006-08-28
a minute after I typed in sudo killall -HUP gdm a blue screen came up that said "Failed to start the X server (our graphical interface).  It is likely that it is not setup correctly.  Would you like to veiw the X server output to diagnose the problem?" then it says yes or no.  I press yes a couple of times and then another box comes up that says " The X server is now disabled.  Restart GDM when it is configured correctly." wat do I do now

---

### Post by linear on 2006-08-28
It sounds as though xorg.conf has gotten messed up or deleted. You can re-create it with:

**sudo dpkg-reconfigure xserver-xorg**

You can accept defaults for most questions, but use the HorizSync and VertRefresh settings specified previously. Also disable dri.

---

### Post by Warcrafter on 2006-08-28
i got it installed with the text base installer.  Everything went sommothly until it loaded and when it was loading the installed ubuntu everything said ok except "Loading Harware Drivers".  then everything after that said ok.  When I got into the login i entered my screen name and password correct but after i entered it a long list of words came up that said bash something.  lol what do I do now?

---

### Post by Warcrafter on 2006-08-28
it says -bash: /dev/null: Permision Denied 

and it says that a bunch of times

---

### Post by Warcrafter on 2006-08-28
and all i did was try to login

---

### Post by linear on 2006-08-29
It sounds like the username/password didn't get set up correctly during the install. I don't know how to fix that. :( (But a search of the forums might turn up an answer.)

---

