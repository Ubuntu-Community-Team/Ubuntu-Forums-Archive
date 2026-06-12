---
title: "Can no longer log in after update"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by TheHow7zer on 2011-02-28
I am having a problem with the latest update of lucid ubuntu. I was on 10.04 for the longest time but decided to update while I was out doing errands. When I got back the logon screen was made up of blue and gray windows on a completely black background and the mouse and keyboard wouldn't work! 

I found that if I unplugged and then replugged my mouse that I could get it working, but not all the options work properly. When you try to close a menu it just stays up, but it isn't there at the same time. Also, the shutdown/restart options don't work along with the physical power button on my computer, I have to remove the battery and power cord to shut it down.

I am currently dual booting ubuntu and windows 7 on my gateway NV59 laptop.

Any help would be greatly appreciated.

~Jacob

---

### Post by runeh76 on 2011-02-28
Hi

I dunno what have went wrong, but u should use another account. Not only that what came after Ubuntu installation.

Now u could boot to recovery-mode (reboot and hit **esc** or **shift**, so u can choose recovery mode--> ROOT terminal and add new user-account

```
useradd test
```
```
passwd test
```

edit login settings, so "test" login is automatic
```
gksudo gedit /etc/gdm/custom.conf
```
at least u should now can login to "test" account.

---

### Post by TheHow7zer on 2011-02-28
yeah, I already tried recovery mode but the keyboard doesn't work there either. 

I have important stuff on my ubuntu account that I need to recover, Help!

---

### Post by runeh76 on 2011-03-01
Use LiveCD

---

### Post by colintivy on 2011-03-01
Hi folks!

I have a similar problem in that I have upgraded 9.10 using the facility in Update Manager. This appeared to go well(eventually)  but when I get to Log-in it accepts my username and password (as used in 9.10, no authenticate faiure), there is some disk activity but it then goes back to the log-in page. Using the Gnome Failsafe option I have looked into the custom.config file but there is nothing in it. 10.04.2 sort of works but, because of the means of not requiring logging-in, it is sluggish (Just like Safe mode in Windows). Clearly there is bug somewhere in the loading software that returns mw to the log-in page instead of finishing the loading. I have posted this earlier but found this as a likely alternative source of guidance.

---

### Post by runeh76 on 2011-03-01
Hi colintivy  :)

I have seen lots of these upgrade problems, and i think its better just make a nice clean install with LiveCD. Backup stuff and enjoy ur new clean OS.  :)

---

### Post by TheHow7zer on 2011-03-01
> **runeh76 said:**
> Use LiveCD
is there any way for me to use my liveCD to login to my account on ubuntu?

---

### Post by colintivy on 2011-03-03
Hi runeh76!

Advice taken, Ordered a 10.04 Desktop CD, our download speed a bit dodgy these days and extra GBs a bit expensive. I hope to be able to report that all is well soon. I had not heard of Gnome failsafe facility before but It sure got me out of a hole. Has it been written up somewhere? It seems to work OK but I have not explored its limitations. I do know about Windows Safe Mode and used it (washes mouth out!!) Will change my profile asap!

 :D :D

---

### Post by runeh76 on 2011-03-04
> **colintivy said:**
> 
 I do know about Windows Safe Mode and used it (washes mouth out!!) 
 :D :D

:lolflag:

---

### Post by TheHow7zer on 2011-03-06
I am able to access everything in all of my partitions accept for my user folder (which I have been told is encrypted), is there a way to access it from the livecd? If so I could use that to save my information, right?

---

### Post by xx58 on 2011-03-06
:rolleyes:    	 	 	 	p { margin-bottom: 0.08in; }h2 { margin-bottom: 0.08in; }h3 { margin-bottom: 0.08in; }a:link {  }  **Recover Grub 2 via LiveCD**

 
[LIST]
[*] 	First, grab a copy of the latest [Ubuntu 	LiveCD]("http://www.ubuntu.com/getubuntu/download") and boot it.  	
[*]Open a terminal and type  	
[/LIST]
 $ sudo fdisk -l  
 
[LIST]
[*]Now, you need to remember 	which device listed is your linux distribution, for reference, 	/dev/sda1 will be used. Now we need to mount the filesystem to /mnt  	
[/LIST]
 $ sudo mount /dev/sda1 /mnt  
 
[LIST]
[*]If you have /boot on a 	separate partition, that need's to be mounted aswell. For reference, 	/dev/sda2 will be used.  	
[/LIST]
 $ sudo mount /dev/sda2 /mnt/boot *Make sure you don't mix these up, pay attention to the output of FDISK*  
 
[LIST]
[*]Now mount the rest of your 	devices  	
[/LIST]
 $ sudo mount --bind /dev /mnt/dev  
 
[LIST]
[*]Now chroot into your system  	
[/LIST]
 $ sudo chroot /mnt  
 You should be chroot'd into your system as root, you can now run commands as root, without the need for sudo.  
 
[LIST]
[*]Now you need to edit 	the **/etc/default/grub** 	file to fit your system  	
[/LIST]
 $ nano /etc/default/grub  
 
[LIST]
[*]When that is done you 	need to run **update-grub** 	to create the configuration file.  	
[/LIST]
 $ update-grub  
 
[LIST]
[*]To install GRUB 2 to 	the MBR, next you need to run **grub-install 	/dev/sda**  	
[/LIST]
 $ grub-install /dev/sda  
 
[LIST]
[*]If you encounter any 	errors, try **grub-install --recheck 	/dev/sda**  	
[/LIST]
 $ grub-install --recheck /dev/sda  
 
[LIST]
[*]Press 	Ctrl+D to exit out of the chroot.  	
[*]Once you exit back to your 	regular console, undo all the mounting, first the /dev  	
[/LIST]
 $ sudo umount /mnt/dev  
 
[LIST]
[*]Now you can unmount the root 	system  	
[/LIST]
 $ sudo umount /mnt  
 
[LIST]
[*]And 	you should be free to restart your system right into GRUB 2 and then 	into your system installation.  	
[/LIST]
 **Errors**

 ** Where did my Grub2 boot menu go!?!?!**

  According to an email that was sent out today Monday, August 10, 2009 with the newest Grub2 update, the boot menu is hidden by default now. It's easy to get it back, just edit **/etc/default/grub** and comment out **GRUB_HIDDEN_TIMEOUT**  
 $ sudo nano /etc/default/grub  Make your timeout line look like this...  
 #GRUB_HIDDEN_TIMEOUT=3 GRUB_TIMEOUT=XXX        <---Make sure you put in a timeout value here.  Save the file and exit, then run...  
 $ sudo update-grub

---

