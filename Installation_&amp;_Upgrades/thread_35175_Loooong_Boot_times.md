---
title: "Loooong Boot times"
date: 2005-05-17
forum: Installation &amp; Upgrades
---

### Post by sambo69 on 2005-05-17
Hoary loaded and working. In fact the only problem I have is that the machine takes an insane amount of time to boot. 
I've waited for 45 MINUTES and walked away without seeing it boot. When I check it the next day , it's at the login screen waiting for me...

I don't see any errors in dmesg; I've taken the quiet out of the GRUB boot commands and don't see an errors, the PC hangs with something like this on the screen:

Booting 'Ubuntu, kernel 2.6.10-5-386 '

root   ( hd0,0)
Filesystem type is ext2fs, partition type is 0x83
blah blah blah

savedefault
boot

( wait for > 45 min)
 and then it boots up.

Please let me know if you have any suggestions.

Network is working 
static IPs

everything functions fine AFTER it boots.

Regards
Sam

---

### Post by defkewl on 2005-05-17
I think that's quite normal  ;-)

---

### Post by nad on 2005-05-18
This is _not_ normal.

Computer specs please.

---

### Post by sambo69 on 2005-05-18
Anyone have any suggestions about my boot time issue?

Regards
Sam

---

### Post by apollyonis on 2005-05-19
You weren't dual booting with Grub by any chance, were you? The savedefault / boot portion is in the menu.lst file under /boot/grub Changed kernels recently or had a dual boot system by any chance? You may have to alter menu.lst

---

### Post by sambo69 on 2005-05-19
Thanks for the serious reply ( by the way moderator, my comments were NOT extraneous!)

Here is some more info:
PIII 550 
385 mb RAM
Viper770 video card ( 32mb video ram)

running straight clean ubuntu load not dual booting

haven't changed kernels; this has been a problem since I installed... when I rebooted at the end of the install and got the above problem, I waited until I gave up and went to bed. When I checked the next day I had the login splash screen. The longest that I've ever been able to wait has been 45 minutes and it still didn't load. When I came back later, it was loaded. 

Any suggestions?

Sam

---

### Post by sambo69 on 2005-05-22
Well,
so far only ONE serious reply on my problem.... Thanks you all have been great!

Sam

---

### Post by bored2k on 2005-05-22
[QUOTE=sambo69]Well,
so far only ONE serious reply on my problem.... Thanks you all have been great!

Sam[/QUOTE]
 Try this
sudo chmod -x /etc/init.d/ntpp && sudo chmod -x /etc/init.d/hotplug

---

### Post by sambo69 on 2005-05-23
Bored2k,
I think you've hit it!

I ran the commands that you recommended ( sudo chmod -x /etc/init.d/ntpdate) and that seems to have sped it up. I'll keep playing with it. 

Thanks for your help!

Sam

---

### Post by bored2k on 2005-05-23
[QUOTE=sambo69]Bored2k,
I think you've hit it!

I ran the commands that you recommended ( sudo chmod -x /etc/init.d/ntpdate) and that seems to have sped it up. I'll keep playing with it. 

Thanks for your help!

Sam[/QUOTE]
 [http://ubuntuguide.org/#ubm](http://ubuntuguide.org/#ubm) 
A little GUI gift.

---

### Post by sambo69 on 2005-05-24
Well I *thought* I had it...

Dl'd the ubm (thanks) and disabled hotplug in addition to PPP( just to be safe) still takes about an hour to go from :

BLAH BLAH
savedefault
boot

to 

login screen.

Can't seem to make any real headway on this problem.

When I thought is was fixed before,  PC booted quickly once but only into 640x480 resolution?!?! when I rebooted , it came back up ( after about an hour of hang time) into normal resolution 1024x786.!?!?!?!  

I am totally adrift here...

Any other suggestions?

---

### Post by sambo69 on 2005-05-26
anyone... anyone.... bueller.... anyone ?!?!?!?!

---

### Post by sambo69 on 2005-05-28
Help...
anyone ... anyone at all,

I removed ubuntu and loaded Debian and managed to get that working on the same PC. It boots normally. 

Can anyone tell me what is supposed to be happening right after this comes on screen:

savedefault
boot

That way I would at least have a direction to go in.

---

### Post by sambo69 on 2005-05-28
I dumped Ubuntu and loaded Debian (testing) on the PC. as it boots up I looked for the same screen output as the one that shows when I have a problem with Ubuntu.

savedefault
boot
<then>
Uncompressing linux

I'm guessing that I'm having a problems at the "uncompressing linux" part with Ubuntu. Is there any info out there related to speeding this part up. With the debian install, it sails right past the problem area with no issues. 

any suggestions?

---

### Post by sambo69 on 2005-05-28
Welp,

I've gotten debian working just the way I wanted it... except for sound... and am going to stick with it instead of Ubuntu.


Close this thread.

Thanks to the ONE person that tried to help.

Regards
Sambo69

---

