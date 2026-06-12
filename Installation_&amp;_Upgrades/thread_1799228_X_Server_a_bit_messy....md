---
title: "X Server a bit messy..."
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by Neoxhadowespio on 2011-07-07
Eheheh... Well I'm screwed again. Some time ago I was attempting to install updates for my OS (Ubuntu 10.10 Maverick) when the Update Manager told me that it had some broken packages that needed to repaired first, or something. "xserver-xorg-core." Well, the most likely cause of that was a half installation of Natty. The computer had accidently shut down during the operation. So I repaired the package (via Terminal) and rebooted my system. It froze immediatly after showing me the User Select thingie. A reboot was not enough. So I held down (shift) while I was booting so I could load the recovery menu. Then, using W3M I download Maverick's original "xserver-xorg-config" .deb from Launchpad and installed that. But rather it made the problem worse. After the splash-screen the system entirely disconnects from Pymouth. And I know that because it tells me so in the face. I again tried to rely on the recovery menu once more but when I load that, the scripts are quickly displayed (thats normal) then the screen goes black. Now I am typing this from Rescatux LiveCD. What do you think I should do. Based on some research the issue is associated with a bad configuration file, however I cannot do anything to the HDD because it is encrypted. Unless there is some terminal code to enter my password and unlock it temporarily, or something. So, yeah. Any help would be greatly appreciated and will keep the Linux community strong! :KS

---

### Post by MAFoElffen on 2011-07-07
> **Neoxhadowespio said:**
> Eheheh... Well I'm screwed again. Some time ago I was attempting to install updates for my OS (Ubuntu 10.10 Maverick) when the Update Manager told me that it had some broken packages that needed to repaired first, or something. "xserver-xorg-core." Well, the most likely cause of that was a half installation of Natty. The computer had accidently shut down during the operation. So I repaired the package (via Terminal) and rebooted my system. It froze immediatly after showing me the User Select thingie. A reboot was not enough. So I held down (shift) while I was booting so I could load the recovery menu. Then, using W3M I download Maverick's original "xserver-xorg-config" .deb from Launchpad and installed that. But rather it made the problem worse. After the splash-screen the system entirely disconnects from Pymouth. And I know that because it tells me so in the face. I again tried to rely on the recovery menu once more but when I load that, the scripts are quickly displayed (thats normal) then the screen goes black. Now I am typing this from Rescatux LiveCD. What do you think I should do. Based on some research the issue is associated with a bad configuration file, however I cannot do anything to the HDD because it is encrypted. Unless there is some terminal code to enter my password and unlock it temporarily, or something. So, yeah. Any help would be greatly appreciated and will keep the Linux community strong! :KSOkay... Yon can get to a grub menu by holding the shift key while booting, right?

While in the grub menu, press " e ' to get into an edit mode.  Go to the kernel boot line- starts with "linux"... Near the end it will say " ro quiet splash vt.handoff=7 "... Change it to " ro --verbose text ".  Press <Cntrl><x> and it will boot with those options into a text console with verbose boot messaging turned on.

You can review the messages by the hot-keys <Cntrl><Alt><+> and <Cntrl><Alt><-> to go up or down a page at a time.  At the login prompt, enter you username and password.

After it gets to a command prompt:
```
[FONT=monospace]
[/FONT]sudo dpkg --configure -a 
sudo apt-get clean all
sudo apt-get update
sudo apt-get -f install
sudo apt-get install libqt-perl
sudo apt-get install xserver-xorg-core -t experimental 
sudo apt-get dist-update

```That should refresh your packages database, try to fix any broken packages and try to resolve any un-met dependencies.

---

### Post by Neoxhadowespio on 2011-07-07
Okay, thank you. I will try this as soon as I get the chance.
But how will the login prompt appear by editing a small line of code that enables verbose boot?
I should mention that I can boot into other "old" linux kernels and (without an desktop enviroment) boot into my system. So thats probably my best option...

---

### Post by Neoxhadowespio on 2011-07-07
Well then. I have found out that booting into any recovery "mode" regardless of which kernel I use causes the screen to go black. Booting into normal mode in any other kernel except my default one works fine except its all terminal based. So I did the codes from there. The very first one doesn't do anything because of a "xserver-xorg-config" error. So I skipped that and did the ones after it. The fifth code is "not an installation candidate," or something. The sixth one did not do anything because the package was already the most recent. I purposely skipped the last one because I really don't want that. I'm fine with Maverick, I have little faith in Natty now. All because of Unity...
Anyway, I just remembered to attempt to preform the first code again. After all, only now had the broken package been fixed so yeah!

---

### Post by MAFoElffen on 2011-07-07
> **Neoxhadowespio said:**
> Well then. I have found out that booting into any recovery "mode" regardless of which kernel I use causes the screen to go black. Booting into normal mode in any other kernel except my default one works fine except its all terminal based. So I did the codes from there. The very first one doesn't do anything because of a "xserver-xorg-config" error. So I skipped that and did the ones after it. The fifth code is "not an installation candidate," or something. The sixth one did not do anything because the package was already the most recent. I purposely skipped the last one because I really don't want that. I'm fine with Maverick, I have little faith in Natty now. All because of Unity...
Anyway, I just remembered to attempt to preform the first code again. After all, only now had the broken package been fixed so yeah!Yes, I'm not sue how to d that command and have it no do a release upgrade.... But if on a current release and executed,           
> 
dist-upgrade in addition to performing the function of of upgrade, also intelligently 
handles changing dependencies with new versions of packages; apt-get has a 
"smart" conflict resolution system, and it will attempt to upgrade the most 
important packages at the expense of less important ones if necessary. So, 
dist-upgrade command may remove some packages. The /etc/apt/sources.list file 
contains a list of locations from which to retrieve desired package files. See also 
apt_preferences(5) for a mechanism for overriding the general settings for individual 
packages.
But yes, Maverick would try to go to Natty... Darn, would not be good for you.


Admittedly, I mostly use Ubuntu Classic (Gnome) under 11.04.  Just as it looked in 10.10 and I know where everything is.  Trying to ween myself into "changes outside my comfort zone"- as 11.10 loses Ubuntu Classic (Gnome 2.x / no longer supported) and goes to Gnome 3, with main as Unity 3D and fackback as Unity 2D...  New learinng curve again.

---

### Post by MAFoElffen on 2011-07-07
> **Neoxhadowespio said:**
> Okay, thank you. I will try this as soon as I get the chance.
But how will the login prompt appear by editing a small line of code that enables verbose boot?
I should mention that I can boot into other "old" linux kernels and (without an desktop enviroment) boot into my system. So thats probably my best option...
Lots of messages... then after the kernel boots, it goes to a text console... Not pretty, but you can do things from the commands line, start GDM, toggle back to it and kill (stop) GDM... So diagnose, test, install packages and work out your problems.

---

### Post by Neoxhadowespio on 2011-07-08
>  *Admittedly, I mostly use Ubuntu Classic (Gnome) under 11.04. Just as it looked in 10.10 and I know where everything is. Trying to ween myself into "changes outside my comfort zone"- as 11.10 loses Ubuntu Classic (Gnome 2.x / no longer supported) and goes to Gnome 3, with main as Unity 3D and fackback as Unity 2D... New learinng curve again.* I had high hopes for 11.10 when I heard it would use Gnome 3. The interface is sleek and it looks effecient. But that opinion change when I found out that the taskbar and the menus were shoved into that one "Applications" button. And then I found out that it would go back to Unity on top of that. Let's just hope it works out well. So what do you suggest now? (Haven't done "sudo dpkg --confgure -a" yet so thats what I will do next.)

---

### Post by MAFoElffen on 2011-07-08
> **Neoxhadowespio said:**
> I had high hopes for 11.10 when I heard it would use Gnome 3. The interface is sleek and it looks effecient. But that opinion change when I found out that the taskbar and the menus were shoved into that one "Applications" button. And then I found out that it would go back to Unity on top of that. Let's just hope it works out well. So what do you suggest now? (Haven't done "sudo dpkg --confgure -a" yet so thats what I will do next.)
Please try it in this order and please post the results:
```
[FONT=monospace]
[/FONT]sudo apt-get install -f 
sudo dpkg --configure -a[FONT=monospace]
[/FONT]cat /var/log/dist-upgrade/apt.log | grep broken

```

---

### Post by Neoxhadowespio on 2011-07-08
(Typing through W3M. Appologies if this doesn't look right.) var/log/dist-update/apt.log The directory does not exist. Any ideas?

---

### Post by MAFoElffen on 2011-07-09
> **Neoxhadowespio said:**
> (Typing through W3M. Appologies if this doesn't look right.) var/log/dist-update/apt.log The directory does not exist. Any ideas?
Apology, that log was for different version... Try this one:
```

cat /var/log/apt/history.log | grep broken

```

---

### Post by Neoxhadowespio on 2011-07-09
The "cat" code worked this time around... after I "cd /". But I am still being disconnected from Plymouth. Interestingly enough the recovery boots worked this time and the normal ones did not.

---

### Post by MAFoElffen on 2011-07-09
> **Neoxhadowespio said:**
> The "cat" code worked this time around... after I "cd /". But I am still being disconnected from Plymouth. Interestingly enough the recovery boots worked this time and the normal ones did not.
That command doesn't fix things.

I'm sorry, I thought I mentioned that I needed to see the output of that to see what broken packages...  I still would like to see that please.

---

### Post by Neoxhadowespio on 2011-07-09
Oh it just does its job and leaves. What I mean by that is that there is no output. Just another line to enter your commands. I thought it would fix things because of " | grep broken". I am unfamiliar with something like that.

---

### Post by MAFoElffen on 2011-07-09
> **Neoxhadowespio said:**
> Oh it just does its job and leaves. What I mean by that is that there is no output. Just another line to enter your commands. I thought it would fix things because of " | grep broken". I am unfamiliar with something like that.
So from what you just said- form the output of apt-get's history, grep is not seeing any broken packages?  And there was was out from "sudo apt-get install -f" saying there were any dependency problems of packages that needed to be fixed?

And there "is" still a problem with all that right? (It just didn't go away on you and we just didn't realize it, right? I think I already know that answer.

  I know I'm going to regret this but, can you please post the whole /var/log/apt/history.log file. as it is, without any filters...

---

### Post by Neoxhadowespio on 2011-07-09
> *So from what you just said- form the output of apt-get's history, grep is not seeing any broken packages? And there was was out from "sudo apt-get install -f" saying there were any dependency problems of packages that needed to be fixed?*If I remember correctly there are no remaining packages that need to be fixed. Although if you say so I will find out once more. I believe the problem is that I need a specific "xserver-xorg-core" package version. The one that I had before problems. If I wanted to update the package I should have updated "xserver" altogether no?
> *And there "is" still a problem with all that right? (It just didn't go away on you and we just didn't realize it, right? I think I already know that answer.*No it is still there. 
> *I know I'm going to regret this but, can you please post the whole /var/log/apt/history.log file. as it is, without any filters...*How do you suppose I do that? First of all what line of code would enable for me to view it all? And second would the output not be quite long? How can I "pastebin" all of that? Unless you expect me to copy down the entire thing on paper by hand then type it all over again here...

Edit: Oh wait never mind I was thinking of something else (for viewing the history.log on the command line).

---

### Post by MAFoElffen on 2011-07-09
> **Neoxhadowespio said:**
> If I remember correctly there are no remaining packages that need to be fixed. Although if you say so I will find out once more. I believe the problem is that I need a specific "xserver-xorg-core" package version. The one that I had before problems. If I wanted to update the package I should have updated "xserver" altogether no?
No it is still there. 
How do you suppose I do that? First of all what line of code would enable for me to view it all? And second would the output not be quite long? How can I "pastebin" all of that? Unless you expect me to copy down the entire thing on paper by hand then type it all over again here...

Edit: Oh wait never mind I was thinking of something else (for viewing the history.log on the command line).
So know that there are no broken packages and no unmet dependencies (reported)... Does that mean xserver-core or whatever now shows no errors from __ ?
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Neoxhadowespio on 2011-07-09
Nothing new...

---

### Post by MAFoElffen on 2011-07-09
> **Neoxhadowespio said:**
> Nothing new...
Now that those problems are fixed...

Please remove "splash" and "quiet" from your grub menu entries.

Instructions:
1) Edit  the file /etc/default/grub as root*.  You should see a line that looks like: 
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```Comment this line out 
```

# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  

```or delete the text within the quotation marks, leaving the quotation marks... 
```

GRUB_CMDLINE_LINUX_DEFAULT=""  

```
Either way / One of the two methods.  Save and exit.
 
2) Run: 
```

sudo update-grub

```Reboot and see what happens / if it fixes it.

* There are many ways to edit a file as root.  I prefer if required from a terminal > type "sudo vi  file_name".  If I have an Xsession (even from a LiveCD) then "sudo gedit file_name."  Since you do Kubuntu then you might be more familiar with "kdesudo kate file_name"?

---

### Post by Neoxhadowespio on 2011-07-09
Will do. I think I would prefer GNU Nano ;)
But I have never dwelled too deep into the "politics" of this.

---

### Post by MAFoElffen on 2011-07-09
> **Neoxhadowespio said:**
> Will do. I think I would prefer GNU Nano ;)
But I have never dwelled too deep into the "politics" of this.
Yes, all personal preferences.  LOL

---

### Post by Neoxhadowespio on 2011-07-09
I have confirmed that I prefer Nano. Also all that removing the splash does is cause Ubuntu to crash while booting. I should mention that there was more that just "quite splash" in the file's line. For backup purposes I had it written down on some paper. I had everything cleared between the " ~ ". Should I have only cleared the "quite splash" part? Any other ideas?

---

### Post by MAFoElffen on 2011-07-09
> **Neoxhadowespio said:**
> I have confirmed that I prefer Nano. Also all that removing the splash does is cause Ubuntu to crash while booting. I should mention that there was more that just "quite splash" in the file's line. For backup purposes I had it written down on some paper. I had everything cleared between the " ~ ". [COLOR=Green]Should I have only cleared the "quite splash" part?[/COLOR] Any other ideas?
Yes, just that part, those two words, leaving the other kernel boot switches.  Sorry.  I should have thought of that.

---

### Post by Neoxhadowespio on 2011-07-09
Alright. I will do that tommorow.

---

### Post by Neoxhadowespio on 2011-07-10
It still crashes. I have checked over my work and it is word-by-word the same. Probably missing something as sensitive as a space.  ](*,)

---

### Post by MAFoElffen on 2011-07-10
> **Neoxhadowespio said:**
> It still crashes. I have checked over my work and it is word-by-word the same. Probably missing something as sensitive as a space.  ](*,)
LOL  Remember, It's an adventure...  What are the switches you wrote down?  Maybe I could help with that syntax?

---

### Post by Neoxhadowespio on 2011-07-11
No luck. How can I generate a new cfg file?

---

### Post by Neoxhadowespio on 2011-07-11
Also maybe others can pitch in as well at the moment...

---

### Post by Neoxhadowespio on 2011-07-11
(bump!)

---

### Post by MAFoElffen on 2011-07-11
> **Neoxhadowespio said:**
> No luck. How can I generate a new cfg file?
Remind me what video hardware you have... Working on 10 threads....

What was the kernel boot line before you editted?  You said you had written it down...

New config file for what? (many types)

---

### Post by Neoxhadowespio on 2011-07-12
Well if you are asking for resolution the screen is 1680x1200 or something. But the line had (by deafult) 1600x1200. I also have dedicated GPU (forget the specs) and I think thats all. 

The original line was something like this: ```
 quite splash nomodest video=uvesofb:mode_option=1600x1200-24(*comma)mtrr=3 scroll=ywarp 
```How are there "many" different grub cnfg files? :wink:

---

### Post by MAFoElffen on 2011-07-12
> **Neoxhadowespio said:**
> Well if you are asking for resolution the screen is 1680x1200 or something. But the line had (by deafult) 1600x1200. I also have [COLOR=Red]dedicated GPU (forget the specs) and I think thats all. [/COLOR]

The original line was something like this: ```
 [COLOR=Teal]quite splash nomodest video=uvesofb:mode_option=1600x1200-24(*comma)mtrr=3 scroll=ywarp[/COLOR] 
```How are there "many" different grub cnfg files? :wink:
Ahhh.... look what you wrote down... typo- should have been "nomoseset" not "[COLOR=Red]nomodest[/COLOR]"  If it was "nomodeset". then is your video nvidia?  That's a common switch from that type of video chipset.  [FONT=monospace]"[/FONT]uvesafb" is a kms switch to start a generic driver that works with video cards that have a Video BIOS compliant with VBE 2.0.  The rest is config options for that driver-- but it should have been in this format:
```
[FONT=monospace]
[/FONT]video=uvesafb:16600x1200-24,mtrr:3,ywrap

```(Notice you typo'ed on the driver name also) But if you "were" using that module for graphics and lost it after an upgrade... 

Look at this:
> 
Configuration 
 ---------------- 
 uvesafb can be compiled either as a module, or directly into the kernel. 
 In both cases it supports the same set of configuration options, which 
are either given on the kernel command line or as module parameters, e.g.: 

 video=uvesafb:1024x768-32,mtrr:3,ywrap (compiled into the kernel) 

 # modprobe uvesafb mode_option=1024x768-32 mtrr=3 scroll=ywrap  (module)
So that brings up whether an update replaced the Linux kernel and when it did, it left out what was previously added for that driver module...(?)  Another possibility may be that "that" version of "uvesafb" may have a problem with an update... As the only dicumentation I can find of that driver is from gentoo linux about 3 or 54 years ago... not  any other linux distro.
 
Yes, knowing what video chipset would help with this to figure out what drivers are having problems, what kind of configuration it should have versus what it has changed to...  If you could get to a terminal or text console, even from a LiveCD...
```

sudo hwinfo --framebuffer
lspci -nn | grep VGA

```How many grub config files?  Offhand I can think of 6 files that grub uses to make the 7th file- grub.cfg.  If some of these files, it passed variables and parameters to the kernel and further on to Xorg.  The kernel uses different config files to load modules during it's boot.  Xorg uses a main xorg.conf file and compensates with various other .xprofile and configuration files to display the graphics and whatever desktop the user is using...

Enough?  Or too much info?  Basically it all happens in layers that is supposed to talk with each other and work together.  Not always, but that's the goal!

---

### Post by MAFoElffen on 2011-07-12
What I forgot to say was, if it was compiled into the kernel, like your kernel boot line switches implied (even though it had a few syntax errors)... then you should be able to boot off the previous kernel version.  To boot off the current kernel we could check to see if it is in the current kernel by adding the switches back to your kernel boot line, booting to a text console and doing 
```

dmesg | grep uvesafb

```to see if it is present.

If not, then you could either reinstall this Vesa derivative driver or another driver. Knowing what video chipset you have, can help decide with that.  There's a lot of drivers out since that one was released.

---

### Post by Neoxhadowespio on 2011-07-13
Sorry for the lat reply. I was kinda busy...
Anyway I have rewritten the lines of code and I will try it soon. But "16600x1200"? 
That doesn't look right. Also I think Arch has some documentation for the driver as well. I am a bit lost on the update and kernel part. Also is it normal for the older versions of the linux kernel to remain after an update?

---

### Post by Neoxhadowespio on 2011-07-14
Uggh! I've tried almost all I could think of for grub line. Isn't there a way for me to just "generate" new boot files? A handy application that creates boot files for you based on what runs on your PC? Maybe I could just download a new /boot folder and litterly replace the old one. I think its high time I just preform a reinstallation of Ubuntu Maverick. I have scattered packages, a half-installation of Natty, a locked user account and many questionable errors I would otherwise get later anyway. How do you suggest I access my data? Of course, unlike "certain" operating systems (*looks at Windows), Ubuntu encrypts your HDD. Can I somehow enter a root password and gain full access? Also, how can I backup things like theme configurations, tweaks, mods, stuff outside your home folder?

I'm will now preform a lengthy session of GoogieLookLook and ForumFindFind...

---

### Post by Neoxhadowespio on 2011-07-14
Yep. I'm going to preform a fresh install of Mint. From a LiveUSB I hope to backup all my data. I just hope that I won't be stuck with some "Boot Error" again. I have a new USB drive...

---

### Post by MAFoElffen on 2011-07-14
> **Neoxhadowespio said:**
> Sorry for the lat reply. I was kinda busy...
Anyway I have rewritten the lines of code and I will try it soon. But "[COLOR=Red]16600x1200[/COLOR]"? 
That doesn't look right. Also I think Arch has some documentation for the driver as well. I am a bit lost on the update and kernel part. Also is it normal for the older versions of the linux kernel to remain after an update?
My typo... You did say 1600x1200.

Have you gone through the troubleshooting flow chart in post 1 of this sticky?
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") 

I have asked you for some info on your video chipset a few times... to help you.  Without that info... its more of a guess.  The info I asked would help with coming up with a new kernel boot line.

Older versions of the Linux kernel?  Yes it is normal when there is a kernel update for the new kernel to be built, which older kernel to remain... The grub menu then gets rebuilt with the older versions of the kernel to reaim in the menu, with the current version ads the default meu item... 

So this problem is in Linux Mint 11?  Any other applicable info that you're leaving out here?  (Just jumped over to my LM 11 install to apply updates this morning.)

LOL... No matters.  The funny thing is that with the current changes and updates in grub, kernel and Xorg... All upstream changes... You're going to run into similar issues with any distro of Linux or Unix.

---

### Post by Neoxhadowespio on 2011-07-14
Oh yeah, sorry. The commands gave me many lines. In brief I have an ATI RADEON GPU. And a bunch of other resoultions it supports. But the highest my moniter supports is the one given (1680x1200 <???>). Also, what do you mean by the LM problems? Is this bad? I'm going to boot into Linux Mint LiveUSB now, I hope to see you soon.

---

### Post by MAFoElffen on 2011-07-14
> **Neoxhadowespio said:**
> Oh yeah, sorry. The commands gave me many lines. In brief I have an [COLOR=Teal]ATI RADEON GPU[/COLOR]. And a bunch of other resoultions it supports. But the highest my moniter supports is the one given (1680x1200 <???>). Also, what do you mean by the LM problems? Is this bad? I'm going to boot into Linux Mint LiveUSB now, I hope to see you soon.
There you go... Now we're getting somewhere!  Using at least the xorg driver for Radeon will give you a lot more that the uvesafb driver.  If you (even if booted from a LiveCD) and ran 
```

lspci -n | grep VGA

```It would tell us what model of Radeon card you had.

Even now that we know the basic type of video card you have, I can help you better.  For the kernel boot line, instead of using "nomodeset" as a kms switch, you should be using "radeon.mode=1" 

So the basic of your kernel boot line should be something like this:
```

linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro   [COLOR=Teal]quiet splash radeon.mode=1 vga=[/COLOR][COLOR=Red]xxx[/COLOR]

```This is an example with the kms switches in green... Now see where the red x's are in than. The command I gave you that returned all those resolutions(That you didn't post the reult back?)... Of all those resolution lines, at the start of the line of that had 1680x1200 (24bit)... there is a hex formatted number starting with 0x... You can take that number in hex format or convert it to decimal format and replace those x's with that number to tell the kernel to boot in that resolution and to pass that graphics resolution on to Xorg... To boot the graphics in that resolution.

To use the radeon driver, I need to know the model reported by the commnad above, so I don't waste your time steering you in the wrong direction.  If we're doing it right, we should do it right the first time.  Less frustrating that way.

If you just made those kernel line changes by themself, they should get you up booted in an Xsession with a basic default driver.... but it "can" get better than that.

---

### Post by Neoxhadowespio on 2011-07-15
Eheheh...sorry. The thing is I already installed Mint (and I am not a fan!). **Really now all I care about is getting my old data back.** Operating Systems can be configured and tweaked again and packages can be reinstalled but some things can never be the same again. Not that its deleted or anything. Far from it. The home folder is looking me in the eye... encrypted... and worse with one of those "Access your private data.desktop" things. How will I ever get around that? Once all this is done I'm going to carry my OS on a pendrive. I'm sorry for all the inconvenience I have caused you overall. :sad: On the bright side I have learned many things. :o

---

### Post by MAFoElffen on 2011-07-15
> **Neoxhadowespio said:**
> Eheheh...sorry. The thing is I already installed Mint (and I am not a fan!). **Really now all I care about is getting my old data back.** Operating Systems can be configured and tweaked again and packages can be reinstalled but some things can never be the same again. Not that its deleted or anything. Far from it. The home folder is looking me in the eye... encrypted... and worse with one of those "Access your private data.desktop" things. How will I ever get around that? Once all this is done I'm going to carry my OS on a pendrive. I'm sorry for all the inconvenience I have caused you overall. :sad: On the bright side I have learned many things. :o
No apologies are necessary at all!  In fact, if you look at my signature...

The changes I have suggested would work for you no matter if you had Linux Mint, Gentoo, Ubuntu, Fedora, CentOS, Mepis, Debian, openSUSE, Red Hat, KNOPPIX, Fusion, Arch... Etc. (Linux), OpenIndiana, Illuminos, Incenta, Nexenta, Schillix, Dragonfly, Etc... (Unix)

In fact for Linux Mint... Mint goes back and forth with it's distro being derived from Ubuntu and Debian (Which Ubuntu is derived from).  The suggestions I have given you are from the upstream resources of both those-- plus of Linux and Unix itself.  So yes, you can be helped by either applying those changes or just reinstalling [FONT=monospace]"[/FONT]uvesafb"-- (and applying the uvesafb changes to the kernel).

What do I have here on these boxes? Various Stable and Development releases of Windows, Linux and Unix... and a few more... Including [COLOR=Teal][COLOR=SeaGreen]**Linux Mint**[/COLOR][COLOR=Black].

As for your newly stated priority:
[/COLOR][/COLOR][Live CD method of opening a encrypted home directory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory")
[http://forums.linuxmint.com/viewtopic.php?f=18&t=75580&p=444580](http://forums.linuxmint.com/viewtopic.php?f=18&t=75580&p=444580)

---

### Post by Neoxhadowespio on 2011-07-16
I've tried it. It doesn't work. But I didn't use a LiveCD or LiveUSB. Also I installed Ubuntu 10.10 on a pendrive. Its missing Gnome and the installation itself is a little more that a gigabyte. Now how can a get Gnome and everything needed to run it? I'm not certain but I believe you need x-server packages and things. How can I get it all in one?

---

### Post by Neoxhadowespio on 2011-07-16
Never mind it is alright now (DE). Any other way to break through encryption?

---

### Post by Neoxhadowespio on 2011-07-17
(bump!)
Also anyone getting the "Boot Error" message when trying to use a LiveUSB? The funny thing is it was working a few days ago.

---

### Post by Neoxhadowespio on 2011-07-19
(bump!)
...Nobody? 
Actually as usual I have a number of questions so I might as well make a new thread.

---

