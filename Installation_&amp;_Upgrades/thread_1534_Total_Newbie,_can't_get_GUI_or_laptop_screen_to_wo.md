---
title: "Total Newbie, can't get GUI or laptop screen to work"
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by helwitch on 2004-10-21
I'm a total newbie to Linux, install ubuntu on my laptop, and the GUI doesn't work, and the laptop screen doesn't work. 
It get to a certain point in booting, just after saying the bit about GRUB, and the laptop screen starts jumping, to the point where it's unreadable. I'd guess it's a resolution/refresh rate kinda problem. It looks like when a TV doesn't have a good signal and the picture rolls across the screen and jumps around. But when I plug my CRT into the laptop, it shows up fine on the CRT.
for getting the GUI to work, I tried to do the things listed here [http://wiki.ubuntulinux.org/DebuggingXautoconfiguration](http://wiki.ubuntulinux.org/DebuggingXautoconfiguration) but it said something like dpkg-reconfigure wasn't valid. (no, I didn't write down the exact error msg. I know, bad me, but I was nearly at the point where one's head explodes from frustration.) And, seriously, I'm totally new to Linux, so I really have no clue what I'm doing, I'm just trying semi random things that seem to maybe be applicable.
I installed the NVIDIA driver, but it didn't make the GUI or the laptop screen work.
Help, please? I've spent the past 4 hours trying to get this to work, and have no clue what else to do.

Laptop specs-Compaq Presario R3000Z, AMD Athlon 64 3400+ 2.20 GHz, 15.4" WXGA (1280x800), 64MB NVIDIA GeForce 4 440 Go +1394 &amp; 5-in-1 media reader, 1.0GB DDR (2x512MB), 60GB 4200, 4X DVD+RW, 54g Broadcom 802.11b/g
Exact error msg (well, close to exact)-'Cannot start X Server, likely not set up correctly, View X server output?' and the X Server output says 'Prerelease of XFree86, not in any way supported. Bugs to....Fixes to....Before reporting bugs, check version.
XFree86 v 4.3.0.1 (ubuntu 4.3.0.dfsg.1-6ubuntu25 20041018053828) [email]root@crested.warthogs.hbd.com[/email]
release date-15 Aug 04
X Protocol V 11, rev 0, rls 6.6
Build OS Linux 2.6.8-rc2 x86_64 {ELF}
Build Date 18 Oct 04
Module Loader Present'
Then it asks if I want to view the detailed X Server output, which says exactly the same thing. I don't see anything in that to give me any clue what the problem is, and I have no clue how to go about finding what the problem is from a command line. I'm a GUI kinda girl. And I can't even see what in that error msg I would google to try and figure out the problem, I don't see an error number or description, just app names and build/version #s.

---

### Post by cybrjackle on 2004-10-21
From what I have read on the net, that laptop needs the 3d drivers installed before X will even come up, so try doing this:

All of this is from the command line,

$ sudo apt-get install linux-headers-`uname -r`
$ sudo apt-get install linux-restricted-modules-`uname -r`
$ sudo apt-get install nvidia-glx
$ sudo nvidia-glx-config enable
$ sudo vi /etc/X11/XF86Config-4

Leave out the quotes in following example:

When the file is open, hit the "**/**" key and type "**HorizSync**"  and hit "**enter** key. You should see a line for your monitor see what the HorizSync &amp; VertRefresh rate are.  Yours should be set to: 

 [b]
HorizSync    30.0 - 90.0
VertRefresh  50.0 -n 75.0[/b]

You might see 2 monitors since you have a CRT connected too, (you should see two)  You might see in the Identifier line something like Compaq, that will be the one to edit.  Anyway, if those settings are different, you will want to change them to what i posted up there.  To do that, lets step back and remember that we are now sitting on the line for HorizSync,  use your letter "**L** key to move to the left until you get to the first number, if all of the numbers are incorrect, use the letter "**X** to delete them, one-by-one.  Once they are gone, hit the letter "**A**" and type in your numbers.  After that, hit the "**ESC**" key and then the "**J**" key and that will move you down to the next line were you can do "**X** to delete and "**A**" to add then "**ESC**" again. Then hit the following keys '**shift**" + "**:**" then "**wq**" and hit enter.

sudo reboot

Cross your fingers :)

If you can, post your entire  /etc/X11/XF86Config-4  So we can take a look at it.

---

### Post by cybrjackle on 2004-10-21
:oops: 

Sorry, you said your a total noobie, all that "vi" stuff isn't going to make a lick of sense to you.

Um, if you can see from your CRT, and you install all those packages. and espically the last line 
```
sudo nvidia-glx-config enable
```
You might simply be able to reboot and be good, i might have made that a tad difficult to follow.

---

### Post by JProgrammer on 2004-10-21
Yes vi is really too dificult for a noobie to use try pico or nano

sudo nano /etc/X11/XF86Config-4

or 

sudo pico /etc/X11/XF86Config-4

---

### Post by helwitch on 2004-10-21
[quote=cybrjackle]:oops: 

Sorry, you said your a total noobie, all that "vi" stuff isn't going to make a lick of sense to you.

Um, if you can see from your CRT, and you install all those packages. and espically the last line 
```
sudo nvidia-glx-config enable
```
You might simply be able to reboot and be good, i might have made that a tad difficult to follow.[/quote]
Eh, if that was the exact, step by step process for what I do, seems simple enough. I'll give it a try. but I'll try without all the vi stuff first, and see if that does the trick :)
And as for posting the  /etc/X11/XF86Config-4 file, if it's reasonably simple to email it to myself from the command line, and someone is willing to give me step by step instructions (example:type this to create a mail with the file attached. type the email addy to send to. type your smtp server. type the smtp auth. type this. the mail is sent. or whatev) then I'll give it a shot. cos ubuntu connected to my router quite nicely :)

---

### Post by JProgrammer on 2004-10-22
just open it up in gedit and post it here on the forums with a copy and past

sudo gedit /etc/X11/XF86Config-4

---

### Post by FLeiXiuS on 2004-10-22
[quote=JProgrammer]just open it up in gedit and post it here on the forums with a copy and past

sudo gedit /etc/X11/XF86Config-4[/quote]

He won't be able to open it up with gedit if X won't start  :P

---

### Post by helwitch on 2004-10-22
[quote=JProgrammer]just open it up in gedit and post it here on the forums with a copy and paste sudo gedit /etc/X11/XF86Config-4[/quote]
I'm accessing the forums from a diff comp. I have no clue how I would go about copy pasting across the network. Is that even possible? :) If it is, again, give me the exact commands for it and I'll give it a try.

[quote=cybrjackle]:oops:
Sorry, you said your a total noobie, all that "vi" stuff isn't going to make a lick of sense to you.
Um, if you can see from your CRT, and you install all those packages. and espically the last line 
```
sudo nvidia-glx-config enable
```
You might simply be able to reboot and be good, i might have made that a tad difficult to follow.[/quote]
The laptop screen works now, YAY.
$ sudo apt-get install linux-headers-`uname -r` 
$ sudo apt-get install linux-restricted-modules-`uname -r` 
both came back package not found (or maybe it was can't find package)
$ sudo apt-get install nvidia-glx 
$ sudo nvidia-glx-config enable 
seems to have done the trick, screen wise anyway. When it tries to run Gnome, it flashes a full screen Nvidia logo 3 or 4 times, and then gives me the same error msg it did originally. (cept I can see it on the laptop screen now, which makes life easier since I only have one monitor *grin*)
when I do $ sudo vi /etc/X11/XF86Config-4 it opens what looks to be a blank file, and says new file at the bottom, (and, um, is 'shift+: Q' the right thing for closing the file without changing it? it got me a command line at least, so I'm guessing it was right.) 
and when I '/HorizSync', it says pattern not found. So, I'm guessing there's something majorly wrong with /etc/X11/XF86Config-4 ?

[quote=FLeiXiuS]He won't be able to open it up with gedit if X won't start  :P[/quote]
She. :)

---

### Post by helwitch on 2004-10-22
right, ok, capitalization matters. I didn't realize this. in retrospect, it's obvious, sorta. (why can't linux be smart enough to know that x11 and X11 are the same thing when only one of them exists?). The HorizSync is set to 30.0 - 90.0, and the VertRefresh is set to 50.0 - 75.0.
I found a website [http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/](http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/) that has an XF86Config-4 that is supposed to work with my model laptop. But how do I get the file onto the laptop? like I said, it seems to be able to connect to the internet, (it got packages during install, and keeps timesyncing on boot) so is there a command line way to get the file from the net straight onto the laptop? Or, if I burn it to CD, how do I copy it from the CD onto the laptop? (Yes, I really am this clueless about linux/command lines.)
If you want to point me to a nice tutorial, that'd be great so I could learn for the future, but if you could take pity on me and give me the step by step commands to get it working properly for now, I'd REALLY appreciate it. (or, ya know, don't if you don't wanna. I've already made plans to go bug a friend of a friend saturday who I know is willing to put up with me being clueless.) I'm just not really at a 'grow through learning new things' point right now. More like 'work you piece of $%#&amp;@ laptop, WORK!'
*sigh* I keep trying to go to bed, and then thinking of something else I haven't tried yet, and MUST try. and I have to be awake for class in 5 hours. *double sigh* must go to bed. must stop trying to make laptop work. hmm, I may actually listen to myself, cos I can't think of anything I haven't tried.

---

### Post by cybrjackle on 2004-10-22
$ cd /etc/X11/
$ sudo mv XF86Config-4 XF86Config-4.orig
$ sudo wget [http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/XF86Config-4](http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/XF86Config-4)



Yes, caps matter.  I put caps in my vi directions so you could tell the difference in some of the letters.  sorry, should have pointed that out :)

---

### Post by helwitch on 2004-10-22
[quote=cybrjackle]$ cd /etc/X11/
$ sudo mv XF86Config-4 XF86Config-4.orig
$ sudo wget [http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/XF86Config-4](http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/XF86Config-4)[/quote]
*whimper* it didn't work. I replaced the XF86Config-4 file that was there with the internet one, and there's still no GUI. (and yes, I remembered to reboot after making the switch)*whimper* I checked the file, and it replaced it just fine. Apparently, that wasn't the problem. So, I'm open to suggestions, tho at this point I'm more or less ready to just hand it to the friend of a friend and let him try to make it work.

---

### Post by cybrjackle on 2004-10-22
Since you said that it did not find these files, update first.

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo reboot

Then 

$ sudo apt-get install linux-headers-`uname -r`
$ sudo apt-get install linux-restricted-modules-`uname -r`
$ sudo apt-get install nvidia-glx
$ sudo nvidia-glx-config enable

---

### Post by helwitch on 2004-10-23
[QUOTE=cybrjackle]Since you said that it did not find these files, update first.

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo reboot

Then 

$ sudo apt-get install linux-headers-`uname -r`
$ sudo apt-get install linux-restricted-modules-`uname -r`
$ sudo apt-get install nvidia-glx
$ sudo nvidia-glx-config enable[/QUOTE]
My router just died, which means I can't get online with my laptop from linux. so trying to get the GUI working gets to wait til I replace the router. Thanks for this tho, I'll try it as soon as I can, and let you know if it works. And in the meantime, I'm getting a bit of a forced lesson in command line usage, which isn't exactly a bad thing.
Oh, and I used your vi directions to edit my grub menu to be able to boot windows, and it worked perfectly, thanks!

---

### Post by helwitch on 2004-10-23
[QUOTE=cybrjackle]Since you said that it did not find these files, update first.

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo reboot

Then 

$ sudo apt-get install linux-headers-`uname -r`
$ sudo apt-get install linux-restricted-modules-`uname -r`
$ sudo apt-get install nvidia-glx
$ sudo nvidia-glx-config enable[/QUOTE]
It's still coming back saying couldn't find package for linux-headers-`uname -r` and linux-restricted-modules-`uname -r`.

---

