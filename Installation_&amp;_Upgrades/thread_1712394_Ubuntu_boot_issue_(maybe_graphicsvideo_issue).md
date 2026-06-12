---
title: "Ubuntu boot issue (maybe graphics/video issue)"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by coly13 on 2011-03-22
Hey guys, im new to the forum but have been reading around for days.
I havent got much of a clue about Linux (used windows all my life) but want to get off the bandwagon and onto another.

I downloaded Ubuntu 10.10 and burned to a cd (twice infact).
I was already having problems when putting the disk in, my monitor would go black with an 'out of range input2:hd15 15.6Hz/25Hz'.
Anyway, i got past this by pressing F6 and selecting nomodeset. This way i got the installation box up and installed on my hdd (i have since reinstalled it many times and on 2 seperate hdds, one with only ubuntu installed, and one with it installed alongside windows xp).
However, when i install and it asks me to reboot (remove the cd and press enter) it trys to restart, i get a wee white line at the top left hand side of my screen then it flicks to the same 'out of range input2........' message.
Im pretty sure it mite be a video/graphics card issue, but ive been trying for 2 days straight and i cant seem to sort it.

Im coming to my whits end but i dont want to give up on ubuntu!!!!

also, when i put the disk in i can access ubuntu, all i do it pretend to install again but click cancel, it brings me to the ubuntu desktop and i can select away at preferences, programs, etc. But when i take the disk out it all messes up because its booting from the disk not the HDD.

Any help would be fantastic as i want to have a positive Linux experience.

---

### Post by tommcd on 2011-03-22
If the nomodeset option worked for the live CD it should work on the installed Ubuntu.
What video card do you have?
To boot with nomodeset, when the grub menu comes up, hit "e" to edit the entry. Then scroll down to the line that starts with linux. Use the arrow keys to get to the end of that line. Remove the words *quiet* and *splash* and add *nomodeset*.
Then hit *ctrl* + *x* to boot.
If this works, then add nomodeset to the *GRUB_CMDLINE_LINUX=""* line of the */etc/default/grub* file (in between the quotes). Then run ```
sudo update-grub
``` from the terminal to update your */boot/grub/grub.cfg* file.
See this for more info on editing /etc/default/grub: [https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29)

And welcome to the Ubuntu forums!

---

### Post by coly13 on 2011-03-23
Hey, first of all cheers for the help, i knew someone would come to my aid.
So i booted with nomodeset instead of quiet splash and it worked a charm, got me to the desktop in a matter of seconds.
But now for the tricky part....i have located the /etc/default/grub file, but when i open it and try to write in nomodeset between the two " "s it wont let me type, infact it wont let me type anywhere in that file, or delete, or do anything apart from highlight.
Im pretty sure that this is the last step in my "Ubuntu working perfectly" process, any ideas about why i cant edit it??

Thanks again for the help!

---

### Post by tommcd on 2011-03-23
> **coly13 said:**
> 
So i booted with nomodeset ... and it worked a charm, got me to the desktop in a matter of seconds.
So you just need to set grub2 to boot with nomodeset all the time. Just out of curiosity, what video card do you have?
> **coly13 said:**
> 
...i have located the /etc/default/grub file, but when i open it and try to write in nomodeset between the two " "s it wont let me type ... why i cant edit it??

You can not edit system files as a normal user in linux. Most distros use a root user for this; but Ubuntu uses sudo in place of a root user, which works just fine.
To edit */etc/default/grub* you must use a text editor with sudo. The easiest way to do that is to open a terminal and run:
```
gksudo gedit /etc/default/grub
```
Note: The **gk**sudo is used for graphical apps like the *gedit* text editor.
Then scroll down to the *GRUB_CMDLINE_LINUX=""* line and add *nomodeset* in between the quotes. Then save and exit the file. 
Then be sure to run: ```
sudo update-grub
``` from the terminal, so these changes will be written to your */boot/grub/grub.cfg* file.
You should be good to go with nomodeset after that.

---

### Post by coly13 on 2011-03-23
My Graphics Card is
VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (reva2)

I have it up and running 100%
Now when I startup my computer it boots perfectly.
I fiddled about for 3 days trying to solve it and with your help i basically had it done in about 10minutes.

I honestly can't thank you enough tommcd, you help was/is greatly appreciated.
Now to find and install a driver for my Tenda W54U Wireless USB Adaptor.

Thanks again.
Colin

---

### Post by tommcd on 2011-03-23
> **coly13 said:**
> My Graphics Card is
VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (reva2)

Have you tried installing the nvidia driver for your card? You could use either the *nvidia-current* or the *nvidia-173* driver.
Just go to system > administration > hardware drivers and install whatever driver it recommends. Then reboot.

---

### Post by coly13 on 2011-03-24
Yea i installed the Nvidia driver last night, i installed the 1 ubuntu recommended, and sofar everything is going smoothly.
Already loving it, glad i made the switch.
No to spend the next while getting a driver for my wireless usb adaptor, think i saw a thread here somewhere to do with it.

Thanks again for your help.

---

