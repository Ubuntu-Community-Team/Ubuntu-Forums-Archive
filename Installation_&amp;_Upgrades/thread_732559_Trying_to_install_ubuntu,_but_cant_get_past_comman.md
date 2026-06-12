---
title: "Trying to install ubuntu, but cant get past command line"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by duhglas on 2008-03-23
Hey guys, I'm new to the group, have just begun checking out linux lately, and gonna give it a shot. I've been trying to install ubuntu, I've read through a lot of the installation guide and some forum posts, but I havn't got anything to work yet.
First off I build my computer myself, I have intel quad core processor, geforce 8800 gt vid card, 2gb ram, 320gb hard drive, and I use a wireless connection.
I downloaded the 64 bit version of ubuntu, burnt it to cd, and everything seemed to go well. 
I got to the first ubuntu install screen and clicked on the install ubuntu option. There my screen shuts off for 30 seconds or so then turns back on and says that ubuntu does not recognize my graphics card or monitor. I enter in the correct graphics specs, but my acer x263w monitor isn't on list. So I enter in generic one. I have a dell monitor that I tried using as well, that was recognized, but it didn't seem to make any difference.
Then it goes to command line screen and says:
* Starting deferred execution scheduler atd [OK]
* Starting periodic command scheduler crond [OK]
*checking battery state...    [OK]
* Running local boot scripts (/etc/rc.local) [OK]

I tried following the instructions on installing ubuntu from command line. Entered in a bunch of different commands didn't get it working. Entered in same commands in the different ctrl - alt- f1, f7, f4 screens, and tried quite a few different things but didn't get it working.
I'm stuck here, can't get ubuntu working.
Is my hardware compatible, is it compatible with 64 bit version? Any ideas? Thanks ahead of time for the help.

p.s. I'm running 32 bit vista home basic right now.
I checked the ubuntu file after downloading and it was fine, and used the suggested infra recorder to burn cd.

---

### Post by thamood on 2008-03-23
i replied this on another post:

Hey i have the same problem...my solution for now is when the list comes up "the grub list" don't select the first option (mine was something etc... at the end is 386 your might be diffrent) try to select the one the ends with the word "**generic**" is worked for me but why didn't the first one run???

---

### Post by PreviousN on 2008-03-23
Well, I just built my own computer as well, except my processor is Phenom and I've got a 8800gs and 4 gbs of ram. Anywho, I had to use the alternate installer and install in text mode. It spouted off errors in the normal 64bit installer too. 

Upon first boot after text mode install it gave me bulletproof x. So I downloaded envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
and it automatically installed nvidia's latest driver and had it rewrite my xorg.conf. Then I restarted and had desktop wall/wobbly windows. I'd say worked great (after some headaches in the beginning)

I've heard that editing the boot options to remove "splash" helps as well, so you could try that before downloading the whole alternate installer. 

So advice?

Change boot options on cd to have no "splash"

If that doesn't work, try the alternate installer cd.

---

### Post by duhglas on 2008-03-23
Ok i'll try both these ideas, but do you know the command to enter to turn splash off, as I am not familiar with using the command line, I just enter in what others tell me to.

---

### Post by fain on 2008-03-23
Hello i have a 8800 ultra and the splash stops my system from booting too.

the command for turning the splash off is nosplash at the end of the kernel line
example of my /boot/grub/menu.lst
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=74a56dd0-2265-445d-b729-fd4e28d839a1 ro quiet nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

the "nosplash' will disable the splash hope this helps

---

### Post by duhglas on 2008-03-23
Ok I'm goign to try that now. So at the end of the kernel line I just put 'nosplash', then hit enter. Or do I have to enter in 'sudo nosplash' with some other commands. I am hardly familiar with how to use the command prompt, so sorry if I am asking simple, ridiculous, or stupid questions.
I am going to go try that right now though, and get back to you with the details soon.

---

### Post by duhglas on 2008-03-23
I tried turning off nosplash, but I wasn't doing something right so it didn't recognize the command. The first command screen that comes up for me is:
* Starting deferred execution scheduler atd        [OK]
* Starting periodic command scheduler crond    [OK]
*checking battery state...                                     [OK]
* Running local boot scripts (/etc/rc.local)          [OK]
_

Is this and I enter in commands here which have done nothing for me yet. So I hit ctrl-alt-F1 usually and it goes to another screen where my commands do something. So I tried entering in 'nosplash' and 'sudo nosplash', and they were not recognized. I hit ctrl-alt-F4 and F7 as well and tried it there but it did nothing. Not sure what to do here.

---

### Post by PreviousN on 2008-03-23
sorry if I wasn't clear. 

The nosplash option is entered BEFORE the system is booted. So you put the cd in the system and then hit I think the tab key to edit. This will allow you to edit boot options. 

To be completly honest with you, I'm sorry this hasn't worked out. I've got 6 computers running ubuntu and just chanced upon this problem with my new computer.You must be pretty frustrated. As such, keep posting and we'll figure out you're problem or submit a bug report. 

Cheers!

---

### Post by duhglas on 2008-03-23
Alright I entered in the nosplash option before i booted up and it made a big difference. It was faster, and there was way more information being displayed then there was before. It was telling me that it was booting and to wait, and showing me everything that was loading up.
Unfortunately it didn't get loaded up though, it went through the whole process then got to this screen that it was going to before which says:

     Ubuntu is running in low graphics mode
screen adn graphics card could not be recongnized......you have to configure display yourself.

So I try doing that, have tried a few different settings but it just goes back to the text boot everytime.

It had this message though when ubuntu was trying to boot:

*Strating powernawd...   
/etc/rc2.d/520powernawd: 156: cannot creat
/sys/devices/system/cpu/cpu0//cpufreq/scaling-governor: Directory nonexistent

*CPU frequency scaling not supported

so not sure if that means anything to you, but it seemed like an important message. 
Atleast we're making progress here, I was getting excited before thought it was going to boot up but not quite. So what shoudl we try now?

Can I try the envy program to download the drivers, or do I have to get ubuntu running for real first before I can?

I was wondering too if vista can be affecting ubuntu at all. I've just recently had some problems with windows media player, powerdvd, and a few other programs when I try to play avi's or dvd's, and my computer has seemed to be working a little slower, and games don't seem quite as smooth. I tweaked a few nvidia settings and ran ntune, so just wondering if a clean install of vista might help out, as I'm planning to do this anyway before the permanent install of ubuntu.

---

### Post by fain on 2008-03-23
> **duhglas said:**
> 

Can I try the envy program to download the drivers, or do I have to get ubuntu running for real first before I can?

I was wondering too if vista can be affecting ubuntu at all. I've just recently had some problems with windows media player, powerdvd, and a few other programs when I try to play avi's or dvd's, and my computer has seemed to be working a little slower, and games don't seem quite as smooth. I tweaked a few nvidia settings and ran ntune, so just wondering if a clean install of vista might help out, as I'm planning to do this anyway before the permanent install of ubuntu.

Windows shouldn't affect it but it wouldn't hurt either. Yes try envy, I had the low res mode problem with and old 6200 nvidia and envy solved it for me. But it was a different situation all together. It wont hurt to try it though.

---

### Post by fain on 2008-03-23
> **duhglas said:**
> 
It had this message though when ubuntu was trying to boot:

*Strating powernawd...   
/etc/rc2.d/520powernawd: 156: cannot creat
/sys/devices/system/cpu/cpu0//cpufreq/scaling-governor: Directory nonexistent

*CPU frequency scaling not supported

so not sure if that means anything to you, but it seemed like an important message. 
Atleast we're making progress here, I was getting excited before thought it was going to boot up but not quite. So what shoudl we try now?




Probably means that you have AMD cool n' quite and/or AMD live turned off in the BIOS if you have AMD that is. I do not know much about Intel processors but im sure they have a frequency scaler too. Either way the system should still boot.

---

