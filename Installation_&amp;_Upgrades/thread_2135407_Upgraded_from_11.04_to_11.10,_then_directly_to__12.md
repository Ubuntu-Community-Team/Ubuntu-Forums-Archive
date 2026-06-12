---
title: "Upgraded from 11.04 to 11.10, then directly to  12.04 - several problems now!"
date: 2013-04-14
forum: Installation &amp; Upgrades
---

### Post by crazybear on 2013-04-14
I loved 11.04, but it was no longer supported; reluctantly recently upgraded to 11.10 [...tried it for a few hours...all seemed OK!]; then upgraded again to 12.04 as I HATE constantly upgrading. I have an Ubuntu 12.04 system, I use the Classic desktop [don't like Unity....can't find a damn thing on it!]. However, there are some problems to which I did find solutions and others I have been unable to find solutions to. [Note: the same happened before, so I've actually gone though this process twice - same results each time - only minor difference noted below]. NB I think I correctly did the upgrades...it took all day, as I didn't use CDs, which seem to cause problems more often than live updates.

 Current Problems, for which I'd love some helpful ideas are:

- Opera [which I love] which worked fine in 11.04 and 11.10 doesn't work worth a damn in 12.04...the window is scrambled and unreadable.

- The sound is blurry and I re-installed all sound components - no change.

 - Only on the second update, any .pdf or .avi icon I have on my desktop [not the folder icons] are **much** too large and I can't find a way to reduce them! Strangely, .doc and .odt icons are fine.

- I'd like to find a way to put some of the applications and programs I have on the panels, but can only seem to put on those on the brief panel list...there must be a way.

- 12.04 is glacially slow to boot and has [apparently] only a very ugly boot/spash screen. I'd like to both change the font size and have a background image, if this is possible.

- No matter how I set things to NEVER blank screen, it goes blank after a short time. If I try to set a screensaver, it never goes on. The only success I had was not to have to log back on after it went blank.

 ...I think that covers it. I'm not happy...I liked my 11.04 and think it will be a LONG time before I'm back to where I was in productivity and lack of frustration. Luckily, the ATI driver and printer driver are fine and needed no tweeking. But these little things can drive one crazy! sound and not being able to use Opera are NOT minor!] Any help on any of the issues appreciated. Sorry, there are many, I know. Thanks in advance.

---

### Post by darkod on 2013-04-14
Have you tried a clean 12.04 LTS installation? Does it have the same issues?

Often doing upgrades in a row can create issues.

---

### Post by ajgreeny on 2013-04-14
What about trying a clean install of Xubuntu 12.04, if you really do not like unity.

I am in agreement with you that unity is not for me so last month, just before 10.04 loses support, I started using Xubuntu 12.04 as my main OS, and I have to admit it is superb.  I have added and use xfce-4.10 from the ppa and find that also very good and fast, and I am missing nothing from my old Lucid with gnome 2 DE.

Try it as a clean install; you may be surprised at how Xubuntu has grown up.

---

### Post by crazybear on 2013-04-24
I avoid 'clean installs'. The way my system is set up, a clean install will take me weeks to get back to where I was...and help from someone local sitting next to me on a few difficult programs - obscure ones. I should have mentioned 'please no suggestions for a clean install'. For some it makes little difference. For me is is the worst alternative and ONLY to be considered as an absolute last resort. While I only stayed with the 11.10 for a few hours, all seemed to be fine. However [twice] when I then upgraded to 12.04 many things sent wrong. None of which I've been able to find a reasonable fix for on the internet. :( I know an expert could move in all the programs and files from the old 11.04 [as I upgraded on a cloned disk, but I don't know how to do that. Even then, I don't think some would work if not installed in the new system. One program I use called Warrick is so rarely used one can find no help online other than from the developer - who is too busy with requests to EVER answer [two years and waiting!].

---

### Post by darkod on 2013-04-24
In that case, while I can't help you much, I can advise you to stick to LTS releases only. That way you upgrade to a new release every few years, not every 6 moths. The math is clear, more upgrades, more problems.

If in your case you can't make a clean install, tough luck.

---

### Post by fantab on 2013-04-24
Does this "Warric" have a dot folder, something like .warrik in Home? It will be hidden (Ctrl+H to reveal). Generally that dot folder should house your app preferences and settings. What you can do is backup that folder, install the program Warrick on machine with newer version of Ubuntu (or you try it on Live USB or DVD, with or without peristence). Then copy that backed up dot folder (.warrick) in Home and run the program and see if it runs as expected. Try for other programs as well. If it helps then you can "Clean" install Ubuntu 12.04. 

If you have cloned or Back up 11.04, then you can restore that image. Perhaps someone here can help you restore...

---

### Post by crazybear on 2013-04-25
> **darkod said:**
> In that case, while I can't help you much, I can advise you to stick to LTS releases only. That way you upgrade to a new release every few years, not every 6 moths. The math is clear, more upgrades, more problems.

If in your case you can't make a clean install, tough luck.

Look, the thing that is the most obviously missing thing - and that likely could fix many [or all?] of the other problems would be the repair console which is missing [not listed] on the grub login screen and is not working when I try to initiate it from within the program. Anyone have an idea of how to repair or reload that 'function'? Perhaps via terminal commands? Thanks.

Warrick is not an easy program and uses a huge number of perl files as dependencies. It is a program that reconstructs lost websites. I lost one and it has been reconstructing it. It takes a long time. However, getting it to run is not an easy chore. I'm not asking for help on that here. Once it is set up to run everytime I'm logged in, it runs in background and slowly reconstucts the lost website from a variety of places on the internet. Sadly, the guy who designed it doesn't respond to his emails and the instructions are for a very advanced linux person. I'll have to have someone come over for that, I think. It is not my priority o ther than I do NOT want to loose what is there now. I have many programs installed besides that and a clean install is the very last thing I want to try. Currently, I'm still using my 11.04 as the 12.04 is too annoying in the condition it is now.

Another side question. Why when both the 11.04 disk and 12.04 disk are in my computer will neither OS disk boot? Take out either one and they book fine. When I have two 11.04 disks in my computer there is no such problem. Is this a clue or just a strange artifact - same UUID perhaps?

---

### Post by darkod on 2013-04-25
If you copied partitions they would often have same UUID. You can always check all UUIDs with sudo blkid. If it doesn't work with both disks connected, do it one at a time and compare the UUIDs.

---

### Post by crazybear on 2013-04-26
Thanks, and if the UUIDs are the same, how do I change one of them. I assume I can randomly pick any number with the same amount of digits.

No help from anyone on the repair function not showing or working on the Grub screen? Have tried to reinstall grub...but it stays the same...odd.

---

### Post by darkod on 2013-04-26
I only know that UUID is assigned on formatting the partition. So, I don't know of a way to do it without formatting it (which means losing the data, or copying the data first, formatting the partition, then copying data back).

But I never even looked for changing UUID. I think it's posible, you would have to ask google for more details.

---

### Post by coffeecat on 2013-04-26
> **crazybear said:**
> Thanks, and if the UUIDs are the same, how do I change one of them. I assume I can randomly pick any number with the same amount of digits.

Assuming the partition is ext3 or ext4, and assuming the partition you want to reassign a random UUID to is /dev/sda1 (for illustration):

```
sudo tune2fs -U random /dev/sda1
```

Or if you want to assign a known UUID:

```
sudo tune2fs -U known-UUID /dev/sda1
```

Obviously, substitute your known UUID for "known-UUID" in the latter case.

---

### Post by tgalati4 on 2013-04-26
Regarding opera, what version of opera do you have on your system.  On 12.10 it looks like:

tgalati4@Mint14-Extensa ~ $ apt-cache policy opera
opera:
  Installed: (none)
  Candidate: 12.14.1738-1linuxmint
  Version table:
     12.14.1738-1linuxmint 0
        700 [http://packages.linuxmint.com/](http://packages.linuxmint.com/) nadia/import amd64 Packages

It's possible that opera didn't get upgraded since it comes from a 3rd-party repository.  The repository just contains the installer script and my understanding is that it is no longer being supported under Linux.

---

### Post by crazybear on 2013-05-01
I know you high-techies just LOOOOVE clean installs...but those of us who are not so Linux savvy avoid them like the plague - especially if one has a system one put months of work into tweaking it just right. 

 OK...I cloned my 11.04 and very carefully upgraded to 11.10 - set that  up a bit; then upgraded to 12.04. This time many fewer problems! Opera seems to be working OK so far; sound is not perfect [changed number of speakers to 6 from default of 2, but something still not right - I can hear voice - but wouldn't enjoy music - and it used to be exquisite!]. 

Icons on desktop are normal size - not oversized, so that fixed itself too.

 So, what remains is: 1- No repair console shows on the boot screen, so can't repair broken packages, nor have it update what other OS are available to boot to...instructions on this on internet seemed very advanced and not clear enough to dare to edit the grub file...still looking for clear instructions and if the instructions apply to me.
2 - the muddy sound, though I've tried all I can think of. 
 
the others are minor and I'm sure I can figure them out myself, eventually. The two above so far have defeated me.

But, it is getting better!...very slowly and after three LONG double upgrades!

---

