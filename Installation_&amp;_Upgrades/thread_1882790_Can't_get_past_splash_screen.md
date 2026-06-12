---
title: "Can't get past splash screen"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by Crimson_Tider on 2011-11-17
Hi, I am trying to do a clean install of Oneiric using a live USB flash drive.  The installation seemed to go fine and then I got to the desktop, but it never displayed anything but the default background and purple bars at the top and on the left where I assume all the app shortcuts and controls should be.  I am very much a newbie, so the posts I have found so far about this problem are a little over my head.  I have a BIOSTAR COMBO6S3B with an NVIDIA GeForce 7025 onboard video.  Can anyone help?  Thanks!

---

### Post by hahrugud on 2011-11-18
> ** said:**
> 
By Michael Bowman ,[abercrombie and fitch paris](http://www.abercrombieandfitchparis.biz) Washington 09 August 2009President Barack Obama's national security advisor says Iran has confirmed it is holding three Americans who are trusted apt have strayed into Iranian territory while hiking in northern Iraq. Retired General Jim Jones says the Iranian government has cleared up whichever doubts about the place of three missing Americans. "The government has officially acknowledged that they have them in their custody,[abercrombie paris](http://www.abercrombieandfitchparis.biz)," Jones said. "As of this a.m.,[******* sito ufficiale](http://www.monclersitoufficialet.com), we do have that confirmation." Jones was speaking on NBC's "Meet the Press" procedure.The United States has not foreign narratives with Iran. In recent days,[piumini *******](http://www.monclersitoufficialet.com), Swiss and Iraqi officials have inquired approximately the three Americans on Washington's behalf.News reports nail them as two males and a feminine who did writing and environmental go.Iranian state TV has depicted the detainees for spies,[louboutin pas cher](http://www.chaussureolouboutinpascher.com), a charge Jones rejected. "We have sent strong messages that we would like these three juvenile people loosened as presently as possible,[louboutin pas cher](http://www.chaussuresolouboutinpascher.com)," Jones said. "These are innocent people. We absence their families reunited." Regarding Iran's nuclear program,[*******](http://www.monclersitoufficialet.com), Jones was asked if the Obama administration would engage in talk with President Mahmoud Ahmadinejad emulating Iran's disputed presidential vote and subsequent protests and unrest."He namely the figure of legislature namely we have to handle with. But it is explicit there are major events going above inside Iran that must do with the [squabbled presidential] voting,[doudoune *******](http://www.doudoune-monclerquincy.com)," Jones said. "But we have to handle with the figures of authorization namely are in position."On dissimilar matter,[abercrombie](http://www.abercrombieandfitchparis.biz), Jones said the United States is approximately certain that one American missile strike in Pakistan final week annihilated the top-ranked Taliban actuator in the nation,[*******](http://www.doudoune-monclerquincy.com), and that a presidency skirmish has since emerged within the militant team.    Related articles&#65306;      [&#33080;&#19978;&#20725;&#30828;&#30340;&#32908;&#32905;&#32456;&#20110;&#30334;&#24180;&#19981;&#35265;&#22320;&#21160;&#20102;&#19968;&#21160;](http://www.jygjzx.cn/bbs/viewthread.php?tid=340518&pid=370705&page=1&extra=page%3D1#pid370705)     []&#26089;&#20986;&#65288;&#22806;&#20108;&#39318;&#65289;](http://wuzhendong1.gotoip4.com/read.php?tid=20205&page=e#a)     [&#12288;&#12288;&#36364;&#36487;&#19981;&#21069;](http://bbs.7192.com/viewthread.php?tid=61382&pid=124261&page=1&extra=#pid124261)   "It is with great sadness and a heavy heart that I have decided to end my six-year marriage to Ashton. As a woman, a mother and a wife there are certain values and vows that I hold sacred, and it is in this spirit that I have chosen to move forward with my life. This is a trying time for me and my family, and so I would ask for the same compassion and privacy that you would give to anyone going through a similar situation," she said in her statement to the AP

---

### Post by Crimson_Tider on 2011-11-18
Can anyone help me with this?

---

### Post by MAFoElffen on 2011-11-18
> **Crimson_Tider said:**
> Hi, I am trying to do a clean install of Oneiric using a live USB flash drive.  The installation seemed to go fine and then I got to the desktop, but it never displayed anything but the default background and purple bars at the top and on the left where I assume all the app shortcuts and controls should be.  I am very much a newbie, so the posts I have found so far about this problem are a little over my head.  I have a BIOSTAR COMBO6S3B with an NVIDIA GeForce 7025 onboard video.  Can anyone help?  Thanks!
I'm confused by your title versus your description... Even your description is confusing. No matter. Lets see if I can ask some questions so I have a clear idea of where you're at.

You booted from a LiveCD image from a USB drive. You said the install "seemed" fine, then went to a desktop. After that, it gets confusing.
- Did your install finish, ask you to remove the LiveCD and reboot? -or- If not, did it lock up to blank install desktop?
- If it did complete the install, did it boot past the Plymouth Splash and the Login Screen?
- Next milestone would be the Ubuntu Welcome Audio and the initial desktop panel of unity... Did it get that far without getting a Untity error saying that your graphics hardware...?

So if it got that far...It could be 2 things (Might be other than, but most common): Video driver or compiz

First and primary- What video driver diid you install? If an NVidia driver, is it a Binary or Debian package? What version driver are you using?

Have you tried this yet?
```

sudo dpkg-reconfigure compiz

```

---

### Post by Crimson_Tider on 2011-11-19
Sorry about the confusing title and description.  I forgot what I had typed in the title when I typed the description.  The truth is that tried installing several times, and sometimes it didn't make it past the splash screen right after I chose "Install to hard drive" and sometimes it would make it past that, through the installation (I know it installed because it eventually gave me the message, "Installation is complete. You need to restart the computer in order to use the new installation."), and then when it booted it just gave me the feaureless screen that I described above.  Right now, it is sitting on that screen--desktop with background and two blank purple bars, one on the left and one at the top.  There are no icons, no text anywhere, nothing.

Answers to your questions:

This time, yes the install finished, and yes it prompted me to reboot.

Yes, it booted past the splash screen, though I don't know what Plymouth is, and it doesn't give me a login screen because I told it in the installation to automatically log me in.

I don't know about the Ubuntu welcome audio because I didn't have the speakers plugged in.  I don't know what the "desktop panel of unity" is, but the answer is certainly no because I have not seen anything after rebooting but the featureless screen described above.  No, I didn't get an error message of any kind after rebooting.

I didn't install a video driver; I don't know how to do that.  All I know is that the specs on newegg.com where I bought the motherboard a couple weeks ago said "Onboard Video Chipset: NVIDIA GeForce 7025."

I haven't tried that code yet because I can't figure out how to get to a console where I can enter Linux commands.

Thanks very much for the help so far.  I eagerly await your reply.

---

### Post by Crimson_Tider on 2011-11-19
I figured out how to get to the command prompt on another website.

```
sudo dpkg-reconfigure compiz
```

didn't work.  I ran it, rebooted, and got the same result.

---

### Post by MAFoElffen on 2011-11-19
> **Crimson_Tider said:**
> I figured out how to get to the command prompt on another website.

```
sudo dpkg-reconfigure compiz
```didn't work.  I ran it, rebooted, and got the same result.
Now install your video driver, which should be nvidia-current.  
- Get back to a terminal session through <cntrl><alt><F2> or <cntrl><alt><t> or however it worked for you
- Open the Additional Drivers applet
```

gksudo jockey-gtk

```- Select the nvidia-current driver
- Press activate
- Close
- Restart the X-Session
```

sudo service lightdm restart

```*** Yes, the pro's and cons of "autologon!" Users think it's convenient, but when things go wrong, it cut's out the ability to change to a different desktop during login.  (Like Unity 2D, etc.) Sometimes it's nice having the ability the select a different desktop to do something.

---

### Post by Crimson_Tider on 2011-11-19
> - Open the Additional Drivers applet
```

gksudo jockey-gtk


That command resulted in this console message:

[CODE](gksudo:1586): Gtk-WARNING **: cannot open display:
[my username]$ [  141.564369] usbhid 2-1.3:1.1: couldn't find an input interrupt endpoint
```

I'm pretty sure I can't do any of the other steps you gave after that.

---

### Post by Crimson_Tider on 2011-11-19
After doing a little searching on the web, it seems like this may have something to do with my KVM switch.  Could that be the problem?  The way I have it rigged right now, it would be a real pain to disconnect it and an even bigger pain to go without it indefinitely because I have two computer running simultaneously.  Whaddaya think?

---

### Post by MAFoElffen on 2011-11-19
> **Crimson_Tider said:**
> After doing a little searching on the web, it seems like this may have something to do with my KVM switch.  Could that be the problem?  The way I have it rigged right now, it would be a real pain to disconnect it and an even bigger pain to go without it indefinitely because I have two computer running simultaneously.  Whaddaya think?
On the KVM switch-- You know it's hard to fight 2 problems at once, besides being frustrating.

Here is what I would do.  Think of this as a temporary kind of diagnostics thing.  Hook the monitor and keyboard directly to the computer > Install the graphics drivers (instructions below > work out the problems... Then hook it back up to the switch.

What you need to know about Linux/Unix graphics and a KVM switch, is that when a box w/NVidia or ATI graphics boot the X-Session under Linux, it probes it's ports and see's what's there.  If it doesn't see a device, it turns off that port. It a device is booted, but turned off, then on (also if switched), then it loses the sync and forgets with the resolution. (Thats a very basic explanation of a larger picture.) There's ways around all that.  Just more work...

But for now... Install your driver following the instruction in this post:
**[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][[B]Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")[/SIZE][/COLOR][/SIZE][/COLOR][/B][COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]

Then that will be out of the way[/SIZE][/COLOR][/SIZE][/COLOR][B][COLOR=Red][SIZE=2][COLOR=Black][SIZE=1].
[/SIZE][/COLOR][/SIZE][/COLOR][/B]

---

### Post by Crimson_Tider on 2011-11-19
That got me into X, but I'm still having problems.  For one, my background is totally white.  I selected a different background, but it is still white.  Another thing is that if I resize a window too large, the contents of the window go totally white.  I looked at the Additional Drivers module, and it shows a list of drivers available.  One of them is activated, nvidia-current, but when I click on it, it says, "Activated, but not currently in use."  I couldn't figure out how to put it "in use."  Is that what I need to do, or something else?

---

### Post by MAFoElffen on 2011-11-19
> **Crimson_Tider said:**
> That got me into X, but I'm still having problems.  For one, my background is totally white.  I selected a different background, but it is still white.  Another thing is that if I resize a window too large, the contents of the window go totally white.  I looked at the Additional Drivers module, and it shows a list of drivers available.  One of them is activated, nvidia-current, but when I click on it, it says, "Activated, but not currently in use."  I couldn't figure out how to put it "in use."  Is that what I need to do, or something else?
White screen eh?  The nvidia workaraound for that is to go back into the Additional Drivers > remove the nvidia-current as active > Then activate the nvidia-173 driver... Ubuntu and NVidia says that error only happens to a minority of people with old hardware. HaHa-boink?!@#$%.  With the nvidia-173 driver, you'll get less performance, but everything should work, including Unity.

The "Activated but not currently in use" is a known jockey problem that they are working on... The message is not an out-and-out lie... It's just "confused."

---

### Post by Crimson_Tider on 2011-11-19
Now it's much worse.  After I rebooted, just as soon as I got past the BIOS screen, my monitor immediately said "Input not supported" and nothing else ever happened.  I know it's a monitor message because it has the name of the monitor, AOC, under it.  Now what do I do?

---

### Post by MAFoElffen on 2011-11-19
> **Crimson_Tider said:**
> Now it's much worse.  After I rebooted, just as soon as I got past the BIOS screen, my monitor immediately said "Input not supported" and nothing else ever happened.  I know it's a monitor message because it has the name of the monitor, AOC, under it.  Now what do I do?
Boot on a LiveCD, open a terminal session,
```

sudo apt-get update
sudo apt-get remove nvidia-*
sudo apt-get install 'uname -r'
sudo apt-get install nvidia-current  
sudo nvidia-xconfig  
sudo reboot

```
Which will get rid of the installed driver and any remnants, make sure it has the files to install and new driver and install the nvidia-current driver. Then it will reboot.

---

### Post by Crimson_Tider on 2011-11-20
How do I open a terminal session now?  Ctrl+Alt+F2 doesn't work anymore.  I saw in another post that I should append the word "text" to the "Run Ubuntu from this USB" menu entry, but that doesn't work either.

---

### Post by MAFoElffen on 2011-11-20
> **Crimson_Tider said:**
> How do I open a terminal session now?  Ctrl+Alt+F2 doesn't work anymore.  I saw in another post that I should append the word "text" to the "Run Ubuntu from this USB" menu entry, but that doesn't work either.
I have an upstream bug open on the "text" boot option not working on the 3.x Kernel... You could use "single" instead... or boot it to the desktop of the live image and press <cntrl><alt><t>

---

### Post by Crimson_Tider on 2011-11-20
When I put in "single," and hit Enter, the screen went black and my monitor put a display message up, "Input not supported."  I waited for a while for it to do something else, but it stayed like that for a long time.  So I eventually gave up and just reinstalled from the live USB again.  I eventually got back to the white background with the same window problem I described earlier, and this time I activated a different driver.  I rebooted, and now I have two activated drivers: nvidia-current, which was the original, and nvidia-current-update or updated.  I can't check to see which one because now the screen has gone back to "Input not supported."  Another problem I'm having is that it is difficult to tell which drivers I've tried and which ones I haven't because they are all named exactly the same thing.  I have to look at the descriptions on the lower part of that window, and even some of those are identical.  Obviously I'm going to need to figure out which driver to try before I try them, because this is going nowhere.

---

### Post by MAFoElffen on 2011-11-20
> **Crimson_Tider said:**
> When I put in "single," and hit Enter, the screen went black and my monitor put a display message up, "Input not supported."  I waited for a while for it to do something else, but it stayed like that for a long time.  So I eventually gave up and just reinstalled from the live USB again.  I eventually got back to the white background with the same window problem I described earlier, and this time I activated a different driver.  I rebooted, and now I have two activated drivers: nvidia-current, which was the original, and nvidia-current-update or updated.  I can't check to see which one because now the screen has gone back to "Input not supported."  Another problem I'm having is that it is difficult to tell which drivers I've tried and which ones I haven't because they are all named exactly the same thing.  I have to look at the descriptions on the lower part of that window, and even some of those are identical.  Obviously I'm going to need to figure out which driver to try before I try them, because this is going nowhere.
You tried:
nvidia-173 - Didn't work at all
nvidia-current - (280.13) Gives you a whitescreen in unity

You haven't tried:
nvidia-current-updates (285.05)
[Nouveau Experimental 3D for NVidia]("http://ubuntuforums.org/showpost.php?p=6592005&postcount=1") (<--Link)

---

### Post by Crimson_Tider on 2011-11-20
One thing I need to know is this: do I need to deactivate each driver after I activate the next one?  Which one does it use if more than one is activated?

---

### Post by MAFoElffen on 2011-11-22
> **Crimson_Tider said:**
> One thing I need to know is this: do I need to deactivate each driver after I activate the next one?  Which one does it use if more than one is activated?
If multiple drivers are loaded/installed, most of the time it has a tendency to just be confused = conflicting modules.

---

### Post by Crimson_Tider on 2011-11-23
Okay, now I have a somewhat useable driver.  I can now see the desktop and the background and all the icons at the side and at the top.  I can also see the contents of all windows.  However, there are still some problems, like the fact that some windows don't have the window sizing buttons at the upper left.  Also when I go to another desktop 7series drivers? screen by hitting Ctrl-Alt-arrow key, all the icons disappear and don't come back until I reboot.  Anyway, I need another driver.  Which would be easier--doing the experimental Nouveau thing or installing a driver that I downloaded from the NVIDIA website for NVIDIA 7 series drivers?

---

### Post by MAFoElffen on 2011-11-24
> **Crimson_Tider said:**
> Okay, now I have a somewhat useable driver.  I can now see the desktop and the background and all the icons at the side and at the top.  I can also see the contents of all windows.  However, there are still some problems, like the fact that some windows don't have the window sizing buttons at the upper left.  Also when I go to another desktop 7series drivers? screen by hitting Ctrl-Alt-arrow key, all the icons disappear and don't come back until I reboot.  Anyway, I need another driver.  Which would be easier--doing the experimental Nouveau thing or installing a driver that I downloaded from the NVIDIA website for NVIDIA 7 series drivers?
I'm thinking the NVidia binaries. Their current works fine for me.  I have two Geforce 9800 GTX's SLI-bridged and another as two Geforce 6800 Utra's SLI-bridged that are up on the drivers that you would use... working just fine.  The disclaimer there, You have different hardware underneath that (so nothing is ever "exactly" the same) and that I've been tweaking X-Windows for 22 years.

The Nouveau driver does work. Not as well performance wise. The same driver for the older Nvidia cards shows up in the Additional Drivers applet, but for the Geforce 6xxx and above, it's a manual affair and quite a chore to install.

---

### Post by Crimson_Tider on 2011-11-24
I downloaded the driver file, used chmod to make it executable, and then tried running it with ./path-to-file.  It gave me an error, saying that I am currently running an X session, so I took that to mean that I need to log out of X and run the command from a console, but I'm having a problem with that because I've only found one way to get to a console that actually works.  That is to insert my live USB stick, choose to install to the hard disk, and after it starts the installation process, click Quit at the first chance I get, and then hit Ctrl+Alt+F1.  The only problem with that is that the prompt shows me logged in as ubuntu@ubuntu.  Is there a way for me to switch to my usual username from this?  I think all I need to do is run ./home/[driver file name].  By the way, without the live USB stick, holding Shift at boot-up doesn't work, there is no grub menu, as I've seen several posts allude to, pressing Ctrl+Alt+F1 or F2 through F6 when at the desktop doesn't work, and pressing that same combination at bootup anywhere after the BIOS doesn't work.  My computer is determined not to let me access a console to try to fix this problem!

---

### Post by MAFoElffen on 2011-11-25
> **Crimson_Tider said:**
> I downloaded the driver file, used chmod to make it executable, and then tried running it with ./path-to-file.  It gave me an error, saying that I am currently running an X session, so I took that to mean that I need to log out of X and run the command from a console, but I'm having a problem with that because I've only found one way to get to a console that actually works.  That is to insert my live USB stick, choose to install to the hard disk, and after it starts the installation process, click Quit at the first chance I get, and then hit Ctrl+Alt+F1.  The only problem with that is that the prompt shows me logged in as ubuntu@ubuntu.  Is there a way for me to switch to my usual username from this?  I think all I need to do is run ./home/[driver file name].  By the way, without the live USB stick, holding Shift at boot-up doesn't work, there is no grub menu, as I've seen several posts allude to, pressing Ctrl+Alt+F1 or F2 through F6 when at the desktop doesn't work, and pressing that same combination at bootup anywhere after the BIOS doesn't work.  My computer is determined not to let me access a console to try to fix this problem!
No...
```

sudo service lightdm stop

```
Will shut down the X-session if you're using Oneiric. If you're using Natty:
```

sudo service gdm stop

``` 
Please use these instructions:
[[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[URL="http://ubuntuforums.org/showpost.php?p=10909540&postcount=280"]Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")**[/SIZE][/COLOR][/SIZE][/COLOR][/URL]

They have the lastest workarounds included in it.

---

### Post by Crimson_Tider on 2011-11-25
> **MAFoElffen said:**
> No...
```

sudo service lightdm stop

```
Will shut down the X-session if you're using Oneiric. If you're using Natty:
```

sudo service gdm stop

``` 
Please use these instructions:
[[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[URL="http://ubuntuforums.org/showpost.php?p=10909540&postcount=280"]Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")**[/SIZE][/COLOR][/SIZE][/COLOR][/URL]

They have the lastest workarounds included in it.

I did the sudo service lightdm stop command first, and it worked.  However, after I went to your link directly above and got to Step 5, "Reboot into a text console," that command no longer worked.  There was another link on that page that said, "Temporarily booting into a TTY text console" which told me to hold the Shift key down at boot, which doesn't work.  All my computer will do now is go through the BIOS screen.  Directly after that, my monitor tells me "Input not supported".  That's it, although I have learned that Ctrl-Alt-Del still can reboot the computer.  Other than that, I have no control after the BIOS screen.

---

### Post by MAFoElffen on 2011-11-25
> **Crimson_Tider said:**
> I did the sudo service lightdm stop command first, and it worked.  However, after I went to your link directly above and got to Step 5, "Reboot into a text console," that command no longer worked.  There was another link on that page that said, "Temporarily booting into a TTY text console" which told me to hold the Shift key down at boot, which doesn't work.  All my computer will do now is go through the BIOS screen.  Directly after that, my monitor tells me "Input not supported".  That's it, although I have learned that Ctrl-Alt-Del still can reboot the computer.  Other than that, I have no control after the BIOS screen.
If you had the X-Session stopped already, you didn't need to reboot... I guess I need to reread what I wrote and see id I need to clarify that.

Boot on a LiveCD, then follow these instruction to force the Grub menu to display:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Forcing Grub to Show Menu**]("http://ubuntuforums.org/showpost.php?p=11469860&postcount=800")[/SIZE][/COLOR][/SIZE][/COLOR]

While booting the LiveCD, you might need to use the nomodeset boot option from the Advance Install Menu (First half of Post #3 of that same thread). Then follow the link in my last post to boot into a TTY Console.  After that, contunue on with Step 6.

---

### Post by Crimson_Tider on 2011-11-25
> **MAFoElffen said:**
> If you had the X-Session stopped already, you didn't need to reboot... I guess I need to reread what I wrote and see id I need to clarify that.

Boot on a LiveCD, then follow these instruction to force the Grub menu to display:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Forcing Grub to Show Menu**]("http://ubuntuforums.org/showpost.php?p=11469860&postcount=800")[/SIZE][/COLOR][/SIZE][/COLOR]

While booting the LiveCD, you might need to use the nomodeset boot option from the Advance Install Menu (First half of Post #3 of that same thread). Then follow the link in my last post to boot into a TTY Console.  After that, contunue on with Step 6.


No, don't change what you wrote in that other link; it is accurate.  What I meant is that I just tried the "sudo service lightdm stop" command before I started any of your instructions just as a trial.  Then when I started using your instructions, I had to go back into X session because your instructions require using gedit to add lines to blacklist.conf.  So it was after I did all that in X windows that I had the problem.

So here are the results so far of running sh to install the driver:

First of all, I got, "WARNING: Skipping the runlevel check (the utility 'runlevel' failed to run)."  After choosing OK, I got, "WARNING: Unable to open the file '/proc/version' (No such file or directory)."  After choosing OK again, I got, "The CC version check failed: /proc/version does not exist.  If you know what you are doing and want to ignore the gcc version check, select "No" to continue installation.  Otherwise, select "Yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart installation.  Abort now? [Yes or No]"

This sounds okay for me to hit No and continue, but I'll check with you first just to make sure because I've had so many problems already.

---

### Post by MAFoElffen on 2011-11-25
> **Crimson_Tider said:**
> No, don't change what you wrote in that other link; it is accurate.  What I meant is that I just tried the "sudo service lightdm stop" command before I started any of your instructions just as a trial.  Then when I started using your instructions, I had to go back into X session because your instructions require using gedit to add lines to blacklist.conf.  So it was after I did all that in X windows that I had the problem.

So here are the results so far of running sh to install the driver:

First of all, I got, "WARNING: Skipping the runlevel check (the utility 'runlevel' failed to run)."  After choosing OK, I got, "WARNING: Unable to open the file '/proc/version' (No such file or directory)."  After choosing OK again, I got, "The CC version check failed: /proc/version does not exist.  If you know what you are doing and want to ignore the gcc version check, select "No" to continue installation.  Otherwise, select "Yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart installation.  Abort now? [Yes or No]"

This sounds okay for me to hit No and continue, but I'll check with you first just to make sure because I've had so many problems already.
??? The script runs nvidia-installer with all options "forced" to yes.  The frist thing it does is to "verify" the files.  If it is messed up before that though... What version driver did you install?

I'm up on upgraded binary v290.10 64bit.  When it upgraded, it had a "pre-install script failure" message... But it installed okay. Previous v285.13 didn't have that message, that I remember.  

Curious on yours is that GCC isn't found in your path. Thats the default installed compiler for Linux and Unix. The start of my tutorial makes sure it's installed. Do this:
```

gcc --version

```
It it doesn't come up, something is seriously wrong. That would mean not only the Nvidia kernel will not compile--> Other updates won't install without that compiler.

---

### Post by Crimson_Tider on 2011-11-25
> **MAFoElffen said:**
> ??? The script runs nvidia-installer with all options "forced" to yes.  The frist thing it does is to "verify" the files.  If it is messed up before that though... What version driver did you install?

x86 290.10

> **MAFoElffen said:**
> I'm up on upgraded binary v290.10 64bit.  When it upgraded, it had a "pre-install script failure" message... But it installed okay. Previous v285.13 didn't have that message, that I remember.  

Curious on yours is that GCC isn't found in your path. Thats the default installed compiler for Linux and Unix. The start of my tutorial makes sure it's installed. Do this:
```

gcc --version

```
It it doesn't come up, something is seriously wrong. That would mean not only the Nvidia kernel will not compile--> Other updates won't install without that compiler.

It says
```
gcc (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
```
[Copyright . . . disclaimer stuff . . .]

I will say this, also: When I ran
```
sudo apt-get install linux-headers-'uname -r'
```

It gave me
```
Reading package lists. . . Done
Building dependency tree
Reading state information. . . Done
E: Unable to locate package linux-headers-uname -r
```

Does that have anything to do with it?

---

### Post by Crimson_Tider on 2011-11-25
By the way . . . this is off-topic . . . but I think my processor is 64-bit--it is an AMD Sempron 130.  Would it be better for me to install 64-bit Ubuntu even though ubuntu.com doesn't recommend it?  Is there sufficient support for it?

---

### Post by MAFoElffen on 2011-11-26
> **Crimson_Tider said:**
> x86 290.10



It says
```
gcc (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
```[Copyright . . . disclaimer stuff . . .]

I will say this, also: When I ran
```
sudo apt-get install linux-headers-'uname -r'
```It gave me
```
Reading package lists. . . Done
Building dependency tree
Reading state information. . . Done
E: Unable to locate package linux-headers-uname -r
```Does that have anything to do with it?
and what if you run 
```

uname -r

```That should return the Linux kernel version number...
I'm starting to think that you either have a /bin/bash problem or something corrupting your environment variables, like when it can't find the path to GCC or the carry the linux kernel version, etc... If that's what it's doing, then the install script is not going to work, as it uses environment variables. Let me do some research on this and get bak to you. 

On 64bit... Your Sempron is 64bit/single core... My rule of thumb is try with the 64bit LiveCD, if it runs the Live Image, install it. If not, then 32bit. A fresh install on 64bit might clear this issue of weirdness right up... any fresh install should for that matter.  

Something is just real off with that install.  If seems to have amnesia. Lets check it.  Get to a terminal session- <cntrl> <alt><t>
```

echo $SHELL

```Should return /bin/bash

We can see what the environment variables are set to by:
```

env

```Please post the results of that and the ".profile" and ".bashrc" files in your Home directory. Those 2 files can vary those settings for each user.

---

### Post by MAFoElffen on 2011-11-26
I just went back to your 1st post... This was a fresh, new, clean install.  It should not have these bash shell problems. but it does.  I think a fresh install will be a whole lot less work than trying to repair a bad or broken install.  Unless you are practicing patience and learning a lot by this... LOL

Just reinstall. 64bit or 32bit.

Tell me how it goes.

---

### Post by Crimson_Tider on 2011-11-26
Hahaha, this has been a great learning experience so far, so it has been worth it!

---

### Post by Crimson_Tider on 2011-11-26
Now I'm having problems with my USB drive.  I downloaded the 64-bit ISO file, then started Startup Disk Creator.  I've tried it 3 or 4 times, but keep getting error messages and have to quit.  The latest one is

```
"Checksums do not match.  Retry?
```

It gives me that when 38% complete.  I have retried a few times, but it keeps giving me that message.  I noticed a little while ago that my USB drive is giving me some little problems, so I guess I may need to reformat it.  Do you think so, and if so, could you help me through it?

---

### Post by MAFoElffen on 2011-11-26
> **Crimson_Tider said:**
> Now I'm having problems with my USB drive.  I downloaded the 64-bit ISO file, then started Startup Disk Creator.  I've tried it 3 or 4 times, but keep getting error messages and have to quit.  The latest one is

```
"Checksums do not match.  Retry?
```It gives me that when 38% complete.  I have retried a few times, but it keeps giving me that message.  I noticed a little while ago that my USB drive is giving me some little problems, so I guess I may need to reformat it.  Do you think so, and if so, could you help me through it?
Is the message something like "Error Splicing File..."  Yes- reformat. Was having some issue last night with one of my 4GB USB pendrives.

---

### Post by Crimson_Tider on 2011-11-27
After reformatting, when I boot the computer with the USB drive inserted, after the BIOS screen, I get

```
SYSLINUX 4.04 EDD 20110518 Copyright (C) 1994-2011 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot: _
```

I did some searching, and one suggestion I saw was to change the directory on the USB drive called isolinux to syslinux.  I tried that using the mv command, but I got a message saying

```
mv: cannot move `isolinux' to `syslinux': Read-only file system
```

I tried changing permissions using chown, but that didn't work.  I may not be using the command correctly, but I'm not sure.

Just to give you the background information that led me to this point, I had reformatted using GParted instead of Startup Disk Creator, and I chose FAT32.  I had also used a different application to make it bootable this time--Unetbootin.  I ran md5sum on the iso file, and the hash matched up correctly with the hash at [https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes").

---

### Post by MAFoElffen on 2011-11-27
> **Crimson_Tider said:**
> After reformatting, when I boot the computer with the USB drive inserted, after the BIOS screen, I get

```
SYSLINUX 4.04 EDD 20110518 Copyright (C) 1994-2011 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot: _
```I did some searching, and one suggestion I saw was to change the directory on the USB drive called isolinux to syslinux.  I tried that using the mv command, but I got a message saying

```
mv: cannot move `isolinux' to `syslinux': Read-only file system
```I tried changing permissions using chown, but that didn't work.  I may not be using the command correctly, but I'm not sure.

Just to give you the background information that led me to this point, I had reformatted using GParted instead of Startup Disk Creator, and I chose FAT32.  I had also used a different application to make it bootable this time--Unetbootin.  I ran md5sum on the iso file, and the hash matched up correctly with the hash at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).
How many USB ports does it have... Have you tried another port? Does it have a CD/DVD drive?

---

### Post by Crimson_Tider on 2011-11-27
It has 7 USB ports; I've tried 3 of them.  It does have a DVD-writer/CD-writer combo drive.  I guess I could try that, but I've never had any luck installing from CD's.  Besides that, it really seems that I am close to making this work.  If I could just figure out how to change the name of the directory . . .

---

### Post by MAFoElffen on 2011-11-27
> **Crimson_Tider said:**
> It has 7 USB ports; I've tried 3 of them.  It does have a DVD-writer/CD-writer combo drive.  I guess I could try that, but I've never had any luck installing from CD's.  Besides that, it really seems that I am close to making this work.  If I could just figure out how to change the name of the directory . . .
ROTFLMAO!!!! (Picking myself back up) That's what I keep saying in the middle of a project... then I realize it's 3 in the morning... 

What is the host OS that your maying the USB from?

---

### Post by Crimson_Tider on 2011-11-27
> **MAFoElffen said:**
> ROTFLMAO!!!! (Picking myself back up) That's what I keep saying in the middle of a project... then I realize it's 3 in the morning... 

What is the host OS that your maying the USB from?

Ubuntu 11.10 on my msi-U-100 netbook.  But I think I've screwed up my USB drive for good as far as Ubuntu is concerned.  I've tried reformatting it a couple different ways today, and now I get an error message when I insert it in the USB drive; it won't mount now--at least not automatically.  I inserted it in my Windows XP machine and reformatted it there and it seems to be opening fine.  So now I'm going to try to download the 64-bit version in Windows and make it bootable.  Then I'll remove it and insert it into the computer I want Ubuntu on and try again.

---

### Post by Crimson_Tider on 2011-11-28
> **Crimson_Tider said:**
> Ubuntu 11.10 on my msi-U-100 netbook.  But I think I've screwed up my USB drive for good as far as Ubuntu is concerned.  I've tried reformatting it a couple different ways today, and now I get an error message when I insert it in the USB drive; it won't mount now--at least not automatically.  I inserted it in my Windows XP machine and reformatted it there and it seems to be opening fine.  So now I'm going to try to download the 64-bit version in Windows and make it bootable.  Then I'll remove it and insert it into the computer I want Ubuntu on and try again.

I did all that, and when I got about halfway through the installation, I got an error:

```
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk.  It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment. [OK]
```

After I click OK, it says

```
Installer crashed

We're sorry; the installer crashed.  After you close this window, we'll allow you to file a bug report using the integrated bug reporting tool.  This will gather information about your system and the installation process.  The details will be sent to our bug tracker and a developer will attend to the problem as soon as possible.
```

So I tried running fsck on the USB drive, and I got some things that look like errors:

```
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
```

and then it filled up about two screens' worth of the terminal with what I assumed are bad places on the USB drive.  I ran a check in Win XP, and it didn't report any errors.  So how do I fix this (please don't say I have to reformat the drive again :) )?

---

### Post by MAFoElffen on 2011-11-28
> **Crimson_Tider said:**
> I did all that, and when I got about halfway through the installation, I got an error:

```
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk.  It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment. [OK]
```After I click OK, it says

```
Installer crashed

We're sorry; the installer crashed.  After you close this window, we'll allow you to file a bug report using the integrated bug reporting tool.  This will gather information about your system and the installation process.  The details will be sent to our bug tracker and a developer will attend to the problem as soon as possible.
```So I tried running fsck on the USB drive, and I got some things that look like errors:

```
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
```and then it filled up about two screens' worth of the terminal with what I assumed are bad places on the USB drive.  I ran a check in Win XP, and it didn't report any errors.  So how do I fix this (please don't say I have to reformat the drive again :) )?
What brand USB disks?

---

### Post by Crimson_Tider on 2011-11-28
> **MAFoElffen said:**
> What brand USB disks?

Well, that's a good question.  Here's what I got when I ran dmesg:

```

[92834.992218] usb 1-1: new high speed USB device number 12 using ehci_hcd
[92835.128639] scsi12 : usb-storage 1-1:1.0
[92836.129225] scsi 12:0:0:0: Direct-Access     Generic  USB Flash Drive  1.00 PQ: 0 ANSI: 2

```

I guess it has no brand name.  There's no name on the device itself, it didn't come in original packaging, and I bought it on ebay for a really low price, but it's worked great for the 3 1/2 years I've had it.

---

### Post by MAFoElffen on 2011-11-28
> **Crimson_Tider said:**
> Well, that's a good question.  Here's what I got when I ran dmesg:

```

[92834.992218] usb 1-1: new high speed USB device number 12 using ehci_hcd
[92835.128639] scsi12 : usb-storage 1-1:1.0
[92836.129225] scsi 12:0:0:0: Direct-Access     Generic  USB Flash Drive  1.00 PQ: 0 ANSI: 2

```I guess it has no brand name.  There's no name on the device itself, it didn't come in original packaging, and I bought it on ebay for a really low price, but it's worked great for the 3 1/2 years I've had it.
That's longer than some of mine... In the middle of a dev cycle, some of mine get ISO's written to then every day.  At the computer recyler's I volunteer at (for both Win & Linux) and talking with other Ubuntu Testers, we've figured out the do wear out.

One more thing to try "with" it first... PBoot from a LiveCD. Prep it and use the LiveCd creator... use the ISO from your NTFS drive...  But if you had a Real Live**CD** you could install from there... Nevermind.

What is the capaicity that that USB device?

---

### Post by MAFoElffen on 2011-11-29
> **MAFoElffen said:**
> What is the capaicity that that USB device?
Reason I asked was... If you you back off the start of the partition 1 sector, then made the partition to about 2 GB... It might act differently.... Then again squashfs file size is limited at 4BG so that would be under that... Mot that that ISO is anywhere near that, but just trying ideas.

There's also a difference in creating Bootable USB's from Linux and Win7... More success from Linux.

---

### Post by Crimson_Tider on 2011-12-03
Well, I finally gave up on using that generic USB flash drive and bought a Kingston.  I used it yesterday to install the 64-bit Oneiric, and then I used your link here to download and install the most up-to-date NVidia driver: [Installing NVidia binary drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280").  In that same post, I followed your Solution Step II, which starts out with

> Solution Step II
If it still doesn't load, then we came try to load the nvidia kernel before the other modules... We can do that by creating a file called /etc/udev/rules.d/90-modprobe.rules and put a line in it saying:

```
RUN+="/sbin/modprobe nvidia"

```


So now I have a working driver, but there are a few little performance issues.  Firstly, I only have two resolutions to choose from: 1024 x 768 and 800 x 600.  The 1024 x 768 is usable, but it doesn't look great--everything is stretched horizontally because my monitor is 16:9.  Also, my mouse cursor doesn't cooperate totally; it disappears when I hover over some icons and stays invisible until I move it from that spot.  For example, that happens when I go to the System Settings window and hover it over Displays or any of the other icons in the window.  Any way to fix these problems?

---

### Post by Crimson_Tider on 2011-12-05
Anyone out there?

---

### Post by MAFoElffen on 2011-12-06
> **Crimson_Tider said:**
> Anyone out there?
Welcome back!

I'm here.... Hadn't heard from you in a long time. Closed the tab to tmake room to help others.  So only 2 resolution choices eh?

Please post your /var/log/Xorg.0.log and /etc/X11/xorg.conf files.

In those two files, it will show which driver you are using, what video card, what monitor and if all is going right- what resolutions of that display by the EDID data from it.

Another thing that would help is to install a hardware uitlity called hwinfo:
```

sudo apt-get install hwinfo

```And post the results of 
```

sudo hwinfo --monitor
sudo hwinfo --frambuffer
xrandr -q

```

---

### Post by Crimson_Tider on 2011-12-06
> **MAFoElffen said:**
> Welcome back!

I'm here.... Hadn't heard from you in a long time. Closed the tab to tmake room to help others.  So only 2 resolution choices eh?

Please post your /var/log/Xorg.0.log and /etc/X11/xorg.conf files.

In those two files, it will show which driver you are using, what video card, what monitor and if all is going right- what resolutions of that display by the EDID data from it.

Another thing that would help is to install a hardware uitlity called hwinfo:
```

sudo apt-get install hwinfo

```And post the results of 
```

sudo hwinfo --monitor
sudo hwinfo --frambuffer
xrandr -q

```



Contents of /var/log/Xorg.0.log:
```
[    14.162] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    14.162] X Protocol Version 11, Revision 0
[    14.162] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.162] Current Operating System: Linux buddy-N68S3B 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64
[    14.162] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=3d1df573-4446-4d6b-bd3e-7dd3288c1f18 ro quiet splash vt.handoff=7
[    14.162] Build Date: 19 October 2011  05:21:26AM
[    14.162] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    14.162] Current version of pixman: 0.22.2
[    14.162] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.162] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.162] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  6 20:35:12 2011
[    14.168] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.168] (==) No Layout section.  Using the first Screen section.
[    14.168] (==) No screen section available. Using defaults.
[    14.168] (**) |-->Screen "Default Screen Section" (0)
[    14.168] (**) |   |-->Monitor "<default monitor>"
[    14.168] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.169] (==) Automatically adding devices
[    14.169] (==) Automatically enabling devices
[    14.169] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.169] 	Entry deleted from font path.
[    14.169] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.169] 	Entry deleted from font path.
[    14.169] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.169] 	Entry deleted from font path.
[    14.169] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.169] 	Entry deleted from font path.
[    14.169] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.169] 	Entry deleted from font path.
[    14.169] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.169] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.169] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.169] (II) Loader magic: 0x7e0220
[    14.169] (II) Module ABI versions:
[    14.169] 	X.Org ANSI C Emulation: 0.4
[    14.169] 	X.Org Video Driver: 10.0
[    14.169] 	X.Org XInput driver : 12.3
[    14.169] 	X.Org Server Extension : 5.0
[    14.169] (--) PCI:*(0:0:13:0) 10de:03d6:1565:1405 rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdd000000/16777216, BIOS @ 0x????????/131072
[    14.169] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.169] (II) LoadModule: "extmod"
[    14.207] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.207] (II) Module extmod: vendor="X.Org Foundation"
[    14.207] 	compiled for 1.10.4, module version = 1.0.0
[    14.207] 	Module class: X.Org Server Extension
[    14.207] 	ABI class: X.Org Server Extension, version 5.0
[    14.207] (II) Loading extension MIT-SCREEN-SAVER
[    14.207] (II) Loading extension XFree86-VidModeExtension
[    14.207] (II) Loading extension XFree86-DGA
[    14.207] (II) Loading extension DPMS
[    14.207] (II) Loading extension XVideo
[    14.207] (II) Loading extension XVideo-MotionCompensation
[    14.207] (II) Loading extension X-Resource
[    14.207] (II) LoadModule: "dbe"
[    14.207] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.207] (II) Module dbe: vendor="X.Org Foundation"
[    14.208] 	compiled for 1.10.4, module version = 1.0.0
[    14.208] 	Module class: X.Org Server Extension
[    14.208] 	ABI class: X.Org Server Extension, version 5.0
[    14.208] (II) Loading extension DOUBLE-BUFFER
[    14.208] (II) LoadModule: "glx"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.208] (II) Module glx: vendor="X.Org Foundation"
[    14.208] 	compiled for 1.10.4, module version = 1.0.0
[    14.208] 	ABI class: X.Org Server Extension, version 5.0
[    14.208] (==) AIGLX enabled
[    14.208] (II) Loading extension GLX
[    14.208] (II) LoadModule: "record"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.208] (II) Module record: vendor="X.Org Foundation"
[    14.208] 	compiled for 1.10.4, module version = 1.13.0
[    14.208] 	Module class: X.Org Server Extension
[    14.208] 	ABI class: X.Org Server Extension, version 5.0
[    14.208] (II) Loading extension RECORD
[    14.208] (II) LoadModule: "dri"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.208] (II) Module dri: vendor="X.Org Foundation"
[    14.208] 	compiled for 1.10.4, module version = 1.0.0
[    14.208] 	ABI class: X.Org Server Extension, version 5.0
[    14.208] (II) Loading extension XFree86-DRI
[    14.208] (II) LoadModule: "dri2"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.208] (II) Module dri2: vendor="X.Org Foundation"
[    14.208] 	compiled for 1.10.4, module version = 1.2.0
[    14.208] 	ABI class: X.Org Server Extension, version 5.0
[    14.208] (II) Loading extension DRI2
[    14.208] (==) Matched nvidia as autoconfigured driver 0
[    14.208] (==) Matched nouveau as autoconfigured driver 1
[    14.209] (==) Matched nv as autoconfigured driver 2
[    14.209] (==) Matched vesa as autoconfigured driver 3
[    14.209] (==) Matched fbdev as autoconfigured driver 4
[    14.209] (==) Assigned the driver to the xf86ConfigLayout
[    14.209] (II) LoadModule: "nvidia"
[    14.220] (WW) Warning, couldn't open module nvidia
[    14.220] (II) UnloadModule: "nvidia"
[    14.220] (II) Unloading nvidia
[    14.220] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    14.220] (II) LoadModule: "nouveau"
[    14.220] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.221] (II) Module nouveau: vendor="X.Org Foundation"
[    14.221] 	compiled for 1.10.1, module version = 0.0.16
[    14.221] 	Module class: X.Org Video Driver
[    14.221] 	ABI class: X.Org Video Driver, version 10.0
[    14.221] (II) LoadModule: "nv"
[    14.221] (WW) Warning, couldn't open module nv
[    14.221] (II) UnloadModule: "nv"
[    14.221] (II) Unloading nv
[    14.221] (EE) Failed to load module "nv" (module does not exist, 0)
[    14.221] (II) LoadModule: "vesa"
[    14.221] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.221] (II) Module vesa: vendor="X.Org Foundation"
[    14.221] 	compiled for 1.10.2, module version = 2.3.0
[    14.221] 	Module class: X.Org Video Driver
[    14.221] 	ABI class: X.Org Video Driver, version 10.0
[    14.221] (II) LoadModule: "fbdev"
[    14.221] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.221] (II) Module fbdev: vendor="X.Org Foundation"
[    14.221] 	compiled for 1.10.0, module version = 0.4.2
[    14.221] 	ABI class: X.Org Video Driver, version 10.0
[    14.221] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    14.221] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.221] 	RIVA TNT        (NV04)
[    14.221] 	RIVA TNT2       (NV05)
[    14.221] 	GeForce 256     (NV10)
[    14.221] 	GeForce 2       (NV11, NV15)
[    14.221] 	GeForce 4MX     (NV17, NV18)
[    14.221] 	GeForce 3       (NV20)
[    14.222] 	GeForce 4Ti     (NV25, NV28)
[    14.222] 	GeForce FX      (NV3x)
[    14.222] 	GeForce 6       (NV4x)
[    14.222] 	GeForce 7       (G7x)
[    14.222] 	GeForce 8       (G8x)
[    14.222] 	GeForce GTX 200 (NVA0)
[    14.222] 	GeForce GTX 400 (NVC0)
[    14.222] (II) VESA: driver for VESA chipsets: vesa
[    14.222] (II) FBDEV: driver for framebuffer: fbdev
[    14.222] (++) using VT number 7

[    14.222] drmOpenDevice: node name is /dev/dri/card0
[    14.254] drmOpenByBusid: Searching for BusID pci:0000:00:0d.0
[    14.254] drmOpenDevice: node name is /dev/dri/card0
[    14.260] drmOpenByBusid: drmOpenMinor returns -1
[    14.260] drmOpenDevice: node name is /dev/dri/card1
[    14.266] drmOpenByBusid: drmOpenMinor returns -1
[    14.266] drmOpenDevice: node name is /dev/dri/card2
[    14.271] drmOpenByBusid: drmOpenMinor returns -1
[    14.271] drmOpenDevice: node name is /dev/dri/card3
[    14.276] drmOpenByBusid: drmOpenMinor returns -1
[    14.276] drmOpenDevice: node name is /dev/dri/card4
[    14.281] drmOpenByBusid: drmOpenMinor returns -1
[    14.281] drmOpenDevice: node name is /dev/dri/card5
[    14.286] drmOpenByBusid: drmOpenMinor returns -1
[    14.286] drmOpenDevice: node name is /dev/dri/card6
[    14.291] drmOpenByBusid: drmOpenMinor returns -1
[    14.291] drmOpenDevice: node name is /dev/dri/card7
[    14.296] drmOpenByBusid: drmOpenMinor returns -1
[    14.296] drmOpenDevice: node name is /dev/dri/card8
[    14.301] drmOpenByBusid: drmOpenMinor returns -1
[    14.301] drmOpenDevice: node name is /dev/dri/card9
[    14.307] drmOpenByBusid: drmOpenMinor returns -1
[    14.307] drmOpenDevice: node name is /dev/dri/card10
[    14.312] drmOpenByBusid: drmOpenMinor returns -1
[    14.312] drmOpenDevice: node name is /dev/dri/card11
[    14.317] drmOpenByBusid: drmOpenMinor returns -1
[    14.317] drmOpenDevice: node name is /dev/dri/card12
[    14.322] drmOpenByBusid: drmOpenMinor returns -1
[    14.322] drmOpenDevice: node name is /dev/dri/card13
[    14.327] drmOpenByBusid: drmOpenMinor returns -1
[    14.327] drmOpenDevice: node name is /dev/dri/card14
[    14.332] drmOpenByBusid: drmOpenMinor returns -1
[    14.332] drmOpenDevice: node name is /dev/dri/card15
[    14.337] drmOpenByBusid: drmOpenMinor returns -1
[    14.337] drmOpenDevice: node name is /dev/dri/card0
[    14.344] drmOpenDevice: node name is /dev/dri/card0
[    14.349] drmOpenDevice: node name is /dev/dri/card1
[    14.354] drmOpenDevice: node name is /dev/dri/card2
[    14.359] drmOpenDevice: node name is /dev/dri/card3
[    14.365] drmOpenDevice: node name is /dev/dri/card4
[    14.370] drmOpenDevice: node name is /dev/dri/card5
[    14.375] drmOpenDevice: node name is /dev/dri/card6
[    14.380] drmOpenDevice: node name is /dev/dri/card7
[    14.385] drmOpenDevice: node name is /dev/dri/card8
[    14.390] drmOpenDevice: node name is /dev/dri/card9
[    14.395] drmOpenDevice: node name is /dev/dri/card10
[    14.400] drmOpenDevice: node name is /dev/dri/card11
[    14.406] drmOpenDevice: node name is /dev/dri/card12
[    14.411] drmOpenDevice: node name is /dev/dri/card13
[    14.416] drmOpenDevice: node name is /dev/dri/card14
[    14.421] drmOpenDevice: node name is /dev/dri/card15
[    14.426] (EE) [drm] failed to open device
[    14.426] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.426] (WW) Falling back to old probe method for fbdev
[    14.426] (II) Loading sub module "fbdevhw"
[    14.426] (II) LoadModule: "fbdevhw"
[    14.427] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.427] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.427] 	compiled for 1.10.4, module version = 0.0.2
[    14.427] 	ABI class: X.Org Video Driver, version 10.0
[    14.427] (II) Loading sub module "vbe"
[    14.427] (II) LoadModule: "vbe"
[    14.427] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.427] (II) Module vbe: vendor="X.Org Foundation"
[    14.427] 	compiled for 1.10.4, module version = 1.1.0
[    14.427] 	ABI class: X.Org Video Driver, version 10.0
[    14.427] (II) Loading sub module "int10"
[    14.427] (II) LoadModule: "int10"
[    14.427] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.427] (II) Module int10: vendor="X.Org Foundation"
[    14.427] 	compiled for 1.10.4, module version = 1.0.0
[    14.427] 	ABI class: X.Org Video Driver, version 10.0
[    14.427] (II) VESA(0): initializing int10
[    14.432] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    14.441] (II) VESA(0): VESA BIOS detected
[    14.441] (II) VESA(0): VESA VBE Version 3.0
[    14.441] (II) VESA(0): VESA VBE Total Mem: 32768 kB
[    14.441] (II) VESA(0): VESA VBE OEM: NVIDIA
[    14.441] (II) VESA(0): VESA VBE OEM Software Rev: 5.97
[    14.441] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    14.441] (II) VESA(0): VESA VBE OEM Product: MCP61 - mcp61-86
[    14.441] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    14.490] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    14.490] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    14.490] (==) VESA(0): RGB weight 888
[    14.490] (==) VESA(0): Default visual is TrueColor
[    14.491] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.491] (II) Loading sub module "ddc"
[    14.491] (II) LoadModule: "ddc"
[    14.491] (II) Module "ddc" already built-in
[    14.524] (II) VESA(0): VESA VBE DDC supported
[    14.524] (II) VESA(0): VESA VBE DDC Level none
[    14.524] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    14.539] (II) VESA(0): VESA VBE DDC read failed
[    14.540] (II) VESA(0): VESA VBE PanelID read successfully
[    14.540] (II) VESA(0): PanelID returned panel resolution -28952x-32598
[    14.540] (II) VESA(0): ...which I refuse to believe
[    14.540] (II) VESA(0): Searching for matching VESA mode(s):
[    14.541] Mode: 100 (640x400)
[    14.541] 	ModeAttributes: 0x39f
[    14.541] 	WinAAttributes: 0x7
[    14.541] 	WinBAttributes: 0x0
[    14.541] 	WinGranularity: 64
[    14.541] 	WinSize: 64
[    14.541] 	WinASegment: 0xa000
[    14.541] 	WinBSegment: 0x0
[    14.541] 	WinFuncPtr: 0xc0009a73
[    14.541] 	BytesPerScanline: 640
[    14.541] 	XResolution: 640
[    14.541] 	YResolution: 400
[    14.541] 	XCharSize: 8
[    14.541] 	YCharSize: 16
[    14.541] 	NumberOfPlanes: 1
[    14.541] 	BitsPerPixel: 8
[    14.541] 	NumberOfBanks: 1
[    14.541] 	MemoryModel: 4
[    14.541] 	BankSize: 0
[    14.541] 	NumberOfImages: 14
[    14.541] 	RedMaskSize: 0
[    14.541] 	RedFieldPosition: 0
[    14.541] 	GreenMaskSize: 0
[    14.541] 	GreenFieldPosition: 0
[    14.541] 	BlueMaskSize: 0
[    14.541] 	BlueFieldPosition: 0
[    14.541] 	RsvdMaskSize: 0
[    14.541] 	RsvdFieldPosition: 0
[    14.541] 	DirectColorModeInfo: 0
[    14.541] 	PhysBasePtr: 0xc0000000
[    14.541] 	LinBytesPerScanLine: 640
[    14.541] 	BnkNumberOfImagePages: 14
[    14.541] 	LinNumberOfImagePages: 14
[    14.541] 	LinRedMaskSize: 0
[    14.541] 	LinRedFieldPosition: 0
[    14.541] 	LinGreenMaskSize: 0
[    14.541] 	LinGreenFieldPosition: 0
[    14.541] 	LinBlueMaskSize: 0
[    14.541] 	LinBlueFieldPosition: 0
[    14.541] 	LinRsvdMaskSize: 0
[    14.541] 	LinRsvdFieldPosition: 0
[    14.541] 	MaxPixelClock: 229500000
[    14.542] Mode: 101 (640x480)
[    14.542] 	ModeAttributes: 0x39f
[    14.542] 	WinAAttributes: 0x7
[    14.542] 	WinBAttributes: 0x0
[    14.542] 	WinGranularity: 64
[    14.542] 	WinSize: 64
[    14.542] 	WinASegment: 0xa000
[    14.542] 	WinBSegment: 0x0
[    14.542] 	WinFuncPtr: 0xc0009a73
[    14.542] 	BytesPerScanline: 640
[    14.542] 	XResolution: 640
[    14.542] 	YResolution: 480
[    14.542] 	XCharSize: 8
[    14.542] 	YCharSize: 16
[    14.542] 	NumberOfPlanes: 1
[    14.542] 	BitsPerPixel: 8
[    14.542] 	NumberOfBanks: 1
[    14.542] 	MemoryModel: 4
[    14.542] 	BankSize: 0
[    14.542] 	NumberOfImages: 10
[    14.542] 	RedMaskSize: 0
[    14.542] 	RedFieldPosition: 0
[    14.542] 	GreenMaskSize: 0
[    14.542] 	GreenFieldPosition: 0
[    14.542] 	BlueMaskSize: 0
[    14.542] 	BlueFieldPosition: 0
[    14.542] 	RsvdMaskSize: 0
[    14.542] 	RsvdFieldPosition: 0
[    14.542] 	DirectColorModeInfo: 0
[    14.542] 	PhysBasePtr: 0xc0000000
[    14.542] 	LinBytesPerScanLine: 640
[    14.542] 	BnkNumberOfImagePages: 10
[    14.542] 	LinNumberOfImagePages: 10
[    14.542] 	LinRedMaskSize: 0
[    14.542] 	LinRedFieldPosition: 0
[    14.542] 	LinGreenMaskSize: 0
[    14.542] 	LinGreenFieldPosition: 0
[    14.542] 	LinBlueMaskSize: 0
[    14.542] 	LinBlueFieldPosition: 0
[    14.542] 	LinRsvdMaskSize: 0
[    14.542] 	LinRsvdFieldPosition: 0
[    14.542] 	MaxPixelClock: 229500000
[    14.544] Mode: 102 (800x600)
[    14.544] 	ModeAttributes: 0x31f
[    14.544] 	WinAAttributes: 0x7
[    14.544] 	WinBAttributes: 0x0
[    14.544] 	WinGranularity: 64
[    14.544] 	WinSize: 64
[    14.544] 	WinASegment: 0xa000
[    14.544] 	WinBSegment: 0x0
[    14.544] 	WinFuncPtr: 0xc0009a73
[    14.544] 	BytesPerScanline: 100
[    14.544] 	XResolution: 800
[    14.544] 	YResolution: 600
[    14.544] 	XCharSize: 8
[    14.544] 	YCharSize: 16
[    14.544] 	NumberOfPlanes: 4
[    14.544] 	BitsPerPixel: 4
[    14.544] 	NumberOfBanks: 1
[    14.544] 	MemoryModel: 3
[    14.544] 	BankSize: 0
[    14.544] 	NumberOfImages: 14
[    14.544] 	RedMaskSize: 0
[    14.544] 	RedFieldPosition: 0
[    14.544] 	GreenMaskSize: 0
[    14.544] 	GreenFieldPosition: 0
[    14.544] 	BlueMaskSize: 0
[    14.544] 	BlueFieldPosition: 0
[    14.544] 	RsvdMaskSize: 0
[    14.544] 	RsvdFieldPosition: 0
[    14.544] 	DirectColorModeInfo: 0
[    14.544] 	PhysBasePtr: 0x0
[    14.544] 	LinBytesPerScanLine: 100
[    14.544] 	BnkNumberOfImagePages: 14
[    14.544] 	LinNumberOfImagePages: 14
[    14.544] 	LinRedMaskSize: 0
[    14.544] 	LinRedFieldPosition: 0
[    14.544] 	LinGreenMaskSize: 0
[    14.544] 	LinGreenFieldPosition: 0
[    14.544] 	LinBlueMaskSize: 0
[    14.544] 	LinBlueFieldPosition: 0
[    14.544] 	LinRsvdMaskSize: 0
[    14.544] 	LinRsvdFieldPosition: 0
[    14.544] 	MaxPixelClock: 108500000
[    14.545] Mode: 103 (800x600)
[    14.545] 	ModeAttributes: 0x39f
[    14.545] 	WinAAttributes: 0x7
[    14.545] 	WinBAttributes: 0x0
[    14.545] 	WinGranularity: 64
[    14.545] 	WinSize: 64
[    14.545] 	WinASegment: 0xa000
[    14.545] 	WinBSegment: 0x0
[    14.545] 	WinFuncPtr: 0xc0009a73
[    14.545] 	BytesPerScanline: 800
[    14.545] 	XResolution: 800
[    14.545] 	YResolution: 600
[    14.545] 	XCharSize: 8
[    14.545] 	YCharSize: 16
[    14.545] 	NumberOfPlanes: 1
[    14.545] 	BitsPerPixel: 8
[    14.545] 	NumberOfBanks: 1
[    14.545] 	MemoryModel: 4
[    14.545] 	BankSize: 0
[    14.545] 	NumberOfImages: 6
[    14.545] 	RedMaskSize: 0
[    14.545] 	RedFieldPosition: 0
[    14.545] 	GreenMaskSize: 0
[    14.545] 	GreenFieldPosition: 0
[    14.545] 	BlueMaskSize: 0
[    14.545] 	BlueFieldPosition: 0
[    14.545] 	RsvdMaskSize: 0
[    14.545] 	RsvdFieldPosition: 0
[    14.545] 	DirectColorModeInfo: 0
[    14.545] 	PhysBasePtr: 0xc0000000
[    14.545] 	LinBytesPerScanLine: 800
[    14.545] 	BnkNumberOfImagePages: 6
[    14.545] 	LinNumberOfImagePages: 6
[    14.545] 	LinRedMaskSize: 0
[    14.545] 	LinRedFieldPosition: 0
[    14.545] 	LinGreenMaskSize: 0
[    14.545] 	LinGreenFieldPosition: 0
[    14.545] 	LinBlueMaskSize: 0
[    14.545] 	LinBlueFieldPosition: 0
[    14.545] 	LinRsvdMaskSize: 0
[    14.545] 	LinRsvdFieldPosition: 0
[    14.545] 	MaxPixelClock: 229500000
[    14.546] Mode: 104 (1024x768)
[    14.546] 	ModeAttributes: 0x31f
[    14.546] 	WinAAttributes: 0x7
[    14.546] 	WinBAttributes: 0x0
[    14.546] 	WinGranularity: 64
[    14.546] 	WinSize: 64
[    14.546] 	WinASegment: 0xa000
[    14.546] 	WinBSegment: 0x0
[    14.546] 	WinFuncPtr: 0xc0009a73
[    14.546] 	BytesPerScanline: 128
[    14.546] 	XResolution: 1024
[    14.546] 	YResolution: 768
[    14.546] 	XCharSize: 8
[    14.546] 	YCharSize: 16
[    14.546] 	NumberOfPlanes: 4
[    14.546] 	BitsPerPixel: 4
[    14.546] 	NumberOfBanks: 1
[    14.546] 	MemoryModel: 3
[    14.546] 	BankSize: 0
[    14.546] 	NumberOfImages: 6
[    14.546] 	RedMaskSize: 0
[    14.546] 	RedFieldPosition: 0
[    14.546] 	GreenMaskSize: 0
[    14.546] 	GreenFieldPosition: 0
[    14.546] 	BlueMaskSize: 0
[    14.546] 	BlueFieldPosition: 0
[    14.546] 	RsvdMaskSize: 0
[    14.546] 	RsvdFieldPosition: 0
[    14.546] 	DirectColorModeInfo: 0
[    14.546] 	PhysBasePtr: 0x0
[    14.546] 	LinBytesPerScanLine: 128
[    14.546] 	BnkNumberOfImagePages: 6
[    14.546] 	LinNumberOfImagePages: 6
[    14.546] 	LinRedMaskSize: 0
[    14.546] 	LinRedFieldPosition: 0
[    14.546] 	LinGreenMaskSize: 0
[    14.546] 	LinGreenFieldPosition: 0
[    14.546] 	LinBlueMaskSize: 0
[    14.546] 	LinBlueFieldPosition: 0
[    14.546] 	LinRsvdMaskSize: 0
[    14.546] 	LinRsvdFieldPosition: 0
[    14.546] 	MaxPixelClock: 108500000
[    14.548] Mode: 105 (1024x768)
[    14.548] 	ModeAttributes: 0x39f
[    14.548] 	WinAAttributes: 0x7
[    14.548] 	WinBAttributes: 0x0
[    14.548] 	WinGranularity: 64
[    14.548] 	WinSize: 64
[    14.548] 	WinASegment: 0xa000
[    14.548] 	WinBSegment: 0x0
[    14.548] 	WinFuncPtr: 0xc0009a73
[    14.548] 	BytesPerScanline: 1024
[    14.548] 	XResolution: 1024
[    14.548] 	YResolution: 768
[    14.548] 	XCharSize: 8
[    14.548] 	YCharSize: 16
[    14.548] 	NumberOfPlanes: 1
[    14.548] 	BitsPerPixel: 8
[    14.548] 	NumberOfBanks: 1
[    14.548] 	MemoryModel: 4
[    14.548] 	BankSize: 0
[    14.548] 	NumberOfImages: 3
[    14.548] 	RedMaskSize: 0
[    14.548] 	RedFieldPosition: 0
[    14.548] 	GreenMaskSize: 0
[    14.548] 	GreenFieldPosition: 0
[    14.548] 	BlueMaskSize: 0
[    14.548] 	BlueFieldPosition: 0
[    14.548] 	RsvdMaskSize: 0
[    14.548] 	RsvdFieldPosition: 0
[    14.548] 	DirectColorModeInfo: 0
[    14.548] 	PhysBasePtr: 0xc0000000
[    14.548] 	LinBytesPerScanLine: 1024
[    14.548] 	BnkNumberOfImagePages: 3
[    14.548] 	LinNumberOfImagePages: 3
[    14.548] 	LinRedMaskSize: 0
[    14.548] 	LinRedFieldPosition: 0
[    14.548] 	LinGreenMaskSize: 0
[    14.548] 	LinGreenFieldPosition: 0
[    14.548] 	LinBlueMaskSize: 0
[    14.548] 	LinBlueFieldPosition: 0
[    14.548] 	LinRsvdMaskSize: 0
[    14.548] 	LinRsvdFieldPosition: 0
[    14.548] 	MaxPixelClock: 229500000
[    14.549] Mode: 106 (1280x1024)
[    14.549] 	ModeAttributes: 0x31f
[    14.549] 	WinAAttributes: 0x7
[    14.549] 	WinBAttributes: 0x0
[    14.549] 	WinGranularity: 64
[    14.549] 	WinSize: 64
[    14.549] 	WinASegment: 0xa000
[    14.549] 	WinBSegment: 0x0
[    14.549] 	WinFuncPtr: 0xc0009a73
[    14.549] 	BytesPerScanline: 160
[    14.549] 	XResolution: 1280
[    14.549] 	YResolution: 1024
[    14.549] 	XCharSize: 8
[    14.549] 	YCharSize: 16
[    14.549] 	NumberOfPlanes: 4
[    14.549] 	BitsPerPixel: 4
[    14.549] 	NumberOfBanks: 1
[    14.549] 	MemoryModel: 3
[    14.549] 	BankSize: 0
[    14.549] 	NumberOfImages: 3
[    14.549] 	RedMaskSize: 0
[    14.549] 	RedFieldPosition: 0
[    14.549] 	GreenMaskSize: 0
[    14.549] 	GreenFieldPosition: 0
[    14.549] 	BlueMaskSize: 0
[    14.549] 	BlueFieldPosition: 0
[    14.549] 	RsvdMaskSize: 0
[    14.549] 	RsvdFieldPosition: 0
[    14.549] 	DirectColorModeInfo: 0
[    14.549] 	PhysBasePtr: 0x0
[    14.549] 	LinBytesPerScanLine: 160
[    14.549] 	BnkNumberOfImagePages: 3
[    14.549] 	LinNumberOfImagePages: 3
[    14.549] 	LinRedMaskSize: 0
[    14.549] 	LinRedFieldPosition: 0
[    14.549] 	LinGreenMaskSize: 0
[    14.549] 	LinGreenFieldPosition: 0
[    14.549] 	LinBlueMaskSize: 0
[    14.549] 	LinBlueFieldPosition: 0
[    14.549] 	LinRsvdMaskSize: 0
[    14.549] 	LinRsvdFieldPosition: 0
[    14.549] 	MaxPixelClock: 108500000
[    14.550] Mode: 107 (1280x1024)
[    14.550] 	ModeAttributes: 0x39f
[    14.550] 	WinAAttributes: 0x7
[    14.550] 	WinBAttributes: 0x0
[    14.550] 	WinGranularity: 64
[    14.550] 	WinSize: 64
[    14.550] 	WinASegment: 0xa000
[    14.550] 	WinBSegment: 0x0
[    14.550] 	WinFuncPtr: 0xc0009a73
[    14.550] 	BytesPerScanline: 1280
[    14.550] 	XResolution: 1280
[    14.550] 	YResolution: 1024
[    14.550] 	XCharSize: 8
[    14.550] 	YCharSize: 16
[    14.550] 	NumberOfPlanes: 1
[    14.550] 	BitsPerPixel: 8
[    14.550] 	NumberOfBanks: 1
[    14.550] 	MemoryModel: 4
[    14.550] 	BankSize: 0
[    14.550] 	NumberOfImages: 1
[    14.550] 	RedMaskSize: 0
[    14.550] 	RedFieldPosition: 0
[    14.550] 	GreenMaskSize: 0
[    14.550] 	GreenFieldPosition: 0
[    14.550] 	BlueMaskSize: 0
[    14.550] 	BlueFieldPosition: 0
[    14.550] 	RsvdMaskSize: 0
[    14.550] 	RsvdFieldPosition: 0
[    14.550] 	DirectColorModeInfo: 0
[    14.550] 	PhysBasePtr: 0xc0000000
[    14.550] 	LinBytesPerScanLine: 1280
[    14.550] 	BnkNumberOfImagePages: 1
[    14.550] 	LinNumberOfImagePages: 1
[    14.550] 	LinRedMaskSize: 0
[    14.550] 	LinRedFieldPosition: 0
[    14.550] 	LinGreenMaskSize: 0
[    14.550] 	LinGreenFieldPosition: 0
[    14.550] 	LinBlueMaskSize: 0
[    14.550] 	LinBlueFieldPosition: 0
[    14.550] 	LinRsvdMaskSize: 0
[    14.550] 	LinRsvdFieldPosition: 0
[    14.550] 	MaxPixelClock: 229500000
[    14.552] Mode: 10e (320x200)
[    14.552] 	ModeAttributes: 0x39f
[    14.552] 	WinAAttributes: 0x7
[    14.552] 	WinBAttributes: 0x0
[    14.552] 	WinGranularity: 64
[    14.552] 	WinSize: 64
[    14.552] 	WinASegment: 0xa000
[    14.552] 	WinBSegment: 0x0
[    14.552] 	WinFuncPtr: 0xc0009a73
[    14.552] 	BytesPerScanline: 640
[    14.552] 	XResolution: 320
[    14.552] 	YResolution: 200
[    14.552] 	XCharSize: 8
[    14.552] 	YCharSize: 8
[    14.552] 	NumberOfPlanes: 1
[    14.552] 	BitsPerPixel: 16
[    14.552] 	NumberOfBanks: 1
[    14.552] 	MemoryModel: 6
[    14.552] 	BankSize: 0
[    14.552] 	NumberOfImages: 30
[    14.552] 	RedMaskSize: 5
[    14.552] 	RedFieldPosition: 11
[    14.552] 	GreenMaskSize: 6
[    14.552] 	GreenFieldPosition: 5
[    14.552] 	BlueMaskSize: 5
[    14.552] 	BlueFieldPosition: 0
[    14.552] 	RsvdMaskSize: 0
[    14.552] 	RsvdFieldPosition: 0
[    14.552] 	DirectColorModeInfo: 0
[    14.552] 	PhysBasePtr: 0xc0000000
[    14.552] 	LinBytesPerScanLine: 640
[    14.552] 	BnkNumberOfImagePages: 30
[    14.552] 	LinNumberOfImagePages: 30
[    14.552] 	LinRedMaskSize: 5
[    14.552] 	LinRedFieldPosition: 11
[    14.552] 	LinGreenMaskSize: 6
[    14.552] 	LinGreenFieldPosition: 5
[    14.552] 	LinBlueMaskSize: 5
[    14.552] 	LinBlueFieldPosition: 0
[    14.552] 	LinRsvdMaskSize: 0
[    14.552] 	LinRsvdFieldPosition: 0
[    14.552] 	MaxPixelClock: 229500000
[    14.553] *Mode: 10f (320x200)
[    14.553] 	ModeAttributes: 0x39f
[    14.553] 	WinAAttributes: 0x7
[    14.553] 	WinBAttributes: 0x0
[    14.553] 	WinGranularity: 64
[    14.553] 	WinSize: 64
[    14.553] 	WinASegment: 0xa000
[    14.553] 	WinBSegment: 0x0
[    14.553] 	WinFuncPtr: 0xc0009a73
[    14.553] 	BytesPerScanline: 1280
[    14.553] 	XResolution: 320
[    14.553] 	YResolution: 200
[    14.553] 	XCharSize: 8
[    14.553] 	YCharSize: 8
[    14.553] 	NumberOfPlanes: 1
[    14.553] 	BitsPerPixel: 32
[    14.553] 	NumberOfBanks: 1
[    14.553] 	MemoryModel: 6
[    14.553] 	BankSize: 0
[    14.553] 	NumberOfImages: 14
[    14.553] 	RedMaskSize: 8
[    14.553] 	RedFieldPosition: 16
[    14.553] 	GreenMaskSize: 8
[    14.553] 	GreenFieldPosition: 8
[    14.553] 	BlueMaskSize: 8
[    14.553] 	BlueFieldPosition: 0
[    14.553] 	RsvdMaskSize: 8
[    14.553] 	RsvdFieldPosition: 24
[    14.553] 	DirectColorModeInfo: 0
[    14.553] 	PhysBasePtr: 0xc0000000
[    14.553] 	LinBytesPerScanLine: 1280
[    14.553] 	BnkNumberOfImagePages: 14
[    14.553] 	LinNumberOfImagePages: 14
[    14.553] 	LinRedMaskSize: 8
[    14.553] 	LinRedFieldPosition: 16
[    14.553] 	LinGreenMaskSize: 8
[    14.553] 	LinGreenFieldPosition: 8
[    14.553] 	LinBlueMaskSize: 8
[    14.553] 	LinBlueFieldPosition: 0
[    14.553] 	LinRsvdMaskSize: 8
[    14.553] 	LinRsvdFieldPosition: 24
[    14.553] 	MaxPixelClock: 229500000
[    14.555] Mode: 111 (640x480)
[    14.555] 	ModeAttributes: 0x39f
[    14.555] 	WinAAttributes: 0x7
[    14.555] 	WinBAttributes: 0x0
[    14.555] 	WinGranularity: 64
[    14.555] 	WinSize: 64
[    14.555] 	WinASegment: 0xa000
[    14.555] 	WinBSegment: 0x0
[    14.555] 	WinFuncPtr: 0xc0009a73
[    14.555] 	BytesPerScanline: 1280
[    14.555] 	XResolution: 640
[    14.555] 	YResolution: 480
[    14.555] 	XCharSize: 8
[    14.555] 	YCharSize: 16
[    14.555] 	NumberOfPlanes: 1
[    14.555] 	BitsPerPixel: 16
[    14.555] 	NumberOfBanks: 1
[    14.555] 	MemoryModel: 6
[    14.555] 	BankSize: 0
[    14.555] 	NumberOfImages: 4
[    14.555] 	RedMaskSize: 5
[    14.555] 	RedFieldPosition: 11
[    14.555] 	GreenMaskSize: 6
[    14.555] 	GreenFieldPosition: 5
[    14.555] 	BlueMaskSize: 5
[    14.555] 	BlueFieldPosition: 0
[    14.555] 	RsvdMaskSize: 0
[    14.555] 	RsvdFieldPosition: 0
[    14.555] 	DirectColorModeInfo: 0
[    14.555] 	PhysBasePtr: 0xc0000000
[    14.555] 	LinBytesPerScanLine: 1280
[    14.555] 	BnkNumberOfImagePages: 4
[    14.555] 	LinNumberOfImagePages: 4
[    14.555] 	LinRedMaskSize: 5
[    14.555] 	LinRedFieldPosition: 11
[    14.555] 	LinGreenMaskSize: 6
[    14.555] 	LinGreenFieldPosition: 5
[    14.555] 	LinBlueMaskSize: 5
[    14.555] 	LinBlueFieldPosition: 0
[    14.555] 	LinRsvdMaskSize: 0
[    14.555] 	LinRsvdFieldPosition: 0
[    14.555] 	MaxPixelClock: 229500000
[    14.556] *Mode: 112 (640x480)
[    14.556] 	ModeAttributes: 0x39f
[    14.556] 	WinAAttributes: 0x7
[    14.556] 	WinBAttributes: 0x0
[    14.556] 	WinGranularity: 64
[    14.556] 	WinSize: 64
[    14.556] 	WinASegment: 0xa000
[    14.556] 	WinBSegment: 0x0
[    14.556] 	WinFuncPtr: 0xc0009a73
[    14.556] 	BytesPerScanline: 2560
[    14.556] 	XResolution: 640
[    14.556] 	YResolution: 480
[    14.556] 	XCharSize: 8
[    14.556] 	YCharSize: 16
[    14.556] 	NumberOfPlanes: 1
[    14.556] 	BitsPerPixel: 32
[    14.556] 	NumberOfBanks: 1
[    14.556] 	MemoryModel: 6
[    14.556] 	BankSize: 0
[    14.556] 	NumberOfImages: 1
[    14.556] 	RedMaskSize: 8
[    14.556] 	RedFieldPosition: 16
[    14.556] 	GreenMaskSize: 8
[    14.556] 	GreenFieldPosition: 8
[    14.556] 	BlueMaskSize: 8
[    14.556] 	BlueFieldPosition: 0
[    14.556] 	RsvdMaskSize: 8
[    14.556] 	RsvdFieldPosition: 24
[    14.556] 	DirectColorModeInfo: 0
[    14.556] 	PhysBasePtr: 0xc0000000
[    14.556] 	LinBytesPerScanLine: 2560
[    14.556] 	BnkNumberOfImagePages: 1
[    14.556] 	LinNumberOfImagePages: 1
[    14.556] 	LinRedMaskSize: 8
[    14.556] 	LinRedFieldPosition: 16
[    14.556] 	LinGreenMaskSize: 8
[    14.556] 	LinGreenFieldPosition: 8
[    14.556] 	LinBlueMaskSize: 8
[    14.556] 	LinBlueFieldPosition: 0
[    14.556] 	LinRsvdMaskSize: 8
[    14.556] 	LinRsvdFieldPosition: 24
[    14.556] 	MaxPixelClock: 229500000
[    14.558] Mode: 114 (800x600)
[    14.558] 	ModeAttributes: 0x39f
[    14.558] 	WinAAttributes: 0x7
[    14.558] 	WinBAttributes: 0x0
[    14.558] 	WinGranularity: 64
[    14.558] 	WinSize: 64
[    14.558] 	WinASegment: 0xa000
[    14.558] 	WinBSegment: 0x0
[    14.558] 	WinFuncPtr: 0xc0009a73
[    14.558] 	BytesPerScanline: 1600
[    14.558] 	XResolution: 800
[    14.558] 	YResolution: 600
[    14.558] 	XCharSize: 8
[    14.558] 	YCharSize: 16
[    14.558] 	NumberOfPlanes: 1
[    14.558] 	BitsPerPixel: 16
[    14.558] 	NumberOfBanks: 1
[    14.558] 	MemoryModel: 6
[    14.558] 	BankSize: 0
[    14.558] 	NumberOfImages: 2
[    14.558] 	RedMaskSize: 5
[    14.558] 	RedFieldPosition: 11
[    14.558] 	GreenMaskSize: 6
[    14.558] 	GreenFieldPosition: 5
[    14.558] 	BlueMaskSize: 5
[    14.558] 	BlueFieldPosition: 0
[    14.558] 	RsvdMaskSize: 0
[    14.558] 	RsvdFieldPosition: 0
[    14.558] 	DirectColorModeInfo: 0
[    14.558] 	PhysBasePtr: 0xc0000000
[    14.558] 	LinBytesPerScanLine: 1600
[    14.558] 	BnkNumberOfImagePages: 2
[    14.558] 	LinNumberOfImagePages: 2
[    14.558] 	LinRedMaskSize: 5
[    14.558] 	LinRedFieldPosition: 11
[    14.558] 	LinGreenMaskSize: 6
[    14.558] 	LinGreenFieldPosition: 5
[    14.558] 	LinBlueMaskSize: 5
[    14.558] 	LinBlueFieldPosition: 0
[    14.558] 	LinRsvdMaskSize: 0
[    14.558] 	LinRsvdFieldPosition: 0
[    14.558] 	MaxPixelClock: 229500000
[    14.559] *Mode: 115 (800x600)
[    14.559] 	ModeAttributes: 0x39f
[    14.559] 	WinAAttributes: 0x7
[    14.559] 	WinBAttributes: 0x0
[    14.559] 	WinGranularity: 64
[    14.559] 	WinSize: 64
[    14.559] 	WinASegment: 0xa000
[    14.559] 	WinBSegment: 0x0
[    14.559] 	WinFuncPtr: 0xc0009a73
[    14.559] 	BytesPerScanline: 3200
[    14.559] 	XResolution: 800
[    14.559] 	YResolution: 600
[    14.559] 	XCharSize: 8
[    14.559] 	YCharSize: 16
[    14.559] 	NumberOfPlanes: 1
[    14.559] 	BitsPerPixel: 32
[    14.559] 	NumberOfBanks: 1
[    14.559] 	MemoryModel: 6
[    14.559] 	BankSize: 0
[    14.559] 	NumberOfImages: 1
[    14.559] 	RedMaskSize: 8
[    14.559] 	RedFieldPosition: 16
[    14.559] 	GreenMaskSize: 8
[    14.559] 	GreenFieldPosition: 8
[    14.559] 	BlueMaskSize: 8
[    14.559] 	BlueFieldPosition: 0
[    14.559] 	RsvdMaskSize: 8
[    14.559] 	RsvdFieldPosition: 24
[    14.559] 	DirectColorModeInfo: 0
[    14.559] 	PhysBasePtr: 0xc0000000
[    14.559] 	LinBytesPerScanLine: 3200
[    14.559] 	BnkNumberOfImagePages: 1
[    14.559] 	LinNumberOfImagePages: 1
[    14.559] 	LinRedMaskSize: 8
[    14.559] 	LinRedFieldPosition: 16
[    14.559] 	LinGreenMaskSize: 8
[    14.559] 	LinGreenFieldPosition: 8
[    14.559] 	LinBlueMaskSize: 8
[    14.559] 	LinBlueFieldPosition: 0
[    14.559] 	LinRsvdMaskSize: 8
[    14.559] 	LinRsvdFieldPosition: 24
[    14.559] 	MaxPixelClock: 229500000
[    14.560] Mode: 117 (1024x768)
[    14.560] 	ModeAttributes: 0x39f
[    14.560] 	WinAAttributes: 0x7
[    14.560] 	WinBAttributes: 0x0
[    14.560] 	WinGranularity: 64
[    14.560] 	WinSize: 64
[    14.560] 	WinASegment: 0xa000
[    14.560] 	WinBSegment: 0x0
[    14.561] 	WinFuncPtr: 0xc0009a73
[    14.561] 	BytesPerScanline: 2048
[    14.561] 	XResolution: 1024
[    14.561] 	YResolution: 768
[    14.561] 	XCharSize: 8
[    14.561] 	YCharSize: 16
[    14.561] 	NumberOfPlanes: 1
[    14.561] 	BitsPerPixel: 16
[    14.561] 	NumberOfBanks: 1
[    14.561] 	MemoryModel: 6
[    14.561] 	BankSize: 0
[    14.561] 	NumberOfImages: 1
[    14.561] 	RedMaskSize: 5
[    14.561] 	RedFieldPosition: 11
[    14.561] 	GreenMaskSize: 6
[    14.561] 	GreenFieldPosition: 5
[    14.561] 	BlueMaskSize: 5
[    14.561] 	BlueFieldPosition: 0
[    14.561] 	RsvdMaskSize: 0
[    14.561] 	RsvdFieldPosition: 0
[    14.561] 	DirectColorModeInfo: 0
[    14.561] 	PhysBasePtr: 0xc0000000
[    14.561] 	LinBytesPerScanLine: 2048
[    14.561] 	BnkNumberOfImagePages: 1
[    14.561] 	LinNumberOfImagePages: 1
[    14.561] 	LinRedMaskSize: 5
[    14.561] 	LinRedFieldPosition: 11
[    14.561] 	LinGreenMaskSize: 6
[    14.561] 	LinGreenFieldPosition: 5
[    14.561] 	LinBlueMaskSize: 5
[    14.561] 	LinBlueFieldPosition: 0
[    14.561] 	LinRsvdMaskSize: 0
[    14.561] 	LinRsvdFieldPosition: 0
[    14.561] 	MaxPixelClock: 229500000
[    14.562] *Mode: 118 (1024x768)
[    14.562] 	ModeAttributes: 0x39f
[    14.562] 	WinAAttributes: 0x7
[    14.562] 	WinBAttributes: 0x0
[    14.562] 	WinGranularity: 64
[    14.562] 	WinSize: 64
[    14.562] 	WinASegment: 0xa000
[    14.562] 	WinBSegment: 0x0
[    14.562] 	WinFuncPtr: 0xc0009a73
[    14.562] 	BytesPerScanline: 4096
[    14.562] 	XResolution: 1024
[    14.562] 	YResolution: 768
[    14.562] 	XCharSize: 8
[    14.562] 	YCharSize: 16
[    14.562] 	NumberOfPlanes: 1
[    14.562] 	BitsPerPixel: 32
[    14.562] 	NumberOfBanks: 1
[    14.562] 	MemoryModel: 6
[    14.562] 	BankSize: 0
[    14.562] 	NumberOfImages: 1
[    14.562] 	RedMaskSize: 8
[    14.562] 	RedFieldPosition: 16
[    14.562] 	GreenMaskSize: 8
[    14.562] 	GreenFieldPosition: 8
[    14.562] 	BlueMaskSize: 8
[    14.562] 	BlueFieldPosition: 0
[    14.562] 	RsvdMaskSize: 8
[    14.562] 	RsvdFieldPosition: 24
[    14.562] 	DirectColorModeInfo: 0
[    14.562] 	PhysBasePtr: 0xc0000000
[    14.562] 	LinBytesPerScanLine: 4096
[    14.562] 	BnkNumberOfImagePages: 1
[    14.562] 	LinNumberOfImagePages: 1
[    14.562] 	LinRedMaskSize: 8
[    14.562] 	LinRedFieldPosition: 16
[    14.562] 	LinGreenMaskSize: 8
[    14.562] 	LinGreenFieldPosition: 8
[    14.562] 	LinBlueMaskSize: 8
[    14.562] 	LinBlueFieldPosition: 0
[    14.562] 	LinRsvdMaskSize: 8
[    14.562] 	LinRsvdFieldPosition: 24
[    14.562] 	MaxPixelClock: 229500000
[    14.563] Mode: 11a (1280x1024)
[    14.563] 	ModeAttributes: 0x39f
[    14.563] 	WinAAttributes: 0x7
[    14.563] 	WinBAttributes: 0x0
[    14.563] 	WinGranularity: 64
[    14.563] 	WinSize: 64
[    14.563] 	WinASegment: 0xa000
[    14.563] 	WinBSegment: 0x0
[    14.563] 	WinFuncPtr: 0xc0009a73
[    14.563] 	BytesPerScanline: 2560
[    14.563] 	XResolution: 1280
[    14.563] 	YResolution: 1024
[    14.563] 	XCharSize: 8
[    14.563] 	YCharSize: 16
[    14.563] 	NumberOfPlanes: 1
[    14.563] 	BitsPerPixel: 16
[    14.563] 	NumberOfBanks: 1
[    14.563] 	MemoryModel: 6
[    14.563] 	BankSize: 0
[    14.563] 	NumberOfImages: 1
[    14.563] 	RedMaskSize: 5
[    14.563] 	RedFieldPosition: 11
[    14.563] 	GreenMaskSize: 6
[    14.563] 	GreenFieldPosition: 5
[    14.563] 	BlueMaskSize: 5
[    14.563] 	BlueFieldPosition: 0
[    14.563] 	RsvdMaskSize: 0
[    14.563] 	RsvdFieldPosition: 0
[    14.563] 	DirectColorModeInfo: 0
[    14.563] 	PhysBasePtr: 0xc0000000
[    14.563] 	LinBytesPerScanLine: 2560
[    14.563] 	BnkNumberOfImagePages: 1
[    14.563] 	LinNumberOfImagePages: 1
[    14.563] 	LinRedMaskSize: 5
[    14.563] 	LinRedFieldPosition: 11
[    14.563] 	LinGreenMaskSize: 6
[    14.563] 	LinGreenFieldPosition: 5
[    14.563] 	LinBlueMaskSize: 5
[    14.563] 	LinBlueFieldPosition: 0
[    14.563] 	LinRsvdMaskSize: 0
[    14.563] 	LinRsvdFieldPosition: 0
[    14.563] 	MaxPixelClock: 229500000
[    14.565] *Mode: 11b (1280x1024)
[    14.565] 	ModeAttributes: 0x39f
[    14.565] 	WinAAttributes: 0x7
[    14.565] 	WinBAttributes: 0x0
[    14.565] 	WinGranularity: 64
[    14.565] 	WinSize: 64
[    14.565] 	WinASegment: 0xa000
[    14.565] 	WinBSegment: 0x0
[    14.565] 	WinFuncPtr: 0xc0009a73
[    14.565] 	BytesPerScanline: 5120
[    14.565] 	XResolution: 1280
[    14.565] 	YResolution: 1024
[    14.565] 	XCharSize: 8
[    14.565] 	YCharSize: 16
[    14.565] 	NumberOfPlanes: 1
[    14.565] 	BitsPerPixel: 32
[    14.565] 	NumberOfBanks: 1
[    14.565] 	MemoryModel: 6
[    14.565] 	BankSize: 0
[    14.565] 	NumberOfImages: 0
[    14.565] 	RedMaskSize: 8
[    14.565] 	RedFieldPosition: 16
[    14.565] 	GreenMaskSize: 8
[    14.565] 	GreenFieldPosition: 8
[    14.565] 	BlueMaskSize: 8
[    14.565] 	BlueFieldPosition: 0
[    14.565] 	RsvdMaskSize: 8
[    14.565] 	RsvdFieldPosition: 24
[    14.565] 	DirectColorModeInfo: 0
[    14.565] 	PhysBasePtr: 0xc0000000
[    14.565] 	LinBytesPerScanLine: 5120
[    14.565] 	BnkNumberOfImagePages: 0
[    14.565] 	LinNumberOfImagePages: 0
[    14.565] 	LinRedMaskSize: 8
[    14.565] 	LinRedFieldPosition: 16
[    14.565] 	LinGreenMaskSize: 8
[    14.565] 	LinGreenFieldPosition: 8
[    14.565] 	LinBlueMaskSize: 8
[    14.565] 	LinBlueFieldPosition: 0
[    14.565] 	LinRsvdMaskSize: 8
[    14.565] 	LinRsvdFieldPosition: 24
[    14.565] 	MaxPixelClock: 229500000
[    14.566] Mode: 130 (320x200)
[    14.566] 	ModeAttributes: 0x39f
[    14.566] 	WinAAttributes: 0x7
[    14.566] 	WinBAttributes: 0x0
[    14.566] 	WinGranularity: 64
[    14.566] 	WinSize: 64
[    14.566] 	WinASegment: 0xa000
[    14.566] 	WinBSegment: 0x0
[    14.566] 	WinFuncPtr: 0xc0009a73
[    14.566] 	BytesPerScanline: 320
[    14.566] 	XResolution: 320
[    14.566] 	YResolution: 200
[    14.566] 	XCharSize: 8
[    14.566] 	YCharSize: 8
[    14.566] 	NumberOfPlanes: 1
[    14.566] 	BitsPerPixel: 8
[    14.566] 	NumberOfBanks: 1
[    14.566] 	MemoryModel: 4
[    14.566] 	BankSize: 0
[    14.566] 	NumberOfImages: 62
[    14.566] 	RedMaskSize: 0
[    14.566] 	RedFieldPosition: 0
[    14.566] 	GreenMaskSize: 0
[    14.566] 	GreenFieldPosition: 0
[    14.566] 	BlueMaskSize: 0
[    14.566] 	BlueFieldPosition: 0
[    14.566] 	RsvdMaskSize: 0
[    14.566] 	RsvdFieldPosition: 0
[    14.566] 	DirectColorModeInfo: 0
[    14.566] 	PhysBasePtr: 0xc0000000
[    14.566] 	LinBytesPerScanLine: 320
[    14.566] 	BnkNumberOfImagePages: 62
[    14.566] 	LinNumberOfImagePages: 62
[    14.566] 	LinRedMaskSize: 0
[    14.566] 	LinRedFieldPosition: 0
[    14.566] 	LinGreenMaskSize: 0
[    14.566] 	LinGreenFieldPosition: 0
[    14.566] 	LinBlueMaskSize: 0
[    14.566] 	LinBlueFieldPosition: 0
[    14.566] 	LinRsvdMaskSize: 0
[    14.566] 	LinRsvdFieldPosition: 0
[    14.566] 	MaxPixelClock: 229500000
[    14.567] Mode: 131 (320x400)
[    14.567] 	ModeAttributes: 0x39f
[    14.567] 	WinAAttributes: 0x7
[    14.567] 	WinBAttributes: 0x0
[    14.567] 	WinGranularity: 64
[    14.567] 	WinSize: 64
[    14.567] 	WinASegment: 0xa000
[    14.567] 	WinBSegment: 0x0
[    14.567] 	WinFuncPtr: 0xc0009a73
[    14.567] 	BytesPerScanline: 320
[    14.567] 	XResolution: 320
[    14.567] 	YResolution: 400
[    14.567] 	XCharSize: 8
[    14.567] 	YCharSize: 16
[    14.567] 	NumberOfPlanes: 1
[    14.567] 	BitsPerPixel: 8
[    14.567] 	NumberOfBanks: 1
[    14.567] 	MemoryModel: 4
[    14.567] 	BankSize: 0
[    14.567] 	NumberOfImages: 30
[    14.567] 	RedMaskSize: 0
[    14.568] 	RedFieldPosition: 0
[    14.568] 	GreenMaskSize: 0
[    14.568] 	GreenFieldPosition: 0
[    14.568] 	BlueMaskSize: 0
[    14.568] 	BlueFieldPosition: 0
[    14.568] 	RsvdMaskSize: 0
[    14.568] 	RsvdFieldPosition: 0
[    14.568] 	DirectColorModeInfo: 0
[    14.568] 	PhysBasePtr: 0xc0000000
[    14.568] 	LinBytesPerScanLine: 320
[    14.568] 	BnkNumberOfImagePages: 30
[    14.568] 	LinNumberOfImagePages: 30
[    14.568] 	LinRedMaskSize: 0
[    14.568] 	LinRedFieldPosition: 0
[    14.568] 	LinGreenMaskSize: 0
[    14.568] 	LinGreenFieldPosition: 0
[    14.568] 	LinBlueMaskSize: 0
[    14.568] 	LinBlueFieldPosition: 0
[    14.568] 	LinRsvdMaskSize: 0
[    14.568] 	LinRsvdFieldPosition: 0
[    14.568] 	MaxPixelClock: 229500000
[    14.569] Mode: 132 (320x400)
[    14.569] 	ModeAttributes: 0x39f
[    14.569] 	WinAAttributes: 0x7
[    14.569] 	WinBAttributes: 0x0
[    14.569] 	WinGranularity: 64
[    14.569] 	WinSize: 64
[    14.569] 	WinASegment: 0xa000
[    14.569] 	WinBSegment: 0x0
[    14.569] 	WinFuncPtr: 0xc0009a73
[    14.569] 	BytesPerScanline: 640
[    14.569] 	XResolution: 320
[    14.569] 	YResolution: 400
[    14.569] 	XCharSize: 8
[    14.569] 	YCharSize: 16
[    14.569] 	NumberOfPlanes: 1
[    14.569] 	BitsPerPixel: 16
[    14.569] 	NumberOfBanks: 1
[    14.569] 	MemoryModel: 6
[    14.569] 	BankSize: 0
[    14.569] 	NumberOfImages: 14
[    14.569] 	RedMaskSize: 5
[    14.569] 	RedFieldPosition: 11
[    14.569] 	GreenMaskSize: 6
[    14.569] 	GreenFieldPosition: 5
[    14.569] 	BlueMaskSize: 5
[    14.569] 	BlueFieldPosition: 0
[    14.569] 	RsvdMaskSize: 0
[    14.569] 	RsvdFieldPosition: 0
[    14.569] 	DirectColorModeInfo: 0
[    14.569] 	PhysBasePtr: 0xc0000000
[    14.569] 	LinBytesPerScanLine: 640
[    14.569] 	BnkNumberOfImagePages: 14
[    14.569] 	LinNumberOfImagePages: 14
[    14.569] 	LinRedMaskSize: 5
[    14.569] 	LinRedFieldPosition: 11
[    14.569] 	LinGreenMaskSize: 6
[    14.569] 	LinGreenFieldPosition: 5
[    14.569] 	LinBlueMaskSize: 5
[    14.569] 	LinBlueFieldPosition: 0
[    14.569] 	LinRsvdMaskSize: 0
[    14.569] 	LinRsvdFieldPosition: 0
[    14.569] 	MaxPixelClock: 229500000
[    14.570] *Mode: 133 (320x400)
[    14.570] 	ModeAttributes: 0x39f
[    14.570] 	WinAAttributes: 0x7
[    14.570] 	WinBAttributes: 0x0
[    14.570] 	WinGranularity: 64
[    14.570] 	WinSize: 64
[    14.570] 	WinASegment: 0xa000
[    14.570] 	WinBSegment: 0x0
[    14.570] 	WinFuncPtr: 0xc0009a73
[    14.570] 	BytesPerScanline: 1280
[    14.570] 	XResolution: 320
[    14.570] 	YResolution: 400
[    14.570] 	XCharSize: 8
[    14.570] 	YCharSize: 16
[    14.570] 	NumberOfPlanes: 1
[    14.570] 	BitsPerPixel: 32
[    14.570] 	NumberOfBanks: 1
[    14.570] 	MemoryModel: 6
[    14.570] 	BankSize: 0
[    14.570] 	NumberOfImages: 6
[    14.570] 	RedMaskSize: 8
[    14.570] 	RedFieldPosition: 16
[    14.570] 	GreenMaskSize: 8
[    14.570] 	GreenFieldPosition: 8
[    14.570] 	BlueMaskSize: 8
[    14.570] 	BlueFieldPosition: 0
[    14.570] 	RsvdMaskSize: 8
[    14.570] 	RsvdFieldPosition: 24
[    14.570] 	DirectColorModeInfo: 0
[    14.570] 	PhysBasePtr: 0xc0000000
[    14.570] 	LinBytesPerScanLine: 1280
[    14.570] 	BnkNumberOfImagePages: 6
[    14.570] 	LinNumberOfImagePages: 6
[    14.570] 	LinRedMaskSize: 8
[    14.570] 	LinRedFieldPosition: 16
[    14.570] 	LinGreenMaskSize: 8
[    14.570] 	LinGreenFieldPosition: 8
[    14.570] 	LinBlueMaskSize: 8
[    14.570] 	LinBlueFieldPosition: 0
[    14.570] 	LinRsvdMaskSize: 8
[    14.570] 	LinRsvdFieldPosition: 24
[    14.570] 	MaxPixelClock: 229500000
[    14.572] Mode: 134 (320x240)
[    14.572] 	ModeAttributes: 0x39f
[    14.572] 	WinAAttributes: 0x7
[    14.572] 	WinBAttributes: 0x0
[    14.572] 	WinGranularity: 64
[    14.572] 	WinSize: 64
[    14.572] 	WinASegment: 0xa000
[    14.572] 	WinBSegment: 0x0
[    14.572] 	WinFuncPtr: 0xc0009a73
[    14.572] 	BytesPerScanline: 320
[    14.572] 	XResolution: 320
[    14.572] 	YResolution: 240
[    14.572] 	XCharSize: 8
[    14.572] 	YCharSize: 8
[    14.572] 	NumberOfPlanes: 1
[    14.572] 	BitsPerPixel: 8
[    14.572] 	NumberOfBanks: 1
[    14.572] 	MemoryModel: 4
[    14.572] 	BankSize: 0
[    14.572] 	NumberOfImages: 30
[    14.572] 	RedMaskSize: 0
[    14.572] 	RedFieldPosition: 0
[    14.572] 	GreenMaskSize: 0
[    14.572] 	GreenFieldPosition: 0
[    14.572] 	BlueMaskSize: 0
[    14.572] 	BlueFieldPosition: 0
[    14.572] 	RsvdMaskSize: 0
[    14.572] 	RsvdFieldPosition: 0
[    14.572] 	DirectColorModeInfo: 0
[    14.572] 	PhysBasePtr: 0xc0000000
[    14.572] 	LinBytesPerScanLine: 320
[    14.572] 	BnkNumberOfImagePages: 30
[    14.572] 	LinNumberOfImagePages: 30
[    14.572] 	LinRedMaskSize: 0
[    14.572] 	LinRedFieldPosition: 0
[    14.572] 	LinGreenMaskSize: 0
[    14.572] 	LinGreenFieldPosition: 0
[    14.572] 	LinBlueMaskSize: 0
[    14.572] 	LinBlueFieldPosition: 0
[    14.572] 	LinRsvdMaskSize: 0
[    14.572] 	LinRsvdFieldPosition: 0
[    14.572] 	MaxPixelClock: 229500000
[    14.573] Mode: 135 (320x240)
[    14.573] 	ModeAttributes: 0x39f
[    14.573] 	WinAAttributes: 0x7
[    14.573] 	WinBAttributes: 0x0
[    14.573] 	WinGranularity: 64
[    14.573] 	WinSize: 64
[    14.573] 	WinASegment: 0xa000
[    14.573] 	WinBSegment: 0x0
[    14.573] 	WinFuncPtr: 0xc0009a73
[    14.573] 	BytesPerScanline: 640
[    14.573] 	XResolution: 320
[    14.573] 	YResolution: 240
[    14.573] 	XCharSize: 8
[    14.573] 	YCharSize: 8
[    14.573] 	NumberOfPlanes: 1
[    14.573] 	BitsPerPixel: 16
[    14.573] 	NumberOfBanks: 1
[    14.573] 	MemoryModel: 6
[    14.573] 	BankSize: 0
[    14.573] 	NumberOfImages: 19
[    14.573] 	RedMaskSize: 5
[    14.573] 	RedFieldPosition: 11
[    14.573] 	GreenMaskSize: 6
[    14.573] 	GreenFieldPosition: 5
[    14.573] 	BlueMaskSize: 5
[    14.573] 	BlueFieldPosition: 0
[    14.573] 	RsvdMaskSize: 0
[    14.573] 	RsvdFieldPosition: 0
[    14.573] 	DirectColorModeInfo: 0
[    14.573] 	PhysBasePtr: 0xc0000000
[    14.573] 	LinBytesPerScanLine: 640
[    14.573] 	BnkNumberOfImagePages: 19
[    14.573] 	LinNumberOfImagePages: 19
[    14.573] 	LinRedMaskSize: 5
[    14.573] 	LinRedFieldPosition: 11
[    14.573] 	LinGreenMaskSize: 6
[    14.573] 	LinGreenFieldPosition: 5
[    14.573] 	LinBlueMaskSize: 5
[    14.573] 	LinBlueFieldPosition: 0
[    14.573] 	LinRsvdMaskSize: 0
[    14.573] 	LinRsvdFieldPosition: 0
[    14.573] 	MaxPixelClock: 229500000
[    14.574] *Mode: 136 (320x240)
[    14.574] 	ModeAttributes: 0x39f
[    14.574] 	WinAAttributes: 0x7
[    14.574] 	WinBAttributes: 0x0
[    14.574] 	WinGranularity: 64
[    14.574] 	WinSize: 64
[    14.574] 	WinASegment: 0xa000
[    14.574] 	WinBSegment: 0x0
[    14.574] 	WinFuncPtr: 0xc0009a73
[    14.574] 	BytesPerScanline: 1280
[    14.574] 	XResolution: 320
[    14.574] 	YResolution: 240
[    14.574] 	XCharSize: 8
[    14.574] 	YCharSize: 8
[    14.574] 	NumberOfPlanes: 1
[    14.574] 	BitsPerPixel: 32
[    14.574] 	NumberOfBanks: 1
[    14.574] 	MemoryModel: 6
[    14.574] 	BankSize: 0
[    14.574] 	NumberOfImages: 10
[    14.574] 	RedMaskSize: 8
[    14.574] 	RedFieldPosition: 16
[    14.574] 	GreenMaskSize: 8
[    14.574] 	GreenFieldPosition: 8
[    14.574] 	BlueMaskSize: 8
[    14.574] 	BlueFieldPosition: 0
[    14.574] 	RsvdMaskSize: 8
[    14.574] 	RsvdFieldPosition: 24
[    14.574] 	DirectColorModeInfo: 0
[    14.574] 	PhysBasePtr: 0xc0000000
[    14.574] 	LinBytesPerScanLine: 1280
[    14.574] 	BnkNumberOfImagePages: 10
[    14.574] 	LinNumberOfImagePages: 10
[    14.574] 	LinRedMaskSize: 8
[    14.574] 	LinRedFieldPosition: 16
[    14.574] 	LinGreenMaskSize: 8
[    14.574] 	LinGreenFieldPosition: 8
[    14.574] 	LinBlueMaskSize: 8
[    14.574] 	LinBlueFieldPosition: 0
[    14.574] 	LinRsvdMaskSize: 8
[    14.575] 	LinRsvdFieldPosition: 24
[    14.575] 	MaxPixelClock: 229500000
[    14.576] Mode: 13d (640x400)
[    14.576] 	ModeAttributes: 0x39f
[    14.576] 	WinAAttributes: 0x7
[    14.576] 	WinBAttributes: 0x0
[    14.576] 	WinGranularity: 64
[    14.576] 	WinSize: 64
[    14.576] 	WinASegment: 0xa000
[    14.576] 	WinBSegment: 0x0
[    14.576] 	WinFuncPtr: 0xc0009a73
[    14.576] 	BytesPerScanline: 1280
[    14.576] 	XResolution: 640
[    14.576] 	YResolution: 400
[    14.576] 	XCharSize: 8
[    14.576] 	YCharSize: 16
[    14.576] 	NumberOfPlanes: 1
[    14.576] 	BitsPerPixel: 16
[    14.576] 	NumberOfBanks: 1
[    14.576] 	MemoryModel: 6
[    14.576] 	BankSize: 0
[    14.576] 	NumberOfImages: 6
[    14.576] 	RedMaskSize: 5
[    14.576] 	RedFieldPosition: 11
[    14.576] 	GreenMaskSize: 6
[    14.576] 	GreenFieldPosition: 5
[    14.576] 	BlueMaskSize: 5
[    14.576] 	BlueFieldPosition: 0
[    14.576] 	RsvdMaskSize: 0
[    14.576] 	RsvdFieldPosition: 0
[    14.576] 	DirectColorModeInfo: 0
[    14.576] 	PhysBasePtr: 0xc0000000
[    14.576] 	LinBytesPerScanLine: 1280
[    14.576] 	BnkNumberOfImagePages: 6
[    14.576] 	LinNumberOfImagePages: 6
[    14.576] 	LinRedMaskSize: 5
[    14.576] 	LinRedFieldPosition: 11
[    14.576] 	LinGreenMaskSize: 6
[    14.576] 	LinGreenFieldPosition: 5
[    14.576] 	LinBlueMaskSize: 5
[    14.576] 	LinBlueFieldPosition: 0
[    14.576] 	LinRsvdMaskSize: 0
[    14.576] 	LinRsvdFieldPosition: 0
[    14.576] 	MaxPixelClock: 229500000
[    14.577] *Mode: 13e (640x400)
[    14.577] 	ModeAttributes: 0x39f
[    14.577] 	WinAAttributes: 0x7
[    14.577] 	WinBAttributes: 0x0
[    14.577] 	WinGranularity: 64
[    14.577] 	WinSize: 64
[    14.577] 	WinASegment: 0xa000
[    14.577] 	WinBSegment: 0x0
[    14.577] 	WinFuncPtr: 0xc0009a73
[    14.577] 	BytesPerScanline: 2560
[    14.577] 	XResolution: 640
[    14.577] 	YResolution: 400
[    14.577] 	XCharSize: 8
[    14.577] 	YCharSize: 16
[    14.577] 	NumberOfPlanes: 1
[    14.577] 	BitsPerPixel: 32
[    14.577] 	NumberOfBanks: 1
[    14.577] 	MemoryModel: 6
[    14.577] 	BankSize: 0
[    14.577] 	NumberOfImages: 2
[    14.577] 	RedMaskSize: 8
[    14.577] 	RedFieldPosition: 16
[    14.577] 	GreenMaskSize: 8
[    14.577] 	GreenFieldPosition: 8
[    14.577] 	BlueMaskSize: 8
[    14.577] 	BlueFieldPosition: 0
[    14.577] 	RsvdMaskSize: 8
[    14.577] 	RsvdFieldPosition: 24
[    14.577] 	DirectColorModeInfo: 0
[    14.577] 	PhysBasePtr: 0xc0000000
[    14.577] 	LinBytesPerScanLine: 2560
[    14.577] 	BnkNumberOfImagePages: 2
[    14.577] 	LinNumberOfImagePages: 2
[    14.577] 	LinRedMaskSize: 8
[    14.577] 	LinRedFieldPosition: 16
[    14.577] 	LinGreenMaskSize: 8
[    14.577] 	LinGreenFieldPosition: 8
[    14.577] 	LinBlueMaskSize: 8
[    14.577] 	LinBlueFieldPosition: 0
[    14.577] 	LinRsvdMaskSize: 8
[    14.577] 	LinRsvdFieldPosition: 24
[    14.577] 	MaxPixelClock: 229500000
[    14.579] Mode: 145 (1600x1200)
[    14.579] 	ModeAttributes: 0x39f
[    14.579] 	WinAAttributes: 0x7
[    14.579] 	WinBAttributes: 0x0
[    14.579] 	WinGranularity: 64
[    14.579] 	WinSize: 64
[    14.579] 	WinASegment: 0xa000
[    14.579] 	WinBSegment: 0x0
[    14.579] 	WinFuncPtr: 0xc0009a73
[    14.579] 	BytesPerScanline: 1600
[    14.579] 	XResolution: 1600
[    14.579] 	YResolution: 1200
[    14.579] 	XCharSize: 8
[    14.579] 	YCharSize: 16
[    14.579] 	NumberOfPlanes: 1
[    14.579] 	BitsPerPixel: 8
[    14.579] 	NumberOfBanks: 1
[    14.579] 	MemoryModel: 4
[    14.579] 	BankSize: 0
[    14.579] 	NumberOfImages: 1
[    14.579] 	RedMaskSize: 0
[    14.579] 	RedFieldPosition: 0
[    14.579] 	GreenMaskSize: 0
[    14.579] 	GreenFieldPosition: 0
[    14.579] 	BlueMaskSize: 0
[    14.579] 	BlueFieldPosition: 0
[    14.579] 	RsvdMaskSize: 0
[    14.579] 	RsvdFieldPosition: 0
[    14.579] 	DirectColorModeInfo: 0
[    14.579] 	PhysBasePtr: 0xc0000000
[    14.579] 	LinBytesPerScanLine: 1600
[    14.579] 	BnkNumberOfImagePages: 1
[    14.579] 	LinNumberOfImagePages: 1
[    14.579] 	LinRedMaskSize: 0
[    14.579] 	LinRedFieldPosition: 0
[    14.579] 	LinGreenMaskSize: 0
[    14.579] 	LinGreenFieldPosition: 0
[    14.579] 	LinBlueMaskSize: 0
[    14.579] 	LinBlueFieldPosition: 0
[    14.579] 	LinRsvdMaskSize: 0
[    14.579] 	LinRsvdFieldPosition: 0
[    14.579] 	MaxPixelClock: 229500000
[    14.580] Mode: 146 (1600x1200)
[    14.580] 	ModeAttributes: 0x39f
[    14.580] 	WinAAttributes: 0x7
[    14.580] 	WinBAttributes: 0x0
[    14.580] 	WinGranularity: 64
[    14.580] 	WinSize: 64
[    14.580] 	WinASegment: 0xa000
[    14.580] 	WinBSegment: 0x0
[    14.580] 	WinFuncPtr: 0xc0009a73
[    14.580] 	BytesPerScanline: 3200
[    14.580] 	XResolution: 1600
[    14.580] 	YResolution: 1200
[    14.580] 	XCharSize: 8
[    14.580] 	YCharSize: 16
[    14.580] 	NumberOfPlanes: 1
[    14.580] 	BitsPerPixel: 16
[    14.580] 	NumberOfBanks: 1
[    14.580] 	MemoryModel: 6
[    14.580] 	BankSize: 0
[    14.580] 	NumberOfImages: 1
[    14.580] 	RedMaskSize: 5
[    14.580] 	RedFieldPosition: 11
[    14.580] 	GreenMaskSize: 6
[    14.580] 	GreenFieldPosition: 5
[    14.580] 	BlueMaskSize: 5
[    14.580] 	BlueFieldPosition: 0
[    14.580] 	RsvdMaskSize: 0
[    14.580] 	RsvdFieldPosition: 0
[    14.580] 	DirectColorModeInfo: 0
[    14.580] 	PhysBasePtr: 0xc0000000
[    14.580] 	LinBytesPerScanLine: 3200
[    14.580] 	BnkNumberOfImagePages: 1
[    14.580] 	LinNumberOfImagePages: 1
[    14.580] 	LinRedMaskSize: 5
[    14.580] 	LinRedFieldPosition: 11
[    14.580] 	LinGreenMaskSize: 6
[    14.580] 	LinGreenFieldPosition: 5
[    14.580] 	LinBlueMaskSize: 5
[    14.580] 	LinBlueFieldPosition: 0
[    14.580] 	LinRsvdMaskSize: 0
[    14.580] 	LinRsvdFieldPosition: 0
[    14.580] 	MaxPixelClock: 229500000
[    14.582] Mode: 147 (1400x1050)
[    14.582] 	ModeAttributes: 0x39f
[    14.582] 	WinAAttributes: 0x7
[    14.582] 	WinBAttributes: 0x0
[    14.582] 	WinGranularity: 64
[    14.582] 	WinSize: 64
[    14.582] 	WinASegment: 0xa000
[    14.582] 	WinBSegment: 0x0
[    14.582] 	WinFuncPtr: 0xc0009a73
[    14.582] 	BytesPerScanline: 1400
[    14.582] 	XResolution: 1400
[    14.582] 	YResolution: 1050
[    14.582] 	XCharSize: 8
[    14.582] 	YCharSize: 14
[    14.582] 	NumberOfPlanes: 1
[    14.582] 	BitsPerPixel: 8
[    14.582] 	NumberOfBanks: 1
[    14.582] 	MemoryModel: 4
[    14.582] 	BankSize: 0
[    14.582] 	NumberOfImages: 1
[    14.582] 	RedMaskSize: 0
[    14.582] 	RedFieldPosition: 0
[    14.582] 	GreenMaskSize: 0
[    14.582] 	GreenFieldPosition: 0
[    14.582] 	BlueMaskSize: 0
[    14.582] 	BlueFieldPosition: 0
[    14.582] 	RsvdMaskSize: 0
[    14.582] 	RsvdFieldPosition: 0
[    14.582] 	DirectColorModeInfo: 0
[    14.582] 	PhysBasePtr: 0xc0000000
[    14.582] 	LinBytesPerScanLine: 1400
[    14.582] 	BnkNumberOfImagePages: 1
[    14.582] 	LinNumberOfImagePages: 1
[    14.582] 	LinRedMaskSize: 0
[    14.582] 	LinRedFieldPosition: 0
[    14.582] 	LinGreenMaskSize: 0
[    14.582] 	LinGreenFieldPosition: 0
[    14.582] 	LinBlueMaskSize: 0
[    14.582] 	LinBlueFieldPosition: 0
[    14.582] 	LinRsvdMaskSize: 0
[    14.582] 	LinRsvdFieldPosition: 0
[    14.582] 	MaxPixelClock: 229500000
[    14.583] Mode: 148 (1400x1050)
[    14.583] 	ModeAttributes: 0x39f
[    14.583] 	WinAAttributes: 0x7
[    14.583] 	WinBAttributes: 0x0
[    14.583] 	WinGranularity: 64
[    14.583] 	WinSize: 64
[    14.583] 	WinASegment: 0xa000
[    14.583] 	WinBSegment: 0x0
[    14.583] 	WinFuncPtr: 0xc0009a73
[    14.583] 	BytesPerScanline: 2800
[    14.583] 	XResolution: 1400
[    14.583] 	YResolution: 1050
[    14.583] 	XCharSize: 8
[    14.583] 	YCharSize: 14
[    14.583] 	NumberOfPlanes: 1
[    14.583] 	BitsPerPixel: 16
[    14.583] 	NumberOfBanks: 1
[    14.583] 	MemoryModel: 6
[    14.583] 	BankSize: 0
[    14.583] 	NumberOfImages: 1
[    14.583] 	RedMaskSize: 5
[    14.583] 	RedFieldPosition: 11
[    14.583] 	GreenMaskSize: 6
[    14.583] 	GreenFieldPosition: 5
[    14.583] 	BlueMaskSize: 5
[    14.583] 	BlueFieldPosition: 0
[    14.583] 	RsvdMaskSize: 0
[    14.583] 	RsvdFieldPosition: 0
[    14.583] 	DirectColorModeInfo: 0
[    14.583] 	PhysBasePtr: 0xc0000000
[    14.583] 	LinBytesPerScanLine: 2800
[    14.583] 	BnkNumberOfImagePages: 1
[    14.583] 	LinNumberOfImagePages: 1
[    14.583] 	LinRedMaskSize: 5
[    14.583] 	LinRedFieldPosition: 11
[    14.583] 	LinGreenMaskSize: 6
[    14.583] 	LinGreenFieldPosition: 5
[    14.583] 	LinBlueMaskSize: 5
[    14.583] 	LinBlueFieldPosition: 0
[    14.583] 	LinRsvdMaskSize: 0
[    14.583] 	LinRsvdFieldPosition: 0
[    14.583] 	MaxPixelClock: 229500000
[    14.584] *Mode: 152 (2048x1536)
[    14.584] 	ModeAttributes: 0x3db
[    14.584] 	WinAAttributes: 0x7
[    14.584] 	WinBAttributes: 0x0
[    14.584] 	WinGranularity: 64
[    14.584] 	WinSize: 64
[    14.584] 	WinASegment: 0xa000
[    14.585] 	WinBSegment: 0x0
[    14.585] 	WinFuncPtr: 0xc0009a73
[    14.585] 	BytesPerScanline: 8192
[    14.585] 	XResolution: 2048
[    14.585] 	YResolution: 1536
[    14.585] 	XCharSize: 8
[    14.585] 	YCharSize: 16
[    14.585] 	NumberOfPlanes: 1
[    14.585] 	BitsPerPixel: 32
[    14.585] 	NumberOfBanks: 1
[    14.585] 	MemoryModel: 6
[    14.585] 	BankSize: 0
[    14.585] 	NumberOfImages: 0
[    14.585] 	RedMaskSize: 8
[    14.585] 	RedFieldPosition: 16
[    14.585] 	GreenMaskSize: 8
[    14.585] 	GreenFieldPosition: 8
[    14.585] 	BlueMaskSize: 8
[    14.585] 	BlueFieldPosition: 0
[    14.585] 	RsvdMaskSize: 8
[    14.585] 	RsvdFieldPosition: 24
[    14.585] 	DirectColorModeInfo: 0
[    14.585] 	PhysBasePtr: 0xc0000000
[    14.585] 	LinBytesPerScanLine: 8192
[    14.585] 	BnkNumberOfImagePages: 0
[    14.585] 	LinNumberOfImagePages: 0
[    14.585] 	LinRedMaskSize: 8
[    14.585] 	LinRedFieldPosition: 16
[    14.585] 	LinGreenMaskSize: 8
[    14.585] 	LinGreenFieldPosition: 8
[    14.585] 	LinBlueMaskSize: 8
[    14.585] 	LinBlueFieldPosition: 0
[    14.585] 	LinRsvdMaskSize: 8
[    14.585] 	LinRsvdFieldPosition: 24
[    14.585] 	MaxPixelClock: 229500000
[    14.585] 
[    14.585] (II) VESA(0): Total Memory: 512 64KB banks (32768kB)
[    14.585] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    14.585] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    14.585] (II) VESA(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    14.585] (WW) VESA(0): Unable to estimate virtual size
[    14.585] (II) VESA(0): Not using built-in mode "2048x1536" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    14.585] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    14.585] (II) VESA(0): <default monitor>: Using hsync range of 31.50-48.00 kHz
[    14.585] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    14.585] (II) VESA(0): <default monitor>: Using maximum pixel clock of 65.00 MHz
[    14.585] (WW) VESA(0): Unable to estimate virtual size
[    14.585] (II) VESA(0): Not using built-in mode "2048x1536" (hsync out of range)
[    14.585] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[    14.585] (II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
[    14.585] (II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
[    14.585] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    14.585] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    14.585] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    14.585] (**) VESA(0): *Built-in mode "1024x768"
[    14.585] (**) VESA(0): *Built-in mode "800x600"
[    14.585] (**) VESA(0): *Built-in mode "640x480"
[    14.585] (==) VESA(0): DPI set to (96, 96)
[    14.585] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    14.587] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    14.588] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    14.590] (**) VESA(0): Using "Shadow Framebuffer"
[    14.590] (II) Loading sub module "shadow"
[    14.590] (II) LoadModule: "shadow"
[    14.590] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    14.590] (II) Module shadow: vendor="X.Org Foundation"
[    14.590] 	compiled for 1.10.4, module version = 1.1.0
[    14.590] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.590] (II) Loading sub module "fb"
[    14.590] (II) LoadModule: "fb"
[    14.590] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.590] (II) Module fb: vendor="X.Org Foundation"
[    14.590] 	compiled for 1.10.4, module version = 1.0.0
[    14.590] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.590] (II) UnloadModule: "fbdev"
[    14.590] (II) Unloading fbdev
[    14.590] (II) UnloadModule: "fbdevhw"
[    14.590] (II) Unloading fbdevhw
[    14.590] (==) Depth 24 pixmap format is 32 bpp
[    14.590] (II) Loading sub module "int10"
[    14.590] (II) LoadModule: "int10"
[    14.591] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.591] (II) Module int10: vendor="X.Org Foundation"
[    14.591] 	compiled for 1.10.4, module version = 1.0.0
[    14.591] 	ABI class: X.Org Video Driver, version 10.0
[    14.591] (II) VESA(0): initializing int10
[    14.595] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    14.605] (II) VESA(0): VESA BIOS detected
[    14.605] (II) VESA(0): VESA VBE Version 3.0
[    14.605] (II) VESA(0): VESA VBE Total Mem: 32768 kB
[    14.605] (II) VESA(0): VESA VBE OEM: NVIDIA
[    14.605] (II) VESA(0): VESA VBE OEM Software Rev: 5.97
[    14.605] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    14.605] (II) VESA(0): VESA VBE OEM Product: MCP61 - mcp61-86
[    14.605] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    14.608] (II) VESA(0): virtual address = 0x7f6907fad000,
	physical address = 0xc0000000, size = 33554432
[    14.617] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    14.654] (==) VESA(0): Default visual is TrueColor
[    14.654] (==) VESA(0): Backing store disabled
[    14.654] (==) VESA(0): DPMS enabled
[    14.654] (==) RandR enabled
[    14.654] (II) Initializing built-in extension Generic Event Extension
[    14.654] (II) Initializing built-in extension SHAPE
[    14.654] (II) Initializing built-in extension MIT-SHM
[    14.654] (II) Initializing built-in extension XInputExtension
[    14.654] (II) Initializing built-in extension XTEST
[    14.654] (II) Initializing built-in extension BIG-REQUESTS
[    14.654] (II) Initializing built-in extension SYNC
[    14.654] (II) Initializing built-in extension XKEYBOARD
[    14.654] (II) Initializing built-in extension XC-MISC
[    14.654] (II) Initializing built-in extension SECURITY
[    14.654] (II) Initializing built-in extension XINERAMA
[    14.654] (II) Initializing built-in extension XFIXES
[    14.654] (II) Initializing built-in extension RENDER
[    14.654] (II) Initializing built-in extension RANDR
[    14.654] (II) Initializing built-in extension COMPOSITE
[    14.654] (II) Initializing built-in extension DAMAGE
[    14.654] (II) Initializing built-in extension GESTURE
[    14.662] (II) AIGLX: Screen 0 is not DRI2 capable
[    14.662] (II) AIGLX: Screen 0 is not DRI capable
[    14.662] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
[    14.664] (II) AIGLX: Loaded and initialized swrast
[    14.664] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    14.673] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.680] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.680] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.680] (II) LoadModule: "evdev"
[    14.680] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.681] (II) Module evdev: vendor="X.Org Foundation"
[    14.681] 	compiled for 1.10.2, module version = 2.6.0
[    14.681] 	Module class: X.Org XInput Driver
[    14.681] 	ABI class: X.Org XInput driver, version 12.3
[    14.681] (II) Using input driver 'evdev' for 'Power Button'
[    14.681] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.681] (**) Power Button: always reports core events
[    14.681] (**) Power Button: Device: "/dev/input/event1"
[    14.681] (--) Power Button: Found keys
[    14.681] (II) Power Button: Configuring as keyboard
[    14.681] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.681] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.681] (**) Option "xkb_rules" "evdev"
[    14.681] (**) Option "xkb_model" "pc105"
[    14.681] (**) Option "xkb_layout" "us"
[    14.682] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.682] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.682] (II) Using input driver 'evdev' for 'Power Button'
[    14.682] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.682] (**) Power Button: always reports core events
[    14.682] (**) Power Button: Device: "/dev/input/event0"
[    14.683] (--) Power Button: Found keys
[    14.683] (II) Power Button: Configuring as keyboard
[    14.683] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    14.683] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.683] (**) Option "xkb_rules" "evdev"
[    14.683] (**) Option "xkb_model" "pc105"
[    14.683] (**) Option "xkb_layout" "us"
[    14.684] (II) config/udev: Adding input device DELL DELL USB Keyboard (/dev/input/event2)
[    14.684] (**) DELL DELL USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.684] (II) Using input driver 'evdev' for 'DELL DELL USB Keyboard'
[    14.684] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.684] (**) DELL DELL USB Keyboard: always reports core events
[    14.684] (**) DELL DELL USB Keyboard: Device: "/dev/input/event2"
[    14.684] (--) DELL DELL USB Keyboard: Found keys
[    14.684] (II) DELL DELL USB Keyboard: Configuring as keyboard
[    14.684] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input2/event2"
[    14.684] (II) XINPUT: Adding extended input device "DELL DELL USB Keyboard" (type: KEYBOARD)
[    14.684] (**) Option "xkb_rules" "evdev"
[    14.684] (**) Option "xkb_model" "pc105"
[    14.684] (**) Option "xkb_layout" "us"
[    14.685] (II) config/udev: Adding input device DELL DELL USB Keyboard (/dev/input/event3)
[    14.685] (**) DELL DELL USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.685] (II) Using input driver 'evdev' for 'DELL DELL USB Keyboard'
[    14.685] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.685] (**) DELL DELL USB Keyboard: always reports core events
[    14.685] (**) DELL DELL USB Keyboard: Device: "/dev/input/event3"
[    14.685] (--) DELL DELL USB Keyboard: Found keys
[    14.685] (II) DELL DELL USB Keyboard: Configuring as keyboard
[    14.685] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input3/event3"
[    14.685] (II) XINPUT: Adding extended input device "DELL DELL USB Keyboard" (type: KEYBOARD)
[    14.685] (**) Option "xkb_rules" "evdev"
[    14.685] (**) Option "xkb_model" "pc105"
[    14.685] (**) Option "xkb_layout" "us"
[    14.686] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event4)
[    14.686] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    14.686] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    14.686] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.686] (**) USB Optical Mouse: always reports core events
[    14.686] (**) USB Optical Mouse: Device: "/dev/input/event4"
[    14.686] (--) USB Optical Mouse: Found 3 mouse buttons
[    14.686] (--) USB Optical Mouse: Found scroll wheel(s)
[    14.686] (--) USB Optical Mouse: Found relative axes
[    14.686] (--) USB Optical Mouse: Found x and y relative axes
[    14.686] (II) USB Optical Mouse: Configuring as mouse
[    14.686] (II) USB Optical Mouse: Adding scrollwheel support
[    14.686] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    14.686] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.686] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input4/event4"
[    14.686] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    14.686] (II) USB Optical Mouse: initialized for relative axes.
[    14.686] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    14.686] (**) USB Optical Mouse: (accel) acceleration profile 0
[    14.686] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    14.686] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    14.686] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    14.686] (II) No input driver/identifier specified (ignoring)
[    43.237] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
```

My /etc/X11 directory doesn't have a file named xorg.conf as you can see:

```
name@name:/etc/X11$ ls
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config

```

Results from other commands:

```
name@name:/etc/X11$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 3185: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
31: None 00.1: 10000 Monitor                                    
  [Created at monitor.95]
  Unique ID: jyhG.1pU1cwyUUDF
  Hardware Class: monitor
  Model: "AOC 2036"
  Vendor: AOC "AOC"
  Device: eisa 0x2036 "2036"
  Serial ID: "Q8199JA010068"
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@67Hz
  Resolution: 640x480@72Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@56Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@72Hz
  Resolution: 800x600@75Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@70Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x720@60Hz
  Resolution: 1600x900@60Hz
  Size: 443x249 mm
  Detailed Timings #0:
     Resolution: 1600x900
     Horizontal: 1600 1624 1704 1800 (+24 +104 +200) +hsync
       Vertical:  900  901  904 1000 (+1 +4 +100) +vsync
    Frequencies: 108.00 MHz, 60.00 kHz, 60.00 Hz
  Driver Info #0:
    Max. Resolution: 1600x900
    Vert. Sync Range: 55-75 Hz
    Hor. Sync Range: 30-83 kHz
    Bandwidth: 108 MHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
name@name:/etc/X11$ sudo hwinfo --frambuffer
Usage: hwinfo [options]
Probe for hardware.
  --short        just a short listing
  --log logfile  write info to logfile
  --debug level  set debuglevel
  --version      show libhd version
  --dump-db n    dump hardware data base, 0: external, 1: internal
  --hw_item      probe for hw_item
  hw_item is one of:
   all, bios, block, bluetooth, braille, bridge, camera, cdrom, chipcard,
   cpu, disk, dsl, dvb, fingerprint, floppy, framebuffer, gfxcard, hub,
   ide, isapnp, isdn, joystick, keyboard, memory, modem, monitor, mouse,
   netcard, network, partition, pci, pcmcia, pcmcia-ctrl, pppoe, printer,
   scanner, scsi, smp, sound, storage-ctrl, sys, tape, tv, usb, usb-ctrl,
   vbe, wlan, zip

  Note: debug info is shown only in the log file. (If you specify a
  log file the debug level is implicitly set to a reasonable value.)
name@name:/etc/X11$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  

```

By the way, thanks for the tons of help you've given!

---

### Post by MAFoElffen on 2011-12-07
> **Crimson_Tider said:**
> Contents of /var/log/Xorg.0.log:
```
[    14.162] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    14.162] X Protocol Version 11, Revision 0
[    14.162] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.162] Current Operating System: Linux buddy-N68S3B 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64
[    14.162] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=3d1df573-4446-4d6b-bd3e-7dd3288c1f18 ro quiet splash vt.handoff=7
[    14.162] Build Date: 19 October 2011  05:21:26AM
[    14.162] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    14.162] Current version of pixman: 0.22.2
[    14.162]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.162] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.162] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  6 20:35:12 2011
[    14.168] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.168] (==) No Layout section.  Using the first Screen section.
[    14.168] (==) No screen section available. Using defaults.
[    14.168] (**) |-->Screen "Default Screen Section" (0)
[    14.168] (**) |   |-->Monitor "<default monitor>"
[    14.168] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.169] (==) Automatically adding devices
[    14.169] (==) Automatically enabling devices
[    14.169] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.169]     Entry deleted from font path.
[    14.169] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.169]     Entry deleted from font path.
[    14.169] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.169]     Entry deleted from font path.
[    14.169] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.169]     Entry deleted from font path.
[    14.169] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.169]     Entry deleted from font path.
[    14.169] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.169] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.169] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.169] (II) Loader magic: 0x7e0220
[    14.169] (II) Module ABI versions:
[    14.169]     X.Org ANSI C Emulation: 0.4
[    14.169]     X.Org Video Driver: 10.0
[    14.169]     X.Org XInput driver : 12.3
[    14.169]     X.Org Server Extension : 5.0
[    14.169] (--) PCI:*(0:0:13:0) 10de:03d6:1565:1405 rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdd000000/16777216, BIOS @ 0x????????/131072
[    14.169] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.169] (II) LoadModule: "extmod"
[    14.207] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.207] (II) Module extmod: vendor="X.Org Foundation"
[    14.207]     compiled for 1.10.4, module version = 1.0.0
[    14.207]     Module class: X.Org Server Extension
[    14.207]     ABI class: X.Org Server Extension, version 5.0
[    14.207] (II) Loading extension MIT-SCREEN-SAVER
[    14.207] (II) Loading extension XFree86-VidModeExtension
[    14.207] (II) Loading extension XFree86-DGA
[    14.207] (II) Loading extension DPMS
[    14.207] (II) Loading extension XVideo
[    14.207] (II) Loading extension XVideo-MotionCompensation
[    14.207] (II) Loading extension X-Resource
[    14.207] (II) LoadModule: "dbe"
[    14.207] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.207] (II) Module dbe: vendor="X.Org Foundation"
[    14.208]     compiled for 1.10.4, module version = 1.0.0
[    14.208]     Module class: X.Org Server Extension
[    14.208]     ABI class: X.Org Server Extension, version 5.0
[    14.208] (II) Loading extension DOUBLE-BUFFER
[    14.208] (II) LoadModule: "glx"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.208] (II) Module glx: vendor="X.Org Foundation"
[    14.208]     compiled for 1.10.4, module version = 1.0.0
[    14.208]     ABI class: X.Org Server Extension, version 5.0
[    14.208] (==) AIGLX enabled
[    14.208] (II) Loading extension GLX
[    14.208] (II) LoadModule: "record"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.208] (II) Module record: vendor="X.Org Foundation"
[    14.208]     compiled for 1.10.4, module version = 1.13.0
[    14.208]     Module class: X.Org Server Extension
[    14.208]     ABI class: X.Org Server Extension, version 5.0
[    14.208] (II) Loading extension RECORD
[    14.208] (II) LoadModule: "dri"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.208] (II) Module dri: vendor="X.Org Foundation"
[    14.208]     compiled for 1.10.4, module version = 1.0.0
[    14.208]     ABI class: X.Org Server Extension, version 5.0
[    14.208] (II) Loading extension XFree86-DRI
[    14.208] (II) LoadModule: "dri2"
[    14.208] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.208] (II) Module dri2: vendor="X.Org Foundation"
[    14.208]     compiled for 1.10.4, module version = 1.2.0
[    14.208]     ABI class: X.Org Server Extension, version 5.0
[    14.208] (II) Loading extension DRI2
[    14.208] (==) Matched nvidia as autoconfigured driver 0
[    14.208] (==) Matched nouveau as autoconfigured driver 1
[    14.209] (==) Matched nv as autoconfigured driver 2
[    14.209] (==) Matched vesa as autoconfigured driver 3
[    14.209] (==) Matched fbdev as autoconfigured driver 4
[    14.209] (==) Assigned the driver to the xf86ConfigLayout
[    14.209] (II) LoadModule: "nvidia"
[    14.220] (WW) Warning, couldn't open module nvidia
[    14.220] (II) UnloadModule: "nvidia"
[    14.220] (II) Unloading nvidia
[    14.220] ([COLOR=Red]EE) Failed to load module "nvidia" (module does not exist, 0)[/COLOR]
[    14.220] (II) LoadModule: "nouveau"
[    14.220] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.221] (II) Module nouveau: vendor="X.Org Foundation"
[    14.221]     compiled for 1.10.1, module version = 0.0.16
[    14.221]     Module class: X.Org Video Driver
[    14.221]     ABI class: X.Org Video Driver, version 10.0
[    14.221] (II) LoadModule: "nv"
[    14.221] (WW) Warning, couldn't open module nv
[    14.221] (II) UnloadModule: "nv"
[    14.221] (II) Unloading nv
[    14.221] (EE) Failed to load module "nv" (module does not exist, 0)
[    14.221] (II) LoadModule: "vesa"
[    14.221] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.221] (II) Module vesa: vendor="X.Org Foundation"
[    14.221]     compiled for 1.10.2, module version = 2.3.0
[    14.221]     Module class: X.Org Video Driver
[    14.221]     ABI class: X.Org Video Driver, version 10.0
[    14.221] (II) LoadModule: "fbdev"
[    14.221] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.221] (II) Module fbdev: vendor="X.Org Foundation"
[    14.221]     compiled for 1.10.0, module version = 0.4.2
[    14.221]     ABI class: X.Org Video Driver, version 10.0
[    14.221] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    14.221] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.221]     RIVA TNT        (NV04)
[    14.221]     RIVA TNT2       (NV05)
[    14.221]     GeForce 256     (NV10)
[    14.221]     GeForce 2       (NV11, NV15)
[    14.221]     GeForce 4MX     (NV17, NV18)
[    14.221]     GeForce 3       (NV20)
[    14.222]     GeForce 4Ti     (NV25, NV28)
[    14.222]     GeForce FX      (NV3x)
[    14.222]     GeForce 6       (NV4x)
[    14.222]     GeForce 7       (G7x)
[    14.222]     GeForce 8       (G8x)
[    14.222]     GeForce GTX 200 (NVA0)
[    14.222]     GeForce GTX 400 (NVC0)
[    14.222] (II) VESA: driver for VESA chipsets: vesa
[    14.222] (II) FBDEV: driver for framebuffer: fbdev
[    14.222] (++) using VT number 7

[    14.222] drmOpenDevice: node name is /dev/dri/card0
[    14.254] drmOpenByBusid: Searching for BusID pci:0000:00:0d.0
[    14.254] drmOpenDevice: node name is /dev/dri/card0
[    14.260] drmOpenByBusid: drmOpenMinor returns -1
[    14.260] drmOpenDevice: node name is /dev/dri/card1
[    14.266] drmOpenByBusid: drmOpenMinor returns -1
[    14.266] drmOpenDevice: node name is /dev/dri/card2
[    14.271] drmOpenByBusid: drmOpenMinor returns -1
[    14.271] drmOpenDevice: node name is /dev/dri/card3
[    14.276] drmOpenByBusid: drmOpenMinor returns -1
[    14.276] drmOpenDevice: node name is /dev/dri/card4
[    14.281] drmOpenByBusid: drmOpenMinor returns -1
[    14.281] drmOpenDevice: node name is /dev/dri/card5
[    14.286] drmOpenByBusid: drmOpenMinor returns -1
[    14.286] drmOpenDevice: node name is /dev/dri/card6
[    14.291] drmOpenByBusid: drmOpenMinor returns -1
[    14.291] drmOpenDevice: node name is /dev/dri/card7
[    14.296] drmOpenByBusid: drmOpenMinor returns -1
[    14.296] drmOpenDevice: node name is /dev/dri/card8
[    14.301] drmOpenByBusid: drmOpenMinor returns -1
[    14.301] drmOpenDevice: node name is /dev/dri/card9
[    14.307] drmOpenByBusid: drmOpenMinor returns -1
[    14.307] drmOpenDevice: node name is /dev/dri/card10
[    14.312] drmOpenByBusid: drmOpenMinor returns -1
[    14.312] drmOpenDevice: node name is /dev/dri/card11
[    14.317] drmOpenByBusid: drmOpenMinor returns -1
[    14.317] drmOpenDevice: node name is /dev/dri/card12
[    14.322] drmOpenByBusid: drmOpenMinor returns -1
[    14.322] drmOpenDevice: node name is /dev/dri/card13
[    14.327] drmOpenByBusid: drmOpenMinor returns -1
[    14.327] drmOpenDevice: node name is /dev/dri/card14
[    14.332] drmOpenByBusid: drmOpenMinor returns -1
[    14.332] drmOpenDevice: node name is /dev/dri/card15
[    14.337] drmOpenByBusid: drmOpenMinor returns -1
[    14.337] drmOpenDevice: node name is /dev/dri/card0
[    14.344] drmOpenDevice: node name is /dev/dri/card0
[    14.349] drmOpenDevice: node name is /dev/dri/card1
[    14.354] drmOpenDevice: node name is /dev/dri/card2
[    14.359] drmOpenDevice: node name is /dev/dri/card3
[    14.365] drmOpenDevice: node name is /dev/dri/card4
[    14.370] drmOpenDevice: node name is /dev/dri/card5
[    14.375] drmOpenDevice: node name is /dev/dri/card6
[    14.380] drmOpenDevice: node name is /dev/dri/card7
[    14.385] drmOpenDevice: node name is /dev/dri/card8
[    14.390] drmOpenDevice: node name is /dev/dri/card9
[    14.395] drmOpenDevice: node name is /dev/dri/card10
[    14.400] drmOpenDevice: node name is /dev/dri/card11
[    14.406] drmOpenDevice: node name is /dev/dri/card12
[    14.411] drmOpenDevice: node name is /dev/dri/card13
[    14.416] drmOpenDevice: node name is /dev/dri/card14
[    14.421] drmOpenDevice: node name is /dev/dri/card15
[    14.426] (EE) [drm] failed to open device
[    14.426] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.426] (WW) Falling back to old probe method for fbdev
[    14.426] (II) Loading sub module "fbdevhw"
[    14.426] (II) LoadModule: "fbdevhw"
[    14.427] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.427] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.427]     compiled for 1.10.4, module version = 0.0.2
[    14.427]     ABI class: X.Org Video Driver, version 10.0
[    14.427] (II) Loading sub module "vbe"
[    14.427] (II) LoadModule: "vbe"
[    14.427] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.427] (II) Module vbe: vendor="X.Org Foundation"
[    14.427]     compiled for 1.10.4, module version = 1.1.0
[    14.427]     ABI class: X.Org Video Driver, version 10.0
[    14.427] (II) Loading sub module "int10"
[    14.427] (II) LoadModule: "int10"
[    14.427] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.427] (II) Module int10: vendor="X.Org Foundation"
[    14.427]     compiled for 1.10.4, module version = 1.0.0
[    14.427]     ABI class: X.Org Video Driver, version 10.0
[    14.427] (II) VESA(0): initializing int10
[    14.432] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    14.441] (II) VESA(0): VESA BIOS detected
[    14.441] (II) VESA(0): VESA VBE Version 3.0
[    14.441] (II) VESA(0): VESA VBE Total Mem: 32768 kB
[    14.441] (II) VESA(0): VESA VBE OEM: NVIDIA
[    14.441] (II) VESA(0): VESA VBE OEM Software Rev: 5.97
[    14.441] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    14.441] (II) VESA(0): VESA VBE OEM Product: MCP61 - mcp61-86
[    14.441] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    14.490] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    14.490] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    14.490] (==) VESA(0): RGB weight 888
[    14.490] (==) VESA(0): Default visual is TrueColor
[    14.491] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.491] (II) Loading sub module "ddc"
[    14.491] (II) LoadModule: "ddc"
[    14.491] (II) Module "ddc" already built-in
[    14.524] (II) VESA(0): VESA VBE DDC supported
[    14.524] (II) VESA(0): VESA VBE DDC Level none
[    14.524] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    14.539] (II) VESA(0): VESA VBE DDC read failed
[    14.540] (II) VESA(0): VESA VBE PanelID read successfully
[    14.540] (II) VESA(0): PanelID returned panel resolution -28952x-32598
[    14.540] (II) VESA(0): ...which I refuse to believe
[    14.540] (II) VESA(0): Searching for matching VESA mode(s):
[    14.541] Mode: 100 (640x400)
[    14.541]     ModeAttributes: 0x39f
[    14.541]     WinAAttributes: 0x7
[    14.541]     WinBAttributes: 0x0
[    14.541]     WinGranularity: 64
[    14.541]     WinSize: 64
[    14.541]     WinASegment: 0xa000
[    14.541]     WinBSegment: 0x0
[    14.541]     WinFuncPtr: 0xc0009a73
[    14.541]     BytesPerScanline: 640
[    14.541]     XResolution: 640
[    14.541]     YResolution: 400
[    14.541]     XCharSize: 8
[    14.541]     YCharSize: 16
[    14.541]     NumberOfPlanes: 1
[    14.541]     BitsPerPixel: 8
[    14.541]     NumberOfBanks: 1
[    14.541]     MemoryModel: 4
[    14.541]     BankSize: 0
[    14.541]     NumberOfImages: 14
[    14.541]     RedMaskSize: 0
[    14.541]     RedFieldPosition: 0
[    14.541]     GreenMaskSize: 0
[    14.541]     GreenFieldPosition: 0
[    14.541]     BlueMaskSize: 0
[    14.541]     BlueFieldPosition: 0
[    14.541]     RsvdMaskSize: 0
[    14.541]     RsvdFieldPosition: 0
[    14.541]     DirectColorModeInfo: 0
[    14.541]     PhysBasePtr: 0xc0000000
[    14.541]     LinBytesPerScanLine: 640
[    14.541]     BnkNumberOfImagePages: 14
[    14.541]     LinNumberOfImagePages: 14
[    14.541]     LinRedMaskSize: 0
[    14.541]     LinRedFieldPosition: 0
[    14.541]     LinGreenMaskSize: 0
[    14.541]     LinGreenFieldPosition: 0
[    14.541]     LinBlueMaskSize: 0
[    14.541]     LinBlueFieldPosition: 0
[    14.541]     LinRsvdMaskSize: 0
[    14.541]     LinRsvdFieldPosition: 0
[    14.541]     MaxPixelClock: 229500000
[    14.542] Mode: 101 (640x480)
[    14.542]     ModeAttributes: 0x39f
[    14.542]     WinAAttributes: 0x7
[    14.542]     WinBAttributes: 0x0
[    14.542]     WinGranularity: 64
[    14.542]     WinSize: 64
[    14.542]     WinASegment: 0xa000
[    14.542]     WinBSegment: 0x0
[    14.542]     WinFuncPtr: 0xc0009a73
[    14.542]     BytesPerScanline: 640
[    14.542]     XResolution: 640
[    14.542]     YResolution: 480
[    14.542]     XCharSize: 8
[    14.542]     YCharSize: 16
[    14.542]     NumberOfPlanes: 1
[    14.542]     BitsPerPixel: 8
[    14.542]     NumberOfBanks: 1
[    14.542]     MemoryModel: 4
[    14.542]     BankSize: 0
[    14.542]     NumberOfImages: 10
[    14.542]     RedMaskSize: 0
[    14.542]     RedFieldPosition: 0
[    14.542]     GreenMaskSize: 0
[    14.542]     GreenFieldPosition: 0
[    14.542]     BlueMaskSize: 0
[    14.542]     BlueFieldPosition: 0
[    14.542]     RsvdMaskSize: 0
[    14.542]     RsvdFieldPosition: 0
[    14.542]     DirectColorModeInfo: 0
[    14.542]     PhysBasePtr: 0xc0000000
[    14.542]     LinBytesPerScanLine: 640
[    14.542]     BnkNumberOfImagePages: 10
[    14.542]     LinNumberOfImagePages: 10
[    14.542]     LinRedMaskSize: 0
[    14.542]     LinRedFieldPosition: 0
[    14.542]     LinGreenMaskSize: 0
[    14.542]     LinGreenFieldPosition: 0
[    14.542]     LinBlueMaskSize: 0
[    14.542]     LinBlueFieldPosition: 0
[    14.542]     LinRsvdMaskSize: 0
[    14.542]     LinRsvdFieldPosition: 0
[    14.542]     MaxPixelClock: 229500000
[    14.544] Mode: 102 (800x600)
[    14.544]     ModeAttributes: 0x31f
[    14.544]     WinAAttributes: 0x7
[    14.544]     WinBAttributes: 0x0
[    14.544]     WinGranularity: 64
[    14.544]     WinSize: 64
[    14.544]     WinASegment: 0xa000
[    14.544]     WinBSegment: 0x0
[    14.544]     WinFuncPtr: 0xc0009a73
[    14.544]     BytesPerScanline: 100
[    14.544]     XResolution: 800
[    14.544]     YResolution: 600
[    14.544]     XCharSize: 8
[    14.544]     YCharSize: 16
[    14.544]     NumberOfPlanes: 4
[    14.544]     BitsPerPixel: 4
[    14.544]     NumberOfBanks: 1
[    14.544]     MemoryModel: 3
[    14.544]     BankSize: 0
[    14.544]     NumberOfImages: 14
[    14.544]     RedMaskSize: 0
[    14.544]     RedFieldPosition: 0
[    14.544]     GreenMaskSize: 0
[    14.544]     GreenFieldPosition: 0
[    14.544]     BlueMaskSize: 0
[    14.544]     BlueFieldPosition: 0
[    14.544]     RsvdMaskSize: 0
[    14.544]     RsvdFieldPosition: 0
[    14.544]     DirectColorModeInfo: 0
[    14.544]     PhysBasePtr: 0x0
[    14.544]     LinBytesPerScanLine: 100
[    14.544]     BnkNumberOfImagePages: 14
[    14.544]     LinNumberOfImagePages: 14
[    14.544]     LinRedMaskSize: 0
[    14.544]     LinRedFieldPosition: 0
[    14.544]     LinGreenMaskSize: 0
[    14.544]     LinGreenFieldPosition: 0
[    14.544]     LinBlueMaskSize: 0
[    14.544]     LinBlueFieldPosition: 0
[    14.544]     LinRsvdMaskSize: 0
[    14.544]     LinRsvdFieldPosition: 0
[    14.544]     MaxPixelClock: 108500000
[    14.545] Mode: 103 (800x600)
[    14.545]     ModeAttributes: 0x39f
[    14.545]     WinAAttributes: 0x7
[    14.545]     WinBAttributes: 0x0
[    14.545]     WinGranularity: 64
[    14.545]     WinSize: 64
[    14.545]     WinASegment: 0xa000
[    14.545]     WinBSegment: 0x0
[    14.545]     WinFuncPtr: 0xc0009a73
[    14.545]     BytesPerScanline: 800
[    14.545]     XResolution: 800
[    14.545]     YResolution: 600
[    14.545]     XCharSize: 8
[    14.545]     YCharSize: 16
[    14.545]     NumberOfPlanes: 1
[    14.545]     BitsPerPixel: 8
[    14.545]     NumberOfBanks: 1
[    14.545]     MemoryModel: 4
[    14.545]     BankSize: 0
[    14.545]     NumberOfImages: 6
[    14.545]     RedMaskSize: 0
[    14.545]     RedFieldPosition: 0
[    14.545]     GreenMaskSize: 0
[    14.545]     GreenFieldPosition: 0
[    14.545]     BlueMaskSize: 0
[    14.545]     BlueFieldPosition: 0
[    14.545]     RsvdMaskSize: 0
[    14.545]     RsvdFieldPosition: 0
[    14.545]     DirectColorModeInfo: 0
[    14.545]     PhysBasePtr: 0xc0000000
[    14.545]     LinBytesPerScanLine: 800
[    14.545]     BnkNumberOfImagePages: 6
[    14.545]     LinNumberOfImagePages: 6
[    14.545]     LinRedMaskSize: 0
[    14.545]     LinRedFieldPosition: 0
[    14.545]     LinGreenMaskSize: 0
[    14.545]     LinGreenFieldPosition: 0
[    14.545]     LinBlueMaskSize: 0
[    14.545]     LinBlueFieldPosition: 0
[    14.545]     LinRsvdMaskSize: 0
[    14.545]     LinRsvdFieldPosition: 0
[    14.545]     MaxPixelClock: 229500000
[    14.546] Mode: 104 (1024x768)
[    14.546]     ModeAttributes: 0x31f
[    14.546]     WinAAttributes: 0x7
[    14.546]     WinBAttributes: 0x0
[    14.546]     WinGranularity: 64
[    14.546]     WinSize: 64
[    14.546]     WinASegment: 0xa000
[    14.546]     WinBSegment: 0x0
[    14.546]     WinFuncPtr: 0xc0009a73
[    14.546]     BytesPerScanline: 128
[    14.546]     XResolution: 1024
[    14.546]     YResolution: 768
[    14.546]     XCharSize: 8
[    14.546]     YCharSize: 16
[    14.546]     NumberOfPlanes: 4
[    14.546]     BitsPerPixel: 4
[    14.546]     NumberOfBanks: 1
[    14.546]     MemoryModel: 3
[    14.546]     BankSize: 0
[    14.546]     NumberOfImages: 6
[    14.546]     RedMaskSize: 0
[    14.546]     RedFieldPosition: 0
[    14.546]     GreenMaskSize: 0
[    14.546]     GreenFieldPosition: 0
[    14.546]     BlueMaskSize: 0
[    14.546]     BlueFieldPosition: 0
[    14.546]     RsvdMaskSize: 0
[    14.546]     RsvdFieldPosition: 0
[    14.546]     DirectColorModeInfo: 0
[    14.546]     PhysBasePtr: 0x0
[    14.546]     LinBytesPerScanLine: 128
[    14.546]     BnkNumberOfImagePages: 6
[    14.546]     LinNumberOfImagePages: 6
[    14.546]     LinRedMaskSize: 0
[    14.546]     LinRedFieldPosition: 0
[    14.546]     LinGreenMaskSize: 0
[    14.546]     LinGreenFieldPosition: 0
[    14.546]     LinBlueMaskSize: 0
[    14.546]     LinBlueFieldPosition: 0
[    14.546]     LinRsvdMaskSize: 0
[    14.546]     LinRsvdFieldPosition: 0
[    14.546]     MaxPixelClock: 108500000
[    14.548] Mode: 105 (1024x768)
[    14.548]     ModeAttributes: 0x39f
[    14.548]     WinAAttributes: 0x7
[    14.548]     WinBAttributes: 0x0
[    14.548]     WinGranularity: 64
[    14.548]     WinSize: 64
[    14.548]     WinASegment: 0xa000
[    14.548]     WinBSegment: 0x0
[    14.548]     WinFuncPtr: 0xc0009a73
[    14.548]     BytesPerScanline: 1024
[    14.548]     XResolution: 1024
[    14.548]     YResolution: 768
[    14.548]     XCharSize: 8
[    14.548]     YCharSize: 16
[    14.548]     NumberOfPlanes: 1
[    14.548]     BitsPerPixel: 8
[    14.548]     NumberOfBanks: 1
[    14.548]     MemoryModel: 4
[    14.548]     BankSize: 0
[    14.548]     NumberOfImages: 3
[    14.548]     RedMaskSize: 0
[    14.548]     RedFieldPosition: 0
[    14.548]     GreenMaskSize: 0
[    14.548]     GreenFieldPosition: 0
[    14.548]     BlueMaskSize: 0
[    14.548]     BlueFieldPosition: 0
[    14.548]     RsvdMaskSize: 0
[    14.548]     RsvdFieldPosition: 0
[    14.548]     DirectColorModeInfo: 0
[    14.548]     PhysBasePtr: 0xc0000000
[    14.548]     LinBytesPerScanLine: 1024
[    14.548]     BnkNumberOfImagePages: 3
[    14.548]     LinNumberOfImagePages: 3
[    14.548]     LinRedMaskSize: 0
[    14.548]     LinRedFieldPosition: 0
[    14.548]     LinGreenMaskSize: 0
[    14.548]     LinGreenFieldPosition: 0
[    14.548]     LinBlueMaskSize: 0
[    14.548]     LinBlueFieldPosition: 0
[    14.548]     LinRsvdMaskSize: 0
[    14.548]     LinRsvdFieldPosition: 0
[    14.548]     MaxPixelClock: 229500000
[    14.549] Mode: 106 (1280x1024)
[    14.549]     ModeAttributes: 0x31f
[    14.549]     WinAAttributes: 0x7
[    14.549]     WinBAttributes: 0x0
[    14.549]     WinGranularity: 64
[    14.549]     WinSize: 64
[    14.549]     WinASegment: 0xa000
[    14.549]     WinBSegment: 0x0
[    14.549]     WinFuncPtr: 0xc0009a73
[    14.549]     BytesPerScanline: 160
[    14.549]     XResolution: 1280
[    14.549]     YResolution: 1024
[    14.549]     XCharSize: 8
[    14.549]     YCharSize: 16
[    14.549]     NumberOfPlanes: 4
[    14.549]     BitsPerPixel: 4
[    14.549]     NumberOfBanks: 1
[    14.549]     MemoryModel: 3
[    14.549]     BankSize: 0
[    14.549]     NumberOfImages: 3
[    14.549]     RedMaskSize: 0
[    14.549]     RedFieldPosition: 0
[    14.549]     GreenMaskSize: 0
[    14.549]     GreenFieldPosition: 0
[    14.549]     BlueMaskSize: 0
[    14.549]     BlueFieldPosition: 0
[    14.549]     RsvdMaskSize: 0
[    14.549]     RsvdFieldPosition: 0
[    14.549]     DirectColorModeInfo: 0
[    14.549]     PhysBasePtr: 0x0
[    14.549]     LinBytesPerScanLine: 160
[    14.549]     BnkNumberOfImagePages: 3
[    14.549]     LinNumberOfImagePages: 3
[    14.549]     LinRedMaskSize: 0
[    14.549]     LinRedFieldPosition: 0
[    14.549]     LinGreenMaskSize: 0
[    14.549]     LinGreenFieldPosition: 0
[    14.549]     LinBlueMaskSize: 0
[    14.549]     LinBlueFieldPosition: 0
[    14.549]     LinRsvdMaskSize: 0
[    14.549]     LinRsvdFieldPosition: 0
[    14.549]     MaxPixelClock: 108500000
[    14.550] Mode: 107 (1280x1024)
[    14.550]     ModeAttributes: 0x39f
[    14.550]     WinAAttributes: 0x7
[    14.550]     WinBAttributes: 0x0
[    14.550]     WinGranularity: 64
[    14.550]     WinSize: 64
[    14.550]     WinASegment: 0xa000
[    14.550]     WinBSegment: 0x0
[    14.550]     WinFuncPtr: 0xc0009a73
[    14.550]     BytesPerScanline: 1280
[    14.550]     XResolution: 1280
[    14.550]     YResolution: 1024
[    14.550]     XCharSize: 8
[    14.550]     YCharSize: 16
[    14.550]     NumberOfPlanes: 1
[    14.550]     BitsPerPixel: 8
[    14.550]     NumberOfBanks: 1
[    14.550]     MemoryModel: 4
[    14.550]     BankSize: 0
[    14.550]     NumberOfImages: 1
[    14.550]     RedMaskSize: 0
[    14.550]     RedFieldPosition: 0
[    14.550]     GreenMaskSize: 0
[    14.550]     GreenFieldPosition: 0
[    14.550]     BlueMaskSize: 0
[    14.550]     BlueFieldPosition: 0
[    14.550]     RsvdMaskSize: 0
[    14.550]     RsvdFieldPosition: 0
[    14.550]     DirectColorModeInfo: 0
[    14.550]     PhysBasePtr: 0xc0000000
[    14.550]     LinBytesPerScanLine: 1280
[    14.550]     BnkNumberOfImagePages: 1
[    14.550]     LinNumberOfImagePages: 1
[    14.550]     LinRedMaskSize: 0
[    14.550]     LinRedFieldPosition: 0
[    14.550]     LinGreenMaskSize: 0
[    14.550]     LinGreenFieldPosition: 0
[    14.550]     LinBlueMaskSize: 0
[    14.550]     LinBlueFieldPosition: 0
[    14.550]     LinRsvdMaskSize: 0
[    14.550]     LinRsvdFieldPosition: 0
[    14.550]     MaxPixelClock: 229500000
[    14.552] Mode: 10e (320x200)
[    14.552]     ModeAttributes: 0x39f
[    14.552]     WinAAttributes: 0x7
[    14.552]     WinBAttributes: 0x0
[    14.552]     WinGranularity: 64
[    14.552]     WinSize: 64
[    14.552]     WinASegment: 0xa000
[    14.552]     WinBSegment: 0x0
[    14.552]     WinFuncPtr: 0xc0009a73
[    14.552]     BytesPerScanline: 640
[    14.552]     XResolution: 320
[    14.552]     YResolution: 200
[    14.552]     XCharSize: 8
[    14.552]     YCharSize: 8
[    14.552]     NumberOfPlanes: 1
[    14.552]     BitsPerPixel: 16
[    14.552]     NumberOfBanks: 1
[    14.552]     MemoryModel: 6
[    14.552]     BankSize: 0
[    14.552]     NumberOfImages: 30
[    14.552]     RedMaskSize: 5
[    14.552]     RedFieldPosition: 11
[    14.552]     GreenMaskSize: 6
[    14.552]     GreenFieldPosition: 5
[    14.552]     BlueMaskSize: 5
[    14.552]     BlueFieldPosition: 0
[    14.552]     RsvdMaskSize: 0
[    14.552]     RsvdFieldPosition: 0
[    14.552]     DirectColorModeInfo: 0
[    14.552]     PhysBasePtr: 0xc0000000
[    14.552]     LinBytesPerScanLine: 640
[    14.552]     BnkNumberOfImagePages: 30
[    14.552]     LinNumberOfImagePages: 30
[    14.552]     LinRedMaskSize: 5
[    14.552]     LinRedFieldPosition: 11
[    14.552]     LinGreenMaskSize: 6
[    14.552]     LinGreenFieldPosition: 5
[    14.552]     LinBlueMaskSize: 5
[    14.552]     LinBlueFieldPosition: 0
[    14.552]     LinRsvdMaskSize: 0
[    14.552]     LinRsvdFieldPosition: 0
[    14.552]     MaxPixelClock: 229500000
[    14.553] *Mode: 10f (320x200)
[    14.553]     ModeAttributes: 0x39f
[    14.553]     WinAAttributes: 0x7
[    14.553]     WinBAttributes: 0x0
[    14.553]     WinGranularity: 64
[    14.553]     WinSize: 64
[    14.553]     WinASegment: 0xa000
[    14.553]     WinBSegment: 0x0
[    14.553]     WinFuncPtr: 0xc0009a73
[    14.553]     BytesPerScanline: 1280
[    14.553]     XResolution: 320
[    14.553]     YResolution: 200
[    14.553]     XCharSize: 8
[    14.553]     YCharSize: 8
[    14.553]     NumberOfPlanes: 1
[    14.553]     BitsPerPixel: 32
[    14.553]     NumberOfBanks: 1
[    14.553]     MemoryModel: 6
[    14.553]     BankSize: 0
[    14.553]     NumberOfImages: 14
[    14.553]     RedMaskSize: 8
[    14.553]     RedFieldPosition: 16
[    14.553]     GreenMaskSize: 8
[    14.553]     GreenFieldPosition: 8
[    14.553]     BlueMaskSize: 8
[    14.553]     BlueFieldPosition: 0
[    14.553]     RsvdMaskSize: 8
[    14.553]     RsvdFieldPosition: 24
[    14.553]     DirectColorModeInfo: 0
[    14.553]     PhysBasePtr: 0xc0000000
[    14.553]     LinBytesPerScanLine: 1280
[    14.553]     BnkNumberOfImagePages: 14
[    14.553]     LinNumberOfImagePages: 14
[    14.553]     LinRedMaskSize: 8
[    14.553]     LinRedFieldPosition: 16
[    14.553]     LinGreenMaskSize: 8
[    14.553]     LinGreenFieldPosition: 8
[    14.553]     LinBlueMaskSize: 8
[    14.553]     LinBlueFieldPosition: 0
[    14.553]     LinRsvdMaskSize: 8
[    14.553]     LinRsvdFieldPosition: 24
[    14.553]     MaxPixelClock: 229500000
[    14.555] Mode: 111 (640x480)
[    14.555]     ModeAttributes: 0x39f
[    14.555]     WinAAttributes: 0x7
[    14.555]     WinBAttributes: 0x0
[    14.555]     WinGranularity: 64
[    14.555]     WinSize: 64
[    14.555]     WinASegment: 0xa000
[    14.555]     WinBSegment: 0x0
[    14.555]     WinFuncPtr: 0xc0009a73
[    14.555]     BytesPerScanline: 1280
[    14.555]     XResolution: 640
[    14.555]     YResolution: 480
[    14.555]     XCharSize: 8
[    14.555]     YCharSize: 16
[    14.555]     NumberOfPlanes: 1
[    14.555]     BitsPerPixel: 16
[    14.555]     NumberOfBanks: 1
[    14.555]     MemoryModel: 6
[    14.555]     BankSize: 0
[    14.555]     NumberOfImages: 4
[    14.555]     RedMaskSize: 5
[    14.555]     RedFieldPosition: 11
[    14.555]     GreenMaskSize: 6
[    14.555]     GreenFieldPosition: 5
[    14.555]     BlueMaskSize: 5
[    14.555]     BlueFieldPosition: 0
[    14.555]     RsvdMaskSize: 0
[    14.555]     RsvdFieldPosition: 0
[    14.555]     DirectColorModeInfo: 0
[    14.555]     PhysBasePtr: 0xc0000000
[    14.555]     LinBytesPerScanLine: 1280
[    14.555]     BnkNumberOfImagePages: 4
[    14.555]     LinNumberOfImagePages: 4
[    14.555]     LinRedMaskSize: 5
[    14.555]     LinRedFieldPosition: 11
[    14.555]     LinGreenMaskSize: 6
[    14.555]     LinGreenFieldPosition: 5
[    14.555]     LinBlueMaskSize: 5
[    14.555]     LinBlueFieldPosition: 0
[    14.555]     LinRsvdMaskSize: 0
[    14.555]     LinRsvdFieldPosition: 0
[    14.555]     MaxPixelClock: 229500000
[    14.556] *Mode: 112 (640x480)
[    14.556]     ModeAttributes: 0x39f
[    14.556]     WinAAttributes: 0x7
[    14.556]     WinBAttributes: 0x0
[    14.556]     WinGranularity: 64
[    14.556]     WinSize: 64
[    14.556]     WinASegment: 0xa000
[    14.556]     WinBSegment: 0x0
[    14.556]     WinFuncPtr: 0xc0009a73
[    14.556]     BytesPerScanline: 2560
[    14.556]     XResolution: 640
[    14.556]     YResolution: 480
[    14.556]     XCharSize: 8
[    14.556]     YCharSize: 16
[    14.556]     NumberOfPlanes: 1
[    14.556]     BitsPerPixel: 32
[    14.556]     NumberOfBanks: 1
[    14.556]     MemoryModel: 6
[    14.556]     BankSize: 0
[    14.556]     NumberOfImages: 1
[    14.556]     RedMaskSize: 8
[    14.556]     RedFieldPosition: 16
[    14.556]     GreenMaskSize: 8
[    14.556]     GreenFieldPosition: 8
[    14.556]     BlueMaskSize: 8
[    14.556]     BlueFieldPosition: 0
[    14.556]     RsvdMaskSize: 8
[    14.556]     RsvdFieldPosition: 24
[    14.556]     DirectColorModeInfo: 0
[    14.556]     PhysBasePtr: 0xc0000000
[    14.556]     LinBytesPerScanLine: 2560
[    14.556]     BnkNumberOfImagePages: 1
[    14.556]     LinNumberOfImagePages: 1
[    14.556]     LinRedMaskSize: 8
[    14.556]     LinRedFieldPosition: 16
[    14.556]     LinGreenMaskSize: 8
[    14.556]     LinGreenFieldPosition: 8
[    14.556]     LinBlueMaskSize: 8
[    14.556]     LinBlueFieldPosition: 0
[    14.556]     LinRsvdMaskSize: 8
[    14.556]     LinRsvdFieldPosition: 24
[    14.556]     MaxPixelClock: 229500000
[    14.558] Mode: 114 (800x600)
[    14.558]     ModeAttributes: 0x39f
[    14.558]     WinAAttributes: 0x7
[    14.558]     WinBAttributes: 0x0
[    14.558]     WinGranularity: 64
[    14.558]     WinSize: 64
[    14.558]     WinASegment: 0xa000
[    14.558]     WinBSegment: 0x0
[    14.558]     WinFuncPtr: 0xc0009a73
[    14.558]     BytesPerScanline: 1600
[    14.558]     XResolution: 800
[    14.558]     YResolution: 600
[    14.558]     XCharSize: 8
[    14.558]     YCharSize: 16
[    14.558]     NumberOfPlanes: 1
[    14.558]     BitsPerPixel: 16
[    14.558]     NumberOfBanks: 1
[    14.558]     MemoryModel: 6
[    14.558]     BankSize: 0
[    14.558]     NumberOfImages: 2
[    14.558]     RedMaskSize: 5
[    14.558]     RedFieldPosition: 11
[    14.558]     GreenMaskSize: 6
[    14.558]     GreenFieldPosition: 5
[    14.558]     BlueMaskSize: 5
[    14.558]     BlueFieldPosition: 0
[    14.558]     RsvdMaskSize: 0
[    14.558]     RsvdFieldPosition: 0
[    14.558]     DirectColorModeInfo: 0
[    14.558]     PhysBasePtr: 0xc0000000
[    14.558]     LinBytesPerScanLine: 1600
[    14.558]     BnkNumberOfImagePages: 2
[    14.558]     LinNumberOfImagePages: 2
[    14.558]     LinRedMaskSize: 5
[    14.558]     LinRedFieldPosition: 11
[    14.558]     LinGreenMaskSize: 6
[    14.558]     LinGreenFieldPosition: 5
[    14.558]     LinBlueMaskSize: 5
[    14.558]     LinBlueFieldPosition: 0
[    14.558]     LinRsvdMaskSize: 0
[    14.558]     LinRsvdFieldPosition: 0
[    14.558]     MaxPixelClock: 229500000
[    14.559] *Mode: 115 (800x600)
[    14.559]     ModeAttributes: 0x39f
[    14.559]     WinAAttributes: 0x7
[    14.559]     WinBAttributes: 0x0
[    14.559]     WinGranularity: 64
[    14.559]     WinSize: 64
[    14.559]     WinASegment: 0xa000
[    14.559]     WinBSegment: 0x0
[    14.559]     WinFuncPtr: 0xc0009a73
[    14.559]     BytesPerScanline: 3200
[    14.559]     XResolution: 800
[    14.559]     YResolution: 600
[    14.559]     XCharSize: 8
[    14.559]     YCharSize: 16
[    14.559]     NumberOfPlanes: 1
[    14.559]     BitsPerPixel: 32
[    14.559]     NumberOfBanks: 1
[    14.559]     MemoryModel: 6
[    14.559]     BankSize: 0
[    14.559]     NumberOfImages: 1
[    14.559]     RedMaskSize: 8
[    14.559]     RedFieldPosition: 16
[    14.559]     GreenMaskSize: 8
[    14.559]     GreenFieldPosition: 8
[    14.559]     BlueMaskSize: 8
[    14.559]     BlueFieldPosition: 0
[    14.559]     RsvdMaskSize: 8
[    14.559]     RsvdFieldPosition: 24
[    14.559]     DirectColorModeInfo: 0
[    14.559]     PhysBasePtr: 0xc0000000
[    14.559]     LinBytesPerScanLine: 3200
[    14.559]     BnkNumberOfImagePages: 1
[    14.559]     LinNumberOfImagePages: 1
[    14.559]     LinRedMaskSize: 8
[    14.559]     LinRedFieldPosition: 16
[    14.559]     LinGreenMaskSize: 8
[    14.559]     LinGreenFieldPosition: 8
[    14.559]     LinBlueMaskSize: 8
[    14.559]     LinBlueFieldPosition: 0
[    14.559]     LinRsvdMaskSize: 8
[    14.559]     LinRsvdFieldPosition: 24
[    14.559]     MaxPixelClock: 229500000
[    14.560] Mode: 117 (1024x768)
[    14.560]     ModeAttributes: 0x39f
[    14.560]     WinAAttributes: 0x7
[    14.560]     WinBAttributes: 0x0
[    14.560]     WinGranularity: 64
[    14.560]     WinSize: 64
[    14.560]     WinASegment: 0xa000
[    14.560]     WinBSegment: 0x0
[    14.561]     WinFuncPtr: 0xc0009a73
[    14.561]     BytesPerScanline: 2048
[    14.561]     XResolution: 1024
[    14.561]     YResolution: 768
[    14.561]     XCharSize: 8
[    14.561]     YCharSize: 16
[    14.561]     NumberOfPlanes: 1
[    14.561]     BitsPerPixel: 16
[    14.561]     NumberOfBanks: 1
[    14.561]     MemoryModel: 6
[    14.561]     BankSize: 0
[    14.561]     NumberOfImages: 1
[    14.561]     RedMaskSize: 5
[    14.561]     RedFieldPosition: 11
[    14.561]     GreenMaskSize: 6
[    14.561]     GreenFieldPosition: 5
[    14.561]     BlueMaskSize: 5
[    14.561]     BlueFieldPosition: 0
[    14.561]     RsvdMaskSize: 0
[    14.561]     RsvdFieldPosition: 0
[    14.561]     DirectColorModeInfo: 0
[    14.561]     PhysBasePtr: 0xc0000000
[    14.561]     LinBytesPerScanLine: 2048
[    14.561]     BnkNumberOfImagePages: 1
[    14.561]     LinNumberOfImagePages: 1
[    14.561]     LinRedMaskSize: 5
[    14.561]     LinRedFieldPosition: 11
[    14.561]     LinGreenMaskSize: 6
[    14.561]     LinGreenFieldPosition: 5
[    14.561]     LinBlueMaskSize: 5
[    14.561]     LinBlueFieldPosition: 0
[    14.561]     LinRsvdMaskSize: 0
[    14.561]     LinRsvdFieldPosition: 0
[    14.561]     MaxPixelClock: 229500000
[    14.562] *Mode: 118 (1024x768)
[    14.562]     ModeAttributes: 0x39f
[    14.562]     WinAAttributes: 0x7
[    14.562]     WinBAttributes: 0x0
[    14.562]     WinGranularity: 64
[    14.562]     WinSize: 64
[    14.562]     WinASegment: 0xa000
[    14.562]     WinBSegment: 0x0
[    14.562]     WinFuncPtr: 0xc0009a73
[    14.562]     BytesPerScanline: 4096
[    14.562]     XResolution: 1024
[    14.562]     YResolution: 768
[    14.562]     XCharSize: 8
[    14.562]     YCharSize: 16
[    14.562]     NumberOfPlanes: 1
[    14.562]     BitsPerPixel: 32
[    14.562]     NumberOfBanks: 1
[    14.562]     MemoryModel: 6
[    14.562]     BankSize: 0
[    14.562]     NumberOfImages: 1
[    14.562]     RedMaskSize: 8
[    14.562]     RedFieldPosition: 16
[    14.562]     GreenMaskSize: 8
[    14.562]     GreenFieldPosition: 8
[    14.562]     BlueMaskSize: 8
[    14.562]     BlueFieldPosition: 0
[    14.562]     RsvdMaskSize: 8
[    14.562]     RsvdFieldPosition: 24
[    14.562]     DirectColorModeInfo: 0
[    14.562]     PhysBasePtr: 0xc0000000
[    14.562]     LinBytesPerScanLine: 4096
[    14.562]     BnkNumberOfImagePages: 1
[    14.562]     LinNumberOfImagePages: 1
[    14.562]     LinRedMaskSize: 8
[    14.562]     LinRedFieldPosition: 16
[    14.562]     LinGreenMaskSize: 8
[    14.562]     LinGreenFieldPosition: 8
[    14.562]     LinBlueMaskSize: 8
[    14.562]     LinBlueFieldPosition: 0
[    14.562]     LinRsvdMaskSize: 8
[    14.562]     LinRsvdFieldPosition: 24
[    14.562]     MaxPixelClock: 229500000
[    14.563] Mode: 11a (1280x1024)
[    14.563]     ModeAttributes: 0x39f
[    14.563]     WinAAttributes: 0x7
[    14.563]     WinBAttributes: 0x0
[    14.563]     WinGranularity: 64
[    14.563]     WinSize: 64
[    14.563]     WinASegment: 0xa000
[    14.563]     WinBSegment: 0x0
[    14.563]     WinFuncPtr: 0xc0009a73
[    14.563]     BytesPerScanline: 2560
[    14.563]     XResolution: 1280
[    14.563]     YResolution: 1024
[    14.563]     XCharSize: 8
[    14.563]     YCharSize: 16
[    14.563]     NumberOfPlanes: 1
[    14.563]     BitsPerPixel: 16
[    14.563]     NumberOfBanks: 1
[    14.563]     MemoryModel: 6
[    14.563]     BankSize: 0
[    14.563]     NumberOfImages: 1
[    14.563]     RedMaskSize: 5
[    14.563]     RedFieldPosition: 11
[    14.563]     GreenMaskSize: 6
[    14.563]     GreenFieldPosition: 5
[    14.563]     BlueMaskSize: 5
[    14.563]     BlueFieldPosition: 0
[    14.563]     RsvdMaskSize: 0
[    14.563]     RsvdFieldPosition: 0
[    14.563]     DirectColorModeInfo: 0
[    14.563]     PhysBasePtr: 0xc0000000
[    14.563]     LinBytesPerScanLine: 2560
[    14.563]     BnkNumberOfImagePages: 1
[    14.563]     LinNumberOfImagePages: 1
[    14.563]     LinRedMaskSize: 5
[    14.563]     LinRedFieldPosition: 11
[    14.563]     LinGreenMaskSize: 6
[    14.563]     LinGreenFieldPosition: 5
[    14.563]     LinBlueMaskSize: 5
[    14.563]     LinBlueFieldPosition: 0
[    14.563]     LinRsvdMaskSize: 0
[    14.563]     LinRsvdFieldPosition: 0
[    14.563]     MaxPixelClock: 229500000
[    14.565] *Mode: 11b (1280x1024)
[    14.565]     ModeAttributes: 0x39f
[    14.565]     WinAAttributes: 0x7
[    14.565]     WinBAttributes: 0x0
[    14.565]     WinGranularity: 64
[    14.565]     WinSize: 64
[    14.565]     WinASegment: 0xa000
[    14.565]     WinBSegment: 0x0
[    14.565]     WinFuncPtr: 0xc0009a73
[    14.565]     BytesPerScanline: 5120
[    14.565]     XResolution: 1280
[    14.565]     YResolution: 1024
[    14.565]     XCharSize: 8
[    14.565]     YCharSize: 16
[    14.565]     NumberOfPlanes: 1
[    14.565]     BitsPerPixel: 32
[    14.565]     NumberOfBanks: 1
[    14.565]     MemoryModel: 6
[    14.565]     BankSize: 0
[    14.565]     NumberOfImages: 0
[    14.565]     RedMaskSize: 8
[    14.565]     RedFieldPosition: 16
[    14.565]     GreenMaskSize: 8
[    14.565]     GreenFieldPosition: 8
[    14.565]     BlueMaskSize: 8
[    14.565]     BlueFieldPosition: 0
[    14.565]     RsvdMaskSize: 8
[    14.565]     RsvdFieldPosition: 24
[    14.565]     DirectColorModeInfo: 0
[    14.565]     PhysBasePtr: 0xc0000000
[    14.565]     LinBytesPerScanLine: 5120
[    14.565]     BnkNumberOfImagePages: 0
[    14.565]     LinNumberOfImagePages: 0
[    14.565]     LinRedMaskSize: 8
[    14.565]     LinRedFieldPosition: 16
[    14.565]     LinGreenMaskSize: 8
[    14.565]     LinGreenFieldPosition: 8
[    14.565]     LinBlueMaskSize: 8
[    14.565]     LinBlueFieldPosition: 0
[    14.565]     LinRsvdMaskSize: 8
[    14.565]     LinRsvdFieldPosition: 24
[    14.565]     MaxPixelClock: 229500000
[    14.566] Mode: 130 (320x200)
[    14.566]     ModeAttributes: 0x39f
[    14.566]     WinAAttributes: 0x7
[    14.566]     WinBAttributes: 0x0
[    14.566]     WinGranularity: 64
[    14.566]     WinSize: 64
[    14.566]     WinASegment: 0xa000
[    14.566]     WinBSegment: 0x0
[    14.566]     WinFuncPtr: 0xc0009a73
[    14.566]     BytesPerScanline: 320
[    14.566]     XResolution: 320
[    14.566]     YResolution: 200
[    14.566]     XCharSize: 8
[    14.566]     YCharSize: 8
[    14.566]     NumberOfPlanes: 1
[    14.566]     BitsPerPixel: 8
[    14.566]     NumberOfBanks: 1
[    14.566]     MemoryModel: 4
[    14.566]     BankSize: 0
[    14.566]     NumberOfImages: 62
[    14.566]     RedMaskSize: 0
[    14.566]     RedFieldPosition: 0
[    14.566]     GreenMaskSize: 0
[    14.566]     GreenFieldPosition: 0
[    14.566]     BlueMaskSize: 0
[    14.566]     BlueFieldPosition: 0
[    14.566]     RsvdMaskSize: 0
[    14.566]     RsvdFieldPosition: 0
[    14.566]     DirectColorModeInfo: 0
[    14.566]     PhysBasePtr: 0xc0000000
[    14.566]     LinBytesPerScanLine: 320
[    14.566]     BnkNumberOfImagePages: 62
[    14.566]     LinNumberOfImagePages: 62
[    14.566]     LinRedMaskSize: 0
[    14.566]     LinRedFieldPosition: 0
[    14.566]     LinGreenMaskSize: 0
[    14.566]     LinGreenFieldPosition: 0
[    14.566]     LinBlueMaskSize: 0
[    14.566]     LinBlueFieldPosition: 0
[    14.566]     LinRsvdMaskSize: 0
[    14.566]     LinRsvdFieldPosition: 0
[    14.566]     MaxPixelClock: 229500000
[    14.567] Mode: 131 (320x400)
[    14.567]     ModeAttributes: 0x39f
[    14.567]     WinAAttributes: 0x7
[    14.567]     WinBAttributes: 0x0
[    14.567]     WinGranularity: 64
[    14.567]     WinSize: 64
[    14.567]     WinASegment: 0xa000
[    14.567]     WinBSegment: 0x0
[    14.567]     WinFuncPtr: 0xc0009a73
[    14.567]     BytesPerScanline: 320
[    14.567]     XResolution: 320
[    14.567]     YResolution: 400
[    14.567]     XCharSize: 8
[    14.567]     YCharSize: 16
[    14.567]     NumberOfPlanes: 1
[    14.567]     BitsPerPixel: 8
[    14.567]     NumberOfBanks: 1
[    14.567]     MemoryModel: 4
[    14.567]     BankSize: 0
[    14.567]     NumberOfImages: 30
[    14.567]     RedMaskSize: 0
[    14.568]     RedFieldPosition: 0
[    14.568]     GreenMaskSize: 0
[    14.568]     GreenFieldPosition: 0
[    14.568]     BlueMaskSize: 0
[    14.568]     BlueFieldPosition: 0
[    14.568]     RsvdMaskSize: 0
[    14.568]     RsvdFieldPosition: 0
[    14.568]     DirectColorModeInfo: 0
[    14.568]     PhysBasePtr: 0xc0000000
[    14.568]     LinBytesPerScanLine: 320
[    14.568]     BnkNumberOfImagePages: 30
[    14.568]     LinNumberOfImagePages: 30
[    14.568]     LinRedMaskSize: 0
[    14.568]     LinRedFieldPosition: 0
[    14.568]     LinGreenMaskSize: 0
[    14.568]     LinGreenFieldPosition: 0
[    14.568]     LinBlueMaskSize: 0
[    14.568]     LinBlueFieldPosition: 0
[    14.568]     LinRsvdMaskSize: 0
[    14.568]     LinRsvdFieldPosition: 0
[    14.568]     MaxPixelClock: 229500000
[    14.569] Mode: 132 (320x400)
[    14.569]     ModeAttributes: 0x39f
[    14.569]     WinAAttributes: 0x7
[    14.569]     WinBAttributes: 0x0
[    14.569]     WinGranularity: 64
[    14.569]     WinSize: 64
[    14.569]     WinASegment: 0xa000
[    14.569]     WinBSegment: 0x0
[    14.569]     WinFuncPtr: 0xc0009a73
[    14.569]     BytesPerScanline: 640
[    14.569]     XResolution: 320
[    14.569]     YResolution: 400
[    14.569]     XCharSize: 8
[    14.569]     YCharSize: 16
[    14.569]     NumberOfPlanes: 1
[    14.569]     BitsPerPixel: 16
[    14.569]     NumberOfBanks: 1
[    14.569]     MemoryModel: 6
[    14.569]     BankSize: 0
[    14.569]     NumberOfImages: 14
[    14.569]     RedMaskSize: 5
[    14.569]     RedFieldPosition: 11
[    14.569]     GreenMaskSize: 6
[    14.569]     GreenFieldPosition: 5
[    14.569]     BlueMaskSize: 5
[    14.569]     BlueFieldPosition: 0
[    14.569]     RsvdMaskSize: 0
[    14.569]     RsvdFieldPosition: 0
[    14.569]     DirectColorModeInfo: 0
[    14.569]     PhysBasePtr: 0xc0000000
[    14.569]     LinBytesPerScanLine: 640
[    14.569]     BnkNumberOfImagePages: 14
[    14.569]     LinNumberOfImagePages: 14
[    14.569]     LinRedMaskSize: 5
[    14.569]     LinRedFieldPosition: 11
[    14.569]     LinGreenMaskSize: 6
[    14.569]     LinGreenFieldPosition: 5
[    14.569]     LinBlueMaskSize: 5
[    14.569]     LinBlueFieldPosition: 0
[    14.569]     LinRsvdMaskSize: 0
[    14.569]     LinRsvdFieldPosition: 0
[    14.569]     MaxPixelClock: 229500000
[    14.570] *Mode: 133 (320x400)
[    14.570]     ModeAttributes: 0x39f
[    14.570]     WinAAttributes: 0x7
[    14.570]     WinBAttributes: 0x0
[    14.570]     WinGranularity: 64
[    14.570]     WinSize: 64
[    14.570]     WinASegment: 0xa000
[    14.570]     WinBSegment: 0x0
[    14.570]     WinFuncPtr: 0xc0009a73
[    14.570]     BytesPerScanline: 1280
[    14.570]     XResolution: 320
[    14.570]     YResolution: 400
[    14.570]     XCharSize: 8
[    14.570]     YCharSize: 16
[    14.570]     NumberOfPlanes: 1
[    14.570]     BitsPerPixel: 32
[    14.570]     NumberOfBanks: 1
[    14.570]     MemoryModel: 6
[    14.570]     BankSize: 0
[    14.570]     NumberOfImages: 6
[    14.570]     RedMaskSize: 8
[    14.570]     RedFieldPosition: 16
[    14.570]     GreenMaskSize: 8
[    14.570]     GreenFieldPosition: 8
[    14.570]     BlueMaskSize: 8
[    14.570]     BlueFieldPosition: 0
[    14.570]     RsvdMaskSize: 8
[    14.570]     RsvdFieldPosition: 24
[    14.570]     DirectColorModeInfo: 0
[    14.570]     PhysBasePtr: 0xc0000000
[    14.570]     LinBytesPerScanLine: 1280
[    14.570]     BnkNumberOfImagePages: 6
[    14.570]     LinNumberOfImagePages: 6
[    14.570]     LinRedMaskSize: 8
[    14.570]     LinRedFieldPosition: 16
[    14.570]     LinGreenMaskSize: 8
[    14.570]     LinGreenFieldPosition: 8
[    14.570]     LinBlueMaskSize: 8
[    14.570]     LinBlueFieldPosition: 0
[    14.570]     LinRsvdMaskSize: 8
[    14.570]     LinRsvdFieldPosition: 24
[    14.570]     MaxPixelClock: 229500000
[    14.572] Mode: 134 (320x240)
[    14.572]     ModeAttributes: 0x39f
[    14.572]     WinAAttributes: 0x7
[    14.572]     WinBAttributes: 0x0
[    14.572]     WinGranularity: 64
[    14.572]     WinSize: 64
[    14.572]     WinASegment: 0xa000
[    14.572]     WinBSegment: 0x0
[    14.572]     WinFuncPtr: 0xc0009a73
[    14.572]     BytesPerScanline: 320
[    14.572]     XResolution: 320
[    14.572]     YResolution: 240
[    14.572]     XCharSize: 8
[    14.572]     YCharSize: 8
[    14.572]     NumberOfPlanes: 1
[    14.572]     BitsPerPixel: 8
[    14.572]     NumberOfBanks: 1
[    14.572]     MemoryModel: 4
[    14.572]     BankSize: 0
[    14.572]     NumberOfImages: 30
[    14.572]     RedMaskSize: 0
[    14.572]     RedFieldPosition: 0
[    14.572]     GreenMaskSize: 0
[    14.572]     GreenFieldPosition: 0
[    14.572]     BlueMaskSize: 0
[    14.572]     BlueFieldPosition: 0
[    14.572]     RsvdMaskSize: 0
[    14.572]     RsvdFieldPosition: 0
[    14.572]     DirectColorModeInfo: 0
[    14.572]     PhysBasePtr: 0xc0000000
[    14.572]     LinBytesPerScanLine: 320
[    14.572]     BnkNumberOfImagePages: 30
[    14.572]     LinNumberOfImagePages: 30
[    14.572]     LinRedMaskSize: 0
[    14.572]     LinRedFieldPosition: 0
[    14.572]     LinGreenMaskSize: 0
[    14.572]     LinGreenFieldPosition: 0
[    14.572]     LinBlueMaskSize: 0
[    14.572]     LinBlueFieldPosition: 0
[    14.572]     LinRsvdMaskSize: 0
[    14.572]     LinRsvdFieldPosition: 0
[    14.572]     MaxPixelClock: 229500000
[    14.573] Mode: 135 (320x240)
[    14.573]     ModeAttributes: 0x39f
[    14.573]     WinAAttributes: 0x7
[    14.573]     WinBAttributes: 0x0
[    14.573]     WinGranularity: 64
[    14.573]     WinSize: 64
[    14.573]     WinASegment: 0xa000
[    14.573]     WinBSegment: 0x0
[    14.573]     WinFuncPtr: 0xc0009a73
[    14.573]     BytesPerScanline: 640
[    14.573]     XResolution: 320
[    14.573]     YResolution: 240
[    14.573]     XCharSize: 8
[    14.573]     YCharSize: 8
[    14.573]     NumberOfPlanes: 1
[    14.573]     BitsPerPixel: 16
[    14.573]     NumberOfBanks: 1
[    14.573]     MemoryModel: 6
[    14.573]     BankSize: 0
[    14.573]     NumberOfImages: 19
[    14.573]     RedMaskSize: 5
[    14.573]     RedFieldPosition: 11
[    14.573]     GreenMaskSize: 6
[    14.573]     GreenFieldPosition: 5
[    14.573]     BlueMaskSize: 5
[    14.573]     BlueFieldPosition: 0
[    14.573]     RsvdMaskSize: 0
[    14.573]     RsvdFieldPosition: 0
[    14.573]     DirectColorModeInfo: 0
[    14.573]     PhysBasePtr: 0xc0000000
[    14.573]     LinBytesPerScanLine: 640
[    14.573]     BnkNumberOfImagePages: 19
[    14.573]     LinNumberOfImagePages: 19
[    14.573]     LinRedMaskSize: 5
[    14.573]     LinRedFieldPosition: 11
[    14.573]     LinGreenMaskSize: 6
[    14.573]     LinGreenFieldPosition: 5
[    14.573]     LinBlueMaskSize: 5
[    14.573]     LinBlueFieldPosition: 0
[    14.573]     LinRsvdMaskSize: 0
[    14.573]     LinRsvdFieldPosition: 0
[    14.573]     MaxPixelClock: 229500000
[    14.574] *Mode: 136 (320x240)
[    14.574]     ModeAttributes: 0x39f
[    14.574]     WinAAttributes: 0x7
[    14.574]     WinBAttributes: 0x0
[    14.574]     WinGranularity: 64
[    14.574]     WinSize: 64
[    14.574]     WinASegment: 0xa000
[    14.574]     WinBSegment: 0x0
[    14.574]     WinFuncPtr: 0xc0009a73
[    14.574]     BytesPerScanline: 1280
[    14.574]     XResolution: 320
[    14.574]     YResolution: 240
[    14.574]     XCharSize: 8
[    14.574]     YCharSize: 8
[    14.574]     NumberOfPlanes: 1
[    14.574]     BitsPerPixel: 32
[    14.574]     NumberOfBanks: 1
[    14.574]     MemoryModel: 6
[    14.574]     BankSize: 0
[    14.574]     NumberOfImages: 10
[    14.574]     RedMaskSize: 8
[    14.574]     RedFieldPosition: 16
[    14.574]     GreenMaskSize: 8
[    14.574]     GreenFieldPosition: 8
[    14.574]     BlueMaskSize: 8
[    14.574]     BlueFieldPosition: 0
[    14.574]     RsvdMaskSize: 8
[    14.574]     RsvdFieldPosition: 24
[    14.574]     DirectColorModeInfo: 0
[    14.574]     PhysBasePtr: 0xc0000000
[    14.574]     LinBytesPerScanLine: 1280
[    14.574]     BnkNumberOfImagePages: 10
[    14.574]     LinNumberOfImagePages: 10
[    14.574]     LinRedMaskSize: 8
[    14.574]     LinRedFieldPosition: 16
[    14.574]     LinGreenMaskSize: 8
[    14.574]     LinGreenFieldPosition: 8
[    14.574]     LinBlueMaskSize: 8
[    14.574]     LinBlueFieldPosition: 0
[    14.574]     LinRsvdMaskSize: 8
[    14.575]     LinRsvdFieldPosition: 24
[    14.575]     MaxPixelClock: 229500000
[    14.576] Mode: 13d (640x400)
[    14.576]     ModeAttributes: 0x39f
[    14.576]     WinAAttributes: 0x7
[    14.576]     WinBAttributes: 0x0
[    14.576]     WinGranularity: 64
[    14.576]     WinSize: 64
[    14.576]     WinASegment: 0xa000
[    14.576]     WinBSegment: 0x0
[    14.576]     WinFuncPtr: 0xc0009a73
[    14.576]     BytesPerScanline: 1280
[    14.576]     XResolution: 640
[    14.576]     YResolution: 400
[    14.576]     XCharSize: 8
[    14.576]     YCharSize: 16
[    14.576]     NumberOfPlanes: 1
[    14.576]     BitsPerPixel: 16
[    14.576]     NumberOfBanks: 1
[    14.576]     MemoryModel: 6
[    14.576]     BankSize: 0
[    14.576]     NumberOfImages: 6
[    14.576]     RedMaskSize: 5
[    14.576]     RedFieldPosition: 11
[    14.576]     GreenMaskSize: 6
[    14.576]     GreenFieldPosition: 5
[    14.576]     BlueMaskSize: 5
[    14.576]     BlueFieldPosition: 0
[    14.576]     RsvdMaskSize: 0
[    14.576]     RsvdFieldPosition: 0
[    14.576]     DirectColorModeInfo: 0
[    14.576]     PhysBasePtr: 0xc0000000
[    14.576]     LinBytesPerScanLine: 1280
[    14.576]     BnkNumberOfImagePages: 6
[    14.576]     LinNumberOfImagePages: 6
[    14.576]     LinRedMaskSize: 5
[    14.576]     LinRedFieldPosition: 11
[    14.576]     LinGreenMaskSize: 6
[    14.576]     LinGreenFieldPosition: 5
[    14.576]     LinBlueMaskSize: 5
[    14.576]     LinBlueFieldPosition: 0
[    14.576]     LinRsvdMaskSize: 0
[    14.576]     LinRsvdFieldPosition: 0
[    14.576]     MaxPixelClock: 229500000
[    14.577] *Mode: 13e (640x400)
[    14.577]     ModeAttributes: 0x39f
[    14.577]     WinAAttributes: 0x7
[    14.577]     WinBAttributes: 0x0
[    14.577]     WinGranularity: 64
[    14.577]     WinSize: 64
[    14.577]     WinASegment: 0xa000
[    14.577]     WinBSegment: 0x0
[    14.577]     WinFuncPtr: 0xc0009a73
[    14.577]     BytesPerScanline: 2560
[    14.577]     XResolution: 640
[    14.577]     YResolution: 400
[    14.577]     XCharSize: 8
[    14.577]     YCharSize: 16
[    14.577]     NumberOfPlanes: 1
[    14.577]     BitsPerPixel: 32
[    14.577]     NumberOfBanks: 1
[    14.577]     MemoryModel: 6
[    14.577]     BankSize: 0
[    14.577]     NumberOfImages: 2
[    14.577]     RedMaskSize: 8
[    14.577]     RedFieldPosition: 16
[    14.577]     GreenMaskSize: 8
[    14.577]     GreenFieldPosition: 8
[    14.577]     BlueMaskSize: 8
[    14.577]     BlueFieldPosition: 0
[    14.577]     RsvdMaskSize: 8
[    14.577]     RsvdFieldPosition: 24
[    14.577]     DirectColorModeInfo: 0
[    14.577]     PhysBasePtr: 0xc0000000
[    14.577]     LinBytesPerScanLine: 2560
[    14.577]     BnkNumberOfImagePages: 2
[    14.577]     LinNumberOfImagePages: 2
[    14.577]     LinRedMaskSize: 8
[    14.577]     LinRedFieldPosition: 16
[    14.577]     LinGreenMaskSize: 8
[    14.577]     LinGreenFieldPosition: 8
[    14.577]     LinBlueMaskSize: 8
[    14.577]     LinBlueFieldPosition: 0
[    14.577]     LinRsvdMaskSize: 8
[    14.577]     LinRsvdFieldPosition: 24
[    14.577]     MaxPixelClock: 229500000
[    14.579] Mode: 145 (1600x1200)
[    14.579]     ModeAttributes: 0x39f
[    14.579]     WinAAttributes: 0x7
[    14.579]     WinBAttributes: 0x0
[    14.579]     WinGranularity: 64
[    14.579]     WinSize: 64
[    14.579]     WinASegment: 0xa000
[    14.579]     WinBSegment: 0x0
[    14.579]     WinFuncPtr: 0xc0009a73
[    14.579]     BytesPerScanline: 1600
[    14.579]     XResolution: 1600
[    14.579]     YResolution: 1200
[    14.579]     XCharSize: 8
[    14.579]     YCharSize: 16
[    14.579]     NumberOfPlanes: 1
[    14.579]     BitsPerPixel: 8
[    14.579]     NumberOfBanks: 1
[    14.579]     MemoryModel: 4
[    14.579]     BankSize: 0
[    14.579]     NumberOfImages: 1
[    14.579]     RedMaskSize: 0
[    14.579]     RedFieldPosition: 0
[    14.579]     GreenMaskSize: 0
[    14.579]     GreenFieldPosition: 0
[    14.579]     BlueMaskSize: 0
[    14.579]     BlueFieldPosition: 0
[    14.579]     RsvdMaskSize: 0
[    14.579]     RsvdFieldPosition: 0
[    14.579]     DirectColorModeInfo: 0
[    14.579]     PhysBasePtr: 0xc0000000
[    14.579]     LinBytesPerScanLine: 1600
[    14.579]     BnkNumberOfImagePages: 1
[    14.579]     LinNumberOfImagePages: 1
[    14.579]     LinRedMaskSize: 0
[    14.579]     LinRedFieldPosition: 0
[    14.579]     LinGreenMaskSize: 0
[    14.579]     LinGreenFieldPosition: 0
[    14.579]     LinBlueMaskSize: 0
[    14.579]     LinBlueFieldPosition: 0
[    14.579]     LinRsvdMaskSize: 0
[    14.579]     LinRsvdFieldPosition: 0
[    14.579]     MaxPixelClock: 229500000
[    14.580] Mode: 146 (1600x1200)
[    14.580]     ModeAttributes: 0x39f
[    14.580]     WinAAttributes: 0x7
[    14.580]     WinBAttributes: 0x0
[    14.580]     WinGranularity: 64
[    14.580]     WinSize: 64
[    14.580]     WinASegment: 0xa000
[    14.580]     WinBSegment: 0x0
[    14.580]     WinFuncPtr: 0xc0009a73
[    14.580]     BytesPerScanline: 3200
[    14.580]     XResolution: 1600
[    14.580]     YResolution: 1200
[    14.580]     XCharSize: 8
[    14.580]     YCharSize: 16
[    14.580]     NumberOfPlanes: 1
[    14.580]     BitsPerPixel: 16
[    14.580]     NumberOfBanks: 1
[    14.580]     MemoryModel: 6
[    14.580]     BankSize: 0
[    14.580]     NumberOfImages: 1
[    14.580]     RedMaskSize: 5
[    14.580]     RedFieldPosition: 11
[    14.580]     GreenMaskSize: 6
[    14.580]     GreenFieldPosition: 5
[    14.580]     BlueMaskSize: 5
[    14.580]     BlueFieldPosition: 0
[    14.580]     RsvdMaskSize: 0
[    14.580]     RsvdFieldPosition: 0
[    14.580]     DirectColorModeInfo: 0
[    14.580]     PhysBasePtr: 0xc0000000
[    14.580]     LinBytesPerScanLine: 3200
[    14.580]     BnkNumberOfImagePages: 1
[    14.580]     LinNumberOfImagePages: 1
[    14.580]     LinRedMaskSize: 5
[    14.580]     LinRedFieldPosition: 11
[    14.580]     LinGreenMaskSize: 6
[    14.580]     LinGreenFieldPosition: 5
[    14.580]     LinBlueMaskSize: 5
[    14.580]     LinBlueFieldPosition: 0
[    14.580]     LinRsvdMaskSize: 0
[    14.580]     LinRsvdFieldPosition: 0
[    14.580]     MaxPixelClock: 229500000
[    14.582] Mode: 147 (1400x1050)
[    14.582]     ModeAttributes: 0x39f
[    14.582]     WinAAttributes: 0x7
[    14.582]     WinBAttributes: 0x0
[    14.582]     WinGranularity: 64
[    14.582]     WinSize: 64
[    14.582]     WinASegment: 0xa000
[    14.582]     WinBSegment: 0x0
[    14.582]     WinFuncPtr: 0xc0009a73
[    14.582]     BytesPerScanline: 1400
[    14.582]     XResolution: 1400
[    14.582]     YResolution: 1050
[    14.582]     XCharSize: 8
[    14.582]     YCharSize: 14
[    14.582]     NumberOfPlanes: 1
[    14.582]     BitsPerPixel: 8
[    14.582]     NumberOfBanks: 1
[    14.582]     MemoryModel: 4
[    14.582]     BankSize: 0
[    14.582]     NumberOfImages: 1
[    14.582]     RedMaskSize: 0
[    14.582]     RedFieldPosition: 0
[    14.582]     GreenMaskSize: 0
[    14.582]     GreenFieldPosition: 0
[    14.582]     BlueMaskSize: 0
[    14.582]     BlueFieldPosition: 0
[    14.582]     RsvdMaskSize: 0
[    14.582]     RsvdFieldPosition: 0
[    14.582]     DirectColorModeInfo: 0
[    14.582]     PhysBasePtr: 0xc0000000
[    14.582]     LinBytesPerScanLine: 1400
[    14.582]     BnkNumberOfImagePages: 1
[    14.582]     LinNumberOfImagePages: 1
[    14.582]     LinRedMaskSize: 0
[    14.582]     LinRedFieldPosition: 0
[    14.582]     LinGreenMaskSize: 0
[    14.582]     LinGreenFieldPosition: 0
[    14.582]     LinBlueMaskSize: 0
[    14.582]     LinBlueFieldPosition: 0
[    14.582]     LinRsvdMaskSize: 0
[    14.582]     LinRsvdFieldPosition: 0
[    14.582]     MaxPixelClock: 229500000
[    14.583] Mode: 148 (1400x1050)
[    14.583]     ModeAttributes: 0x39f
[    14.583]     WinAAttributes: 0x7
[    14.583]     WinBAttributes: 0x0
[    14.583]     WinGranularity: 64
[    14.583]     WinSize: 64
[    14.583]     WinASegment: 0xa000
[    14.583]     WinBSegment: 0x0
[    14.583]     WinFuncPtr: 0xc0009a73
[    14.583]     BytesPerScanline: 2800
[    14.583]     XResolution: 1400
[    14.583]     YResolution: 1050
[    14.583]     XCharSize: 8
[    14.583]     YCharSize: 14
[    14.583]     NumberOfPlanes: 1
[    14.583]     BitsPerPixel: 16
[    14.583]     NumberOfBanks: 1
[    14.583]     MemoryModel: 6
[    14.583]     BankSize: 0
[    14.583]     NumberOfImages: 1
[    14.583]     RedMaskSize: 5
[    14.583]     RedFieldPosition: 11
[    14.583]     GreenMaskSize: 6
[    14.583]     GreenFieldPosition: 5
[    14.583]     BlueMaskSize: 5
[    14.583]     BlueFieldPosition: 0
[    14.583]     RsvdMaskSize: 0
[    14.583]     RsvdFieldPosition: 0
[    14.583]     DirectColorModeInfo: 0
[    14.583]     PhysBasePtr: 0xc0000000
[    14.583]     LinBytesPerScanLine: 2800
[    14.583]     BnkNumberOfImagePages: 1
[    14.583]     LinNumberOfImagePages: 1
[    14.583]     LinRedMaskSize: 5
[    14.583]     LinRedFieldPosition: 11
[    14.583]     LinGreenMaskSize: 6
[    14.583]     LinGreenFieldPosition: 5
[    14.583]     LinBlueMaskSize: 5
[    14.583]     LinBlueFieldPosition: 0
[    14.583]     LinRsvdMaskSize: 0
[    14.583]     LinRsvdFieldPosition: 0
[    14.583]     MaxPixelClock: 229500000
[    14.584] *Mode: 152 (2048x1536)
[    14.584]     ModeAttributes: 0x3db
[    14.584]     WinAAttributes: 0x7
[    14.584]     WinBAttributes: 0x0
[    14.584]     WinGranularity: 64
[    14.584]     WinSize: 64
[    14.584]     WinASegment: 0xa000
[    14.585]     WinBSegment: 0x0
[    14.585]     WinFuncPtr: 0xc0009a73
[    14.585]     BytesPerScanline: 8192
[    14.585]     XResolution: 2048
[    14.585]     YResolution: 1536
[    14.585]     XCharSize: 8
[    14.585]     YCharSize: 16
[    14.585]     NumberOfPlanes: 1
[    14.585]     BitsPerPixel: 32
[    14.585]     NumberOfBanks: 1
[    14.585]     MemoryModel: 6
[    14.585]     BankSize: 0
[    14.585]     NumberOfImages: 0
[    14.585]     RedMaskSize: 8
[    14.585]     RedFieldPosition: 16
[    14.585]     GreenMaskSize: 8
[    14.585]     GreenFieldPosition: 8
[    14.585]     BlueMaskSize: 8
[    14.585]     BlueFieldPosition: 0
[    14.585]     RsvdMaskSize: 8
[    14.585]     RsvdFieldPosition: 24
[    14.585]     DirectColorModeInfo: 0
[    14.585]     PhysBasePtr: 0xc0000000
[    14.585]     LinBytesPerScanLine: 8192
[    14.585]     BnkNumberOfImagePages: 0
[    14.585]     LinNumberOfImagePages: 0
[    14.585]     LinRedMaskSize: 8
[    14.585]     LinRedFieldPosition: 16
[    14.585]     LinGreenMaskSize: 8
[    14.585]     LinGreenFieldPosition: 8
[    14.585]     LinBlueMaskSize: 8
[    14.585]     LinBlueFieldPosition: 0
[    14.585]     LinRsvdMaskSize: 8
[    14.585]     LinRsvdFieldPosition: 24
[    14.585]     MaxPixelClock: 229500000
[    14.585] 
[    14.585] (II) VESA(0): Total Memory: 512 64KB banks (32768kB)
[    14.585] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    14.585] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    14.585] (II) VESA(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    14.585] (WW) VESA(0): Unable to estimate virtual size
[    14.585] (II) VESA(0): Not using built-in mode "2048x1536" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    14.585] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    14.585] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    14.585] (II) VESA(0): <default monitor>: Using hsync range of 31.50-48.00 kHz
[    14.585] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    14.585] (II) VESA(0): <default monitor>: Using maximum pixel clock of 65.00 MHz
[    14.585] (WW) VESA(0): Unable to estimate virtual size
[    14.585] (II) VESA(0): Not using built-in mode "2048x1536" (hsync out of range)
[    14.585] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[    14.585] (II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
[    14.585] (II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
[    14.585] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    14.585] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    14.585] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    14.585] (**) VESA(0): *Built-in mode "1024x768"
[    14.585] (**) VESA(0): *Built-in mode "800x600"
[    14.585] (**) VESA(0): *Built-in mode "640x480"
[    14.585] (==) VESA(0): DPI set to (96, 96)
[    14.585] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    14.587] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    14.588] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    14.590] (**) VESA(0): Using "Shadow Framebuffer"
[    14.590] (II) Loading sub module "shadow"
[    14.590] (II) LoadModule: "shadow"
[    14.590] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    14.590] (II) Module shadow: vendor="X.Org Foundation"
[    14.590]     compiled for 1.10.4, module version = 1.1.0
[    14.590]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.590] (II) Loading sub module "fb"
[    14.590] (II) LoadModule: "fb"
[    14.590] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.590] (II) Module fb: vendor="X.Org Foundation"
[    14.590]     compiled for 1.10.4, module version = 1.0.0
[    14.590]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.590] (II) UnloadModule: "fbdev"
[    14.590] (II) Unloading fbdev
[    14.590] (II) UnloadModule: "fbdevhw"
[    14.590] (II) Unloading fbdevhw
[    14.590] (==) Depth 24 pixmap format is 32 bpp
[    14.590] (II) Loading sub module "int10"
[    14.590] (II) LoadModule: "int10"
[    14.591] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.591] (II) Module int10: vendor="X.Org Foundation"
[    14.591]     compiled for 1.10.4, module version = 1.0.0
[    14.591]     ABI class: X.Org Video Driver, version 10.0
[    14.591] (II) VESA(0): initializing int10
[    14.595] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    14.605] (II) VESA(0): VESA BIOS detected
[    14.605] (II) VESA(0): VESA VBE Version 3.0
[    14.605] (II) VESA(0): VESA VBE Total Mem: 32768 kB
[    14.605] (II) VESA(0): VESA VBE OEM: NVIDIA
[    14.605] (II) VESA(0): VESA VBE OEM Software Rev: 5.97
[    14.605] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    14.605] (II) VESA(0): VESA VBE OEM Product: MCP61 - mcp61-86
[    14.605] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    14.608] (II) VESA(0): virtual address = 0x7f6907fad000,
    physical address = 0xc0000000, size = 33554432
[    14.617] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    14.654] (==) VESA(0): Default visual is TrueColor
[    14.654] (==) VESA(0): Backing store disabled
[    14.654] (==) VESA(0): DPMS enabled
[    14.654] (==) RandR enabled
[    14.654] (II) Initializing built-in extension Generic Event Extension
[    14.654] (II) Initializing built-in extension SHAPE
[    14.654] (II) Initializing built-in extension MIT-SHM
[    14.654] (II) Initializing built-in extension XInputExtension
[    14.654] (II) Initializing built-in extension XTEST
[    14.654] (II) Initializing built-in extension BIG-REQUESTS
[    14.654] (II) Initializing built-in extension SYNC
[    14.654] (II) Initializing built-in extension XKEYBOARD
[    14.654] (II) Initializing built-in extension XC-MISC
[    14.654] (II) Initializing built-in extension SECURITY
[    14.654] (II) Initializing built-in extension XINERAMA
[    14.654] (II) Initializing built-in extension XFIXES
[    14.654] (II) Initializing built-in extension RENDER
[    14.654] (II) Initializing built-in extension RANDR
[    14.654] (II) Initializing built-in extension COMPOSITE
[    14.654] (II) Initializing built-in extension DAMAGE
[    14.654] (II) Initializing built-in extension GESTURE
[    14.662] (II) AIGLX: Screen 0 is not DRI2 capable
[    14.662] (II) AIGLX: Screen 0 is not DRI capable
[    14.662] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
[    14.664] (II) AIGLX: Loaded and initialized swrast
[    14.664] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    14.673] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.680] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.680] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.680] (II) LoadModule: "evdev"
[    14.680] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.681] (II) Module evdev: vendor="X.Org Foundation"
[    14.681]     compiled for 1.10.2, module version = 2.6.0
[    14.681]     Module class: X.Org XInput Driver
[    14.681]     ABI class: X.Org XInput driver, version 12.3
[    14.681] (II) Using input driver 'evdev' for 'Power Button'
[    14.681] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.681] (**) Power Button: always reports core events
[    14.681] (**) Power Button: Device: "/dev/input/event1"
[    14.681] (--) Power Button: Found keys
[    14.681] (II) Power Button: Configuring as keyboard
[    14.681] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.681] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.681] (**) Option "xkb_rules" "evdev"
[    14.681] (**) Option "xkb_model" "pc105"
[    14.681] (**) Option "xkb_layout" "us"
[    14.682] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.682] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.682] (II) Using input driver 'evdev' for 'Power Button'
[    14.682] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.682] (**) Power Button: always reports core events
[    14.682] (**) Power Button: Device: "/dev/input/event0"
[    14.683] (--) Power Button: Found keys
[    14.683] (II) Power Button: Configuring as keyboard
[    14.683] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    14.683] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.683] (**) Option "xkb_rules" "evdev"
[    14.683] (**) Option "xkb_model" "pc105"
[    14.683] (**) Option "xkb_layout" "us"
[    14.684] (II) config/udev: Adding input device DELL DELL USB Keyboard (/dev/input/event2)
[    14.684] (**) DELL DELL USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.684] (II) Using input driver 'evdev' for 'DELL DELL USB Keyboard'
[    14.684] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.684] (**) DELL DELL USB Keyboard: always reports core events
[    14.684] (**) DELL DELL USB Keyboard: Device: "/dev/input/event2"
[    14.684] (--) DELL DELL USB Keyboard: Found keys
[    14.684] (II) DELL DELL USB Keyboard: Configuring as keyboard
[    14.684] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input2/event2"
[    14.684] (II) XINPUT: Adding extended input device "DELL DELL USB Keyboard" (type: KEYBOARD)
[    14.684] (**) Option "xkb_rules" "evdev"
[    14.684] (**) Option "xkb_model" "pc105"
[    14.684] (**) Option "xkb_layout" "us"
[    14.685] (II) config/udev: Adding input device DELL DELL USB Keyboard (/dev/input/event3)
[    14.685] (**) DELL DELL USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.685] (II) Using input driver 'evdev' for 'DELL DELL USB Keyboard'
[    14.685] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.685] (**) DELL DELL USB Keyboard: always reports core events
[    14.685] (**) DELL DELL USB Keyboard: Device: "/dev/input/event3"
[    14.685] (--) DELL DELL USB Keyboard: Found keys
[    14.685] (II) DELL DELL USB Keyboard: Configuring as keyboard
[    14.685] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input3/event3"
[    14.685] (II) XINPUT: Adding extended input device "DELL DELL USB Keyboard" (type: KEYBOARD)
[    14.685] (**) Option "xkb_rules" "evdev"
[    14.685] (**) Option "xkb_model" "pc105"
[    14.685] (**) Option "xkb_layout" "us"
[    14.686] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event4)
[    14.686] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    14.686] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    14.686] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.686] (**) USB Optical Mouse: always reports core events
[    14.686] (**) USB Optical Mouse: Device: "/dev/input/event4"
[    14.686] (--) USB Optical Mouse: Found 3 mouse buttons
[    14.686] (--) USB Optical Mouse: Found scroll wheel(s)
[    14.686] (--) USB Optical Mouse: Found relative axes
[    14.686] (--) USB Optical Mouse: Found x and y relative axes
[    14.686] (II) USB Optical Mouse: Configuring as mouse
[    14.686] (II) USB Optical Mouse: Adding scrollwheel support
[    14.686] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    14.686] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.686] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input4/event4"
[    14.686] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    14.686] (II) USB Optical Mouse: initialized for relative axes.
[    14.686] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    14.686] (**) USB Optical Mouse: (accel) acceleration profile 0
[    14.686] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    14.686] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    14.686] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    14.686] (II) No input driver/identifier specified (ignoring)
[    43.237] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
```My /etc/X11 directory doesn't have a file named xorg.conf as you can see:

```
name@name:/etc/X11$ ls
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config

```Results from other commands:

```
name@name:/etc/X11$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 3185: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
31: None 00.1: 10000 Monitor                                    
  [Created at monitor.95]
  Unique ID: jyhG.1pU1cwyUUDF
  Hardware Class: monitor
  Model: "AOC 2036"
  Vendor: AOC "AOC"
  Device: eisa 0x2036 "2036"
  Serial ID: "Q8199JA010068"
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@67Hz
  Resolution: 640x480@72Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@56Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@72Hz
  Resolution: 800x600@75Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@70Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x720@60Hz
  Resolution: 1600x900@60Hz
  Size: 443x249 mm
  Detailed Timings #0:
     Resolution: 1600x900
     Horizontal: 1600 1624 1704 1800 (+24 +104 +200) +hsync
       Vertical:  900  901  904 1000 (+1 +4 +100) +vsync
    Frequencies: 108.00 MHz, 60.00 kHz, 60.00 Hz
  Driver Info #0:
    Max. Resolution: 1600x900
    Vert. Sync Range: 55-75 Hz
    Hor. Sync Range: 30-83 kHz
    Bandwidth: 108 MHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
name@name:/etc/X11$ sudo hwinfo --frambuffer
Usage: hwinfo [options]
Probe for hardware.
  --short        just a short listing
  --log logfile  write info to logfile
  --debug level  set debuglevel
  --version      show libhd version
  --dump-db n    dump hardware data base, 0: external, 1: internal
  --hw_item      probe for hw_item
  hw_item is one of:
   all, bios, block, bluetooth, braille, bridge, camera, cdrom, chipcard,
   cpu, disk, dsl, dvb, fingerprint, floppy, framebuffer, gfxcard, hub,
   ide, isapnp, isdn, joystick, keyboard, memory, modem, monitor, mouse,
   netcard, network, partition, pci, pcmcia, pcmcia-ctrl, pppoe, printer,
   scanner, scsi, smp, sound, storage-ctrl, sys, tape, tv, usb, usb-ctrl,
   vbe, wlan, zip

  Note: debug info is shown only in the log file. (If you specify a
  log file the debug level is implicitly set to a reasonable value.)
name@name:/etc/X11$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  

```By the way, thanks for the tons of help you've given!
Go to System Settings > Addition Drivers > Look for the driver that has "Recommended" after it...

What the above said, is that you have an nvidia card, but don't have it's drivers installed, so it then tried the nouveau driver, then dropped down the the VESA driver.  Since your drivers were not installed, you had no /etc/X11/xorg.conf file. On the on command thew errored - typo = should have been "--framebuffer" instead of "--frambuffer". No matters, we got what we needed to see.

---

### Post by Crimson_Tider on 2011-12-08
> **MAFoElffen said:**
> Go to System Settings > Addition Drivers > Look for the driver that has "Recommended" after it...

What the above said, is that you have an nvidia card, but don't have it's drivers installed, so it then tried the nouveau driver, then dropped down the the VESA driver.  Since your drivers were not installed, you had no /etc/X11/xorg.conf file. On the on command thew errored - typo = should have been "--framebuffer" instead of "--frambuffer". No matters, we got what we needed to see.

I'm fairly certain I tried the recommended driver when I very first installed.  I then tried at least 2 other ones, maybe 3 or 4, and then only after those didn't work, I installed the one I downloaded from NVIDIA.  Shouldn't it show that I tried all of those?

---

### Post by MAFoElffen on 2011-12-08
> **Crimson_Tider said:**
> I'm fairly certain I tried the recommended driver when I very first installed.  I then tried at least 2 other ones, maybe 3 or 4, and then only after those didn't work, I installed the one I downloaded from NVIDIA.  Shouldn't it show that I tried all of those?
Careful there.... The packaged and binary drivers don't always play nice together. Sometime you end out with mixed versions of a driver that conflict with each other.  Always remove a driver before installing another. The first part of each of these instructions remove old drivers before an install:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")** 
[**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by Crimson_Tider on 2011-12-09
Those are the instructions that I followed just before I installed the current driver.  Perhaps I should just try again ...

---

### Post by MAFoElffen on 2011-12-09
> **Crimson_Tider said:**
> Those are the instructions that I followed just before I installed the current driver.  Perhaps I should just try again ...
Do you IM or IRC?  This has been going 3 weeks now.  We could get this done in less that an hour.

---

### Post by Crimson_Tider on 2011-12-10
> **MAFoElffen said:**
> Do you IM or IRC?  This has been going 3 weeks now.  We could get this done in less that an hour.

Yes, I chat on Gmail or Facebook.  Will one of those work for you?

---

### Post by MAFoElffen on 2011-12-10
> **Crimson_Tider said:**
> Yes, I chat on Gmail or Facebook.  Will one of those work for you?Either. Although I haven't logged into facebook for almost a year.
GTalk. --> MAFoElffen 
Facebook --> Mike Ferreira

---

### Post by Crimson_Tider on 2011-12-10
Which Mike Ferreira are you on Facebook?  There are lots of them!

---

### Post by Crimson_Tider on 2011-12-10
Well, I got it.  With great difficulty, I reinstalled the driver, but now it works perfectly.  Thanks MAFoElffen!

---

