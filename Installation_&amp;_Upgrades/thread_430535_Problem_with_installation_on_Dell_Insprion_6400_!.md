---
title: "Problem with installation on Dell Insprion 6400 ! ?"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by ZataH on 2007-05-02
I have a Dell Inspiron 6400

Intel Core2Duo 2GHz
2048MB ram
ATI Radeon x1400 256mb
15,4 " 1280x800

And i can`t install Ubuntu 7.04 ! 
When i try the graphical installer, the installer said i couldn`t start X, because of some misunderstanding with my video driver. 

And the Text mode installer, stop/freeze when it is 6%, when it trying to get some data over network/internet. 

Anyone know what i should do ? Realy want to try this new version.

---

### Post by NotMeAnyMore on 2007-05-02
Sounds like a coaster , Download it again and burn it , i have successfully installed on a Inspiron 6400 without issue.

---

### Post by ZataH on 2007-05-02
Hmm wierd. but i have tryed both cds. The normal installer, and the alternative ! both fail each way.

---

### Post by dislocated on 2007-05-02
Did you download the 64 bit version? That was my first mistake when installing on my Inspiron 6400.

The 64 bit version worked great on mine.

---

### Post by ZataH on 2007-05-02
Why should a 64 bit version works better ?

I got it installed now, but can`t start it, X wouldnt start up.

---

### Post by schmigz on 2007-05-03
Same issue here.  X fails.  Sorry, I did not have time to write down the error messages.  I will post later.  Not sure why the 64-bit version would make a difference.

My video card is ATI Mobility Radeon X1400 with 128 MB of RAM with WSXGA+ 1680x1050 resolution flat panel.  I get the error when trying to boot off the Live CD.

---

### Post by mihaic on 2007-05-06
Hi,
  I also tried to install Ubuntu 7.04 from the live CD onto a Fujitsu Siemens laptop powered by a ATI Radeon Mobility graphics card and I have problems starting up Ubuntu from the live cd. The X server session seems to fail with an incomprehensible error message and the system enters in a login loop. I tried changing to a graphics failsafe session but no luck. So if someone figures this one out I would be interested also.
Have fun!

---

### Post by Neuralgia on 2007-05-06
Same problem here, I've posted severel threads, and no answer yet.

My system:

     Dell Inspiron 6400
     ATI x1300 128MB
     Intel Centrino Core 2 Duo (T7200 2.0Ghz)
     1GB Ram

With what I'm trying to install:

Ubuntu Live CD 32 bit
     a) graphical interface
     c) text mode

Error I get
     Something about my xorg.conf not configured, and that I don't have a monitor. All in Blue Screen (get 
     this in both, text and graphical mode)

What have I done
     a) checked the .iso w/MD5SUM: OK
     b) installed in other computer (Dell Dimension 8400 ATI x300): OK
     c) used the CD option to check for erros: OK

What's really weird
     a) I can install Feisty with the same CD in other computers (all P4's)
     b) I can install Ubuntu 6.06 and 6.10 in the same computer with NO problems (32 version)
     c) Other users are saying they can install it on their 6400 with NO problems (they don't specify which
         version they're using 32 or 64)
     d) My previous installations I used 32 bit versions, why do I have problems now?
     e) When I first upgraded from 6.10 (32bit) to Feisty, I didn't have any problems.

Things I need to try before going back to 6.10, and forgetting about Feisty
     a) Download 64 bit version

Why don't I just install the 6.10 and the upgrade
    a) This is what I did in the first place, and some things didn't work the way they're supposed to. Beryl, 
         screen, etc.
    b) I should be able to installl it with the LiveCD, that what the CD is meant for, right?

---

### Post by mihaic on 2007-05-06
I gave it a run from the alternate CD image which uses the text mode installer and that did it for me. So there is a chance you can have a successful install by using the alternate cd instead of the live cd. If even that doesn't work and you get some X server errors you can try to install the ATi drivers as indicated in[[COLOR="DarkOrange"] this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=414194") [COLOR="Black"]post.

Have fun![/COLOR]

---

### Post by msandersen on 2007-05-06
People with X problems: Various people have had problems with Feisty somehow not setting Horizontal and Vertical refresh rates in their xorg.conf when installing. Once added, it starts up normally for them. 
So if you've upgraded, and have your old xorg.conf, have a look.

---

### Post by Neuralgia on 2007-05-06
the question is, how to fix that during installation... :?

---

### Post by mihaic on 2007-05-07
Normally if your X session fails right after install in full text, you will still be able to run in command mode (text mode). You will need to find the xorg.config file which usually is located under /etc/X11/ and use a text editor with the sudo command in order to be able to edit the file.
Hope this helps...

Have fun!

---

### Post by msandersen on 2007-05-07
eg:
```
sudo pico /etc/X11/xorg.conf
```

---

### Post by barlaso on 2007-05-07
I'm not sure this is an ATI problem.
I had the same problem with a Dell Inspiron 1200 with onboard intel graphics:
- Live cd didnt work, due to xorg issues
- Alternate cd gave error during "Select and install software" at 6%
- CD checks ok

I tried the 'select and install software' step again, but same thing happened.
Then i figured, 'why dont i go on with grub install, i can at least boot into command line and figure something out from there.'  So after the error, i went on with grub install.

At this point, the weirdest thing happened, GRUB installed, and after that the install continued from the 'select and install software' step at 6% from where it left off.  It waited a while at 6%, but this time, went on without errors.  The installation completed, system booted, and works like a charm.

I have serious doubts about the repeatibility of this solution, but i thought i'd share anyway.

System:
Dell Inspiron 1200
Intel graphics
256mb ram
1.3 ghz celeron M

---

### Post by Neuralgia on 2007-05-13
if it's an ATI problem, the WHY can I install PERFECTLY 6.10 on the same laptop?

I can even install Beryl

since Fesity everyhting seems like Linux 5 years ago

:(

Not not sound "stupid", but things like this, are the ones to need to be fixed ASAP so Ubuntu can go mainstream, or it will keep itself "geek-exclusive".

-*-*-*-

is there a way I can know when this issue is fixed?

---

### Post by Neuralgia on 2007-05-14
sorry for the double post, but, found the solution

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

It worked perfectly for me.

Now the question is, when will this be fixed? why did this worked on Edgy, and now it doesn't?

I know I might sound a little paranoid, but I just goy my Ubuntu Feisty CD, and was wondering if they will make a CD with this Cd fixed? I don't like the feeling of having an installation CD, that I know has a bug with my laptop :(

---

