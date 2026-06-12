---
title: "Dell Inspiron 1501 + Coloured Vertical Lines"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Shadow_Walker on 2010-05-09
When i boot off the install disc for Linux 10.04 it loads the little symbols down the bottom of the screen then they dissappear and Coloured Vertical Lines appear on my screen. How can i fix this?

I also downloaded the Text Based version of the install disc and i managed to install Linux fine but when i rebooted the Vertical Lines reappeared but i could still hear sounds so this leads me to believe it is a graphical error. Any help is much appreciated.

---

### Post by Catharsis on 2010-05-09
What graphics card do you have?
```
lspci | grep VGA
```

You can try booting into Recovery Mode. Hold down Shift while you boot and then select the recovery mode kernel.

---

### Post by jscrane on 2010-05-10
Uninstalling the radeon driver worked for me:

```

# apt-get remove xserver-xorg-video-radeon

```

I guess this causes it to use a generic driver or something, however at least the box is useable now :)

---

### Post by Catharsis on 2010-05-10
Hold down Shift while booting to get to grub. Then hit 'e' to edit, and remove "quiet splash". Ctrl+x to boot.

If that doesn't do anything, remove "quiet splash" again and replace it with "nomodeset".

---

### Post by jjgl7 on 2010-05-17
> **Catharsis said:**
> Hold down Shift while booting to get to grub. Then hit 'e' to edit, and remove "quiet splash". Ctrl+x to boot.

If that doesn't do anything, remove "quiet splash" again and replace it with "nomodeset".

I had the same issue, the "nomodeset" option worked for me in my Dell Inspiron 1501, with a little workarounds, when I logged in, the vertical lines come back, so I go to tty1 with  ctrl-alt-f1 (vertical lines showing too) and then go back to ctrl-alt-f7. 

Does someone fix the issue?

Thanks a lot Catharsis,

---

### Post by Catharsis on 2010-05-18
Wait, what happens? I'm confused.

If the problem is that the fix doesn't work after you rebooted, that's because editing settings through grub doesn't make them permanent. To do that:
```
gksudo gedit /etc/default/grub
```
And add "nomodeset" to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
then save and exit. Then:
```
sudo update-grub
```

---

### Post by brad15 on 2010-05-23
I am having the same problem. The funny thing is for the first three times i booted into ubuntu, i had no issues, but now everytime i log in i get the vertical lines.
 
This laptop has a ATI Radeon Mobility Xpress 1150 graphics card (im assuming it's the standard one)
 
This is my first full installation of ubuntu that i'm actually trying to use and , i am actually a mac person and came across this laptop to play with linux on, so any help to get a fully functional radeon driver would be apprecated. I noticed when i boot into low-graphics mode it seems to use a ton more battery than when it uses the accelerated one.
 
Edit, so removing the Quiet Splash seems to work for now, i'll check back later and see what it's doing tomorrow... hopefully this fixed it

---

### Post by jjgl7 on 2010-05-31
> **Catharsis said:**
> Wait, what happens? I'm confused.

Thanks for your help, Catharsis.  I didn't found the grub data because I've been upgrading Ubuntu since 8.04 with online updates.  So I had to format my computer, the nomodeset option worked great.

---

### Post by n4pgw on 2010-06-25
You fine folk are quite wonderful.  I just had this problem and found this thread.  The following instructions worked perfectly for me.  

Thank you very much
Buck

UPDATE++++++++++++++++

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
The above line failed to work.  I re-edited it and took out the quiet splash and left only nomodset.  This appears to work.  


> **Catharsis said:**
> Wait, what happens? I'm confused.

If the problem is that the fix doesn't work after you rebooted, that's because editing settings through grub doesn't make them permanent. To do that:
```
gksudo gedit /etc/default/grub
```And add "nomodeset" to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```then save and exit. Then:
```
sudo update-grub
```

+++++++++++  Another Update ++++++++++

The laptop is still having the problem.  After it has been off over an hour, it boots with the vertical lines.  The last time I just hit the enter key and it continued and booted to a normal screen.  

Before this last occurrence I deleted the display driver according to the above instructions.

This is a 64 bit computer with 32 bit Ubuntu.  Could that be part of the problem?

Thanks
Buck

---

### Post by Scott. on 2010-09-01
I have the exact same problem on my Dell Vostro 1000.  I found a workaround.  I haven't had a chance to try the suggestions below.  Hopefully I'll have time later on today.  However, if your still having problems, try this.

You need to get to the GUI at least once (or find the command line commands).  Set the power to the monitor to power down the monitor after 1 min.

Next time you boot up you'll have to guess when to type in your name and password.  I have audio when mine comes up.  At the first audio queue type your username and hit enter (The first audio queue may come after you do this.  I don't remember.)  Then type your password and hit enter.  You should get the intro audio.

Now...just wait a minute for the screen to go black.  When you wake it back up you should have your desktop staring you in the face.  I shouldn't need to say a permanent solution is better.  But if you still want to use your machines while trying to fix it, this will work. - S

---

### Post by InMyHumbleOpinion on 2010-10-31
Installing 10.10 on to a hand me down Inspiron 1501 with what I also assume is the default video card, an ATI Raedon  Xpress 1150.  Install was done without any network/internet connection.  I came up with the same vertical lines problem, so thanks to Shadow Walker for starting this thread that I found with my search parameters.

I did get some error messages which I believe are related to close  source wireless network hardware, but those did not interfere with the  install itself.  

For the most part, Cartharsis' advice got me through this, so a big thanks to you Cartharsis.  However, to break down the steps and give more specifics on what to do about the first install here's how I did it:

_Intall disk_
Once the install disk starts booting, press Ctrl-x.  This will bring up an ASCII menu, with the expected list in the middle of screen (boot up without install, install, test disk, and one or two others).  First though, select the language with up and down arrow keys and press enter/return (it's already on English, so just hit enter/return if that will work) from the pop up menus.  Then scan the bottom line, which will have options that will pull up other menus by pressing the function keys- language is one and keyset another.  To the far right, F6 for me, was "Other Options".  Clicking that pulled up a menu that included "nomodeset".  Arrow down to it and press enter/return and an "x" should appear to the left of "nomodeset".  Press Esc to leave that pull and NOW look at the middle menu.  Arrow to your choice and press enter (which I'm going to start using instead of enter/return now).

If you choose any option other than install (for instance, I did the test install disk), you'll likely have to reboot and repeat the above.

For the rest of that session, you should have no colored vertical lines UNTIL you shutdown/restart, but that will only be once you make that selection.  At that point everything will run automatically and they'll disappear soon enough.

_Initial boot up from installed system_

Okay, I messed up here and instead of removing/replacing "quiet splash", I simply added "nomodeset" to the end.  It worked for me.  Otherwise, I did everything as Catharsis instructed here:

> **Catharsis said:**
> Hold down Shift while booting to get to grub. Then hit 'e' to edit, and remove "quiet splash". Ctrl+x to boot.

If that doesn't do anything, remove "quiet splash" again and replace it with "nomodeset".

_Grub edit for permanent fix_
Again followed Cartharsis' instructions below.  Tried both with adding "nomodeset" to the end of "quiet splash" and by replacing the latter with the former.  Both work for me.  I still get the vertical lines AFTER I confirm shutdown/restart, but again, it doesn't interrupt the process, and so it's not up long.  

> **Catharsis said:**
> Wait, what happens? I'm confused.

If the problem is that the fix doesn't work after you rebooted, that's  because editing settings through grub doesn't make them permanent. To do  that:
```
gksudo gedit /etc/default/grub
```And add "nomodeset" to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```then save and exit. Then:
```
sudo update-grub
```

The only thing I would add is, even though you save the changes to grub in gedit, remember you still have to run the sudo update-grub command in the terminal.  Yeah, I did forget at first.

Thanks again for the help.  Out of curiosity, and if it's not trouble or too long of an explanation, what do "quite splash" and "nomodeset" do?

---

