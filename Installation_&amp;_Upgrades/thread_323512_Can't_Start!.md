---
title: "Can't Start!"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by AgeingAdolescent on 2006-12-22
Trying to install Edubuntu from a CD (6.06 LTS)

I have installed it all successfully on a partition alongside XP it seems (I did this before while I was expermenting with Mandrake so think it's ok)

After everything restarts and boots up again, I'm told to put in username and password, no problem.

Then it just leaves me with a command line!  What am I supposed to type to get the whole thing started?!  (Yes I am newbyish...)

---

### Post by MrHorus on 2006-12-22
Did you actually install X and a window manager?

Try startx from the command line and see if this launches X11 and your default window manager.

If not, you will need to set up your networking and then use apt-get to isntall the relevant packages like kde-base etc

---

### Post by AgeingAdolescent on 2006-12-22
well, i installed everything!  or rather, the installer did.  tried typing "startx", no joy.  doesn't help that when i do type something that actually gets a response it scrolls down for ages very quickly and dont know how to pause it... see, i AM a newby!  when i typed in apt-get it scrolled down with a whole load of stuff including "This APT has Super Cow Powers."  ???!!!

---

### Post by taurus on 2006-12-22
So there is a **startx** command!!!  Maybe you just need to reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by MrHorus on 2006-12-22
> **AgeingAdolescent said:**
> well, i installed everything!  or rather, the installer did.  tried typing "startx", no joy.  

When you say no joy, do you mean that it does absolutely *nothing* *at all* or that it does something but gives and error message?

If it gives an error message then it would help if you could past it here as whilst it might look gibberish to you, some of us will be able to tell you what the error means and suggest ways of fixing it.

---

### Post by AgeingAdolescent on 2006-12-22
ok, thanx, seems like my xserver isnt installed after all... not really sure what to do but when i typed "aptitude" a whole load of stuff came up to confuse me.

and can someone PLEASE tell me what it is i type to stop everything scrolling down so quickly?!

ALSO now i'm not even at a command prompt! no idea what to do

---

### Post by taurus on 2006-12-22
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by AgeingAdolescent on 2006-12-22
THAN-Q - ok, did Ctrl-Alt-F1 to get back to command prompt, it liked the first line of what you said, and also the second line when i put the CD in - it is DEFINITELY doing something, all apparently to do with [http://security.ubuntu.com](http://security.ubuntu.com) ??? will let you know.....

---

### Post by AgeingAdolescent on 2006-12-22
getting closer!

after doing all three lines that Taurus said the ubuntu interface seemed to come up, i logged in and... nothing.  just a red screen.  now its put me back into some sort of command line (i tried restarting a couple of times) and when i've put in "/etc/init.d/gdm start" it's said Starting GNOME Display Manager...... [fail]

what now?!

---

### Post by taurus on 2006-12-22
```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by AgeingAdolescent on 2006-12-22
:confused: 
ok so the first bit you just told me to write went well, went through lots of x configuration.

then when i wrote startx it said:
X: user not authorized to run the X server, aborting.
Couldnt get a file descriptor referring to the console.

even better, when i restarted, my monitor came up with "input not supported"  so i logged on blindly, no idea what's happening...

sorry!  and thanx!

---

### Post by taurus on 2006-12-22
You need to boot into recovery mode from GRUB menu and reconfigure your X again!!!

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

p.s.  What's the spec of your machine especially the video card?

---

### Post by AgeingAdolescent on 2006-12-22
it says:
"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20061222155111"

so do i type that last bit in?

i can't believe this is so complex and i haven't even opened the thing yet!

WOOPS - FORGOT : my video card is VIA/S3G UniChrome IGP with 32MB memory size.  Is that what you mean?

---

### Post by floke on 2006-12-22
No, don't type the last bit in - it's just a message telling you that it's making a backup of the xorg file (and where it is) in case the changes you have just made screw it up.

Did you run this from a LiveCD first - and did it work ok?
And also - did you verify the disk before installing it?

---

### Post by AgeingAdolescent on 2006-12-22
yeah i ran ubuntu straight from another (bonafide) CD i had with it on, no probs, and yeah, i checked this CD's integrity first and it was fine :(

---

### Post by floke on 2006-12-22
when you say you did this before with Mandrake - what do you mean?
Did you actually install it alongside XP?
And how did you remove it?
And how did you then install Edubuntu?

(Sorry for lots of questions, but it might have been something in the installation process)

---

### Post by AgeingAdolescent on 2006-12-22
it's ok - i'm grateful for any help i can get!

i had mandrake on a partition alongside my XP partition a while back, but very stupidly decided to just take off my files and delete the mandrake partition!  so i still had the GRUB boot but no linux for a while, but anyway it's ok now i think because ubuntu seems to have replaced the GRUB boot without any hitch.

i installed edubuntu from a CD i actually sent away for properly, and installed from the menu through the "rescue a broken system" since that allowed me to make sure i didnt deleted the XP partition.

---

### Post by floke on 2006-12-22
When you install ubuntu it will automatically rewrite Grub so that's fine. You might have an error on the actual disk though. You could try running 'fsck' from the terminal to check the disk.
Also, when you removed Mandwhatsit - did you also delete the swap partition, or just the main one? I don;t know if this will have caused a problem - but it's possible.

If all else fails you could try a complete reinstall: Use the LiveCD to delete the main Edubuntu partition and the swap partition (this will be in an extended partition - don't remove this - just the swap). Then install and let is install to the largest available free space - this will keep the XP partition intact and will just install in the gaps left by the deletions.

If you then get the same problem then at least you'll know it can't have been an installation problem, so that can be crossed off the list.

Since it only takes around 20mins to install ubuntu, I'd be inclined to try it.

---

### Post by AgeingAdolescent on 2006-12-22
i actually have already tried deleting the partitions and re-installing as you suggested.

bit worried about the fsck command... isnt it dangerous?

---

### Post by floke on 2006-12-22
I'm no expert - but from what I can tell the system automatically forces a fsck after 30 reboots anyway.
You should have the option as you go through it to make any changes to errors or to ignore them.

Does it still work from the LiveCD? If so you could try printing off the xorg.conf file - you can see this by clicking up levels (you have to let nautilus view hidden files) - its in /etc/X11/xorg.conf

When you boot from hard disk and you get no GUI - you could then compare the readout to what you have with no LiveCD - from the terminal type 'sudo nano /etc/X11/xorg.conf' - this will allow you to edit the file, so you can change it to the LiveCD version - which presumably works?

If you're worried about the fsck, I would check around the forum for info on it.

Sorry not to be of more help.

---

### Post by AgeingAdolescent on 2006-12-22
oh wait!  somethings happening, i did something i did before AGAIN and it seems to have opened ubuntu!!! BUT its saying i must start the dbus system service...

and you HAVE been a great help, honest :)

---

### Post by AgeingAdolescent on 2006-12-22
Yay!!! Magically All Working!!! Thank-you Guys!!!:d

---

