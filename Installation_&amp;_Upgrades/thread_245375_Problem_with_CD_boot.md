---
title: "Problem with CD boot"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by Riza H. on 2006-08-27
Alright, I know nothing about the coding, and am not a programmer. So keep it simple for the stupid person here, ok? So, I can get to the point where I SHOULD be able to try out the OS (Xubuntu) before installing it. I can see the desktop, but it's divided into bars and there are three cursors, and three divisions of the same screen, if that makes any sense. Can I fix this without buying any new hardware (or without venturing too far into the coding)?

---

### Post by confused57 on 2006-08-27
> **Riza H. said:**
> Alright, I know nothing about the coding, and am not a programmer. So keep it simple for the stupid person here, ok? So, I can get to the point where I SHOULD be able to try out the OS (Xubuntu) before installing it. I can see the desktop, but it's divided into bars and there are three cursors, and three divisions of the same screen, if that makes any sense. Can I fix this without buying any new hardware (or without venturing too far into the coding)?
What type of video graphics card or controller do you have?  Sounds like it might be a problem with Xubuntu assigning a video driver.
If it is, we should be able to help you...

When you get to the scrambled screen, press Ctrl+Alt+F1, which will get you to a console...login(guess you don't need to with the live cd).
Enter:
```
sudo /etc/init.d/gdm stop
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
At the first screen, select "no" for autodetect, then just select the defaults for everything else, except when it asks which video driver to use...try "vesa" to begin with, or "nv" if you have a nvidia or "ati" if you have an ati card(try vesa first),etc.
When you've finished reconfiguring, enter:
```
sudo /etc/init.d/gdm start
```

---

### Post by Riza H. on 2006-08-27
I really have no idea. Nothing that originally came with the computer is in there now. 
I had to go boot up Windows (](*,) ) to find out. I'm running XP on a computer built in 1992, with the original amount of RAM, though I now have a second hard drive (which is what I'm hoping to use for Xubuntu, instead of risking a partition).
My 3D card (I'm fairly certain it's not important, but...) is ATI Technologies, inc. 3d Rage pro PCI.
And... I think my uncle messed something up when he installed the 3d card. What I think you're looking for is: SiS 530/620, but that has a warning message that "this device cannot start".
Unless none of the above are important, and the second was removed for some reason...

---

### Post by confused57 on 2006-08-27
Since you have a second hard drive, you might want to consider this option to dualboot with:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Back to your problem,  you probably need at least 128 Mb ram to run the Xubuntu live cd and 256 Mb or more to install.  You can install, using less ram, with the Xubuntu alternate cd.

Does your computer have onboard graphics, as well as the ati graphics card(where is the monitor connected to your computer?)?  ATI cards can be a little tricky to get configured.  Try what I suggested above, you might even want to try "sis" as a video driver & see what works.  Once you find something that works, then you might consider downloading the alternate cd and installing to your 2nd hard drive.
"this device cannot start" error message might be a problem.

---

### Post by Riza H. on 2006-08-28
Um... the command prompt gave me a nasty little error message when I tried to imput the first string of code. Is it right?
And... I was wondering: Is there a way to specify what hardware you have hooked up during live bootup, instead of using the command prompt?
I'm fairly certain I have enough ram to run that; it ran Windows XP without crashing (well, without crashing more than Windows is supposed to, anyway). It wasn't at all fast, but it ran...

---

### Post by confused57 on 2006-08-28
> **Riza H. said:**
> Um... the command prompt gave me a nasty little error message when I tried to imput the first string of code. Is it right?
And... I was wondering: Is there a way to specify what hardware you have hooked up during live bootup, instead of using the command prompt?
I'm fairly certain I have enough ram to run that; it ran Windows XP without crashing (well, without crashing more than Windows is supposed to, anyway). It wasn't at all fast, but it ran...
The first command should have worked, but the 2nd is most important...there is a list of "cheatcodes" or boot options for the Knoppix cd:
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
I've never seen a comparable list for Ubuntu and some of the Knoppix cheatcodes may work in Ubuntu.

When your Live CD first starts, there should be a key mentioned(F6?) that you can specify boot options to boot up with...you can try this later if the sudo dpkg-reconfigure xserver-xorg doesn't help you.  I did a google search and found a couple of boot options that may work:
nox(boots to a command line)
xmodule=vesa(assigns the "vesa" driver to the xserver?)

The above is just commentary on my part, I've never actually tried any of it with the Ubuntu Live CD, although I have booted Knoppix with boot options.

Try what I mentioned in my earlier reply, press Ctrl+Alt+F1, to get to a console command prompt, enter:
```
sudo dpkg-reconfigure xserver-xorg
```
When you're finished & are back at the command prompt, enter:
```
startx
```
or
```
sudo /etc/init.d/gdm restart
```

Good luck.

---

