---
title: "nomodeset booting issues"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by dondiego2 on 2010-10-23
I had another thread that seemed to die.  So I'll try again.

I tried to upgrade from 10.04 to 10.10 and killed my computer.  I have windows xp on a 320gb drive and ubuntu 10.10 on the 25ogb drive. I got windows going again.  I could not get 10.10 to boot - grub was missing.  So I decided to reinstall 10.10.  I downloaded and burned a disc with the iso file but I could not get it to run - it just put my monitor to sleep.  I finally stumbled upon nomodeset and set it to that and it finally installed 10.10 on my 250gb drive.  It then asked me to reboot.  

That takes me to tonight.  Rebooted, went to grub, chose linux and my monitor went to sleep.  Rebooted, at the grub screen hit "e" to bring up an editor.  I added a space and "nomodeset" behind the no splash remark.

It booted but it booted into a full screen terminal asking for my username and password.  I typed startx after entering the username and password and got a boatload of errors.  In essence it couldn't find any drivers.

How do I fix this and get back to my desktop and a regular boot without having to edit the grub screen every time?

---

### Post by Harvil on 2010-10-23
Just edit the /etc/default/grub and save it.
I believe the code is.... " gksudo gedit /etc/default/grub "
After you change it update it: " sudo update-grub "

---

### Post by dondiego2 on 2010-10-24
> **Harvil said:**
> Just edit the /etc/default/grub and save it.
I believe the code is.... " gksudo gedit /etc/default/grub "
After you change it update it: " sudo update-grub "

```
gksudo gedit/etc/default/grub
```

returned

```
(gksudo:1604):Gtk-WARNING **:cannot open display:
```

How do I load drivers and start my display and get into the desktop from the terminal?  If that's what I need to do.

---

### Post by akand074 on 2010-10-24
To start the graphic user interface use this command:

```
sudo /etc/init.d/gdm start
```And also the command you got before won't work because that runs the GUI text editor, you'll have to use a command line text editor. Try this:

```
sudo nano /etc/default/grub
```

Edit: Also about loading drivers, in Linux, unlike windows, the drivers are built right into the kernel (though you could still install different drivers like proprietary drivers). Your only problem is that your user interface is not running.

How did you install Ubuntu? I don't know how you managed to cause such a problem. If you installed Ubuntu manually, I would suggest you let the auto-installer do it for you if your having trouble.

---

### Post by dondiego2 on 2010-10-24
> **akand074 said:**
> To start the graphic user interface use this command:

```
sudo /etc/init.d/gdm start
```And also the command you got before won't work because that runs the GUI text editor, you'll have to use a command line text editor. Try this:

```
sudo nano /etc/default/grub
```Edit: Also about loading drivers, in Linux, unlike windows, the drivers are built right into the kernel (though you could still install different drivers like proprietary drivers). Your only problem is that your user interface is not running.

How did you install Ubuntu? I don't know how you managed to cause such a problem. If you installed Ubuntu manually, I would suggest you let the auto-installer do it for you if your having trouble.


Thanks I will try you suggestions after I finish typing my reply in Windows and reboot my computer.

 I was running 10.04 and just used the upgrade manager to update to 10.10.  I remember telling it not to change my grub (maybe I shouldn't have).  Anyway, after it upgraded I rebooted my machine as required and I got grub missing prompt or something like that and could not boot Windows or Ubuntu.  I ended uo getting Windows going and downloaded the 10.10 iso file and tried to reinstall 10.10 from the live CD.  I have Windows and Ubuntu on two separate hard drives.

The only way I could get the live CD to run was to hit hit F6 at the menu screen and check the nomodeset menu item.  Anything else I did just put my monitor to sleep and would not run.  So I installed 10.10 on the same drive I already had it on but did not wipe the drive clean (maybe that was another mistake).  It installed everything looked great, then it asked me to reboot to finish the installation.  That is where I am at now. It will reboot and put my monitor to sleep or it will reboot to the terminal if I edit the grub screen to include the nomodeset command.  

That's how I got here.

---

### Post by kansasnoob on 2010-10-24
Ultimately it would be very helpful to know the specific graphics card info, so if you have some other, older Linux live disc that will run on that machine please post the output of:

```
lspci | grep VGA
```

---

### Post by dondiego2 on 2010-10-24
> **kansasnoob said:**
> Ultimately it would be very helpful to know the specific graphics card info, so if you have some other, older Linux live disc that will run on that machine please post the output of:

```
lspci | grep VGA
```


OK, let's try this again.  I was in the middle of typing a response to you and my power went out!

I was able to edit my grub file and that part is fixed so now I don't to manually edit grub every time - thanks.

I then typed the following:
```
sudo /etc/init.d/gdm start
```

After typing in my password the computer returned:
```
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start gdm

```

To which I typed:
```
sudo start gdm

```

The computer responded:
```
start: Job is already running: gdm
```

I will query about the graphics card next.

---

### Post by dondiego2 on 2010-10-24
> **kansasnoob said:**
> Ultimately it would be very helpful to know the specific graphics card info, so if you have some other, older Linux live disc that will run on that machine please post the output of:

```
lspci | grep VGA
```


The results of that command are:
```
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (re a2)
```

There is another character, it looks like, after the "re" at the end of the line but I couldn't tell what it was, maybe "v"?  The screen goes about 1mm more than my monitor shows and cuts off part of characters.

---

### Post by tommcd on 2010-10-24
To startx in Ubuntu these days run:
```
sudo service gdm start
```
It has been this way since 9.10 as far as I remember.
Your output of "*lspci | grep VGA*" indicates that you have the nvidia GForce 6150.
Did you install the nvidia driver in 10.04? 
If so, then how did you install it? Did you install the driver from the Ubuntu repos? Or did you install the driver from nvidia.com.
At this point it would also be helpful if you could post your */etc/X11/xorg.conf* file.

---

### Post by dondiego2 on 2010-10-24
> **tommcd said:**
> To startx in Ubuntu these days run:
```
sudo service gdm start
```It has been this way since 9.10 as far as I remember.
Your output of "*lspci | grep VGA*" indicates that you have the nvidia GForce 6150.
Did you install the nvidia driver in 10.04? 
If so, then how did you install it? Did you install the driver from the Ubuntu repos? Or did you install the driver from nvidia.com.
At this point it would also be helpful if you could post your */etc/X11/xorg.conf* file.


Yes I did install the nvidia driver in 10.04.  I did not go to nvidia.  I went to system/hardware and installed the recommended driver through there as far as I remember.  I know I did not do it manually.

How do I get the results of the /etc/X11/xorg.conf file?  I am not that skilled in the terminal.

---

### Post by dondiego2 on 2010-10-24
> **dondiego2 said:**
> Yes I did install the nvidia driver in 10.04.  I did not go to nvidia.  I went to system/hardware and installed the recommended driver through there as far as I remember.  I know I did not do it manually.

How do I get the results of the /etc/X11/xorg.conf file?  I am not that skilled in the terminal.


Or I guess the better question is how do I post the /etc/X11/xorg file?

I found it by using the ls command but I don't know haw to post it or even see what is in it.

---

### Post by dondiego2 on 2010-10-24
I saw this on another thread

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
#Flush Nvidia Drivers
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
#Restore OpenGL and Mesa Libs
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg 

Should I try this and see if it works or will it just mess things up?  Or should I just do a new install, this time wiping out my hard drive?

---

### Post by akand074 on 2010-10-24
> **dondiego2 said:**
> I saw this on another thread

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
#Flush Nvidia Drivers
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
#Restore OpenGL and Mesa Libs
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg 

Should I try this and see if it works or will it just mess things up?  Or should I just do a new install, this time wiping out my hard drive?

I would just do a clean install. Did you install it manually or did you let the auto-installer do it? If your installing Ubuntu on its own hard drive perhaps let the auto installer do it. Otherwise if your doing it manually make two partitions one the size of how much ram you have (set it as swap), and the rest in another partition (set that as Primary, EXT4, Beginning, Mount point "/" without the quotations). 

Should install everything fine and should be good to go. That's all I could suggest I don't know why it wouldn't work otherwise.

---

### Post by dondiego2 on 2010-10-24
I started over and did a clean install.

I let ubuntu use the whole ubuntu drive and let it rip.  I had to do F6 nomodeset to get it to run.  After it installed and it said reboot I got to the no grub prompt.  Rebooted and hit F1 to get into bios.  I thought maybe the drive boot order was wrong since I have 2 drives (XP and ubuntu).  So I switched the order and rebooted.  I had to hit "e" and edit the nomodeset command when I got to the grub screen.

Everything booted fine into the desktop this time.  I updated everything, edited the grub file to contain nomodeset and saved it.  Updated drivers that it asked me too (one was for nvidia).  So now I am up and running and will work on setting it up the way I want to in the next few days.

Thanks for your help.

---

### Post by tommcd on 2010-10-25
> **dondiego2 said:**
> 
How do I get the results of the /etc/X11/xorg.conf file?  I am not that skilled in the terminal.
To post the *etc/X11/xorg.conf* file, or any other file, simply run in the terminal:
```
less /etc/X11/xorg.conf
```
You can scroll through the less command with the arrow keys, or page through less with the Page_Up or Page_Down keys. Simply copy and paste the results (inside CODE tags if possible) here.
Then just type the letter "q" to quit out of less.

Glad you got this fixed. To make sure that the nvidia driver is running correctly, run this command:
```
glxinfo | grep -i render
```
It should report: *direct rendering: Yes*, along with your video card listed after: *OpenGL renderer string*. Like this:
```

tom[data]$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 

```

---

### Post by dondiego2 on 2010-10-26
> **tommcd said:**
> To post the *etc/X11/xorg.conf* file, or any other file, simply run in the terminal:
```
less /etc/X11/xorg.conf
```You can scroll through the less command with the arrow keys, or page through less with the Page_Up or Page_Down keys. Simply copy and paste the results (inside CODE tags if possible) here.
Then just type the letter "q" to quit out of less.

Glad you got this fixed. To make sure that the nvidia driver is running correctly, run this command:
```
glxinfo | grep -i render
```It should report: *direct rendering: Yes*, along with your video card listed after: *OpenGL renderer string*. Like this:
```

tom[data]$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 

```


[SIZE=2]Thanks a lot!  I was fumbling all over trying to find out how to look at file contents.  I uses "less" but not at the beginning of the line so I guess that was my problem.

I had to install [/SIZE]mesa-utils to get the glxinfo statement to work.  I guess it looked like a good thing to have so I installed it and ran it.  Here are the results:

```
direct rendering: Yes
OpenGL renderer string: GeForce 6150 LE/PCI/SSE2/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
```

Thanks again for your help.  I am happy and running ubuntu again.  Now I have weeks ahead of me playing with the settings and messing around.

---

### Post by tommcd on 2010-10-26
> **dondiego2 said:**
> 
I had to install *mesa-utils* to get the glxinfo statement to work.
I should have mentioned that you need *mesa-utils* to run *glxinfo*. Glad you found that. Your output from *glxinfo* looks good for direct rendering with the nvidia driver.
 You should also install **nvidia-settings** if you do not already have it. The nvidia-settings will allow you to run the nvidia driver GUI that will show you your settings and stuff.

You can also print the output of a file with the **cat** command like this:
```
cat /etc/X11/xorg.conf
```
I like using **less** though, since you can more easily scroll through large files with less than you can with cat.
Anyway, glad you got this fixed!

---

### Post by jhighley02 on 2011-02-18
> **dondiego2 said:**
> I started over and did a clean install.

I let ubuntu use the whole ubuntu drive and let it rip.  I had to do F6 nomodeset to get it to run.  After it installed and it said reboot I got to the no grub prompt.  Rebooted and hit F1 to get into bios.  I thought maybe the drive boot order was wrong since I have 2 drives (XP and ubuntu).  So I switched the order and rebooted.  I had to hit "e" and edit the nomodeset command when I got to the grub screen.

Everything booted fine into the desktop this time.  I updated everything, edited the grub file to contain nomodeset and saved it.  Updated drivers that it asked me too (one was for nvidia).  So now I am up and running and will work on setting it up the way I want to in the next few days.

Thanks for your help.

dondiego2,

How did you save the grub file that contains nomodeset? I am something of a newbie and thought I would ask. :)

---

