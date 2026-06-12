---
title: "Is my beloved Ubuntu broken?  (Pictures inside)"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Morty007 on 2008-06-08
Today after being in windows xp for a bit, (Actually gaming for a few hours) I reboot the machine to ubuntu. On bootup I get the following picture.

[IMG]http://i3.photobucket.com/albums/y70/morty007/IMG_0487.jpg[/IMG]



I then restart several times and it's the same thing. Ctrl-alt-backspace just bring me to a black screen a blinking prompt. (Or whatever you call it. ) The kernel version I was booting into was the latest one, .19 was the end of it. 

Windows boots up just fine. If you look at the bottom of the picture it said ubuntu couldn't detect keyboard and video card. 

Can anyone help me? I haven't booted into safe mode yet but I'll try that next. Really scary stuff.

---

### Post by underdog512 on 2008-06-08
it looks like there is somthing wrong with your xorg.conf file. You are going to need to boot into recovery mode.  

when you see grub loading, press ESC.  select "root prompt" from the menu.

We need to see if you a have a backup of your xorg.conf file.  

Once you are at the command prompt type:

ls /etc/X11/

tell us what files you have listed.

FYI... the filenames are case sensitive.

---

### Post by Morty007 on 2008-06-08
Thanks, I will try that now.

---

### Post by Morty007 on 2008-06-08
Ok, I booted into recovery mode and put in the prompt. Below is what I got:

[IMG]http://i3.photobucket.com/albums/y70/morty007/IMG_0490.jpg[/IMG]



[IMG]http://i3.photobucket.com/albums/y70/morty007/IMG_0491.jpg[/IMG]

And then after that I accidentally hit enter or something and it gave me this:


[IMG]http://i3.photobucket.com/albums/y70/morty007/IMG_0493.jpg[/IMG]



Where should I go from here?

---

### Post by Morty007 on 2008-06-08
Is my beloved Ubuntu broken? 

This is a repost from here. (Felt it was wrong forum.)   [http://ubuntuforums.org/showthread.php?t=822162](http://ubuntuforums.org/showthread.php?t=822162)

--------------------------------------------------------------------------------

Today after being in windows xp for a bit, (Actually gaming for a few hours) I reboot the machine to ubuntu. On bootup I get the following picture.

[IMG]http://i3.photobucket.com/albums/y70/morty007/IMG_0487.jpg[/IMG]



I then restart several times and it's the same thing. Ctrl-alt-backspace just brings me to a black screen and blinking prompt.  The kernel version I was booting into was the latest one, .19 was the end of it.

I've booted with other kernels and it's the same thing. 

Windows boots up just fine. If you look at the bottom of the picture it said ubuntu couldn't detect keyboard and video card. 

Can anyone help me? I haven't booted into safe mode yet but I'll try that next. Really scary stuff.
__________________
      

**[SIZE="5"]What I have tried to to do fix:[/SIZE]**
  

Someone in the general forum told me below:

it looks like there is somthing wrong with your xorg.conf file. You are going to need to boot into recovery mode. 

when you see grub loading, press ESC. select "root prompt" from the menu.

We need to see if you a have a backup of your xorg.conf file. 

Once you are at the command prompt type:

ls /etc/X11/

tell us what files you have listed.

FYI... the filenames are case sensitive. 
      

underdog512 

Ok, I booted into recovery mode and put in the prompt. Below is what I got:

[IMG]http://i3.photobucket.com/albums/y70/morty007/IMG_0491.jpg[/IMG]




[IMG]http://i3.photobucket.com/albums/y70/morty007/IMG_0490.jpg[/IMG]





And then after that I accidentally hit enter or something and it gave me this:


[IMG]http://i3.photobucket.com/albums/y70/morty007/IMG_0493.jpg[/IMG]



That's where I'm at now. So I'm still stuck. Anyone who could please help me, I love Linux but I'm also a newbie so this is frustrating not knowing what to do.

---

### Post by Gizkaguy on 2008-06-08
That's happened to me once, although I didn't get all of those errors ... I got a desktop that couldn't use 3D effects.

But, I have had a lot of problems with graphics. The only OS that seems to really work with my graphics card is Ubuntu.

What usually works is to type

vim /etc/X11/xorg.conf

you then need to change the driver to "vesa":

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

That has always worked for me, but you will then get no 3D graphics. :(

Good luck!

EDIT: Didn't see those at first ... it looks like you have several xorg.conf backup files. If the above doesn't work, try renaming xorg.conf to something like xorg.conf.bk and renaming a backup to xorg.conf

---

### Post by dasunst3r on 2008-06-08
In safe mode, you can also issue the command *dpkg-reconfigure xserver-xorg*.  This will run you through the process of reconfiguring your graphical server.

---

### Post by Morty007 on 2008-06-08
Well, I definitely want the 3-d graphics and compiz. I guess I will try dasunst3r's solution.

---

### Post by Tom--d on 2008-06-08
> **dasunst3r said:**
> In safe mode, you can also issue the command *dpkg-reconfigure xserver-xorg*.  This will run you through the process of reconfiguring your graphical server.


That works btw. 
Its very helpful ;) gets me out of trouble when messing around with the xorg.conf :p

---

### Post by bapoumba on 2008-06-08
Threads merged.

---

### Post by Morty007 on 2008-06-08
> **dasunst3r said:**
> In safe mode, you can also issue the command *dpkg-reconfigure xserver-xorg*.  This will run you through the process of reconfiguring your graphical server.

Dasunst3r and Tom- I did that and it went through some screens telling me about the keyboard layout, and whether to autodetect or not.

I went through them but at the end it just brought me to a command prompt marc@root or something to that effect. (I'm Marc needless to say) I didn't know what to do at that point. Can either of you all help?

---

### Post by bapoumba on 2008-06-08
> **Morty007 said:**
> Dasunst3r and Tom- I did that and it went through some screens telling me about the keyboard layout, and whether to autodetect or not.

I went through them but at the end it just brought me to a command prompt marc@root or something to that effect. (I'm Marc needless to say) I didn't know what to do at that point. Can either of you all help?

Did you run the reconfigure from the recovery session or a virtual terminal ? (Ctrl-Alt-F2 for ex). Did it finish smoothly ? If so, you need to restart the session (ctrl-alt-backspace) for the new file to be loaded.

---

### Post by Morty007 on 2008-06-08
I did it through the recovery session, but had to power down the machine because I had to leave unexpectedly. 

I will try this again with the ctrl-alt-backspace at the end, and report back in a few hours.

---

### Post by bapoumba on 2008-06-08
> **Morty007 said:**
> I did it through the recovery session, but had to power down the machine because I had to leave unexpectedly. 

I will try this again with the ctrl-alt-backspace at the end, and report back in a few hours.

From the recovery session, after you are done with the reconfigure just run```
reboot
``` and it will reboot the machine ;)

---

### Post by Morty007 on 2008-06-08
Thanks bapoumpa and everyone else! It booted up fine. The desktop effects are off, so I will try to fix that now and hopefully all will be well.

---

### Post by Morty007 on 2008-06-08
Bad news- Since there were no effects I enabled the nvidia drivers and then rebooted as told. Took me back to the original plain black screen and then the jumbled colors. 

Is there anything else I can try? I would like to avoid a reinstall.

---

### Post by Morty007 on 2008-06-09
Anyone?

---

### Post by Morty007 on 2008-06-09
?

---

### Post by tom66 on 2008-06-09
Try copying the backup files to the original.

Execute the following commands in recovery/failsafe mode.

1.) cd /etc/X11
2.) mv xorg.conf xorg.conf.broken -i
3.) cp xorg.conf.2008<TAB KEY> xorg.conf -i
    (where <TAB KEY> should be a press of the tab key)
4.) reboot

Try and see if it works... 

By the way, the -i flag is interactive, so it will confirm for one last time about the copying/renaming, in case you mistype the file name. 

Hope this helps!
Tom

---

### Post by Morty007 on 2008-06-09
Thanks Tom, I'll give it a try.

---

### Post by Morty007 on 2008-06-09
I got a "missing destination file operand after 'xorg.conf.20080600xorg.conf'

Try cp--help for more info. 

I think I'll have to reinstall, or maybe its my chance to try a different distro.

---

### Post by bapoumba on 2008-06-09
Looking for your video card, there are these two old threads (be careful, the situation may have changed with hardy):
[http://ubuntuforums.org/showthread.php?t=452835]("http://ubuntuforums.org/showthread.php?t=452835")
[http://ubuntuforums.org/showthread.php?p=2842452]("http://ubuntuforums.org/showthread.php?p=2842452")

Did you install the nvidia drivers ? (there should be a menu entry for hardware drivers).

---

### Post by Morty007 on 2008-06-09
Yes, after I re-enabled the drivers I rebooted and it went back to that screen.

---

### Post by bapoumba on 2008-06-09
> **Morty007 said:**
> Yes, after I re-enabled the drivers I rebooted and it went back to that screen.

There was no error message or no complaint when you enabled the drivers? Quite strange if it is not actually working (I assume installing the proprietary drivers should prompt with an error message if not correctly installed).

---

### Post by tom66 on 2008-06-09
I think you missed the space out, put one between 0600 and xorg.conf

---

### Post by Morty007 on 2008-06-09
I tried it again, and this time after I pressed tab and the rest of the line it said "xorg.conf.broken?"

I wasn't sure what to do so I continued with the code. Back to the same screen on reboot.

---

### Post by tom66 on 2008-06-09
That's supposed to happen, but it should have worked. If that doesn't work it may be best to just back up and reinstall, I'm sorry about this.

---

### Post by Morty007 on 2008-06-09
No problem. I will uninstall and then give Mint 5 a try. It's probably good that it happened, I'm a little more experienced now.

---

### Post by Rotarychainsaw on 2008-06-09
What if you boot an older kernel?

---

### Post by Morty007 on 2008-06-09
I think it did the same thing, but I'll try again just in case.

---

### Post by Morty007 on 2008-06-09
All kernels are hosed. I just uninstalled and fixed my mbr so now I'm back to just windows. I'm getting Linux Mint 5 and will try that.

---

