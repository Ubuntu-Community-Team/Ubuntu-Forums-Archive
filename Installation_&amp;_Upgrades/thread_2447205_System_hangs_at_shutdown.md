---
title: "System hangs at shutdown"
date: 2020-07-14
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2020-07-14
I bought a new (for me) Dell Optiplex 9020 with windows 10 installed.  I installed Xubuntu 16.04 form a CD I have,and then upgraded to 18.04.4. everything was working fine, but shutdown paused at the end.  I looked up this problem and follow instructions to fix this from this page:
[https://medium.com/@sbyang/slow-shut-down-of-ubuntu-18-04-e5fcc31255e2](https://medium.com/@sbyang/slow-shut-down-of-ubuntu-18-04-e5fcc31255e2) 

I did not take out the # sign at the beginning of the line--I'm not sure if I needed to do that. I changed
#DefaultTimeoutStopSec=90s to #DefaultTimeoutStopSec=4, and I also changed the line above it which I think was DefaultTimeoutstartSec=90s as well.  
I read at the top of the file, at that if I wanted to undo my changes I could delete the file and the defaults would be restored.  
I assumed that a new file identical to the original would be created in its place, but now there is no such file at  /etc/systemd/system.conf.  
When the shutdown finishes, the computer does nothing for a while then I start getting error:
revalidation failed (errno-5) and this goes on until I power off the system by holding the power button.  
I tried changing the file back to it's original state--no change
I tried deleting the file--no change.  of course i rebooted the system sever times in the process and since.

The last lines before the pause are:
[OK] Reached target shutdown
[OK] Reached target Final step
        Starting Power-off
After pause the first few lines are:
[] ata3.00 exception Emask 0x0 SAct 0x0 action 0x0 frozen
[] ata300 cmd a0/00:00:00:00:08 00/00:00:00:00:00:00/90 tag 27 pio 16392 in
               Get event status notification 4a 01 00 00 10 00 00 00 08 00 ics 40/00:00:00:00:00:/00 /100 Emask 0x4

There are a few more lines like this then the revalidation errors start.

How can I fix this and not have a delay in the shutdown/restart process?

Any help would be greatly appreciated,
Reuven

---

### Post by Impavidus on 2020-07-15
Two notes:
- You installed Xubuntu 16.04, which reached end of life already, but the parts it has in common with Ubuntu are still supported, so it still mostly works. Then you upgraded to 18.04 and within 9 months from now you'll have to upgrade to 20.04. If you had installed 20.04 directly, it would have saved you two release upgrades. I guess you didn't want to create a new live disk, but if facing the choice between creating a live disk and a double release upgrade, I wouldn't even consider that double release upgrade.
- Don't use **sudo gedit**, as used in that tutorial. It has nasty side effects, like leaving root-owned configuration files in your home directory, which can make it impossible to modify those files later as a normal user and can even prevent login. If you want to edit files with root permissions, use```
sudoedit [filename]
```sudoedit can be configured to use any text editor you like using the EDITOR environment variable. It defaults to nano.

During shutdown, it occasionally happens that some process doesn't terminate cleanly when it should. The shutdown process then waits for a timeout before killing the process. Normally it waits 90 seconds and that tutorial tells you how to change that to 5 seconds. Lines starting with # are comments, so to make the change work, you have to remove that #. When shutdown seems to hang, you can hit escape to close the splash screen and see the details. If it's waiting for a timeout, it should tell you.

I don't think the changes you made to /etc/systemd/system.conf did any changes to your shutdown process. If you want to retore the original file, you could reinstall systemd.

---

### Post by reut2 on 2020-07-15
Thank you for your response.  I usually open Thunar as super user and edit the files directly.  I did not have any blank disks around, so I used the one I had.  At this point, should I make a new 20.04 disk and reinstall or should I upgrade?
How do I reinstall systemd?  I tried 

reuven@reuven-OptiPlex-9020:/$ sudo apt-get install systemd

...

[B]systemd is already the newest version (237-3ubuntu10.41).
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.[/B]
reuven@reuven-OptiPlex-9020:/$

---

### Post by Impavidus on 2020-07-16
To reinstall a package that's already installed, use```
sudo apt install --reinstall [package]
```

Xubuntu 18.04 will be supported until somewhere in April next year, so there's no hurry to get to 20.04. The upgrade from 18.04 to 20.04 isn't officially released yet.

Live dvds are a bit old-fashioned. Only very old computers require them. I use a cheap 16GB usb drive (the smallest I could find) with the latest live system. I overwrite it twice a year. No more running out of blank disks. A usb drive is faster too.

I don't really use thunar. I manage my files from terminal. Thunar doesn't edit files, but it can open a text editor for you. I don't know how exactly thunar allows you to edit a file as root. As long as it doesn't involve typing **sudo [name_of_some_GUI_application]**, it's OK.

---

### Post by reut2 on 2020-07-20
I reinstalled systemd as you suggested, and have now rebooted a few times, and I still get the same hang at power off.  Attached is a screen shot of the readout I get.
The last time I tried to create a usb drive installer I had some issues--it was a long time ago, so I don't remember the details, but it was an old computer.  I will try again with my newer box.  

I do enter```
sudo thunar
``` then when I open a file from within Thunar I have root privileges, and can save it in the root file system.  I usually save the original, but in this case I did not--my bad. 

But I do wish there was a way to fix this problem (bug).

---

