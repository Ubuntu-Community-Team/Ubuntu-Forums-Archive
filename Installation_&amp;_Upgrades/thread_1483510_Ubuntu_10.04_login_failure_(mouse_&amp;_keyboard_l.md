---
title: "Ubuntu 10.04: login failure (mouse &amp; keyboard locked); network failure."
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by Garry_L on 2010-05-14
[FONT=Liberation Sans, sans-serif]I have had, & still have, problems.

I am a GUI user. I can run command-line, but I only know & understand a few commands, so I can only run other commands when I find them on the forum (etc.) or someone tells me what to do. So, in many ways, I am a newby with Ubuntu, in spite of lots of usage.

I have been using Ubuntu for over 4 years now, usually upgrading a month or so after a new release. However, since I had an easy upgrade to 9.10 last year, I decided to upgrade to 10.04 ~ 1 week after release (07/05/10). I downloaded the alternate CD, as I have been able to pass that on to friends with even less download capability than me.

The install went reasonably well. I did not take the option to include updates at the same time.

I did accept to allow the upgrade tool to delete all suggested files (I don't know what most of them were for, but I was happy to get rid of a lot of old kernels, etc.). This deletion may have been the reason for my subsequent problems.

When I booted & had problems, I thought that the missing updates would help, so allowed those to be installed (this was later, after I managed to boot using fail-safe). It didn't solve the problems. 2 are listed below:

1. Now when I boot using the current kernel, I get the following:

When it reaches the login screen, I get either of the following:
. A locked screen with no mouse or keyboard capability. So I press & hold the start button for 6 seconds to stop the PC.
. The screen is not initially locked, but after I select my user & try to enter my password, It either locks up as above or it keeps looping through saying the user/PW combination is not valid (sometimes filling the PW line with dots).

Once, it worked perfectly!?

So, from then on, I booted using the fail-safe mode.
[/FONT]


From reading other posts, I gained the impression that this login problem may be caused by the graphics driver.


[FONT=Liberation Sans, sans-serif]I now know that I have a 5-year-old ATI graphics card. However, at one stage during the boot, it said to configure an NVidia graphics driver. This didn't help.

Hardware Driver didn't help, as it merely comments "No proprietary drivers are in use on this system".

I tried to work out what was wrong with the graphics driver, & soon realised that it was set up for the wrong card type.

After lots of searching files, I thought fglrx might be the solution, & downloaded that (even though ATI said that the legacy cards support stopped over 1 year ago). It didn't help.

I then noticed that there was no /etc/x11/xorg.conf, only backups & failsafe.

So I copied failsafe to xorg.conf, & changed the driver to "radeon". This didn't help.

I did try the "reconfigure graphics" option that comes up when using the fail-safe mode.

I think that this latest step may have helped to provide high-resolution graphics, at least.[/FONT]


                                  [FONT=Liberation Sans, sans-serif]I changed the driver to “fbdev”, but this didn't help the login problem, so I changed it back to "radeon".  I still have HD graphics, so I think that I will stay with "radeon", as it seems to be the right driver.[/FONT]
 

 [FONT=Liberation Sans, sans-serif]I think that I need to look elsewhere for an answer to the login problem.[/FONT]


                                  [FONT=Liberation Sans, sans-serif]2. On Tuesday, when I booted (using the fail-safe mode, I could not get any network connection. My first thought was that the problem was in the modem (or possibly the separate router). However, when I checked my other PC (Mythbuntu 9.10), it could access the Internet.

Furthermore, The icon on the top left was for the wireless connection, not the cable connection. My router has wireless, but my PC doesn't.

I did lots of searching using my other PC, but with no success.

However, when I booted up on Thursday (I needed a break from looking at these problems for 5 days!), the network started properly... and is still working.

I hate this random/intermittent aspect of problems.

Regards, Garry.
[/FONT]

---

### Post by davidmohammed on 2010-05-14
ok, I know you don't like the command line - but can you confirm your graphics card by starting a terminal and typing

lspci | grep VGA

Also - does booting with nomodeset in your grub help or hinder your graphics issues?

(shift to display grub when rebooting, press e to edit, and type nomodeset before the "quiet splash")

---

### Post by edempco on 2010-07-13
I have exactly the same problem!

My ATI card is a Radeon 9550. 

I also tried to follow non-GUI instructions to fix the ATI graphics problems with no success. I used the insructions at this URL: [http://ubuntuforums.org/showthread.php?t=1504027](http://ubuntuforums.org/showthread.php?t=1504027) 

Any suggestions?

---

