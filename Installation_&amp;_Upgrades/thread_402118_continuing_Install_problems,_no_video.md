---
title: "continuing Install problems, no video"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by genecaldwell on 2007-04-05
for more than a year now I have been having install problems as follows: no video when switching to the GUI towards the end of the install. Now I am by no means a skilled linux operator, however I have tried every single cheatcode trying to get the display to show something. This happens on literally every single computer I try to install to. not just one particular PC. I have tried to install using the safe mode video option, I have tried manual designation of video resolution, I have tried installing on computers with ATI cards, Nvidia cards, onboard video of sis video, but with out exception, when it switches to the GUI from text, the screen goes blank( actually it goes black) and I get a message from my LCD panel( its a dell, and brand new, well, 6 months old) stating that it cannot display this video resolution, please change your input to 1600x1200x60hz. I had thought that it may have been an issue with my old LCD, I had been using it for over 5 years, and decided that it might have some issues, so I bought a new flat panel from dell. but the issues continue. my point being that I have been unable to install any UBUNTU based distro for a very long while now due to the lack of any kind of video display after the start of install. 

"alternate CD's" do not work either, the refresh rate gets set to something my Flat panel cannot display and I get stopped dead in my tracks with no out put whatsoever. And now that I think about it the issue seems to have started when the "alternate CD" first began to be used, I think "alternate CD" were offered due to the change in the Live CD's. "alternate CD" install just fine until re-boot and when GUI starts, the screen just goes black., Live CD never display the GUI.

I do not think this is an ubuntu issue, I believe the problem started with the release of one of the kernal updates some 6 months back (with 6.06 I believe) or maybe the X.org updates.  I have never been able to install 6.10 on any computer, ATI, Nvidia, old Nvidia card or new Nvidia card ( Geforce FX 5500, Geforce FX 5700ultra, Geforce 6800GT OC, ATI x700 pro, ATI X850 Pro) . What is odd is that I have had no problems going back to pre 6.06 distros. I just cannot figure out how to get the refresh rate to work. I am positively convinced that its the refresh rate that is causing the error message I am getting on my display.

I have tried Ubuntu, Xubuntu, LinuxMint, and Fluxubuntu and some non ubuntu based distro's. no video output for any distro when the GUI is switched to during install. I have also tried to run the live CD's from most Ubuntu based distro's and the same issues occures, the boot starts, but then when the GUI is switched to, it goes blank, no matter what display setting I select from the startup options. Since I really believe that this is a refresh problem because I have tried all the different display resolutions and none work, that only leaves refresh rate, but there is no refresh rate of 60 hz to select from. I have also tried to just add the 60hz at the end of the resolution, 1600x1200x8/16/24/32 @60hz, but nothing seems to work. So how do I **force** the refresh rate to be 60hz on different distro's ?

I would have thought that many people are having this problem and that it would be fixed by now but I have got tired of waiting. why does pre 6.06 work, but nothing after that work ? One note: I have no issues at all when I install the very same distro in VMware. I have never even had issues with the beta's installed in VMware. So I know that the CD's I D/L and burn are ok.

and a second issue on OLDER computers only, the keyboard goes crazy on older computers, and that started happening at about the same time as the video issue problems. the specific issue is that typing just one letter results in dozens and dozens of that key being repeated, install goes fine, the problem starts after all the latestst updates are down loaded and installed and I reboot. just trying to login: the password entry just goes crazy and repeats each and every letter an unknown number of times preventing me from logging in. I first notice this when I first started trying Xubuntu, all the beta's seemed to work fine, then when the release came out, the problem started with the updates that followed. I tried all the different cheat options I found on the different forums, (NOAPIC, NOLAPIC, etc) but nothing seems to work. I was forced to go to DSL, and had no problems at all, even today with all the latest updates, DSL installs and runs just fine with no keyboard problems, nor any video issues on the target older computer. I also discovered that there is an older ubuntu distro called BeaFanatiX that is based on Ubuntu 5.04(hoary?) I believe, it installed just fine and I have had no issues at all using that distro. However no new Xubuntu will install without keyboard problems.

None of my computer would be considered a newer computer, but they are all in very very good condition, and all run windows just fine, and all run the older versions of most distro's just fine if they are pre-6.06 time period kernels ( I think that puts it at 2.6.6 or close to it.) I should note that the current DSL kernel of 2.4.x and later works just fine,  but none of the new 2.6.X after 2.6.6 seem to work.

In short, testing in VMWare does not do me any good, the distros always seem to run just fine in VMWare, the video problem only appear when actually running on a real computer. the keyboard problems only occur on older computers and first showed up with the last beta of Xubuntu when it first came out, the early beta's of Xubuntu( I'm talking about the time frame here and what kernel would have been used) all ran just fine, then the kernel was updated and broke everything.

One last note, the latest release of Parsix runs just fine on the target computers as well as DSL. So I am pretty darn sure I have no problems with my computers. and I can run Win2k just fine on all of them, I can even go back to earlier releases of Ubuntu and Ubuntu based distros and they run just fine. How do I get video to work right ? how do I get keyboards to work right on older computers with newer releases of Ubuntu based distros ? and am I the only person that continues to have these two issues ? One last note: I don't really care for the other distro's so I can't say if they have the same problem, I stick strictly to Ubuntu based Distro's other than what I stated here.

---

### Post by mssever on 2007-04-05
The refresh rate is set in /etc/X11/xorg.conf in the Monitor section. It's a bit opaque, so I suggest reading ```
man xorg.conf
``` and looking up your monitor's technical documentation. You can edit xorg.conf from recovery mode:
```
cd /etc/X11/
cp xorg.conf xorg.conf.backup
nano xorg.conf #change settings here; maybe comment out all resolutions except your monitor's native resolution
su - your_username
xtartx
```If X doesn't start properly, look for error messages in ~your_username/.xsession-errors

To reboot, type ```
exit
reboot
```PS: The only thing I can think of with your keyboard is to toggle its connection between USB and PS/2 (or try a different keyboard).

---

### Post by genecaldwell on 2007-04-05
> **mssever said:**
> The refresh rate is set in /etc/X11/xorg.conf in the Monitor section. It's a bit opaque, so I suggest reading ```
man xorg.conf
``` and looking up your monitor's technical documentation. You can edit xorg.conf from recovery mode:
```
cd /etc/X11/
cp xorg.conf xorg.conf.backup
nano xorg.conf #change settings here; maybe comment out all resolutions except your monitor's native resolution
su - your_username
xtartx
```If X doesn't start properly, look for error messages in ~your_username/.xsession-errors

To reboot, type ```
exit
reboot
```PS: The only thing I can think of with your keyboard is to toggle its connection between USB and PS/2 (or try a different keyboard).

First, I am not having a **resolution** problem, I am having a **refresh rate** problem.

**Would SOMEONE tell me how I am supposed to edit anything when I have no display output ??????** and how do I edit this file when it lives on the CDrom ? also, please explain how I edit anything thats on the CDROM in the first place ? This is an install problem. I have read all the responses that the linux experts have left for this install problem - and tried them as best I could, and what they dont seem to get is that there is nothing to edit until the install is complete, but if you can't even get the Live CD to produce a display once the GUI starts, then the live CD is worthless for installing. the alternate install CD does not work either, as other people had left posts about this also. 

The assumption that I need to look anything up about my monitor is frustrating, I don't need to look anything up about it, I know all my computer components forwards and backwards on every computer I own - and I own about a dozen from much older computers to newer computers. I know everything about them and how they need to be configured for proper operation. In this case with my display, the correct display output needs to be 1600x1200@60hz. because that is the native display of my flat panel. I should also re-inforce, this problem is happening on all my computers, not just one computer. I would also point out that other people are in fact reporting the very same problem with display issues.

The problem is that at the completion of the install(alternate install CD), after you reboot the computer, the display does not produce output, so if you cannot see anything due to the monitor error stating that the requested output refresh rate is not valid, I can't report error numbers, I can't report anything other than no video output. I have tried booting to command prompt, I have edited the file you stated "xorg.conf" and this did not fix anything, it feels as if its ignoring everything except the resolution, refresh rate just feels like it is hard coded. one important thing, I am not a linux expert, I am clueless. and much of what is written in response to many posts I have read about this problem are just simply over a newbies head. most of what is written in man files are not helpful as they assume an understanding of file layout and directory structure. I just want to get the install completed and THEN start learning about Linux. One other thing, If I cannot get any output display produced, how would you suggest that I read the man xorg.conf document you suggest as the first thing in this reply ? I have no clue or understanding about command prompts in linux. I feel that I have done real good in the past editing and changing that file to properly set resolution when the GUI would not show the correct resolution 

as for toggling the connection between USB and PS/2...humm, how do I do that ? its a PS/2 keyboard, and there is nothing wrong with it. it works just fine with the earlier versions of Ubuntu, 5.04, 5.10, 6.04, 6.06LTS  all work just fine with this keyboard, so why would I think I have a hardware problem with my keyboard ? its 6.10 and later that I'm having Keyboard/video problems with. WHY can't we get a confirmation about the display setting durning install that will be used including the refresh rate along with over ride options when they are wrong ?

---

### Post by mssever on 2007-04-05
When it comes to your keyboard, that was just a guess. The problem must be either  hardware-related (not necessarily bad hardware, maybe just a bad interaction with Ubuntu) or some (accidental) mis-configuration; otherwise, everybody would be having keyboard problems, and such problems are rare.

In my previous post, I asked you to boot into recovery mode for the precise reason that you don't have graphical output from X. Of course, if you can't install from the alternate install CD, you're pretty much sunk. If you can install from that CD, you should be able to fix your problems from recovery mode.

When it comes to the refresh rate, Xorg doesn't use rates such as 60Hz. It uses separate ranges for horizontal refresh and vertical refresh. It's silly, I know, but that's the way X works. Those ranges were what I was referring to finding in your monitor's docs. The refresh rate is the most difficult part of configuring X.

Also, it appears to me from your posts that while you're using multiple computers, you're only dealing with a single monitor. Is that correct?

---

### Post by genecaldwell on 2007-04-05
you are correct about the display, I have just one. however I started having this issue a while back and was just waiting for someone to get around to reporting and fixing this problem, I got tired of waiting, so I posted. when the issue first came up many months back, I was using an older different display that was about 5 years old and thought it might be related to that so I bought a new one just a few months back, but continued to have the very same problem.

I should point out that I do in fact have Ubuntu 6.10 running on another computer, however I seem to remember that I got it install by using a completely different video card from what I have been using. I pulled an old matrox card out, tried installing with that and it worked, then I switched back to nvidia card and re-configured the display using the noted command in the xorg.conf file and it worked. This seems to imply that BOTH ATI as well as Nvidia have issues with all the newer releases of Ubuntu when installing. ( I literally have about a dozen computers all having some version of ATI or Nvidia cards.) and yet I did not have video problems at all  prior to 6.06.

Once again, I must point out that I have just gone back to older versions of Ubuntu and do not have keyboard problems, nor do I have video problems. I should also point out that I am having these problems with all the Ubuntu based distro's, LinuxMint, FluxUbuntu, Xubuntu, etc....., however as I said, only the new stuff, this STRONGLY points to code in the OS, NOT to hardware issues. And that can be solved by adding a confirmation about what display setting will be used. Please note again that I searched and found other people with the same video issue I am having, so there again, it suggests that its not my hardware. While I agree that other people would have the same keyboard problems I am having, I am not convince they are trying to install Xubuntu on an older system, like I am. I can duplicate this issue at will( with Xubuntu ), and have finally found an Ubuntu based distro called BeaFanatix that is based on Ubuntu 5.04 and it runs just fine, this once again points to the coding, not the hardware. I might add again that DSL (all versions) run flawlessly on this target computer.

as far as the alternate install CD is concerned,  I can no longer use that either because I am have the same exact problem that others are now reporting using that, I am getting a buffer I/O error on HDC as has been previously reported here([http://ubuntuforums.org/showthread.php?t=402081)](http://ubuntuforums.org/showthread.php?t=402081)). The more I think about it, all the problems I am having started when the switch was made to the new installer. there used to be only one CD offered, this was 5.10 I believe, and with the intro of 6.06 and the alternate CD install, the problems started. I have not had a single problem installing into VMWare however.

I really appreciate all efforts of help, please remember that I am NOT a skilled Linux user, however I am a very skilled windows user and all my hardware expertise is derived from windows. I can build a computer with my eyes closed, its that easy for me, however I have discovered what works under windows sometimes does not work under Linux(hardware configuration wise) I have discovered some CDrom's just will not work with Linux, but function perfectly under windows. So I am taking that into account, and going through many trials. What I just don't get is how can it( the hardware) work for 5.10, but fail with 6.10 using the very same hardware if its not a software failure ?

---

### Post by mssever on 2007-04-05
My previous theory was that your monitor couldn't handle the signal from the video card.  However, since you've used another monitor with the same results, that calls my theory into question.

Have you tried using different video drivers from the default? There should be plenty of threads here on how to do that if you haven't tried it already. And since most people around here give commands to type at a terminal, you can do the same thing from recovery mode, most likely. Just leave off the sudo since in recovery mode you're already root.

Otherwise, let's try to get some error messages. Boot into recovery mode and type the following commands (The comments explain what the commands do):
```
su - your_username #switches from running as root to running as your user
cd #make sure you're in your home directory
startx #attempt to start Xorg
```When your display goes haywire, hit Ctrl+Alt+Backspace to kill X. If X doesn't die and give you back a command prompt, you'll have to reboot into recovery mode again and repeat the first two commands above.

Now, look at .xsession-errors:
```
less .xsession-errors
```Post the contents of that file, enclosed in [code] tags.

If you aren't able to take these steps, then it will be very difficult to diagnose and fix your problem. Given that you've tried several monitors, I don't think that the refresh rate is your primary problem.

---

### Post by mssever on 2007-04-05
Didn't catch your last edit. Have you filed bug(s) on launchpad.net? It sounds like something that changed between breezy and dapper doesn't like your hardware. Regressions are annoying.


Here's a wild idea... What happens if you install Breezy, then upgrade to Dapper, then upgrade to Edgy?

---

### Post by genecaldwell on 2007-04-05
> **mssever said:**
> Didn't catch your last edit. Have you filed bug(s) on launchpad.net? It sounds like something that changed between breezy and dapper doesn't like your hardware. Regressions are annoying.


Here's a wild idea... What happens if you install Breezy, then upgrade to Dapper, then upgrade to Edgy?

ok, your mind works just like mine, I try to think outside the box to solve problems. ( I have infact done lots of beta testing for many windows vendors as well as for MSFT, always trying workarounds) I did in fact try the upgrade route from a properly installed and functioning release, however I have not had a single case where upgrading worked when going from one Ubuntu release to the next. Sorry, thats just my experience, however I believe thats because I switch to Nvidai-glx drivers as quickly as the system is up and running and it looks like the GLX drivers are casing the crash and burn every time. But I am at my limits of Linux understanding here, I have never been able to uninstall them. 

I have a computer running 6.10 now, it has the GLX drivers installed, I run Google earth, VMWare Player, celistia, and one other, and I know for a fact that if I try to upgrade it, it will become hosed, and I will not be able to re-install Ubuntu because of all the other problems I am discovering,  video,  and this one ([http://ubuntuforums.org/showthread.php?t=402081](http://ubuntuforums.org/showthread.php?t=402081)) which I am also having now. 
I have tried the upgrade path in VMWare and it fails there, so I have no confidence at all that an upgrade would work on the 6.10 machine.

Other people have in fact reported the problems here that I am experiencing, however I am doing lots more trouble shooting trying different video cards, different release versions of Ubuntu, and trying different distros altogather, DSL works flawlessly(all versions) Parsix does too, as a matter of fact ALL distros that use kernel 2.4.x run fine, video, keyboard etc. It really looks like everything after 2.6.6 or very close to that seem to fail. I really have done lots of testing and everything goes back to the very early days of the Xubuntu project, the first few betas works, then started failing, along with the same versions of Ubuntu at that time, as well as all the other distros that are based on Ubuntu.

---

### Post by mssever on 2007-04-05
It really sounds to me like this discussion should be taking place on Launchpad as a bug. You've done more testing than I could ever hope to do (especially since I've never encountered the kinds of problems you're experiencing), and very few developers frequent these forums. I think that you're definitely fighting some bug(s) somewhere in Xorg or the kernel.

I wish I knew a workaround, but I don't.

---

### Post by genecaldwell on 2007-04-05
> **mssever said:**
> It really sounds to me like this discussion should be taking place on Launchpad as a bug. You've done more testing than I could ever hope to do (especially since I've never encountered the kinds of problems you're experiencing), and very few developers frequent these forums. I think that you're definitely fighting some bug(s) somewhere in Xorg or the kernel.

I wish I knew a workaround, but I don't.

I'm sorry, I have no clue what launchpad is. I thought posting here would get some sort of bug tracking going ? I got here by selecting support from the links above, I see no other link that looks like a support or bug tracking link....

---

### Post by mssever on 2007-04-05
> **genecaldwell said:**
> I'm sorry, I have no clue what launchpad is. I thought posting here would get some sort of bug tracking going ? I got here by selecting support from the links above, I see no other link that looks like a support or bug tracking link....

Sorry. launchpad.net is where [kx]ubuntu bugs are tracked. see [https://bugs.launchpad.net](https://bugs.launchpad.net). I should have explained that more. These forums are for technical support.

---

### Post by genecaldwell on 2007-04-05
Oh yea, one last thing, I have noticed when I install any Ubuntu based distro in VMWare,  it installs just fine, and I check the refresh rate that gets configured there and its always set to 46hz. If that same value is being used when I install on an actual computer , then that is the problem, and is what I have suspected all along. My LCD will only work with a refresh rate of 60 hz at a mnimum, and 75hz at the max. I have tried to change the xorg.conf if I manage to get the alternate install to complete, but nothing ever works.

---

### Post by mssever on 2007-04-05
Hmm... The LCD on my laptop is quite particular, and I'm pretty sure that it runs at 60Hz under Ubuntu. (I've never had to mess with the refresh rate on that box.) I can't test it now because I have a dead power supply.

---

### Post by genecaldwell on 2007-04-05
as far as I'm aware, all LCD's are designed to run at 60hz. I did quite a bit of reading when I was researching what would be the best new flat panel to buy. I came to the conclusion that I did not need to consider the refresh rate since they all appeared to be limited at a hardware level due to technology to 60hz. notebooks are the same as flat panel displays for workstations, I never read one article that talked about anything other than 60 hz.

---

### Post by mssever on 2007-04-05
In that case, we can be sure that my laptop is running at 60Hz, out of the box. But yours might or might not be. Weird.

---

### Post by gewilli on 2007-04-10
I want to join in here to state that I'm having a similar problem with UBUNTU and KUBUNTU install of the latest distros. 64bit.

However, I am using a CRT monitor, not LCD. I don't get a black screen I get a messed up screen. That is lots of colors all messed up in a somewhat geometric pattern. Since this is during the install process I can't change anything. 

My monitor is a e-Geforce 6800GS. NVIDIA.

BTW I get a similar problem with SUSE 10.2.

---

### Post by gpearston on 2007-04-12
I am running in to the same issue when attempting to install UBUNTU latest distro's of the 64bit flavor.  Using a GeForce 6800GS and NVIDIA.  

I can install the same distro (using the same CD as above) on a Toshiba laptop so it would appear the assumption of the locked 60Hz for a laptop is correct.

---

### Post by captain_frostbyte on 2007-05-05
I'm a little late to this party, buy i'm having the same issue with 3 out of 4 pc's  i am currently trying to set up for diffrent reasons. using diffrent video cards, (ati, nvidia, and SIS chipsets) and i run into the problem with almost any Distro i try, I have gone back to 6.06 on the one i need to have running.

Has there been any more news on fixing the base install refresh rate?

---

### Post by chris.olsen on 2007-05-05
Sounds like I am having the exact same problem.  I have a dell 6400 and had all the instructions printed out on how to handle the ati issues, installed, booted up, and all I get is a black screen.  

Funny how it installed perfectly on a old athalon 1200 computer, but doesn't work at all on my laptop.  I really don't understand how this got released in it's current state.  Things like this make the Apple ads all the more appealing.

---

