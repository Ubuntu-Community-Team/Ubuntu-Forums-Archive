---
title: "Ati X700 Screen Black out"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by herroyuy on 2006-10-08
Dear all,

I'm a beginner in linux. I've downloaded Ubuntu 6.06 desktop 1386. when i try to install ubuntu.. i always end up in black screen after starting acpi and hp printing service. i can hear the startup sound tho... just no screen.

i booted using the following command:

live noapic nolapic

if i dun include noapic and nolapic. i can't even hear the startup sound. i also tried

live vga=safe noapic nolapic
live vga=771 noapic nolapic

still doesn't help.

when i use live vga=safe noapic nolapic i saw some i/o error on device hdb, logical block 178793

i've searched the forum... some having the same problem as me as they are having ATI Mobility Radeon X700 like i am... they mentioned start ubuntu in graphic safe mode... how to do that? i dun see that option in F1 Help index... please advice

thanks!

---

### Post by UKHack on 2006-10-09
Hi,

You mentioned you are using the ATI X700 card - what laptop are you using it in?

I had a similar problem on my Acer Ferrar 4002 laptop. It's down to the displays getting mixed up.

You may want to try editing your xorg.conf file (use Ctrl Alt F1 to get to a console and type sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old to make a backup.

Then type sudo vi /etc/X11/xorg.conf). Press the Insert key on your keyboard so you can edit the file and scroll down to the "Device" section

Add the following lines to the "Device" section:

```
Option   "CRT2Position" "clone"
Option   "MonitorLayout"  "LVDS, CRT"
```

Hit the Escape key and press :wq and enter to save the file.

Now switch back to the X window by pressing Ctrl Alt F7 and then press Ctrl-Alt-Backspace to restart X. Hopefully you should be greeted by the login screen. If you are running the Live CD then just press enter here.

If you need to restore your original xorg.conf file then when you are at the terminal type sudo cp /etc/X11/xorg.conf.

Hope this helps,

Andrew

---

### Post by herroyuy on 2006-10-10
i'm on acer aspire 5504WXMi

thanks for ur advice
i shall try that next time..

does it mean that as long as i can reach the isntallation part and in the case that it installed properly.. the screen blank out prob won't come again?

---

### Post by Groovie on 2006-10-10
Hi.
I have been troubling with the same thing myself. The easiest way to awoyd it is using an external screen when installing the system.
Then when you are finished, reboot.. Go to "Synaptic start senter" update it. Search for fglrx download the controller install and use. Now when it is finished downloading go to console and type: 
"sudo nano -w /etc/X11/xorg.conf"
Now you are in your xorg config file. 
Press ctrl-w and search for "radeon"
Now you can se a line that says "driver" it is probably "ati" that is the cosen driver. Change it to "fglrx"
press ctrl-o and save to the same name.
Now just do a ctrl-alt-backspace and you have visual on your laptop screen.

If you do not have a external screen at your disposal, you can press ctrl-alt-F1 and get up console.
Type: sudo apt-get update
sudo apt-get install xorg-driver-fglrx
"sudo nano -w /etc/X11/xorg.conf"
Now you are in your xorg config file. 
Press ctrl-w and search for "radeon"
Now you can se a line that says "driver" it is probably "ati" that is the cosen driver. Change it to "fglrx".
Now comes the part I am not sure of, but some say you are suposed to type: killall gdm
gdm

But that dint work for me..
I typed: startx
Then I get a message to delet a tmp file .. do so using sudo rm and the filepath.
startx again.

The last option requires that you download the driver again after the install is complete.

Hope it was of help. :)

---

### Post by jazzroy on 2006-10-10
I have a X700 too on my Asus Laptop and I had the same issue.

Here is how I easily solved it:

When you install use the safe graphic mode it will configure xorg to VESA driver, it will work. That's important because Ubunt installation if detects a X700 sets up the "Ati" driver, which is responsible of the black scren.

So, after a clear install with safe graphic (or, if you have already installed, edit your xorg.conf in another session - try CTRL+Fn keys -  and change "Ati" to "vesa" and restart X) all you have to do is to install the "fglrx" driver (through synaptic - follow the wiki doc) and it will work like a charm.

---

### Post by herroyuy on 2006-10-10
thanks a lot for the tutorial.. i tried andrew's method... but i got a reply of can't stat '/etc/x11/xorg.conf' directory or file not found

streange... thanks a lot... i shall try now again and see..

---

### Post by herroyuy on 2006-10-10
but then even when i try to backup the xorg.conf it says no such file... now is it possible to edit it?? btw.. i'm booting from live cd... any advice?

---

### Post by jrohde on 2006-10-26
Hi,

I guess you have found out by now, but - just in case:

Remember, that Linux' file system is case sensitive. It is /etc/X11 (not /etc/x11).

That should do it.

Jakob

---

### Post by Arcadio on 2006-10-26
I just have experienced the same problem with another X700 card using Ubuntu 6.10.

---

### Post by Franchie on 2006-10-31
Maybe you have already come across a solution, but this is the one which works best for me on my acer aspire laptop with an X700 video card:

When installing the live CD, append the following to the commandline:
```
xforcevga vga=XXX
```

The actual value of XXX can be taken from the general guide here:
256 colours: 769 (640x480), 771 (800x600), 773 (1024x768 ).
I know that 256 colours is not great, but that driver will mainly be used for the console, which is black and white anyway. I found out by testing that more colours proved to be very unreliable...

After this, boot up... In my case ubuntu will STILL come up with a black screen, but thats ok, since we now have a console. Wait for the music before switching, just in case!

Once you have the console, you can edit the /etc/X11/xorg.conf file as mentioned before, just including the following line in the DEVICES section:
```
Option "MonitorLayout" "LVDS,AUTO"
```The AUTO is not really necessary, but makes things look more high-tech, and it works, so I didn't touch it!

Right, that config should be ok, so now restart X. The easiest way (though a bit brute-force) is by doing the following command:
```
sudo killall -9 Xorg
```Now the X server should restart, and you should have a UI!

In my case, when I later installed ubuntu 6.10, it took the correct settings, so I have a GUI right after installing! But if you don't, the same thing should fix it!

I hope this helps someone!

---

### Post by Skukfas on 2006-12-25
Hi all... i had the same problem.
My laptop is an Acer Aspire 1694 WLMi (1690 Series)

Did something similliar to what Franchie said and worked.. except for the restart X
Instead of "killall", I did:
ALT+F7
then
CTRL+ALT+BackSpace

:)

---

### Post by mmendez on 2007-01-02
Hi all I've had the same problem with Dapper and then Edgy on my acer ferrari I found this and it's kind of worked. It atleast gets me to see everything ok. except that in edgy the refresh rate is a little off. 
so here is the quick fix for me until I download the ATI driver

after you install, reboot and then when the GRUB is loading and it says press escape to enter the menu well do so, choose run in safe mode, wait a while and then you should see a command line. You will be logged in as root and just do this
```
nano -w /etc/X11/xorg.conf
```
scroll down and find the ATI Radeon ... and change erase what you have and change it to vesa, exit by pressing ctrl+x (i think) and then save to the file and exit

---

