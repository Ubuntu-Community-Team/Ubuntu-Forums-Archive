---
title: "Exasperation over Nvidia Kernel, Driver Install..."
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by casparov on 2010-06-14
Hi Everyone...  

I got into this mess myself by trying to create a work-around to a known bug in Ubuntu, one that allows the DVD drive to disappear from the PC's devices and results in much frustration.  [http://ubuntuforums.org/showthread.php?p=9444186#post9444186](http://ubuntuforums.org/showthread.php?p=9444186#post9444186) 

I was advised to install a newer kernel (26.6.34), which had solved this problem.  I did this (though it didn't solve that particular problem, entirely) but lost my Nvidia driver function and am now left in low graphics mode, w/ no NVIDIA driver installed.  (I know the Preferences-->Appearance-->Visual Effects routine, which only created a loop of failure, as the driver wouldn't be loaded, and, after restart, the message was that Normal and Extra desktop effects were not available.)  

I have downloaded the most recent driver from the NVIDIA site (NVIDIA-Linux-x86-195.36.24-pkg1.run), but it will not install due to an inability to stop X-server.  (I have tried to do this, but I get the same error--that X-server is still active--no matter what I do).

Does anyone have any idea how I can get Desktop effects back?  Do I keep X-server installed?  Is it necessary on a PC that isn't networked?  The low-graphics mode warning indicates that there is no NVIDIA kernel installed.  Does anyone know how I go about installing that, if necessary?  Will installation of the NVIDIA driver fix everything?  I am completely lost and have spent hours and hours on failed attempts-it has consumed much of my recent free time.
:confused: 

On the upside, those trying to help have tried v. hard and donated their valuable time on this forum, and, from their efforts, I have learned a lot.  It's just that I have lost a lot of function and wish I had never tried to fix the original bug.

Any help would be greatly appreciated.

Thanks for reading,    C.

---

### Post by davidmohammed on 2010-06-14
casparov - does this [how to ]("http://ubuntuforums.org/showthread.php?t=1467074")help?

also, just to check you have the headers installed, please dump the contents here of

ls /usr/src

and

echo `uname -r`

---

### Post by casparov on 2010-06-15
David!!

It's nice to see you again--I though that I had exhausted your patience.:p  (And you would be entitled to that.)

Okay, here is the latest terminal output for the headers: 

 whit@whit-desktop:~$ ls /usr/src
linux-headers-2.6.32-21          linux-headers-2.6.32-22-generic
linux-headers-2.6.32-21-generic  nvidia-current-195.36.15
linux-headers-2.6.32-22
whit@whit-desktop:~$ echo 'uname -r'
uname -r
whit@whit-desktop:~$ 
whit@whit-desktop:~$ 


I didn't see anything from the *.34 kernel, but, then again, I don't know what to look for, either.  

I did a decent perusal of your link and read every page of it.  I am a bit guarded about trying it because I have no printer and don't know much about redirecting to different folders within terminal (and don't know how to get to terminal w/o a graphical interface).

But, for now (and I may have to face the bottomless pit of running a console to fix that), I have followed the following instruction to install a .run, and that is how I got to the X Server problem, regarding its not being shutdown: 

1. Open a terminal. In Gnome the terminal is found in Applications>Accessories>Terminal.
2. Navigate to the directory of the .run file. For this example, I have mine on the desktop so I would type in "cd ~/Desktop" and press enter.
3. Type "chmod +x example.run" (press enter).
4. Now type "./example.run", press enter, and the installer will run.

Now, pertaining to Item 4, above, the installer does run but is ultimately defeated by the X Server bit.  

Another link says to do this to stop X Server: 

sudo /etc/init.d/gdm stop

Now, would the last command put me into a black screen, and, if so, how do I get to Terminal/Console? [UPDATE: upon running this last command, the PC switched to an unresponsive black screen w/ a shimmering band of green (about 2 in. wide) at the top.  Upon killing the PC, it rebooted into low graphics mode w/ the associated options.]   

Anyway, that is where I am--the headers don't appear to reference the *.34 Kernel, and I am not sure what to do about navigating Terminal w/o Gnome.  (I wouldn't mind experimenting if a reboot after some problem would give me the option of low graphics mode again--at least I would have the PC back.  I just don't want to face a situation where I have no PC at all.)  

David, I hope my blather made some sense... 

Thanks so much again,   C.

---

### Post by Xgen on 2010-06-15
Maybe I am missing something...but I am running Lucid with the 173 nvidia driver and the 34 and 35 kernels. I install the propriety driver by going to a tty prompt (Control|Alt|F2 to F6) and stop the service with: "sudo service gdm stop" then install the driver. If not, then restart in recovery mode of the kernel that you wish to install.

---

### Post by davidmohammed on 2010-06-15
Hi Casparov - from the /usr/src it doesnt appear that you've got the .34 kernel header files installed.  That is most likely the key reason why your graphical issues exist.  NVIDIA - whether the downloaded version, or the version activated through the Hardware Drivers window needs those header files to compile against.

From the previous thread I asked the following question:

"question for you: did you install both of the "<header>.deb" packages when you installed the kernel? i.e. the package names that has "header" somewhere in the file names

e.g. for a intel processor did you download and install the following packages

linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38 675K 
linux-headers-2.6.34-020634_2.6.34-020634_all.deb 17-May-2010 20:27 9.6M 
linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb "

Can you confirm whether those two header deb packages have been installed - when installed they should have created directories under /usr/src.


I suspect when you see those .34 /usr/src directories, you should be able to activate your nvidia graphics through hardware-drivers. :p

don't worry about being left without graphics...
To get back to a graphical desktop, boot using recovery to a terminal.

type 

sudo nano /etc/modprobe.d/blacklist.conf

delete those blacklist items you have added.

sudo apt-get install nvidia-current
sudo modprobe nvidia-current

reboot.

---

### Post by casparov on 2010-06-16
David... 

Thank-you so much for the information...

Those header packages are, definitely, not installed--only *.32 series kernel headers are installed.  

Could you please tell me where, and how, to go about installing the headers you indicated?

I must apologize for the painstaking walk-through that I always require--my only hope is that this will help many others along the way.  

All Regards,   C.

---

### Post by dino99 on 2010-06-16
synaptic is your boy

---

### Post by davidmohammed on 2010-06-16
given that you've installed the mainline .34 kernel - it will not be in synaptic:p

However its quite easy to download:

go to this [site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/")

now download the following links:
 linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38  675K 
 linux-headers-2.6.34-020634_2.6.34-020634_all.deb 17-May-2010 20:27  9.6M 
 linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38  30M 

check they have downloaded to your Downloads folder

then

cd Downloads
ls *.deb  --> should list the 3 files above
sudo dpkg -i *.deb --> this will install all three deb files

if you see any errors being reported then the install hasn't worked.

reboot

hopefully you will now see headers in /usr/src

---

### Post by casparov on 2010-06-17
OMG!!!   IT WORKED!!!   YOU DID IT!!!!!!!!!!!!!!  

David...  

I can't thank you enough for all of your help.  Somehow, magically, your direction got everything worked around--even the DVD drives are behaving (for now)!!!!!!!!!!!  

(I really think that England could use your header management in the WC--they've really got to get something going in the box next time around.) 

Now, Linux is running better than ever.  I have just purchased a couple of Ubuntu/Linux texts because I really, really need a bootcamp in this system.  I am very, very flabby--most unfit and driving lots of people--like you--crazy.

Anyway, thanks so much again--I hope we don't have to meet under these terms again very soon.  

All Regards,   C.

---

### Post by davidmohammed on 2010-06-17
casparov - you are more than welcome.  

Please mark this thread (and the other as well) as solved.  TIA

---

