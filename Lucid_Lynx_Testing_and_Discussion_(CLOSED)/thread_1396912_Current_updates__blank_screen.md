---
title: "Current updates  blank screen"
date: 2010-02-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-02-02
The last updates causes a blank screen. If I use "nomodeset", it boots and after a few minutes everything freezes.

These were the last updates: nautilus, libnautilus, libglib2.0, nautilus-data, libglib2.0-data

An update for plymouth came in a hour earlier, not sure if that had something to do with it.

anyone else with this issue?

Also, I no longer have the xplash/usplash white circle of friends boot logo.

So I **removed Plymouth** and now I'm able to boot.

 I get the message "..could not connect to plymouth", but I got that even when plymouth was installed ?!?!

---

### Post by dagrump on 2010-02-02
I am glad you mentioned this, I had to remove plymouth. Froze up solid, no response to the key board at all.
Thanks.

---

### Post by beazizo on 2010-02-02
I get all the way to gdm login screen then system freezes.  

This from X.org.log probably has something to do with it:


Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a22b8]
1: /usr/bin/X (0x400000+0x65059) [0x465059]
2: /lib/libpthread.so.0 (0x7f51994df000+0xf780) [0x7f51994ee780]
3: /lib/libc.so.6 (__select+0x13) [0x7f5198299be3]
4: /usr/bin/X (WaitForSomething+0x1ba) [0x45f41a]
5: /usr/bin/X (0x400000+0x30762) [0x430762]
6: /usr/bin/X (0x400000+0x260aa) [0x4260aa]
7: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f51981dbc4d]
8: /usr/bin/X (0x400000+0x25c59) [0x425c59]

atal server error:
Caught signal 3 (Quit). Server aborting


Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by beazizo on 2010-02-02
Removing plymouth solved my freezing problem too.

---

### Post by tad1073 on 2010-02-02
same here as far as keyboard and mouse, removing plymouth did the trick

---

### Post by zaphod777 on 2010-02-03
> **tad1073 said:**
> same here as far as keyboard and mouse, removing plymouth did the trick

Same issue and fix for me.

---

### Post by Ibidem on 2010-02-03
Sounds like time to file a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/plymouth") or check [this bug]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/510524").

---

### Post by VMC on 2010-02-03
> **Ibidem said:**
> Sounds like time to file a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/plymouth") or check [this bug]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/510524").

I wasn't at the bug thinking at the moment. This was just a feeler to see if I was the only one. Now it defiantly looks like a bug. I choose the #510524 "Affect me too". thanks for the link!

---

### Post by moviemaniac on 2010-02-03
No problems here...

---

### Post by MacUntu on 2010-02-03
Strg+Alt+F7 Strg+Alt+F8 Strg+Alt+F7 Strg+Alt+F8 and it works. Plymouth worked fine before the update, now it*s a bit crippled.

---

### Post by xtoudi on 2010-02-03
> **MacUntu said:**
> Strg+Alt+F7 Strg+Alt+F8 Strg+Alt+F7 Strg+Alt+F8 and it works. Plymouth worked fine before the update, now it*s a bit crippled.

Strg???? You mean Ctrl, I think :-)

---

### Post by MacUntu on 2010-02-03
Damn, now you know I have a German keyboard layout (Ctrl = control = Steuerung = Strg). :D

Not sure this is the same problem as described in the bug report, because I get no freezes.

---

### Post by ronacc on 2010-02-03
I got that this morning , I had updated yesterday but not rebooted before shutting down for the night . I could hear the login sound but ended up with a black screen with 3 small white rectangles . I tried ctrl>alt>F2 logged in by blind typing and tried startx no help , I could see the drive light flickering when I hit return so I knew something was happening , tried sudo reboot  and the reboot went to normal desktop , during the reboot I did get some strange colored patches traveling across the screen , if it recurs I will remove plymouth which has never worked for me anyway.

---

### Post by Jordanwb on 2010-02-03
> **VMC said:**
>  I get the message "..could not connect to plymouth", but I got that even when plymouth was installed ?!?!

That bug has been reported. I haven't had any problems, but there are 80 updates waiting to be installed.

---

### Post by xtoudi on 2010-02-03
No need to purge plymouth - just Ctrl+Alt+F1, then:
 sudo /etc/init.d/gdm restart - works fine (of course next restart=next gdm restart)

---

### Post by VMC on 2010-02-03
> **xtoudi said:**
> No need to purge plymouth - just Ctrl+Alt+F1, then:
 sudo /etc/init.d/gdm restart - works fine (of course next restart=next gdm restart)

The reason I created this topic was the fact that nothing worked. It started to boot then froze solid. "alt + reisub" didn't work, nothing but a power-cycle worked.

I had to chroot into my lucid partition and then removed Plymouth. First as a test. Then I realized Plymouth was causing my problem.
So following Ibidem bug link, I had the same issue the others had.

---

### Post by xtoudi on 2010-02-03
> **VMC said:**
> The reason I created this topic was the fact that nothing worked. It started to boot then froze solid. "alt + reisub" didn't work, nothing but a power-cycle worked.

I had to chroot into my lucid partition and then removed Plymouth. First as a test. Then I realized Plymouth was causing my problem.
So following Ibidem bug link, I had the same issue the others had.

OK - there are still problems and ... right now (a few steps and few resolved bugs later) I can workaround this by doing this what I wrote.

... and the screen is still blank so ... I'm in the topic :-)

---

### Post by tad1073 on 2010-02-03
> **xtoudi said:**
> OK - there are still problems and ... right now (a few steps and few resolved bugs later) I can workaround this by doing this what I wrote.

... and the screen is still blank so ... I'm in the topic :-)

The point is, plymouth is breaking something, I assume Xorg and GDM, the work around you suggested is too tedious. Removing plymouth solves the problem and no work around is needed.

---

### Post by xtoudi on 2010-02-03
> **tad1073 said:**
> The point is, plymouth is breaking something, I assume Xorg and GDM, the work around you suggested is too tedious. Removing plymouth solves the problem and no work around is needed.

But of course you're right. I agree that plymouth is the problem ... This work around might be usefull if someone do not need to delete sth (or do not feel well with that). And I agree with you ... this is too tedious - becouse this is only light work around (without any modyfications) and this is not any kind of solution which definitely solves the problem.

... but removing plymouth also do not solves the problem for me ... but this is my opinion and please ... do not start any conversation with "what is solved and what is not ...." :-) - this is only my opinion.

---

### Post by mikeyphi on 2010-02-03
Similar problem here! Screen froze with 'out of range' for display. Removed plymouth via recovery mode and all is OK.

---

### Post by phenest on 2010-02-03
Same problem here, and removing plymouth also worked. Is this a plymouth + nvidia issue? Worth checking as plymouth does not currently work with nvidia.

---

### Post by zaphod777 on 2010-02-03
I am using nvidia so could be.

---

### Post by VMC on 2010-02-03
> **phenest said:**
> Same problem here, and removing plymouth also worked. Is this a plymouth + nvidia issue? Worth checking as plymouth does not currently work with nvidia.

I don't think its just nVidia, I have an Intel i865 chip.

---

### Post by bshosey on 2010-02-03
I also have a strange problem. I get a curer flashing in the up left corner and I do see the courser. every key including the ctrl, alt and even the laptops fn key will make it type symbols in the up corner but do not get the logon box.

---

### Post by ricsi-pontaz on 2010-02-04
> **VMC said:**
> I don't think its just nVidia, I have an Intel i865 chip.

Yes, I think it too, because I have an ATI card.

---

### Post by vrkalak on 2010-02-07
I had the same problem, a few days back, after my Upgrade.d in Xubuntu Lucid A2.  About the same time, as you have mentioned ... must have been the same upgrades/updates.

After the upgrades, I still stayed in the OS, finishing some artwork I was doing in Inkscape.  Before, I did the recommended 'system re-start'

My Inkscape and Firefox-3.6 both froze at about the same time.  This has never happened with any App. in Ubuntu before.  I didn't give it a 2nd thought.  I just used the System Monitor and killed/closed everything

Then, I did the re-start of the computer.  Upon re-booting, it went through the Grub screen and the Log-in screen ... then, the dreaded BSOD.

I haven't been able to re-enter the b0rked Xubuntu Lucid A2 no matter how I have tried.  Even the Recovery Mode from Grub won't open it.  The only way I can get inside the b0rked OS is by mounting it from my other Linux OS in my PC.  Or through the original LiveCD, or the SystemRescue CD.  But, I have not been able to change anything inside the broken OS  partition.

I have attributed the problems to either Plymouth or the newer Kernel upgrade.  

In a couple of weeks the next Alpha 3 release will be out.  If I still can't fix it, then I'll just install the new Lucid Alpha 3 over the Alpha 2.

No harm done ... all my data/files/documents and such are on a separate /home partition.

---

### Post by gjoellee on 2010-02-07
I am not sure if the blank screen is caused by plymouth directly, I think it might be related to GDM. I don't get this problem in Kubuntu, which use KDM.

Also I figured out that GDM does not start at all. I have to start it maually:
```
sudo services gdm start
```

---

### Post by ranch hand on 2010-02-07
I get a lot of errors at shutdown and wonder if it is not due to some  x component being caught up with plymouth.

---

### Post by Hobbes on 2010-02-08
Not sure if this is the same thing or not:

1. I installed Lucid daily yesterday (netbook remix)

2. Booted fine the first time, used it for a bit, whatever, shutdown

3. Booted back up, got to a black screen, froze... next time using ctl-alt-f1, f7, etc. I eventually got it to get back to gdm, but ** after I logged in ** it froze again...

4. rebooted, updated a couple packages from tty1, logged in again, completely hung up again, repeat, repeat

---

### Post by zika on 2010-02-08
> **ranch hand said:**
> I get a lot of errors at shutdown and wonder if it is not due to some  x component being caught up with plymouth.My machine doesn't even shutdown. I have to switch it off on switch. At the moment, I do not have xorg-edregrs or any other ppa, just chromium. So, it is a plain LL... Yes, I've tried **shutdown -P**.

---

### Post by VMC on 2010-02-11
The newest kernel (2.6.32-13-generic #18-Ubuntu SMP), did **not fix Plymouth**.

Edit. My bad. It took three reboots to confirm its still a problem.

---

### Post by ranch hand on 2010-02-11
Also in the upgrade were;
> 
libplymouth2
plymouth 
gdm

I did my update/upgrade on a throwaway OS and tried it and it worked great.  Then I upgraded the kernel and it was back to where it was.

I was just doing the evening update and got to booting to that same system and it acted like it has.  I tried to call for tty2 and the login screen showed up.

Thinking that was strange I tried it with my ISO testing OS.  Same deal.

Not trusting that result due to the 2.6.33 kernel it is running I am upgrading another one to try this out on.

It really looked frozen at the black screen.  No flickers of my externals lights.  Nothing but the small cursor flasher.

Well, it is done so I am off to try it again.

---

### Post by ranch hand on 2010-02-11
Well, that was fun.

Upgraded the bugger and thought "well now we will see, I,ll make sure I wait even longer than before before trying any thing".  Didn't work.  The bugger was a little slow but just booted up to the login screen and it worked.

So, I thought I may as well try it on this OS.  This is the one I use.  It is also the one that seems to be the most pissy about this.  I I chrooted in from the one that booted up and tried it out.

This one booted up.  Some do.  Some don't.

Beats me.  They are all on the same drive so I really doubt that it is hardware related.

---

### Post by VMC on 2010-02-11
Remember, it takes at least 3 reboots before you really see if Plymouth freezes anything. 

I thought the newest kernel fixed the Plymouth problem. I even re-booted a couple of times. Then I shutdown completely and re-booted. It then froze.

---

### Post by ranch hand on 2010-02-11
That should not be my "problem".  While the box itself is seldom shut down the hard drives for the test platform are.  They are off right now as I just moved to my stable OS (9.04) that I have boinc on too.

Your post, however, gives me hope for fun tomorrow when I boot back over to the test platform.  Thanks.

Bring on the FUN.

---

### Post by tr33m4n on 2010-03-04
Similar situation with my setup, running Lucid 64 bit, open source radeon drivers... concluded its not the graphics drivers but as mentioned before, gdm. Not sure what's going on... I get the blank cursor at boot up, but can get to the login screen by pressing return. From then on it works perfectly, except for some unknown reason the screen will randomly go blank after about 10/15 minutes... Before recent updates I was able to tty and (blindly) restart my computer the right way... however everything freezes now when the screen blanks. D'oh...

Hope this gets fixed soon
Dan

---

