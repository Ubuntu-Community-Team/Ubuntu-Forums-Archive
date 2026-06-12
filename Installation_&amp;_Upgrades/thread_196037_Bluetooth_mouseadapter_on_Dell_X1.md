---
title: "Bluetooth mouse/adapter on Dell X1"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by tsiMental on 2006-06-13
I've been trying to get my bluetooth Logitech V270 mouse to work on my Dell Latitude X1 laptop using the Live CD. I want to get this mouse to work before I install Ubuntu on my laptop.

I've tried the instructions on [this thread]("http://ubuntuforums.org/showthread.php?p=478109") with no luck.
Edit:[SIZE="3"]**There are instructions on how to make this mouse and possibly many other bluetooth mice work on a permanent basis [further down this thread.]("http://www.ubuntuforums.org/showthread.php?p=1440347#post1440347")**[/SIZE]
If you follow these instructions, the mouse will connect once it is turned on, even if you restart after connecting the mouse.

---

### Post by tsiMental on 2006-06-13
deleted [look at this post to find the best approach.]("http://www.ubuntuforums.org/showthread.php?p=1440347#post1440347")

---

### Post by tsiMental on 2006-06-15
Using KUbuntu, all you need to do, is actually:

Pop a Konsole and type the following, but don't press the enter key just yet...
```
sudo hidd --search
```Now, press the Reset/Connect button on your mouse. And rather quickly thereafter, press enter in the Konsole window.

Works like a charm... should be working this way using Ubuntu and GNome also... so try this approach before you start trying the way I explained before...

Try to use HIDD first... The "hidd --search" and "hcitool scan" functions should do the same. But I've not got hcitool to work...

It seems to me that hcitool isn't working as good as hidd. And if used in combination, only creates trouble...

Edit:[Find the permanent solution to the problem here.]("http://www.ubuntuforums.org/showthread.php?p=1440347#post1440347")

---

### Post by x64Jimbo on 2006-06-16
the problem with this method is that it does not pair the device with the computer with any permanency. It's great for short term but even if the device disconnects to save battery, you'll have to run that command and hit the pair switch on the device again. Very much a pain, and I would like to see a way to actually pair the devices permanently with encryption keys.

---

### Post by tsiMental on 2006-06-16
There is a solution to the permanency problem further down, [in the next post.]("http://www.ubuntuforums.org/showthread.php?p=1440347#post1440347")

---

### Post by tsiMental on 2006-08-30
I have found the solution for the pemanency problem!! :D 
***This method makes the mouse connect immidiately once turned on, no fuzz...***

Open a console:```
sudo apt-get install nano
sudo nano /etc/rc.local
```Add the following line to /etc/rc.local:```
/usr/bin/hidd --server
```Make sure /etc/rc.local ends with 'exit 0' and a newline. (Ctrl+X exits nano)

Now either restart or open a console and type the following command to start the hidd server:```
sudo hidd --server
```Now lets connect the mouse:```
sudo hidd --search
```Retry the 'sudo hidd --search' command until the mouse connects. You might have to turn it off and on or press the reset button a couple of times.

The alternative connection method is looking for the bluetooth adress, usually located at the bottom of the mouse, and type:
```
sudo hidd --connect 00:01:02:03:04:05
```Where you change the numbers into the numbers you find on your mouse.

**Now the mouse should reconnect once you turn it on, even if you reboot.**

*Using the hcitools for anything, might create some fuzz with the hidd tool.* But that is not proven and not sertain.

My software:
kubuntu 6.06 dapper
kernel: 2.6.15-26-386
bluez-utils: 2.24

Thanks to Charles Bueche for telling me about the 'hidd --server' command.

---

### Post by nrwilk on 2006-09-02
> **tsiMental said:**
> I have found the solution for the pemanency problem!! :D 

Oh man.  This is great!  It finally fixed my permanency problem.

Big thumbs-up!

Thank you!

nrwilk

---

### Post by tanguyr on 2007-01-11
> **tsiMental said:**
> I have found the solution for the pemanency problem!! :D 
***This method makes the mouse connect immidiately once turned on, no fuzz...***

THANK YOU VERY MUCH! Worked like a charm on

kubuntu 6.10 (32bit) on asus w2p with asus bluetooth mouse.

Regs,
/t

---

### Post by djhanson on 2007-03-10
Worked great on my Thinkpad R51 too.  Very cool.  This was the only thing that the Ubuntu install did not setup correctly.  Everything else was detected and worked like a charm.  This is my first Ubuntu installation, and I'm sold.  Easiest install that I've ever done.

And holding down the connect/reset button on my logitech mouse was the key  to have it recognized during the search phase.

---

### Post by djhanson on 2007-03-10
Just found this on the Ubuntu website.  Works great, also.

[https://help.ubuntu.com/community/BluetoothMouse](https://help.ubuntu.com/community/BluetoothMouse)

---

### Post by nrwilk on 2007-04-25
> **djhanson said:**
> Just found this on the Ubuntu website.  Works great, also.

[https://help.ubuntu.com/community/BluetoothMouse](https://help.ubuntu.com/community/BluetoothMouse)

Thanks for that, man.  Works like a charm and even easier than before! :)

---

