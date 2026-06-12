---
title: "No keyboard and mouse input when xorg has started(?!)"
date: 2009-06-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by skbftw on 2009-06-21
Hello, since I couldn't find anything useful on web I've decided to post here about my lovely (as always) ubuntu upgrade. The thing is that the whole upgrade went smoothly but after reboot I've lost my mouse and keyboard in gdm. (even ctrl+alt+f1 doesn't work) Later, I went to root shell in recovery mode and started X from there and it still didn't help. The problem is that I am not experienced in bug catching so I am asking whether anyone could help me sorting out this issue. The system is up-to-date though :D.
By the way, "dpkg-reconfigure xserver-xorg" didn't help either. Any suggestions? 

P.S. I don't want to lose my data on the hard drive.

---

### Post by douham on 2009-06-21
> **skbftw said:**
> Hello, since I couldn't find anything useful on web I've decided to post here about my lovely (as always) ubuntu upgrade.

P.S. I don't want to lose my data on the hard drive.


Hi skbftw, can you tell me what version of Ubuntu did you upgrade to and what version did you upgrade from please?
 If you upgraded to ubuntu 9.10 this is a testing release. 

Any way, are you using a cordless mouse and keyboard. If so try using a ps/2 or usb mouse and k/b 
It' always a good idea to back up your data before upgrading Ubuntu.

---

### Post by skbftw on 2009-06-22
I upgraded my distro from 9.04 to 9.10A2
The thing is that I'm using ps/2 mouse and keyboard (usb doesn't work either). For some reason I can't find any errors in logs or maybe I don't know what to look for :|

EDIT: wait, maybe this is the problem ? "(EE) config/hal: couldn't initialise context: (null) ((null))"

---

### Post by Zorael on 2009-06-22
I'd try reconfiguring hal.
```
$ sudo dpkg-reconfigure hal
```

---

### Post by Polaris96 on 2009-06-22
you can try reconfiguring X11 also:

sudo X --configure

---

### Post by jerrylamos on 2009-06-23
On my Thinkpad T40 the USB mouse and USB keyboard are disabled with normal boot.

Boot in recovery mode and just select "continue" works O.K.

Another thing to try is remove "quiet splash" from the line that starts with linux.  Someplace in the forums someone said that worked for them.  I just tried it and it worked on the T40.

For karmic to make the fix permanent do 
sudo chmod 644 /boot/grub/grub.cfg
sudo gedit /boot/grub/grub.cfg
remove quiet splash from the line that starts with linux

Another way may be to 
sudo gedit /etc/default/grub
and remove quiet splash there,
then do
sudo update-grub

Lately boot has been taking 10 or 20 seconds so I don't really care what it is displaying with splash or whether lines scroll by.

Good luck on karmic Grub2 !!

Jerry

Good luck, Jerry

---

### Post by taavikko on 2009-06-23
@jerrylamos, I fail to see how "quiet splash" could be responsible for this input failure.
quiet just suppress messages and splash is self explanatory...

I might lose usb-mouse input when I start openGL application, but it's restored as soon as the application has been terminated.

---

### Post by skbftw on 2009-06-24
> **Zorael said:**
> I'd try reconfiguring hal.
```
$ sudo dpkg-reconfigure hal
```
Reconfiguring didn't help. Also in the end of configuring I get:```
invoke-rc.d:  init script hal, action "start" failed.
```X --configure says : "unrecognized option --configure". Maybe update manager removed one package too many/less? I think soon I'll have to borrow hdd from a friend of mine because nothing helps :|

---

### Post by Zorael on 2009-06-24
> **skbftw said:**
> Reconfiguring didn't help. Also in the end of configuring I get:```
invoke-rc.d:  init script hal, action "start" failed.
```X --configure says : "unrecognized option --configure". Maybe update manager removed one package too many/less? I think soon I'll have to borrow hdd from a friend of mine because nothing helps :|
Hum.
```
$ sudo aptitude reinstall hal
```

---

### Post by skbftw on 2009-06-25
> **Zorael said:**
> Hum.
```
$ sudo aptitude reinstall hal
```
Reinstall fails.
```

Setting up hal (0.5.12+git20090512-0ubuntu3) ... 
 * Reloading system message bus config...      [ OK ] 
 * Starting Hardware abstraction layer hald
invoke-rc.d: initscript hal, action "start" failed. 
dpkg: error processing hal (--configure): 
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing: 
 hal
``` I guess hal doesn't start at all because "/etc/init.d/hal start" does nothing.
What if I purged hal and reinstalled everything manually? Am I likely to end up like this?

---

### Post by Zorael on 2009-06-25
> **skbftw said:**
> Reinstall fails.
```

Setting up hal (0.5.12+git20090512-0ubuntu3) ... 
 * Reloading system message bus config...      [ OK ] 
 * Starting Hardware abstraction layer hald
invoke-rc.d: initscript hal, action "start" failed. 
dpkg: error processing hal (--configure): 
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing: 
 hal
``` I guess hal doesn't start at all because "/etc/init.d/hal start" does nothing.
What if I purged hal and reinstalled everything manually? Am I likely to end up like this?
Before you do that, try the following.
```
$ hald --verbose=yes
```
It'd help if it actually said *why* it failed. ;/

---

### Post by skbftw on 2009-06-26
> **Zorael said:**
> Before you do that, try the following.
```
$ hald --verbose=yes
```It'd help if it actually said *why* it failed. ;/
Thanks for you help. :)  I realized that I haven't tried recompiling hal. Problem is solved but I had to recompile 
hal , glib2.0, and policykit.

---

### Post by bsm1th on 2009-08-21
This happened to me recently and this is what I did..

First, no keyboard or mouse only in X
After googling a bit, I found that hal could be the problem
Start the recovery kernel on the hard drive and use the root shell option

Did a 'ps -ef | grep hal' - nothing there, so..

Tried '/etc/rc5.d/S24hal start' and got this message
   Can't start Hardware Abstraction Layer - please ensure dbus is running

Next was 'ps -ef | grep dbus' - nothing there..

Lets try '/etc/rc5.d/S12dbus start' then
         '/etc/rc5.d/S24hal start'
         'startx'

X is back - not sure why this happened, though. Those scripts should be running at each boot.


Bob

---

### Post by alextud on 2009-08-21
This does the trick for me:
  sudo service dbus restart
  sudo service gdm restart

---

### Post by edvar on 2009-09-30
It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!

---

