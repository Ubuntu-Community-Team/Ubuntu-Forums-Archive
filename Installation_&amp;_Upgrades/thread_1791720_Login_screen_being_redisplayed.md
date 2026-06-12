---
title: "Login screen being redisplayed"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by pravsemilo on 2011-06-27
Hi,

I just upgraded to Ubuntu 10.04 LTS. The upgrade went fine and once it was done, it did a restart of computer. (Expected)

After the restart, I cleaned up my computer a bit. (Reinstalled some packages, removed some). One extra thing that I did was removed all .Xsession_* files from my home directory. (I thought they were old and removed them). 

Since then whenever I restart my machine, the login screen is displayed, but that doesn't allow me to login.When I enter my user name and password, it just displays the login screen again afer some time (displays a black screen and then back to login screen). Same for the root user.

However I am able to login in console mode using both my own user id and root user id.

I doubt if I messed up something while trying to do my own clean up. I don't have a live CD. I upgraded over the internet.

Can someone help me out of this?

Thanks.

---

### Post by MAFoElffen on 2011-06-27
> **pravsemilo said:**
> Hi,

I just upgraded to Ubuntu 10.04 LTS. The upgrade went fine and once it was done, it did a restart of computer. (Expected)

After the restart, I cleaned up my computer a bit. (Reinstalled some packages, removed some). One extra thing that I did was removed all .Xsession_* files from my home directory. (I thought they were old and removed them). 

Since then whenever I restart my machine, the login screen is displayed, but that doesn't allow me to login.When I enter my user name and password, it just displays the login screen again afer some time (displays a black screen and then back to login screen). Same for the root user.

However I am able to login in console mode using both my own user id and root user id.

I doubt if I messed up something while trying to do my own clean up. I don't have a live CD. I upgraded over the internet.

Can someone help me out of this?

Thanks.
Welcome to Ubuntu Forums!

Running out the door at moment but... will be back later to help.

Deleting the .Xsession files from your home directory removed the per-user graphics settings you previously had. Those setting were done by xrandr commands that set resident temporary settings, that just affected that user's graphics session.  Global settings are commonly set now with the xorg.conf file.

While I'm gone, please read the first 3 posts of:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") 

Then post the results of:
```

lspci -v | grep VGA
sudo hwinfo --framebuffer
sudo hwinfo --monitor
xrandr -q

```If you get a command not found error on hwinfo, please install and run those 2 commands again.  Install via:
```

sudo apt-get install hwinfo

```Also please post these 2 files* if present*:
```

/etc/X11/xorg.conf
/var/log/xorg.0.log

```

---

### Post by pravsemilo on 2011-06-27
lspci -v | grep VGA - VGA compatible controller : INtel corporation core processor controller integrated graphics controlelr rev 12


xrandr -q  - Cannot open display

I cannot run hwinfo commands as I am not able to access internet from the console. apt-get fails saying cannot access archive.ubuntu.com

/etc/X11/xorg.conf - I dont have this file. But I do have a xorg.conf.backup
/var/log/worg.0.log - Did you mean Xorg.0.log?

---

### Post by MAFoElffen on 2011-06-27
> **pravsemilo said:**
> lspci -v | grep VGA - VGA compatible controller : INtel corporation core processor controller integrated graphics controlelr rev 12


xrandr -q  - Cannot open display

I cannot run hwinfo commands as I am not able to access internet from the console. apt-get fails saying cannot access archive.ubuntu.com

/etc/X11/xorg.conf - I dont have this file. But I do have a xorg.conf.backup
/var/log/worg.0.log - [COLOR=Red]Did you mean Xorg.0.log?[/COLOR]Yes, that was my typo as I was running out the door.  That will show us what is loading & where the graphics is crashing.

Is this really old equipment?  What you said about the monitor might mean it doesn't store or return EDID data.  Would need hwinfo data to pick a driver and configure an xorg.conf...

Now no internet connection?

---

### Post by ToshibaLaptoplinux on 2011-06-27
I have the exact same problem as described by the original poster. However, this occurred after a clean install of Natty! My Home Directory is on a separate partition.

Should I start a separate thread or contribute to this one.

How do I solve this??? The link you provided doesn't seem to be related but I could be mistaken.

---

### Post by ToshibaLaptoplinux on 2011-06-27
Deleted

---

### Post by ToshibaLaptoplinux on 2011-06-27
Neither of these files are on my machine.
/etc/X11/xorg.conf
/var/log/worg.0.log

lspci -v | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])

xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)



I would also note that I was successfully running Natty as an upgrade up until now. I chose to do a clean install because my system had gone through multiple upgrades and was a bit clunky as a result. The iso checksums checked out and the disc was successfully burned and verified. I also re-executed the clean install multiple times to double check and after every install the behaviour is the same.

Thanks for help.

---

### Post by MAFoElffen on 2011-06-28
> **ToshibaLaptoplinux said:**
> This is my xsessions error file.
[COLOR=Red]<< Edited >>[/COLOR]
[html]
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/tlee/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/ibus.
Initializing nautilus-dropbox 0.6.7
Initializing nautilus-gdu extension
** Message: Initializing gksu extension...
Initializing nautilus-open-terminal extension

(nautilus:2421): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

(nautilus:2421): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.

Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
Shutting down nautilus-open-terminal extension
Shutting down nautilus-gdu extension

--- Hash table keys for warning below:
--> inode/directory
--> l2050
--> tlee
--> l2069
[/html]
First, as a forum admin kind of thing... When posting logs or code, please use the forum posting toolbar and use the " # " icon for code tags or the  " <> " icon for html tags and paste text or code within the tags. That will organize your text within a textboxt with scrollbars and make it easier to read... without taking up a whole display page.

Next, looks like you may may not have the same problem as the originator of this thread... You may be better served by starting your own new thread.  In your title (Example- Lost ownership of home) and post, your should describe your problem. & include this log... Describing that your are having a "home" ownership problem along with a "compiz" problem. (but the compiz problem could be caused by the ownership problem)

Yes-  Both of you are having problems not seeing or finding settings files, but that is where the similarity ends-->

After multiple other errors, your later xerver errors are from not being able to find existing settings files from your home directory, because it says you do not have ownership of your own home directory...

The originator of this thread has problems not finding settings files because of manualy deleting those settings files from his home directory- which he does have valid ownership of...  His "fix" in going to be much different that yours..

You could reference a link to this post or copy/quote this post into that post for reference, so that other's aren't looking at your problem from scratch.

Hint on yours--> Once you start a new thread > Run the "Boot Info Script" in my sig and post it in a post there.  (Remember to paste it within code tags.) I think we will find your problem in your fstab file.  Come back here and post a link to your new thread so that I can help you with that there...

---

### Post by MAFoElffen on 2011-06-28
Bump... Still there?  Internet connection yet?

---

### Post by pravsemilo on 2011-06-30
Thank you very much MAFoElffen.

Truly appreciate your time and efforts.

I couldn't try out the solutions proposed due to above reasons. However I got a colleague of mine to look into this.

He upgraded the install pack of ubuntu-desktop from the live CD and that fixed the issue.

Thanks again.

---

### Post by ToshibaLaptoplinux on 2011-06-30
> **MAFoElffen said:**
> First, as a forum admin kind of thing... When posting logs or code, please use the forum posting toolbar and use the " # " icon for code tags or the  " <> " icon for html tags and paste text or code within the tags. That will organize your text within a textboxt with scrollbars and make it easier to read... without taking up a whole display page.

Next, looks like you may may not have the same problem as the originator of this thread... You may be better served by starting your own new thread.  In your title (Example- Lost ownership of home) and post, your should describe your problem. & include this log... Describing that your are having a "home" ownership problem along with a "compiz" problem. (but the compiz problem could be caused by the ownership problem)

Yes-  Both of you are having problems not seeing or finding settings files, but that is where the similarity ends-->

After multiple other errors, your later xerver errors are from not being able to find existing settings files from your home directory, because it says you do not have ownership of your own home directory...

The originator of this thread has problems not finding settings files because of manualy deleting those settings files from his home directory- which he does have valid ownership of...  His "fix" in going to be much different that yours..

You could reference a link to this post or copy/quote this post into that post for reference, so that other's aren't looking at your problem from scratch.

Hint on yours--> Once you start a new thread > Run the "Boot Info Script" in my sig and post it in a post there.  (Remember to paste it within code tags.) I think we will find your problem in your fstab file.  Come back here and post a link to your new thread so that I can help you with that there...

Thank you for the time and information.

I am sorry for not enclosing the log in # or <>. After I initially posted I was wondering how it could be easily read. In the future I will do so when posting such long text strings.

To not derail this thread, I deleted the post because as you kindly indicated it was not the same problem as the original poster. I also noticed that there was some private data in there I rather not have posted on an open forum. Would you be so kind as to delete your quote as well.

Due to the information you provided I changed the ownership of my home and re-installed again and now I can successfully login to my desktop...however I am only able to login to the "classic" desktop. If I log into the Ubuntu desktop it gets borked. As that is a separate problem I will start another thread however it is disconcerting that I would have these problems after a clean install.

Thanks again.

---

