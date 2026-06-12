---
title: "Can't log in to Ubuntu. TTY???"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by FrozenFlame22 on 2010-10-25
I recently did a fresh reformat and install of Ubuntu 10.10 and Windows XP on my 3 year old computer. After a couple of days of failed installs (the CD installer would hang and crash), I got a good install and got to work setting up my computer. Today, I was in the middle of transferring 15 GB of data between two hard drives and I needed to leave the computer running to finish the transfer. When I came back home, I had a black screen that read:

Ubuntu 10.10 Erebor tty1
Erebor login:

Erebor is my computer name. I am a complete novice when it comes to Linux and I have never heard of tty. Rebooting the computer brings it back to the same screen. I tried the passwords for the three users for the computer and nothing works. I have been able to start the recovery console and I selected repair broken packages, but that doesn't change that it still boots into this tty login. I have no idea how to log in or how to get my gui working again once I am logged in. Help?!

Right now the only thing I know to do is to start from scratch again and reinstall from the live CD, but that was such a fiddly procedure that I don't want to go through the 20+ tries to reinstall it again.

Edited to Add: I tried booting into Windows XP, but it just gives me a black screen. I'm really lost here on what might be the problem. Any ideas? Is there any more information I can add?

---

### Post by FrozenFlame22 on 2010-10-26
Bump.

Is this the right forum for this question? Should I try a different one?

---

### Post by akand074 on 2010-10-26
Weird problem, not sure what caused it, but try logging in through the command line when you get to that point and then once your logged in run this command:

```
sudo service gdm start
```

That should start your graphic user interface.. not sure why its not already.

---

### Post by msandoy on 2010-10-26
Actually what you are getting on the screen is the CLI login. Enter your username at the Login: and then you will be asked for the password. When it has logged in, try to type startx and press enter. It will then try to start up the GUI, and if it fails, it will give you some error messages that you can post in here.

---

### Post by FrozenFlame22 on 2010-10-26
New info!!!

I'm 99% sure that my video card driver went berserk. Somehow (not sure exactly what I did) I got into a low graphics mode gui. I tried taking a look at my NVIDIA X Server Settings and it said:

```
You do not appear to be using the NVIDIA X driver.  
Please edit your X configuration file (just run `nvidia-xconfig` 
as root), and restart the X server.
```

So I ran that in a terminal and got:

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

What do I do now?

---

### Post by FrozenFlame22 on 2010-10-26
Last night I was able to finish my file transfers between my hard drives, so next time I reboot I'm going to pull out the extraneous hard drives to allow for better air circulation. I know my system to run a little hot anyway.

I did leave the computer running in low graphics mode overnight, and when I got up this morning the screensaver had frozen and it wasn't responding to anything. I rebooted and got the CLI again. This time when I typed in my user name it showed up on the screen, which it hadn't last night. I was able to log in this way and got a command line. Then I tried the line akand074 suggested, but nothing I type shows up on the screen.

---

### Post by FrozenFlame22 on 2010-10-26
I just finished pulling out two hard drives and the expansion card that was required to read from them. (These were VERY old hard drives!) Cleaned up the fans, blew out (more) dust and rearranged my cables a bit for better air flow. Powered up and it starts just fine like it should. Everything looks and acts perfectly now. So was my problem simply dust and heat? I've been running this computer near constantly for 3 years with very intermittent cleaning and I've never had such strange behavior. I know it's been dustier/hotter before now and all I added was a brand new SATA drive to replace my 2 oldest drives and expansion card.

---

### Post by akand074 on 2010-10-26
> **FrozenFlame22 said:**
> I just finished pulling out two hard drives and the expansion card that was required to read from them. (These were VERY old hard drives!) Cleaned up the fans, blew out (more) dust and rearranged my cables a bit for better air flow. Powered up and it starts just fine like it should. Everything looks and acts perfectly now. So was my problem simply dust and heat? I've been running this computer near constantly for 3 years with very intermittent cleaning and I've never had such strange behavior. I know it's been dustier/hotter before now and all I added was a brand new SATA drive to replace my 2 oldest drives and expansion card.

I honestly don't see how that could have possibly been the issue.. but alls well that ends well.

---

### Post by FrozenFlame22 on 2010-10-26
I'm baffled as well. *shrug*

Thank you very much akand074 and msandoy for your patience!

---

### Post by msandoy on 2010-10-27
Since removing hardware has solved your problem, it seems to me that your PSU is getting old and unreliable (can't take high load without reducing voltage.), and you might benefit from renewing the thermal paste between the CPU and the heatsink. Old paste become hard and less effective in heat transfer. Myself, I usually renew the thermal paste approx. once a year on my own computers, including laptops. It really helps, and the paste is cheap.

---

