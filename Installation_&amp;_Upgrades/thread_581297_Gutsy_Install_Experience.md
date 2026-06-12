---
title: "Gutsy Install Experience"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by leetcharmer on 2007-10-19
I spent yesterday insalling Gutsy over Feisty.  I didn't do an upgrade because I wanted a mint state update.  What I mean by this is, when going from Edgy->Feisty, any changes I made to the taskbar stayed rather than updated to the new way Feisty's was set up.  I wanted Gutsy's new default state.

LiveCD ran smooth, reformat/install was just fine, but after the install, the problems start.

[LIST=1]
[*]Black screen during bootup (no usplash)
[*]Takes much longer to boot than Feisty
[*]Can't configure touchpad
[/LIST]

Things I enjoyed so far:
[LIST]
[*]Restricted Manager: Broadcom Wireless Setup
[*]Automatic Folder Setup in /home
[/LIST]

I don't know if this is the same with anyone else, but I ran into problems when the computer wasn't plugged into the internet while installing, these problems even effected usage after Gutsy installation.  I reinstalled while it was plugged in and regular usage went smoother.

Question:
Does anyone know if I enable SHMConfig in 'x.org' -- if it'll undo my options when using the "Screen and Graphics" configurations?

I need it enabled to configure my touchpad.

**Help or suggestions are welcomed to any of my issues :D!**

---

### Post by davidshere on 2007-10-19
I also have no bootsplash.

---

### Post by leetcharmer on 2007-10-19
Also, does anyone know how to disable switching Workspaces just by scrolling on the desktop?  That gets really annoying with a touchpad.  Can I just scroll on the workspaces down in the bottom right corner rather than scrolling on the desktop?

---

### Post by fcumok on 2007-10-19
To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

---

### Post by leetcharmer on 2007-10-19
Thank you fcumok,

That fixed two issues: The bootsplash and the bootup speed, thank you very much!

All that needs to be fixed left is the Touchpad configuration stuff.

---

### Post by airencracken on 2007-10-19
> **davidshere said:**
> I also have no bootsplash.

Same here.

---

### Post by leetcharmer on 2007-10-19
To fix the touchpad, I went to the terminal :D!

> simbala@gerbert:~$ sudo vim /etc/X11/xorg.conf

I looked for this section:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection
```

and added this line right before EndSection

```
        Option          "SHMConfig"             "1"
```

Now it looks like:


```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"             "1"
EndSection
```

> Type ----> :wq <---- to save
Then I went to Synaptic Package Manager and installed gsynaptics.
After the install, I went to System>Preferences>Touchpad

:D:D:D now I can configure easily to my heart's content!

---

### Post by AlanR8 on 2007-10-19
I did a clean install of the RC client on this Sony laptop and there were no problems.

My next task was to re-format the wife's Dell Dimension 9100 core duo and re-install XP. I took the opportunity to create a dual boot with Gutsy (RC) so I can wean her away from Uncle Bill!

The XP installation was a NIGHTMARE! Talk about XP and drivers? I could not believe that the recovery disks did not pick up the network card, video, sound and one or two other system drivers. I spent over two hours chasing down the drivers.

On the other hand, creating the dual boot and installing Gutsy took about 30 minutes in total! :) EVERYTHING was detected, including the PCI Express ATI graphics card, installed the restricted driver and all was well. The only thing I had an issue with was getting the 5:1 sound card pumping out of all the speakers. Seems to be OK now but I need to spend a bit more time looking at that.

---

### Post by alfredska on 2007-10-19
> **fcumok said:**
> To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

Thanks fcumok, my boot-splash appears now and the boot process is much quicker.
~Matt

---

### Post by EowynCarter on 2007-10-19
All went fine for me.
gusty start faster than feisty did :), i can acctually write on my ntfs partitions :)
no more install ati driver requiered to install kubuntu.

did install while disconected, didn't notice antthing weird, save for it deactivating the "online" packages source.

---

### Post by silent911 on 2007-10-19
> **fcumok said:**
> To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

I tried to do so... and for point 3 I wrote:
update-initramfs -u -k 2.26.22-14-generic
and I had this answer

Cannot find /lib/modules/2.26.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.26.22-14-generic

---

### Post by gjtoth on 2007-10-19
I've been in on the beta of Gutsy from almost day one -- through all the tribes -- through all the bugs and bug-fixes.  In the end, after the final updates, I think on the 17th, my system worked nicely.  Solid.  But, like I did with my upgrade to Feisty, I downloaded the final RC on the 18th and did a fresh install.  Seems to clear things up and make a nice "Spring Cleaning" (even seems to smell better :)).  Things went flawlessly.  All I had to do was reinstall a few of my favs and I'm good to go.  There is just one tiny, little hiccup but, I can live with that -- my screensavers won't let me set anything over 1 minute.  If I do, they don't work.  Other than that, everything is solid here.

---

### Post by bluedragon436 on 2007-10-20
> **fcumok said:**
> To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

This fixed my issue with the no boot splash screen as well as the boot speed.  Thank you very much!!!  Now if I could only figure out the no sound when logging off...but that is a small thing and not too important!!!

---

### Post by flamer on 2007-10-20
The clean install went smoothly,but upgrading from feisty was a DISASTER!

---

### Post by fcumok on 2007-10-20
> **silent911 said:**
> I tried to do so... and for point 3 I wrote:
update-initramfs -u -k 2.26.22-14-generic
and I had this answer

Cannot find /lib/modules/2.26.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.26.22-14-generic

Just copy and paste this line into the terminal and it should work, you don't need to put your kernel number in there:

sudo update-initramfs -u -k `uname -r`

---

### Post by silent911 on 2007-10-20
> **fcumok said:**
> Just copy and paste this line into the terminal and it should work, you don't need to put your kernel number in there:

sudo update-initramfs -u -k `uname -r`


It now works!!! Thanks a lot!
The problem was that I was writing 

sudo update-initramfs -u -k 'uname -r'

but what is the difference between ' and  ` ?

---

### Post by scorp123 on 2007-10-20
> **silent911 said:**
>  but what is the difference between ' and  ` ? Apostrophe << ' >> tells the shell: "This is a string. I mean litterally what I write here." Example: Write the message "Hello World." ```
echo 'Hello World.'
```

The backticks << ` >> have a way different meaning: They tell the shell "Execute the command in there and then give the resulting string back to the rest of my command line". Example: ```
echo 'Hello ' `whoami`
``` ... this should write a message on your screen saying "Hello <yourUserName>". What happens here is that first the "whoami" command is executed. The result --your username-- is given to the rest of the command.

Hope this explanation helped? :)

---

### Post by mgmiller on 2007-10-20
I'm not sure about the difference between the 2 apostrophes.  I can only find one of them on me keyboard also.  
Edit:  I found it.  It's under the ~ key,  so ' and ` are both on my keyboard.
Thanks to scorp123 for the explanation of the differences.

But, on the other hand, you typed :
```
 update-initramfs -u -k 2.26.22-14-generic
```

and it should have been:
```
update-initramfs -u -k 2.6.22-14-generic
```

---

### Post by leetcharmer on 2007-10-20
I've got almost everything setup the way I like it.  The last thing is a minor tweaking to the touchpad.  It's sensitive for scrolling in too wide of an area.  I need to shave off some of the scrollbar area so it fits into the designated area, does this make sense?

Anyone know how to?

---

### Post by leetcharmer on 2007-10-21
[Figured it out]("http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad"):

```
   Option "RightEdge" "5900"
```

That fixed it for me, expect your results to be different :D

---

### Post by Leebo on 2007-10-23
From what i see so far Gutsy is pretty cool..boots faster for me as well (compared to Fiesty).  Upgrade from Fiesty crapped out seemed like Fiesty and Gutsy hooked up and i had some kinda freakish offspring so i decide to just go ahead and clean install Gutsy.

 Install went great...had a problem detecting GeForce 6600 GT as it always does...BUT after the install of nvidia drivers, i have one problem that remains. The display is tiny...like a mini desktop on my 15in lcd monitor. maybe 1/2 to 1/4 size of a full desktop...seems kinda wierd but i also get the "Please setup PC at 1024@768 at 60 Hz" message so i gotta find the problem there but so far no other major problems.

Other than that im pleased.

Leebo

---

### Post by jmap82 on 2008-02-06
> **fcumok said:**
> To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

I know I'm a bit late on the draw, but I'm very new to this whole thing, and I can't seem to get past the first line of this fix.  

When I type "/etc/usplash.conf" into my terminal it tells me that I don't have permission.

If someone could tell me exactly what to type in that would be great.

Be gentle, newbies have feelings too. :)

Thanks


Edit:  Ok, I found out what I was missing... apparently to edit root files you have to open them with a "gedit" command.  This information didn't fix my overall problem, but now I know how to edit protected documents.

---

