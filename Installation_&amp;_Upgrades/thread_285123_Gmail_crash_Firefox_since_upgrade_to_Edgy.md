---
title: "Gmail crash Firefox since upgrade to Edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Stromgol on 2006-10-26
Since my upgrade Firefox always crash after I get logged in gmail.
Am I the only one this is happening to?

---

### Post by Stromgol on 2006-10-26
I get this when started in console.

> ** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by Stromgol on 2006-10-26
Since I removed the flash pluggin Firefox don't crash anymore with gmail.

---

### Post by erichalfb on 2006-10-26
I am having same problem with firefox and flash.  I added flashblock and gmail/yahoomail no longer crash firefox.  Does anyone know a fix for this other than accepting a no flash world?
erichalfb

---

### Post by erichalfb on 2006-10-26
Stromgol
I take it back.  I am now getting the exact same message you are. Happens even with flash removed.
Rats
erichalfb

---

### Post by erichalfb on 2006-10-26
Stromgol
I found a couple threads with same problem.
Following their recommendations I changed the color depth of my monitor to 24.  That corrected the crash.
erichalfb

---

### Post by emax on 2006-10-27
I also fixed this problem by switching to 24 bit in /etc/X11/xorg.conf

However, now Compiz/AIGLX runs like a dog on my Radeon 9250 :-(

Can I work around this problem without going to 24bit colour depth (and keep my compiz with good performance)?

---

### Post by doberman on 2006-10-27
Hi, 

I am exactly in the same situation. :( 
Firefox crash also with the following web sites :
[LIST]
[*][www.liberation.fr](www.liberation.fr)
[*][www.lemonde.fr](www.lemonde.fr)
[/LIST]
(two french newspapers)

D.

---

### Post by pgilmon on 2006-10-27
In my laptop Firefox also crashes with any flash content since I updated to Edgy. Moreover, sometimes Firefox won't even start just after rebooting, and if I try to start it again it complains about another instance of Firefox that is not responding, so I have to reboot again (because there is no firefox-bin process to kill).

---

### Post by jimbren on 2006-10-27
My default color depth in xorg.conf was 16 and I changed it to 24, even though I'm assuming the folks who changed their depth successfully went from 32 to 24.  

Still no joy.  

I'm going on the assumption that my xorg.conf is kind of jacked up because I've made several unsucessful attempts to get compiz working and to change my install the intel915 driver.  

I upgrdaded to edgy from the repositories just to see how it would go, and I think at some point over the weekend I'm going to go ahead and do a clean install from the CD, more to generally clean everything up and get it to a default state than anything else.  Maybe that will help.

If anyone has changed their color depth and continues to have this problem, please write in so other ideas can be tossed around.

jim.

---

### Post by unwoken on 2006-10-27
i have the same problem.

default depth is set at 24.  changing to 16 or 32 does not help.  installing and uninstalling flash nonfree does nothing.

gmail crashes every time.  the other flash based sites listed in this thread also crash if i try to load them.  

gmail works just fine in opera, but not in 'mozilla web browser', which also  crashes.

any solutions would be much appreciated.

u.

---

### Post by pdoes on 2006-10-27
I'm newbie with Ubuntu, thought I would give it a try on my laptop. The laptop used to run FC5 and FC6 with out a problem.

Same problem here but Firefox crashes when loading Yahoo mail.
I installed Adobe's Flash 9 beta but that didn't help. I was able to not crash once, I opened the Error Console within Firefox while the page was loading and Yahoo didn't crash while loading the first page.

I use FF 2 on a Windhose box as well and have no problem there.

This is big let down for me right now, not a good 1st experience. I'm not giving up yet though.

Peter

---

### Post by doberman on 2006-10-27
Hi, 

I changed the color depth from 16 to 24 and firefox doesn't crash anymore. I am using the nvidia driver.

D.

---

### Post by me1on on 2006-10-27
I had the same problem. Any page with Flash crashed. Just type in a terminal (change *gedit* to *kate* if you're using kubuntu):
```
sudo gedit /etc/X11/xorg.conf
```
Then find the line that says (toward the bottom of the file):
```
DefaultDepth	24
```
Change the number 24 to 16, save, close gedit, and restart ubuntu for the changes to take effect.

---

### Post by unwoken on 2006-10-27
didn't work for me me1on.

gmail crashes every time i try to access it, even after a full restart and change from 24 to 16 (tried with nonfree flash both installed and uninstalled).

does anyone else have a possible solution?

u.

---

### Post by unwoken on 2006-10-27
ok.  i found a solution (for my install anyway) in another thread:

[http://www.ubuntuforums.org/search.php?searchid=9211489](http://www.ubuntuforums.org/search.php?searchid=9211489)

thought i would post it here just in case anyone looking here needs more info.

---

### Post by sg_57 on 2006-10-28
Funnily enough (with NVidia graphics card) changing the Default from 16 to 24 in xorg.conf seems to have done the trick. 

I am now able to view GMail!

SG

---

### Post by Jad on 2006-10-29
unwoken, 
Can you give us link to that thread? not to the search result as they don't cache search results

---

### Post by jimbren on 2006-10-29
When I changed my resolution, I restarted X to make the changes take effect, and then went back to gmail to test it, and gmail still crashed.  I tried it a few more times and still couldn't get to gmail and a slew of other pages without crashing.  

I didn't restart for two days, but now that I have, I don't have any problems at all.

So try resetting your color depth and restarting your computer, which is what I"ve also read some people doing here, and you should be good.

jimbo

---

### Post by unwoken on 2006-10-29
> **Jad said:**
> unwoken, 
Can you give us link to that thread? not to the search result as they don't cache search results

oops.  sorry Jad.  not sure how that happened.  this should work:

[http://ubuntuforums.org/showthread.php?p=1679573](http://ubuntuforums.org/showthread.php?p=1679573)

hope it works.

---

### Post by Jad on 2006-10-29
Just want to confirm that all suspects has been deceased and firefox running flawlessly now 
:D

---

### Post by daller on 2006-11-01
Well, I can't make it work!

Can anyone dump me the IMAP/POP options for gmail?

(I have activated it, but forgot the SMTP-server, the inbound-server, and the username - I assume it's "username@gmail.com" - Or is it just "username"?)

Please help!

---

### Post by Jad on 2006-11-01
Daller, 
check this 
[http://mail.google.com/support/bin/answer.py?ctx=%67mail&hl=en&answer=12103](http://mail.google.com/support/bin/answer.py?ctx=%67mail&hl=en&answer=12103)

---

### Post by haveanotherpuff on 2006-11-01
SimpleMepis 6 had the same problem,someone said to change the theme for firefox and it fixed it, had to do it myself.

---

### Post by daller on 2006-11-04
> **Jad said:**
> Daller, 
check this 
[http://mail.google.com/support/bin/answer.py?ctx=%67mail&hl=en&answer=12103](http://mail.google.com/support/bin/answer.py?ctx=%67mail&hl=en&answer=12103)

Thanks! - Now I use Kmail instead of Firefox!

Problem solved :)

---

### Post by rts on 2006-12-09
None of the proposals in either this thread or the thread "flash-related crashes" solves my problem... GMail crashes Firefox every time.

Any more suggestions?

---

### Post by Mrs Harris on 2007-01-15
> **me1on said:**
> I had the same problem. Any page with Flash crashed. Just type in a terminal (change *gedit* to *kate* if you're using kubuntu):
```
sudo gedit /etc/X11/xorg.conf
```
Then find the line that says (toward the bottom of the file):
```
DefaultDepth	24
```
Change the number 24 to 16, save, close gedit, and restart ubuntu for the changes to take effect.
That's great... works a treat for me.
Thanks muchly

---

### Post by Phlegethon13 on 2007-02-17
I am having a similar, yet much much worse problem.

system: 6.10 with updates, firefox, ATI 9250

When I go into gmail (gmail itself works fine) and hover over someone who is also online then click chat it crashes.  Right when I click chat.  And not just firefox mind you.  I get a complete system crash.  Firefox disappears, I can move my mouse for a second, then all panels disappear and system is locked.  Completely locked <ctrl><alt><backspace> does nothing, and <ctrl><alt><del> does nothing.

So, I reboot the system, boot failure.  Grub error 24.  HOw the hell this breaks my boot I have no idea.

Does anyone have ANY ideas????

Please, this is a pain as you can imagine.

Greg

---

