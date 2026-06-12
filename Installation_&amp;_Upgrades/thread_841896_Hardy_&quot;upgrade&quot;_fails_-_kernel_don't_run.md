---
title: "Hardy &quot;upgrade&quot; fails - kernel don't run, display unusable"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by fudoki on 2008-06-26
Since I "upgraded" one of my production workstations, it is totally unusable.  The new kernels (2.6.24-19-generic and 2.6.24-19-rt) do not run.  The display, under the old kernels (2.6.22-15-generic), are degraded to 800x600 resolution - simply not usable.  At least they load...

Running "displayconfig-gtk" as Root highlights the problems.  "Saved" settings do not save.  After selecting the correct monitor (the video card, MGA 450 Dual-Head is, amazingly, correct) the resolution defaults to the bizarre geometry of 832x624!!  Repeated resetting to the needed 1024x768, and saving to a designated configuration, after successfully testing, produces NO CHANGE WHATSOEVER in the behavior of the system, or in the xorg.conf file.

Manual changes to xorg.conf produce no change, or result of any kind - UNLESS one foolishly believes that "sudo dpkg-reconfigure -phigh xserver-xorg" might work as it has for the past DECADE.  It does not.  It produces an xorg.conf file COMPLETELY STRIPPED OF ALL MEANINGFUL CONFIGURATION INFORMATION AND A BLACK SCREEN IS THE RESULT...

Have we made some mistake being loyal to, and trusting, Ubuntu?

It appears a whole different model of configuration has been adopted, as I have seen suggested in some posts.

ANY CHANCE OF THESE CHANGES BEING DISCLOSED AND DOCUMENTED, AND IF SO, WHERE CAN SUCH DOCUMENTATION BE FOUND?

I have received over half a dozen angry calls from quite likely former clients who clicked on "Upgrade" in the update manager window, only to turn their computers into unusable pieces of junk.  This has happened to me on 4 of 6 machines in my Shop and my Offices.

Who can blame them?  Past Upgrades worked.

Not having days to study up on undisclosed, apparently unilateral changes by Ubuntu, I have loaded Debian on my own broken boxes, and they work again.  I don't have the time to play around with some new paradigm of computer science sprung on me without notice or warning...

WHAT'S GOING ON AT UBUNTU?  IS 55% SATISFACTION GOOD ENOUGH FOR YOU GUYS? (see the survey of "update experiences")  IS THERE SOME NEW METHODOLOGY TO CONFIGURATION OF LINUX I MISSED HEARING ABOUT IN THE 7 INDUSTRY MAGS I READ EACH MONTH, AND IF SO, WHERE ARE THE SPECIFICATIONS, DISCUSSION, AND DOCUMENTATION OF THE SAME.

While I await a reply on this Windows machine, I will be loading Debian onto the final development machine here at my Shop/Lab.  I just don't have more than half a day to spend on this kind of thing, and have some very angry clients to try and recover.  Two have already gone back to Windows, after 5 and 4 years of using Linux....  Now that's a real shame, but I can't blame them, considering what happened to their computers that they rely on.

Any help, explanations, or pointers to documentation describing, detailing, and articulating why basic configuration files, procedures, and standards no longer work at all in Ubuntu and related products would be greatly appreciated.

Dr. W. T. "Fudoki" Wilkinson

---

### Post by steak-sandwich on 2008-06-26
The same thing happened to my laptop just a few minutes ago after I updated ubuntu. 
Nothing works properly.
When I click on "Test" in the Screens and Graphics menu nothing happens. Just a black screen and then I have to restart.

---

### Post by Pumalite on 2008-06-26
Everyone that has installed proprietary Driver by enabling 'Hardware Driver' should have no problems. ( 3 of my machines). In the other 2 ones I gor the same as you, but all I had to do was reinstall the proprietary video driver 'the hard way' and I was back in business.

---

### Post by Pumalite on 2008-06-26
pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
pumalite@pumalite-desktop:~$

---

### Post by Midwest-Linux on 2008-06-26
Please, would someone from the forums or one of the moderators please put up a sticky regarding possible loss of function or functions  after a kernel upgrade. Please put the sticky in this forum and the Network and Wireless forums so at least people can be aware of the problems before hand and might give them the option of not upgrading. 

Thanks.

---

### Post by Pumalite on 2008-06-26
'When you're helping a friend with an evil Broadcom wireless card, it's no longer bcm43xx-fwcutter. It's now b43-fwcutter.'

---

### Post by Pumalite on 2008-06-26
For xserver:
'xfix is a command in safe graphics mode. If you're working outside of that, stick to xrandr'

---

### Post by steak-sandwich on 2008-06-26
Now I have a even worse problem. When I start my laptop, after the ubuntu logo my screen becomes black. I can't do anything. What should I do now. I can't even copy my files to a harddisk because I can't see anything. 
Can anyone help me?
Thanks

---

### Post by Pumalite on 2008-06-27
Have you tried:
Ctrl+Alt+F1 to get command line? Can you get one?

---

### Post by steak-sandwich on 2008-06-27
no it didn't work. But I was able to copy my files. Now I installed ubuntu hardy but I'm scared to upgrade. I don't want to get the same problem.

---

### Post by Pumalite on 2008-06-27
Make sure to fully update your system first. No third parties in the sources.list. Donload the latest proprietary driver for your card to the Desktop and you are good to go.

---

