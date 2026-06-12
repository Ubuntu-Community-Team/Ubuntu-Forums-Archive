---
title: "Blinking cursor when installing"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by Blisk on 2012-11-21
I have downloaded all versions of ubuntu 10 to 12 and it is impossible to install it. I always get blinking cursor on black screen and that's it.
I tryed on 3 differend computers one is brand new laptop acer.
And it is no way to instal ubuntu on any of it.

Today I tried Lubuntu on old laptop and it is the same. Blinking cursor

The only way to install ubuntu on new laptop was with wubi, than with partition manager i maded 2 new partitions and than moved that ubuntu installation on new partition and than delete windows and after that expand partition for linux to whole disk.

What is happening with ubuntu this use to be a good distribution, now it doesn't work on almost any pc.

---

### Post by Blisk on 2012-11-21
I also have burned iso dvd to slow rate 2x, on another dvd recorder, etc.
and tryed some solution on internet and nothing worked

---

### Post by cwsnyder on 2012-11-21
To make sure I understand, when you install, are you installing from a Live CD which works?  You have checked your .iso file with the selection on the GRUB menu to make sure your download was good or checked with md5sum or sha256sum against the listings on [http://releases.ubuntu.com](http://releases.ubuntu.com) on the version you downloaded?

---

### Post by Blisk on 2012-11-21
> **cwsnyder said:**
> To make sure I understand, when you install, are you installing from a Live CD which works?  You have checked your .iso file with the selection on the GRUB menu to make sure your download was good or checked with md5sum or sha256sum against the listings on [http://releases.ubuntu.com](http://releases.ubuntu.com) on the version you downloaded?

YES to all questions and I have almost 35 Cds and DVDs here and on everycomputer is the same.
I have also burned with slow speed and another burner and another computer and downloaded from mirrors etc. 
After a week of doing almost everything I used wubi and done with that!

---

### Post by mörgæs on 2012-11-21
For the blinking cursor problem this thread might be worth reading:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Long story short, I guess you need boot options.

---

### Post by Blisk on 2012-11-22
> **mörgæs said:**
> For the blinking cursor problem this thread might be worth reading:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Long story short, I guess you need boot options.
I also have tryed that but still nothing works.

So it is much easier way to install it with wubi, which on winxp doesn't work :)
So I asked myself what is happend to the best distribution of linux? Nothing works anymore.....

---

### Post by mörgæs on 2012-11-22
What exactly have you tried? If we should be able to help you need to provide all details you could possible think of.

---

### Post by coldraven on 2012-11-22
I once bought a box of Memorex CD RW discs and they were all duff. Some sort of manufacturing fault meant that they had small scratches nearest the hole. That section is where the writing starts so they all failed.

---

### Post by Blisk on 2012-11-22
> **mörgæs said:**
> What exactly have you tried? If we should be able to help you need to provide all details you could possible think of.
_**Preface**_  
 Linux distributions such as Ubuntu, basically and simplistically run in  layers like this-->  You have a Linux kernel running.  On top of  that layer, you have a terminal session- running to interact with other  layers.  On top of that, you have an GUI, XTerminal session, X-Wndows,  XServer or also known as an XSession running to have a visually  interactive session running.  In each version of Ubuntu (and of  distro's) an honest and earnest attempt is made to make each new version  easier to use for a new user, in a way that is pleasing to the eye.    Each of these changes does mean underlying changes in how things relate  to each other layer... on a base that is trying to cover a myriad of  hardware combinations, that users will install that distribution onto.   Sometimes all of these combinations cannot be "foreseen."  (For instance  when a certain video card type is made by over a dozen different  vendors...) These techniques are similar to the same problems in Unix  and XServer (XServer Host & Client)...  
 
 Here is a short quick-reference of Linux short-cuts and hot-keys to  help you get around and to help diagnose graphics problems in an Linux  XSession.  Some are also helpful later in just everyday kind of tasks.   Like I said, this is only an abbreviated list, but I included them here  because they do come in handy in diagnostics and the correction of boot  and video errors:  
 
 **<Ctrl><Alt><F1>  **
 Switch to the first text terminal. Under Linux you can have several (6  in standard setup) terminals opened at the same time. Terminals start as  tty0 and go up from there. Most of the time the normal boot text  console, that is present "under" the GUI or XSession (in Ubuntu) is  tty1, so you would press <Cntrl><Alt><F2> to get to  it...  
 
**<Ctrl><Alt><Fn> (n=1..6)  **
 Switch to the nth text terminal.  
 
**tty<Enter>  **
 Print the name of the terminal in which you are typing this command.  
 
**<Ctrl><Alt><F7>  **
 Switch to the first GUI terminal (if X-windows is running on this terminal).  
 
  **<Ctrl><Alt><Fn> (n=7..12)  **
 Switch to the nth GUI terminal (if a GUI terminal is running on screen n-1). On default, nothing is running on terminals  
 8 to 12, but you can run another server there.  
 
**<Tab>  **
 (In a text terminal) Autocomplete the command  if there is only one option, or else show all the available options.  
 THIS SHORTCUT IS VERY HANDY! This also works at LILO or GRUB prompt!  
 
**<ArrowUp>**  
 Scroll and edit the previous command history. You can then use that  command as is or edit it to change. Press <Enter> to execute.  
 
**<Arrow><Down>**  
 As above, but go back to the next command in history.  
 
  **<Shift><PgUp>  **
 Scroll terminal output up. Work also at the login prompt in the tty  text console, so you can scroll through your bootup messages to find  errors and messages.  Does not work to see terminal output that has been  "cleared."  
 
**<Shift><PgDown>  **
 As above, but scrolls terminal output down.  
 
**<Ctrl><Alt><+>  **
 (in X-windows) Change to the next X-server resolution (if you set up  the X-server to more than one resolution in /etc/X11/XF86Config). For  multiple resolutions on my standard XVGA card/monitor, I have the  following line in the file /etc/X11/xorg.conf (the first resolution  starts on default, the largest determines the size of the "virtual  screen"):  
 Modes "1440x900" "1024x768" "800x600" "640x480" "512x384" "480x300"  "400x300" "1152x864"  Whichever resolution you have as first in this  line will be the default.  
 
**<Ctrl><Alt><->  **
 (in XWindows) Change to the previous XServer resolution.  

**<Ctrl><Atl><Backspace>**
Linux Ubuntu version 10.10 and previous- Kill the current X-session.

**<Alt>-<SysReq>-<k>**
Linux Ubuntu version 11.04 and later- Kill the current X-session.

-- The "Linux shortcut keys" are just that, meaning Linux is already     booted. to use them-- although "some" of them do work in the Grub CLI.     *such as the <Tab> for autocomplete)

Basically, between the grub menu and the GUI Desktop Manager (GDM or  LightDM), where you are getting a blank   screen the only short-cut keys  that "may" be available are the   <ctrl><alt><F1 the  F6> keys and   <ctrl><alt><F7> key... which I  mentioned, may not work   even if you  were not having graphical  problems.. But if they do, you have some options.
 
 
 _**General**_  
 Yes, with every new release of a distribution of Ubuntu, there seems to  be similar and reoccurring problems that arise with "graphics" when  trying the run a LiveCD and after the initial install and first boot.  These are my notes that have help people through the last 5 releases of  Ubuntu, up through Ubuntu Natty Narwhal 11.04.  

Basically, we want to make sure that the Grub menu boots. then verify  that the kernel is booting, then that the XServer Session starts and  displays.

_**Troubleshooting Flow Chart **_
This is to break this down into steps:
**Step 1**. Do you have a Grub Menu?
 - Yes: Go to step 2...
 - No: While booting, Press shift key (don't hold down) multiple times to see if the Grub menu will come up.

---

### Post by Blisk on 2012-11-22
Oh yes I forgot one error which I get from 2 installation CDs. 
Invalid or corrupt kernel image

---

### Post by efflandt on 2012-11-23
Maybe there is something wrong with your CD drive writing or reading.  Although, if you tried writing them on different computers you would think something would work.  If you boot a CD and hit any key when you first see symbols at the bottom of a purple screen, they should be a selection in the resulting text menu to check the (CD) disk itself against the checksum on the CD.  That should usually find a corrupted disk (or read problems with the drive).  Although, I have a CD/DVD drive on one old laptop that gets flaky after playing a DVD for about 90 minutes.

What video card or chip is on those computers.  At least with nvidia, various Ubuntu versions sometimes require **nomodset** boot parameter only during install, sometimes only after install, or sometimes both.  But it does not hurt to try that parameter in any case.  The nomodeset parameter forces the use of user space video modules (which can be loaded/unloaded as needed) instead of the newer kernel mode setting.

If you changed memory in any of the computers you may want to download a separate iso for memtest86+ and run that for awhile to see if you have any memory issues.  I have run across a couple of cases where memory that should have been compatible with a PC would have occasional issues and produced errors with memtest86+.  Yet that same RAM lives on in another computer with no memtest errors.

---

### Post by Blisk on 2012-11-23
On new laptop, brand new from store don't know what vga card is. I tryed also with external DVD unit it was the same. I tryed almost everything I remembered and readed on internet what can be wrong. Nothing helped.

On this old laptop it is Intel graphic.
and I manage to install lubuntu over wubi with some tricks but it is to heavy for that laptop with 256 MB of ram.

Also nomodeset I tryed but didn't worked I get kernel error.

I didn't do memtest because That was about 4 PCs where nothing worked when I try to install ubuntu and I am soure all cant be problem.
Like I wrote before on new laptop I have installed it with wubi and partition manager and all that stuff to manage to have it no hard disk like when you installed it from cd.
And now all works ok. but still why installation doesn't work? 
When I tryed with wubi and have the same image ond CD which was extracted and installed on laptop, when runned from CD doesn't work when installed with wubi works?

---

