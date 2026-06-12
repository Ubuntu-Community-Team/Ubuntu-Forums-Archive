---
title: "libv4l error"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by dbloco on 2012-07-15
Hi All

I upgraded to 12.04 and since I have this problem.  The login screen says INPUT NOT SUPPORTED and i get a blank screen.  I managed to get in somehow and setup a user with autologin and no password.  This made sure i can always get in.  Funnily enough, if I log out, I can see the login page fine and can login using ADMIN user or any other user.

After reading many posts, i realised that the problem is with my resolution, so i changed the resolution on the main page.  While trying to find a way to fix the resolution in the login page, i realised the error is somewhere else.  

If I run: ~$ xrandr -q    I get the following:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1368 x 768, maximum 1368 x 768
default connected 1368x768+0+0 0mm x 0mm
   1368x768       50.0* 
   1360x768       51.0     52.0     53.0  

So I assumed the problem is with the library, so using APTITUDE I updated libv4l-0 but still no luck.

I should started by saying I am new to all this, so it has been a rather steep learning curve.

Any assistance is most appreciated

---

### Post by dino99 on 2012-07-15
you can try to purge then reinstall this package (take care of the other packages removed, in case)

sudo apt-get purge libv4l
sudo apt-get install libv4l

sudo dpkg --configure -a

note: better to use apt-get than aptitude (uninstall it)

---

### Post by dbloco on 2012-07-15
Thanks dino99
I will take that into consideration for future. 

I found that LD_PRELOAD was looking at the wrong directory

opened terminal and typed:
~$ find /usr -name v4l1*
/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so

So the error was basically cause the command was missing i386-linux-gnu folder.

I changed this by opening Nautilus using terminal ~:sudo nautilus
This opens file manager and gives me the permissions necessary to change the file and its contents.

I changed the /etc/ld.so.preload file contents to point to the right location simply by using Text Editor

Once I saved it - it got rid of the library issue.

---

### Post by dino99 on 2012-07-15
Glad you have solved your issue, then please mark this thread as SOLVED, using the top right "thread tools" icon

---

### Post by dbloco on 2012-07-15
Hi dinno99

Unfortunately this hasn't solved my problem

It removed the line about the library but still got the error on the login page. No input support.

It now appears to be the driver.  I did a check.  It gives me two options.  If I choose the recommended, it ends up with a driver that doesn;t support 3D, so most functionality is lost.  If i choose the not recommended, the interface is as expected.  Either way I get the Input Not Support

I am now lost :s  does this mean i need a better graphics card?  I got a GeForce 7025 integrated :(

---

