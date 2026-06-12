---
title: "computer stalled at upgrading stage"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by miha2 on 2010-10-05
Hello everyone, I have a little (well, don't think it's easy to solve) issue - my computer stalled at irqbalance (set up), /etc/init/irqbalance.conf (installing, but hung up). So, my question is what to do? Should I just push the button for 6 seconds, unplug the power cord, or what? It's been like this for 5 hours, I thought it'd go away, but no. Of course, I'll leave it for night, but there has to be a way out. I don't want to reinstall the whole OS, I have lots of programs (and files, actually, too) in there. So, if you know what's the reason and how to deal with it, please tell me. Thank you. I know there are many geniuses in there. I launched updater yesterday, oct.3, and pushed install button only today. Come on, guys, there has to be a way out. Thanks to everyone.

---

### Post by Hakunka-Matata on 2010-10-05
I'll take a chance, you don't really have any other choice as I see it.  Are you talking about an Ubuntu upgrade?, if so, you'll probably be OK.  Even if it's totally botched and won't boot, you would be able to  install a new Ubuntu system as 'side by side' when you get to the partitioning section of the new install.  Your other partition would be preserved, and you could copy data off from it while running the new copy by mounting it.

---

### Post by miha2 on 2010-10-05
Yes, I'm talking about Ubuntu upgrade. 10.4 to 10.10. What do you mean, "side by side"? Do you mean it like downloading a dvd and burning it? Well, all the good burning soft I have on my system where the Ubuntu is upgrading. After all, I installed my Ubuntu through Wubi. If there's no other choice, I guess Canonical should be responsible for it, right? I mean, I will lose my data, and that way I can have some money (to build a new computer). Or I'm wrong?

---

### Post by lisati on 2010-10-05
> **miha2 said:**
> Yes, I'm talking about Ubuntu upgrade. 10.4 to 10.10. What do you mean, "[COLOR="DarkRed"]**side by side**[/COLOR]"? Do you mean it like downloading a dvd and burning it? Well, all the good burning soft I have on my system where the Ubuntu is upgrading. After all, I installed my Ubuntu through Wubi. If there's no other choice, I guess Canonical should be responsible for it, right? I mean, I will lose my data, and that way I can have some money (to build a new computer). Or I'm wrong?

If you temporarily use a dual-/multi-boot setup (sometimes referred to as "side by side") which has multiple OSes on your system, you might be recover your data, and delete or repair your original installation. 

Another option might be to use a LiveCD to recover your data, and then do a fresh installation over the top of your damaged install.

---

### Post by Hakunka-Matata on 2010-10-05
When Ubuntu is installed from a CD, you will eventually come to the partition portion of the install, one choice is to partition the hard disc into two (or more) partitions leaving an early OS in place, preserving it.  That method allows you to install two OSs on one hard drive.

Now, since you used wubi to install Ubuntu, it sounds like good ole MS Windows in involved too, is that right?

---

### Post by miha2 on 2010-10-05
Yes, I have old truthful XP, but it's slow. It has lots of viruses. (actually, that's the only reason I switched to Linux. I'd switch to Mac, but there were too much of problems, so I stayed with Linux. I wanted to try it a long time ago, didn't have reason to.)

I can't really see it under XP, I mean, files that are under Linux. I can see the disk image, I can see all the files associated with Wubi, not not Linux itself. Come on, guys, there has to be an easier way to upgrade it... Actually, you know what, it's been like this once or twice. I just did a 6-sec reboot (6-sec shutdown, and startup), and it worked fine. Now I'm afraid that it won't install. If somebody would try to upgrade and say me if it's pretty much important files left (it says 9 minutes left, though when I left for college I think it said 6 mins, so the result is that it's slowly but moving!)

---

### Post by miha2 on 2010-10-05
You know what, can it be just because the hard drive is too old? It's been working for 5 continuous years, shutting a PC, please keep in mind, down for a max of 2 weeks altogether. So, the total would be about somewhere around, but less than, 50,000 hours. I think it's a lot for hard drive that's been in production 5 years ago... Now they create hard drives that work up to 100,000 hours... Or about 10 yearsl, and if mind that my computer is made by HP, all looks true, it looks to be dying. Prove me wrong, please...

---

### Post by miha2 on 2010-10-05
so, it's not responding. it's at least something. what if i wait another night? might it work? or it's useless?

---

### Post by miha2 on 2010-10-05
come on guys, 4th post in a row, only i write. there has to be a way out. i'm ready to wait if required, just tell me if it's worth of it.

---

### Post by Hakunka-Matata on 2010-10-06
> **miha2 said:**
> Yes, I have old truthful XP, but it's slow. It has lots of viruses. (actually, that's the only reason I switched to Linux. I'd switch to Mac, but there were too much of problems, so I stayed with Linux. I wanted to try it a long time ago, didn't have reason to.)

You yourself say you have "lots of viruses", It's very hard to suggest any way forward until you clean out your viruses, unless you are willing to start from scratch and install a new system on that drive.  If you have important data on the drive, now would be the time to attempt to back it up.  Maybe that's why no one wants to suggest anything.  Viruses = undefined outcome

Balls in your court -  Good Luck

Have you run a chkdsk /f on the drive?

---

### Post by miha2 on 2010-10-06
viruses=undefined outcome, but on linux... yes, i admit, i do have Wine installed, but that means only one thing - viruses are in one of the programs that i lauched under wine. and since i launched only a few programs, it seems like one of them has viruses. but anyway, might it be because i have too old hard drive? the yellow button on my computer that lights when hard drive is busy, is always on, for the second day. so, if it's hard drive problem, that's pretty much ok. if it's virus problem, i understand. if it's linux problem, well, i guess it was a bad idea to switch to linux, better idea would have been to switch to mac. less problems, more responsibility from their side, more help, advanced troubleshooting. but for now, i need to know for sure if it's hard drive, or virus, or linux problem.

---

### Post by 23dornot23d on 2010-10-06
> 
issue - my computer stalled at irqbalance
> 
Yes, I'm talking about Ubuntu upgrade. 10.4 to 10.10. What do you mean,  "side by side"? 
a reply to side by side ,,,, 'which has multiple OSes on your system, you might be able to recover your data'

> 
Yes, I have old truthful XP, but it's slow.
[COLOR=Blue]Not a problem as such ..... as XP usually slows over time ...... but a new hard drive and a clean install could solve a lot of problems ......[/COLOR]

One reply 'You yourself say you have "lots of viruses", It's very hard to suggest  any way forward until you clean out your viruses'

Another reply 'If you temporarily use a dual-/multi-boot setup (sometimes referred to  as "side by side") which has multiple OSes on your system, you might be  recover your data, and delete or repair your original installation. '

You say you have a virus ..... You say you have a very old hard drive ....... this leads me to ask a few more questions ......

No operating system will work well if you start off with these two things as problems already 
( a old hard drive that you are not sure is working correctly - which also could have a virus on it ..... a fresh start may be required here ..... ) 
_______________________________________________

Q1 .... What computer is it ..... desktop a laptop ....  is it 32 bit ..... 64 bit ?

Q2 .... How many Hard Drives does it have >     1 ...... 2 ......  or more ...... ?

Q3 .... Do you have a flash drive and USB ports ..... ?

Q4 .... How have you dealt with the virus on XP ...... ?

Q5 .... Is it worth getting a brand new drive for this machine and starting again ..... 

________________________________________________

[B]If you started with a virus on your machine - 

The problem starts there ...... remove the virus first .....[/B]

[COLOR=Red][B]Once you have removed the virus it will make your life much easier ...... and then 
people can help sort this out  .....

If its a Desktop Machine ...... a new hard drive may be the place to start .....
especially after reading that the one that you have in it is quite old now ......


Solution .......
Do a clean install of LINUX on a Brand new hard Drive ...... 
( keep the other drive as a backup - and copy the useful data off of it but not the virus - that needs sorting out first )
[/B][/COLOR]

---

### Post by miha2 on 2010-10-06
1. Desktop. Windows x32, Ubuntu (don't know why) x64
2. 1
3. No flash drive, but a USB - I guess only 20-year-old computers don't have it
4. I ran Norton, Kaspersky, Trustport, Nod32, some other antiviruses, couldn't find a single virus. though i downloaded one russian antivirus, and it found some.
5. I guess I'll just buy a few new parts, like Atom and a new hard drive, and build a new system. And get a good laptop. For gaming. 
6 But only if it's that bad. So, I have another window popped up, it doesn't say anything so far ( the computer works really slow now), so I guess I'll wait the whole week (might leave for weekend) and see what's the problem. But more ideas are welcome. Especially about how to upgrade/return it to 10.04

---

### Post by miha2 on 2010-10-07
Good that I have an old good Vista upgrade dvd. I upgraded it, and now it loaded up just fine, leaving Ubuntu and all the files on XP. Now, I'm not deleting those. Let there be viruses, IF THERE ARE ANY, and i'll work on Linux. No more Windows until I build another computer. This will definitely go to garbage. Or to be sold. So, for so far, it loaded normally, but it still needs upgrade. So, I'm here to tell you this great news, and I'm just closing Firefox, and let open only Terminal and Update manager. See ya!

---

### Post by miha2 on 2010-10-07
Don't feel so happy you can get rid of me, now it can't find the kernel, and all i see is some window (forgot how it's called) and all I can see there is GRUB: so, is there any other way to at least downgrade it? Or upgrade? And looks like someone down here was right - XP does get old with time. It gets slow, and etc. Now, on Vista, (I'm not against it, but only if it works properly. In my case, it doesn't - the internet doesn't work. All the cables, everything is attached correctly, tried on Linux when I could use it. Actually, after it loaded, I tried to upgrade it, it said that there were some files to upgrade, so I did click to upgrade, and now it shows me the Grub window. I clicked TAB, just like they requested me to, and wrote from there something, and now it won't load. Please help me. Thank you.

---

