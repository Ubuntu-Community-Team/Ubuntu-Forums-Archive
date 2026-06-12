---
title: "upgrade to Gutsy, squares on screen are oblong"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by silbar on 2008-03-09
Sorting out problems after upgrade to Gutsy from Dapper.  This one has me quite baffled, and I've not found any relevant posting in this Forum about it or how to cure it.

I have a Hitachi CM812 monitor.  The installation of Gutsy didn't find it, and it invokes a screen resolution called "Custom 1" of size 1680x1050 at 60 Hz.  The Screen and Graphics app also claims my graphics cardis RIVA TNT.  The problem is that things that ought to be square of circular (the spinning cursur, for example) are a bit squished horizontally (or stretched vertically).  It doesn't make any difference if I installed and enable the nvidia-glx-legacy driver or not. 

Another symptom is that some things print with the bottoms of numerals slightly chopped off.  I assume, but don't know for sure, that this is related.

None of these symptoms showed up under Dapper.

Since 1680x1050 is a bit too tiny in type size for these old eyes, I would dearly love to change to something more amenable, like 1280x1024.  If I click on the Model tab and change to Hitachi CM812 and select that resolution, sometimes I get the opportunity to try a test screen -- but that never works.  This time, as I write this, I don't have that opportunity, so I'm going to submit this posting before taking the plunge and clicking the OK button.

Any help on this matter would be greatly appreciated.  Thanks in advance,

   Dick Silbar

---

### Post by Peter09 on 2008-03-10
I would suggest that you do not change from the best resolution for your monitor, having an incorrect resolution may be what is giving you the strange shaped icons etc. 

Once you have your resolution right then you can install a theme that provides larger fonts and icons so that you have no problems on-screen and you can set the sizes of default fonts in the applications yourself.

There may be a better way than this as I have not considered this in great depth before. :)


PC.

---

### Post by silbar on 2008-03-10
Thanks Peter,   You said "having an incorrect resolution may be what is giving you the strange shaped icons etc."  That sounds about right, since the Hitachi CM812U can handle 1600 by 1200, which is different than the 1680 x 1050 which Custom1 provides.

The reason for the long delay in making this posting, is that I really goofed up good in trying to set the CM812U to a resolution it couldn't handle.  This then, on restart, gave me a completely unworkable screen -- total gibberish (of a yellowish green cast).  I was unable to recover by setting things back to Custom 1 by booting from the Live CD.  

So, in the end, I did a complete new re-install of Gutsy.  Not fun, since it then invokes a 2.5 hour download of 196 updates.  Plus the hassle of extracting my /home/silbar data from the tar file backup.  And then, going through all the installs of the software I need.  If anyone can tell me a BETTER way of recovering a useful screen display, I'd greatly appreciate it.

Also of possible relevance: now in the Screen & Graphics app, setting the model to Hitachi CM812 (no choice of CM812U) and selecting 1280x1024 at 85 Hz (the user's manual says that's OK), I have a Test button to click.  (Why didn't I have this before when I made the first posting?)  However, clicking Test, the screen goes black for a second and then the Screen & Graphics app disappears (crashes).  On restarting that app, I'm back to Custom 1 settings.

I'm going to leave it there for now, hoping for some enlightenment down the line.  Thanks,

   Dick Silbar

---

### Post by Shazaam on 2008-03-10
silbar.....
Do you have, by ANY chance, a copy of your Dapper xorg.conf laying around? The reason I ask is that you CAN use it to get a working system in a pinch .:wink:

---

### Post by Peter09 on 2008-03-11
Have you set your graphics card driver up ok? What is your graphics card?

You normally will not need to reboot the O/S to correct thing as your operating system is running O.K. You need to look at your screen drivers.

It can be a bit difficult getting your card set up  and ubuntu is not good at setting some resolutions by default. 

I guess the first thing is to get the driver right, this is 90% of the issue.

If you have a black screen that you cannot work with try booting into safe mode. 

PC

---

### Post by silbar on 2008-03-11
Hello, Shazaam,

> **Shazaam said:**
> silbar.....
Do you have, by ANY chance, a copy of your Dapper xorg.conf laying around? The reason I ask is that you CAN use it to get a working system in a pinch .:wink:

Not a chance.  I've located xorg.conf in the Gutsy /etc/X11/ but looking at that file in a text editor, I don't see what to change.  Besides, it warns me not to edit anything at all on dire pain of fouling things up.  The brief look I had at 'man xorg.conf' was also not very enlightening.  So, I've changed nothing in that file.

I guess you're suggesting I should have backed up the Dapper /etc/ folder, but now it's too late to do that.  I don't even know if I have the CD for going back to re-install Dapper, even if that were a reasonable idea.

But, thanks for the suggestion.

   Dick Silbar

---

### Post by silbar on 2008-03-12
Thanks, again, Peter,

> **Peter09 said:**
> Have you set your graphics card driver up ok? What is your graphics card?

As intimated in the first posting, it is (or is claimed to be) an NVIDIA RIVA TNT.  It seems to make no difference to my oblongness if I enable the NVIDIA drivers or not.  As stated, it is the nvidia-glx-legacy driver.

> **Peter09 said:**
> You normally will not need to reboot the O/S to correct things as your operating system is running O.K. You need to look at your screen drivers.

It can be a bit difficult getting your card set up  and ubuntu is not good at setting some resolutions by default. 

I guess the first thing is to get the driver right, this is 90% of the issue.

If you have a black screen that you cannot work with try booting into safe mode. 

PC

Actually, the gibberish screen is a kind of putrid yellow-green.  So, the question is, did Ubuntu not pick the right restricted driver to install?  This is, after all, a pretty old machine (it came with Win98 installed).

   Dick Silbar

---

### Post by Peter09 on 2008-03-12
Perhaps the best thing to do is to download ENVY from here:-

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and use that to set up your Nvidia driver. It will also configure your Xorg file for you.

I suggest that you give it a try.

PC

---

### Post by silbar on 2008-03-13
> **Peter09 said:**
> Perhaps the best thing to do is to download ENVY from here:-
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
and use that to set up your Nvidia driver. It will also configure your Xorg file for you.
I suggest that you give it a try.
PC

Thanks, Peter.  I did that last night -- a surprisingly long and complicated process, but it seems to have worked properly.  I get a flash of the NVIDIA logo on a restart, after enabling the restricted driver.

However, the screen still comes up oblong with the Custom1 setting.  Looking at the new /etc/X11/xorg.conf (and there is now also a backup copy there!),
it still says my monitor is "generic".  I suppose that could be changed by going into the Screen Preferences app, yes?  When I started to do so last night, I didn't get the opportunity to try a test page, so I went to bed, it being late.  

Now, however, I have backups of the xorg.conf's on a removable drive.  With Shazam's comments about lying-around xorg.conf's, I'll try that scary procedure later today.

   Dick Silbar

---

### Post by zvacet on 2008-03-13
@ **silbar**


> Sorting out problems after upgrade to Gutsy from Dapper.

Of course you are,because you upgrade directly from Dapper to Gutsy and that is not right way to do upgrade.You should go Dapper>Edgy>Feisty>Gutsy or make separate home partition(if you don´t have it allready),backup your files and make fresh install of Gutsy.But now it is too late for that and I hope that you will sort out your prroblems.Good luck!

---

### Post by Peter09 on 2008-03-13
You do not need to change what your monitor is called, just add the required resolution into the relevant section in your xorg.conf file and then select it in the 

system->preferences-> resolution

menu

Before you do that do this bit of code in a terminal

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.saved
``` 

that will copy your current xorg.conf file to a file called xorg.conf.saved.

in the event of a problem just reinstate the working one with 

```
sudo cp /etc/X11/xorg.conf.saved /etc/X11/xorg.conf
```


PC

---

### Post by silbar on 2008-05-01
Hello,

I was the one who started this thread.  After some time, I have now "solved" the problem by (finally) getting a more modern computer and display.

   Dick Silbar

---

