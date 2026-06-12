---
title: "Upgraded to 8.10, blank screen shows after login."
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by larryn28 on 2008-10-31
hello,

i just upgraded from 8.04 to 8.10, after restarting the computer, once i enter my username & password, the screen just goes to a blank brown page & stays that way permanently. does anyone know what i can do?

---

### Post by jema on 2008-10-31
Just posted exactly the same thread.

So please if you find an answer share it.

---

### Post by larryn28 on 2008-10-31
will do, but so far no haven't seemed to find any help.

---

### Post by Nubsy on 2008-10-31
I have the same problem. Right now I have that comp in the failsafe terminal, but nothing has worked... 

Hopefully someone has an answer. =/

EDIT:
Oh. Oh joy. Just exited the terminal and now I have just a black screen. Still makes the drum-beat noise when you get to the log in screen, but just a black screen. I really regret upgrading now...

EDIT2: Okay, now it goes to the login screen fine. That might just have been a one time thing. (I hope) But still no log in...

---

### Post by shipitkthx on 2008-10-31
> **Nubsy said:**
> I have the same problem. Right now I have that comp in the failsafe terminal, but nothing has worked... 

Hopefully someone has an answer. =/

EDIT:
Oh. Oh joy. Just exited the terminal and now I have just a black screen. Still makes the drum-beat noise when you get to the log in screen, but just a black screen. I really regret upgrading now...

I'm having the exact same issue as everyone. Now after trying to fix it i've lost the ability to use my mouse...why oh why did I upgrade.

---

### Post by mactece on 2008-10-31
I've got the same thing but I can log in successfully using a Gnome session from the options list in the bottom left at the login screen. From there I've been able to run everything as normal except for the compiz effects. In fact I've switched the effects off altogether.

---

### Post by Nubsy on 2008-10-31
I have all use of my mouse and keyboard.

I've tried failsafe gnome, but nada... I'll try it again, I guess...

---

### Post by jema on 2008-10-31
Doesn't sound like the same thing. All I am getting is a blank screen. Having change to a different xorg.conf the blank screen is now black which ain't a lot of progress.

The one thing I can access via the keyboard is the screenshot dialog.

---

### Post by larryn28 on 2008-10-31
i can't even try logging in a gnome session at options, because the screen resolution isn't showing the options in the lower left corner anymore.

---

### Post by shipitkthx on 2008-10-31
I can get gnome to load, however I can't get a network connection once I'm there.

---

### Post by jema on 2008-10-31
Please don't post stuff irrelevant to the problem being reported. It sounds like you need another thread.

---

### Post by shipitkthx on 2008-10-31
> **jema said:**
> Please don't post stuff irrelevant to the problem being reported. It sounds like you need another thread.

I'm having the exact same problem as you, and trying to work around it.

---

### Post by kamishki on 2008-10-31
Lets add one more person with the "blank screen after login" problem.  Sad that I have the issue but glad I am not alone.


Using Thinkpad X30 with 1G RAM...
Worked quite well on 8.04 and I just finished the 8.10 upgrade.

all GUI options end up with blank screen and lockup...
(Xclient script, Gnome, Failsafe)

Failsafe terminal brings comes up but that is it.

:(

---

### Post by Spooky666 on 2008-10-31
How about posting what type of hardware your using.... 

Laptop? Make/Model

Desktop? Graphics card? 

Might help....

---

### Post by jema on 2008-10-31
If i do a "uname -a" my kernel is showing 2.6.24-16 :( I assume that is the Hardy kernel and may explain a lot.

---

### Post by kamishki on 2008-10-31
New Info...

what does this tell you
if I boot,  login and right away switch to another terminal.

I can log in and operate on the terminal.
While I am doing so I can see the disk grinding (as Gnome loads).

When I switch back to the X terminal I can see the prompt for a password for the certificate program,  but there are no bars on the top and bottom.  In about a second the window blanks out and everything locks out.

---

### Post by jerrylamos on 2008-10-31
Might be the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

---

### Post by Nubsy on 2008-10-31
OH SNAP! That worked! :D

So yeah, if your system hangs after logging in, Do the fix Jerry posted.

Also, if you're at the login screen, you can also do this in the fail-safe terminal. Um Exciting.

---

### Post by ulrichard on 2008-10-31
I had the blank screen not the black screen problem after upgrading my hp2133 from 8.04 to 8.10. 
The solution was as simple as choosing a regular gnome session at the login screen. It had somehow lost that default.

---

### Post by larryn28 on 2008-10-31
tried to do the jerry fix, didn't solve anything for me, still getting the blank brown screen. my screen resolution is also defaulting to a size that isn't allowing me options at the log-in screen. any suggestions as to what i can do? would truly appreciate it.

thanks

---

### Post by kamishki on 2008-10-31
You can try a slightly different approach that may help,

If you are not locked hit ctrl-alt F1 to get to a console

Login

try sudo apt-get autoremove compiz

answer Y when prompted

Go back to x by hitting ctrl-alt F7 
hit alt-ctrl-backspace to restart X

Good luck

---

### Post by rswheaton on 2008-11-01
> **jerrylamos said:**
> Might be the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

THANK YOU!!!  Your fixed resolved a Dell Optiplex GX260 w/ Intel 82845G/GL

---

### Post by gulch on 2008-11-01
thanks a lot, I have the same problem,
and livecd can not root system

---

### Post by gandalf2000 on 2008-11-01
Thank you, jerrylamos, your workaround fixed my problem.

---

### Post by davehouston on 2008-11-01
Thanks - this fixed my Dell Dimension 2400 desktop, too.

---

### Post by gjoellee on 2008-11-01
Have you tried booting with an other kernel? If that does not work there might be an issue with xorg. Try run a xfix then, read more about xfix here: [http://kshoster.net/node/18](http://kshoster.net/node/18)

---

### Post by Irishpolyglot on 2008-11-01
Good suggestions. I tried them and still didn't solve the issue and the blue screen continues... Since it's likely not the same problem as people here I started a [new thread]("http://ubuntuforums.org/showthread.php?t=966503")
The xfix solution didn't help either.

---

### Post by edwith on 2008-11-01
I got to "Running local boot scripts (/etc/rc.local) then cursor

---

### Post by Irishpolyglot on 2008-11-01
I've found a temporary work around!! :)

When on the log-in screen (or if it logs in automatically, press CTRL+Alt+Backspace) click "Options" then "Failsafe Gnome" and then log in as normal and it should work!

When inside I see that it needs to update the NVIDIA Hardware Drivers. I tried to select this option, but the update goes to 0% and does not go beyond it, then the update screen disappears. It's a separate issue I'll solve tomorrow, and the update may work directly for you. For the moment I have full access to the OS and everything else seems to be working as long as I'm in Failsafe Gnome! :)

---

### Post by iluvatar85 on 2008-11-01
> **mactece said:**
> I've got the same thing but I can log in successfully using a Gnome session from the options list in the bottom left at the login screen. From there I've been able to run everything as normal except for the compiz effects. In fact I've switched the effects off altogether.Same problem, same solution!
After the login compiz was disabled, so I opened a terminal and launched it (simply run 'compiz'). Now everything it's ok.

---

### Post by Arabiest on 2008-11-01
Thank u gents. I am happy that I am not alone whom having this strange problem. We were having good impression that 8.10 well be our solutions to mots of our problems.

I was optimistic that Ubuntu team will consider all its members findings in its previous bugs and avoid it in each new release and I am still hoping that they are.

I seek you kind help to solve my problem...I did follow all steps mentioned here and no luck.

my pc is:
Technical Specifications for LifeBook T4210
Intel® Centrino® Duo Mobile Technology
Intel® Core™ Duo Processor T2400 (1.83GHz, 2MB L2 Cache, 667MHz FSB) 
Intel® PRO / Wireless 3945ABG network connection 
Intel® 945GM Express Chipset 
12.1" XGA TFT, 1024 x 768 pixels, transmissive with active digitiser

---

### Post by ByteWyse on 2008-11-01
> **jerrylamos said:**
> Might be the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry
I had the same problem and your solution fixed it, thanks for posting it.

---

### Post by mingle on 2008-11-02
Hi,

I have the same issue on a HP Compaq Evo 510 desktop, which has a 64MB Intel 82845G GFX chipset.

During the install of 8.10 from CD, the screen resolution that the installer selected was very strange (1152 x 864), which caused my LCD screen (HP L1530) to report "signal out of range", but luckily the display was still visible!

After the install completed, I had the same issue of a blank/black screen when I'd expect to see the login screen.

I found this thread (after a lot of searching!) and used the solution suggested by jerrylamos and that seemed to work - I could get to a desktop and then used the usual system>preferences>screen resolution util to set the screen res to something my monitor could handle (1024x768).

Strangely the login screen resolution is still 1152 x 864, but the Ubuntu desktop is fine at 1024x768. I suspect that there are more than a few bugs/issues with the Intel 82845G drivers.

If anyone would know how to change the resolution of the login screen, that would also be helpful!

Interestingly I have NO problems with the same install process on a near-identical machine with an Intel 82865G GFX chipset... 

Cheers,

Mike.

---

### Post by Merlin_ua on 2008-11-02
> **jerrylamos said:**
> Might be the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

How do I boot in rescue mode? I though I should select it in GRUB, but if I press ESC on startup I see LILO. There is only one option there (which is Linux) and I don't know how to make it load in the rescue mode.

Ubuntu 8.10 i386 Desktop, installed from alternate CD.

---

### Post by jd24601 on 2008-11-02
Hi everyone.  I had the same issue with a Dimension 2350 and tried the fix that Jerry recommended.  Although it allowed me to get to the GUI after the recovery, upon reboot, it just went to a black screen. This was a spare machine so I downloaded and installed 8.04LTS and it worked with no issues. 

I would much rather have used the 8.1 but am just happy to get this older machine loaded with any version.  If anyone else experiences the same black screen issue after removing compiz, I'd sure like to know....

Thanks.

JD

---

### Post by lhmperth on 2008-11-03
Well, I am glad I am not the only person with this problem either!

Now, pardon the very very silly question, but how do I boot in rescue mode? 

At present when I boot up it asks for my login name and password and then I get a blank orange/brown screen.  Rescue me please!

---

### Post by Partyboi2 on 2008-11-03
> lhmperth              **Re: Upgraded to 8.10, blank screen shows after login.**
         Well, I am glad I am not the only person with this problem either!

Now, pardon the very very silly question, but how do I boot in rescue mode? 

At present when I boot up it asks for my login name and password and then I get a blank orange/brown screen.  Rescue me please!     When you boot ubuntu you should see grub loading... press ESC this will take you to grub menu  then choose recovery mode.

---

### Post by amaiko on 2008-11-03
restart Ubuntu and select the 2nd choise "safemode" them select "root shell" then remove Compiz
sudo apt-get remove compiz compiz-core

---

### Post by TusharG on 2008-11-04
You can follow the steps from my blog page. Only follow the steps if you are using Intel 845 mother boards. For rest of the video cards I've not tried.

---

### Post by kevdog on 2008-11-05
Where is this bug actually documented?

---

### Post by francais on 2008-11-05
> **TusharG said:**
> You can follow the steps from my blog page. Only follow the steps if you are using Intel 845 mother boards. For rest of the video cards I've not tried.
Just a great big thank you to TusharG for his blog on fixing 8.10 blank screen after log on.  Had the blank screen problem on Intel Celeron after upgrading.  As relatively new Ubuntu user, followed TusharG's blog instructions to the letter and was able to finally enjoy the new distro.  [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

### Post by tez1982 on 2008-11-05
I'm runnning Mythbuntu on a Shuttle system with a Nvidia GEForce 5200.

I have the same problem in the system seems to load, gets to the point where it would auto login and just sits on a blank screen.

I can Ctrl+Alt+F1 and access terminal, I've tried removing compiz and that makes no difference?

Any suggestions?

---

### Post by tez1982 on 2008-11-05
I'm getting closer

Got the system part working by editing xorg.conf with the Busid of the card and then setting the driver to Nvidia

However the restricted driver manager isn't recorgnising the card so I can't install the 173 drivers??

---

### Post by mrlwalsh on 2008-11-05
I have a similar problem with one of my laptops

Averatec 3260
Via/S3G UniChrome Pro IGP adapter

The black screen is not permanent, but the initial boot cycles three times and then states that install can not determine the correct adapter.  I get a low graphics screen with options to procees normally, reconfigure, or troubleshoot.  I tried all three without success.

I removed compiz as suggested in this thread with no luck.

I'd manually configure but I don't know what to edit via the command line or how to do it.

I'm using wubi to install 8.10.  I had 8.04 working without a hitch on this laptop.  Neither the upgrade not a new wubi install worked with 8.10.

I'd appreciate suggestions.  Thanks

---

### Post by azray on 2008-11-06
I had the same problem and found a thread that told me to remove compiz and compiz-core. Voila! I am sorry I did not write down the actual code for the terminal session. Search for removing compiz might help...

---

### Post by jalvarez1029 on 2008-12-01
Not sure if this is the same problem, but here goes. I also upgraded and on my first login atempt, went to the blank brown (not black if that matters) screen. I restarted my computer and changed first to a gnome failsafe session, then to a normal gnome session and succefully logged in, but when I tried to go back to the xclient session that I had previously used I got the same blank screen. I get that same screen whenever I try to switch to the guest session in 8.10 if that gives any clues. Not an urgen tproblem since I do have a way to log in, but would be nice to know what's going on. Thanks for any help.

---

### Post by dotdot on 2009-01-24
thanks jerry - worked for me - tis taken me a while to find this thread.

dell x200
8.10
all now working cool

..cheers

..

---

### Post by JF_Sly on 2009-03-26
> **ulrichard said:**
> I had the blank screen not the black screen problem after upgrading my hp2133 from 8.04 to 8.10. 
The solution was as simple as choosing a regular gnome session at the login screen. It had somehow lost that default.

I'm New to Ubuntu - How do I select the regular gnome session when I get to the login screen?

---

### Post by ocribin on 2009-03-26
Your workaround has worked for me!! Thanks!! But should somebody inform the gurus, so that this can be remedied for other non-programmers like me (I was one for years, but that was a long time ago, and things have moved on)

---

### Post by rahul_bhise on 2009-04-09
> **jerrylamos said:**
> Might be the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

thankyou this solved my problem

---

### Post by dmrx24 on 2009-05-05
Please Help, this is happening with 9.04 and seems to have been happening since ubuntu was released. What can I do?

---

