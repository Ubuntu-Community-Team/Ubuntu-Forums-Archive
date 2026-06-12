---
title: "Can't install 6.10 -- x-server problem!"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by camerong on 2007-01-08
**UPDATE:**

the problem is no longer " no screens found ", but is instead:
> AddScreen/ScreenInit failed for driver 0

XIO: fatal error 104 (connection reset by peer) [... and then some other stats were here, but they were all 0 and seemed relatively trivial]
And my device is set to "vesa". I am using a non-custom dell xps 400.. all factory built.

i'd appreciate any help on this issue.. I woulda thought setting up would be easier!

my original post ensues:
-----------------

Hey,

I have 6.10 burnt to a cd. I md5checksum'd it, integrity checked it, and pretty much just made sure it was a good copy. It was. (and is)

Then I booted off it and got to a screen with several options of what to do next. I ran the memory checks, etc, before proceeding. I then attempted an installation, which was the first item on the menu.

The installation loads, then goes to a black screen, which then comes back several seconds later with a bunch of seemingly-random characters forming a window and an error message letting me know that my xserver isn't working. 

I then found this thread: [http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177) , but can't use "Recovery" because ubuntu is not installed yet, which is the very problem.

I tried it in various vga settings and with safe graphics, to no avail.

I'm sure I'm missing something, so if anyone could point out just what it is, I would be very thankful.

Thanks in advance,

Cameron

EDIT:

> it is notable that the exact error is that i have "no screens"

---

### Post by taurus on 2007-01-08
Why not use the alternate CD to install it on your machine.  It doesn't require you to boot into LiveCD first before you can click an icon to install it.  You install it right away at the boot screen.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by camerong on 2007-01-08
will it work, do you think? or will i be downlading and burning something just to watch it not work again...?

il download and burn it pronto if u think it will work, thanks.

---

### Post by taurus on 2007-01-08
I can't guarantee if the alternate CD works or not on your machine.  You just have to try it out then.  However, I have never failed to install Ubuntu on all the machines with the alternate CD.  ;)

---

### Post by triplenine on 2007-01-10
Is there any known fix to this other than the cd? I am having the same problem and just wondering if there is an answer.

---

### Post by rev_b on 2007-01-10
Try this if after the error you are back to a command promp. Type:

sudo nano /etc/X11/xorg.conf

Find Section "Device", and change Driver to "vesa". Follow the screen instructions to save the file and exit. Type:

 startx 

Let us know if that works.

---

### Post by camerong on 2007-01-10
alternative cd yeilds same problem, but i now have ubuntu linux completely set up except fort this xserver no screens issue.

rev_b, noope , didn't work.. but thanks.

---

### Post by camerong on 2007-01-10
oh and by the way im running a completely uncustomized dell xps 400

EDIT: we're getting closer!! (i think)

> AddScreen/ScreenInit failed for driver 0

XIO: fatal error 104 (connection reset by peer) [... and then some other stats were here, but they were all 0 and seemed relatively trivial]

this is using device: "vesa" .. so it found the screens! no more "no screens found" error!

---

### Post by camerong on 2007-01-10
anyone have any idea what the remaining problem's solution is?

---

### Post by taurus on 2007-01-10
Get to a console, <Ctrl><Alt>F2, and log in with your name and password.  Then, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by usererror on 2007-01-10
What is your video card on the machine you are trying to install to?  I have an ATI X600 at work which caused me this headache of 'no screens found'

More than likely the CD doesn't have drivers for your video card, after you go through and it 'fails'...you should be able to press CTRL + ALT + F4 and go a command prompt...

this was my solution:

[http://www.ubuntuforums.org/showthread.php?t=299410](http://www.ubuntuforums.org/showthread.php?t=299410)

Good luck!

---

### Post by camerong on 2007-01-10
thanks

ive done that a couple times the main problem is i dont know what my driver is for the xps 400...?

i'll just go down the list and try a bunch of likely ones i guess... thanks

EDIT: oops didnt see usererror's res[ponse.. il try that now.

EDIT2: how do i install the "xorg-driver-fglrx" package?? i have no internet connection btw and am booting from alternative cd.

---

### Post by camerong on 2007-01-10
my problem is no longer that it can't find screens, it's

> AddScreen/ScreenInit failed for driver 0

XIO: fatal error 104 (connection reset by peer) [... and then some other stats were here, but they were all 0 and seemed relatively trivial]

and taurus i tried that again to no avail..

---

### Post by camerong on 2007-01-11
Has anyone ever had this problem before? Does anyone have any idea how to fix it?

I'm about to give up on ubuntu... :mad: :confused:

---

### Post by triplenine on 2007-01-12
So yeah. I am at the same point as well. I used the alt CD and no dice. I am going to try some of these ideas. I am installing on a Dell E1405 with an Intel integrated vid card. I am concerned about the wireless functionality but one step at a time. :confused:

---

### Post by triplenine on 2007-01-17
Cool, I recon'd the X-server and it worked. Nice, yet now I have to do this all over since I neglected to remember my uid and pword between the time that I set it up and when I got it running. Duh. This will give me a chance to try this without the alt CD.

---

### Post by taurus on 2007-01-17
That's real easy to fix.  Boot into recovery mode from GRUB and at the prompt, see what is your username from this command.

```
ls -la /home
```
Assuming it's called **triplenine**, just change the password with

```
passwd **triplenine**
shutdown -r now
```

---

