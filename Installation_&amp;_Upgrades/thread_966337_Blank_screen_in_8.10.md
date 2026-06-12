---
title: "Blank screen in 8.10"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by srikar on 2008-11-01
Live cd session(8.1) worked fine.But after installation I am getting a  blank screen(i mean after orange loading bar) and monitor turns off(monitor led blinks,as if its off)


I re-installed with different image,problem remains same.I experienced same problem with the beta release also.

I am unable to use this release 
my system specs:
p4,1gb ram,ATI onboard 200 series graphics accelerator .

---

### Post by smartchoo on 2008-11-01
I ever got the same problem with you.
I installed by using alternate-iso instead of desktop-iso.

Did you try it?

---

### Post by Snader on 2008-11-01
We seem to have the same problem. The startup looks normal, but when you expect the login-screen, you get an empty black screen.

If it is of any help, I used the alternate-iso.

System specs: P3 1200, 256 MB RAM, S3 Twister on-board videocard, 6.7 GB EXT3, 534 MB SWAP.

---

### Post by srikar on 2008-11-01
I will try alternate cd,and post back if it workss.

---

### Post by PendragonUK on 2008-11-01
You guys are not the only ones with this issue. If you look through this section of the forum there are quite a few, myself included.

From what I have read of other posts and my own experiences, it's down to the monitor not being detected correctly. When we all used CRT monitors the screen would be garbled. Now most have LCD screen they respond to the wrong type of signal by blacking out. 

I think what we need is the option to "Tell" the system what monitor we have.

---

### Post by gulch on 2008-11-01
apt-get remove compiz compiz-core

---

### Post by srikar on 2008-11-01
> You guys are not the only ones with this issue. If you look through this section of the forum there are quite a few, myself included.

From what I have read of other posts and my own experiences, it's down to the monitor not being detected correctly. When we all used CRT monitors the screen would be garbled. Now most have LCD screen they respond to the wrong type of signal by blacking out.

I think what we need is the option to "Tell" the system what monitor we have.
__________________

**So wat may be the fix ????????**

---

### Post by srikar on 2008-11-01
If da problem is wid monitor ,,,I think installing through alternate cd will not solve da problem , wat do u say???

---

### Post by gulch on 2008-11-01
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

[http://ubuntuforums.org/showthread.php?t=965478&page=2](http://ubuntuforums.org/showthread.php?t=965478&page=2)

please reference

---

### Post by Snader on 2008-11-01
Please note that we have the black screen *before* the login-screen, while the majority of threads is about a black screen after the login-screen. :)

The suggestion of PendragonUK looks plausible to me, but the idea needs to be worked out.

Also, I found some bugreports which look similar to our problems. Although I can't recall that I heard the drums while the screen was black. I'm unable to check it, because I'm back to 8.04 at the moment.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/273510](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/273510)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/277577](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/277577)

---

### Post by srikar on 2008-11-02
Now its better, i re-installed through alternate cd.I am able to use kubuntu, but some times before login screen ,,screen goes black , then i go to rescue mode and fix xserver.

However this time i am havin a rough ride wid ubuntu.

---

### Post by Snader on 2008-11-02
Here, the problem is not yet solved.

As mentioned earlier, installing 8.10 with the alternate-iso does not solve my problem. Today I tried to upgrade 8.04 to 8.10, but the result is the same as a clean install.

Could you explain to me why there is a [SOLVED]-tag in the topic-title? :) I haven't read a solution yet, or am I missing something?

---

### Post by Monsieur Herb on 2008-11-02
I have the same problem. First the status bar comes up but then my CRT-screen dies. I do hear sounds as if the login screen is behind there (drums). Someone must come up with a solution to this.

---

### Post by horned0wl93 on 2008-11-02
> **Monsieur Herb said:**
> I have the same problem. First the status bar comes up but then my CRT-screen dies. I do hear sounds as if the login screen is behind there (drums). Someone must come up with a solution to this.

I dunno who's marking these "Solved," when the problem is still here... One more day and I'm back to 8.04, or maybe even 7.10...  We're starting to lose LOTS with these "upgrades" -- almost like someone sold-out to M$...

Cheers
0wl

---

### Post by zanzibarabiznaz on 2008-11-02
Aye, removing compiz and compiz-core doesn't solve this problem for me either.

Get rid of that [SOLVED] tag.

---

### Post by milaz on 2008-11-02
I have ATI Radeon 9600 graphics card, and the advice to get rid of compiz didn't help me:

> 
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume


Instead, I was able to overcome this issue in two ways:

1) I found /etc/X11/xorg.conf.failsafe file and copied it to /etc/X11/xorg.conf
The result was 800x600 screen, but I was able to browse the web

2) I booted with previous kernel, 2.6.22-14, and got an okay 1440x900 resolution on my wide-screen monitor.

Looks like some kernel issue. Does anybody know, how can I report this?

---

### Post by onslought on 2008-11-02
I had the same problem, and i tried everything that was written here but nothing helped.

But then i figured it out:
i had a graphic tablet connected to my pc and ubuntu detected it as a display thats was why my X crashed all the time

---

### Post by milaz on 2008-11-02
Looks like it's the third issue. I have the drawing tablet too, and I tried to unplug it and to boot with 2.6.27-7 kernel. No success, my LCD display got into stand-by mode right after ubuntu splash screen with progress bar. So, I use 2.6.22-14 kernel for now.

---

### Post by zanzibarabiznaz on 2008-11-02
Disconnecting my Wacom tablet did not solve the problem for me, either.

---

### Post by the lush on 2008-11-02
I have a very similar issue, after the orange loading bar, I am left with just a plain white screen (laptop LCD), after about 5 minutes, the machine crashes and on re-boot returns to the orange bar and the process repeats. I have tried the x64 and x86 discs.

I then tried to install 8.04.1, and was able to get into the system, but the system refused to use the ATI driver (says that it is enabled but not in use). Strangely, it does not see my network card either so I cannot connect to the internet.

8.04 worked perfectly on a near identical system (VGA and wireless were the same), is it possible to get an old copy of this verion from anywhere to try? Of course I would prefer to use 8.80, or even 8.04.1, but for now I just want to be able to use my computer.

---

### Post by srikar on 2008-11-03
sorry guys, i marked it solved by mistake :(

Still i am getting black screen after loading bar, my monitor gets switched off :(.

In 8.04 the open ati driver only supported 2d acceleration(no compiz until restricted driver is installed) , now the open driver is supporting 3d acceleration by default for my onboard graphic accelerator(ati radeon 200 series).

I guess the problem is wid the new modified driver.... are da developers listening to this thread :confused:

---

### Post by milaz on 2008-11-03
I thought maybe I have this issue because of incorrect system upgrade (it was painful indeed, but finally I am sure I did it right), but now I tried Ubuntu i386 desktop CD. And with the same result: after orange progress bar my wide-screen LCD monitor turns off. I have ATI Radeon 9600 video card connected to AGP slot. And as for Live CD, this looks really like a serious issue.

Developers?

Like Steve Ballmer of the concurring company says, 
Developers? Developers? Developers? Developers?
Developers? Developers? Developers? Developers?
Developers? Developers? Developers? Developers?
Developers? Developers? Developers? Developers?

Help us, please...

---

### Post by Pungero on 2008-11-03
I was having the same problem a while ago, but I managed to get the system running after I unplugged my TV from my ancient ATI Radeon 64Mt DDR Vivo videocard. Seems like most users having this problem are using an ATI card, so I suggest you try starting your system up with nothing but primary monitor attached.

---

### Post by milaz on 2008-11-03
Looks like another problem solved.
But my problem still remains :(

I have only one monitor plugged into VGA out. My video card also has TV out and DVI out, but they were never used.

Also I unplugged my Genius Pen Tablet at was advised in earlier posts, although I don't understand how can USB device be confused with a monitor.

---

### Post by milaz on 2008-11-03
I'll try to get some logs to see what really happens there...

---

### Post by m4ss on 2008-11-04
Here same similar problem... Installing Ubuntu 8.10 with monitor LCD 22" synchmaster samsung and an ATI 4870 1gb, at the first screen after the loading install orange bar i get a blank screen without any possibilities to do something...

What I've to do ?

(it's the official release... anyone have install beta 1,2,3,4,5,6 and RC and have this problem at canonical ?!?!?!!!)

---

### Post by mcb CH on 2008-11-04
Same problem here: on-line upgrade from 8.04 to 8.10 on hp (compaq) nx9030. Screen goes blank after 'kubuntu' start-up splash screen, ie. logon-screen does not appear (although it is there, invisible). In other words, screen is not recognised and initialised.

---

### Post by srikar on 2008-11-04
@m4ss

I had the same problem with RC's of ubuntu and kubuntu too :(

---

### Post by timjohn7 on 2008-11-04
I had the same problem on both a laptop (Fujitsu Siemens Amilo L6825 with Intel 82845 Graphics Card) and a Desktop (ViewSonic E70 CRT Monitor and Matrox G450 Card)
The laptop was solved by uninstalling compiz & compiz-core and the desktop required replacing xorg.conf with some sections of an example xorg.conf from the Matrox website.
I understand that developers can neither develop nor maintain systems for every possible hardware combination, but it makes it extremely frustrating to "market" Ubuntu/Linux when the first impression is a black/blank screen followed by frantic editing in a terminal.  Nothing is scarier or more offputting for a Windows user who may be interested in trying Ubuntu.
Bugs have been filed about these problems, but Intrepid seems to have a particularly poor approach to older video systems.
I wish some of the developers would post a simple explanation of what & why they have done to change a system which seemed to work well in Hardy.

---

### Post by timyoungblood on 2008-11-04
ATTENTION DUAL VIDEO CARD USERS

Couldn't go back to 8.04.1 due to the initramfs bug. I even bought a new motherboard yesterday.

It turns out that simply removing 1 of my 2 nvidia cards solved the problem. Something about 8.10 (XServer 1.5) doesn't like dual video cards along with 177.80 drivers.

At least now I can try to get some work done...what a painful day and a half it has been.

---

### Post by 10-10-20 on 2008-11-04
These two threads should be merged... they have the same issue...

[http://ubuntuforums.org/showthread.php?t=965237](http://ubuntuforums.org/showthread.php?t=965237)

---

### Post by 10-10-20 on 2008-11-04
....

---

### Post by Monsieur Herb on 2008-11-05
Ok, i found a solution to my problem. As I disconnected my TV-out cable from my computer I can now see Ubuntu as usual and it works fine. Make sure you don't have anything connected that might make Ubuntu think you have a primary screen and secondary.

---

### Post by srikar on 2008-11-20
heyy i downloaded ubuntu ultimatte 2.0 .,, stii i get black screen during login time. any kinda fix???

---

### Post by srikar on 2008-12-06
**is the bug fixed ??????**

---

### Post by Shuberace on 2008-12-07
> **srikar said:**
> **is the bug fixed ??????**


No.

Did you really think anyone follows these threads? The developers get what they want—that's us newbies—to download this crappy software, hose our systems, beg and plead for help (to no avail), while they sit back and play games on their MacBooks.

All while we're thinking the problem is with Microsoft.

Wake-up call: I have no problem using my laptop with Microsoft products.

Why don't some of you so-called "guru" developers give Bill a call and take some lessons?

This Ubuntu stuff is nothing more than jerk-off crappy "practice-coding" software...

You get what you pay for, I suppose.

---

### Post by Thiago Valle on 2008-12-08
I'm having the same problem. I can access Ubuntu by first booting on windows, then when in windows i reset the computer and then boot on ubuntu, after that it works fine. Kind of weird though.

As Monsieur Herb said i guess it has something to do with the fact that ubuntu thinks there is other monitor plugged in the graphics card, cause mine actually has output to dual monitors, so it seems that ubuntu thinks that the other output is the primary one.

---

### Post by alanrr_sr on 2008-12-13
> **Thiago Valle said:**
> I'm having the same problem. I can access Ubuntu by first booting on windows, then when in windows i reset the computer and then boot on ubuntu, after that it works fine. Kind of weird though.

As Monsieur Herb said i guess it has something to do with the fact that ubuntu thinks there is other monitor plugged in the graphics card, cause mine actually has output to dual monitors, so it seems that ubuntu thinks that the other output is the primary one.

About your solution, something with [http://bugzilla.kernel.org/show_bug.cgi?id=6350](http://bugzilla.kernel.org/show_bug.cgi?id=6350)

Another victim with a bad upgrade (I should have kept 8.04)
Botting 2.6.24-22-generic works fine, but 2.6.27-9-generic is garbaged.


Bug #1 on the way....

---

### Post by jojoalmighty on 2008-12-13
> **Monsieur Herb said:**
> Ok, i found a solution to my problem. As I disconnected my TV-out cable from my computer I can now see Ubuntu as usual and it works fine. Make sure you don't have anything connected that might make Ubuntu think you have a primary screen and secondary.

You are very  right Monsieur Herb... one glimpse on your message, I open my CPU Box and remove my TV Tuner. When I reboot installation proceeds.. Thank you Monsieur and to the whole Ubuntu Community..  

jojoalmighty:popcorn:

---

