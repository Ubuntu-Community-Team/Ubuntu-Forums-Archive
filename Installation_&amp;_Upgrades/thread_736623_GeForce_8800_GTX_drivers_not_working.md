---
title: "GeForce 8800 GTX drivers not working"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by UnfetteredVagary on 2008-03-26
I've been trying for about a week to install the proper driver for this card in ubuntu. For the record the card i have is pictured [here]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2824923&CatId=2513")

the driver I installed can be found [here]("http://www.nvidia.com/object/linux_display_ia32_171.06.html")

I'm running ubuntu 7.10 and have installed all the current updates

sudo apt-get install module-assistant gcc nvidia-kernel-common
sudo m-a update 
sudo m-a prepare
m-a auto-install nvidia

Ctrl + Alt + F1
sudo /etc/init.d/gdm stop
cd /home/[MYUSER]/Desktop/

sudo sh NVIDIA-Linux-x86-171.06-pkg1.run
sudo reboot

Even after this, Each time i boot it tells me i have to boot in low graphics mode.
If anyone can lend me some insight it would be very helpful.

---

### Post by Pumalite on 2008-03-26
Why not this:?
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

---

### Post by Pumalite on 2008-03-26
Are you running 32 bit or 64 bit?

---

### Post by UnfetteredVagary on 2008-03-26
I'm running 32 bit sorry i forgot to mention that.

And i tried to run with the other driver and still no luck.

---

### Post by WoosterB on 2008-03-26
I have the same problem....Just watching =)

I've heard that envy will install it perfectly....but envy doesn't run for me and I'm currently chasing this down.  

-W

---

### Post by UnfetteredVagary on 2008-03-26
I just ran 

sudo nvidia-xconfig

and then restarted

when i run 
sudo nvidia-settings
it tells me  that i am not using the nvidia x driver

---

### Post by Pumalite on 2008-03-26
Install through Virtual Terminal:
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
password
sudo sh /path/to/driver/NVIDIAxxxxx.run
Accept License
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then: startx

---

### Post by WoosterB on 2008-03-26
THanks Pumalite.  I got most of the way through when an error message popped up.
Apparently I need a development library and when I went to find it, I found that there were several to choose from with a similar name/use.  I've included the error log file.  Are you familiar with the particular one I need or do I need to make an educated guess?

  Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.

Edit: I apologize Vagary if I hijack, I just have the same issue.

---

### Post by Pumalite on 2008-03-26
sudo aptitude install build-essential

---

### Post by UnfetteredVagary on 2008-03-26
I followed the instructions, and i still had no luck

when i restarted X (with startx) it failed telling me no screens found

---

### Post by CaesarLike on 2008-03-26
Try this post.  Its how I got a new 8800GT to work.

[http://ubuntuforums.org/showthread.php?t=684424](http://ubuntuforums.org/showthread.php?t=684424)

---

### Post by WoosterB on 2008-03-26
Well, everything seemed to install ok, however upon reboot I got an error message that I do not have display config-gtk and that I would have to modify my config file manually.  It then goes into a black screen for a good period of time.

I've restarted in safe mode and can get to a command prompt.  

I'll try to re-install and see if I can't pull the rabbit from the hat.

-W

---

### Post by UnfetteredVagary on 2008-03-26
Aye, i've decided to reinstall and try from scratch as well

---

### Post by WoosterB on 2008-03-26
Erm...off topic question Vagary, but how does one re-install while keeping the same partition?  Before I try and manage to destroy all life on my HD?  

There is a post here about this, but no response from anyone...so I'm waiting patiently to see if someone does.

-W

---

### Post by dconnors on 2008-03-27
> **UnfetteredVagary said:**
> Aye, i've decided to reinstall and try from scratch as well

Ok.. in the same thread I have a 

quad core 3ghz, 8 gig of ram, nvidia 8800 gtx, 1 320 gig seagate barracuda partitioned into two

with vista 64 home premium on the c drive.. and second 1 tb for a data drive. 

i tried installing ubuntu, for 64 bit, off 64 bit live cd and it hangs with a black screen before it even gets to the desktop. 

anyone have any suggestions? 


thanks!

---

### Post by WoosterB on 2008-03-27
Did you make sure you added "noapic" to the end of the command line (F6)?

For some reason my graphics need that added piece before they will go into the live desktop environ

Thats the only thing I can think of off the top of my head.

-W

---

### Post by dconnors on 2008-03-27
yep I tried adding noapic and no luck..

---

### Post by WoosterB on 2008-03-27
Have you also tried just the regular ol' 32 bit download just to make sure?  

Also, (and I'm sure you've done this I'm just covering the bases) make sure you do a disk check.  I had a file go bad in the burn process.

-W

---

### Post by UnfetteredVagary on 2008-03-27
It seems I've got my graphic drivers to work after using envy, twice (the  first time really screwed things up)

but now I'm getting a resolution problem, 

namely that my resolution is bigger than my monitor.

My computer is hooked into a 42 in sharp aquos lcd tv.

I can't actually get to any of the drop downs at the top of the screen, so is there a way i can fix my resolution from the command line?

---

### Post by WoosterB on 2008-03-27
Vagary, try to see if there is a desktop setting that you can get to show those tabs.

I finally got the thing to work with Envy (thanks) and I'm using a 19" widescreen and things came out ok.  

Now for the soundcard.....


-W

---

